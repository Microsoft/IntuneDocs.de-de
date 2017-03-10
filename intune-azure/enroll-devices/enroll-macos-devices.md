---
title: "Registrieren von macOS-Geräten in Intune | Intune in Azure (Vorschau) | Microsoft Docs"
description: "Intune in Azure (Vorschau): Erfahren Sie, wie Sie macOS-Geräte in der Vorschau von Intune in Azure registrieren."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a2e840797c06322b9efc59438e0675e57b7cdb24
ms.openlocfilehash: f217988313debd33bcba3f8168aa03b6dbf8586e
ms.lasthandoff: 02/14/2017


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>Registrieren von macOS-Geräten in der Vorschau von Intune in Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune ermöglicht es Ihnen, macOS-Geräte zu verwalten. Um die Geräteverwaltung zu aktivieren, müssen Ihre Benutzer ihre Geräte registrieren, indem sie auf die [Unternehmensportal-Website](http://portal.manage.microsoft.com) gehen und die Aufforderungen befolgen. Sobald sich macOS-Geräte unter Verwaltung befinden, können Sie [benutzerdefinierte Einstellungen für macOS-Geräte erstellen](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-macos). Weitere Funktionen sind in Kürze verfügbar.

## <a name="prerequisites"></a>Voraussetzungen

Die folgenden Voraussetzungen müssen vor dem Einrichten der Registrierung von macOS-Geräten erfüllt sein:

- [Konfigurieren von Domänen](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Festlegen der MDM-Autorität](set-mdm-authority.md)
- [Erstellen von Gruppen](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Konfigurieren des Unternehmensportals](/intune-azure/manage-apps/company-portal-app.md)
- Zuweisen von Benutzerlizenzen im [Office 365-Portal](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Abrufen eines Apple-MDM-Push-Zertifikats](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>Einrichten der macOS-Registrierung

Standardmäßig erlaubt Intune bereits die Registrierung von macOS-Geräten. 

Informationen zum Blockieren der Registrierung von macOS-Geräten finden Sie unter [Festlegen von Gerätetypbeschränkungen](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions). 

Um die maximale Anzahl von Geräten festzulegen, die ein Benutzer registrieren kann, sehen Sie sich das Thema [Festlegen von Einschränkungen zum Gerätelimit](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-limit-restrictions) an.

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Kommunizieren der Geräteregistrierung für den Zugriff auf Unternehmensressourcen an die Benutzer

Ihre Endbenutzer müssen auf die [Unternehmensportal-Website](http://portal.manage.microsoft.com) gehen und den Aufforderungen folgen, um ihre Geräte zu registrieren. Sie können ihnen auch einen Link für Online-Registrierungsschritte senden: [Registrieren Ihres Mac OS-Geräts bei Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos). 

Informationen zu anderen Endbenutzeraufgaben finden Sie in den folgenden Artikeln:

- [Ressourcen zu Endbenutzerszenarios in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [Verwenden Ihres iOS- oder Mac OS-Geräts mit Intune](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)