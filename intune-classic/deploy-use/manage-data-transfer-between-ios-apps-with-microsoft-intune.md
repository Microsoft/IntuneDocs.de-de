---
title: Verwalten der Datenübertragung zwischen iOS-Apps
description: Dieses Thema erläutert die Verwendung des iOS-Features „Öffnen in“ und der Richtlinien für die Verwaltung mobiler Apps, um Datenübertragungen zwischen Apps zu verwalten.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6b83e5fa37f9a9844e3011cded3c3cd58f268521
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="manage-data-transfer-between-ios-apps-with-microsoft-intune"></a>Verwalten der Datenübertragung zwischen iOS-Apps mit Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="manage-ios-apps"></a>Verwalten von iOS-Apps
Der Schutz der Unternehmensdaten umfasst die Sicherstellung, dass die Übertragung von Dateien auf Apps beschränkt ist, die von Ihnen verwaltet werden.  Sie können iOS-Apps auf folgende Weise verwalten:

-   Verhindern Sie den Verlust von Unternehmensdaten, indem Sie eine App-Schutzrichtlinie für die Apps konfigurieren, die als **richtlinienverwaltete** Apps bezeichnet werden.

-   Sie können Apps auch über den **MDM-Kanal** bereitstellen und verwalten.  Dies erfordert, dass die Geräte in der MDM-Lösung registriert sind. Dabei kann es sich um **richtlinienverwaltete** Apps oder andere verwaltete Apps handeln.

Mit dem Feature **Open in Management** für iOS-Geräte kann die Übertragung von Dateien zwischen Apps, die über den **MDM-Kanal** bereitgestellt werden, eingeschränkt werden. Die Einschränkungen von „Open in Management“ werden in den Konfigurationseinstellungen festgelegt und mithilfe der MDM-Projektmappe bereitgestellt.  Wenn der Benutzer die bereitgestellte App installiert, werden die festgelegten Einschränkungen angewendet.

##  <a name="manage-data-transfer-between-ios-apps"></a>Verwalten der Datenübertragung zwischen iOS-Apps
App-Schutzrichtlinien können mit dem iOS-Feature **Open in Management** verwendet werden, um Unternehmensdaten auf folgende Weite zu schützen:

-   **Im Besitz der Mitarbeiter befindliche Geräte, die von keiner MDM-Lösung verwaltet werden:** Sie können die [Einstellungen der App-Schutzrichtlinie](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) so festlegen, dass die **App nur Daten an verwaltete Apps übertragen kann**. Wenn der Endbenutzer eine geschützte Datei in einer Anwendung öffnet, die nicht richtlinienverwaltet ist, kann die Datei nicht gelesen werden.

-   **Von Intune verwaltete Geräte:** Für Geräte, die bei Intune registriert sind, wird die Datenübertragung zwischen Apps mit App-Schutzrichtlinien und anderen verwalteten iOS-Apps, die über Intune bereitgestellt wurden, automatisch zugelassen. Um die Datenübertragung zwischen Apps mit App-Schutzrichtlinien zu erlauben, aktivieren Sie die Einstellung **Übermittlung von Daten nur an verwaltete Apps zulassen**. Sie können das Feature **Open in Management** verwenden, um die Datenübertragung zwischen Apps zu steuern, die über Intune bereitgestellt werden.   

-   **Von einem MDM-Lösung eines Drittanbieters verwaltete Geräte:** Sie können die Datenübertragung mithilfe des iOS-Features **Open in Management** auf verwaltete Apps einschränken.
Um sicherzustellen, dass Apps, die Sie mithilfe der Drittanbieter-MDM-Lösung bereitstellen, auch den in Intune konfigurierten App-Schutzrichtlinien zugeordnet sind, müssen Sie die Benutzer-UPN-Einstellung wie in der exemplarischen Vorgehensweise [Konfigurieren der Benutzer-UPN-Einstellung](#configure-user-upn-setting-for-third-party-emm) beschrieben konfigurieren.  Wenn Apps mithilfe der Benutzer-UPN-Einstellung bereitgestellt werden, werden die App-Schutzrichtlinien auf die App angewendet, wenn sich der Endbenutzer mit seinem Geschäftskonto anmeldet.

> [!IMPORTANT]
> Die Benutzer-UPN-Einstellung ist nur für Apps erforderlich, die auf Geräten bereitgestellt werden, die von einer MDM-Lösung eines Drittanbieters verwaltet werden.  Diese Einstellung ist für Geräte nicht erforderlich, die von Intune verwaltet werden.

## <a name="configure-user-upn-setting-for-third-party-emm"></a>Konfigurieren von UPN-Einstellungen für Drittanbieter-EMM
Die Konfiguration der UPN-Einstellung ist für Geräte **erforderlich**, die von der EMM-Lösung eines Drittanbieters verwaltet werden. Das nachfolgend beschriebene Verfahren ist ein allgemeiner Ablauf zum Konfigurieren der UPN-Einstellung und der resultierenden Benutzerumgebung:


1.  [Erstellen und Bereitstellen von Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) für die iOS-Plattform im Azure-Portal. Konfigurieren Sie Richtlinieneinstellungen für alle Unternehmensanforderungen, und wählen Sie die Apps aus, für die diese Richtlinie gelten soll.

2.  Stellen Sie die Apps und das E-Mail-Profil, die **von der MDM-Lösung eines Drittanbieters** verwaltet werden sollen, mithilfe der generalisierten nachstehenden Schritte bereit. Diese wird auch im Beispiel 1 behandelt.

  1.  Stellen Sie die App mithilfe der folgenden App-Konfigurationseinstellungen bereit:

      **Schlüssel** = IntuneMAMUPN, **Wert** = <username@company.com>

      Beispiel: [‘IntuneMAMUPN’, ‚jondoe@microsoft.com‘]

  2.  Stellen Sie die Richtlinie „Open in Management“ mithilfe des MDM-Anbieters eines Drittanbieters für registrierte Geräte bereit.


### <a name="example-1-admin-experience-in-third-party-mdm-console"></a>Beispiel 1: Administratoroberfläche in einer MDM-Konsole eines Drittanbieters

1. Navigieren Sie zur Administratorkonsole Ihres MDM-Anbieters eines Drittanbieters. Navigieren Sie zum Abschnitt der Konsole, in dem Sie die Anwendungskonfigurationseinstellungen für registrierte iOS-Geräte bereitstellen.

2. Geben Sie im Abschnitt „Anwendungskonfiguration“ die folgende Einstellung ein:

  **Schlüssel** = IntuneMAMUPN, **Wert** = <username@company.com>

  Die genaue Syntax des Schlüssel-Wert-Paares kann sich basierend auf Ihrem MDM-Anbieter eines Drittanbieters unterscheiden. In der folgenden Tabelle zeigt Beispiele von MDM-Anbietern von Drittanbietern sowie die genauen Werte, die Sie für das Schlüssel-Wert-Paar eingeben müssen.

|MDM-Anbieter eines Drittanbieters| Konfigurationsschlüssel | Werttyp | Der Konfigurationswert|
| ------- | ---- | ---- | ---- |
| VMware AirWatch | IntuneMAMUPN | Zeichenfolge | {UserPrincipalName}|
| MobileIron Core | IntuneMAMUPN | Zeichenfolge | $EMAIL$ **oder** $USER_UPN$ |
| MobileIron Cloud | IntuneMAMUPN | Zeichenfolge | ${userUPN} **oder** ${userEmailAddress} |
| ManageEngine Mobile Device Manager | IntuneMAMUPN | Zeichenfolge | %upn% |

### <a name="example-2-end-user-experience"></a>Beispiel 2: Endbenutzererfahrung

1.  Der Endbenutzer installiert die Microsoft Word-App auf dem Gerät.

2.  Der Endbenutzer startet die verwaltete systemeigene E-Mail-App für den Zugriff auf seine E-Mails.

3.  Der Endbenutzer versucht, ein Dokument über die systemeigene E-Mail in Microsoft Word zu öffnen.

4.  Beim Start der Word-App wird der Endbenutzer aufgefordert, sich mit seinem Geschäftskonto anzumelden.  Das Geschäftskonto, das der Benutzer eingibt, wenn er dazu aufgefordert wird, sollte dem in den App-Konfigurationseinstellungen für die Microsoft Word-App festgelegten Konto entsprechen.

    > [!NOTE]
    > Der Endbenutzer kann Word für private Zwecke weitere persönliche Konten hinzufügen, die nicht den App-Schutzrichtlinien unterliegen, wenn er die Word-App in einem privaten Kontext verwendet.

5.  Wenn die Anmeldung erfolgreich durchgeführt wurde, werden die Schutzrichtlinieneinstellungen für Apps auf die Word-App angewendet.

6.  Nach der erfolgreiche Dateiübertragung wird das Dokument in der App als Unternehmensidentität markiert. Darüber hinaus wird die Datei in einem Arbeitskontext behandelt und die Richtlinieneinstellungen werden entsprechend angewendet.

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Überprüfen von UPN-Einstellungen für Drittanbieter-EMM

Nach der Konfiguration der Benutzer-UPN-Einstellung sollten Sie die Fähigkeit der iOS-App überprüfen, ob App-Schutzrichtlinien von Intune erhalten und befolgt werden können.

Die Richtlinieneinstellung **Require app PIN (App-PIN erforderlich)** kann einfach auf einem Gerät visuell getestet werden. Wenn die Richtlinieneinstellung auf **Ja** festgelegt wurde, sollte dem Endbenutzer eine Aufforderung angezeigt werden, eine PIN festzulegen oder einzugeben, wenn versucht wird, auf Unternehmensdaten zuzugreifen.

Kümmern Sie sich zuerst um das [Erstellen und Bereitstellen von Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) für die iOS-App. Unter [Überprüfen des Setups für die Verwaltung Ihrer mobilen Anwendungen](validate-mobile-application-management.md) erhalten Sie weitere Informationen zum Testen einer App-Schutzrichtlinie.



### <a name="see-also"></a>Siehe auch
[Protect app data using app protection policies with Microsoft Intune (Schützen von App-Daten mithilfe der App-Schutzrichtlinien mit Microsoft Intune)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
