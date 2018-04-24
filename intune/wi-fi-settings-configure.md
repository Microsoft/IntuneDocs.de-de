---
title: So konfigurieren Sie Intune-WLAN-Einstellungen
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie mit Microsoft Intune WLAN-Einstellungen auf Geräten konfigurieren, die Sie verwalten.
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
ms.openlocfilehash: 9a550e2963fa60a91db3ef63f7771bc4ca352d98
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>So konfigurieren Sie WLAN-Einstellungen in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Verwenden Sie WLAN-Profile in Microsoft Intune, um Benutzern und Geräten in Ihrer Organisation Einstellungen für Drahtlosnetzwerke zuzuweisen. Wenn Sie ein WLAN-Profil zuweisen, erhalten Ihre Benutzer Zugriff auf Ihr Unternehmens-WLAN, ohne es selbst konfigurieren zu müssen.

Beispiel: Sie installieren ein neues WLAN mit dem Namen „Contoso Wi-Fi“ und möchten alle iOS-Geräte so einrichten, dass sie eine Verbindung mit diesem Netzwerk herstellen können. Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie ein WLAN-Profil mit den Einstellungen, die zum Verbinden mit dem Drahtlosnetzwerk „Contoso Wi-Fi“ erforderlich sind.
2. Weisen Sie das Profil einer Gruppe zu, die alle Benutzer von iOS-Geräten enthält.
3. Auf den Geräten der Benutzer erscheint das Netzwerk „Contoso Wi-Fi“ in der Liste der Drahtlosnetzwerke, und es kann bequem eine Verbindung mit diesem Netzwerk hergestellt werden.

## <a name="supported-device-platforms"></a>Unterstützte Geräteplattformen

WLAN-Profile unterstützen folgende Geräteplattformen:

- Android 4 und höher
- Android for Work
- iOS 8.0 und höher
- macOS (Mac OS X 10.9 und höher)

Auf Geräten mit Windows 8.1, Windows 10, Windows 10 Mobile und Windows Holographic for Business können Sie eine WLAN-Konfiguration importieren, die zuvor von einem anderen Gerät exportiert wurde.

Anhand der Informationen in diesem Thema lernen Sie die Grundlagen zum Konfigurieren von WLAN-Profilen kennen. In den weiterführenden Themen zu den einzelnen Plattformen erfahren Sie etwas über Besonderheiten der jeweiligen Geräte.

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>Erstellen eines Geräteprofils mit WLAN-Einstellungen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Gerätekonfiguration**.
2. Klicken Sie im Bereich **Gerätekonfiguration** im Abschnitt **Verwalten** auf **Profile**.
3. Klicken Sie im Bereich „Profile“ auf **Profil erstellen**.
4. Geben Sie im Bereich **Profil erstellen** einen **Namen** und eine **Beschreibung** für das WLAN-Profil ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die Sie WLAN-Einstellungen anwenden möchten. Derzeit können Sie eine der folgenden Plattformen für die WLAN-Einstellungen auswählen:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 und höher**
    - **Windows 10 und höher**

   > [!IMPORTANT]
   > Wenn Sie ein Profil für Windows 10-Geräte einschließlich Windows Holographic for Business erstellen, müssen Sie die Plattform **Windows 8.1 und höher** auswählen. Die Plattform **Windows 10 und höher** schließt keinen WLAN-Profiltyp ein. 

6. Wählen Sie für Apple- oder Android-Geräte in der Dropdownliste **WLAN-Typ** die Option **Standard** oder **Enterprise**. Mithilfe von **Standard** können Sie grundlegende Eigenschaften wie den Netzwerknamen und die SSID angeben. Mit **Enterprise** können Sie detailliertere Informationen angeben, z.B. das Extensible Authentication Protocol (EAP), sofern Ihr WLAN dieses Protokoll verwendet. 

   Mit dem Profil **WLAN (Import)** (für Windows 8.1 und höher) können Sie WLAN-Einstellungen als XML-Datei importieren, die Sie zuvor von einem anderen Gerät exportiert haben.
1. Die konfigurierbaren Einstellungen variieren je nach der ausgewählten Plattform. In den folgenden Themen finden Sie ausführliche Informationen zu den Einstellungen für die einzelnen Plattformen:
    - [Einstellungen für Android und Android for Work](wi-fi-settings-android.md)
    - [Einstellungen für iOS](wi-fi-settings-ios.md)
    - [Einstellungen für macOS](wi-fi-settings-macos.md)
    - [Einstellungen für Windows 8.1 und höher](wi-fi-settings-import-windows-8-1.md) (einschließlich Windows Holographic for Business)
1. Wechseln Sie anschließend wieder zum Bereich **Profil erstellen**, und klicken Sie auf **Erstellen**.

Das Profil wird erstellt und im Bereich „Profilliste“ angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie fortfahren und dieses Profil Gruppen zuweisen möchten, lesen Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md) nach.
