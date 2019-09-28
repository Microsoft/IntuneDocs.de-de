---
title: Ihr Android-Gerät ist offenbar verschlüsselt | Microsoft-Dokumentation
description: Auflösen des Verschlüsselungs Status in Unternehmensportal und Microsoft InTune-App
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: caae22e59e8adb6952e9a69ff03c575ae4467b2d
ms.sourcegitcommit: 6a946a055a2014e00a4ca9d71986727a4ebbc777
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238975"
---
# <a name="device-encrypted-but-apps-say-otherwise"></a>Gerät verschlüsselt, aber apps sagen andernfalls

Wenn Unternehmensportal oder die Microsoft InTune-App sagen, dass Ihr Gerät nicht verschlüsselt ist, Sie aber sicher sind, führen Sie die Schritte in diesem Artikel aus.  

## <a name="add-a-startup-pin"></a>Hinzufügen einer Start-PIN

Bei bestimmten Android-Geräten müssen Sie eine Start-PIN erstellen, um die Sicherheit Ihres Geräts zu gewährleisten. Der Speicherort dieser Einstellung wird in der App " **Einstellungen** " des Geräts angezeigt. Der Name und der Speicherort der Einstellung können variieren. Beispielsweise wird die Einstellung auf Samsung Galaxy S7 als **sicherer Start**bezeichnet. Um es zu aktivieren und eine Kennung zu erstellen, wechseln Sie zu **Einstellungen** > **Sperrbildschirm und Sicherheits** > **sicherer Start**.  

## <a name="encrypt-the-entire-device"></a>Verschlüsseln Sie das gesamte Gerät

Dieser Abschnitt gilt nur für die Unternehmensportal-app. Bei einigen Geräten haben Sie die Wahl: Sie können entweder das gesamte Gerät verschlüsseln oder nur den tatsächlich belegten Speicherplatz. Wählen Sie die Option zum Verschlüsseln des gesamten Geräts aus. Wenn Sie ausgewählt haben, dass nur der verwendete Speicherplatz verschlüsselt werden soll:

1. [Entfernen Sie dieses Geräts aus dem Unternehmensportal](unenroll-your-device-from-intune-android.md).
2. Entschlüsseln Sie den belegten Speicherplatz.  
3. Verschlüsseln Sie das gesamte Gerät.  
4. Registrieren Sie das Gerät erneut.  

## <a name="downgrade-your-version-of-android"></a>Herabstufen Ihrer Android-Version

Dieser Abschnitt gilt nur für die Unternehmensportal-app. Falls Ihr Gerät Ihnen die Option gibt, auf Android 6.0 downzugraden, tun Sie dies. Falls Sie versuchen, Ihr Gerät downzugraden, besteht die Gefahr, dass Daten verloren gehen. Wenden Sie sich andernfalls an die Supportabteilung Ihres Unternehmens, um dieses Problem zu beheben. Die Kontaktinformationen für die Supportabteilung Ihres Unternehmens finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="specific-manufacturer-issues"></a>Spezifische Herstellerprobleme

Einige Android-Geräte mit Version 7.0 und höher verschlüsseln Daten so, dass sie mit gewissen Android-Plattformstandards nicht kompatibel sind. Mit diesen Verschlüsselungsmethoden werden Geräteinformationen gefährdet. Dies hat zur Folge, dass diese Geräte nicht unterstützt werden.

Eine nicht vollständige Liste der unterstützten Android-Geräte finden Sie im Artikel [Unterstützte Betriebssysteme und Browser in InTune](https://docs.microsoft.com/intune/supported-devices-browsers#supported-samsung-knox-standard-devices). Wenn Ihr Gerät nicht aufgeführt ist, wenden Sie sich an den Gerätehersteller, oder wenden Sie sich an den Support.

> [!Note]
> Microsoft arbeitet mit Herstellern zusammen, um Probleme zu beheben, die wir beim Testen finden oder die Benutzer uns melden. Dieser Artikel wird aktualisiert, sobald neue Informationen verfügbar sind.

## <a name="update-devices"></a>Aktualisieren von Geräten

Wenn Sie Ihr Gerät nicht auf die neueste Version von Android aktualisiert haben, besuchen Sie die APP- **Einstellungen** Ihres Geräts, und wählen Sie **Aktualisieren**aus.  

## <a name="next-steps"></a>Nächste Schritte

Benötigen Sie weitere Unterstützung? Wenden Sie sich an den Support Ihres Unternehmens (suchen Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980) nach Kontaktinformationen) oder an das <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-Team</a>.  
