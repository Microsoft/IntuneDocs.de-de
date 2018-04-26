---
title: Entfernen von Unternehmensdaten von Geräten mithilfe von Microsoft Intune (Azure) | Microsoft-Dokumentation
description: Entfernen von Unternehmensdaten von einem Gerät oder Zurücksetzen eines Geräts (Android, Android for Work, iOS, macOS oder Windows) auf Werkseinstellungen mithilfe von Microsoft Intune. Entfernen eines Geräts aus Azure Active Directory.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 228198276643f1eb8dfcb0392e4902a7f56875c9
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="remove-devices-by-using-factory-reset-or-remove-company-data"></a>Entfernen von Geräte mithilfe der Zurücksetzung auf Werkseinstellungen oder dem Entfernen von Unternehmensdaten

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Sie können Geräte aus Intune entfernen, wenn sie nicht mehr benötigt werden, einem neuen Zweck zugeführt werden oder verloren gegangen sind. Sie erreichen dies durch Verwenden des Befehls **Unternehmensdaten entfernen** oder durch die Aktion **Zurücksetzung auf Werkseinstellungen**. Für private Geräte, die in Intune registriert sind, können die Benutzer über das Intune-Unternehmensportal einen Remotebefehl erteilen.

> [!NOTE]
> Bevor Sie einen Benutzer aus Azure Active Directory (Azure AD) entfernen, verwenden Sie den Befehl **Unternehmensdaten entfernen** oder die Aktion **Zurücksetzung auf Werkseinstellungen** für alle diesem Benutzer zugeordneten Geräte. Wenn Sie Benutzer mit verwalteten Geräten aus Azure AD entfernen, kann Intune keine Zurücksetzung auf Werkseinstellungen mehr vornehmen oder Unternehmensdaten von diesen Geräten entfernen.

## <a name="factory-reset"></a>Wiederherstellung der Herstellerstandards

Die Aktion **Zurücksetzung auf Werkseinstellungen** setzt das Gerät auf die Werkseinstellungen zurück. Dadurch werden alle Unternehmens- und Benutzerdaten sowie -einstellungen entfernt. Das Gerät wird aus der Intune-Verwaltung entfernt. Die Zurücksetzung eines Geräts auf Werkseinstellungen ist nützlich, bevor es an einen neuen Benutzer weitergegeben wird oder wenn es gestohlen wurde oder verloren gegangen ist. Überlegen Sie sich genau, ob Sie ein Gerät wirklich **auf Werkseinstellungen zurücksetzen** möchten. Die Daten auf dem Gerät können anschließend nicht wiederhergestellt werden.

### <a name="factory-reset-a-device"></a>Zurücksetzen eines Geräts auf Werkseinstellungen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** > **Alle Geräte**.
4. Wählen Sie den Namen des Geräts aus, das Sie auf Werkseinstellungen zurücksetzen möchten.
5. Klicken Sie im Bereich, der den Gerätenamen anzeigt, auf **Zurücksetzung auf Werkseinstellungen**.
6. Bei Windows 10 (Version 1709 oder höher) steht Ihnen ebenfalls die Option **Registrierungszustand und Benutzerkonto beibehalten** zur Verfügung. 
    
    |Während der Zurücksetzung auf Werkseinstellungen beibehalten|Nicht beibehalten|
    | -------------|------------|
    |Dem Gerät zugeordnete Benutzerkonten|Benutzerdateien|
    |Zustand des Computers \(der Domäne beigetreten, mit Azure AD verknüpft)| Vom Benutzer installierte Apps \(Store- und Win32-Apps)|
    |Anmeldung für die Verwaltung mobiler Geräte (MDM)|Geräteeinstellungen, die nicht dem Standard entsprechen|
    |Über OEM installierte Apps \(Store- und Win32-Apps)||
    |Benutzerprofil||
    |Benutzerdaten außerhalb des Benutzerprofils||
    |Automatische Anmeldung des Benutzers|| 
    
         
7. Klicken Sie auf **Ja**, um die Zurücksetzung auf Werkseinstellungen zu bestätigen.

Wenn das Gerät eingeschaltet und verbunden ist, dauert es weniger als 15 Minuten, bis die Aktion **Zurücksetzung auf Werkseinstellungen** an alle Gerätetypen weitergegeben wurde.

## <a name="remove-company-data"></a>Entfernen von Unternehmensdaten

Die Aktion **Unternehmensdaten entfernen** entfernt die Daten aus verwalteten Apps (falls zutreffend), Einstellungen und E-Mail-Profilen, die mithilfe von Intune zugewiesen wurden. Bei der Aktion **Unternehmensdaten entfernen** bleiben die persönlichen Daten des Benutzers auf dem Gerät erhalten. Das Gerät wird aus der Intune-Verwaltung entfernt. 

Die folgende Tabelle beschreibt, welche Daten entfernt werden und welche Auswirkung die Aktion **Unternehmensdaten entfernen** auf die Daten hat, die nach dem Entfernen der Unternehmensdaten auf dem Gerät verbleiben.

### <a name="ios"></a>iOS

|Datentyp|iOS|
|-------------|-------|
|Von Intune installierte Unternehmens-Apps und zugehörige Daten|Apps werden deinstalliert. Daten von Unternehmens-Apps werden entfernt.<br /><br />App-Daten aus Microsoft-Anwendungen, die die Verwaltung von mobilen Anwendungen verwenden, werden entfernt. Die App wird nicht entfernt.|
|Einstellung|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate werden entfernt und gesperrt.|
|Verwaltungs-Agent|Das Verwaltungsprofil wird entfernt.|
|E-Mail|E-Mail-Profile, die über Intune bereitgestellt werden, werden entfernt. Auf dem Gerät zwischengespeicherte E-Mails werden gelöscht.|
|Outlook|E-Mails, die über die Microsoft Outlook-App für iOS empfangen wurden, werden entfernt. Dies erfordert, dass die mobile Outlook-App als erforderliche App zunächst für iOS-Benutzer bereitgestellt wird.|
|Entfernen von Azure AD|Der Azure AD-Datensatz wird entfernt.|
|Kontakte |Kontakte, die direkt aus der App mit dem internen Adressbuch synchronisiert werden, werden entfernt. Alle Kontakte, die aus dem internen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht entfernt werden. <br /> <br />Derzeit wird nur die Outlook-App unterstützt.

### <a name="android"></a>Android

|Datentyp|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Weblinks|Entfernt.|Entfernt.|
|Nicht verwaltete Google Play-Apps|Apps und Daten bleiben installiert.|Apps und Daten bleiben installiert.|
|Nicht verwaltete Geschäftssparten-Apps|Apps und Daten bleiben installiert.|Apps werden deinstalliert, und daher werden auch die lokalen Daten der App entfernt. Daten außerhalb der App (z.B. auf einer SD-Karte) werden nicht entfernt.|
|Verwaltete Google Play-Apps|App-Daten werden entfernt. Die App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung (Mobile Application Management) außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|App-Daten werden entfernt. Die App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt, werden aber nicht entfernt.|
|Nicht verwaltete Geschäftssparten-Apps|App-Daten werden entfernt. Die App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|App-Daten werden entfernt. Die App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|
|Einstellung|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate werden gesperrt, aber nicht entfernt.|Zertifikate werden entfernt und gesperrt.|
|Verwaltungs-Agent|Die Berechtigung „Geräteadministrator“ wird gesperrt.|Die Berechtigung „Geräteadministrator“ wird gesperrt.|
|E-Mail|N/V (E-Mail-Profile werden von Android-Geräten nicht unterstützt.)|E-Mail-Profile, die über Intune bereitgestellt werden, werden entfernt. Auf dem Gerät zwischengespeicherte E-Mails werden gelöscht.|
|Outlook|Von der Outlook-App für Android empfangene E-Mails werden entfernt, allerdings nur, wenn Outlook durch MAM-Richtlinien geschützt wird. Andernfalls wird Outlook nicht zurückgesetzt, wenn das Gerät abgemeldet wird.|Von der Outlook-App für Android empfangene E-Mails werden entfernt, allerdings nur, wenn Outlook durch MAM-Richtlinien geschützt wird. Andernfalls wird Outlook nicht zurückgesetzt, wenn das Gerät abgemeldet wird.|
|Entfernen von Azure AD|Der Azure AD-Datensatz wird entfernt.|Der Azure AD-Datensatz wird entfernt.|
|Kontakte |Kontakte, die direkt aus der App mit dem internen Adressbuch synchronisiert werden, werden entfernt. Alle Kontakte, die aus dem internen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht entfernt werden. <br /> <br />Derzeit wird nur die Outlook-App unterstützt.|Kontakte, die direkt aus der App mit dem internen Adressbuch synchronisiert werden, werden entfernt. Alle Kontakte, die aus dem internen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht entfernt werden. <br /> <br />Derzeit wird nur die Outlook-App unterstützt.

### <a name="android-for-work"></a>Android for Work

Beim Entfernen von Unternehmensdaten von Android for Work-Geräten entfernt alle Daten, Apps und Einstellungen im Arbeitsprofil auf diesem Gerät. Das Gerät wird aus der Verwaltung mit Intune entfernt. Das Zurücksetzen auf Werkseinstellungen wird für Android for Work nicht unterstützt.


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
|Von Intune installierte Unternehmens-Apps und zugehörige Daten|Die Schlüssel für Dateien, die von EFS geschützt sind, werden entfernt. Der Benutzer kann die Dateien nicht öffnen.|Unternehmens-Apps werden nicht entfernt.|Ursprünglich über das Unternehmensportal installierte Apps werden deinstalliert. Daten von Unternehmens-Apps werden entfernt.|Apps werden deinstalliert. Sideload-Schlüssel werden entfernt.<br>Für Windows 10 Version 1703 (Creators Update) und höher und Office 365 werden ProPlus-Apps nicht entfernt.|
|Einstellung|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|Von der Intune-Richtlinie festgelegte Konfigurationen werden nicht mehr erzwungen. Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|Entfernt.|Nicht unterstützt.|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate werden entfernt und gesperrt.|Zertifikate werden entfernt und gesperrt.|Nicht unterstützt.|Zertifikate werden entfernt und gesperrt.|
|E-Mail|Entfernt E-Mails, für die EFS aktiviert ist. Dazu zählen E-Mails und Anhänge in der E-Mail-App für Windows.|Nicht unterstützt.|E-Mail-Profile, die über Intune bereitgestellt werden, werden entfernt. Auf dem Gerät zwischengespeicherte E-Mails werden gelöscht.|Entfernt E-Mails, für die EFS aktiviert ist. Dazu zählen E-Mails und Anhänge in der E-Mail-App für Windows. Entfernt E-Mail-Konten, die von Intune bereitgestellt wurden.|
|Entfernen von Azure AD|Nein.|Nein.|Der Azure AD-Datensatz wird entfernt.|Nicht zutreffend. Unter Windows 10 können Sie keine Unternehmensdaten von mit Azure AD verknüpften Geräten entfernen.|

### <a name="remove-company-data"></a>Entfernen von Unternehmensdaten

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Alle Geräte**.
4. Wählen Sie den Namen des Geräts aus, von dem Sie die Unternehmensdaten entfernen möchten.
5. Klicken Sie im Bereich, der den Gerätenamen anzeigt, auf **Unternehmensdaten entfernen**. Klicken Sie zum Bestätigen auf **Ja**.

Wenn das Gerät eingeschaltet und verbunden ist, dauert es weniger als 15 Minuten, bis die Aktion **Unternehmensdaten entfernen** an alle Gerätetypen weitergegeben wurde.

## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Löschen von Geräten über das Azure Active Directory-Portal

Aufgrund von Kommunikationsproblemen oder fehlenden Geräten müssen Sie möglicherweise Geräte aus Azure AD löschen. Sie können die Aktion **Löschen** aber dazu verwenden, Gerätedatensätze aus dem Azure-Portal von den Geräten zu entfernen, von denen Sie wissen, dass sie schwer zugänglich sind, und für die eine erneute Kommunikation mit Azure unwahrscheinlich ist. Die Aktion **Löschen** entfernt keine Geräte aus der Verwaltung.

1.  Melden Sie sich mit Ihren Administratoranmeldeinformationen [im Azure-Portal bei Azure Active Directory](http://aka.ms/accessaad) an. Sie können sich ebenfalls im [Office 365-Portal](https://portal.office.com) anmelden. Klicken Sie im Menü auf **Admin Center** > **Azure AD**.
2.  Erstellen Sie ein Azure-Abonnement, wenn Sie noch keins besitzen. Hierzu sollte keine Kreditkarte oder Zahlung erforderlich sein, wenn Sie ein gebührenpflichtiges Konto besitzen (klicken Sie auf den Abonnementlink **Ihr kostenloses Azure Active Directory registrieren**).
3.  Wählen Sie zuerst **Azure Active Directory** und dann Ihre Organisation aus.
4.  Wählen Sie die Registerkarte **Benutzer** aus.
5. Wählen Sie den Benutzer aus, der dem Gerät zugeordnet ist, das Sie löschen möchten.
6.  Klicken Sie auf **Geräte**.
7.  Entfernen Sie Geräte nach Bedarf. Sie können beispielsweise Geräte entfernen, die nicht mehr verwendet werden oder fehlerhafte Definitionen aufweisen.
