---
title: "Festlegen der Autorität für die Verwaltung mobiler Geräte"
titleSuffix: Intune Azure preview
description: "Intune in Azure (Vorschau): Erfahren Sie, wie die Autorität für die Verwaltung mobiler Geräte in Intune festlegen. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c36ddef7e53d6f4f15c82c97dc6d18863e6859f1
ms.contentlocale: de-de
ms.lasthandoff: 05/23/2017

---

# <a name="set-the-mobile-device-management-authority"></a>Festlegen der Autorität für die Verwaltung mobiler Geräte

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Die Einstellung für die Autorität für die Verwaltung mobiler Geräte (Mobile Device Management, MDM) bestimmt, wie Sie Ihre Geräte verwalten. Als IT-Administrator müssen Sie eine MDM-Autorität festlegen, damit Benutzer Geräte zur Verwaltung registrieren können.

Die möglichen Konfigurationen sind Folgende:

- **Intune Standalone:** Ausschließliche Verwaltung in der Cloud, die Sie mithilfe des Azure-Portals konfigurieren. Ihnen stehen alle Funktionen von Intune zur Verfügung. [Legen Sie die MDM-Autorität in der Intune-Konsole fest](#mdm-authority-set-to-intune).

- **Intune Hybrid:** Integration der Intune-Cloudlösung in System Center Configuration Manager. Sie konfigurieren Intune mithilfe der Configuration Manager-Konsole. [Legen Sie die MDM-Autorität im Configuration Manager fest](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Verwaltung mobiler Geräte für Office 365:** Integration von Office 365 in die Intune-Cloudlösung. Sie konfigurieren Intune über das Office 365 Admin Center. Ihnen steht eine Teilmenge der Funktionen von Intune Standalone zur Verfügung. Legen Sie die MDM-Autorität im Office 365 Admin Center fest.

>[!IMPORTANT]
>Nachdem Sie die Autorität für die Verwaltung mobiler Geräte einmal festgelegt haben, müssen Sie sich für eine Änderung an den [Microsoft-Support](https://docs.microsoft.com/intune-classic/troubleshoot/get-support) wenden. Sie sollten Ihre Auswahl daher sorgfältig treffen.

## <a name="set-mdm-authority-to-intune"></a>Festlegen der MDM-Autorität in Intune

1. Wählen Sie im Azure-Portal **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
  ![Screenshot der Workload zur Problembehandlung in Intune mit dem Link „Benutzer auswählen“](media/set-mdm-auth.png)
2. Wählen Sie auf dem Blatt „Intune“ die Option **Geräteregistrierung** und dann **Übersicht** aus.

3. Wählen Sie auf dem Blatt **Mit der Geräteverwaltung beginnen** die Option **MDM-Autorität auf Intune festlegen** aus. Eine Meldung zeigt an, dass Sie die MDM-Autorität erfolgreich auf Intune festgelegt haben.
