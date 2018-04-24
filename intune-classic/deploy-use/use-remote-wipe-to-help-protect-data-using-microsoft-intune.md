---
title: Verwenden der Remotezurücksetzung zum Schützen von Daten
description: Intune bietet Funktionen zum selektiven und vollständigen Zurücksetzen, um vertrauliche Unternehmensdaten und den Zugriff auf viele Unternehmensressourcen zu entfernen.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8519e411-3d48-44eb-9b41-3e4fd6a93112
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 82c50be9a8def23fadd8d24fc7654312d5c7ca5c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="help-protect-your-data-with-full-or-selective-wipe-using-microsoft-intune"></a>Schützen von Daten durch vollständiges oder selektives Zurücksetzen mit Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Sie können Apps und Daten von Intune-verwalteten Geräten zurücksetzen, die nicht mehr benötigt werden, einem neuen Zweck zugeführt werden oder verloren gegangen sind. Zu diesem Zweck enthält Intune Funktionen zum vollständigen oder selektiven Zurücksetzen. Für private Geräte, die in Intune registriert sind, können die Benutzer über die Intune-Unternehmensportal-App einen Remotebefehl zum Zurücksetzen des Geräts erteilen.

  > [!NOTE]
  > In diesem Thema wird nur das Zurücksetzen von Geräten behandelt, die von der Verwaltung mobiler Geräte für Intune verwaltet werden. Sie können auch das [Azure-Portal](https://portal.azure.com) zum [Entfernen von Unternehmensdaten aus Apps](wipe-managed-company-app-data-with-microsoft-intune.md) verwenden. Außerdem können Sie [mit der Intune-Clientsoftware verwaltete Computer abkoppeln](retire-a-windows-pc-with-microsoft-intune.md).

## <a name="full-wipe"></a>Vollständiges Zurücksetzen

**Vollständiges Zurücksetzen** setzt ein Gerät auf die werkseitigen Standardeinstellungen zurück, wobei alle Unternehmens- und Benutzerdaten und -einstellungen entfernt werden. Das Gerät wird aus Intune entfernt. Das vollständige Zurücksetzen ist hilfreich, wenn Sie ein Gerät vor der Übergabe an einen neuen Benutzer zurücksetzen möchten oder wenn ein Gerät verloren oder gestohlen wurde.  **Überlegen Sie sich genau, ob Sie ein Gerät wirklich vollständig zurücksetzen möchten. Die Daten auf dem Gerät können anschließend nicht wiederhergestellt werden.**


> [!Warning]
> Nach dem Zurücksetzen ist der Zugriff auf Windows 10 RTM-Geräte (Geräte vor Windows 10, Version 1511) mit weniger als 4 GB RAM vielleicht nicht möglich. Um auf ein Windows 10-Gerät zuzugreifen, das nicht mehr reagiert hat, können Sie das Gerät von einem USB-Laufwerk aus starten.

### <a name="remotely-wipe-a-device-from-the-intune-administrator-console"></a>Remotezurücksetzen eines Geräts über die Intune-Administratorkonsole

1. Wählen Sie Geräte aus, die zurückgesetzt werden sollen. Sie können diese nach Benutzer oder Gerät suchen.

   - **Nach Benutzer:**

     1.  Klicken Sie in der [Intune-Administratorkonsole](https://manage.microsoft.com/) auf **Gruppen** &gt; **Alle Benutzer**.

     2.  Klicken Sie auf den Namen des Benutzers, dessen mobiles Gerät Sie zurücksetzen möchten. Klicken Sie auf **Eigenschaften anzeigen**.

     3.  Klicken Sie auf der Seite **Eigenschaften** des Benutzers auf **Geräte** und dann auf den Namen des mobilen Geräts, das Sie zurücksetzen möchten. Zum Auswählen mehrerer Geräte halten Sie die STRG-Taste gedrückt und klicken auf jedes gewünschte Gerät.

   - **Nach Gerät:**

     1. Klicken Sie in der [Intune-Administratorkonsole](https://manage.microsoft.com/) auf **Gruppen** &gt; **Alle mobilen Geräte**.

        ![Starten eines Vorgangs zum Abkoppeln oder Zurücksetzen](../media/dev-sa-wipe.png)

     2. Klicken Sie auf **Geräte** und dann auf den Namen des mobilen Geräts, das Sie zurücksetzen möchten. Zum Auswählen mehrerer Geräte halten Sie die STRG-Taste gedrückt und klicken auf jedes gewünschte Gerät.

2. Klicken Sie auf **Abkoppeln/Zurücksetzen**.

3. Sie werden in einer Bestätigungsmeldung gefragt, ob Sie das Gerät abkoppeln möchten.

   -   Klicken Sie zum Ausführen einer **selektiven Zurücksetzung**, bei der nur unternehmenseigene Apps und Daten entfernt werden, auf **Ja**.

   -   Wählen Sie zum Ausführen einer **vollständigen Zurücksetzung**, bei der alle Apps und Daten gelöscht werden und das Gerät auf die werkseitigen Standardeinstellungen zurückgesetzt wird, die Option **Gerät vor dem Abkoppeln zurücksetzen**. Diese Aktion gilt für alle Plattformen außer Windows 8.1. **Daten, die durch ein vollständiges Zurücksetzen entfernt wurden, können nicht wiederhergestellt werden**.

Wenn das Gerät eingeschaltet und verbunden ist, dauert es weniger als 15 Minuten, bis ein Befehl zum Zurücksetzen an alle Gerätetypen weitergegeben wurde.

#### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>So löschen Sie Geräte im Azure Active Directory-Portal

1.  Navigieren Sie zu [http://aka.ms/accessaad](http://aka.ms/accessaad), oder wählen Sie **Administrator** &gt; **Azure AD** von [https://portal.office.com](https://portal.office.com) aus.

2.  Melden Sie sich mit Ihrer Organisations-ID über den Link im linken Bereich der Seite an.

3.  Erstellen Sie ein Azure-Abonnement, wenn Sie noch keins besitzen. Hierzu sollte keine Kreditkarte oder Zahlung erforderlich sein, wenn Sie ein gebührenpflichtiges Konto besitzen (klicken Sie auf den Abonnementlink **Ihr kostenloses Azure Active Directory registrieren** ).

4.  Wählen Sie zuerst **Active Directory** und dann Ihre Organisation aus.

5.  Wählen Sie die Registerkarte **Benutzer** aus.

6.  Wählen Sie den Benutzer aus, dessen Geräte Sie löschen möchten.

7.  Klicken Sie auf **Geräte**.

8.  Entfernen Sie Geräte nach Bedarf, z. B. solche, die nicht mehr verwendet werden oder fehlerhafte Definitionen haben.


## <a name="selective-wipe"></a>Selektives Zurücksetzen

Beim **selektiven Zurücksetzen** werden die Unternehmensdaten und bei Bedarf auch die Daten für die Verwaltung mobiler Apps (MAM, Mobile App Management) vom Gerät entfernt. Außerdem werden Einstellungen und E-Mail-Profile entfernt. Die persönlichen Daten des Benutzers bleiben beim selektiven Zurücksetzen auf dem Gerät erhalten. Das Gerät wird aus Intune entfernt. Die folgende Tabelle beschreibt, welche Daten bei einem selektiven Zurücksetzen entfernt werden und mit welchen Auswirkungen auf die auf dem Gerät verbleibenden Daten zu rechnen ist. (Diese Tabellen sind nach Plattform sortiert.)

**iOS**

|Datentyp|iOS|
|-------------|-------|
|Von Intune installierte Unternehmens-Apps und zugehörige Daten|Apps werden deinstalliert. Daten von Unternehmens-Apps werden entfernt.<br /><br />App-Daten aus Microsoft-Anwendungen, die die Verwaltung von mobilen Anwendungen verwenden, werden entfernt. Die App wird nicht entfernt.|
|Einstellung|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate werden entfernt und gesperrt.|
|Verwaltungs-Agent|Das Verwaltungsprofil wird entfernt.|
|E-Mail|E-Mail-Profile, die über Intune bereitgestellt wurden, werden entfernt und zwischengespeicherte E-Mails auf dem Gerät gelöscht.|
|Outlook|E-Mails, die über die Microsoft Outlook-App für iOS empfangen wurden, werden entfernt.|
|Azure Active Directory (AAD)-Verbindung aufgehoben|AAD-Datensatz wird entfernt.|
|Kontakte | Direkt aus der App mit dem nativen Adressbuch synchronisierte Kontakte werden entfernt.  Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht zurückgesetzt werden. <br /> <br />Derzeit wird nur die Outlook-App unterstützt.

**Android**

|Datentyp|Android|Android Samsung KNOX Standard|
|-------------|-----------|------------------------|
|Weblinks|Entfernt.|Entfernt.|
|Nicht verwaltete Google Play-Apps|Apps und Daten bleiben installiert.|Apps und Daten bleiben installiert.|
|Nicht verwaltete Geschäftssparten-Apps|Apps und Daten bleiben installiert.|Apps werden deinstalliert, und daher werden auch lokal für die App gespeicherte Daten entfernt. Daten außerhalb der App (z.B. auf einer SD-Karte) werden nicht entfernt.|
|Verwaltete Google Play-Apps|App-Daten werden entfernt. App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|App-Daten werden entfernt. App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt, werden aber nicht entfernt.|
|Nicht verwaltete Geschäftssparten-Apps|App-Daten werden entfernt. App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|App-Daten werden entfernt. App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|
|Einstellung|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate gesperrt, aber nicht entfernt.|Zertifikate wurden entfernt und gesperrt.|
|Verwaltungs-Agent|Die Berechtigung „Geräteadministrator“ wird gesperrt.|Die Berechtigung „Geräteadministrator“ wird gesperrt.|
|E-Mail|– Siehe das Outlook-Element.|E-Mail-Profile, die über Intune bereitgestellt wurden, werden entfernt und zwischengespeicherte E-Mails auf dem Gerät gelöscht.|
|Outlook|Von der Microsoft Outlook-App für Android empfangene E-Mail werden entfernt, allerdings nur, wenn Outlook durch MAM-Richtlinien geschützt wird. Andernfalls wird Outlook bei der Aufhebung der Registrierung nicht zurückgesetzt.|Von der Microsoft Outlook-App für Android empfangene E-Mail werden entfernt, allerdings nur, wenn Outlook durch MAM-Richtlinien geschützt wird. Andernfalls wird Outlook bei der Aufhebung der Registrierung nicht zurückgesetzt.|
|Azure Active Directory (AAD)-Verbindung aufgehoben|AAD-Datensatz wird entfernt.|AAD-Datensatz wird entfernt.|
|Kontakte | Direkt aus der App mit dem nativen Adressbuch synchronisierte Kontakte werden entfernt.  Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht zurückgesetzt werden. <br /> <br />Derzeit wird nur die Outlook-App unterstützt.|Direkt aus der App mit dem nativen Adressbuch synchronisierte Kontakte werden entfernt.  Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht zurückgesetzt werden. <br /> <br />Derzeit wird nur die Outlook-App unterstützt.

**Android for Work**

Das selektive Zurücksetzen auf Android for Work-Geräten entfernt alle Daten, Apps und Einstellungen im Arbeitsprofil auf diesem Gerät. Dies koppelt das Gerät von der Intuneverwaltung ab. Das vollständigen Zurücksetzen wird für Android for Work nicht unterstützt.

**Windows**

|Datentyp|Windows 8.1 (MDM) und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Von Intune installierte Unternehmens-Apps und zugehörige Daten|Bei Dateien, die durch ein EFS geschützt sind, wird der Schlüssel gesperrt, und der Benutzer kann die Dateien nicht mehr öffnen.|Unternehmensanwendungen werden nicht entfernt.|Ursprünglich über das Unternehmensportal installierte Anwendungen werden deinstalliert. Daten von Unternehmens-Apps werden entfernt.|Anwendungen werden deinstalliert, und Sideload-Schlüssel werden entfernt.|
|Einstellung|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|Entfernt.|Nicht unterstützt.|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate wurden entfernt und gesperrt.|Zertifikate wurden entfernt und gesperrt.|Nicht unterstützt.|Zertifikate wurden entfernt und gesperrt.|
|E-Mail|Entfernt EFS-aktivierte E-Mails, darunter die E-Mail-App für Windows-E-Mails und -Anlagen.|Nicht unterstützt.|E-Mail-Profile, die über Intune bereitgestellt wurden, werden entfernt und zwischengespeicherte E-Mails auf dem Gerät gelöscht.|Entfernt EFS-aktivierte E-Mails, darunter die E-Mail-App für Windows-E-Mails und -Anlagen. Entfernt E-Mail-Konten, die von Intune bereitgestellt wurden.|
|Azure Active Directory (AAD)-Verbindung aufgehoben|Nein.|Nein.|AAD-Datensatz wird entfernt.|Nicht zutreffend. Windows 10 unterstützt kein selektives Zurücksetzen für Geräte, die in Azure Active Directory eingebunden wurden.|

## <a name="wipe-encryption-file-system-efs-enabled-content"></a>Zurücksetzen EFS-aktivierter Inhalte
Das selektive Zurücksetzen von EFS-verschlüsselten Inhalten wird von Windows 8.1 und Windows RT 8.1 unterstützt. Folgendes gilt für das selektive Zurücksetzen von EFS-aktivierten Inhalten:

-   Nur Apps und Daten, die mit dem verschlüsselnden Dateisystem (EFS, Encrypting File System) geschützt sind und die die gleiche Internetdomäne wie das Intune-Konto verwenden, werden selektiv zurückgesetzt. Weitere Informationen finden Sie unter [Selektives Zurücksetzen bei der Gerätedatenverwaltung in Windows](http://technet.microsoft.com/library/dn486874.aspx).

-   Wenn Änderungen an der EFS zugeordneten Domäne vorgenommen werden, können die Änderungen bis zu 48 Stunden dauern, bevor Apps und Daten selektiv zurückgesetzt werden können, die die neue Domäne verwenden.

-   Jede bei Intune registrierte Domäne wird zurückgesetzt.

Folgende Daten und Apps werden derzeit vom selektiven Zurücksetzen mit EFS unterstützt:

-   E-Mail-App für Windows

-   Arbeitsordner

-   Von EFS verschlüsselte Dateien und Ordner Weitere Informationen finden Sie unter [Vorgehensweisen bei Verwendung des verschlüsselnden Dateisystems](http://support.microsoft.com/kb/223316).

-   Wenn Ihr Unternehmen seine Identität in Active Directory verwaltet, muss das Tool Verzeichnissynchronisierung (DirSync) verwendet werden, um Informationen in AAD zu synchronisieren, damit das selektive EFS-Zurücksetzen ordnungsgemäß funktioniert.  Weitere Informationen zu DirSync finden Sie unter [Verzeichnissynchronisierungsszenario](http://technet.microsoft.com/library/dn441212.aspx) in der Azure Active Directory-Dokumentation.

## <a name="monitor-retire-wipe-and-delete-actions"></a>Überwachen von Abkopplungs-, Zurücksetzungs- und Löschaktionen
So erhalten Sie einen Bericht zu Geräten, die abgekoppelt, zurückgesetzt oder gelöscht wurden:

1.  Klicken Sie in der [Intune-Administratorkonsole](https://manage.microsoft.com/) auf **Berichte** &gt; **Geräteverlaufsberichte**.

2.  Geben Sie ein Start- und Enddatum für den Bericht ein, und klicken Sie dann auf **Bericht anzeigen**.

Dieser Bericht zeigt auch, welcher Benutzer die Aktion ausgeführt hat.

### <a name="see-also"></a>Siehe auch
[Abkoppeln von Geräten](retire-devices-from-microsoft-intune-management.md)

[Windows Selective Wipe for Device Data Management (Selektives Zurücksetzen bei der Gerätedatenverwaltung in Windows)](http://technet.microsoft.com/library/dn486874.aspx)
