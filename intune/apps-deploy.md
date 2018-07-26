---
title: Zuweisen von Apps zu Gruppen in Microsoft Intune
titlesuffix: ''
description: Informationen zum Zuweisen einer Intune-App zu Gruppen von Benutzern oder Geräten.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 46ef614af39a1dd1b44f4f5ff32f53687ccb060a
ms.sourcegitcommit: a8b544975156dd45c2bf215b57ac994415b568bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39164568"
---
# <a name="assign-apps-to-groups-with-microsoft-intune"></a>Zuweisen von Apps zu Gruppen mit Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Nachdem Sie Microsoft Intune [eine App hinzugefügt](apps-add.md) haben, können Sie diese Benutzern und Geräten zuweisen. Beachten Sie: Sie können eine App einem Gerät unabhängig davon zuweisen, ob das Gerät von Intune verwaltet wird. 

In der folgenden Tabelle werden die verschiedenen Optionen für die Zuweisung von Apps zu Benutzern und Geräten erläutert:

||||
|-|-|-|-|
|&nbsp;|**Bei Intune registrierte Geräte**|**Nicht bei Intune registrierte Geräte**|
|Zuweisen zu Benutzern|Ja |Ja |
|Zuweisen zu Geräten|Ja |Nein|
|Zuweisen von umschlossenen Apps oder Apps, die das Intune SDK enthalten (für App-Schutzrichtlinien)|Ja |Ja |
|Zuweisen von Apps als verfügbar|Ja |Ja |
|Zuweisen von Apps als erforderlich|Ja |Nein|
|Deinstallieren von Apps|Ja |Nein|
|Erhalten von App-Updates von Intune|Ja |Nein|
|Endbenutzer installieren verfügbare Apps über die Unternehmensportal-App|Ja |Nein|
|Endbenutzer installieren verfügbare Apps über das webbasierte Unternehmensportal|Ja |Ja |

> [!NOTE]
> Derzeit können Sie iOS- und Android-Apps (Branchen-Apps und Apps aus dem Store) Geräten zuweisen, die nicht bei Intune registriert sind.
>
> Um App-Updates zu Geräten zu erhalten, die nicht bei Intune registriert sind, müssen Gerätebenutzer zum Unternehmensportal Ihrer Organisation navigieren und App-Updates manuell installieren.

## <a name="to-assign-an-app"></a>So weisen Sie eine App zu

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Menü **Intune** die Option **Mobile Apps** aus.
4. Wählen Sie im Abschnitt **Verwalten** des Menüs **Apps** aus.
5. Wählen Sie im Bereich **Apps** die App aus, die Sie zuweisen möchten.
6. Wählen Sie im Abschnitt **Verwalten** des Menüs **Zuweisungen** aus.
7. Wählen Sie **Gruppe hinzufügen** aus, um den Bereich **Gruppe hinzufügen** zu öffnen, der mit der App verknüpft ist.
8. Wählen Sie für die bestimmte App einen **Zuweisungstyp** aus:
   - **Für registrierte Geräte verfügbar**: Benutzer installieren die App über die Unternehmensportal-App oder -Website.
   - **Verfügbar mit oder ohne Registrierung**: Weisen Sie diese App Benutzergruppen zu, deren Geräte nicht bei Intune registriert sind. Apps von Managed Google Play unterstützen diese Option nicht. 
   - **Erforderlich**: Die App wird auf Geräten in den ausgewählten Gruppen installiert.
   - **Deinstallieren**: Die App wird auf Geräten in den ausgewählten Gruppen deinstalliert.

     > [!NOTE]
     > **Nur für iOS-Apps**: Wenn Sie ein iOS-VPN-Profil erstellt haben, das Pro-App-VPN-Einstellungen enthält, können Sie es unter **VPN** auswählen. Wenn die App ausgeführt wird, wird die VPN-Verbindung geöffnet. Weitere Informationen finden Sie unter [VPN-Einstellungen für iOS-Geräte](vpn-settings-ios.md).

9. Um die Benutzergruppen auszuwählen, denen diese App zugewiesen werden soll, wählen Sie **Eingeschlossene Gruppen** aus.
10. Wenn Sie mindestens eine Gruppe ausgewählt haben, die eingeschlossen werden soll, wählen Sie **Auswählen** aus.
11. Wählen Sie im Bereich **Zuweisen** die Option **OK** aus, um die Auswahl der eingeschlossenen Gruppe abzuschließen.
12. Wenn Sie Benutzergruppen von dieser App-Zuweisung ausschließen möchten, wählen Sie **Gruppen ausschließen** aus.
13. Wenn Sie auszuschließende Gruppen ausgewählt haben, wählen Sie in **Gruppen auswählen** die Option **Auswählen** aus.
14. Wählen Sie im Bereich **Gruppe hinzufügen** die Option **OK** aus.
15. Wählen Sie im Bereich **Zuweisungen** die Option **Speichern** aus.

Die App wird jetzt den von Ihnen ausgewählten Gruppen zugewiesen. Weitere Informationen zum Ein- und Ausschließen von App-Zuweisungen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen](apps-inc-exl-assignments.md).

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Auflösung von Konflikten zwischen App-Absichten

In manchen Fällen wird die gleiche App mehreren Gruppen zugewiesen, jedoch mit unterschiedlichen Absichten. Verwenden Sie in diesen Fällen diese Tabelle, um die sich ergebende Absicht zu verstehen:

||||
|-|-|-|
|**Absicht Gruppe 1**|**Absicht Gruppe 2**|**Resultierende Absicht**|
|Erforderlicher Benutzer|Verfügbarer Benutzer|Erforderlich und Verfügbar|
|Erforderlicher Benutzer|Benutzer nicht verfügbar|Erforderlich|
|Erforderlicher Benutzer|Benutzerdeinstallation|Erforderlich|
|Verfügbarer Benutzer|Benutzer nicht verfügbar|Nicht verfügbar|
|Verfügbarer Benutzer|Benutzerdeinstallation|Deinstallieren|
|Benutzer nicht verfügbar|Benutzerdeinstallation|Deinstallieren
|Erforderlicher Benutzer|Erforderliches Gerät|Beides vorhanden, Intune behandelt Erforderliches
|Erforderlicher Benutzer|Gerätedeinstallation|Beides vorhanden, Intune löst Erforderliches auf
|Verfügbarer Benutzer|Erforderliches Gerät|Beides vorhanden, Intune löst Erforderliches auf (Erforderlich und Verfügbar)
|Verfügbarer Benutzer|Gerätedeinstallation|Beides vorhanden, Intune löst Verfügbares auf<br><br>App wird im Unternehmensportal angezeigt.<br><br>Wenn die App bereits installiert wurde (als erforderliche App mit vorheriger Absicht), wird die App deinstalliert.<br><br>Wenn der Benutzer **Über das Unternehmensportal installieren** auswählt, wird die App installiert und die Deinstallationsabsicht nicht berücksichtigt.|
|Benutzer nicht verfügbar|Erforderliches Gerät|Erforderlich|
|Benutzer nicht verfügbar|Gerätedeinstallation|Deinstallieren|
|Benutzerdeinstallation|Erforderliches Gerät|Beides vorhanden, Intune löst Erforderliches auf|
|Benutzerdeinstallation|Gerätedeinstallation|Beides vorhanden, Intune löst Deinstallation auf|
|Erforderliches Gerät|Gerätedeinstallation|Erforderlich|
|Erforderlicher und verfügbarer Benutzer|Verfügbarer Benutzer|Erforderlich und Verfügbar|
|Erforderlicher und verfügbarer Benutzer|Benutzerdeinstallation|Erforderlich und Verfügbar|
|Erforderlicher und verfügbarer Benutzer|Benutzer nicht verfügbar|Erforderlich und Verfügbar|
|Erforderlicher und verfügbarer Benutzer|Erforderliches Gerät|Beides vorhanden, erforderlich und verfügbar
|Erforderlicher und verfügbarer Benutzer|Gerät nicht verfügbar|Erforderlich und Verfügbar|
|Erforderlicher und verfügbarer Benutzer|Gerätedeinstallation|Beides vorhanden, Intune löst Erforderliches auf (Erforderlich und Verfügbar)
|Benutzer nicht verfügbar|Gerät nicht verfügbar|Nicht verfügbar|
|Verfügbarer Benutzer|Gerät nicht verfügbar|Verfügbar|
|Erforderlicher Benutzer|Gerät nicht verfügbar|Erforderlich|
|Benutzer verfügbar ohne Registrierung|Erforderlicher und verfügbarer Benutzer|Erforderlich und Verfügbar
|Benutzer verfügbar ohne Registrierung|Erforderlicher Benutzer|Erforderlich
|Benutzer verfügbar ohne Registrierung|Benutzer nicht verfügbar|Nicht verfügbar
|Benutzer verfügbar ohne Registrierung|Verfügbarer Benutzer|Verfügbar|
|Benutzer verfügbar ohne Registrierung|Erforderliches Gerät|Erforderlich und verfügbar ohne Registrierung|
|Benutzer verfügbar ohne Registrierung|Gerät nicht verfügbar|Verfügbar ohne Registrierung|
|Benutzer verfügbar ohne Registrierung|Gerätedeinstallation|Deinstallation und verfügbar ohne Registrierung.<br><br>Wenn der Benutzer die App nicht über das Unternehmensportal installiert hat, wird die Deinstallation berücksichtigt.<br><br>Wenn der Benutzer die App über das Unternehmensportal installiert, wird die Installation gegenüber der Deinstallation bevorzugt.|

> [!NOTE]
> Nur für verwaltete iOS Store-Apps: Wenn Sie diese Apps Microsoft Intune hinzufügen und als **Erforderlich** zuweisen, werden sie automatisch sowohl mit der Absicht **Erforderlich** als auch mit der Absicht **Verfügbar** erstellt.<br><br>
> iOS Store-Apps (keine iOS-VPP-Apps), die mit der Absicht „Erforderlich“ als Ziel verwendet werden, werden auf dem Gerät beim Check-In erzwungen und in der Unternehmensportal-App angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Überwachen von App-Zuweisungen finden Sie unter [Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune](apps-monitor.md).
