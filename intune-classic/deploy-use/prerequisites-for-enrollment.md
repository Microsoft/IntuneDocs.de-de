---
title: "Voraussetzungen für die Registrierung mobiler Geräte"
description: "Einrichten der Voraussetzungen für die Verwaltung mobiler Geräte (Mobile Device Management, MDM) und Vorbereiten der Registrierung für verschiedene Betriebssysteme."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 57dfc1bf2765de6c2e02352caca58f3859742fd6
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="prerequisites-for-mobile-device-management-in-intune"></a>Voraussetzungen für die Verwaltung von mobilen Geräten in Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Damit Mitarbeiter ihre mobilen Geräten bei Intune registrieren können, sind die folgenden Schritte erforderlich. Dieselben Schritte müssen auch ausgeführt werden, um unternehmenseigene Geräte verwalten zu können.

|Schritte|Details|  
|-----------|-------------|  
|**Schritt 1:** [Aktivieren von Verbindungen](#step-1-enable-connections)|Stellen Sie sicher, dass der benutzerdefinierte Domänenname konfiguriert und die Netzwerkkommunikation eingerichtet ist.|  
|**Schritt 2:** [Festlegen der MDM-Autorität](#step-2-set-mdm-authority)|Die Autorität für die Verwaltung mobiler Geräte definiert den Dienst, der Ihren Geräten zugewiesen ist.|
|**Schritt 3:** [Erstellen von Gruppen](#step-3-create-groups)|Konfigurieren Sie benutzerseitige Einstellungen für die Unternehmensportal-App.|  
|**Schritt 4:** [Konfigurieren des Unternehmensportals](#step-4-configure-company-portal)|Konfigurieren Sie benutzerseitige Einstellungen für die Unternehmensportal-App.|  
|**Schritt 5:** [Zuweisen von Benutzerlizenzen](#step-5-assign-user-licenses)|Weisen Sie den Benutzern Intune-Lizenzen zu, damit sie ihre Geräte registrieren können.|
|**Schritt 6:** [Aktivieren der Registrierung](#step-6-enable-enrollment)|Aktivieren Sie plattformspezifische Einstellungen für die iOS- und Windows-Verwaltung. Für Android-Geräte ist keine weitere Konfiguration erforderlich.|
|**Schritt 7:** [Nächste Schritte](#step-7-next-steps)|Aktivieren Sie plattformspezifische Einstellungen für die iOS- und Windows-Verwaltung. Für Android-Geräte ist keine weitere Konfiguration erforderlich.|

Suchen Sie nach Intune mit Configuration Manager?
> [!div class="button"]
> [SCCM-Dokumentation anzeigen >](https://docs.microsoft.com/sccm/mdm/deploy-use/setup-hybrid-mdm)

## <a name="step-1-enable-connections"></a>Schritt 1: Aktivieren von Verbindungen

Bevor Sie die Registrierung mobiler Geräte aktivieren, müssen Sie die folgenden Aufgaben ausgeführt haben:
- [Überprüfen der erforderlichen Netzwerk-URLs und -ports](/intune/network-bandwidth-use)
- [Hinzufügen und Überprüfen Ihres Domänennamens](/intune/custom-domain-name-configure)

## <a name="step-2-set-mdm-authority"></a>Schritt 2: Festlegen der MDM-Autorität
Die MDM-Autorität definiert den Verwaltungsdienst, der über die Berechtigung zum Verwalten einer Gruppe von Geräten verfügt. Die Optionen für die MDM-Autorität umfassen Intune selbst und Configuration Manager mit Intune. Wenn Sie Configuration Manager als Verwaltungsautorität festlegen, kann kein anderer Dienst für die Verwaltung mobiler Geräte verwendet werden.

>[!IMPORTANT]
> In Configuration Manager, Version 1610 oder höher, und Microsoft Intune, Version 1705, können Sie Ihre MDM-Autorität ändern, ohne sich an den Microsoft Support wenden und die Aufhebung der Registrierung sowie die erneute Registrierung vorhandener verwalteten Geräte durchführen zu müssen. Details finden Sie unter [Was Sie machen können, wenn Sie die falsche MDM-Autoritätseinstellung vorgenommen haben](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting).

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Verwaltung** &gt; **Verwaltung mobiler Geräte** aus.

2.  Klicken Sie in der Liste **Aufgaben** auf **Autorität für die Verwaltung mobiler Geräte festlegen**. Das Dialogfeld **MDM-Autorität festlegen** wird geöffnet.

    ![Dialogfeld „MDM-Autorität festlegen“](../media/intune-mdm-authority.png)

3.  Intune erfordert eine Bestätigung, dass es als MDM-Autorität verwendet werden soll. Aktivieren Sie das Kontrollkästchen, und wählen Sie dann **Ja** aus, um Microsoft Intune zum Verwalten mobiler Geräte zu verwenden.

## <a name="step-3-create-groups"></a>Schritt 3: Erstellen von Gruppen

Sie können Benutzer- und Gerätegruppen erstellen, um die Verwaltung zu vereinfachen und die Zielauswahl für bereitgestellte Apps, Richtlinien und Unternehmensressourcen zu verbessern. [Erfahren Sie, wie Sie Gruppen erstellen](use-groups-to-manage-users-and-devices-with-microsoft-intune.md#create-groups).

## <a name="step-4-configure-company-portal"></a>Schritt 4: Konfigurieren des Unternehmensportals

Im Intune-Unternehmensportal können Benutzer auf Unternehmensdaten zugreifen, häufige Aufgaben wie das Registrieren von Geräten und das Installieren von Apps ausführen und sich über Unterstützungsmöglichkeiten durch Ihre IT-Abteilung informieren.

> [!TIP]
> Wenn Sie das Unternehmensportal anpassen, gelten die Konfigurationen sowohl für die Unternehmensportal-Website als auch für die Unternehmensportal-Apps.

Durch Anpassen des Unternehmensportals können Sie Ihren Endbenutzern eine vertraute und hilfreiche Benutzeroberfläche bereitstellen. Melden Sie sich zu diesem Zweck einfach als Mandanten- oder Dienstadministrator bei der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) an, wählen Sie **Verwaltung** &gt; **Unternehmensportal** aus, und konfigurieren Sie die Einstellungen für das Unternehmensportal.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

### <a name="company-contact-information-and-privacy-statement"></a>Kontaktdaten und Datenschutzerklärung des Unternehmens

Der Unternehmensname wird als Titel des Unternehmensportals angezeigt. Die Kontaktinformationen werden Benutzern im Unternehmensportal auf dem Bildschirm für die Kontaktaufnahme mit der IT-Abteilung angezeigt. Die Datenschutzerklärung wird angezeigt, wenn ein Benutzer auf den Datenschutzlink klickt.


|          Feldname           | Max. Länge |                                                                                       Weitere Informationen                                                                                        |
|-------------------------------|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Firmenname          |     40     |                Dieser Name wird als Titel des Unternehmensportals angezeigt. <strong>Hinweis</strong>: Nur alphanumerische Zeichen. Dieses Feld unterstützt keine Sonderzeichen.                |
|  Kontaktname für IT-Abteilung   |     40     |                                                                Dieser Name wird auf der Seite <strong>An IT-Abteilung wenden</strong> angezeigt.                                                                |
|  Telefonnummer der IT-Abteilung   |     20     |                                                           Diese Telefonnummer wird auf der Seite <strong>An IT-Abteilung wenden</strong> angezeigt.                                                           |
|  E-Mail-Adresse der IT-Abteilung  |     40     |             Diese Kontaktadresse wird auf der Seite <strong>An IT-Abteilung</strong> wenden angezeigt. Sie müssen eine gültige E-Mail-Adresse im Format <strong>alias@domainname.com</strong> eingeben.              |
|    Zusätzliche Informationen     |    120     |                                                            Diese Informationen werden auf der Seite <strong>An IT wenden</strong> angezeigt.                                                             |
| URL der Datenschutzrichtlinie des Unternehmens |     79     | Sie können eine eigene Datenschutzerklärung für Ihr Unternehmen angeben. Diese wird angezeigt, wenn die Benutzer im Unternehmensportal auf die Datenschutzlinks klicken. Sie müssen eine gültige URL im Format https://www.contoso.com eingeben. |

### <a name="support-contacts"></a>Supportkontakte
Die Supportwebsite wird Benutzern im Unternehmensportal angezeigt, um ihnen Zugriff auf Onlinesupport zu ermöglichen.

|Feldname|Max. Länge|Weitere Informationen|
    |----------|------------------------|----------------|
    |URL der Supportwebsite|150|Wenn Sie über eine Supportwebsite verfügen, die Ihre Benutzer verwenden sollen, geben Sie hier die URL an. Die URL muss das Format https://www.contoso.com aufweisen. Wenn Sie keine URL angeben, wird im Unternehmensportal auf der Seite **An IT-Abteilung wenden** keine Supportwebsite angezeigt.|
    |Name der Website|40|Dies ist der Anzeigename der URL für die Supportwebsite. Wenn Sie für die Supportwebsite eine URL, aber keinen Anzeigenamen angeben, wird im Unternehmensportal auf der Seite **An IT-Abteilung wenden** der Text **Zur IT-Website wechseln** angezeigt.|


### <a name="company-branding-customization"></a>Anpassen des Unternehmensbrandings

Sie können Ihr Unternehmensportal mit Ihrem Firmenlogo, Firmennamen, Farbdesign und Hintergrund anpassen.

|Feldname|Weitere Informationen|
    |----------|----------------|
    |Farbdesign|Wählen Sie ein Farbdesign aus, das auf das Unternehmensportal angewendet werden soll.|
    |Firmenlogo einschließen|Wenn Sie diese Option aktivieren, können Sie Ihr Firmenlogo hochladen. Dieses wird dann im Unternehmensportal angezeigt. Sie können zwei Logos hochladen: ein Logo, das angezeigt wird, wenn der Hintergrund des Unternehmensportals weiß ist, und eines, das angezeigt wird, wenn für den Hintergrund des Unternehmensportals das von Ihnen ausgewählte Farbdesign verwendet wird. Die Logos müssen als PNG- oder JPG-Dateien vorliegen. Ihre Auflösung darf maximal 400 x 100 Pixel betragen, und die Größe darf 750 KB nicht überschreiten.|
    |Hintergrund für die Unternehmensportal-App auswählen|Diese Einstellung betrifft nur den Hintergrund der Unternehmensportal-App.|


Nach dem Speichern Ihrer Änderungen können Sie über die Links, die am unteren Rand der Seite **Unternehmensportal** in der Verwaltungskonsole angegeben sind, die Unternehmensportalwebsite anzeigen. Diese Links können nicht geändert werden. Wenn ein Benutzer sich anmeldet, werden über diese Links Ihre Abonnements im Unternehmensportal angezeigt.

## <a name="step-5-assign-user-licenses"></a>Schritt 5: Zuweisen von Benutzerlizenzen

Verwenden Sie das **Office 365-Verwaltungsportal**, um cloudbasierte Benutzer manuell hinzuzufügen und um sowohl cloudbasierten Benutzerkonten als auch Konten, die aus Ihrem lokalen Active Directory mit Azure Active Directory (Azure AD) synchronisiert wurden, Lizenzen zuzuweisen. Sie können [lokale Benutzer mit Azure AD synchronisieren](/intune/users-permissions-add#how-to-sync-on-premises-users-with-azure-ad).

1.  Melden Sie sich mit den Anmeldeinformationen Ihres Mandantenadministrators beim [Office 365-Verwaltungsportal](https://portal.office.com/Admin/Default.aspx) an.

2.  Wählen Sie das Benutzerkonto aus, dem Sie eine Intune-Benutzerlizenz zuweisen möchten, und aktivieren Sie in den Eigenschaften des Benutzerkontos das Kontrollkästchen **Microsoft Intune**.

3.  Das Benutzerkonto wird jetzt der Microsoft Intune-Benutzergruppe zugewiesen, die dem Benutzer Berechtigungen zur Verwendung des Diensts und zur Registrierung von Geräten für die Verwaltung gewährt.

### <a name="to-synchronize-on-premises-users-with-azure-ad"></a>So synchronisieren Sie lokale Benutzer mit Azure AD

1. [Fügen Sie das UPN-Suffix](https://technet.microsoft.com/library/cc772007.aspx) für Ihre benutzerdefinierte Domäne in Ihrem lokalen Active Directory hinzu.
2. Legen Sie das neue UPN-Suffix für die lokalen Benutzer fest, die Sie importieren möchten.
3. Führen Sie die [Azure AD Connect-Synchronisierung](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) aus, um Ihre lokalen Benutzer mit Azure AD zu integrieren.
4. Sobald die Informationen des Benutzerkontos erfolgreich synchronisiert wurden, können Sie mithilfe des [Verwaltungsportals für Office 365](https://portal.office.com/Admin/Default.aspx) Microsoft Intune-Lizenzen zuweisen.

## <a name="step-6-enable-enrollment"></a>Schritt 6: Aktivieren der Registrierung
Nach dem Einrichten der MDM-Autorität müssen Sie die Geräteverwaltung für die Betriebssysteme einrichten, die Ihre Organisation unterstützen möchte. Die zum Einrichten der Geräteverwaltung erforderlichen Schritte unterscheiden sich je nach Betriebssystem. Beispielsweise müssen Sie für Android-Betriebssysteme keinerlei Aktivitäten in der Intune-Verwaltungskonsole ausführen. Andererseits setzen Windows und iOS eine Vertrauensbeziehung zwischen den Geräten und Intune voraus, um die Verwaltung zu ermöglichen.

Richten Sie Verwaltung für die folgenden Plattformen ein:
- [iOS und Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Android](set-up-android-management-with-microsoft-intune.md)
- [Android for Work](set-up-android-for-work.md)
- [Windows 10 Mobile und Windows Phone](set-up-windows-device-management-with-microsoft-intune.md)
- [Windows-PCs und Laptops](manage-windows-pcs-with-microsoft-intune.md) (Intune-Clientsoftware)

Sie können auch die [Registrierung von unternehmenseigenen Geräten](manage-corporate-owned-devices.md) aktivieren.

## <a name="step-7-next-steps"></a>Schritt 7: Nächste Schritte

Nachdem nun die Registrierung aktiviert ist, sollten Sie die Verwaltung einrichten, um Ihre geschäftlichen Anforderungen zu erfüllen. Im Folgenden finden Sie einige Verwaltungsoptionen:

- [Bereitstellen von Richtlinien zum Verwalten von Einstellungen und Features auf Geräten](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
- [Aktivieren des Zugriffs auf Unternehmensressourcen wie E-Mail, WLAN und VPN](enable-access-to-company-resources-with-microsoft-intune.md)
- [Hinzufügen von Apps](add-apps.md) und [Bereitstellen von Apps](deploy-apps.md) auf verwalteten Geräten
- [Erstellen von Gerätekompatibilitätsrichtlinien](introduction-to-device-compliance-policies-in-microsoft-intune.md) und [Beschränken des Zugriffs basierend auf Kompatibilität](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)

## <a name="what-to-do-if-you-choose-the-wrong-mdm-authority-setting"></a>Was Sie machen können, wenn Sie die falsche MDM-Autoritätseinstellung vorgenommen haben

Wenn Sie feststellen, dass Sie die falsche MDM-Autoritätseinstellung vorgenommen haben, und Sie diese ändern möchten, haben Sie die folgenden Optionen.

### <a name="change-the-mdm-authority-yourself"></a>Selbst die MDM-Autorität ändern
Ab Configuration Manager, Version 1610, und Microsoft Intune, Version 1705, können Sie die MDM-Autorität von Microsoft Intune in Configuration Manager (hybrid) oder umgekehrt ändern, ohne sich an den Microsoft Support wenden und die Aufhebung der Registrierung sowie die erneute Registrierung vorhandener verwalteter Geräte durchführen zu müssen. Einzelheiten finden Sie unter [Ändern Ihrer MDM-Autorität]( /sccm/mdm/deploy-use/change-mdm-authority).

### <a name="contact-microsoft-support"></a>Kontaktaufnahme mit dem Microsoft-Support
Wenn Sie Configuration Manager vor Version 1610 ausführen, müssen Sie den Microsoft-Support kontaktieren. Sie können die Einstellung nicht selbst ändern. Bevor Sie sich an den Microsoft Support wenden, schauen Sie sich bitte die folgenden Informationen an, welche Angaben Sie dem Microsoft Support machen müssen, damit diese die Änderungen vornehmen können.

Es gibt drei Möglichkeiten, Ihre MDM-Autorität zurückzusetzen. In Ihrer Anfrage an den Support müssen Sie die Möglichkeit auswählen, die auf Ihren Fall zutrifft. Falls Ihr Szenario zu keiner der Möglichkeiten passt, wenden Sie sich an den Microsoft Support.

Der Microsoft Support wird Sie darum bitten, folgende Angaben zu bestätigen:

- Mandanten-ID: die Domäne, mit der Sie sich im Dienst anmelden (z.B. intune.onmicrosoft.com)
- Die MDM-Autorität, zu der Sie wechseln möchten
- Die Bestätigung, dass Sie die erforderlichen Schritte abgeschlossen haben (siehe unten)

Wenn Sie Koexistenz verwenden, müssen Sie sowohl die Intune- als auch die Office 365-Checklisten überprüfen.

#### <a name="reset-mdm-authority-from-intune-to-configuration-manager"></a>MDM-Autorität von Intune auf Configuration Manager zurücksetzen

Führen Sie zum Zurücksetzen Ihrer MDM-Autorität diese Schritte durch, bevor Sie sich an den Microsoft Support wenden.

- Alle Geräte aus der Intune-Administratorkonsole außer Kraft setzen. Versuchen Sie nicht, ein Gerät im Gerät selbst außer Kraft zu setzen. 
- Löschen Sie den Service to Service Connector (unter **Administration** > **Verwaltung mobiler Geräte** > **Microsoft Exchange**), oder deaktivieren Sie den Exchange Connector, falls dieser eingerichtet ist.
- Entfernen Sie die Verwaltungsrolle des Geräteregistrierungs-Managers aus **Admin** > **Geräteregistrierungs-Manager**.
- Deaktivieren Sie die Gerätegruppenzuordnung unter **Admin** > **Verwaltung mobiler Geräte** > **Gerätegruppenzuordnung** aus.
- Entfernen Sie Sideload-Schlüssel aus **Admin** > **Verwaltung mobiler Geräte** > **Windows** > **Sideload-Schlüssel**.
- Löschen Sie das APNS-Zertifikat von iOS unter **Admin** > **Verwaltung mobiler Geräte** > **iOS**.
- Löschen Sie das iOS-DEP-Token unter **Admin** > **Verwaltung mobiler Geräte** > **iOS**.
- Löschen Sie alle Richtlinien, die für MDM-Geräte vorgesehen sind, unter **Richtlinie** > **Konfigurationsrichtlinien**.
- Löschen Sie alle veröffentlichten Anwendungen, die für MDM-Geräte vorgesehen sind, unter **Apps** > **Verwaltete Software**.

#### <a name="reset-mdm-authority-from-configuration-manager-to-intune"></a>MDM-Autorität von Configuration Manager auf Intune zurücksetzen

Führen Sie zum Zurücksetzen Ihrer MDM-Autorität diese Schritte durch, bevor Sie sich an den Microsoft Support wenden.

- Alle als mobile Geräte verwaltete Geräte aus der Configuration Manager-Konsole außer Kraft setzen. Versuchen Sie nicht, ein Gerät im Gerät selbst außer Kraft zu setzen. 
- Entfernen sie alle Benutzer aus der Intune-Benutzergruppe. Richten Sie das Intune-Abonnement auf eine leere Benutzersammlung, oder entfernen Sie alle Benutzer aus der anvisierten Sammlung.  Bestätigen Sie in der Datei CloudUserSync.log, dass alle Benutzer entfernt wurden. 
- Deaktivieren sie die iOS-Plattform, um das APNS-Zertifikat zu bereinigen.
- Löschen Sie alle veröffentlichten Anwendungen, die für MDM-Geräte vorgesehen sind.
- Löschen Sie alle Richtlinien, die für MDM-Geräte vorgesehen sind.
- Entfernen Sie den Windows Intune Connector aus der Configuration Manager-Konsole (gilt nur für R2 SP1 oder davor).
Entfernen Sie das Intune-Abonnement, indem Sie mit der rechten Maustaste auf das Abo klicken und dann **Löschen** auswählen.
- SMS-Executive-Dienst neu starten.
- Stellen Sie uns einige Beispielbenutzer zur Verfügung, sodass wir, nachdem der Prozess abgeschlossen wurde, überprüfen können, ob Configuration Manager-Lizenzen entfernt wurden.

#### <a name="reset-mdm-authority-from-office-365-to-configuration-manager"></a>MDM-Autorität von Office 365 auf Configuration Manager zurücksetzen

1. Navigieren Sie zu [https://protection.office.com](https://protection.office.com).
2. Wählen Sie die Registerkarte **Sicherheitsrichtlinien** dann **Geräteverwaltung** aus.
3. Setzen Sie alle Geräte mit **Selektives Zurücksetzen** außer Kraft. Versuchen Sie nicht, ein Gerät im Gerät selbst außer Kraft zu setzen. Wenn das selektive Zurücksetzen deaktiviert ist, ist keine weitere Aktion erforderlich.
4. Wählen Sie die Registerkarte **Sicherheitsrichtlinien** dann **Gerätesicherheitsrichtlinien** aus.
5. Wählen Sie für alle vorhandenen Richtlinien **Löschen** aus. Wenn sich die Richtlinien im Status „ausstehend“ befinden, ist keine weitere Aktion erforderlich.

>[!NOTE]
>Das APNS-Zertifikat von iOS kann nicht gelöscht werden und bleibt an den Account angeschlossen.

#### <a name="next-steps-for-mdm-authority-resets"></a>Die nächsten Schritte für ein Zurücksetzen der MDM-Autorität

Sobald der Microsoft Support die Elemente auf der verfügbaren Checkliste überprüft hat, kann das Zurücksetzen der MDM-Autorität bis zu drei Werktage in Anspruch nehmen – normalerweise dauert es aber nur einen Tag.

>[!IMPORTANT]
>Bitte konfigurieren Sie Ihr Abonnement erst, wenn der Microsoft Support bestätigt hat, dass das Zurücksetzen erfolgreich abgeschlossen wurde! Frühzeitige Konfiguration kann dazu führen, dass Schäden auftreten bzw. dass Sie in der Benutzung Ihres Intune eingeschränkt werden.
