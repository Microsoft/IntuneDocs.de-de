---
title: Verwalten der Datenübertragung zwischen iOS-Apps
titlesuffix: Microsoft Intune
description: Hier finden Sie Informationen zur Verwendung der Richtlinien zur Verwaltung mobiler Apps in Microsoft Intune zum Verwalten der Datenübertragung zwischen Apps.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ecf3791a7b01a9214c95680816a0fae16aade8f2
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31835532"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Verwalten der Datenübertragung zwischen iOS-Apps in Microsoft Intune
## <a name="manage-ios-apps"></a>Verwalten von iOS-Apps
Der Schutz der Unternehmensdaten umfasst die Sicherstellung, dass die Übertragung von Dateien auf Apps beschränkt ist, die von Ihnen verwaltet werden.  Sie können iOS-Apps auf folgende Weise verwalten:

-   Verhindern Sie den Verlust von Unternehmensdaten, indem Sie eine App-Schutzrichtlinie für die Apps konfigurieren, die als **richtlinienverwaltete** Apps bezeichnet werden. Weitere Informationen finden Sie unter [allen mit Intune verwalteten Apps, die Sie mit der App-Schutzrichtlinie verwalten können](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

-   Sie können Apps auch über den **MDM-Kanal** bereitstellen und verwalten.  Dies erfordert, dass die Geräte in der MDM-Lösung registriert sind. Dabei kann es sich um **richtlinienverwaltete** Apps oder andere verwaltete Apps handeln.

Mit dem Feature **Open in Management** für iOS-Geräte kann die Übertragung von Dateien zwischen Apps, die über den **MDM-Kanal** bereitgestellt werden, eingeschränkt werden. Die Einschränkungen für „Open in Management“ werden in den Konfigurationseinstellungen festgelegt und mithilfe der MDM-Lösung bereitgestellt.  Wenn der Benutzer die bereitgestellte App installiert, werden die festgelegten Einschränkungen angewendet.

##  <a name="using-app-protection-with-ios-apps"></a>Verwenden von App-Schutz mit iOS-Apps
App-Schutzrichtlinien können mit dem iOS-Feature **Open in Management** verwendet werden, um Unternehmensdaten auf folgende Weise zu schützen:

-   **Private Geräte von Mitarbeitern, die von keiner MDM-Lösung verwaltet werden:** Sie können die Einstellungen der App-Schutzrichtlinie so festlegen, dass die **App nur Daten an per Richtlinien verwaltete Apps übertragen darf**. Das Verhalten des Features „Öffnen in“ einer per Richtlinie verwalteten App zeigt nur andere per Richtlinie verwaltete Apps als Option für die Freigabe. Wenn ein Benutzer versucht, eine richtliniengeschützte Datei als Anhang von OneDrive in der nativen E-Mail zu senden, ist diese Datei nicht lesbar.

-   **Von Intune verwaltete Geräte:** Für Geräte, die bei Intune registriert sind, wird die Datenübertragung zwischen Apps mit App-Schutzrichtlinien und anderen verwalteten iOS-Apps, die über Intune bereitgestellt wurden, automatisch zugelassen. Um die Datenübertragung zwischen Apps mit App-Schutzrichtlinien zu erlauben, aktivieren Sie die Einstellung **Übermittlung von Daten nur an verwaltete Apps zulassen**. Sie können das Feature **Open in Management** verwenden, um die Datenübertragung zwischen Apps zu steuern, die über Intune bereitgestellt werden.   

-   **Von einem MDM-Lösung eines Drittanbieters verwaltete Geräte:** Sie können die Datenübertragung mithilfe des iOS-Features **Open in Management** auf verwaltete Apps einschränken.
Um sicherzustellen, dass Apps, die Sie mithilfe der Drittanbieter-MDM-Lösung bereitstellen, auch den in Intune konfigurierten App-Schutzrichtlinien zugeordnet sind, müssen Sie die Benutzer-UPN-Einstellung wie in der exemplarischen Vorgehensweise [Konfigurieren der Benutzer-UPN-Einstellung](#configure-user-upn-setting-for-third-party-emm) beschrieben konfigurieren.  Wenn Apps mithilfe der Benutzer-UPN-Einstellung bereitgestellt werden, werden die App-Schutzrichtlinien auf die App angewendet, wenn sich der Endbenutzer mit seinem Geschäftskonto anmeldet.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Konfigurieren der Benutzer-UPN-Einstellung für Microsoft Intune oder Drittanbieter-EMM
Die Konfiguration der UPN-Einstellung ist für Geräte **erforderlich**, die mit Intune oder der EMM-Lösung eines Drittanbieters verwaltet werden. Das nachfolgend beschriebene Verfahren ist ein allgemeiner Ablauf zum Konfigurieren der UPN-Einstellung und der resultierenden Benutzerumgebung:

1.  [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md) für iOS im [Azure-Portal](https://portal.azure.com). Konfigurieren Sie Richtlinieneinstellungen für alle Unternehmensanforderungen, und wählen Sie die iOS-Apps aus, für die diese Richtlinie gelten soll.

2.  Stellen Sie die Apps und das E-Mail-Profil, die mit Intune oder der MDM-Lösung eines Drittanbieters verwaltet werden sollen, mithilfe der generalisierten nachstehenden Schritte bereit. Diese wird auch im Beispiel 1 behandelt.

3.  Stellen Sie die App mithilfe der folgenden App-Konfigurationseinstellungen bereit:

      **Schlüssel** = IntuneMAMUPN, **Wert** = <username@company.com>

      Beispiel: [‘IntuneMAMUPN’, ‚jondoe@microsoft.com‘]

4.  Stellen Sie die Richtlinie **Open in Management** mithilfe von Intune oder Ihrem MDM-Anbieter eines Drittanbieters für registrierte Geräte bereit.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Beispiel 1: Administratoroberfläche in Intune oder einer MDM-Konsole eines Drittanbieters

1. Navigieren Sie zur Administratorkonsole von Intune oder Ihres MDM-Anbieters eines Drittanbieters. Navigieren Sie zum Abschnitt der Konsole, in dem Sie die Anwendungskonfigurationseinstellungen für registrierte iOS-Geräte bereitstellen.

2. Geben Sie im Abschnitt „Anwendungskonfiguration“ die folgende Einstellung ein:

   **Schlüssel** = IntuneMAMUPN, **Wert** = <username@company.com>

   Die genaue Syntax des Schlüssel-Wert-Paares kann sich basierend auf Ihrem MDM-Anbieter eines Drittanbieters unterscheiden. In der folgenden Tabelle zeigt Beispiele von MDM-Anbietern von Drittanbietern sowie die genauen Werte, die Sie für das Schlüssel-Wert-Paar eingeben müssen.

|MDM-Anbieter eines Drittanbieters| Konfigurationsschlüssel | Werttyp | Der Konfigurationswert|
| ------- | ---- | ---- | ---- |
|Microsoft Intune| IntuneMAMUPN | Zeichenfolge | {UserPrincipalName}|
|VMware AirWatch| IntuneMAMUPN | Zeichenfolge | {UserPrincipalName}|
|MobileIron | IntuneMAMUPN | Zeichenfolge | ${userUPN} **oder** ${userEmailAddress} |


### <a name="example-2-end-user-experience"></a>Beispiel 2: Endbenutzererfahrung

1.  Der Endbenutzer installiert die Microsoft Word-App auf dem Gerät.

2.  Der Endbenutzer startet die verwaltete systemeigene E-Mail-App für den Zugriff auf seine E-Mails.

3.  Der Endbenutzer versucht, ein Dokument über die systemeigene E-Mail in Microsoft Word zu öffnen.

4.  Beim Start der Word-App wird der Endbenutzer aufgefordert, sich mit seinem Geschäftskonto anzumelden.  Das Geschäftskonto, das der Benutzer eingibt, wenn er dazu aufgefordert wird, sollte dem in den App-Konfigurationseinstellungen für die Microsoft Word-App festgelegten Konto entsprechen.

    > [!NOTE]
    > Der Endbenutzer kann Word für private Zwecke weitere persönliche Konten hinzufügen, die nicht den App-Schutzrichtlinien unterliegen, wenn er die Word-App in einem privaten Kontext verwendet.

5.  Wenn die Anmeldung erfolgreich durchgeführt wurde, werden die Schutzrichtlinieneinstellungen für Apps auf die Word-App angewendet.

6.  Jetzt erfolgt die Datenübertragung und das Dokument wird in der App mit einer Unternehmensidentität markiert. Darüber hinaus werden die Daten in einem Arbeitskontext behandelt und die Richtlinieneinstellungen werden entsprechend angewendet.

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Überprüfen von UPN-Einstellungen für Drittanbieter-EMM

Nach der Konfiguration der Benutzer-UPN-Einstellung sollten Sie die Fähigkeit der iOS-App überprüfen, ob App-Schutzrichtlinien von Intune erhalten und befolgt werden können.

Die Richtlinieneinstellung **Require app PIN (App-PIN erforderlich)** kann einfach auf einem Gerät visuell getestet werden. Wenn die Richtlinieneinstellung auf **Ja** festgelegt wurde, sollte dem Endbenutzer eine Aufforderung angezeigt werden, eine PIN festzulegen oder einzugeben, wenn versucht wird, auf Unternehmensdaten zuzugreifen.

Kümmern Sie sich zuerst um das [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md) für die iOS-App. Unter [Überprüfen der App-Schutzrichtlinien](app-protection-policies-validate.md) erhalten Sie weitere Informationen zum Testen einer App-Schutzrichtlinie.


### <a name="see-also"></a>Siehe auch
[Was sind Intune-App-Schutzrichtlinien?](app-protection-policy.md)
