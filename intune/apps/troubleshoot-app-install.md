---
title: Problembehandlung bei der App-Installation
titleSuffix: Microsoft Intune
description: Weitere Informationen zur Problembehandlung bei der App-Installation mithilfe des Microsoft Intune-Bereichs zur Problembehandlung
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be66f99006b06dce9f9bfe21eafa9f2be302e7b9
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540978"
---
# <a name="troubleshoot-app-installation-issues"></a>Problembehandlung bei der App-Installation

Auf Geräten, die mit Microsoft Intune MDM verwaltet werden, können App-Installationen manchmal fehlschlagen. In diesen Fällen kann es schwierig sein, die Fehlerursache zu verstehen oder das Problem zu beheben. Microsoft Intune stellt Details zu fehlgeschlagenen App-Installationen bereit. So können Helpdeskmitarbeiter und Intune-Administratoren App-Informationen nutzen, um Benutzern bei ihren Anliegen zu helfen. Der Intune-Bereich „Problembehandlung“ stellt Fehlerdetails bereit, einschließlich Informationen zu verwalteten Apps auf Benutzergeräten. Details zum End-to-End-Lebenszyklus einer App finden Sie unter dem jeweiligen Gerät im Bereich **Verwaltete Apps**. Sie können Installationsprobleme ansehen, z. B. wann die App erstellt, geändert, ausgerichtet und auf einem Gerät bereitgestellt wurde. 

> [!NOTE]
> Informationen zu bestimmten Fehlercodes für die App-Installation finden Sie unter [Fehlerreferenz für die Installation der Intune-App](~/apps/app-install-error-codes.md).

## <a name="app-troubleshooting-details"></a>Details zur Problembehandlung von Apps

Intune stellt anhand von Apps, die auf dem jeweiligen Benutzergerät installiert sind, App-Informationen zur Problembehandlung bereit.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
3. Wählen Sie **Support und Problembehandlung** aus.
4. Klicken Sie auf **Benutzer auswählen**, um einen Benutzer auszuwählen, für den ein Problem behoben werden muss. Der Bereich **Benutzer auswählen** wird angezeigt.
5. Wählen Sie einen Benutzer aus, indem Sie den Namen oder die E-Mail-Adresse eingeben. Klicken Sie unten im Bereich auf **Auswählen**. Die Informationen zur Problembehandlung für den Benutzer werden im Bereich **Problembehandlung** angezeigt. 
6. Wählen Sie aus der Liste **Geräte** ein Gerät zur Problembehandlung aus.
    ![Intune Bereich zur Problembehandlung](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. Wählen Sie im ausgewählten Gerätebereich **Verwaltete Apps** aus. Eine Liste der verwalteten Apps wird angezeigt.
    ![Details zu einem bestimmten Gerät, das von Intune verwaltet wird.](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. Wählen Sie aus der Liste eine App aus. Der **Installationsstatus** zeigt an, ob ein Fehler aufgetreten ist.
    ![Eine ausgewählte App, die Details zur fehlgeschlagenen Installation anzeigt.](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > Eine App kann mehreren Gruppen zugewiesen werden – jedoch mit unterschiedlichen beabsichtigten Aktionen (Absichten) für die App. Beispielsweise zeigt eine aufgelöste Absicht für eine App **Ausgeschlossen** an, wenn die App bei der App-Zuweisung für einen Benutzer ausgeschlossen wird. Weitere Informationen finden Sie unter [Auflösung von Konflikten zwischen App-Absichten](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Wenn ein Installationsfehler bei einer erforderlichen App auftritt, können entweder Sie oder Ihr Helpdesk das Gerät synchronisieren und die App-Installation erneut versuchen.

Die Details zum App-Installationsfehler weisen auf das Problem hin. Anhand dieser Informationen können Sie ermitteln, welche Maßnahmen sich am besten zur Problembehandlung eignen. Weitere Informationen zur Problembehandlung bei der App-Installation finden Sie unter [Installationsfehler bei Android-Apps](app-install-error-codes.md#android-app-installation-errors) und [Installationsfehler bei iOS-Apps](app-install-error-codes.md#ios-app-installation-errors).

> [!Note]  
> Sie können auch auf den Bereich **Problembehandlung** zugreifen, indem Sie in Ihrem Browser zu [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) navigieren.

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>App-Installation für die Benutzergruppe auf dem Gerät nicht möglich
Wenn es bei der Installation von Apps zu Problemen kommt, sollten Sie die folgenden Aktionen in Erwägung ziehen:
- Wenn die App nicht im Unternehmensportal angezeigt wird, überprüfen Sie mithilfe der Absicht **Verfügbar**, ob die App bereitgestellt ist und ob der Benutzer mit einem von dem Gerät unterstützten Gerätetyp auf das Unternehmensportal zugreift.
- Bei BYOD-Geräten von Windows müssen Benutzer auf dem Gerät ein Geschäftskonto hinzufügen.
- Überprüfen Sie, ob der Benutzer das Gerätelimit für AAD überschritten hat:
  1. Navigieren Sie in Azure Active Directory zu [Geräteeinstellungen](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId).
  2. Notieren Sie sich den Wert für die **Maximale Anzahl der Geräte pro Benutzer**.
  3. Navigieren Sie zu [Azure Active Directory-Benutzer](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers).
  4. Wählen Sie den betroffenen Benutzer aus, und klicken Sie auf **Geräte**.
  5. Wenn der Benutzer das festgelegte Limit überschritten hat, löschen Sie abgelaufene Einträge, die nicht mehr benötigt werden.
- Überprüfen Sie bei iOS-DEP-Geräten, ob der Benutzer im Geräteübersichtsbereich in Intune als **Vom Benutzer registriert** aufgeführt ist. Wenn „NA“ angezeigt wird, stellen Sie eine Konfigurationsrichtlinie für das Intune-Unternehmensportal bereit. Weitere Informationen finden Sie unter [Konfigurieren der Unternehmensportal-App zur Unterstützung von iOS-DEP-Geräten](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Problembehandlung bei der Installation von Win32-Apps

Wählen Sie die Win32-App aus, die über die Intune-Verwaltungserweiterung bereitgestellt wurde. Wenn die Installation Ihrer Win32-App fehlschlägt, können Sie die Option **Protokolle sammeln** auswählen. 

> [!IMPORTANT]
> Die Option **Protokolle sammeln** wird nicht aktiviert, wenn die Win32-App erfolgreich auf dem Gerät installiert wurde.<p>Bevor Sie Protokollinformationen für eine Win32-App sammeln können, muss die Intune-Verwaltungserweiterung auf dem Windows-Client installiert werden. Die Intune-Verwaltungserweiterung wird installiert, wenn ein PowerShell-Skript oder eine Win32-App für eine Benutzer- oder Gerätesicherheitsgruppe bereitgestellt wird. Weitere Informationen finden Sie unter [Intune-Verwaltungserweiterung – Voraussetzungen](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Sammeln von Protokollen

Wenn Sie Ihre Win32-App-Installationsprotokolle sammeln möchten, führen Sie zunächst die Schritte aus, die im Abschnitt [Details zur Problembehandlung von Apps](troubleshoot-app-install.md#app-troubleshooting-details) beschrieben sind. Fahren Sie anschließend mit den folgenden Schritten fort:

1. Klicken Sie im Bereich **Installationsdetails** auf **Protokolle sammeln**.

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. Geben Sie Dateipfade mit Protokolldateinamen an, um die Protokolldateierfassung zu starten, und klicken Sie auf **OK**.

    > [!NOTE]
    > Die Protokollsammlung dauert weniger als zwei Stunden. Unterstützte Dateitypen: *.log, .txt, .dmp, .cab, .zip, .xml, .evtx und .evtl*. Maximal 25 Dateipfade sind zulässig.

3. Nachdem die Protokolldateien gesammelt wurden, können Sie auf den Link **Protokolle** klicken, um die Protokolldateien herunterzuladen.

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Eine Benachrichtigung über den Erfolg der App-Protokollsammlung wird angezeigt.

#### <a name="win32-log-collection-requirements"></a>Anforderungen für die Sammlung von Win32-Protokollen

Es gelten besondere Anforderungen, die beim Sammeln von Protokolldateien zu beachten sind:

- Sie müssen den vollständigen Protokolldateipfad angeben. 
- Sie können für die Protokollsammlung Umgebungsvariablen angeben, wie z.B. die folgenden:<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- Nur exakte Dateierweiterungen sind zulässig wie z.B.:<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- Es können maximal 60 MB oder 25 Dateien hochgeladen werden, je nachdem, was zuerst der Fall ist. 
- Die Sammlung von Win32-App-Installationsprotokollen ist für Apps aktiviert, die die App-Zuweisungsabsicht (Erforderlich, Verfügbar und Deinstallieren) erfüllen.
- Gespeicherte Protokolle werden verschlüsselt, um alle personenbezogenen Informationen zu schützen, die in den Protokollen enthalten sind.
- Wenn Sie Supporttickets für Win32-App-Fehler öffnen, fügen Sie die zugehörigen Fehlerprotokolle wie vorstehend beschrieben hinzu.

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Problembehandlung bei Apps aus dem Microsoft Store

Mithilfe der Informationen im Artikel [Problembehandlung beim Packen, Bereitstellen und Abfragen von Microsoft Store-Apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) können Sie allgemeine Probleme beheben, die bei der Installation von Apps aus dem Microsoft Store (mit Intune oder mittels anderer Tools) auftreten können.

## <a name="app-troubleshooting-resources"></a>Ressourcen zur Problembehandlung für Apps
- [Bereitstellen von Visio und Project als Teil Ihrer Office Pro Plus-Bereitstellung](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Maßnahmen ergreifen, um sicherzustellen, dass über Intune bereitgestellte Microsoft Store for Business-Apps mit der Windows 10-Version 1903 installiert werden](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Fehlerbehebung bei Bereitstellungen von MSI-Apps in Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Best Practices für die Verteilung von Intune-Software auf Windows-Computer](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zur Intune-Problembehandlung finden Sie unter [Verwenden des Problembehandlungsportals zur Unterstützung von Benutzern Ihres Unternehmens](../fundamentals/help-desk-operators.md). 
- Erfahren Sie mehr über bekannte Probleme in Microsoft Intune. Weitere Informationen finden Sie unter [Mit Intune zum Kundenerfolg](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- Benötigen Sie zusätzliche Hilfe? Weitere Informationen finden Sie unter [Anfordern von Support für Microsoft Intune](../fundamentals/get-support.md).
