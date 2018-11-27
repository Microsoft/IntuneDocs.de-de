---
title: Verwenden einer Drittanbieter-Zertifizierungsstelle mit SCEP in Microsoft Intune – Azure | Microsoft-Dokumentation
description: In Microsoft Intune können Sie eine Zertifizierungsstelle eines Herstellers oder Drittanbieters hinzufügen, die mithilfe des SCEP-Protokolls Zertifikate für mobile Geräte ausstellen kann. In dieser Übersicht erhält Microsoft Intune durch eine Azure AD-Anwendung (Azure Active Directory) die Berechtigung zum Überprüfen von Zertifikaten. Mit der Anwendungs-ID, dem Authentifizierungsschlüssel und der Mandanten-ID der AAD-Anwendung stellen Sie anschließend während der Einrichtung des SCEP-Servers Zertifikate aus.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: de0df4878d2461d2f7c0a022a7e3d305e58aef7f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187785"
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

Achten Sie darauf, dass Sie über die erforderlichen Berechtigungen zum Registrieren einer Azure AD-App verfügen. Unter [Erforderliche Berechtigungen](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) werden die dafür notwendigen Schritte beschrieben.

**Schritt 1: Erstellen einer Azure AD-Anwendung**

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Navigieren Sie zu **Azure Active Directory** > **App-Registrierungen** > **Registrierung einer neuen Anwendung**.
3. Geben Sie einen Namen und eine Anmelde-URL ein. Wählen Sie **Web-App/API** als Anwendungstyp aus.
4. Wählen Sie **Erstellen** aus.

Unter [Integrieren von Anwendungen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) finden Sie hilfreiche Informationen zum Erstellen einer App sowie Hinweise zur URL und zum Namen.

**Schritt 2: Erteilen von Berechtigungen**

Erteilen Sie nach der Erstellung der Anwendung der Microsoft Intune-API die erforderlichen Berechtigungen:

1. Navigieren Sie in Ihrer Azure AD-App zu **Einstellungen** > **Erforderliche Berechtigungen**.  
2. Rufen Sie **Hinzufügen** > **Hiermit wählen Sie eine API aus** auf, wählen Sie die **Microsoft Intune-API** aus, und klicken Sie auf **Auswählen**.
3. Klicken Sie unter **Berechtigungen auswählen** auf **SCEP challenge validation** (Überprüfung der SCEP-Aufforderung) > **Auswählen**.
4. Wählen Sie **Fertig** aus, um die Änderungen zu speichern.

**Schritt 3: Abrufen der Anwendungs-ID und des Authentifizierungsschlüssels**

Rufen Sie nun die ID und die Schlüsselwerte Ihrer Azure AD-Anwendung ab. Die folgenden Werte sind erforderlich:

- Anwendungs-ID
- Authentifizierungsschlüssel
- Mandanten-ID

**So rufen Sie die Anwendungs-ID und den Authentifizierungsschlüssel ab:**

1. Wählen Sie in Azure AD Ihre neue Anwendung aus (**App-Registrierungen**).
2. Kopieren Sie die **Anwendungs-ID**, und speichern Sie sie in Ihrem Anwendungscode.
3. Generieren Sie nun einen Authentifizierungsschlüssel. Navigieren Sie dazu in Ihrer Azure AD-App zu **Einstellungen** > **Schlüssel**.
4. Geben Sie im Feld **Kennwörter** eine Beschreibung ein, und legen Sie für den Schlüssel einen Gültigkeitszeitraum fest. **Speichern** Sie die Änderungen. Kopieren und speichern Sie den angezeigten Wert.

    > [!IMPORTANT]
    > Kopieren und speichern Sie den Schlüssel, sobald er angezeigt wird. Später ist dieser nicht mehr einsehbar. Dieser Schlüsselwert ist für die Implementierung der Drittanbieter-Zertifizierungsstelle erforderlich. Beachten Sie unbedingt deren Leitfaden zur Konfiguration der Anwendungs-ID, des Authentifizierungsschlüssels und der Mandanten-ID.

Die **Mandanten-ID** ist die Domänenzeichenfolge, die auf das @-Zeichen in Ihrem Konto folgt. Wenn Ihr Konto beispielsweise der Zeichenfolge `admin@name.onmicrosoft.com` entspricht, lautet Ihre Mandanten-ID **name.onmicrosoft.com**.

Unter [Abrufen der Anwendungs-ID und des Authentifizierungsschlüssels](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key) werden die Schritte zum Abrufen dieser Werte aufgeführt. Zusätzlich finden Sie dort weitere Informationen zu Azure AD-Apps.

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

Wenn Sie als Drittanbieter-Zertifizierungsstelle daran interessiert sind, Ihr Produkt in Intune zu integrieren, müssen Sie sich mit dem API-Leitfaden vertraut machen:

- [GitHub-Repository für Intune-SCEP-API](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune-SCEP-API-Leitfaden für Drittanbieter-Zertifizierungsstellen](scep-libraries-apis.md)

## <a name="see-also"></a>Siehe auch

- [Konfigurieren von Zertifikatprofilen](certificates-scep-configure.md)
- [GitHub-Repository für Intune-SCEP-API](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune-SCEP-API-Leitfaden für Drittanbieter-Zertifizierungsstellen](scep-libraries-apis.md)
