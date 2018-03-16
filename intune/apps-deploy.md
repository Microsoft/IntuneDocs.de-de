---
title: Zuweisen von Apps zu Gruppen in Microsoft Intune
titlesuffix: 
description: "Nachdem Sie eine App zu Microsoft Intune hinzugefügt haben, sollten Sie sie Gruppen von Benutzern oder Geräten zuweisen."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 78a9e9f4af41cdb97efd017eec56e676eda82856
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Zuweisen von Apps zu Gruppen mit Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Nachdem Sie eine App in Intune hinzugefügt haben, können Sie diese Benutzern und Geräten zuweisen.

Apps können Geräten zugewiesen werden, und zwar unabhängig davon, ob sie von Intune verwaltet werden. In der folgenden Tabelle werden die verschiedenen Optionen für die Zuweisung von Apps zu Benutzern und Geräten erläutert:

||||
|-|-|-|-|
|&nbsp;|Bei Intune registrierte Geräte|Nicht bei Intune registrierte Geräte|
|Zuweisen zu Benutzern|Ja |Ja |
|Zuweisen zu Geräten|Ja |Nein|
|Zuweisen umschlossener Apps oder von Apps aus dem Intune SDK (für App-Schutzrichtlinien)|Ja |Ja |
|Zuweisen von Apps als verfügbar|Ja |Ja |
|Zuweisen von Apps als erforderlich|Ja |Nein|
|Deinstallieren von Apps|Ja |Nein|
|Erhalten von App-Updates von Intune|Ja |Nein|
|Endbenutzer installieren verfügbare Apps über die Unternehmensportal-App|Ja |Nein|
|Endbenutzer installieren verfügbare Apps über das webbasierte Unternehmensportal|Ja |Ja |

> [!NOTE]
> Derzeit können Sie iOS- und Android-Apps (Branchen-Apps und Apps aus dem Store) Geräten zuweisen, die nicht bei Intune registriert sind.<br></br><br></br>
> Um App-Updates zu Geräten zu erhalten, die nicht bei Intune registriert sind, müssen Gerätebenutzer zu ihrem Unternehmensportal navigieren und App-Updates manuell installieren.

## <a name="how-to-assign-an-app"></a>Zuweisen einer App

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie auf dem Blatt **Intune** die Option **Mobile Apps** aus.
1. Wählen Sie in der Workload **Mobile Apps** die Option **Verwalten** > **Apps** aus.
2. Klicken Sie auf dem Blatt mit der Liste der Apps auf die App, die Sie zuweisen möchten.
3. Wählen Sie auf dem Blatt **Übersicht** die Option **Verwalten** > **Zuweisungen** aus.
4. Wählen Sie **Gruppe hinzufügen** und anschließend auf dem Blatt **Gruppe hinzufügen** die Azure AD-Gruppen aus, die Sie bei der Zuweisung der Gruppe einbeziehen bzw. ausschließen möchten.
5. Wählen Sie für jede ausgewählte App einen **Zuweisungstyp** aus:
    - **Verfügbar für registrierte Geräte:**  Benutzer installieren die App über die Unternehmensportal-App oder -Website.
    - **Verfügbar ohne Registrierung:** Weisen Sie diese App Benutzergruppen zu, deren Geräte nicht bei Intune registriert sind.
    - **Erforderlich:** Die App wird auf Geräten in den ausgewählten Gruppen installiert.
    - **Deinstallieren:** Die App wird auf Geräten in den ausgewählten Gruppen deinstalliert.
6. **Nur für iOS-Apps**: Wenn Sie ein iOS-VPN-Profil erstellt haben, das VPN pro App-Einstellungen enthält, können Sie es unter **VPN** auswählen. Wenn die App ausgeführt wird, wird die VPN-Verbindung geöffnet. Weitere Informationen finden Sie unter [VPN-Einstellungen für iOS-Geräte](vpn-settings-ios.md).
6. Wählen Sie abschließend **OK** und dann **Speichern** aus.

Die App wird jetzt den von Ihnen ausgewählten Gruppen zugewiesen.

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Auflösung von Konflikten zwischen App-Absichten

In manchen Fällen wird die gleiche App mehreren Gruppen zugewiesen, jedoch mit unterschiedlichen Absichten. Verwenden Sie in diesen Fällen diese Tabelle, um die sich ergebende Absicht zu verstehen.

||||
|-|-|-|
|Absicht Gruppe 1|Absicht Gruppe 2|Resultierende Absicht|
|Erforderlicher Benutzer|Verfügbarer Benutzer|Erforderlich und Verfügbar|
|Erforderlicher Benutzer|Benutzer nicht verfügbar|Erforderlich|
|Erforderlicher Benutzer|Benutzerdeinstallation|Erforderlich|
|Verfügbarer Benutzer|Benutzer nicht verfügbar|Nicht verfügbar|
|Verfügbarer Benutzer|Benutzerdeinstallation|Deinstallieren|
|Benutzer nicht verfügbar|Benutzerdeinstallation|Deinstallieren
|Erforderlicher Benutzer|Erforderliches Gerät|Beides vorhanden, Gateway behandelt Erforderliches 
|Erforderlicher Benutzer|Gerätedeinstallation|Beides vorhanden, Gateway löst Erforderliches 
|Verfügbarer Benutzer|Erforderliches Gerät|Beides vorhanden, Gateway löst Erforderliches (Erforderlich und Verfügbar)
|Verfügbarer Benutzer|Gerätedeinstallation|Beides vorhanden, Gateway löst Verfügbares.<br>App wird im Unternehmensportal angezeigt.<br>Wenn die App bereits installiert wurde (als erforderliche App mit vorheriger Absicht), wird die App deinstalliert.<br>Wenn der Benutzer über das Unternehmensportal auf „Installieren“ klickt, wird die App installiert und die deinstallierte Absicht wird nicht berücksichtigt.|
|Benutzer nicht verfügbar|Erforderliches Gerät|Erforderlich|
|Benutzer nicht verfügbar|Gerätedeinstallation|Deinstallieren|
|Benutzerdeinstallation|Erforderliches Gerät|Beides vorhanden, Gateway löst Erforderliches|
|Benutzerdeinstallation|Gerätedeinstallation|Beides vorhanden, Gateway löst Deinstallation|
|Erforderliches Gerät|Gerätedeinstallation|Erforderlich|
|Erforderlicher und verfügbarer Benutzer|Verfügbarer Benutzer|Erforderlich und Verfügbar|
|Erforderlicher und verfügbarer Benutzer|Benutzerdeinstallation|Erforderlich und Verfügbar|
|Erforderlicher und verfügbarer Benutzer|Benutzer nicht verfügbar|Erforderlich und Verfügbar|
|Erforderlicher und verfügbarer Benutzer|Erforderliches Gerät|Beides vorhanden, Erforderlich und Verfügbar
|Erforderlicher und verfügbarer Benutzer|Gerät nicht verfügbar|Erforderlich und Verfügbar|
|Erforderlicher und verfügbarer Benutzer|Gerätedeinstallation|Beides vorhanden, Gateway löst Erforderliches. Erforderlich und verfügbar
|Benutzer nicht verfügbar|Gerät nicht verfügbar|Nicht verfügbar|
|Verfügbarer Benutzer|Gerät nicht verfügbar|Verfügbar|
|Erforderlicher Benutzer|Gerät nicht verfügbar|Erforderlich|
|Benutzer verfügbar ohne Registrierung|Erforderlicher und verfügbarer Benutzer|Erforderlich und Verfügbar
|Benutzer verfügbar ohne Registrierung|Erforderlicher Benutzer|Erforderlich
|Benutzer verfügbar ohne Registrierung|Benutzer nicht verfügbar|Nicht verfügbar
|Benutzer verfügbar ohne Registrierung|Verfügbarer Benutzer|Verfügbar|
|Benutzer verfügbar ohne Registrierung|Erforderliches Gerät|Erforderlich und verfügbar ohne Registrierung|
|Benutzer verfügbar ohne Registrierung|Gerät nicht verfügbar|Verfügbar ohne Registrierung|
|Benutzer verfügbar ohne Registrierung|Gerätedeinstallation|Deinstallation und verfügbar ohne Registrierung.<br>Wenn der Benutzer die App nicht über das Unternehmensportal installiert hat, wird die Deinstallation berücksichtigt.<br>Wenn der Benutzer die App über das Unternehmensportal installiert, wird die Installation gegenüber der Deinstallation bevorzugt.|

>[!NOTE]
>Nur für verwaltete iOS Store-Apps: Falls Sie diese Intune hinzufügen und als „Erforderlich“ zuweisen, werden sie automatisch jeweils mit der Absicht „Erforderlich“ und „Verfügbar“ erstellt.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Überwachen von App-Zuweisungen finden Sie unter [Überwachen von Apps](apps-monitor.md).
