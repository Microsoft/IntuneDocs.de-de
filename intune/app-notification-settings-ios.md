---
title: 'Erstellen von App-Benachrichtigungen für iOS-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Hinzufügen oder Erstellen von App-Benachrichtigungen für iOS-Geräte in Microsoft Intune. Wählen Sie aus, welche Apps Benachrichtigungen senden, konfigurieren Sie die Benachrichtigungseinstellungen auf dem Sperrbildschirm, aktivieren Sie den Ton, wählen Sie den Typ der Warnung aus, und fügen Sie ein Badge hinzu.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 43068163c15c0588a8a6ef745d5b191f4547a94d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025704"
---
# <a name="configure-app-notifications-settings-on-ios-devices-in-intune"></a>Konfigurieren von Einstellungen der App-Benachrichtigungen für iOS-Geräte in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Konfigurieren Sie, wie installierte Apps auf einem iOS-Gerät Benachrichtigungen senden. Diese Einstellungen unterstützen überwachte Geräte, auf denen iOS 9.3 oder höher ausgeführt wird.

## <a name="add-the-app-notification"></a>Hinzufügen der App-Benachrichtigung

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie in Ihrem iOS- oder macOS-Profil auf **Gerätefeatures**. Unter [iOS- oder macOS-Gerätefeatures](device-features-configure.md) werden die Schritte zum Erstellen eines Profils aufgelistet.
3. Klicken Sie auf **App Notifications (supervised only)** (App-Benachrichtigungen (nur überwacht)) und dann auf **Hinzufügen**: ![Add app notification in iOS or macOS profile in Intune](./media/ios-macos-app-notifications.png) (App-Benachrichtigung in iOS- oder macOS-Profil in Intune hinzufügen)
4. Geben Sie die folgenden Eigenschaften ein:

   - **App-Bündel-ID**: Geben Sie die **App-Bündel-ID** der App ein, die Sie konfigurieren möchten. Hilfreiche Informationen dazu finden Sie in diesem Artikel unter **Bündel-ID-Referenz für integrierte iOS-Apps**.
   - **App-Name**: Geben Sie den Namen der App ein, die Sie konfigurieren möchten. Dieser Name wird nicht auf dem Gerät angezeigt und hilft Ihnen dabei, die App in der Liste zu identifizieren.
   - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein, die Sie konfigurieren möchten. Der Name des Herausgebers wird nicht auf dem Gerät angezeigt und hilft Ihnen nur dabei, die App in der Liste zu identifizieren.
   - **Benachrichtigungen**: Aktivieren oder deaktivieren Sie das Senden von Benachrichtigungen von der App an das Gerät. Wenn Sie diese Einstellung deaktivieren, werden die folgenden Einstellungen ebenfalls deaktiviert.
     - **In Mitteilungszentrale anzeigen**: Aktivieren Sie diese Einstellung, um zuzulassen, dass Benachrichtigungen der App in der Mitteilungszentrale angezeigt werden.
     - **In Sperrbildschirm anzeigen**: Aktivieren Sie diese Einstellung, damit Benachrichtigungen der App auf dem Sperrbildschirm des Geräts angezeigt werden.
     - **Warnungstyp**: Wählen Sie die Art der Benachrichtigung aus, die beim Entsperren des Geräts angezeigt werden soll. Diese Optionen sind verfügbar:
       - **Keine**: Es wird keine Benachrichtigung angezeigt.
       - **Banner**: Es wird kurz ein Banner mit der Benachrichtigung angezeigt.
       - **Modal**: Die Benachrichtigung wird angezeigt, und der Benutzer muss sie manuell schließen, um das Gerät weiter verwenden zu können.
     - **Badge für App-Symbol**: Aktivieren Sie diese Einstellung, um dem App-Symbol einen Badge hinzuzufügen, der darauf hinweist, dass die App eine Benachrichtigung gesendet hat.
     - **Sounds**: Aktivieren Sie diese Einstellung, um einen Sound wiederzugeben, wenn eine Benachrichtigung eintrifft.

5. Fügen Sie so viele Apps hinzu, wie Sie benötigen. Wenn Sie mit dem Hinzufügen von Apps fertig sind, klicken Sie auf **OK**.
6. Klicken Sie auf **Erstellen**, um Ihr Profil zu speichern.

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Bündel-ID-Referenz für integrierte iOS-Apps

Die folgende Liste enthält die Bündel-ID einiger gängiger integrierter iOS-Apps. Es wird empfohlen, dass Sie sich an den Softwarehersteller wenden, wenn Sie die Bündel-ID anderer Apps suchen.

|||
|-|-|
|App-Name|Bündel-ID|
|App Store|com.apple.AppStore|
|Calculator|com.apple.calculator|
|Kalender|com.apple.mobilecal|
|Kamera|com.apple.camera|
|Clock|com.apple.mobiletimer|
|Compass|com.apple.compass|
|Kontakte|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|Find Friends|com.apple.mobileme.fmf1|
|Find iPhone|com.apple.mobileme.fmip1|
|Gamecenter|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|Integrität|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|Mail|com.apple.mobilemail|
|Zuordnungen|com.apple.Maps|
|Nachrichten|com.apple.MobileSMS|
|Musik|com.apple.Music|
|News|com.apple.news|
|Hinweise|com.apple.mobilenotes|
|Zahlen|com.apple.Numbers|
|Seiten|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|Fotos|com.apple.mobileslideshow|
|Podcasts|com.apple.podcasts|
|Reminders|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|Einstellung|com.apple.Preferences|
|Stocks|com.apple.stocks|
|Tipps|com.apple.tips|
|Videos|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|Wallet|com.apple.Passbook|
|Überwachen|com.apple.Bridge|
|Weather|com.apple.weather|

## <a name="next-steps"></a>Nächste Schritte

Weisen Sie Ihren ausgewählten Gruppen das Geräteprofil zu. Eine exemplarische Vorgehensweise finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).