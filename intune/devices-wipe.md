---
title: "Zurücksetzen auf Werkseinstellungen oder Entfernen von Unternehmensdaten auf Geräten mit Microsoft Intune"
titlesuffix: 
description: "Erfahren Sie, wie Sie Unternehmensdaten von einem Gerät entfernen oder wie Sie das Gerät auf Werkseinstellungen zurücksetzen."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 01/12/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 62404f6ffede7a7f3f7150da1fde289f2ba9e64f
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="remove-devices-by-using-factory-reset-or-remove-company-data"></a>Entfernen von Geräte mithilfe der Zurücksetzung auf Werkseinstellungen oder dem Entfernen von Unternehmensdaten

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Sie können Geräte aus Intune entfernen, wenn sie nicht mehr benötigt werden, einem neuen Zweck zugeführt werden oder verloren gegangen sind. Sie erreichen dies durch Ausgeben des Befehls **Unternehmensdaten entfernen** oder **Zurücksetzung auf Werkseinstellungen**. Für private Geräte, die in Intune registriert sind, können die Benutzer über das Intune-Unternehmensportal einen Remotebefehl erteilen.

> [!NOTE]
> Bevor Sie einen Benutzer aus Azure Active Directory entfernen, wird der Befehl **Unternehmensdaten entfernen** oder **Zurücksetzung auf Werkseinstellungen** für alle diesem Benutzer zugeordneten Geräte ausgeführt. Wenn Sie Benutzer mit verwalteten Geräten aus Azure Active Directory entfernen, kann Intune keine Zurücksetzung auf Werkseinstellungen vornehmen oder Unternehmensdaten auf diesen Geräten entfernen.

## <a name="factory-reset"></a>Wiederherstellung der Herstellerstandards

Die **Zurücksetzung auf Werkseinstellungen** stellt die Standardwerkseinstellungen wieder her und entfernt alle Daten und Einstellungen, die auf das Unternehmen oder den Benutzer zurückzuführen sind. Das Gerät wird aus der Intune-Verwaltung entfernt. Die Zurücksetzung eines Geräts auf Werkseinstellungen ist sehr nützlich, bevor es an einen Benutzer ausgegeben wird oder wenn es gestohlen wurde oder verloren gegangen ist. Überlegen Sie sich genau, ob Sie ein Gerät wirklich auf Werkseinstellungen zurücksetzen möchten. Die Daten auf dem Gerät können anschließend nicht wiederhergestellt werden.

### <a name="to-factory-reset-a-device"></a>So setzen Sie ein Geräts auf Werkseinstellungen zurück

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie auf dem Blatt **Geräte** die Option **Alle Geräte** aus.
4. Wählen Sie den Namen des Geräts aus, das Sie auf Werkseinstellungen zurücksetzen möchten.
5. Wählen Sie auf dem Blatt mit dem Namen des Geräts **Zurücksetzung auf Werkseinstellungen** aus.
6. Für die Windows 10-Version 1709 oder höher ist gibt es die zusätzliche Option „Registrierungszustand und Benutzerkonto beibehalten“. 
    
    |Bei Zurücksetzung auf Werkseinstellungen beibehalten|Nicht beibehalten|
    | -------------|------------|
    |Dem Gerät zugeordnete Benutzerkonten|Benutzerdateien|
    |Status der virtuellen Maschine \(Domänenbeitritt, mit Azure Active Directory verknüpft)| Vom Benutzer installierte Apps \(Store- und Win32-Apps)|
    |MDM-Registrierung|Geräteeinstellungen, die nicht dem Standard entsprechen|
    |Über OEM installierte Apps \(Store- und Win32-Apps)||
    |Benutzerprofil||
    |Benutzerdaten außerhalb des Benutzerprofils||
    |Automatische Anmeldung des Benutzers|| 
    
         
7. Wählen Sie zum Bestätigen der Zurücksetzung auf die Werkseinstellungen **Ja** aus.

Wenn das Gerät eingeschaltet und verbunden ist, dauert es weniger als 15 Minuten, bis ein Befehl zum Zurücksetzen auf Werkseinstellungen an alle Gerätetypen weitergegeben wurde.

## <a name="remove-company-data"></a>Entfernen von Unternehmensdaten

Der Befehl **Unternehmensdaten entfernen** entfernt die Daten aus verwalteten Apps (falls zutreffend), Einstellungen und E-Mail-Profile, die mithilfe von Intune zugewiesen wurden. Bei diesem Befehl bleiben die persönlichen Daten des Benutzers auf dem Gerät erhalten. Das Gerät wird aus der Intune-Verwaltung entfernt. Die folgende Tabelle beschreibt, welche Daten beim Entfernen von Unternehmensdaten entfernt werden und mit welchen Auswirkungen auf die auf dem Gerät verbleibenden Daten zu rechnen ist.

### <a name="ios"></a>iOS

|Datentyp|iOS|
|-------------|-------|
|Von Intune installierte Unternehmens-Apps und zugehörige Daten|Apps werden deinstalliert. Daten von Unternehmens-Apps werden entfernt.<br /><br />App-Daten aus Microsoft-Anwendungen, die die Verwaltung von mobilen Anwendungen verwenden, werden entfernt. Die App wird nicht entfernt.|
|Einstellung|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate werden entfernt und gesperrt.|
|Verwaltungs-Agent|Das Verwaltungsprofil wird entfernt.|
|E-Mail|E-Mail-Profile, die über Intune bereitgestellt wurden, werden entfernt und zwischengespeicherte E-Mails auf dem Gerät gelöscht.|
|Outlook|E-Mails, die über die Microsoft Outlook-App für iOS empfangen wurden, werden entfernt.|
|Verknüpfung für Azure Active Directory (AAD) aufheben|AAD-Datensatz wird entfernt|
|Kontakte | Direkt aus der App mit dem nativen Adressbuch synchronisierte Kontakte werden entfernt.  Alle Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht entfernt werden. <br /> <br />Derzeit wird nur die Outlook-App unterstützt.

### <a name="android"></a>Android

|Datentyp|Android|Android Samsung Knox Standard|
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
|E-Mail|n/v (E-Mail-Profile werden von Android-Geräten nicht unterstützt.)|E-Mail-Profile, die über Intune bereitgestellt wurden, werden entfernt und zwischengespeicherte E-Mails auf dem Gerät gelöscht.|
|Outlook|Von der Microsoft Outlook-App für Android empfangene E-Mail werden entfernt, allerdings nur, wenn Outlook durch MAM-Richtlinien geschützt wird. Andernfalls wird Outlook bei der Aufhebung der Registrierung nicht zurückgesetzt.|Von der Microsoft Outlook-App für Android empfangene E-Mail werden entfernt, allerdings nur, wenn Outlook durch MAM-Richtlinien geschützt wird. Andernfalls wird Outlook bei der Aufhebung der Registrierung nicht zurückgesetzt.|
|Verknüpfung für Azure Active Directory (AAD) aufheben|Azure AD-Datensatz wird entfernt|Azure AD-Datensatz wird entfernt|
|Kontakte | Direkt aus der App mit dem nativen Adressbuch synchronisierte Kontakte werden entfernt.  Alle Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht entfernt werden. <br /> <br />Derzeit wird nur die Outlook-App unterstützt.|Direkt aus der App mit dem nativen Adressbuch synchronisierte Kontakte werden entfernt.  Alle Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht entfernt werden. <br /> <br />Derzeit wird nur die Outlook-App unterstützt.

### <a name="android-for-work"></a>Android for Work

Beim Entfernen von Unternehmensdaten von Android for Work-Geräten entfernt alle Daten, Apps und Einstellungen im Arbeitsprofil auf diesem Gerät. Dies koppelt das Gerät von der Intuneverwaltung ab. Das Zurücksetzen auf Werkseinstellungen wird für Android for Work nicht unterstützt.


### <a name="macos"></a>macOS

|Datentyp|macOS|
|-------------|-------|
|Einstellung|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate, die über die mobile Geräteverwaltung bereitgestellt wurden, werden entfernt und widerrufen.|
|Verwaltungs-Agent|Das Verwaltungsprofil wird entfernt.|
|Outlook|Wenn der bedingte Zugriff aktiviert ist, empfängt das Gerät keine neuen E-Mails.|
|Verknüpfung für Azure Active Directory (AAD) aufheben|AAD-Datensatz wird entfernt|

### <a name="windows"></a>Windows

|Datentyp|Windows 8.1 (MDM) und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Von Intune installierte Unternehmens-Apps und zugehörige Daten|Bei Dateien, die durch ein EFS geschützt sind, wird der Schlüssel gesperrt, und der Benutzer kann die Dateien nicht mehr öffnen.|Unternehmensanwendungen werden nicht entfernt.|Ursprünglich über das Unternehmensportal installierte Anwendungen werden deinstalliert. Daten von Unternehmens-Apps werden entfernt.|Anwendungen werden deinstalliert, und Sideload-Schlüssel werden entfernt.<br>Für Windows 10 Version 1703 (Creators Update) und höher und Office 365 werden ProPlus-Apps nicht entfernt.|
|Einstellung|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|Entfernt.|Nicht unterstützt.|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate wurden entfernt und gesperrt.|Zertifikate wurden entfernt und gesperrt.|Nicht unterstützt.|Zertifikate wurden entfernt und gesperrt.|
|E-Mail|Entfernt EFS-aktivierte E-Mails, darunter die E-Mail-App für Windows-E-Mails und -Anlagen.|Nicht unterstützt.|E-Mail-Profile, die über Intune bereitgestellt wurden, werden entfernt und zwischengespeicherte E-Mails auf dem Gerät gelöscht.|Entfernt EFS-aktivierte E-Mails, darunter die E-Mail-App für Windows-E-Mails und -Anlagen. Entfernt E-Mail-Konten, die von Intune bereitgestellt wurden.|
|Verknüpfung für Azure Active Directory (AAD) aufheben|Nein.|Nein.|Azure AD-Datensatz wird entfernt|Nicht zutreffend. Windows 10 unterstützt kein Entfernen von Unternehmensdaten von Geräten, die mit Azure Active Directory verknüpft wurden.|

### <a name="to-remove-company-data"></a>So entfernen Sie Unternehmensdaten

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie auf dem Blatt **Geräte** die Option **Alle Geräte** aus.
4. Wählen Sie den Namen des Geräts aus, von dem Sie die Unternehmensdaten entfernen möchten.
5. Wählen Sie auf dem Blatt mit dem Gerätenamen **Unternehmensdaten entfernen** und dann zur Bestätigung **Ja** aus.

Wenn das Gerät eingeschaltet und verbunden ist, dauert es weniger als 15 Minuten, bis ein Befehl zum Entfernen der Daten an alle Gerätetypen weitergegeben wurde.

## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Löschen von Geräten über das Azure Active Directory-Portal

Aufgrund von Kommunikationsproblemen oder fehlender Geräte müssen Sie möglicherweise Geräte über Azure Active Directory (AD) löschen. Der Löschbefehl entfernt kein Gerät aus der Verwaltung. Sie können **Löschen** aber dazu verwenden, Gerätedatensätze über das Azure-Portal zu entfernen, von denen Sie wissen, dass sie schwer zugänglich sind, und für die eine erneute Kommunikation mit Azure unwahrscheinlich ist.

1.  Melden Sie sich [im Azure-Portal bei Azure Active Directory](http://aka.ms/accessaad) mit Ihren Administratoranmeldeinformationen an. Sie können sich auch im [Office 365-Portal](https://portal.office.com) anmelden und dann über den Link auf der linken Seite **Admin Center** &gt; **Azure AD** auswählen.
3.  Erstellen Sie ein Azure-Abonnement, wenn Sie noch keins besitzen. Hierzu sollte keine Kreditkarte oder Zahlung erforderlich sein, wenn Sie ein gebührenpflichtiges Konto besitzen (klicken Sie auf den Abonnementlink **Ihr kostenloses Azure Active Directory registrieren** ).
4.  Wählen Sie zuerst **Azure Active Directory** und dann Ihre Organisation aus.
5.  Wählen Sie die Registerkarte **Benutzer** aus.
6.  Wählen Sie den Benutzer aus, dessen Geräte Sie löschen möchten.
7.  Klicken Sie auf **Geräte**.
8.  Entfernen Sie Geräte nach Bedarf, z. B. solche, die nicht mehr verwendet werden oder fehlerhafte Definitionen haben.
