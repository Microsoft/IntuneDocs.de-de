---
title: Verwalten von PowerShell-Skripts in Microsoft Intune für Windows 10-Geräte – Azure | Microsoft-Dokumentation
description: Fügen Sie PowerShell-Skripts hinzu, weisen Sie Azure Active Directory-Gruppen Skriptrichtlinien zu, überwachen Sie Skripts mit Berichten, und erfahren Sie, wie Sie hinzugefügte Skripte auf Windows 10-Geräten in Microsoft Intune löschen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ad8e874dda47b7c6deeb614b0f893f7c922241ce
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236338"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Verwalten von PowerShell-Skripts in Intune für Windows 10-Geräte
Durch die Verwaltungserweiterung von Intune können Sie PowerShell-Skripts in Intune für die Ausführung auf Windows 10-Geräten hochladen. Die Verwaltungserweiterungen ergänzt Funktionen für die mobile Geräteverwaltung (Mobile Device Management, MDM) von Windows 10 und erleichtert Ihnen den Wechsel zu einer modernen Verwaltung.

## <a name="moving-to-modern-management"></a>Wechsel zu moderner Verwaltung
Die individuelle Datenverarbeitung durchläuft eine digitale Transformation. Die klassische, traditionelle IT konzentriert sich auf eine einzelne Geräteplattform, unternehmenseigene Geräte, Benutzer, die vom Büro aus arbeiten und eine Vielzahl von manuellen, reaktiven IT-Prozessen. Der moderne Arbeitsplatz ermöglicht jedoch mehrere Geräteplattformen, die sowohl benutzer- als auch unternehmenseigen sind. Dadurch können Benutzer von überall aus arbeiten, und automatisierte und proaktive IT-Prozesse werden ermöglicht. 

MDM-Dienste, z.B. Microsoft Intune, können Windows 10-Geräte mithilfe des MDM-Protokolls verwalten. Der integrierte Windows 10-Verwaltungsclient kann mit Intune kommunizieren, um Aufgaben für die Unternehmensverwaltung auszuführen. Dadurch werden Sie bei der Umstellung auf eine moderne Verwaltung von Windows 10-Geräten unterstützt. Es gibt jedoch bestimmte Funktionen, die Sie benötigen, z.B. die erweiterte Gerätekonfiguration, die Problembehandlung und eine ältere Win32-App-Verwaltung, die derzeit nicht für die mobile Geräteverwaltung für Windows 10 verfügbar ist. Für diese Funktionen sollten Sie den Intune-Softwareclient auf Ihren Windows 10-Geräten ausführen. Dadurch können Sie die neuen Funktionen nicht nutzen, die die mobile Geräteverwaltung für Windows 10 bereitstellt. [Vergleichen Sie die Unterschiede zwischen dem Intune-Softwareclient und der mobilen Geräteverwaltung für Windows 10.](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison)

Die Intune-Verwaltungserweiterung ergänzt die integrierten MDM-Funktionen für Windows 10. Sie können PowerShell-Skripts für die Ausführung auf Windows 10-Geräten erstellen, die die Funktionen bereitstellen, die Sie benötigen. Sie können beispielsweise ein PowerShell-Skript erstellen, das eine ältere Win32-App auf Ihren Windows 10-Geräten installiert, das Skript in Intune hochlädt, es einer Azure Active Directory-Gruppe (AD) zuweist und das Skript auf Windows 10-Geräten ausführen. Sie können dann den Ausführungsstatus des Skripts auf Windows 10-Geräten von Anfang bis Ende überwachen.

## <a name="prerequisites"></a>Voraussetzungen
Für die Intune-Verwaltungserweiterung sind folgende Voraussetzungen erforderlich:
- Geräte müssen mit Azure AD verknüpft sein. Die Intune-Verwaltungserweiterung unterstützt Geräte, die in Azure Active Directory und hybride Domänen eingebunden sind, sowie gemeinsam verwaltete registrierte Windows-Geräte.
- Geräte müssen Windows 10, Version 1607, oder höher ausführen.
- Die automatische MDM-Registrierung muss [in Azure AD aktiviert sein](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment), und Geräte müssen automatisch in Intune registriert werden.

## <a name="create-a-powershell-script-policy"></a>Erstellen einer PowerShell-Skriptrichtlinie 
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonfiguration** > **PowerShell-Skripts** > **Hinzufügen**.
4. Geben Sie einen **Namen** und eine **Beschreibung** für das PowerShell-Skript ein. Navigieren Sie zum PowerShell-Skript für den **Skriptstandort**. Das Skript muss kleiner als 200 KB (ASCII) oder 100 KB (Unicode) sein.
5. Wählen Sie **Konfigurieren** aus. Wählen Sie dann aus, ob das Skript mit den Anmeldeinformationen des Benutzers auf dem Gerät (**Ja**) oder im Systemkontext (**Nein**) ausgeführt werden soll. Standardmäßig werden die Skripts im Systemkontext ausgeführt. Wählen Sie **Ja** aus, wenn das Skript nicht im Systemkontext ausgeführt werden muss. 
  ![Bereich „PowerShell-Skript hinzufügen“](./media/mgmt-extension-add-script.png)
6. Wählen Sie aus, ob das Skript von einem vertrauenswürdigen Herausgeber signiert werden muss (**Ja**). Standardmäßig muss das Skript nicht signiert werden. 
7. Klicken Sie auf **OK** und dann auf **Erstellen**, um Ihr Skript zu speichern.

## <a name="assign-a-powershell-script-policy"></a>Zuweisen einer PowerShell-Skriptrichtlinie
1. Wählen Sie unter **PowerShell-Skripts** das zuzuweisende Skript aus, und klicken Sie dann auf **Verwalten** > **Zuweisungen**.
  ![Bereich „PowerShell-Skript hinzufügen“](./media/mgmt-extension-assignments.png)
 
2. Klicken Sie auf **Gruppen auswählen**, um verfügbare Azure AD-Gruppen aufzulisten. 
3. Wählen Sie mindestens eine Gruppe aus, die die Benutzer enthält, deren Geräte das Skript erhalten sollen. Klicken Sie auf **Auswählen**, um die Richtlinie den ausgewählten Gruppen zuzuweisen.

> [!NOTE]
> - PowerShell-Skripts können nicht auf Computergruppen angewendet werden.
> - Endbenutzer müssen nicht beim Gerät angemeldet sein, um PowerShell-Skripts auszuführen. 
> - PowerShell-Skripts in Intune können auf AAD-Gerätesicherheitsgruppen ausgerichtet werden.

Die Intune-Verwaltungserweiterung wird einmal pro Stunde mit Intune synchronisiert. Nachdem Sie die Richtlinie den Azure AD-Gruppen zugewiesen haben, wird das PowerShell-Skript ausgeführt, und die Ausführungsergebnisse werden berichtet. 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>Überwachen des Ausführungsstatus für PowerShell-Skripts
Sie können den Ausführungsstatus von PowerShell-Skripts für Benutzer und Geräte im Azure-Portal überwachen.

Wählen Sie unter **PowerShell-Skripts** das zu überwachende Skript aus, klicken Sie auf **Überwachen**, und wählen Sie anschließend einen der folgenden Berichte aus:
   - **Gerätestatus**
   - **Benutzerstatus**

## <a name="delete-a-powershell-script"></a>Löschen eines PowerShell-Skripts
Klicken Sie unter **PowerShell-Skripts** mit der rechten Maustaste auf das Skript, und klicken Sie dann auf **Löschen**.
