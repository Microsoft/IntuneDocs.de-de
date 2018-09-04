---
title: Verhindern des E-Mail-Zugriffs durch Energieoptimierung | Microsoft-Dokumentation
description: Hier erfahren Sie, wie die Energieoptimierung für Android ausgeschaltet wird, um sicherzustellen, dass Sie Ihre E-Mail erhalten.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ad713f18-40a9-421f-aa2b-f8c21028d57c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 33b6199c25e9e36b65dfe2ca819640fa614e68b6
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "43148222"
---
# <a name="outlook-wont-sync-managed-email-when-battery-optimization-for-android-is-turned-on"></a>Bei aktivierter Akkuoptimierung für Android synchronisiert Outlook keine verwalteten E-Mails

> [!IMPORTANT]
> Dieses Problem wird hier dokumentiert, da diesbezüglich vermehrt Kundenberichte eingetroffen sind. Wenn das Problem nach Ausführung dieser Schritte weiterhin auftritt, wenden Sie sich für zusätzliche Hilfe an [die Supportabteilung Ihres Unternehmens](https://go.microsoft.com/fwlink/?linkid=2010980).

Durch die Registrierung Ihres Geräts bei Intune können Sie auf Unternehmensressourcen zugreifen. Eine der gebräuchlichsten Ressourcen ist der E-Mail-Zugriff. Ein Problem, das bei Android-Geräten beim Zugriff auf E-Mails über Outlook beobachtet wurde, tritt bei aktivierter Akkuoptimierung auf. Die Akkuoptimierung wird möglicherweise automatisch aktiviert, damit Ihr Gerät so lange wie möglich eingeschaltet bleibt. Auf diese Weise kann die Akkuoptimierung teilweise hilfreich sein, da sie versucht, das automatische Herunterladen von E-Mails zu beenden.

Das Microsoft Intune-Team arbeitet aktiv an einer Lösung für dieses Problem. Eine Möglichkeit zur Verhinderung, dass das Gerät in den niedrigen Energiestatus wechselt, besteht darin, sicherzustellen, dass der Akkustand immer über 30 % liegt. Sie müssen das Unternehmensportal und Outlook aus der Liste der Apps entfernen, die von den Einstellungen für die Akkuoptimierung und den Energiesparmodus betroffen sind, damit das Problem im niedrigen Energiestatus nicht auftritt.

Es gibt viele Android-Geräte von den verschiedensten Herstellern. Leider können nicht für jedes Gerät die genauen auszuführenden Schritte dokumentiert werden. Möglicherweise müssen Sie diese Aktion nur in den Systemeinstellungen ausführen oder auch in bestimmten herstellerspezifischen Einstellungen. Wir haben einige gängige Beispiele dafür bereitgestellt, wie Sie dieses Problem auf Android-Geräten beheben können.

## <a name="unmodified-android-devices"></a>Unveränderte Android-Geräte

Viele Hersteller führen Änderungen an ihren Android-Geräten durch. Dadurch können sich bestimmte Interaktionen mit dem Gerät, z.B. Designs und Benachrichtigungen, ändern. Google nimmt in der Regel keine Änderungen dieser Art an den zugehörigen Telefonen vor. Beispiel: Auf einem Google Pixel-Gerät mit Android 7.0 oder höher würden Sie folgende Schritte ausführen, um diese Apps aus der Akkuoptimierung zu entfernen:

1. Öffnen Sie **Einstellungen**.
2. Tippen Sie auf **Akku** > **Weitere** > **Akkuoptimierung**.
3. Tippen Sie auf den Pfeil nach unten und anschließend auf **Nicht optimiert**.
4. Wählen Sie die Unternehmensportal-App und die Outlook-App aus, und deaktivieren Sie die Akkuoptimierung.

## <a name="samsung-devices"></a>Samsung-Geräte

Bei anderen Android-Gerätetypen, z.B. Samsung-Geräten mit Android 7.0 oder höher, müssen Sie andere Schritte ausführen, um die Outlook- und die Unternehmensportal-App aus der Akkuoptimierung zu entfernen.

1. Öffnen Sie **Einstellungen**.
2. Tippen Sie auf **Menü (...)** > **Beschränkter Zugriff** > **Akkunutzung optimieren**.
3. Wählen Sie **Alle Apps** aus der Dropdown-Liste aus.
4. **Deaktivieren** Sie die Umschalttaste neben der Unternehmensportal- und der Outlook-App, um die Akkuoptimierung zu deaktivieren.

Wenn Sie ein Samsung-Gerät mit einer älteren Android-Version verwenden, müssen Sie folgende Schritte ausführen, um diese Apps aus dem Energiesparmodus zu entfernen.

1. Öffnen Sie **Einstellungen**.
2. Tippen Sie auf **Gerätewartung** > **Akku** > **Nicht überwachte Apps**.
3. Tippen Sie auf **Apps hinzufügen**.
4. Wählen Sie die Unternehmensportal- und die Outlook-App aus, und tippen Sie auf **Fertig**.

## <a name="oneplus-devices"></a>OnePlus-Geräte

Diese Einstellungen können beispielsweise auch über die Suche in den Systemeinstellungen lokalisiert werden. Bei einem OnePlus 3-Gerät mit Android 7.1.1 würden Sie beispielsweise folgende Schritte ausführen: 

1. Öffnen Sie **Systemeinstellungen**. 
2. Tippen Sie auf die Schaltfläche **Suchen**. Diese ähnelt einer Lupe im oberen rechten Bildschirmbereich. 
3. Geben Sie in das Suchfeld **Akkuoptimierung** ein, und wählen Sie anschließend in der Anzeige **Einstellungen** die Option **Akkuoptimierung** aus. 
4. Tippen Sie auf **Akku** > **Akkuoptimierung**.
5. Wählen Sie die Unternehmensportal- und die Outlook-App aus, und wählen Sie anschließend **Nicht optimieren** aus. Tippen Sie auf **Fertig**.

<!--On a OnePlus 5 device with Android 7.1.1, you would follow these steps to remove these apps from battery optimization:
1. Open **Settings**.
2. Tap **Battery** > **Battery optimization**.
3. Select the Company Portal and Outlook apps, then select **Don’t optimize**. Tap **Done**.-->

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).
