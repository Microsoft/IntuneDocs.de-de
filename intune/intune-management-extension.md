---
title: "Verwalten von PowerShell-Skripts in Intune für Windows 10-Geräte"
titlesuffix: Azure portal
description: "Erfahren Sie, wie Sie PowerShell-Skripts in Intune für die Ausführung auf Windows 10-Geräten hochladen."
keywords: 
author: dougeby
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a52f2affa235a37b6d99a8452bc83a794cb04ce5
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Verwalten von PowerShell-Skripts in Intune für Windows 10-Geräte
Durch die Verwaltungserweiterung von Intune können Sie PowerShell-Skripts in Intune für die Ausführung auf Windows 10-Geräten hochladen. Die Verwaltungserweiterungen ergänzt Funktionen für die mobile Geräteverwaltung (mobile device management, MDM) von Windows 10 und erleichtert Ihnen den Wechsel zu einer modernen Verwaltung.

## <a name="moving-to-modern-management"></a>Wechsel zu moderner Verwaltung
Die individuelle Datenverarbeitung durchläuft eine digitale Transformation. Die klassische, traditionelle IT konzentriert sich auf eine einzelne Geräteplattform, unternehmenseigene Geräte, Benutzer, die vom Büro aus arbeiten und eine Vielzahl von manuellen, reaktiven IT-Prozessen. Der moderne Arbeitsplatz ermöglicht jedoch mehrere Geräteplattformen, die sowohl benutzer- als auch unternehmenseigen sind. Dadurch können Benutzer von überall aus arbeiten, und automatisierte und proaktive IT-Prozesse werden ermöglicht. 

MDM-Dienste, z.B. Microsoft Intune, können Windows 10-Geräte mithilfe des MDM-Protokolls verwalten. Der integrierte Windows 10-Verwaltungsclient kann mit Intune kommunizieren, um Aufgaben für die Unternehmensverwaltung auszuführen. Dadurch werden Sie bei der Umstellung auf eine moderne Verwaltung von Windows 10-Geräten unterstützt. Es gibt jedoch bestimmte Funktionen, die Sie benötigen, z.B. die erweiterte Gerätekonfiguration, die Problembehandlung und eine ältere Win32-App-Verwaltung, die derzeit nicht für die mobile Geräteverwaltung für Windows 10 verfügbar ist. Für diese Funktionen sollten Sie den Intune-Softwareclient auf Ihren Windows 10-Geräten ausführen. Dadurch können Sie die neuen Funktionen nicht nutzen, die die mobile Geräteverwaltung für Windows 10 bereitstellt. [Vergleichen Sie die Unterschiede zwischen dem Intune-Softwareclient und der mobilen Geräteverwaltung für Windows 10.](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison)

Die Intune-Verwaltungserweiterung ergänzt die integrierten MDM-Funktionen für Windows 10. Sie können PowerShell-Skripts für die Ausführung auf Windows 10-Geräten erstellen, die die Funktionen bereitstellen, die Sie benötigen. Sie können beispielsweise ein PowerShell-Skript erstellen, das eine ältere Win32-App auf Ihren Windows 10-Geräten installiert, das Skript in Intune hochlädt, es einer Azure Active Directory-Gruppe (AD) zuweist und das Skript auf Windows 10-Geräten ausführen. Sie können dann den Ausführungsstatus des Skripts auf Windows 10-Geräten von Anfang bis Ende überwachen.

## <a name="prerequisites"></a>Voraussetzungen
Für die Intune-Verwaltungserweiterung sind folgende Voraussetzungen erforderlich:
- Geräte müssen mit Azure AD verknüpft sein
- Geräte müssen Windows 10, Version 1607, oder höher ausführen

## <a name="create-a-powershell-script-policy"></a>Erstellen einer PowerShell-Skriptrichtlinie 
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Gerätekonfiguration**.
4. Klicken Sie im Bereich **Gerätekonfiguration** auf **Verwalten** > **PowerShell-Skripts**.
5. Klicken im Bereich **PowerShell-Skripts** auf **Hinzufügen**.
6. Geben Sie im Bereich **PowerShell-Skript hinzufügen** einen **Namen** und eine **Beschreibung** für das PowerShell-Skript ein.
7. Suchen Sie das PowerShell-Skript für den **Skriptstandort**. Das Skript muss kleiner als 10 KB (ASCII) oder 5 KB (Unicode) sein.
8. Klicken Sie auf **Konfigurieren**, und wählen Sie dann aus, ob das Skript mit den Anmeldeinformationen des Benutzers auf dem Gerät (**Ja**) oder im Systemkontext (**Nein**) ausgeführt werden soll. Standardmäßig werden die Skripts im Systemkontext ausgeführt. Wählen Sie **Ja** aus, wenn das Skript nicht im Systemkontext ausgeführt werden muss. 
  ![Bereich „PowerShell-Skript hinzufügen“](./media/mgmt-extension-add-script.png)
9. Wählen Sie aus, ob das Skript von einem vertrauenswürdigen Herausgeber signiert werden muss (**Ja**). Standardmäßig muss das Skript nicht signiert werden. 
10. Klicken Sie auf **OK** und dann auf **Erstellen**, um das Skript zu speichern.

## <a name="assign-a-powershell-script-policy"></a>Zuweisen einer PowerShell-Skriptrichtlinie
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Gerätekonfiguration**.
4. Klicken Sie im Bereich **Gerätekonfiguration** auf **Verwalten** > **PowerShell-Skripts**.
5. Wählen Sie im Bereich **PowerShell-Skripts** das zuzuweisende Skript aus, und klicken Sie dann auf **Verwalten** > **Zuweisungen**.
  ![Bereich „PowerShell-Skript hinzufügen“](./media/mgmt-extension-assignments.png)
 
6. Klicken Sie auf **Gruppen auswählen**, um verfügbare Azure AD-Gruppen aufzulisten. 
7. Wählen Sie mindestens eine Gruppe mit den Benutzern aus, deren Geräte das Skript erhalten sollen, und klicken Sie dann auf **Auswählen**, um die Richtlinie den ausgewählten Gruppen zuzuweisen.

Die Intune-Verwaltungserweiterung wird einmal pro Stunde mit Intune synchronisiert. Nachdem Sie die Richtlinie den Azure AD-Gruppen zugewiesen haben, wird das PowerShell-Skript ausgeführt, und die Ausführungsergebnisse werden berichtet. 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>Überwachen des Ausführungsstatus für PowerShell-Skripts
Sie können den Ausführungsstatus von PowerShell-Skripts für Benutzer und Geräte im Azure-Portal überwachen.
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Gerätekonfiguration**.
4. Klicken Sie im Bereich **Gerätekonfiguration** auf **Verwalten** > **PowerShell-Skripts**.
5. Wählen Sie im Bereich **PowerShell-Skripts** das zu überwachende Skript aus, klicken Sie auf **Überwachen**, und wählen Sie anschließend einen der folgenden Berichte aus:
   - **Gerätestatus**
   - **Benutzerstatus**
