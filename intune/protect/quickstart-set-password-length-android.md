---
title: 'Schnellstart: Konformitätsrichtlinie für Kennwörter für Android-Geräte'
titleSuffix: Microsoft Intune
description: In diesem Schnellstart erfahren Sie, wie Sie mithilfe von Microsoft Intune eine erforderliche Kennwortlänge für Android-Geräte festlegen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2969c57a598acbc0239e07d4ed347739c9719c2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726855"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>Schnellstart: Erstellen einer Konformitätsrichtlinie für Kennwörter für Android-Geräte

In diesem Schnellstart erfahren Sie, wie Sie mit Microsoft Intune für Ihre Mitarbeiter mit Android-Geräten festlegen, dass sie ein Kennwort mit einer bestimmten Länge angeben, bevor sie auf Informationen auf dem Gerät zugreifen können. 

Mit einer Konformitätsrichtlinie für Intune-Geräte werden die Regeln und Einstellungen festgelegt, die diese Geräte erfüllen müssen, um als konform angesehen zu werden. Sie können Konformitätsrichtlinien zusammen mit bedingtem Zugriff verwenden, um den Zugriff auf Unternehmensressourcen zuzulassen oder zu blockieren. Außerdem können Sie Geräteberichte abrufen und bei Nichtkonformität Aktionen durchführen.

> [!IMPORTANT]
> Berücksichtigen Sie neben den Kennworteinstellungen auch andere Systemsicherheitseinstellungen, um Ihre Mitarbeiter zu schützen. Weitere Informationen finden Sie unter [Einstellungen für die Systemsicherheit](compliance-policy-create-android-for-work.md).

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als globaler Administrator oder als Intune-Dienstadministrator. 

## <a name="create-a-device-compliance-policy"></a>Erstellen einer Gerätekonformitätsrichtlinie

In diesem Schnellstart erfahren Sie, wie Sie mit Intune für Ihre Mitarbeiter mit Android-Geräten festlegen, dass sie ein Kennwort mit einer bestimmten Länge eingeben, bevor sie auf Informationen auf dem Gerät zugreifen können.

1. Wählen Sie in Intune **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** aus.
2. Fügen Sie als **Name** **Android-Kompatibilität** hinzu. Geben Sie auch eine **Beschreibung** ein.
3. Wählen Sie als **Plattform** die Option **Android** aus. 
4. Wählen Sie **Einstellungen** > **Systemsicherheit** aus, um das Blatt **Systemsicherheit** für Android-Geräte anzuzeigen.
5. Klicken Sie neben **Require a password to unlock mobile devices** (Ein Kennwort zum Entsperren von Mobilgeräten anfordern) auf **Anfordern**.
6. Wählen Sie für **Mindestens numerisch** die Option **Erforderlicher Kennworttyp** aus.
7. Geben Sie neben **Minimale Kennwortlänge** **6** ein. 

    ![Screenshot: Erstellen einer Gruppe in Microsoft Intune](./media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

7. Klicken Sie anschließend auf **OK** > **OK** > **Erstellen**, um die Richtlinie zu erstellen.

Wenn Sie die Richtlinie erfolgreich erstellt haben, erscheint sie in der Liste der Gerätekonformitätsrichtlinien. 

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Löschen Sie die Richtlinie, wenn Sie sie nicht länger benötigen. Wählen Sie dafür die entsprechende Konformitätsrichtlinie aus, und klicken Sie auf **Löschen**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie mit Intune eine Kompatibilitätsrichtlinie für die Android-Geräte Ihrer Mitarbeiter erstellt, die ein Kennwort mit einer Mindestlänge von sechs Zeichen erfordert. Weitere Informationen über Gerätekonformitätsrichtlinien finden Sie unter [Erste Schritte mit den Gerätekonformitätsrichtlinien in Intune](device-compliance-get-started.md).

Weitere Informationen zu Intune erhalten Sie im nächsten Schnellstart.

> [!div class="nextstepaction"]
> [Schnellstart: Senden von Benachrichtigungen an nicht konforme Geräte](../quickstart-send-notification.md)
