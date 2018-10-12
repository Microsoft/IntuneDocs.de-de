---
title: 'Schnellstart: Einrichten der automatischen Registrierung in Intune'
description: 'Schnellstart: Einrichten der automatischen Registrierung für Windows 10-Geräte in Intune'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 3b713f090fb6ada884a269e286f55f6e1b1087c4
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581649"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Schnellstart: Einrichten der automatischen Registrierung für Windows 10-Geräte

In dieser Schnellstartanleitung richten Sie Microsoft Intune so ein, dass Geräte automatisch registriert werden, wenn sich bestimmte Benutzer auf Windows 10-Geräten anmelden.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

- Um dieser Schnellstartanleitung zu folgen, müssen Sie zunächst [einen Benutzer](quickstart-create-user.md) und [eine Gruppe erstellen](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als globaler Administrator oder als Intune-Dienstadministrator.

## <a name="set-up-windows-10-automatic-enrollment"></a>Einrichten der automatischen Registrierung von Windows 10

Für dieses Beispiel verwenden Sie die MDM-Registrierung, sodass die unternehmenseigenen Gerte und BYO-Geräte automatisch registriert werden können.

1. Wählen Sie in Azure **Azure Active Directory** > **Mobilität (MDM und MAM)** > **Microsoft Intune** > **Einige** aus.
![Browser](media/quickstart-setup-auto-enrollment/setup-automatic-enrollment-win10.png)
2. Klicken Sie auf **Gruppen auswählen** > **Contoso Tester** > **Auswählen**.
3. Verwenden Sie die Standardwerte für die folgenden URLs:
    - URL für MDM-Nutzungsbedingungen
    - URL für MDM-Ermittlung
    - MDM Compliance-URL
4. Wählen Sie **Speichern** aus.
5. Melden Sie sich als Benutzer in der Gruppe auf einem Windows 10-Gerät an, und befolgen Sie die Anweisungen.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Lesen Sie den Artikel [Registrierung von Windows-Geräten](windows-enroll.md), um die automatische Registrierung von Intune neu zu konfigurieren.

## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung haben Sie gelernt, wie die automatische Registrierung für Windows 10-Geräte eingerichtet wird. Sie erhalten auf allen Plattformen Informationen zu weiteren Möglichkeiten, Geräte zu registrieren.

> [!div class="nextstepaction"]
> [Artikel: Was ist die Geräteregistrierung?](device-enrollment.md)