---
title: Registrieren eines von Ihrer Organisation bereitgestellten iOS-Geräts für die Verwaltung | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein iOS-Gerät bei Intune registrieren, das von Ihrer Organisation erworben und bereitgestellt wurde.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f4e7d87e-56d1-43e4-8e88-2f62cf0999e2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: c592b558ace0a2a39059de9f64531f1e078c539d
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "55847759"
---
# <a name="enroll-your-organization-provided-ios-device-in-management"></a>Registrieren eines von Ihrer Organisation bereitgestellten iOS-Geräts für die Verwaltung

Erfahren Sie, wie Sie Ihr neues iOS-Gerät in Intune verwalten können.  

Die iOS-Geräte, die Ihnen von der Arbeit, der Schule oder der Universität zur Verfügung gestellt werden, sind häufig vorkonfiguriert, bevor Sie sie erhalten. Ihre Organisation sendet diese vorkonfigurierten Einstellungen an das Gerät, nachdem Sie es eingeschaltet und sich zum ersten Mal angemeldet haben. Wenn Ihr Gerät das Setup abgeschlossen hat, erhalten Sie Zugriff auf Ihre Unternehmens- bzw. Schul- oder Universitätsressourcen.  

Um mit dem Setup zu beginnen, schalten Sie Ihr Gerät ein, und melden Sie sich mit den betreffenden Anmeldeinformationen an. Im folgenden Artikel werden die Schritte und Bildschirme erläutert, die für das Setup mit dem Setup-Assistenten von Bedeutung sind. 

## <a name="what-is-apple-dep"></a>Was ist das Apple-Programm zur Geräteregistrierung?
Möglicherweise hat Ihre Organisation ihre Geräte über ein sogenanntes *Apple-Programm zur Geräteregistrierung* erworben. Über das Apple-Programm zur Geräteregistrierung haben Organisationen die Möglichkeit, große Mengen von iOS- oder macOS-Geräten zu erwerben. Dann können sie diese Geräte über einen beliebigen Dienst (z.B. Intune), der die Verwaltung mobiler Geräte anbietet, konfigurieren und verwalten. Wenn Sie über Administratorberechtigungen verfügen und sich für das Apple-Programm zur Geräteregistrierung interessieren, erhalten Sie weitere Informationen unter [Automatisches Registrieren von iOS-Geräten mit dem Programm zur Geräteregistrierung von Apple](https://docs.microsoft.com/intune/device-enrollment-program-enroll-ios).  

## <a name="set-up-your-ios-device"></a>Einrichten Ihres iOS-Geräts  
Wenn Sie Ihr eigenes iOS-Gerät anstelle eines organisationseigenen Geräts verwenden, führen Sie die Schritte für [persönliche Geräte oder Bring Your Own Device](enroll-your-device-in-intune-ios.md) aus.  

1. Schalten Sie Ihr iOS-Gerät ein. 
2. Stellen Sie auf Ihrem Gerät eine WLAN-Verbindung her, nachdem Sie Ihre **Sprache** ausgewählt haben.
3. Wählen Sie auf der Anzeige **Set up iOS device** (iOS-Gerät einrichten) eine der folgenden Optionen aus: 
 
   - **Set up as new device** (Als neues Gerät einrichten)
   - **Restore from iCloud backup** (Aus iCloud-Sicherung wiederherstellen)
   - **Restore from iTunes backup** (Aus iTunes-Sicherung wiederherstellen)

4. Sobald Sie die WLAN-Verbindung hergestellt haben, wird der Bildschirm **Konfiguration** angezeigt. Darin wird Folgendes mitgeteilt: **Ihr Gerät wird automatisch von [Ihrem Unternehmen] konfiguriert.**

   **Die Konfiguration ermöglicht [Ihrem Unternehmen] die drahtlose Verwaltung dieses Geräts. Ein Administrator unterstützt Sie bei der Einrichtung von E-Mail- und -Netzwerkkonten, der Installation und Konfiguration von Apps und der Remoteverwaltung von Einstellungen. Ein Administrator kann Features deaktivieren, Apps installieren und entfernen, Ihren Internetdatenverkehr überwachen und einschränken sowie eine Remotelöschung dieses Geräts ausführen.**
 
   **Die Konfiguration wird bereitgestellt durch: [Ihr Unternehmen] iOS-Team [Adresse]**

5. Melden Sie sich mit Ihrer Apple-ID an. Wenn Sie sich anmelden, können Sie die Unternehmensportal-App und das Verwaltungsprofil installieren, über das Ihr Unternehmen Ihnen Zugriff auf Unternehmensressourcen wie E-Mails oder Apps erteilen kann. 
6. Akzeptieren Sie die **Geschäftsbedingungen**, und entscheiden Sie, ob Sie Diagnoseinformationen an Apple senden möchten.
7. Sobald Sie Ihre Registrierung abgeschlossen haben, fordert Ihr Gerät Sie möglicherweise dazu auf, weitere Aktionen auszuführen. Bei einigen dieser Schritte müssen Sie möglicherweise Ihr Kennwort eingeben, damit Sie auf E-Mails zugreifen können, oder einen Zugriffscode einrichten.

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).
