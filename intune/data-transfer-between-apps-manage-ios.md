---
title: Verwalten der Datenübertragung zwischen iOS-Apps | Microsoft Intune
description: Hier finden Sie Informationen zur Verwendung der Richtlinien zur Verwaltung mobiler Apps in Microsoft Intune zum Verwalten der Datenübertragung zwischen Apps.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bbd0272b37b56f9f9e66cdf00ddc89a827f3c875
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816972"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Verwalten der Datenübertragung zwischen iOS-Apps in Microsoft Intune

Schränken Sie die Datenübertragung auf die von Ihnen verwalteten Apps ein, um Unternehmensdaten besser zu schützen. Sie können iOS-Apps auf folgende Weise verwalten:

-   Verhindern Sie den Verlust von Unternehmensdaten, indem Sie eine App-Schutzrichtlinie für die Apps konfigurieren, die als **richtlinienverwaltete** Apps bezeichnet werden. Weitere Informationen finden Sie unter [allen mit Intune verwalteten Apps, die Sie mit der App-Schutzrichtlinie verwalten können](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

-   Nutzen Sie den **MDM-Kanal** zum Bereitstellen und Verwalten von Apps. Dafür müssen Ihre Geräte allerdings für eine Lösung zur Verwaltung mobiler Geräte registriert sein. Bei den von Ihnen bereitgestellten Apps kann es sich um **richtlinienverwaltete** Apps oder andere verwaltete Apps handeln.

Mit dem Feature **Open in Management** für iOS-Geräte kann die Übertragung von Dateien zwischen Apps, die über den **MDM-Kanal** bereitgestellt werden, eingeschränkt werden. Legen Sie Einschränkungen für *Open in Management* in den Konfigurationseinstellungen fest, und stellen Sie sie anschließend mithilfe der Lösung zur Verwaltung mobiler Geräte.  Wenn ein Benutzer die bereitgestellte App installiert, werden die von Ihnen festgelegten Einschränkungen angewendet.

##  <a name="use-app-protection-with-ios-apps"></a>Verwenden von App-Schutz mit iOS-Apps
Verwenden Sie App-Schutzrichtlinien mit dem iOS-Feature **Open in Management**, um Unternehmensdaten auf folgende Weite zu schützen:

-   **Mitarbeitereigene Geräte, die von keiner MDM-Lösung verwaltet werden:** Sie können die Einstellungen der App-Schutzrichtlinie so festlegen, dass die **App nur Daten an per Richtlinien verwaltete Apps übertragen darf**. Das *Open-In*-Verhalten einer per Richtlinie verwalteten App stellt nur andere per Richtlinie verwaltete Apps als Option für die Freigabe dar. Wenn ein Benutzer versucht, eine richtliniengeschützte Datei als Anhang von OneDrive in der nativen E-Mail-App zu senden, ist diese Datei nicht lesbar.

-   **Von Intune verwaltete Geräte:** Für Geräte, die bei Intune registriert sind, wird die Datenübertragung zwischen Apps mit App-Schutzrichtlinien und anderen verwalteten iOS-Apps, die über Intune bereitgestellt wurden, automatisch zugelassen. Aktivieren Sie die Einstellung **Allow app to transfer data to other apps** (Zulassen, dass die App Daten an andere Apps überträgt), und wählen Sie die gewünschte Freigabestufe aus, um festzulegen, wie Daten an andere Apps übertragen werden sollen. Aktivieren Sie die Einstellung **Allow app to receive data from other apps** (Zulassen, dass die App Daten von anderen Apps empfängt), und wählen Sie die gewünschte Datenempfangsstufe aus, um festzulegen, wie eine App Daten von anderen Apps empfangen soll. Sie können das Feature **Open in Management** verwenden, um die Datenübertragung zwischen Apps zu steuern, die über Intune bereitgestellt werden. Weitere Informationen zum Empfangen und Senden von App-Daten finden Sie unter [Einstellungen für die Datenverlagerung](app-protection-policy-settings-ios.md#data-protection-settings).   

-   **Mit einer MDM-Lösung eines Drittanbieters verwaltete Geräte:** Sie können die Datenübertragung mithilfe des iOS-Features **Open in Management** auf verwaltete Apps einschränken.
Wenn Sie sicherstellen möchten, dass Apps, die Sie mithilfe der MDM-Lösung eines Drittanbieters bereitstellen, auch den in Intune konfigurierten App-Schutzrichtlinien zugeordnet sind, müssen Sie die Benutzer-UPN-Einstellung wie im folgenden Abschnitt mit der Überschrift [Konfigurieren der Benutzer-UPN-Einstellung](#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm) beschrieben konfigurieren. Wenn Apps mithilfe der Benutzer-UPN-Einstellung bereitgestellt werden, werden die App-Schutzrichtlinien auf die App angewendet, wenn sich der Benutzer mit seinem Geschäftskonto anmeldet.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Konfigurieren der Benutzer-UPN-Einstellung für Microsoft Intune oder Drittanbieter-EMM
Die Konfiguration der UPN-Einstellung ist für Geräte **erforderlich**, die mit Intune oder der EMM-Lösung eines Drittanbieters verwaltet werden. Die UPN-Konfigurationen funktioniert in Verbindung mit den App-Schutzrichtlinien, die Sie über Intune bereitstellen. Das folgende Verfahren stellt einen allgemeinen Ablauf zum Konfigurieren der UPN-Einstellung und der resultierenden Benutzeroberfläche dar:

1.  [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md) für iOS im [Azure-Portal](https://portal.azure.com). Konfigurieren Sie Richtlinieneinstellungen für alle Unternehmensanforderungen, und wählen Sie die iOS-Apps aus, für die diese Richtlinie gelten soll.

2.  Stellen Sie die Apps und das E-Mail-Profil bereit, das mit Intune oder der MDM-Lösung eines Drittanbieters verwaltet werden soll, indem Sie die folgenden allgemeinen Schritte ausführen. Dies wird auch im *Beispiel 1* behandelt.

3.  Stellen Sie die App mithilfe der folgenden App-Konfigurationseinstellungen bereit:

      **key** = IntuneMAMUPN, **value** = <username@company.com>

      Beispiel: [‘IntuneMAMUPN’, ‚jondoe@microsoft.com‘]

4.  Stellen Sie die Richtlinie **Open in Management** mithilfe von Intune oder Ihrem MDM-Anbieter eines Drittanbieters für registrierte Geräte bereit.


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
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | Zeichenfolge | %upn% |


### <a name="example-2-end-user-experience"></a>Beispiel 2: Endbenutzererfahrung

1.  Der Benutzer installiert die Microsoft Word-App auf dem Gerät.

2.  Der Benutzer startet die verwaltete native E-Mail-App, um auf seine E-Mails zuzugreifen.

3.  Der Benutzer versucht, ein Dokument über die native E-Mail in Microsoft Word zu öffnen.

4.  Beim Start der Word-App wird der Benutzer aufgefordert, sich mit seinem Geschäftskonto anzumelden. Das Geschäftskonto, das der Benutzer angibt, wenn er dazu aufgefordert wird, sollte dem in den App-Konfigurationseinstellungen für die Microsoft Word-App festgelegten Konto entsprechen.

    > [!NOTE]
    > Der Benutzer kann seine persönlichen Konten hinzufügen und mit Word verwenden. Es werden keine App-Schutzrichtlinien verwendet, wenn der Benutzer Word außerhalb des Arbeitskontexts verwendet. 

5.  Nach der Anmeldung werden die Einstellungen für die App-Schutzrichtlinie auf die Word-App angewendet.

6.  Jetzt erfolgt die Datenübertragung und das Dokument wird in der App mit einer Unternehmensidentität markiert.  Die Daten werden in einem Arbeitskontext verarbeitet, und die Richtlinieneinstellungen werden angewendet. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Überprüfen von UPN-Einstellungen für Drittanbieter-EMM

Nach der Konfiguration der Benutzer-UPN-Einstellung sollten Sie überprüfen, ob die iOS-App App-Schutzrichtlinien von Intune erhalten kann und ob diese eingehalten werden.

Die Richtlinieneinstellung **Require app PIN** (App-PIN erforderlich) kann einfach getestet werden. Wenn die Richtlinieneinstellung auf **Ja** festgelegt wird, sollte dem Benutzer die Aufforderung angezeigt werden, eine PIN festzulegen oder einzugeben, wenn er auf Unternehmensdaten zugreifen will.

Kümmern Sie sich zuerst um das [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md) für die iOS-App. Unter [Überprüfen der Einrichtung von App-Schutzrichtlinien](app-protection-policies-validate.md) erhalten Sie weitere Informationen zum Testen einer App-Schutzrichtlinie.


### <a name="see-also"></a>Siehe auch
[Was sind Intune-App-Schutzrichtlinien?](app-protection-policy.md)
