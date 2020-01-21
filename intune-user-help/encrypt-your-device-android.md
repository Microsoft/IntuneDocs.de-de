---
title: Verschlüsseln eines Android-Geräts für InTune | Microsoft-Dokumentation
description: Schritte zum Aktivieren der Android-Geräteverschlüsselung, wenn dies für InTune erforderlich ist
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 2774a4f4c571b8a965c9ec47376a671df2dbf006
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856681"
---
# <a name="encrypting-your-android-device"></a>Verschlüsseln Ihres Android-Geräts

Die Geräteverschlüsselung schützt Ihre Dateien und Ordner vor nicht autorisiertem Zugriff, wenn Ihr Gerät verloren geht oder gestohlen wird. Nachdem Sie die Geräteverschlüsselung eingeschaltet haben, können sich nur Personen mit dem richtigen Kennwort oder der PIN bei Ihrem Gerät anmelden. 

Bevor Sie auf Schul-oder Arbeitsressourcen zugreifen können, ist es möglicherweise erforderlich, dass Ihre Organisation Ihr Android-Gerät verschlüsselt. Einige neuere Android-Geräte werden standardmäßig verschlüsselt.  

## <a name="turn-on-encryption"></a>Verschlüsselung aktivieren

Wenn Unternehmensportal oder die Microsoft InTune-app Sie auffordert, Ihr Gerät zu verschlüsseln, führen Sie die folgenden Schritte aus. 

> [!Note]
> Bestimmte Android-Geräte von Huawei, vivo und OPPO können nicht verschlüsselt werden. [Hier](your-device-appears-encrypted-but-cp-says-otherwise-android.md) erfahren Sie mehr.  

1. Legen Sie eine Geräte Bildschirmsperre fest.  
    a. Wechseln Sie zu **Einstellungen** > **Lock Screen and Security** > **Screen lock** (Sperrbildschirm und Sicherheit > Bildschirmsperre).  
    b. Wählen Sie entweder **Pin**, **Kennwort**oder **Muster**aus.  
    c. Befolgen Sie die Anweisungen auf dem Bildschirm, um die Bildschirmsperre zu konfigurieren.  

2. Wechseln Sie zurück zu **Sperrbildschirm und Sicherheit** , und wählen Sie **sicherer Start**aus.
3. Wählen Sie PIN anfordern, **Wenn das Gerät eingeschaltet wird** > **OK**aus.
4. Geben Sie Ihre PIN ein, um Ihr Gerät zu bestätigen und zu verschlüsseln.
5. Öffnen Sie die APP Unternehmensportal oder Microsoft InTune.
    * Unternehmensportalbenutzer: Wählen Sie Ihr Gerät aus, und tippen Sie auf **Geräteeinstellungen überprüfen**. 
    * Microsoft InTune Benutzer: Sie müssen warten, bis die Seite aktualisiert wird. wenn dies der Fall ist, sollte sich der Verschlüsselungs Status in "kompatibel" ändern.  

Geräte unter Android 4,4 und früher verfügen möglicherweise nicht über die Option für den **sicheren Start** . Führen Sie in diesem Fall die folgenden Schritte aus, um Ihr Gerät zu verschlüsseln.

1. Wechseln Sie zu **Einstellungen** > **Sicherheits** > **Gerät verschlüsseln**. Bildschirm Bezeichnungen variieren zwischen Android-Geräten. Wenn die Option **Gerät verschlüsseln** nicht angezeigt wird, checken Sie Folgendes ein:
    * **Speicher** > **Speicherverschlüsselung**
    * **Speicher** > **Sperrbildschirm und Sicherheits** > **andere Sicherheitseinstellungen** 

2. Folgen Sie den Anweisungen auf dem Bildschirm. Während der Verschlüsselung startet Ihr Gerät möglicherweise mehrmals neu.
3. Öffnen Sie die APP Unternehmensportal oder Microsoft InTune.
    * Unternehmensportalbenutzer: Wählen Sie Ihr Gerät aus, und tippen Sie auf **Geräteeinstellungen überprüfen**.  
    * Microsoft InTune Benutzer: Sie müssen warten, bis die Seite aktualisiert wird. wenn dies der Fall ist, sollte sich der Verschlüsselungs Status in "kompatibel" ändern.

## <a name="troubleshoot"></a>Problembehandlung  
**Problem**: Sie haben Ihr Gerät bereits verschlüsselt und

- Die Schaltfläche „Verschlüsselung“ ist deaktiviert.
- Eine Meldung wird angezeigt, dass die Verschlüsselung noch ausgeführt werden muss.
- Beim Versuch, die Unternehmensportal oder Microsoft InTune-APP zu verwenden, treten Fehler auf.

**Versuchen Sie Folgendes**

- Stellen Sie sicher, dass das Gerät aufgeladen und angeschlossen ist.  
- Stellen Sie sicher, dass Sie auf Ihrem Gerät eine PIN oder ein Kennwort festgelegt haben.  

Benötigen Sie weitere Unterstützung? Wenden Sie sich an den Support Ihres Unternehmens (suchen Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980) nach Kontaktinformationen) oder an das <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-Team</a>.  
