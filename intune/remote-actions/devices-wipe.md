---
title: Abkoppeln oder Zurücksetzen von Geräten mit Microsoft Intune | Microsoft-Dokumentation
description: Abkoppeln oder Zurücksetzen eines Geräts auf einem Android-, Android-Arbeitsprofil-, iOS-, macOS oder Windows-Gerät mithilfe von Microsoft Intune. Entfernen eines Geräts aus Azure Active Directory.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7cda7404d24ccb9bb1c42d6bb66d77f29ac925ac
ms.sourcegitcommit: b0d683917af83170f85022b270270d8ced8e301c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76812459"
---
# <a name="remove-devices-by-using-wipe-retire-or-manually-unenrolling-the-device"></a>Entfernen von Geräten durch Zurücksetzen, Abkoppeln oder manuelles Aufheben der Registrierung des Geräts

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Mithilfe der Aktionen **Abkoppeln** und **Zurücksetzen** können Sie Geräte aus Intune entfernen, die nicht mehr benötigt werden, einem neuen Zweck zugeführt werden oder verloren gegangen sind. Für Geräte, die in Intune registriert sind, können die Benutzer über das Intune-Unternehmensportal einen Remotebefehl ausführen.

> [!NOTE]
> Bevor Sie einen Benutzer aus Azure Active Directory (Azure AD) entfernen, verwenden Sie die Aktionen **Zurücksetzen** oder **Abkoppeln** für alle Geräte, die diesem Benutzer zugeordnet sind. Wenn Sie Benutzer mit verwalteten Geräten aus Azure AD entfernen, kann Intune keine Zurücksetzung oder Abkopplung für diese Geräte mehr vornehmen.

## <a name="wipe"></a>Zurücksetzen

Die Aktion **Zurücksetzen** setzt das Gerät auf die Werkseinstellungen zurück. Die Benutzerdaten werden beibehalten, wenn Sie das Kontrollkästchen **Registrierungszustand und Benutzerkonto beibehalten** aktivieren. Andernfalls werden alle Daten, Apps und Einstellungen entfernt.

|Aktion „Zurücksetzen“|**Registrierungszustand und Benutzerkonto beibehalten**|Aus der Intune-Verwaltung entfernt|Beschreibung|
|:-------------:|:------------:|:------------:|------------|
|**Zurücksetzen**| Nicht geprüft | Ja | Setzt alle Benutzerkonten, Daten, MDM-Richtlinien und Einstellungen zurück. Setzt das Betriebssystem auf Standardzustand und -einstellungen zurück.|
|**Zurücksetzen**| Überprüft | Nein | Setzt alle MDM-Richtlinien zurück. Behält Benutzerkonten und Kennwörter bei. Setzt Benutzereinstellungen auf die Standardwerte zurück. Setzt das Betriebssystem auf Standardzustand und -einstellungen zurück.|


> [!NOTE]
> Die Aktion „Zurücksetzen“ ist für iOS-Geräte nicht verfügbar, die mit der „Benutzerregistrierung“ registriert wurden.

Die Option **Registrierungszustand und Benutzerkonto beibehalten** steht Ihnen nur für Windows 10, Version 1709 oder höher, zur Verfügung.

Mit der Option **Perform protected wipe** (Geschütztes Zurücksetzen ausführen) wird sichergestellt, dass die Zurücksetzung nicht umgangen werden kann, indem das Gerät ausgeschaltet wird. Beim geschützten Zurücksetzen wird solange versucht, das Gerät zurückzusetzen, bis der Vorgang erfolgreich ist. In manchen Konfigurationen kann das Gerät aufgrund dieser Aktion nicht neu gestartet werden.

MDM-Richtlinien werden beim nächsten Herstellen einer Verbindung des Geräts mit Intune erneut angewendet.

Die Zurücksetzung eines Geräts auf Werkseinstellungen ist nützlich, bevor es an einen neuen Benutzer weitergegeben wird oder wenn es gestohlen wurde oder verloren gegangen ist. Überlegen Sie sich genau, ob Sie ein Gerät wirklich **zurücksetzen** möchten. Die Daten auf dem Gerät können anschließend nicht wiederhergestellt werden.

### <a name="wiping-a-device"></a>Zurücksetzen eines Geräts

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
3. Klicken Sie auf **Geräte** > **Alle Geräte**.
4. Wählen Sie den Namen des Geräts aus, das Sie auf Werkseinstellungen zurücksetzen möchten.
5. Klicken Sie im Bereich, der den Gerätenamen anzeigt, auf **Zurücksetzen**.
6. Bei Windows 10 Version 1709 oder höher steht Ihnen ebenfalls die Option **Gerät zurücksetzen, aber Registrierungsstatus und zugeordnetes Benutzerkonto beibehalten** zur Verfügung. 
    
    |Bei Zurücksetzung beibehalten |Nicht beibehalten|
    | -------------|------------|
    |Dem Gerät zugeordnete Benutzerkonten|Benutzerdateien|
    |Zustand des Computers \(der Domäne beigetreten, mit Azure AD verknüpft)| Vom Benutzer installierte Apps \(Store- und Win32-Apps)|
    |Anmeldung für die Verwaltung mobiler Geräte (MDM)|Geräteeinstellungen, die nicht dem Standard entsprechen|
    |Über OEM installierte Apps \(Store- und Win32-Apps)||
    |Benutzerprofil||
    |Benutzerdaten außerhalb des Benutzerprofils||
    |Automatische Anmeldung des Benutzers|| 
    
         
7. Klicken Sie auf **Ja**, um die Zurücksetzung zu bestätigen.

Wenn das Gerät eingeschaltet und verbunden ist, wird die Aktion **Zurücksetzen** innerhalb von 15 Minuten an alle Gerätetypen weitergegeben.

## <a name="retire"></a>Außerkraftsetzen

Die Aktion **Abkoppeln** entfernt die Daten aus verwalteten Apps (falls zutreffend), Einstellungen und E-Mail-Profilen, die mithilfe von Intune zugewiesen wurden. Das Gerät wird aus der Intune-Verwaltung entfernt. Dies passiert, wenn das Gerät sich das nächste Mal eincheckt und die Remoteaktion **Abkoppeln** empfängt. Das Gerät wird weiterhin in Intune angezeigt, bis das Gerät eincheckt. Wenn Sie veraltete Geräte sofort entfernen möchten, verwenden Sie stattdessen die Aktion [Löschen](devices-wipe.md#delete-devices-from-the-intune-portal).

Durch **Abkoppeln** werden die personenbezogenen Daten des Benutzers auf dem Gerät erhalten.  

In den folgenden Tabellen wird beschrieben, welche Daten entfernt werden und welche Auswirkung die Aktion **Abkoppeln** auf die Daten hat, die nach dem Entfernen der Unternehmensdaten auf dem Gerät verbleiben.

### <a name="ios"></a>iOS

|Datentyp|iOS|
|-------------|-------|
|Von Intune installierte Unternehmens-Apps und zugehörige Daten|**Über das Unternehmensportal installierte Apps:** Für Apps, die am Verwaltungsprofil angeheftet sind, werden alle App-Daten und Apps entfernt. Hierzu zählen auch Apps, die ursprünglich aus dem App Store installiert und später als Unternehmens-Apps verwaltet wurden, es sei denn, die App ist so konfiguriert, dass sie bei der Geräteentfernung nicht deinstalliert wird. <br /><br /> **Microsoft-Apps mit mobiler App-Verwaltung, die aus dem App Store installiert wurden**: Bei Apps, die nicht vom Unternehmensportal verwaltet werden, werden die Daten der Unternehmensapps, die durch die Mobile Application Management (MAM)-Verschlüsselung innerhalb des lokalen Speichers der App geschützt sind, entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt. Persönliche App-Daten und die Apps selbst werden nicht entfernt.|
|Einstellung|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate werden entfernt und gesperrt.|
|Verwaltungs-Agent|Das Verwaltungsprofil wird entfernt.|
|E-Mail|E-Mail-Profile, die über Intune bereitgestellt werden, werden entfernt. Auf dem Gerät zwischengespeicherte E-Mails werden gelöscht.|
|Entfernen von Azure AD|Der Azure AD-Datensatz wird entfernt.|

### <a name="android"></a>Android

|Datentyp|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Weblinks|Entfernt.|Entfernt.|
|Nicht verwaltete Google Play-Apps|Apps und Daten bleiben installiert. <br /> <br />Daten der Unternehmensapps, die durch die Mobile Application Management (MAM)-Verschlüsselung innerhalb des lokalen Speichers der App geschützt sind, werden entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt. |Apps und Daten bleiben installiert. <br /> <br />Daten der Unternehmensapps, die durch die Mobile Application Management (MAM)-Verschlüsselung innerhalb des lokalen Speichers der App geschützt sind, werden entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|
|Nicht verwaltete Geschäftssparten-Apps|Apps und Daten bleiben installiert.|Apps werden deinstalliert, und daher werden auch die lokalen Daten der App entfernt. Daten außerhalb der App (z.B. auf einer SD-Karte) werden nicht entfernt.|
|Verwaltete Google Play-Apps|App-Daten werden entfernt. Die App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung (Mobile Application Management) außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|App-Daten werden entfernt. Die App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt, werden aber nicht entfernt.|
|Nicht verwaltete Geschäftssparten-Apps|App-Daten werden entfernt. Die App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|App-Daten werden entfernt. Die App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|
|Einstellung|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate werden gesperrt, aber nicht entfernt.|Zertifikate werden entfernt und gesperrt.|
|Verwaltungs-Agent|Die Berechtigung „Geräteadministrator“ wird gesperrt.|Die Berechtigung „Geräteadministrator“ wird gesperrt.|
|E-Mail|N/V (E-Mail-Profile werden von Android-Geräten nicht unterstützt.)|E-Mail-Profile, die über Intune bereitgestellt werden, werden entfernt. Auf dem Gerät zwischengespeicherte E-Mails werden gelöscht.|
|Entfernen von Azure AD|Der Azure AD-Datensatz wird entfernt.|Der Azure AD-Datensatz wird entfernt.|

### <a name="android-work-profile"></a>Android-Arbeitsprofil

Beim Entfernen von Unternehmensdaten von Android-Arbeitsprofil-Geräten werden alle Daten, Apps und Einstellungen im Arbeitsprofil auf diesem Gerät entfernt. Das Gerät wird aus der Verwaltung mit Intune entfernt. Das Zurücksetzen wird für Android-Arbeitsprofile nicht unterstützt.

### <a name="android-enterprise-kiosk-devices"></a>Android Enterprise-Kioskgeräte

Sie können nur Kioskgeräte zurücksetzen. Sie können Android-Kioskgeräte nicht abkoppeln.


### <a name="macos"></a>macOS

|Datentyp|macOS|
|-------------|-------|
|Einstellung|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate, die über die mobile Geräteverwaltung bereitgestellt wurden, werden entfernt und widerrufen.|
|Verwaltungs-Agent|Das Verwaltungsprofil wird entfernt.|
|Outlook|Wenn der bedingte Zugriff aktiviert ist, empfängt das Gerät keine neuen E-Mails.|
|Entfernen von Azure AD|Der Azure AD-Datensatz wird entfernt.|

### <a name="windows"></a>Windows

|Datentyp|Windows 8.1 (MDM) und Windows RT 8.1|Windows RT|Windows Phone 8.1 und Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Von Intune installierte Unternehmens-Apps und zugehörige Daten|Die Schlüssel für Dateien, die von EFS geschützt sind, werden entfernt. Der Benutzer kann die Dateien nicht öffnen.|Unternehmens-Apps werden nicht entfernt.|Ursprünglich über das Unternehmensportal installierte Apps werden deinstalliert. Daten von Unternehmens-Apps werden entfernt.|Apps werden deinstalliert. Sideload-Schlüssel werden entfernt.<br>Für Windows 10 Version 1703 (Creators Update) und höher und Office 365 werden ProPlus-Apps nicht entfernt. Win32-Apps, die über die Intune-Verwaltungserweiterung installiert wurden, werden auf Geräten mit aufgehobener Registrierung nicht deinstalliert. Administratoren können Zuweisungsausnahmen nutzen, um Win32-Apps für BYOD-Geräte auszuschließen.|
|Einstellung|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|Entfernt.|Nicht unterstützt.|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate werden entfernt und gesperrt.|Zertifikate werden entfernt und gesperrt.|Nicht unterstützt.|Zertifikate werden entfernt und gesperrt.|
|E-Mail|Entfernt E-Mails, für die EFS aktiviert ist. Dazu zählen E-Mails und Anhänge in der E-Mail-App für Windows.|Nicht unterstützt.|E-Mail-Profile, die über Intune bereitgestellt werden, werden entfernt. Auf dem Gerät zwischengespeicherte E-Mails werden gelöscht.|Entfernt E-Mails, für die EFS aktiviert ist. Dazu zählen E-Mails und Anhänge in der E-Mail-App für Windows. Entfernt E-Mail-Konten, die von Intune bereitgestellt wurden.|
|Entfernen von Azure AD|Nein.|Nein.|Der Azure AD-Datensatz wird entfernt.|Der Azure AD-Datensatz wird entfernt.|

> [!NOTE]
> Für Windows 10-Geräte, die Azure AD während der Erstinstallation (OOBE) beitreten, entfernt der Befehl „Außer Betrieb setzen“ alle Azure AD-Konten vom Gerät. Führen Sie die Schritte unter [Starten Sie Ihren PC im abgesicherten Modus](https://support.microsoft.com/en-us/help/12376/windows-10-start-your-pc-in-safe-mode) aus, um sich als lokaler Administrator anzumelden und wieder Zugriff auf die lokalen Daten des Benutzers zu erhalten. 

### <a name="retire"></a>Außerkraftsetzen

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Klicken Sie im Bereich **Intune** auf die Option **Alle Geräte**.
3. Wählen Sie den Namen des Geräts aus, das Sie abkoppeln möchten.
4. Klicken Sie im Bereich, der den Gerätenamen anzeigt, auf **Abkoppeln**. Klicken Sie zum Bestätigen auf **Ja**.

Wenn das Gerät eingeschaltet und verbunden ist, wird die Aktion **Abkoppeln** innerhalb von 15 Minuten an alle Gerätetypen weitergegeben.

## <a name="delete-devices-from-the-intune-portal"></a>Löschen von Geräten aus der Intune-Portal

Wenn Sie Geräte aus dem Intune-Portal entfernen möchten, können Sie sie aus dem bestimmten Gerätebereich löschen. Wenn sich das Gerät das nächste Mal eincheckt, werden alle Unternehmensdaten davon entfernt.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Alle Geräte** aus, wählen Sie die Geräte, aus die Sie löschen möchten, und wählen Sie **Löschen** aus.

### <a name="automatically-delete-devices-with-cleanup-rules"></a>Automatisches Löschen von Geräten mit Regeln zur Bereinigung
Sie können Intune so konfigurieren, dass Geräte automatisch gelöscht werden, die inaktiv oder veraltet erscheinen oder vermeintlich nicht reagieren. Diese Bereinigungsregeln überwachen ständig Ihren Gerätebestand, damit Ihre Gerätedatensätze auf dem neuesten Stand bleiben. Geräte, die auf diese Weise gelöscht werden, werden aus der Intune-Verwaltung entfernt.
1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Device cleanup rules** > **Yes** (Gerätebereinigungsregeln > Ja) aus.
3. Geben Sie im Feld **Geräte löschen, die sich nicht eingecheckt haben für (Tage)** eine Zahl zwischen 30 und 270 an.
4. Wählen Sie **Speichern** aus.



## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Löschen von Geräten über das Azure Active Directory-Portal

Aufgrund von Kommunikationsproblemen oder fehlenden Geräten müssen Sie möglicherweise Geräte aus Azure AD löschen. Sie können die Aktion **Löschen** aber dazu verwenden, Gerätedatensätze aus dem Azure-Portal von den Geräten zu entfernen, von denen Sie wissen, dass sie schwer zugänglich sind, und für die eine erneute Kommunikation mit Azure unwahrscheinlich ist. Die Aktion **Löschen** entfernt keine Geräte aus der Verwaltung.

1. Melden Sie sich mit Ihren Administratoranmeldeinformationen [im Azure-Portal bei Azure Active Directory](https://aka.ms/accessaad) an. Sie können sich auch beim [Microsoft 365 Admin Center](https://admin.microsoft.com) anmelden. Klicken Sie im Menü auf **Admin Center** > **Azure AD**.
2. Erstellen Sie ein Azure-Abonnement, wenn Sie noch keins besitzen. Hierzu sollte keine Kreditkarte oder Zahlung erforderlich sein, wenn Sie ein gebührenpflichtiges Konto besitzen (klicken Sie auf den Abonnementlink **Ihr kostenloses Azure Active Directory registrieren**).
3. Wählen Sie zuerst **Azure Active Directory** und dann Ihre Organisation aus.
4. Wählen Sie die Registerkarte **Benutzer** aus.
5. Wählen Sie den Benutzer aus, der dem Gerät zugeordnet ist, das Sie löschen möchten.
6. Klicken Sie auf **Geräte**.
7. Entfernen Sie Geräte nach Bedarf. Sie können beispielsweise Geräte entfernen, die nicht mehr verwendet werden oder fehlerhafte Definitionen aufweisen.

## <a name="retire-an-apple-dep-device-from-intune"></a>Ausmustern eines Apple-DEP-Geräts von Intune

Wenn Sie ein Apple-DEP-Gerät vollständig aus der Intune-Verwaltung entfernen möchten, befolgen Sie diese Schritte:

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Klicken Sie auf **Geräte** > **Alle Geräte**, wählen Sie das Gerät aus, und klicken Sie auf **Abkoppeln**.
![Screenshot vom Abkoppeln](./media/devices-wipe/retire.png)
3. Besuchen Sie [deploy.apple.com](http://deploy.apple.com), und suchen Sie über die Seriennummer nach dem Gerät.
4. Wählen Sie im Menü **Assigned to** (Zugewiesen an) die Option **Unassigned** (Nicht zugewiesen) aus.

5. Wählen Sie **Reassign** (Neu zuweisen) aus.

    ![Screenshot für die Neuzuweisung für Apple](./media/devices-wipe/apple-reassign.png)

## <a name="fresh-start"></a>Sauberer Start

Gilt für Geräte mit Windows 10 Weitere Informationen finden Sie unter [Verwenden der Aktion „Sauberer Start“ zum Zurücksetzen von Windows 10-Geräten mit Intune](device-fresh-start.md).

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie ein gelöschtes Geräte erneut registrieren möchten, finden Sie in den [Optionen für die Registrierung](../enrollment/enrollment-options.md) weitere Informationen.

