---
title: Registrieren von Android Enterprise-Kioskgeräten in Intune
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Android Enterprise-Kioskgeräte in Intune registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 90cd71383e8f2f82bf9fd6a3dc579c1c0a954227
ms.sourcegitcommit: d99def6e4ceb44f3e7ca10fe7cdd7f222cf814c8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42903142"
---
# <a name="set-up-enrollment-of-android-enterprise-kiosk-devices"></a>Einrichten der Registrierung von Android Enterprise-Kioskgeräten

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android unterstützt kioskartige Geräte mit unternehmenseigenen Lösungen zur einmaligen Verwendung. Solche Geräte werden für einen einzigen Zweck verwendet, dazu gehören z.B. die digitale Beschilderung, das Drucken von Tickets oder die Bestandsverwaltung. Administratoren beschränken die Verwendung eines Geräts auf eine begrenzte Anzahl von Apps und Weblinks. Außerdem wird verhindert, dass Benutzer andere Apps hinzufügen oder andere Aktionen auf dem Gerät ausführen können.

Intune unterstützt Sie beim Bereitstellen von Apps und Einstellungen für Android-Kioskgeräte. Ausführliche Informationen über Android Enterprise finden Sie in den [Voraussetzungen für Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Geräte, die Sie auf diese Weise verwalten, werden ohne Benutzerkonto in Intune registriert und keinem Endbenutzer zugeordnet. Sie sind nicht für den persönlichen Gebrauch von Anwendungen oder Apps vorgesehen, die ausführliche Voraussetzung für benutzerspezifische Kontodaten umfassen, z.B. Outlook oder Gmail.

## <a name="device-requirements"></a>Geräteanforderungen

Geräte müssen diese Anforderungen erfüllen, um als Android Enterprise-Kioskgerät verwaltet zu werden:

- Android-Betriebssystemversion 5.1 und höher.
- Geräte müssen eine Android-Verteilung ausführen, die über GMS-Konnektivität (Google Mobile Services) verfügt. Geräte müssen über GMS verfügen und dazu in der Lage sein, eine Verbindung mit GMS herzustellen.

## <a name="set-up-android-kiosk-management"></a>Einrichten der Android-Kioskverwaltung

Führen Sie die folgenden Schritte aus, um die Android-Kioskverwaltung einzurichten:

1. Sie müssen [**Microsoft Intune** als MDM-Autorität (mobile Geräteverwaltung) festlegen](mdm-authority-set.md), um die Verwaltung von mobilen Geräten vorzubereiten. Sie legen dieses Element nur einmal fest, wenn Sie die Ersteinrichtung von Intune für die Verwaltung mobiler Geräte durchführen.
2. [Verknüpfen Sie Ihr Intune-Mandantenkonto mit Ihrem Android Enterprise-Konto](connect-intune-android-enterprise.md).
3. [Erstellen Sie ein Registrierungsprofil](#create-an-enrollment-profile).
4. [Erstellen Sie eine Gerätegruppe](#create-a-device-group).
5. [Registrieren Sie die Kioskgeräte](#enroll-the-kiosk-devices).

### <a name="create-an-enrollment-profile"></a>Erstellen eines Anmeldungsprofils

Sie müssen ein Registrierungsprofil erstellen, damit Sie Ihre Kioskgeräte registrieren können. Wenn das Profil erstellt wird, wird ein Registrierungstoken (zufällige Zeichenfolge) und ein QR-Code bereitgestellt. Je nach Android-Betriebssystem und Version des Geräts können Sie entweder das Token oder den QR-Code zum [Registrieren des Kioskgeräts](#enroll-the-kiosk-devices) verwenden.

1. Navigieren Sie zum [Intune-Portal](https://portal.azure.com), und klicken Sie auf **Geräteregistrierung** > **Android-Registrierung** > **Kiosk und Taskgeräteregistrierungen**.
2. Klicken Sie auf **Erstellen**, und füllen Sie die erforderlichen Felder aus.
    - **Name:** Geben Sie einen Namen ein, den Sie zum Zuweisen des Profils zu einer dynamischen Gerätegruppe verwenden.
    - **Datum für Tokenablauf:** Das Datum, an dem das Token abläuft. Google erzwingt maximal 90 Tage.
3. Wählen Sie **Erstellen** aus, um das Profil zu speichern.

### <a name="create-a-device-group"></a>Erstellen einer Gerätegruppe

Sie können Apps und Richtlinien auf zugewiesene oder dynamische Gerätegruppen ausrichten. Sie können dynamische AAD-Gerätegruppen konfigurieren, um Geräte dynamisch aufzufüllen, die mit einem bestimmten Registrierungsprofil registriert werden, indem Sie die folgenden Schritte ausführen:

1. Navigieren Sie zum [Intune-Portal](https://portal.azure.com), und klicken Sie auf **Gruppen** > **Alle Gruppen** > **Neue Gruppe**.
2. Füllen Sie auf dem Blatt **Gruppe** die erforderlichen Felder wie folgt aus:
    - **Gruppentyp:** Sicherheit
    - **Gruppenname:** Geben Sie einen aussagekräftigen Namen ein (z.B. Factory 1-Geräte)
    - **Mitgliedschaftstyp:** Dynamisches Gerät
3. Klicken Sie auf **Dynamische Abfrage hinzufügen**.
4. Füllen Sie die Felder auf dem Blatt **Dynamische Mitgliedschaftsregeln** wie folgt aus:
    - **Regel für dynamische Mitgliedschaft hinzufügen:** Einfache Regel
    - **Geräte hinzufügen, wobei:** enrollmentProfileName
    - Klicken Sie im mittleren Feld auf **Übereinstimmung**.
    - Geben Sie im letzten Feld den Namen des Registrierungsprofils ein, das Sie zuvor erstellt haben.
5. Klicken Sie auf **Abfrage hinzufügen** > **Erstellen**.

### <a name="replace-or-remove-tokens"></a>Ersetzen oder Entfernen von Token

Sie können Token und QR-Codes ersetzen oder entfernen.

- **Token ersetzen:** Sie können ein neues Token bzw. einen neuen QR-Code generieren, wenn das Ablaufdatum sich nähert, indem Sie „Token ersetzen“ verwenden.
- **Token widerrufen:** Sie können das Token bzw. den QR-Code sofort ablaufen lassen. Von diesem Zeitpunkt an kann das Token bzw. der QR-Code nicht mehr verwendet werden. Sie können diese Option verwenden, wenn Sie:
    - das Token bzw. den QR-Code versehentlich mit nicht autorisierten Personen geteilt haben
    - alle Registrierungen abgeschlossen haben und das Token bzw. den QR-Code nicht mehr benötigen

Das Ersetzen oder Widerrufen eines Tokens bzw. QR-Codes hat keine Auswirkungen auf Geräte, die bereits registriert sind.

1. Navigieren Sie zum [Intune-Portal](https://portal.azure.com), und klicken Sie auf **Geräteregistrierung** > **Android-Registrierung** > **Kiosk und Taskgeräteregistrierungen**.
2. Wählen Sie das Profil aus, mit dem Sie arbeiten möchten.
3. Klicken Sie auf **Token**.
4. Klicken Sie auf **Token ersetzen**, um das Token zu ersetzen.
5. Klicken Sie auf **Token widerrufen**, um das Token zu widerrufen.

## <a name="enroll-the-kiosk-devices"></a>Registrieren der Kioskgeräte

Nachdem Sie das Registrierungsprofil und die dynamische Gerätegruppe erstellt haben, können Sie Ihre Kioskgeräte registrieren. Wie Sie Ihre Android-Geräte registrieren hängt vom Betriebssystem ab.

| Registrierungsmethode | Niedrigste unterstützte Android-Betriebssystemversion |
| ----- | ----- |
| Near Field Communication | 5.1 |
| Token-Eingabe | 6.0 |
| QR-Code | 7.0 |
| Zero-Touch | 8.0 bei beteiligten Herstellern |

### <a name="enroll-by-using-near-field-communication-nfc"></a>Registrieren mit NFC (Near Field Communication)

Bei Android 5.1- und höheren Geräten, die NFC unterstützen, können Sie Ihre Geräte bereitstellen, indem Sie ein speziell formatiertes NFC-Tag erstellen. Sie können Ihre eigene App oder ein beliebiges NFC-Tagerstellungstool verwenden. Weitere Informationen finden Sie in der [Google-Dokumentation zur Android-Verwaltungs-API](https://developers.google.com/android/management/provision-device#nfc_method).

### <a name="enroll-by-using-a-token"></a>Registrieren mithilfe eines Tokens

Für Android 6-Geräte und höher können Sie das Token zum Registrieren des Geräts verwenden. Bei Android 6.1 und höheren Versionen kann bei Verwendung der Registrierungsmethode **aft#setup** auch der QR-Code-Scan genutzt werden.

1. Schalten Sie das Gerät ein, das Sie auf Werkseinstellungen zurücksetzen möchten.
2. Wählen Sie auf dem **Willkommenssbildschirm** Ihre Sprache aus.
3. Stellen Sie eine **WLAN**-Verbindung her, und tippen Sie dann auf **WEITER**.
4. Akzeptieren Sie Nutzungsbedingungen von Google, und tippen Sie dann auf **WEITER**.
5. Geben Sie auf dem Google-Anmeldebildschirm anstelle eines Gmail-Kontos **afw#setup** ein, und tippen Sie dann auf **WEITER**.
6. Tippen Sie bei der **Android-Geräterichtlinien**-App auf **INSTALLIEREN**.
7. Fahren Sie mit der Installation dieser Richtlinie fort.  Einige Geräte erfordern möglicherweise, dass zusätzliche Lizenzbedingungen akzeptiert werden. 
8. Lassen Sie auf dem Bildschirm **Dieses Gerät registrieren** zu, dass Ihr Gerät den QR-Code scannen kann, oder geben Sie das Token manuell ein.
9. Führen Sie die angezeigten Eingabeaufforderungen durch, um die Registrierung abzuschließen. 

### <a name="enroll-by-using-a-qr-code"></a>Registrieren mithilfe eines QR-Codes

Auf Android 7-Geräten und höher können Sie den QR-Code aus dem Registrierungsprofil scannen, um das Gerät zu registrieren.

> [!Note]
> Bei bestimmten Zoomeinstellungen des Browsers können Geräte möglicherweise keine QR-Codes scannen. Dieses Problem lässt sich durch die Erhöhung des Zooms beheben.

1. Tippen Sie mehrmals auf den ersten Bildschirm, der nach einer Zurücksetzung auf die Werkseinstellungen angezeigt wird, um einen QR-Scanner auf dem Android-Gerät zu starten.
2. Auf Android 7- und 8-Geräten werden Sie dazu aufgefordert, einen QR-Scanner zu installieren. Auf Android 9-Geräten und höher ist bereits ein QR-Scanner installiert.
3. Verwenden Sie den QR-Scanner zum Scannen des QR-Codes vom Registrierungsprofil, und führen Sie anschließend die angezeigten Eingabeaufforderungen aus, um die Registrierung durchzuführen.

### <a name="enroll-by-using-google-zero-touch"></a>Registrieren mithilfe von Google Zero-Touch

Das Gerät muss das Zero-Touch-System von Google unterstützen und einem Lieferanten zugeordnet sein, der Teil des Diensts ist, damit das System verwendet werden kann.  Weitere Informationen finden Sie auf der [Website zum Zero-Touch-Programm von Google](https://www.android.com/enterprise/management/zero-touch/). 


1. Erstellen Sie eine neue Konfiguration in der Zero-Touch-Konsole.
2. Wählen Sie in der EMM DPC-Dropdownliste **Microsoft Intune** aus.
3. Kopieren Sie den folgenden JSON-Code, und fügen Sie ihn in der Zero-Touch-Konsole von Google in das Feld „DPC-Extras“ ein. Ersetzen Sie die Zeichenfolge *YourEnrollmentToken* mit dem Registrierungstoken, das Sie als Teil Ihres Registrierungsprofils erstellt haben. Stellen Sie sicher, dass das Registrierungstoken mit doppelten Anführungszeichen umgeben ist.

```
{ 
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME": "com.google.android.apps.work.clouddpc/.receivers.CloudDeviceAdminReceiver", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_SIGNATURE_CHECKSUM": "I5YvS0O5hXY46mb01BlRjq4oJJGs2kuUcHvVkAPEXlg", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION": "https://play.google.com/managed/downloadManagingApp?identifier=setup", 

    "android.app.extra.PROVISIONING_ADMIN_EXTRAS_BUNDLE": { 
        "com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "YourEnrollmentToken" 
    } 
} 
```
4. Wählen Sie **Anwenden** aus.

## <a name="managing-apps-on-android-kiosk-devices"></a>Verwalten von Apps auf Android-Kioskgeräten

Nur Apps, deren Zuweisungstyp auf [Erforderlich](apps-deploy.md#to-assign-an-app) festgelegt ist, können auf Android-Kioskgeräten installiert werden. Apps werden über den verwalteten Google Play Store auf die gleiche Weise installiert wie bei Android-Arbeitsprofilgeräten.

Apps werden auf verwalteten Geräten automatisch aktualisiert, wenn der App-Entwickler ein Update auf Google Play veröffentlicht.

Sie können eine der folgenden Aktionen durchführen, um eine App von Android-Kioskgeräten zu entfernen:
-   Löschen Sie die erforderliche App-Bereitstellung.
-   Erstellen Sie eine Deinstallationsdatei für die App.


## <a name="next-steps"></a>Nächste Schritte
- [Bereitstellen von Android-Kiosk-Apps](apps-deploy.md)
- [Hinzufügen von Konfigurationsrichtlinien für einen Android-Kiosk](device-profiles.md)
