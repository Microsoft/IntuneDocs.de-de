---
title: Verwalten der Datenübertragung zwischen iOS-Apps
titleSuffix: Microsoft Intune
description: Hier finden Sie Informationen zur Verwendung der Richtlinien zur Verwaltung mobiler Apps in Microsoft Intune zum Verwalten der Datenübertragung zwischen Apps.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db583b1fc89edf72f329a605cc86363593eaaa9d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72497917"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Verwalten der Datenübertragung zwischen iOS-Apps in Microsoft Intune

Schränken Sie die Datenübertragung auf die von Ihnen verwalteten Apps ein, um Unternehmensdaten besser zu schützen. Sie können iOS-Apps auf folgende Weise verwalten:

- Schützen Sie Organisationsdaten für Geschäfts-, Schul- oder Unikonten, indem Sie eine App-Schutzrichtlinie für die Apps konfigurieren. Solche Apps werden als *richtlinienverwaltete Apps* bezeichnet.  Weitere Informationen finden Sie unter [allen mit Intune verwalteten Apps, die Sie mit der App-Schutzrichtlinie verwalten können](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

- Nutzen Sie die iOS-Geräteverwaltung zum Bereitstellen und Verwalten der Apps. Dafür müssen Ihre Geräte in einer Lösung zur Verwaltung mobiler Geräte (Mobile Device Management, MDM) registriert sein. Bei den von Ihnen bereitgestellten Apps kann es sich um *per Richtlinie verwaltete Apps* oder andere verwaltete iOS-Apps handeln.

Mit dem Feature **Open-in Management** für registrierte iOS-Geräte kann die Übertragung von Dateien zwischen verwalteten iOS-Apps begrenzt werden. Legen Sie Einschränkungen für *Open-in Management* in den Konfigurationseinstellungen fest, und stellen Sie sie dann über Ihre Lösung zur Verwaltung mobiler Geräte bereit.  Wenn ein Benutzer die bereitgestellte App installiert, werden die von Ihnen festgelegten Einschränkungen angewendet.

## <a name="use-app-protection-with-ios-apps"></a>Verwenden von App-Schutz mit iOS-Apps
Verwenden Sie App-Schutzrichtlinien mit dem iOS-Feature **Open-in Management**, um Unternehmensdaten auf folgende Arten zu schützen:

- **Geräte, die von keiner MDM-Lösung verwaltet werden**: Sie können die App-Schutzrichtlinieneinstellungen so festlegen, dass die Freigabe von Daten für andere Anwendungen über *Open-in* oder über *Freigabe von Erweiterungen* gesteuert wird.  Konfigurieren Sie zu diesem Zweck die Einstellung **Organisationsdaten an andere App senden** auf den Wert **Per Richtlinie verwaltete Apps mit Filterung für Open-in/Freigabe**.  Das *Open-in/Freigabe*-Verhalten in der *per Richtlinie verwalteten App* stellt nur andere *per Richtlinie verwaltete Apps* als Option für eine Freigabe zur Verfügung. 

- **Geräte, die mit MDM-Lösungen verwaltet werden**: Bei Geräten, die in Intune oder MDM-Drittanbieterlösungen registriert sind, wird die gemeinsame Datennutzung durch Apps mit App-Schutzrichtlinien und andere verwaltete, über MDM bereitgestellte iOS-Apps von Intune-App-Richtlinien und dem **Open in Management**-Feature von iOS gesteuert. Wenn Sie sicherstellen möchten, dass Apps, die Sie mithilfe einer MDM-Lösung bereitstellen, auch den Intune-App-Schutzrichtlinien zugeordnet werden, konfigurieren Sie die Benutzer-UPN-Einstellung gemäß der Beschreibung im folgenden Abschnitt [Konfigurieren der Benutzer-UPN-Einstellung](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Um festzulegen, wie Daten an andere Apps übertragen werden sollen, aktivieren Sie die Einstellung **Organisationsdaten an andere Apps senden**, und wählen Sie die gewünschte Freigabestufe aus. Um festzulegen, wie eine App Daten von anderen Apps empfangen soll, aktivieren Sie die Einstellung **Daten von anderen Apps empfangen**, und wählen Sie die gewünschte Datenempfangsstufe aus. Weitere Informationen zum Empfangen und Senden von App-Daten finden Sie unter [Einstellungen für die Datenverlagerung](app-protection-policy-settings-ios.md#data-protection).

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Konfigurieren der Benutzer-UPN-Einstellung für Microsoft Intune oder Drittanbieter-EMM
Die Konfiguration der Benutzer-UPN-Einstellung ist **erforderlich**, damit Geräte, die mit Intune oder der EMM-Lösung eines Drittanbieters verwaltet werden, das registrierte Benutzerkonto identifizieren können. Die UPN-Konfigurationen funktioniert in Verbindung mit den App-Schutzrichtlinien, die Sie über Intune bereitstellen. Das folgende Verfahren stellt einen allgemeinen Ablauf zum Konfigurieren der UPN-Einstellung und der resultierenden Benutzeroberfläche dar:

1. [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md) für iOS im [Azure-Portal](https://portal.azure.com). Konfigurieren Sie Richtlinieneinstellungen für alle Unternehmensanforderungen, und wählen Sie die iOS-Apps aus, für die diese Richtlinie gelten soll.

2. Stellen Sie die Apps und das E-Mail-Profil bereit, das mit Intune oder der MDM-Lösung eines Drittanbieters verwaltet werden soll, indem Sie die folgenden allgemeinen Schritte ausführen. Dies wird auch im *Beispiel 1* behandelt.

3. Stellen Sie die App mit den folgenden App-Konfigurationseinstellungen für das verwaltete Gerät bereit:

      **key** = IntuneMAMUPN, **value** = <username@company.com>

      Beispiel: [‘IntuneMAMUPN’, ‚janellecraig@contoso.com‘]
      
     > [!NOTE]
     > In Intune muss der Registrierungstyp der App-Konfigurationsrichtlinie auf **Verwaltete Geräte** festgelegt sein.
     > Zudem muss die App entweder aus dem Intune-Unternehmensportal installiert (wenn sie als verfügbar festgelegt ist) oder bei Bedarf mithilfe von Push an das Gerät übertragen werden. 

4. Stellen Sie die Richtlinie **Open in Management** mithilfe von Intune oder Ihrem MDM-Anbieter eines Drittanbieters für registrierte Geräte bereit.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Beispiel 1: Administratoroberfläche in Intune oder einer MDM-Konsole eines Drittanbieters

1. Navigieren Sie zur Administratorkonsole von Intune oder Ihres MDM-Anbieters eines Drittanbieters. Navigieren Sie zum Abschnitt der Konsole, in dem Sie die Anwendungskonfigurationseinstellungen für registrierte iOS-Geräte bereitstellen.

2. Geben Sie im Abschnitt „Anwendungskonfiguration“ die folgende Einstellung ein:

   **key** = IntuneMAMUPN, **value** = <username@company.com>

   Die genaue Syntax des Schlüssel-Wert-Paares kann sich basierend auf Ihrem MDM-Anbieter eines Drittanbieters unterscheiden. In der folgenden Tabelle finden Sie Beispiele für MDM-Lösungen von Drittanbietern sowie die genauen Werte, die Sie für das Schlüssel-Wert-Paar eingeben müssen.

   |MDM-Anbieter eines Drittanbieters| Konfigurationsschlüssel | Werttyp | Der Konfigurationswert|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Zeichenfolge | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Zeichenfolge | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Zeichenfolge | ${userUPN} **oder** ${userEmailAddress} |
   |Citrix-Endpunktverwaltung | IntuneMAMUPN | Zeichenfolge | ${user.userprincipalname} |
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | Zeichenfolge | %upn% |

> [!NOTE]  
> Wenn Sie für die Outlook-App in iOS eine App-Konfigurationsrichtlinie mit der Option zum Verwenden des Konfigurations-Designers bereitstellen, wird im Hintergrund automatisch der Konfigurationsschlüssel „IntuneMAMUPN“ für die Richtlinie konfiguriert. Weitere Informationen finden Sie im Abschnitt mit häufig gestellten Fragen des Artikels [New Outlook for iOS and Android App Configuration Policy Experience – General App Configuration ](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481) (Neue Funktionen bei Konfigurationsrichtlinien für Outlook für iOS und Android – allgemeine App-Konfiguration). 


### <a name="example-2-end-user-experience"></a>Beispiel 2: Endbenutzererfahrung

*Freigabe aus einer* per Richtlinie verwalteten App *für andere Anwendungen per Freigabe über das Betriebssystem*

1. Ein Benutzer öffnet die Microsoft OneDrive-App auf einem registrierten iOS-Gerät und meldet sich bei seinem Geschäftskonto an.  Das vom Benutzer angegebene Konto muss dem in den App-Konfigurationseinstellungen für die Microsoft OneDrive-App festgelegten Konto-UPN entsprechen.

2. Nach dem Anmelden werden die vom Adminstrator konfigurierten Einstellungen für Anwendungsschutzrichtlinien auf das Benutzerkonto in Microsoft OneDrive angewendet.  Hierzu gehört auch, dass die Einstellung **Organisationsdaten an andere Apps senden** auf den Wert **Per Richtlinie verwaltete Apps mit Betriebssystemfreigabe** festgelegt wird.

3. Der Benutzer zeigt die Vorschau einer Arbeitsdatei an und versucht, diese über Open-in für eine verwaltete iOS-App freizugeben.  

4. Die Daten werden erfolgreich übertragen und sind jetzt durch **Open-in Management** in der verwalteten iOS-App geschützt.  Die Intune-Anwendungsschutzrichtlinien gelten nicht für Anwendungen, bei denen es sich nicht um *per Richtlinie verwaltete Apps* handelt.

*Freigabe aus einer* verwalteten iOS-App*für eine*per Richtlinie verwaltete App *mit eingehenden Organisationsdaten*

1. Ein Benutzer öffnet eine native E-Mail auf einem registrierten iOS-Gerät mit einem verwalteten E-Mail-Profil.  

1. Der Benutzer öffnet ein Arbeitsdokument in Microsoft Word, das als Anlage an die native E-Mail angefügt war.

1. Wenn die Word-App gestartet wird, gibt es zwei Möglichkeiten:
   1. Die Daten werden durch Intune-Anwendungsschutzrichtlinien geschützt, wenn Folgendes gilt:
      - Der Benutzer ist bei einem Geschäftskonto angemeldet, das dem in den App-Konfigurationseinstellungen für die Microsoft Word-App festgelegten Konto-UPN entspricht. 
      - Die vom Adminstrator konfigurierten Einstellungen für Anwendungsschutzrichtlinien werden auf das Benutzerkonto in Microsoft Word angewendet.  Hierzu gehört auch, dass die Einstellung **Daten von anderen Apps empfangen** auf den Wert **Alle Apps mit eingehenden Organisationsdaten** festgelegt wird.
      - Die Daten werden erfolgreich übertragen, und das Dokument wird in der App mit der Identität des Geschäftskontos gekennzeichnet.  Intune-Anwendungsschutzrichtlinien schützen die Benutzeraktionen für das Dokument.
   1. Die Daten werden **nicht** durch Intune-Anwendungsschutzrichtlinien geschützt, wenn Folgendes gilt:
      - Der Benutzer ist **nicht** bei seinem Geschäftskonto angemeldet.
      - Ihr Administrator hat Einstellungen konfiguriert, die **nicht** auf Microsoft Word angewendet werden, weil der Benutzer nicht angemeldet ist.
      - Die Daten werden erfolgreich übertragen, und das Dokument wird in der App **nicht** mit der Identität des Geschäftskontos gekennzeichnet.  Intune-Anwendungsschutzrichtlinien schützen die Benutzeraktionen für das Dokument **nicht**, weil sie nicht aktiv sind.

    > [!NOTE]
    > Der Benutzer kann seine persönlichen Konten hinzufügen und mit Word verwenden. Es werden keine App-Schutzrichtlinien verwendet, wenn der Benutzer Word außerhalb des Arbeitskontexts verwendet. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Überprüfen von UPN-Einstellungen für Drittanbieter-EMM

Nach der Konfiguration der Benutzer-UPN-Einstellung sollten Sie überprüfen, ob die iOS-App App-Schutzrichtlinien von Intune erhalten kann und ob diese eingehalten werden.

Die Richtlinieneinstellung **Require app PIN** (App-PIN erforderlich) kann einfach getestet werden. Wenn die Richtlinieneinstellung **Erforderlich** lautet, sollte dem Benutzer die Aufforderung angezeigt werden, eine PIN festzulegen oder einzugeben, bevor er auf Unternehmensdaten zugreifen kann.

Kümmern Sie sich zuerst um das [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md) für die iOS-App. Unter [Überprüfen der Einrichtung von App-Schutzrichtlinien](app-protection-policies-validate.md) erhalten Sie weitere Informationen zum Testen einer App-Schutzrichtlinie.


## <a name="see-also"></a>Siehe auch
[Was sind Intune-App-Schutzrichtlinien?](app-protection-policy.md)
