---
title: Verschlüsseln von Android-Gerät für Intune | Microsoft-Dokumentation
description: Schritte zum Aktivieren von Intune benötigte Verschlüsselung Android-Gerät
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfc17c60412a1cfe90693216caa69ada3d2d2c9a
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545256"
---
# <a name="encrypting-your-android-device"></a>Verschlüsseln Ihres Android-Geräts

Geräteverschlüsselung schützt die Dateien und Ordner vor nicht autorisiertem Zugriff, wenn Ihr Gerät verloren geht oder gestohlen wird. Nachdem Sie geräteverschlüsselung aktivieren, werden nur Personen mit dem korrekten Kennwort oder Pin auf Ihrem Gerät anmelden können. 

Bevor Sie schulkonto oder Geschäfts-Ressourcen zugreifen können, Ihre Organisation müssen Sie möglicherweise Ihr Android-Gerät zu verschlüsseln. Einige neuere Android-Geräte werden standardmäßig verschlüsselt Out-of-the-Box.  

## <a name="turn-on-encryption"></a>Verschlüsselung aktivieren

Wenn die Unternehmensportal-App oder der Microsoft Intune-app zum Verschlüsseln Ihres Geräts aufgefordert werden, führen Sie folgende Schritte aus. 

> [!Note]
> Bestimmte Android-Geräte von Huawei, Vivo und OPPO, können nicht verschlüsselt werden. [Hier](your-device-appears-encrypted-but-cp-says-otherwise-android.md) erfahren Sie mehr.  

1. Legen Sie eine Geräte-Sperrbildschirm.  
    ein. Wechseln Sie zu **Einstellungen** > **Lock Screen and Security** > **Screen lock** (Sperrbildschirm und Sicherheit > Bildschirmsperre).  
    b. Wählen Sie entweder **PIN**, **Kennwort**, oder **Muster**.  
    c. Führen Sie die Anweisungen auf dem Bildschirm so konfigurieren Sie Ihre Bildschirmsperre ein.  

2. Wechseln Sie zurück zur **Sperrbildschirm und Sicherheit** , und wählen Sie **sicherer Start**.
3. Wählen Sie **PIN anfordern, wenn das Gerät eingeschaltet** > **OK**.
4. Geben Sie Ihre PIN zur Bestätigung und zum Verschlüsseln Ihres Geräts aus.
5. Öffnen Sie die Unternehmensportal-App oder Microsoft Intune-app.
    * Unternehmensportal-Benutzer: Wählen Sie Ihr Gerät aus, und tippen Sie auf **Geräteeinstellungen überprüfen**. 
    * Microsoft Intune-Benutzer: Sie müssen warten, bis der Seite wird aktualisiert, aber wenn dies der Fall, sollten Ihre Verschlüsselungsstatus zu kompatiblen ändern.  

Geräte mit Android 4.4 oder früheren möglicherweise nicht die **sicherer Start** Option. In diesem Fall führen Sie die folgenden Schritte aus, zum Verschlüsseln des Geräts.

1. Wechseln Sie zu **Einstellungen** > **Sicherheit** > **Gerät verschlüsseln**. Auf dem Bildschirm Bezeichnungen variieren zwischen Android-Geräte. Wenn Sie nicht sehen die **Gerät verschlüsseln** aus, überprüfen Sie die im:
    * **Storage** > **speicherverschlüsselung**
    * **Storage** > **Sperrbildschirm und Sicherheit** > **andere Sicherheitseinstellungen** 

2. Folgen Sie den Anweisungen auf dem Bildschirm. Während der Verschlüsselung startet Ihr Gerät möglicherweise mehrmals neu.
3. Öffnen Sie die Unternehmensportal-App oder Microsoft Intune-app.
    * Unternehmensportal-Benutzer: Wählen Sie Ihr Gerät aus, und tippen Sie auf **Geräteeinstellungen überprüfen**.  
    * Microsoft Intune-Benutzer: Sie müssen warten, bis der Seite wird aktualisiert, aber wenn dies der Fall, sollten Ihre Verschlüsselungsstatus zu kompatiblen ändern.

## <a name="troubleshoot"></a>Problembehandlung  
**Problem**: Sie haben Ihr Gerät bereits verschlüsselt und

- Die Schaltfläche „Verschlüsselung“ ist deaktiviert.
- Eine Meldung wird angezeigt, dass die Verschlüsselung noch ausgeführt werden muss.
- Es treten Fehler beim Versuch, die Unternehmensportal-App oder Microsoft Intune-app verwenden.

**Versuchen Sie Folgendes**

- Stellen Sie sicher, dass das Gerät aufgeladen und angeschlossen ist.  
- Stellen Sie sicher, dass Sie auf Ihrem Gerät eine PIN oder ein Kennwort festgelegt haben.  

Benötigen Sie weitere Unterstützung? Wenden Sie sich an den Support Ihres Unternehmens (suchen Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980) nach Kontaktinformationen) oder an das <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-Team</a>.  
