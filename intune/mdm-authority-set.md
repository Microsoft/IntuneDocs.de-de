---
title: Festlegen der Autorität für die Verwaltung mobiler Geräte
titlesuffix: Microsoft Intune
description: Festlegen der Autorität für die Verwaltung mobiler Geräte in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f903e9dfe5fb30f45806aac5694171814492f2e
ms.sourcegitcommit: 0f1a5d6e577915d2d748d681840ca04a0a2604dd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="set-the-mobile-device-management-authority"></a>Festlegen der Autorität für die Verwaltung mobiler Geräte

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Die Einstellung für die Autorität für die Verwaltung mobiler Geräte (Mobile Device Management, MDM) bestimmt, wie Sie Ihre Geräte verwalten. Als IT-Administrator müssen Sie eine MDM-Autorität festlegen, damit Benutzer Geräte zur Verwaltung registrieren können.

Die möglichen Konfigurationen sind Folgende:

- **Intune Standalone:** Ausschließliche Verwaltung in der Cloud, die Sie mithilfe des Azure-Portals konfigurieren. Ihnen stehen alle Funktionen von Intune zur Verfügung. [Legen Sie die MDM-Autorität in der Intune-Konsole fest](#set-mdm-authority-to-intune).

- **Intune Hybrid:** Integration der Intune-Cloudlösung in System Center Configuration Manager. Sie konfigurieren Intune mithilfe der Configuration Manager-Konsole. [Legen Sie die MDM-Autorität im Configuration Manager fest](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Verwaltung mobiler Geräte für Office 365:** Integration von Office 365 in die Intune-Cloudlösung. Sie konfigurieren Intune über das Office 365 Admin Center. Ihnen steht eine Teilmenge der Funktionen von Intune Standalone zur Verfügung. Legen Sie die MDM-Autorität im Office 365 Admin Center fest.

> [!IMPORTANT]
> In Configuration Manager, Version 1610 oder höher, und Microsoft Intune, Version 1705, können Sie Ihre MDM-Autorität ändern, ohne sich an den Microsoft Support wenden und die Aufhebung der Registrierung sowie die erneute Registrierung vorhandener verwalteten Geräte durchführen zu müssen. Details finden Sie unter [Was Sie machen können, wenn Sie die falsche MDM-Autoritätseinstellung vorgenommen haben](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting).

## <a name="set-mdm-authority-to-intune"></a>Festlegen der MDM-Autorität in Intune

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie den orangefarbenen Banner aus, um die Einstellung **Autorität für die Verwaltung mobiler Geräte** zu öffnen.
4. Wählen Sie unter **Autorität für die Verwaltung mobiler Geräte** Ihre MDM-Autorität aus den folgenden Optionen aus:
   - **Intune-MDM-Autorität**
   - **Configuration Manager-MDM-Autorität**
   - **Keine**

   ![Screenshot vom Intune-Bildschirm zum Festlegen der Autorität für die mobile Geräteverwaltung](media/set-mdm-auth.png)

   Eine Meldung zeigt an, dass Sie die MDM-Autorität erfolgreich auf Intune festgelegt haben.

## <a name="enable-device-enrollment"></a>Aktivieren der Geräteregistrierung

Mit Intune als MDM-Autorität können Benutzer private Geräte registrieren und durch das Installieren der Unternehmensportal-App (iOS, macOS und Android), das Hinzufügen von Unternehmensanmeldeinformationen (Windows) oder das Zugreifen auf die Unternehmensportal-Website (iOS, Android, macOS) Zugriff auf Ressourcen wie E-Mails erhalten.

Verschiedene Plattformen haben die folgenden Anforderungen für das Aktivieren oder Vereinfachen der Registrierung:
- **iOS** – (erforderlich): [Rufen Sie ein MDM-Pushzertifikat von Apple ab](apple-mdm-push-certificate-get.md), und [registrieren Sie dann unternehmenseigene iOS-Geräte](ios-enroll.md) (optional).
- **Android** – (optional): [Aktivieren Sie Android-Arbeitsprofile.](android-enroll.md)
- **Windows** – (optional): Aktivieren Sie die [automatische Registrierung](windows-enroll.md) oder die [Massenregistrierung](windows-bulk-enroll.md).
- **macOS** (erforderlich): [Abrufen eines Apple-MDM-Push-Zertifikats](apple-mdm-push-certificate-get.md).

### <a name="workflow-of-intune-administration-ui"></a>Workflow der Intune-Verwaltungsbenutzeroberfläche
Wenn die Verwaltung von Android- oder Apple-Geräten aktiviert ist, sendet Intune Geräte- und Benutzerinformationen zur Integration mit diesen Drittanbieterdiensten, um ihre jeweiligen Geräte zu verwalten.

Szenarios, die eine Zustimmung zur Datenfreigabe hinzufügen, werden unter den folgenden Bedingungen eingeschlossen:
- Android for Work wird aktiviert.
- Apple-MDM-Push-Zertifikate werden aktiviert und hochgeladen.
- Einer der Apple-Dienste wie das Programm zur Geräteregistrierung, School Manager oder Volume Purchase Program wird aktiviert.

In jedem Fall ist die Zustimmung streng mit der Ausführung eines Diensts zur Verwaltung mobiler Geräte verknüpft, z.B. der Bestätigung, dass ein IT-Administrator Google- oder Apple-Geräte zur Registrierung autorisiert hat. An den folgenden Speicherorten finden Sie die Dokumentation zur Frage, welche Informationen freigegeben werden, wenn die neuen Workflows live sind:
- [Von Intune an Google gesendete Daten](https://aka.ms/Data-intune-sends-to-google)
- [Von Intune an Apple gesendete Daten](https://aka.ms/data-intune-sends-to-apple)

Weitere Informationen zur Einhaltung der DSGVO durch Microsoft finden Sie unter [Trust Center - Assess your GDPR compliance (Trust Center: Analyse Ihrer Einhaltung der DSGVO)](https://aka.ms/trust_center_info).

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Bereinigen mobiler Geräte nach Ablauf des MDM-Zertifikats

Das MDM-Zertifikat wird automatisch erneuert, wenn mobile Geräte mit dem Intune-Dienst kommunizieren. Wenn mobile Geräte zurückgesetzt werden oder für längere Zeit keine Kommunikation mit dem Intune-Dienst stattfindet, wird das MDM-Zertifikat nicht erneuert. Das Gerät wird 180 Tage nach Ablauf des MDM-Zertifikats aus dem Azure-Portal entfernt.
