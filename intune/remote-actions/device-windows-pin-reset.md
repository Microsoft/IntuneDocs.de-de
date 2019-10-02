---
title: 'Zurücksetzen der Kennung auf Windows-Geräten mit Microsoft Intune: Azure | Microsoft-Dokumentation'
description: 'Gehen Sie zum Zurücksetzen der Kennung auf Windows-Geräten wie folgt vor: Installieren Sie den PIN-Zurücksetzungsdienst und den PIN-Zurücksetzungsclient von Microsoft, erstellen Sie eine Geräterichtlinie mit Ihrer Azure Active Directory-Verzeichnis-ID, und setzen Sie die Kennung im Azure-Portal mithilfe von Microsoft-Intune zurück.'
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cb34490b6b88d6a62fa9fb29a64b7a391eed7c6b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728428"
---
# <a name="reset-the-passcode-on-windows-devices-using-intune"></a>Zurücksetzen der Kennung auf Windows-Geräten mit Intune

Sie können die Kennung für Windows-Geräte zurücksetzen. Das Feature zum Zurücksetzen der Kennung verwendet den PIN-Zurücksetzungsdienst, um eine neue Kennung für Geräte zu erstellen, auf denen Windows 10 Mobile ausgeführt wird. 

## <a name="supported-platforms"></a>Unterstützte Plattformen

- Windows 10 Mobile mit Windows 10 Creators Update oder höher (verknüpftes Azure AD).

Die folgenden Plattformen werden **nicht** unterstützt:
- Windows
- iOS
- macOS
- Android

## <a name="authorize-the-pin-reset-services"></a>Autorisieren des PIN-Zurücksetzungsdiensts

Integrieren Sie den PIN-Zurücksetzungsdienst in Ihren Intune-Mandanten, um die Kennung auf Windows-Geräten zurückzusetzen.

1. Navigieren Sie zum [Microsoft PIN Reset Service production](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent) (Microsoft-PIN-Zurücksetzungsdienst für die Produktion), und melden sich mit dem Mandantenadministratorkonto an.
2. Klicken Sie auf **Akzeptieren**, um dem PIN-Zurücksetzungsdienst zu erlauben, auf Ihr Konto zuzugreifen: ![Berechtigungsanforderung zum Zurücksetzen der PIN für den Server akzeptieren](./media/device-windows-pin-reset/pin-reset-service-home-screen.png)
3. Navigieren Sie zum [Client des PIN-Zurücksetzungsdiensts von Microsoft](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent), und melden sich mit dem Mandantenadministratorkonto an. Klicken Sie auf **Akzeptieren**, um dem PIN-Zurücksetzungsclient zu erlauben, auf Ihr Konto zuzugreifen.
4. Überprüfen Sie im [Azure-Portal](https://portal.azure.com), ob die PIN-Zurücksetzungsdienste unter „Enterprise applications (All applications)“ (Unternehmensanwendungen (Alle Anwendungen)) aufgelistet sind: ![Berechtigungsseite für den PIN-Zurücksetzungsdienst](./media/device-windows-pin-reset/pin-reset-service-application.png)

> [!NOTE]
> Nachdem Sie die Anforderung der PIN-Zurücksetzung akzeptiert haben, wird Ihnen möglicherweise die Meldung `Page not found` angezeigt, oder es scheint, als würde nichts passieren. Dieses Verhalten ist normal. Achten Sie darauf, dass die beiden Anwendungen für Ihren Mandanten aufgelistet sind.

## <a name="configure-windows-devices-to-use-pin-reset"></a>Konfigurieren von Windows-Geräten zur Verwendung des PIN-Zurücksetzungsdiensts

Verwenden Sie zum Konfigurieren der PIN-Zurücksetzung auf von Ihnen verwalteten Windows-Geräten eine [benutzerdefinierte Intune-Geräterichtlinie für Windows 10](../configuration/custom-settings-windows-10.md). Konfigurieren Sie die Richtlinie mithilfe des folgenden Konfigurationsdienstanbieters für Windows-Richtlinien (Configuration Service Provider, CSPs):

**Verwenden Sie die Geräterichtlinie** - `./Device/Vendor/MSFT/PassportForWork/*tenant ID*/Policies/EnablePinRecovery`

Ersetzen Sie die *Mandanten-ID* durch Ihre Azure AD-Verzeichnis-ID, die unter **Eigenschaften** in Azure Active Directory im [Azure-Portal](https://portal.azure.com) aufgeführt wird.

Legen Sie den Wert diesen CSP auf **TRUE** fest.

> [!TIP]
> Nachdem Sie eine Richtlinie erstellt haben, weisen Sie sie einer Gruppe zu (oder stellen Sie sie bereit). Die Richtlinie kann Benutzergruppen oder einer Gerätegruppe zugewiesen werden. Wenn Sie sie einer Benutzergruppe zuweisen, kann diese Gruppe Benutzer beinhalten, die andere Geräte verwenden, z.B. ein iOS-Gerät. Technisch gesehen gilt die Richtlinie nicht, dennoch werden diese Geräte in den Statusdetails aufgeführt.

## <a name="reset-the-passcode"></a>Zurücksetzen der Kennung

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an. 
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** > **Alle Geräte**.
4. Wählen Sie das Gerät aus, dessen Kennung Sie zurücksetzen möchten. Klicken Sie in den Geräteeigenschaften auf **Neue Kennung**.
5. Klicken Sie zum Bestätigen auf **Ja**. Die Kennung wird generiert und für die folgenden sieben Tage im Portal angezeigt.

## <a name="next-step"></a>Nächster Schritt

Sollte bei der Zurücksetzung der Kennung ein Fehler auftreten, wird im Portal ein Link mit weiteren Informationen angezeigt.
