---
title: 'Schnellstart: Festlegen einer erforderlichen Kennwortlänge für Android-Geräte'
titlesuffix: Microsoft Intune
description: In diesem Schnellstart legen Sie mithilfe von Microsoft Intune eine erforderliche Kennwortlänge für Android-Geräte fest.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f925df731c3ddd45b13d976b0686d76d941c71e6
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "49395283"
---
# <a name="quickstart-set-a-required-password-length-for-android-devices"></a>Schnellstart: Festlegen einer erforderlichen Kennwortlänge für Android-Geräte

In diesem Schnellstart erfahren Sie, wie Sie mit Microsoft Intune für Ihre Mitarbeiter mit Android-Geräten festlegen, dass sie ein Kennwort mit einer bestimmten Länge angeben, bevor sie auf Informationen auf dem Gerät zugreifen können. 

> [!IMPORTANT]
> Berücksichtigen Sie neben den Kennworteinstellungen auch andere Systemsicherheitseinstellungen, um Ihre Mitarbeiter zu schützen. Weitere Informationen finden Sie unter [Einstellungen für die Systemsicherheit](compliance-policy-create-android-for-work.md#system-security-settings).

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als globaler Administrator oder als Intune-Dienstadministrator. Intune finden Sie im Azure-Portal, indem Sie **Alle Dienste** > **Intune** auswählen. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.

## <a name="create-a-device-compliance-policy"></a>Erstellen einer Gerätekonformitätsrichtlinie
1. Wenn das Blatt **Microsoft Intune** geöffnet ist, wählen Sie **Gerätekompatibilität** > **Richtlinien** > **Richtlinie erstellen** aus.
2. Fügen Sie als **Name** **Android-Kompatibilität** hinzu. Geben Sie auch eine **Beschreibung** ein.
3. Wählen Sie als **Plattform** die Option **Android** aus. 
4. Wählen Sie **Einstellungen** > **Systemsicherheit** aus, um das Blatt **Systemsicherheit** für Android-Geräte anzuzeigen.
5. Klicken Sie im Abschnitt **Kennwort** neben **Kennwort zum Entsperren mobiler Geräte erforderlich** auf **Erforderlich**.
6. Geben Sie neben **Minimale Kennwortlänge** **6** ein.  

    ![Screenshot: Erstellen einer Gruppe in Microsoft Intune](./media/quickstart-set-password-length-android-01.png)

7. Wenn Sie fertig sind, klicken Sie auf **OK**, um das Blatt **Systemsicherheit** zu schließen. 
8. Klicken Sie auf **OK**, um das Blatt **Android-Kompatibilitätsrichtlinie** zu schließen. 
9. Klicken Sie auf **Erstellen**, um die Richtlinie zu erstellen.

Wenn Sie die Richtlinie erfolgreich erstellt haben, erscheint sie in der Liste **Gerätekompatibilität – Richtlinien**. 

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie mit Intune eine Kompatibilitätsrichtlinie für die Android-Geräte Ihrer Mitarbeiter erstellt, die ein Kennwort mit einer Mindestlänge von sechs Zeichen erfordert.

> [!div class="nextstepaction"]
> [Set up automatic enrollment (Festlegen der automatischen Registrierung)](quickstart-setup-auto-enrollment.md)
