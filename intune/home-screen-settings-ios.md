---
title: Einstellungen des Layouts des Microsoft Intune-Startbildschirms für iOS-Geräte
titleSuffix: ''
description: Erfahren Sie mehr zu den Einstellungen in Microsoft Intune, die Sie verwenden können, um den Startbildschirm anzupassen und an iOS-Geräte anzudocken.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 56527da7ac8c2ed00a4b33049c8ba4ad03299976
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
---
# <a name="microsoft-intune-home-screen-layout-settings-for-devices-running-ios"></a>Einstellungen des Layouts des Microsoft Intune-Startbildschirms für iOS-Geräte

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Verwenden Sie diese Einstellungen, um das Layout von Apps und Ordner auf dem iOS-Start- und Dockbildschirm zu konfigurieren.

iOS-Geräte, denen ein Profil zugewiesen ist, müssen sich im überwachten Modus befinden und iOS 9.3 oder höher ausführen.

1. Navigieren Sie in [Intune im Azure-Portal](https://portal.azure.com) [im Gerätekonfigurationsbereich zu **Gerätefunktionen**](device-features-configure.md).
2. Wählen Sie im Bereich **Gerätefunktionen** die Option **Layout des Startbildschirms (nur überwacht)** aus.
3. Wählen Sie im Bereich **Layout des Startbildschirms (nur überwacht)** aus, ob Sie das Layout des **Docks** oder der **Seiten** konfigurieren möchten.

## <a name="add-items-to-the-dock"></a>Hinzufügen von Elementen zum Dock

Im Bereich **Dock** können Sie dem Dock des iOS-Bildschirms bis zu sechs Elemente oder Ordner hinzufügen. Allerdings unterstützen viele Geräte weniger Elemente – z.B. unterstützen iPhone-Geräte bis zu vier Elemente. In diesem Fall werden nur die ersten vier Elemente, die Sie konfiguriert haben, auf dem Gerät angezeigt.

1. Wählen Sie **Hinzufügen**, um dem Dock ein Element hinzuzufügen.
2. Wählen Sie im Bereich **Zeile hinzufügen** aus, ob Sie eine **App** oder einen **Ordner** hinzufügen möchten.
3. Konfigurieren Sie mit den Informationen in diesem Thema die Apps und Ordner, die im Dock angezeigt werden sollen.
4. Fügen Sie nach Bedarf weitere Elemente hinzu. Klicken Sie anschließend in jedem Bereich auf **OK**, bis Sie sich wieder im Bereich **Profil erstellen** befinden. Wählen Sie **Erstellen** aus.

>[!TIP]
> In jedem Startbildschirm und auf allen Seiten können Sie Elemente mittels Ziehen und Ablegen sortieren.

### <a name="example"></a>Beispiel

In diesem Beispiel haben Sie den Dockbildschirm so konfiguriert, dass nur die Apps „Safari“, „Mail“ und „Stocks“ angezeigt werden. In der folgenden Abbildung wird die App „Mail“ ausgewählt, um ihre Eigenschaften zu veranschaulichen:

![Beispiel für iOS-Dockeinstellungen](./media/FfFiUcP.png)

Wenn Sie einem iPhone die Richtlinie zuweisen, ist das Ergebnis ein Dock, das etwa so aussieht:

![Beispiel für das iOS-Docklayout eines iPhones](./media/bAgCe8F.png)

## <a name="add-home-screen-pages"></a>Hinzufügen von Startbildschirmseiten

Fügen Sie die Seiten hinzu, die auf dem Startbildschirm angezeigt werden sollen, und die Apps, die auf jeder Seite angezeigt werden. Apps, die Sie einer Seite hinzufügen, sind in der Reihenfolge, in der sie in der Liste angegeben sind, von links nach rechts angeordnet. Wenn Sie mehr Apps hinzufügen, als auf eine Seite passen, werden die Apps auf eine nachfolgende Seite verschoben.

1. Wählen Sie im Bereich **Seiten** die Option **Hinzufügen** aus.
2. Geben Sie im Bereich **Zeile hinzufügen** einen **Seitennamen** ein. Dieser Name wird im Azure-Portal zur Referenz verwendet und auf dem iOS-Gerät *nicht angezeigt*.
3. Wählen Sie **Hinzufügen** aus, und wählen Sie dann, ob Sie der Seite eine **App** oder einen **Ordner** hinzufügen möchten.
4. Konfigurieren Sie mit den Informationen in diesem Thema die Apps und Ordner, die auf der Seite angezeigt werden sollen.

### <a name="example"></a>Beispiel

In diesem Beispiel haben Sie eine neue Seite mit dem Namen **Contoso** konfiguriert. Diese Seite zeigt nur die Apps „Find Friends“ und „Settings“ an. In der folgenden Abbildung wird die App „Settings“ ausgewählt, um ihre Eigenschaften zu veranschaulichen:

![Beispiel für Einstellungen des iOS-Startbildschirms](./media/Jc2OxyX.png)

Wenn Sie einem iPhone die Richtlinie zuweisen, ist das Ergebnis eine Seite, die etwa so aussieht:

![iOS-Gerät mit geändertem Startbildschirm](./media/Bd37PHa.png)

## <a name="how-to-add-an-app-to-the-list"></a>Hinzufügen einer App zur Liste

1. Geben Sie den **App-Namen** ein. Dieser Name wird im Azure-Portal zur Referenz verwendet und auf dem iOS-Gerät *nicht angezeigt*.
2. Geben Sie die **App-Bündel-ID** der App ein, die Sie anzeigen möchten. Hilfe finden Sie weiter unten in diesem Thema unter **Bündel-ID-Referenz für integrierte iOS-Apps**.
3. Klicken Sie auf **OK**, und fahren Sie mit dem Hinzufügen von Elementen bis zu einem Maximum von **6** für das Gerätedock und **60** für eine Geräteseite fort.
4. Klicken Sie zum Abschluss auf **OK**.

## <a name="how-to-add-a-folder-to-the-list"></a>Hinzufügen eines Ordners zur Liste

Apps, die Sie einer Seite in einem Ordner hinzufügen, sind in der Reihenfolge, in der sie in der Liste angegeben sind, von links nach rechts angeordnet. Wenn Sie mehr Apps hinzufügen, als auf eine Seite passen, werden die Apps auf eine nachfolgende Seite verschoben.

1. Geben Sie den **Ordnernamen** ein. Dieser Name wird Benutzern auf ihren Geräten angezeigt.
2. Wählen Sie **Hinzufügen**, um eine Seite im Ordner zu erstellen. Sie können bis zu 20 Seiten hinzufügen.
3. Geben Sie im Bereich **Zeile hinzufügen** einen Namen für die Seite ein. Dieser Name wird im Azure-Portal zur Referenz verwendet und auf dem iOS-Gerät *nicht angezeigt*.
3. Geben Sie den **App-Namen** ein. Dieser Name wird im Azure-Portal zur Referenz verwendet und auf dem iOS-Gerät *nicht angezeigt*.
2. Geben Sie die **App-Bündel-ID** der App ein, die Sie anzeigen möchten. Hilfe finden Sie unter **Hinzufügen einer App zur Liste**.
3. Wählen Sie **Hinzufügen** aus. Sie können bis zu 60 Elemente hinzufügen.
4. Klicken Sie zum Abschluss auf **OK**.


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Bündel-ID-Referenz für integrierte iOS-Apps

Diese Liste zeigt die Bündel-ID einiger gängiger integrierter iOS-Apps. Um die Bündel-ID von anderen Apps zu finden, wenden Sie sich an den Softwarehersteller.

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

Sie können nun das Geräteprofil den von Ihnen ausgewählten Gruppen zuweisen. Weitere Informationen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).
