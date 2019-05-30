---
title: Verwenden einer Drittanbieter-Zertifizierungsstelle mit SCEP in Microsoft Intune – Azure | Microsoft-Dokumentation
description: In Microsoft Intune können Sie eine Zertifizierungsstelle eines Herstellers oder Drittanbieters hinzufügen, die mithilfe des SCEP-Protokolls Zertifikate für mobile Geräte ausstellen kann. In dieser Übersicht erhält Microsoft Intune durch eine Azure AD-Anwendung (Azure Active Directory) die Berechtigung zum Überprüfen von Zertifikaten. Mit der Anwendungs-ID, dem Authentifizierungsschlüssel und der Mandanten-ID der AAD-Anwendung stellen Sie anschließend während der Einrichtung des SCEP-Servers Zertifikate aus.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ed95507d8a7486bc1c1cca2c2a067658239eed8
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66043537"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Hinzufügen einer Partnerzertifizierungsstelle in Intune mithilfe von SCEP

In Microsoft Intune können Sie Drittanbieter-Zertifizierungsstellen hinzufügen. Diese Zertifizierungsstellen können mithilfe von SCEP (Simple Certificate Enrollment Protocol) Zertifikate an mobile Geräte übermitteln. Durch dieses Feature können auf Geräten mit Windows, iOS, Android und macOS neue Zertifikate ausgestellt oder vorhandene erneuert werden.

Die Nutzung des Features umfasst zwei Aspekte: die Verwendung einer Open Source-API und die Durchführung von Intune-Administratoraufgaben.

**1. Verwenden einer Open Source-API**  
Die von Microsoft erstellte API lässt sich in Intune integrieren und ermöglicht es, Zertifikate zu überprüfen, Erfolgs- oder Fehlermeldungen zu senden und SSL (insbesondere SSLSocketFactory) zur Kommunikation mit Intune zu verwenden.

Sie können die API aus dem [öffentlichen GitHub-Repository für die Intune-SCEP-API](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) herunterladen und in Ihren Lösungen verwenden. Verwenden Sie diese API mit SCEP-Servern von Drittanbietern, um benutzerdefinierte Aufforderungsüberprüfungen für Intune auszuführen, bevor ein Zertifikat an das Gerät übermittelt wird.

Unter [Integrieren von Drittanbieter-Zertifizierungsstellen in eine Intune-SCEP-Verwaltungslösung](scep-libraries-apis.md) finden Sie weitere Informationen zur Nutzung der API, deren Methoden und dem Testen der Lösung.

**2. Erstellen der Anwendung und des Profils**  
Mit einer Azure AD-Anwendung können Sie Rechte an Intune delegieren, wodurch sich SCEP-Anforderungen von Geräten verarbeitet lassen. Die Azure AD-Anwendung enthält die Anwendungs-ID und die Authentifizierungsschlüsselwerte, die in der API-Lösung der Entwickler verwendet werden. Administratoren können anschließend mithilfe von Intune SCEP-Zertifikatprofile bereitstellen. Sie können sich außerdem Berichte zum Bereitstellungsstatus auf Geräten anzeigen lassen.

Dieser Artikel stellt eine Übersicht über dieses Feature aus der Perspektive von Administratoren bereit und geht auch auf die Erstellung einer Azure AD-Anwendung ein.

## <a name="overview"></a>Übersicht

Die folgenden Schritte bieten einen Überblick über das Ausstellen von SCEP-Zertifikaten in Intune:

1. Ein Administrator erstellt in Intune ein SCEP-Zertifikatprofil für bestimmte Benutzer oder Geräte.
2. Das Gerät verbindet sich mit Intune.
3. Intune erstellt eine eindeutige SCEP-Aufforderung und stellt zusätzliche Informationen zur Integritätsprüfung bereit. Dazu gehören beispielsweise der erwartete Antragstellername und der alternative Antragstellername.
4. Intune verschlüsselt und signiert sowohl die Aufforderung als auch die Informationen zur Integritätsprüfung und sendet diese Informationen dann an das Gerät, das die SCEP-Anforderung stellt.
5. Das Gerät generiert auf der Grundlage des SCEP-Zertifikatprofils, das per Push von Intune übertragen wird, eine Zertifikatsignierungsanforderung (CSR) und ein Schlüsselpaar aus einem öffentlichen und privaten Schlüssel.
6. Die CSR und die verschlüsselt/signierte Aufforderung werden an den SCEP-Server-Endpunkt des Drittanbieters gesendet.
7. Der SCEP-Server sendet die CSR und die Aufforderung an Intune. Intune überprüft anschließend die Signatur, entschlüsselt die Nutzlast und vergleicht die CSR mit den Informationen zur Integritätsprüfung.
8. Intune sendet eine Antwort an den SCEP-Server zurück und gibt an, ob die Überprüfung der Aufforderung erfolgreich war.  
9. Wenn die Überprüfung der Aufforderung erfolgreich war, stellt der SCEP-Server das Zertifikat aus und überträgt es an das Gerät.

Im folgenden Diagramm wird der Ablauf der Drittanbieter-SCEP-Integration in Intune ausführlich dargestellt:

![Integration von Drittanbieter-Zertifizierungsstellen mittels SCEP in Microsoft Intune](./media/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Vorbereitungsschritte zur Integration von Drittanbieter-Zertifizierungsstellen

### <a name="validate-third-party-certification-authority"></a>Überprüfen der Drittanbieter-Zertifizierungsstelle

Vor der Integration von Drittanbieter-Zertifizierungsstellen in Intune muss sichergestellt werden, dass die verwendete Zertifizierungsstelle Intune unterstützt. Im Abschnitt [Drittanbieter-Partnerzertifizierungsstellen](#third-party-certification-authority-partners) weiter unten finden Sie eine Liste mit unterstützten Partnern. Weitere Informationen finden Sie auch im Leitfaden Ihrer Zertifizierungsstelle. Möglicherweise stellt Ihre Zertifizierungsstelle implementierungsspezifische Einrichtungsanleitungen bereit.

### <a name="authorize-communication-between-ca-and-intune"></a>Autorisieren der Kommunikation zwischen Zertifizierungsstelle und Intune

Wen ein SCEP-Server eines Drittanbieters eine benutzerdefinierte Aufforderung für Intune überprüfen soll, ist es erforderlich, eine App in Azure AD zu erstellen. Diese App erteilt Intune delegierte Berechtigungen, mit denen SCEP-Anforderungen überprüft werden.

Achten Sie darauf, dass Sie über die erforderlichen Berechtigungen zum Registrieren einer Azure AD-App verfügen. Siehe [Erforderliche Berechtigungen](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) in der Azure AD-Dokumentation.

#### <a name="create-an-application-in-azure-active-directory"></a>Registrieren einer Anwendung in Azure Active Directory  

1. Navigieren Sie im [Azure-Portal](https://portal.azure.com) zu **Azure Active Directory** > **App-Registrierungen**, und wählen Sie dann **Neue Registrierung** aus.  

2. Geben Sie auf der Seite **Anwendung registrieren** folgende Details an:  
   - Geben Sie im Abschnitt **Name** einen aussagekräftigen Anwendungsnamen ein.  
   - Wählen Sie im Abschnitt **Unterstützte Kontotypen** die Option **Konten in einem Organisationsverzeichnis** aus.  
   - Für **Umleitungs-URI** übernehmen Sie den Standardwert „Web“, und geben Sie dann die Anmelde-URL für den SCEP-Server des Drittanbieters an.  

3. Wählen Sie **Registrieren** aus, um die Anwendung zu erstellen und die Seite „Übersicht“ für die neue App zu öffnen.  

4. Kopieren Sie auf der App-Seite **Übersicht** den Wert der **Anwendungs-ID (Client)**, und notieren Sie ihn zur späteren Verwendung. Sie benötigen diesen Wert später.  

5. Navigieren Sie im Navigationsbereich der App unter **Verwalten** zu **Zertifikate und Geheimnisse**. Wählen Sie die Schaltfläche **Neuer geheimer Clientschlüssel** aus. Geben Sie einen Wert in „Beschreibung“ ein, wählen Sie eine Option für **Gültig bis** aus, und wählen Sie **Hinzufügen** aus, um einen *Wert* für den geheimen Clientschlüssel zu generieren. 
   > [!IMPORTANT]  
   > Bevor Sie diese Seite verlassen, kopieren Sie den Wert für den geheimen Clientschlüssel, und notieren Sie ihn zur späteren Verwendung mit der Zertifizierungsstellenimplementierung Ihres Drittanbieters. Dieser Wert wird nicht erneut angezeigt. Beachten Sie unbedingt den Leitfaden für die Zertifizierungsstelle Ihres Drittanbieters hinsichtlich der Konfiguration der Anwendungs-ID, des Authentifizierungsschlüssels und der Mandanten-ID.  

6. Notieren Sie sich Ihre **Mandanten-ID**. Die Mandanten-ID ist der Domänentext, der auf das @-Zeichen in Ihrem Konto folgt. Wenn Ihr Konto beispielsweise *admin@name.onmicrosoft.com* lautet, ist Ihre Mandanten-ID **name.onmicrosoft.com**.  

7. Wechseln Sie im Navigationsbereich für die App unter **Verwalten** zu **API-Berechtigungen**, und wählen Sie dann **Berechtigung hinzufügen** aus.  

8. Wählen Sie auf der Seite **API-Berechtigungen anfordern** den Eintrag **Intune** aus, und wählen Sie dann **Anwendungsberechtigungen** aus. Aktivieren Sie das Kontrollkästchen für **scep_challenge_provider** (SCEP-Challenge-Validierung).  

   Wählen Sie **Berechtigungen hinzufügen** aus, um diese Konfiguration zu speichern.  

9. Bleiben Sie auf der Seite **API-Berechtigungen**, und wählen Sie den Eintrag **Administratoreinwilligung für Microsoft gewähren** aus, und wählen Sie dann **Ja** aus.  
   
   Der Prozess der App-Registrierung in Azure AD ist abgeschlossen.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Konfigurieren und Bereitstellen eines SCEP-Zertifikatprofils
Erstellen Sie als Administrator ein SCEP-Zertifikatprofil für bestimmte Benutzer oder Geräte. Weisen Sie anschließend das Profil zu. Weitere Informationen finden Sie in den folgenden Artikeln:

- [Erstellen eines SCEP-Zertifikatprofils](certificates-scep-configure.md#create-a-scep-certificate-profile)

- [Zuweisen des Zertifikatprofils](certificates-scep-configure.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Entfernen von Zertifikaten

Wenn Sie die Registrierung aufheben oder das Gerät zurücksetzen, werden die Zertifikate entfernt. Die Zertifikate werden nicht widerrufen.

## <a name="third-party-certification-authority-partners"></a>Drittanbieter-Partnerzertifizierungsstellen
Intune wird von den folgenden Drittanbieter-Zertifizierungsstellen unterstützt:

- [Entrust Datacard](http://www.entrustdatacard.com/resource-center/documents/documentation)
- [EJBCA GitHub open-source version (Open Source-Version von EJBCA in GitHub)](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)

Wenn Sie als Drittanbieter-Zertifizierungsstelle daran interessiert sind, Ihr Produkt in Intune zu integrieren, müssen Sie sich mit dem API-Leitfaden vertraut machen:

- [GitHub-Repository für Intune-SCEP-API](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune-SCEP-API-Leitfaden für Drittanbieter-Zertifizierungsstellen](scep-libraries-apis.md)

## <a name="see-also"></a>Siehe auch

- [Konfigurieren von Zertifikatprofilen](certificates-scep-configure.md)
- [GitHub-Repository für Intune-SCEP-API](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune-SCEP-API-Leitfaden für Drittanbieter-Zertifizierungsstellen](scep-libraries-apis.md)
