---
title: Registrieren von macOS-Geräten
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie die Registrierung von macOS-Geräten in Intune einrichten.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d23d03169cdbf3c88be257cafe6aa84dc8c5257f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236755"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Registrieren von macOS-Geräten in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune ermöglicht Ihnen das Verwalten von macOS-Geräten, um Benutzern Zugriff auf Unternehmens-E-Mail und -Apps zu gewähren.

Als Intune-Administrator können Sie die Registrierung für unternehmenseigene macOS-Geräte und macOS-Geräte in Privatbesitz ("bring your own Device" oder BYOD) einrichten. 

## <a name="prerequisites"></a>Voraussetzungen

Die folgenden Voraussetzungen müssen vor dem Einrichten der Registrierung von macOS-Geräten erfüllt sein:

- [Konfigurieren von Domänen](custom-domain-name-configure.md)
- [Festlegen der MDM-Autorität](mdm-authority-set.md)
- [Erstellen von Gruppen](groups-add.md)
- [Konfigurieren des Unternehmensportals](company-portal-app.md)
- Zuweisen von Benutzerlizenzen im [Office 365-Portal](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Abrufen eines Apple-MDM-Push-Zertifikats](apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>macOS-Geräte im Besitz des Benutzers (BYOD)

Benutzer können ihre persönlichen Geräte für die Intune-Verwaltung registrieren. Dies wird als „bring your own device“ oder BYOD bezeichnet. Nachdem Sie die Voraussetzungen erfüllt und Benutzerlizenzen zugewiesen haben, können Ihre Benutzer ihre Geräte registrieren, indem sie
- zur [Website des Unternehmensportals](https://portal.manage.microsoft.com) wechseln oder
- die Unternehmensportal-App herunterladen.
Sie können ihnen auch einen Link zu den Schritten für die Onlineregistrierung senden: [Registrieren Ihres macOS-Geräts in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)

Informationen zu anderen Endbenutzeraufgaben finden Sie in den folgenden Artikeln:

- [Ressourcen zu Endbenutzerszenarios in Microsoft Intune](end-user-educate.md)
- [Verwenden Ihres macOS-Geräts mit Intune](/intune-user-help/using-your-macos-device-with-intune)

## <a name="company-owned-macos-devices"></a>Unternehmenseigene macOS-Geräte
Für Organisationen, die Geräte für Ihre Benutzer erwerben, unterstützt Intune die folgenden Methoden für die Registrierung von unternehmenseigenen macOS-Geräten:
- [Apple-Programm zur Geräteregistrierung (DEP)](device-enrollment-program-enroll-macos.md): Organisationen können macOS-Geräte über das Apple-Programm zur Geräteregistrierung (Device Enrollment Program, DEP) erwerben. Mit DEP können Sie drahtlos (Over The Air) ein Registrierungsprofil bereitstellen, das Geräte für die Verwaltung registriert.
- [Geräteregistrierungs-Manager (Device Enrollment Manager, DEM)](device-enrollment-manager-enroll.md): Über ein DEM-Konto können Sie bis zu 1.000 Geräte registrieren.

## <a name="block-macos-enrollment"></a>Blockieren der macOS-Registrierung
Intune lässt macOS-Geräte standardmäßig registrieren. Informationen zum Blockieren der Registrierung von macOS-Geräten finden Sie unter [Festlegen von Gerätetypbeschränkungen](enrollment-restrictions-set.md).

## <a name="enroll-virtual-macos-machines-for-testing"></a>Registrieren von virtuellen macOS-Computern zu Testzwecken

> [!NOTE]
> Virtuelle macOS-Computer werden nur für Testzwecke unterstützt. Verwenden Sie keine virtuellen macOS-Computer als Produktionsgeräte für Ihre Endbenutzer. 

Sie können virtuelle macOS-Computer mithilfe von Parallels Desktop oder VMware Fusion zu Testzwecken verwenden. 

Für Parallels Desktop müssen Sie den Hardwaretyp sowie die Seriennummer für die virtuellen Computer festlegen, damit Intune diese erkennen kann. Befolgen Sie die Anleitungen von Parallels zum Festlegen des Hardwaretyps sowie der [Seriennummer](http://kb.parallels.com/123455), um die nötigen Einstellungen für die Tests einzurichten. Es wird empfohlen, den Hardwaretyp des Geräts, auf dem die virtuellen Computer ausgeführt werden, mit dem Hardwaretyp der von Ihnen erstellten virtuellen Computer abzustimmen. Sie finden diesen Hardwaretyp im **Apple-Menü** > **Über diesen Mac** > **Systembericht** > **Modell-Identifizierung**. 

Für VMware Fusion müssen Sie die [VMX-Datei bearbeiten](https://kb.vmware.com/s/article/1014782), um das Hardwaremodell und die Seriennummer des virtuellen Computers festzulegen. Es wird empfohlen, den Hardwaretyp des Geräts, auf dem die virtuellen Computer ausgeführt werden, mit dem Hardwaretyp der von Ihnen erstellten virtuellen Computer abzustimmen. Sie finden diesen Hardwaretyp im **Apple-Menü** > **Über diesen Mac** > **Systembericht** > **Modell-Identifizierung**. 

## <a name="user-approved-enrollment"></a>Durch den Benutzer genehmigte Registrierung

Die durch den Benutzer genehmigte MDM-Registrierung ist ein Typ der macOS-Registrierung, mit dem Sie bestimmte sicherheitsrelevante Einstellungen verwalten können. Weitere Informationen finden Sie in der [Supportdokumentation von Apple](https://support.apple.com/HT208019).

Zur Genehmigung durch den Benutzer muss der Endbenutzer nach der Registrierung im macOS-Unternehmensportal die Genehmigung manuell mithilfe der Systemeinstellungen bereitstellen. Anweisungen hierzu finden Sie im macOS-Unternehmensportal für Benutzer von macOS 10.13.2 und höher.

Um herauszufinden, ob ein Gerät durch den Benutzer genehmigt ist, besuchen Sie das Intune-Portal, und wählen Sie **Geräte** > **Alle Geräte**, das Gerät und dann **Hardware** aus. Aktivieren Sie das Feld **Genehmigt durch den Benutzer**.

## <a name="next-steps"></a>Nächste Schritte

Nachdem macOS-Geräte registriert wurden, können Sie [benutzerdefinierte Einstellungen für macOS-Geräte erstellen](custom-settings-macos.md).
