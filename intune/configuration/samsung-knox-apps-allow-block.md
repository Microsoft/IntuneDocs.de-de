---
title: Microsoft Intune-Richtlinie zum Zulassen/Blockieren von Apps für Samsung KNOX
titleSuffix: ''
description: Erstellen eines benutzerdefinierten Profils zum Zulassen und Blockieren von Apps für Samsung KNOX Standard-Geräte
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a8486e121e6497eefdd2d098c2421f2f3b53b8a2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734348"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Verwenden von benutzerdefinierten Richtlinien zum Zulassen und Blockieren von Apps für Samsung KNOX Standardgeräte in Microsoft Intune 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Verwenden Sie die in diesem Artikel beschriebenen Verfahren, um eine benutzerdefinierte Microsoft Intune-Richtlinie zu erstellen, die eine der folgenden Listen erstellt:

- Eine Liste von Apps, deren Ausführung auf dem Gerät blockiert wird. Die Ausführung der Apps in dieser Liste wird blockiert, auch wenn diese bereits vor der Anwendung der Richtlinie installiert waren.
- Eine Liste von Apps, die Benutzer des Geräts aus dem Google Play Store installieren dürfen. Nur die aufgelisteten Apps können installiert werden. Es können keine anderen Apps aus dem Store installiert werden.

Diese Einstellungen können nur von Geräten verwendet werden, auf denen Samsung KNOX Standard ausgeführt wird.

## <a name="create-an-allowed-or-blocked-app-list"></a>Erstellen einer Liste mit zulässigen oder blockierten Apps

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** die Option **Gerätekonfiguration** aus.
2. Klicken Sie im Bereich **Gerätekonfiguration** auf **Verwalten** > **Profile**.
2. Klicken Sie in dem Bereich mit der Profilliste auf die Option **Profil erstellen**.
3. Geben Sie im Bereich **Profil erstellen** einen **Namen** und eine optionale **Beschreibung** für dieses Geräteprofil ein.
2. Wählen Sie als **Plattform** die Option **Android** und als **Profiltyp** **Benutzerdefiniert** aus.
3. Klicken Sie auf **Einstellungen**.
3. Klicken Sie im Bereich **Custom OMA-URI Settings** (Benutzerdefinierte OMA-URI-Einstellungen) auf **Hinzufügen**.
4. Geben Sie im Dialogfeld **Add or Edit OMA-URI Setting** (OMA-URI-Einstellung hinzufügen oder bearbeiten) die folgende Einstellungen an:

   Für eine Liste von Apps, deren Ausführung auf dem Gerät blockiert wird:

   - **Name:** Geben Sie **PreventStartPackages** ein.
   - **Beschreibung:** Geben Sie optional eine Beschreibung wie z.B. „Liste der Apps, deren Ausführung blockiert wird“ ein.
   - **Datentyp:** Wählen Sie in der Dropdownliste **Zeichenfolge** aus.
   - **OMA-URI:** Geben Sie **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages** ein.
   - **Wert:** Geben Sie eine Liste mit den Namen der App-Pakete ein, die Sie zulassen möchten. Sie können **; : ,** oder **|** als Trennzeichen verwenden. (Beispiel: Paket1; Paket2;)

   Für eine Liste von Apps, die Benutzer des Geräts aus Google Play Store installieren dürfen, wobei alle anderen Apps ausgeschlossen werden:
   - **Name:** Geben Sie **AllowInstallPackages** ein.
   - **Beschreibung:** Geben Sie optional eine Beschreibung wie z.B. „Liste der Apps, die Benutzer aus Google Play installieren dürfen“ ein.
   - **Datentyp:** Wählen Sie in der Dropdownliste **Zeichenfolge** aus.
   - **OMA-URI:** Geben Sie **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages** ein.
   - **Wert:** Geben Sie eine Liste mit den Namen der App-Pakete ein, die Sie zulassen möchten. Sie können **; : ,** oder **|** als Trennzeichen verwenden. (Beispiel: Paket1; Paket2;)

4. Klicken Sie auf **OK**, und klicken Sie dann im Bereich **Profil erstellen** auf die Option **Erstellen**.

>[!TIP]
> Sie finden die Paket-ID einer App, indem Sie im Google Play Store zu der App navigieren. Die Paket-ID ist in der URL der Seite der App enthalten. Die Paket-ID der Microsoft Word-App lautet z.B. **com.microsoft.office.word**.

Die App-Einstellungen werden beim nächsten Einchecken jedes Zielgeräts angewendet.


<!---## Assign the custom profile--->