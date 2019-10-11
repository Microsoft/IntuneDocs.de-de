---
title: Zuweisen von Apps zu Gruppen in Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie eine Intune-App mithilfe von Microsoft Intune einer Gruppe von Benutzern oder Geräten zuweisen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f0f00b635a04f4ffe5bc09489b9909e9243ee98
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725152"
---
# <a name="assign-apps-to-groups-with-microsoft-intune"></a>Zuweisen von Apps zu Gruppen mit Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Nachdem Sie Microsoft Intune [eine App hinzugefügt](apps-add.md) haben, können Sie diese Benutzern und Geräten zuweisen. Beachten Sie: Sie können eine App einem Gerät unabhängig davon zuweisen, ob das Gerät von Intune verwaltet wird.

> [!NOTE]
> Die Absicht „Verfügbare Bereitstellung“ wird nur für Benutzergruppen unterstützt, nicht für Gerätegruppen.

In der folgenden Tabelle werden die verschiedenen Optionen für die Zuweisung von Apps zu Benutzern und Geräten erläutert:

|   | Bei Intune registrierte Geräte | Nicht bei Intune registrierte Geräte |
|-------------------------------------------------------------------------------------------|------------------------------|----------------------------------|
| Zuweisen zu Benutzern | Ja | Ja |
| Zuweisen zu Geräten | Ja | Nein |
| Zuweisen von umschlossenen Apps oder Apps, die das Intune SDK enthalten (für App-Schutzrichtlinien) | Ja | Ja |
| Zuweisen von Apps als verfügbar | Ja | Ja |
| Zuweisen von Apps als erforderlich | Ja | Nein |
| Deinstallieren von Apps | Ja | Nein |
| Erhalten von App-Updates von Intune | Ja | Nein |
| Endbenutzer installieren verfügbare Apps über die Unternehmensportal-App | Ja | Nein |
| Endbenutzer installieren verfügbare Apps über das webbasierte Unternehmensportal | Ja | Ja |

> [!NOTE]
> Derzeit können Sie iOS- und Android-Apps (Branchen-Apps und Apps aus dem Store) Geräten zuweisen, die nicht bei Intune registriert sind.
>
> Um App-Updates zu Geräten zu erhalten, die nicht bei Intune registriert sind, müssen Gerätebenutzer zum Unternehmensportal Ihrer Organisation navigieren und App-Updates manuell installieren.

## <a name="assign-an-app"></a>Zuweisen einer App

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie im Abschnitt **Verwalten** des Menüs **Apps** aus.
5. Wählen Sie im Bereich **Apps** die App aus, die Sie zuweisen möchten.
6. Wählen Sie im Abschnitt **Verwalten** des Menüs **Zuweisungen** aus.
7. Wählen Sie **Gruppe hinzufügen** aus, um den Bereich **Gruppe hinzufügen** zu öffnen, der mit der App verknüpft ist.
8. Wählen Sie für die bestimmte App einen **Zuweisungstyp** aus:
   - **Für registrierte Geräte verfügbar**: Weisen Sie die App Gruppen von Benutzern zu, die die App über die Unternehmensportal-App oder -Website installieren können.
   - **Verfügbar mit oder ohne Registrierung**: Weisen Sie diese App Gruppen von Benutzern zu, deren Geräte nicht bei Intune registriert sind. Benutzern muss eine Intune-Lizenz zugewiesen sein. Weitere Informationen finden Sie unter [Intune-Lizenzen](../fundamentals/licenses.md).
   - **Erforderlich**: Die App wird auf Geräten in den ausgewählten Gruppen installiert. Auf einigen Plattformen muss der Endbenutzer möglicherweise weitere Eingabeaufforderungen bestätigen, bevor die App-Installation startet.
   - **Deinstallieren**: Die App wird auf Geräten in den ausgewählten Gruppen deinstalliert, wenn Intune die App zuvor über eine Zuweisung vom Typ „Für registrierte Geräte verfügbar“ oder „Erforderlich“ in der gleichen Bereitstellung auf dem Gerät installiert hat. Weblinks können nach der Bereitstellung nicht entfernt werden.

     > [!NOTE]
     > **Nur für iOS-Apps**:
     > - Sie können die Vorgehensweise für verwaltete Apps konfigurieren, wenn die Geräte nicht mehr verwaltet werden. Wählen Sie hierzu unter **Deinstallieren beim Entfernen des Geräts** die gewünschte Einstellung aus. Weitere Informationen finden Sie im Abschnitt [Einstellung zum Deinstallieren von Apps für verwaltete iOS-Apps](apps-deploy.md#app-uninstall-setting-for-ios-managed-apps).
     > - Wenn Sie ein iOS-VPN-Profil erstellt haben, das VPN-Einstellungen pro App enthält, können Sie dieses unter **VPN** auswählen. Wenn die App ausgeführt wird, wird die VPN-Verbindung geöffnet. Weitere Informationen finden Sie unter [VPN-Einstellungen für iOS-Geräte](../vpn-settings-ios.md).
     >
     > **Nur für Android-Apps**: Wenn Sie eine Android-App als **Verfügbar mit oder ohne Registrierung** bereitstellen, ist der Berichtsstatus nur auf registrierten Geräten verfügbar.
     >
     > **Für registrierte Geräte verfügbar**: Die App wird nur als verfügbar angezeigt, wenn der im Unternehmensportal angemeldete Benutzer auch der primäre Benutzer ist, der das Gerät registriert hat, und die App auf dem Gerät ausgeführt werden kann.

9. Um die Benutzergruppen auszuwählen, denen diese App zugewiesen werden soll, wählen Sie **Eingeschlossene Gruppen** aus.
10. Wenn Sie mindestens eine Gruppe ausgewählt haben, die eingeschlossen werden soll, wählen Sie **Auswählen** aus.
11. Wählen Sie im Bereich **Zuweisen** die Option **OK** aus, um die Auswahl der eingeschlossenen Gruppe abzuschließen.
12. Wenn Sie Benutzergruppen von dieser App-Zuweisung ausschließen möchten, wählen Sie **Gruppen ausschließen** aus.
13. Wenn Sie auszuschließende Gruppen ausgewählt haben, wählen Sie in **Gruppen auswählen** die Option **Auswählen** aus.
14. Wählen Sie im Bereich **Gruppe hinzufügen** die Option **OK** aus.
15. Wählen Sie im Bereich **Zuweisungen** die Option **Speichern** aus.

Die App wird jetzt den von Ihnen ausgewählten Gruppen zugewiesen. Weitere Informationen zum Ein- und Ausschließen von App-Zuweisungen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen](apps-inc-exl-assignments.md).

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Auflösung von Konflikten zwischen App-Absichten

Eine einzelne Gruppe kann nicht als Ziel für mehrere App-Zuweisungsabsichten verwendet werden. Gehört ein Benutzer oder ein Gerät jedoch mehreren Gruppen mit jeweils unterschiedlichen Absichten an, führt dies zu einem Konflikt. Zuweisungskonflikte bei Anwendungen sollten jedoch vermieden werden.
Verwenden Sie die folgende Tabelle, um die resultierende Absicht bei einem entstehenden Konflikt besser zu verstehen:

| Absicht Gruppe 1 | Absicht Gruppe 2 | Resultierende Absicht |
|-----------------------------------|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
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
> iOS Store-Apps (keine iOS-VPP-Apps), die mit der Absicht „Erforderlich“ als Ziel verwendet werden, werden auf dem Gerät beim Check-In erzwungen und in der Unternehmensportal-App angezeigt.<br><br>
> Treten bei der Einstellung **Deinstallieren beim Entfernen des Geräts** Konflikte auf, wird die App von einem nicht mehr verwalteten Gerät nicht entfernt.

## <a name="managed-google-play-app-deployment-to-unmanaged-devices"></a>Verwaltete Google Play-App-Bereitstellung für nicht verwaltete Geräte
Für Android-Geräte in einem Bereitstellungsszenario mit einer nicht registrierten App-Schutzrichtlinie ohne Registrierung (App Protection Policy Without Enrollment, APP-WE) können Sie verwaltetes Google Play zum Bereitstellen von Store-Apps und branchenspezifischen Apps (LOB-Anwendungen) für Benutzer verwenden. Verwaltete Google Play-Apps mit dem Ziel **Verfügbar mit oder ohne Registrierung** werden in der Play Store-App auf dem Gerät des Benutzers und nicht in der Unternehmensportal-App angezeigt. Der Endbenutzer durchsucht und installiert wird die auf diese Weise bereitgestellten Apps aus der Play-App. Da die Apps über verwaltetes Google Play installiert werden, muss der Endbenutzer seine Geräteeinstellungen nicht ändern, um die App-Installation aus unbekannten Quellen zu ermöglichen, was bedeutet, dass die Geräte sicherer sind. Wenn der App-Entwickler eine neue Version einer App in Play veröffentlicht, die auf dem Gerät eines Benutzers installiert wurde, wird die App automatisch von Play aktualisiert. 

Schritte zum Zuweisen einer verwalteten Google Play-App zu nicht verwalteten Geräten:

1. Verbinden Sie Ihren Intune-Mandanten mit verwaltetem Google Play. Wenn dies bereits geschehen ist, um das Android Enterprise-Arbeitsprofil, dedizierte oder vollständig verwaltete Geräte zu verwalten, müssen Sie diesen Vorgang nicht erneut ausführen.
2. Fügen Sie Apps aus verwaltetem Google Play Ihrer Intune-Konsole hinzu.
3. Stellen Sie verwaltete Google Play-Apps als Ziel **Verfügbar mit oder ohne Registrierung** für die gewünschte Benutzergruppe bereit. Die App-Ziele **Erforderlich** und **Deinstallieren** werden für nicht registrierte Geräte nicht unterstützt.
4. Weisen Sie der Benutzergruppe eine App-Schutzrichtlinie zu.
5. Das nächste Mal, wenn der Endbenutzer die Unternehmensportal-App öffnet, erhält er eine Meldung, die besagt, dass Apps in der Play Store-App verfügbar sind.  Der Benutzer kann auf diese Benachrichtigung tippen, um direkt zur Play-App zu gelangen, um Unternehmens-Apps anzuzeigen, oder er kann separat zur Play Store-App navigieren.
6. Der Endnutzer kann das Kontextmenü innerhalb der Play Store-App erweitern und zwischen seinem persönlichen Google-Konto (in dem seine persönlichen Apps angezeigt werden) und seinem Geschäftskonto (in dem die auf ihn zugeschnittenen Store- und LOB-Apps angezeigt werden) wechseln. Endbenutzer installieren die Apps durch Tippen auf „Installieren“ in der Play Store-App.

Wenn ein selektiver APP-Löschbefehl in der Intune-Konsole ausgegeben wird, wird das Geschäftskonto automatisch aus der Play Store-App entfernt, und der Endbenutzer sieht ab diesem Zeitpunkt keine Geschäfts-Apps mehr im Play Store-App-Katalog. Wenn das Geschäftskonto von einem Gerät entfernt wird, bleiben aus dem Play Store installierte Apps auf dem Gerät installiert und werden nicht deinstalliert. 

## <a name="app-uninstall-setting-for-ios-managed-apps"></a>Einstellung zum Deinstallieren von Apps für verwaltete iOS-Apps
Bei iOS-Geräten können Sie auswählen, was mit verwalteten Apps geschehen soll, wenn die Registrierung des Geräts bei Intune aufgehoben oder das Verwaltungsprofil mithilfe der Einstellung **Deinstallieren beim Entfernen des Geräts** entfernt wird. Diese Einstellung gilt nur für Apps auf einem registrierten Gerät und erst nach deren Installation als verwaltete Apps. Die Einstellung kann nicht für Web-Apps oder Weblinks konfiguriert werden. 

Folgende Standardwerte werden bei neuen Zuweisungen vorab für die Einstellung aufgefüllt:

|Typ der iOS-App | Standardeinstellung für „Deinstallieren beim Entfernen des Geräts“ |
|--------------------|----------------|
| Branchenspezifische App | Ja |
| Store-App | Nein |
| VPP-App | Nein |
| Integrierte App | Nein |

>[!NOTE]
>**Zuweisungen vom Typ „Verfügbar“:** Wenn Sie diese Einstellung für die Gruppen „Für registrierte Geräte verfügbar“ oder „Verfügbar mit oder ohne Registrierung“ aktualisieren, erhalten Benutzer, die bereits über die verwaltete App verfügen, erst dann die aktualisierte Einstellung, wenn sie das Gerät mit Intune synchronisieren und die App neu installieren. 
>
>**Bereits vorhandene Zuweisungen:** Zuweisungen, die bereits vor der Einführung dieser Einstellung vorhanden waren, bleiben unverändert, und es werden alle verwalteten Apps beim Entfernen des Geräts aus der Verwaltung entfernt.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Überwachen von App-Zuweisungen finden Sie unter [Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune](apps-monitor.md).
