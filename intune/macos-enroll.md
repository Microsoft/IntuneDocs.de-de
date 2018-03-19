---
title: "Registrieren von macOS-Geräten"
titlesuffix: Microsoft Intune
description: "Erfahren Sie, wie Sie die Registrierung von macOS-Geräten in Intune einrichten."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 77a1551321079765f00f0e35d57211ae4c99e5a6
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Registrieren von macOS-Geräten in Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune ermöglicht es Ihnen, macOS-Geräte zu verwalten. Um die Geräteverwaltung zu aktivieren, müssen Ihre Benutzer ihre Geräte registrieren, indem sie auf die [Unternehmensportal-Website](http://portal.manage.microsoft.com) gehen und die Aufforderungen befolgen. Sobald sich macOS-Geräte unter Verwaltung befinden, können Sie [benutzerdefinierte Einstellungen für macOS-Geräte erstellen](custom-settings-macos.md). Weitere Funktionen sind in Kürze verfügbar.

## <a name="prerequisites"></a>Voraussetzungen

Die folgenden Voraussetzungen müssen vor dem Einrichten der Registrierung von macOS-Geräten erfüllt sein:

- [Konfigurieren von Domänen](custom-domain-name-configure.md)
- [Festlegen der MDM-Autorität](mdm-authority-set.md)
- [Erstellen von Gruppen](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Konfigurieren des Unternehmensportals](company-portal-app.md)
- Zuweisen von Benutzerlizenzen im [Office 365-Portal](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Abrufen eines Apple-MDM-Push-Zertifikats](apple-mdm-push-certificate-get.md)

## <a name="user-owned-ios-devices-byod"></a>iOS-Gerät im Besitz des Benutzers (BYOD)

Benutzer können ihre persönlichen Geräte für die Intune-Verwaltung registrieren. Dies wird als „bring your own device“ oder BYOD bezeichnet. Sobald Sie über die Voraussetzungen verfügen und den Benutzern Lizenzen zugewiesen haben, können diese die Unternehmensportal-App für macOS aus dem App Store herunterladen und den Registrierungsanweisungen in der App folgen.

## <a name="company-owned-ios-devices"></a>Unternehmenseigenes iOS-Gerät
Für Organisationen, die Geräte für ihre Benutzer erwerben, unterstützt Intune die Registrierung von firmeneigenen macOS-Geräten mit einem [Device Enrollment Manager](device-enrollment-manager-enroll.md)-Konto (DEM).

## <a name="set-up-macos-enrollment"></a>Einrichten der macOS-Registrierung

Standardmäßig erlaubt Intune bereits die Registrierung von macOS-Geräten.

Informationen zum Blockieren der Registrierung von macOS-Geräten finden Sie unter [Festlegen von Gerätetypbeschränkungen](enrollment-restrictions-set.md).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Kommunizieren der Geräteregistrierung für den Zugriff auf Unternehmensressourcen an die Benutzer

Ihre Endbenutzer müssen die [Unternehmensportalwebsite](http://portal.manage.microsoft.com) besuchen und den Aufforderungen folgen, um ihre Geräte zu registrieren. Sie können ihnen auch einen Link für Online-Registrierungsschritte senden: [Registrieren Ihres Mac OS-Geräts bei Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Informationen zu anderen Endbenutzeraufgaben finden Sie in den folgenden Artikeln:

- [Ressourcen zu Endbenutzerszenarios in Microsoft Intune](end-user-educate.md)
- [Verwenden Ihres macOS-Geräts mit Intune](/intune-user-help/using-your-macos-device-with-intune)
