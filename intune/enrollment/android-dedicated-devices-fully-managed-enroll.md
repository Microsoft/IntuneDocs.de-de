---
title: Registrierung dedizierter Android Enterprise-Geräte oder vollständig verwalteter Geräte in Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie dedizierte Android Enterprise-Geräte und vollständig verwaltete Geräte in Intune registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ad96c80a2cad71feec2afdfa87da767aa72fdb1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505612"
---
# <a name="enroll-your-android-enterprise-dedicated-devices-or-fully-managed-devices"></a>Registrieren Ihrer dedizierten Android Enterprise-Geräte oder vollständig verwalteten Geräte

Nachdem Sie Ihre [dedizierten Android Enterprise-Geräte](android-kiosk-enroll.md) oder [vollständig verwalteten](android-fully-managed-enroll.md) Geräte in Intune eingerichtet haben, können Sie sie registrieren. Die Intune-Registrierung für dedizierte Geräte und vollständig verwaltete Geräte beginnt mit dem Zurücksetzen auf die Werkseinstellungen. Wie Sie Ihre Android Enterprise-Geräte registrieren, hängt vom Betriebssystem ab.

| Registrierungsmethode | Mindestversion des Android-Betriebssystems für dedizierte und vollständig verwaltete Geräte |
| ----- | ----- |
| Near Field Communication | 5.1 |
| Token-Eingabe | 6.0 |
| QR-Code | 7.0 |
| Zero-Touch  | 8.0\* |

\* Bei beteiligten Herstellern

## <a name="enroll-by-using-near-field-communication-nfc"></a>Registrieren mit NFC (Near Field Communication)

Bei Geräten, die NFC unterstützen, können Sie Ihre Geräte bereitstellen, indem Sie ein speziell formatiertes NFC-Tag erstellen. Sie können Ihre eigene App oder ein beliebiges NFC-Tagerstellungstool verwenden. Weitere Informationen finden Sie im Blogbeitrag [NFC-based Android Enterprise device enrollment with Microsoft Intune (NFC-basierte Android Enterprise-Geräteregistrierung mit Microsoft Intune)](https://blogs.technet.microsoft.com/cbernier/2018/10/15/nfc-based-android-enterprise-device-enrollment-with-microsoft-intune/) und in der Google-Dokumentation zur [Android Management API](https://developers.google.com/android/management/provision-device#nfc_method).

## <a name="enroll-by-using-a-token"></a>Registrieren mithilfe eines Tokens

Für Android 6-Geräte und höher können Sie das Token zum Registrieren des Geräts verwenden. Bei Android 6.1 und höheren Versionen kann bei Verwendung der Registrierungsmethode **afw#setup** auch der QR-Code-Scan genutzt werden.

1. Schalten Sie das zurückgesetzte Gerät ein.
2. Wählen Sie auf dem **Willkommenssbildschirm** Ihre Sprache aus.
3. Stellen Sie eine **WLAN**-Verbindung her, und tippen Sie dann auf **WEITER**.
4. Akzeptieren Sie Nutzungsbedingungen von Google, und tippen Sie dann auf **WEITER**.
5. Geben Sie auf dem Google-Anmeldebildschirm anstelle eines Gmail-Kontos **afw#setup** ein, und tippen Sie dann auf **WEITER**.
6. Tippen Sie bei der **Android-Geräterichtlinien**-App auf **INSTALLIEREN**.
7. Fahren Sie mit der Installation dieser Richtlinie fort.  Einige Geräte erfordern möglicherweise, dass zusätzliche Lizenzbedingungen akzeptiert werden.
8. Lassen Sie auf dem Bildschirm **Dieses Gerät registrieren** zu, dass Ihr Gerät den QR-Code scannen kann, oder geben Sie das Token manuell ein.
9. Führen Sie die angezeigten Eingabeaufforderungen durch, um die Registrierung abzuschließen.

## <a name="enroll-by-using-a-qr-code"></a>Registrieren mithilfe eines QR-Codes

Auf Android 7-Geräten und höher können Sie den QR-Code aus dem Registrierungsprofil scannen, um das Gerät zu registrieren.

> [!Note]
> Bei bestimmten Zoomeinstellungen des Browsers können Geräte möglicherweise keine QR-Codes scannen. Dieses Problem lässt sich durch die Erhöhung des Zooms beheben.

1. Tippen Sie mehrmals auf den ersten Bildschirm, der nach einer Zurücksetzung angezeigt wird, um einen QR-Scanner auf dem Android-Gerät zu starten.
2. Auf Android 7- und 8-Geräten werden Sie dazu aufgefordert, einen QR-Scanner zu installieren. Auf Android 9-Geräten und höher ist bereits ein QR-Scanner installiert.
3. Verwenden Sie den QR-Scanner zum Scannen des QR-Codes vom Registrierungsprofil, und führen Sie anschließend die angezeigten Eingabeaufforderungen aus, um die Registrierung durchzuführen.

## <a name="enroll-by-using-google-zero-touch"></a>Registrieren mithilfe von Google Zero-Touch

Das Gerät muss das Zero-Touch-System von Google unterstützen und einem Lieferanten zugeordnet sein, der Teil des Diensts ist, damit das System verwendet werden kann.  Weitere Informationen finden Sie auf der [Website zum Zero-Touch-Programm von Google](https://www.android.com/enterprise/management/zero-touch/).

1. Erstellen Sie eine neue Konfiguration in der Zero-Touch-Konsole.
2. Wählen Sie in der EMM DPC-Dropdownliste **Microsoft Intune** aus.
3. Kopieren Sie den folgenden JSON-Code, und fügen Sie ihn in der Zero-Touch-Konsole von Google in das Feld „DPC-Extras“ ein. Ersetzen Sie die Zeichenfolge *YourEnrollmentToken* mit dem Registrierungstoken, das Sie als Teil Ihres Registrierungsprofils erstellt haben. Stellen Sie sicher, dass das Registrierungstoken mit doppelten Anführungszeichen umgeben ist.

    ```json
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


## <a name="next-steps"></a>Nächste Schritte
- [Bereitstellen von Android-Apps](../apps/apps-deploy.md)
- [Hinzufügen von Android-Konfigurationsrichtlinien](../configuration/device-profiles.md)

