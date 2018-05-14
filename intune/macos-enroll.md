---
title: Registrieren von macOS-Geräten
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie die Registrierung von macOS-Geräten in Intune einrichten.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4f8cddb69ac85e45acde8a846df3b5413c3b75bf
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2018
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Registrieren von macOS-Geräten in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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

Ihre Endbenutzer müssen die [Unternehmensportalwebsite](https://portal.manage.microsoft.com) besuchen und den Aufforderungen folgen, um ihre Geräte zu registrieren. Sie können ihnen auch einen Link für Online-Registrierungsschritte senden: [Registrieren Ihres Mac OS-Geräts bei Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Informationen zu anderen Endbenutzeraufgaben finden Sie in den folgenden Artikeln:

- [Ressourcen zu Endbenutzerszenarios in Microsoft Intune](end-user-educate.md)
- [Verwenden Ihres macOS-Geräts mit Intune](/intune-user-help/using-your-macos-device-with-intune)

## <a name="enroll-virtual-macos-machines-for-testing"></a>Registrieren von virtuellen macOS-Computern zu Testzwecken

> [!NOTE]
> Virtuelle macOS-Computer werden nur für Testzwecke unterstützt. Verwenden Sie keine virtuellen macOS-Computer als Produktionsgeräte für Ihre Endbenutzer. 

Sie können virtuelle macOS-Computer mithilfe von Parallels Desktop oder VMware Fusion zu Testzwecken verwenden. 

Für Parallels Desktop müssen Sie den Hardwaretyp sowie die Seriennummer für die virtuellen Computer festlegen, damit Intune diese erkennen kann. Befolgen Sie die Anleitungen von Parallels zum [Festlegen des Hardwaretyps](http://kb.parallels.com/123594) sowie der [Seriennummer](http://kb.parallels.com/123455), um die nötigen Einstellungen für die Tests einzurichten. Es wird empfohlen, den Hardwaretyp des Geräts, auf dem die virtuellen Computer ausgeführt werden, mit dem Hardwaretyp der von Ihnen erstellten virtuellen Computer abzustimmen. Sie finden diesen Hardwaretyp im **Apple-Menü** unter **Über diesen Mac** > **Systembericht** > **Modell-Identifizierung**. 

Für VMware Fusion müssen Sie die [VMX-Datei bearbeiten](https://kb.vmware.com/s/article/1014782), um das Hardwaremodell und die Seriennummer des virtuellen Computers festzulegen. Es wird empfohlen, den Hardwaretyp des Geräts, auf dem die virtuellen Computer ausgeführt werden, mit dem Hardwaretyp der von Ihnen erstellten virtuellen Computer abzustimmen. Sie finden diesen Hardwaretyp im **Apple-Menü** unter **Über diesen Mac** > **Systembericht** > **Modell-Identifizierung**. 

## <a name="user-approved-enrollment"></a>Durch den Benutzer genehmigte Registrierung

Die durch den Benutzer genehmigte MDM-Registrierung ist ein Typ der macOS-Registrierung, mit dem Sie bestimmte sicherheitsrelevante Einstellungen verwalten können. Weitere Informationen finden Sie in der [Supportdokumentation von Apple](https://support.apple.com/HT208019).

Zur Genehmigung durch den Benutzer muss der Endbenutzer nach der Registrierung im macOS-Unternehmensportal die Genehmigung manuell mithilfe der Systemeinstellungen bereitstellen. Anweisungen hierzu finden Sie im macOS-Unternehmensportal für Benutzer von macOS 10.13.2 und höher.

Um herauszufinden, ob ein Gerät durch den Benutzer genehmigt ist, besuchen Sie das Intune-Portal, und wählen Sie **Geräte** > **Alle Geräte**, das Gerät und dann **Hardware** aus. Aktivieren Sie das Feld **Genehmigt durch den Benutzer**.