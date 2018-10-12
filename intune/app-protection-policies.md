---
title: Erstellen und Bereitstellen von App-Schutzrichtlinien
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Microsoft Intune-App-Schutzrichtlinien erstellen und zuweisen.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 09/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 45c394f3aadde63299b8397974f4547c4968c192
ms.sourcegitcommit: 534efa7c5033098233b2549c2d7fc6cf33330e79
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169031"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Erstellen und Zuweisen von App-Schutzrichtlinien

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Erfahren Sie, wie Sie Microsoft Intune-App-Schutzrichtlinien erstellen und Ihren Benutzern zuweisen. In diesem Thema wird beschrieben, wie Änderungen an bestehenden Richtlinien vorgenommen werden.

## <a name="before-you-begin"></a>Vorbereitung

App-Schutzrichtlinien können angewendet werden, unabhängig davon, ob die Geräte, auf denen die Apps ausgeführt werden, von Intune verwaltet werden. Eine ausführlichere Beschreibung der Funktionsweise von App-Schutzrichtlinien und der von Intune-App-Schutzrichtlinien unterstützten Szenarios finden Sie unter [Was sind Microsoft Intune-App-Schutzrichtlinien?](app-protection-policy.md).

Wenn Sie nach einer Liste der unterstützten MAM-Apps suchen, finden Sie weitere Informationen in der [Liste der MAM-Apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Informationen zum Hinzufügen von Line-of-Business-Apps (LOB) Ihrer Organisation zu Microsoft Intune in Vorbereitung auf App-Schutzrichtlinien finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).

##  <a name="create-an-app-protection-policy"></a>Erstellen einer App-Schutzrichtlinie
1. Wählen Sie in der Workload **Client-Apps** im Bereich **Verwalten** **App-Schutzrichtlinien** aus. Mit dieser Auswahl werden die Details zu **App-Schutzrichtlinien** geöffnet und Sie können neue Richtlinien erstellen und vorhandene bearbeiten.
2. Wählen Sie **Richtlinie hinzufügen** aus.

   ![Screenshot des Blatts „Richtlinie hinzufügen“](./media/app-protection-add-policy.png)

3. Geben Sie einen Namen für die Richtlinie sowie eine kurze Beschreibung ein, und wählen Sie den Plattformtyp für Ihre Richtlinie aus. Bei Bedarf können Sie für jede Plattform mehr als eine Richtlinie erstellen.

4. Wählen Sie **Apps** aus, um das Blatt **Apps** zu öffnen, auf dem eine Liste der verfügbaren Apps angezeigt wird. Wählen Sie eine oder mehrere Apps in der Liste aus, mit denen Sie die von Ihnen zu erstellende Richtlinie verknüpfen möchten.
5. Nachdem Sie die Apps ausgewählt haben, wählen Sie **Auswählen** aus, um Ihre Auswahl zu speichern.

    > [!IMPORTANT]
    > Sie müssen mindestens eine App auswählen, um eine Richtlinie erstellen zu können.

6. Wählen Sie auf dem Blatt **Richtlinie hinzufügen** die Option **Erforderliche Einstellungen konfigurieren** aus, um **Einstellungen** zu öffnen.

   Es gibt zwei Kategorien von Richtlinieneinstellungen: **Datenverlagerung** und **Zugriff**.  Datenverschiebungsrichtlinien können auf Datenverschiebungen in und aus Apps angewendet werden. Mit den Zugriffsrichtlinien wird festgelegt, wie der Endbenutzer in einem Arbeitskontext auf die Apps zugreift.
   Um Ihnen bei den ersten Schritten zu helfen, enthalten die Richtlinieneinstellung Standardwerte. Sie müssen keine Änderungen vornehmen, wenn die Standardwerte Ihren Anforderungen entsprechen.

   > [!TIP]
   > Diese Richtlinieneinstellungen werden nur durchgesetzt, wenn Apps im beruflichen Kontext verwendet werden. Wenn der Endbenutzer die App zum Erledigen einer privaten Aufgabe verwendet, ist er von diesen Richtlinien nicht betroffen. Beachten Sie, dass Dateien, die Sie neu erstellen, als persönliche Dateien angesehen werden. 

7. Wählen Sie **OK** aus, um diese Konfiguration zu speichern. Damit befinden Sie sich wieder im Bereich **Richtlinie hinzufügen**.
8. Wählen Sie **Erstellen** aus, um die Richtlinie zu erstellen und Ihre Einstellungen zu speichern.

Wenn Sie mit dem Erstellen einer Richtlinie wie im vorherigen Verfahren beschrieben fertig sind, wird sie noch nicht für Benutzer bereitgestellt. Informationen zum Bereitstellen einer Richtlinie finden Sie unter [Bereitstellen einer Richtlinie für Benutzer](app-protection-policies.md#deploy-a-policy-to-users).

## <a name="deploy-a-policy-to-users"></a>Bereitstellen einer Richtlinie für Benutzer

1. Wählen Sie im Bereich **App-Schutzrichtlinien** eine Richtlinie aus.

2. Wählen Sie im Bereich **Richtlinie** die Option **Zuweisungen** aus. Dadurch wird der Bereich **Intune-App-Schutz - Zuweisungen** geöffnet. Wählen Sie im Bereich **Zuweisungen** die Option **Select groups to include** (Einzuschließende Gruppen auswählen) aus, um den Bereich **Select groups to include** zu öffnen.

   ![Screenshot des Bereichs „Zuweisungen“ mit Hervorhebung der Menüoption „Select groups to include“ (Einzuschließende Gruppen auswählen)](./media/app-protection-policy-add-users.png)

3.  Im Bereich **Benutzergruppe hinzufügen** wird eine Liste der Benutzergruppen angezeigt. In dieser Liste werden alle Sicherheitsgruppen in Ihrem **Azure Active Directory** angezeigt. Wählen Sie die Benutzergruppen aus, auf die diese Richtlinie angewendet werden soll, und anschließend **Auswählen**. Die Auswahl von **Auswählen** bewirkt die Bereitstellung der Richtlinie für Benutzer.

    ![Screenshot des Bereichs „Benutzergruppe hinzufügen“ mit der Liste der Azure Active Directory-Benutzer](./media/azure-ad-user-group-list.png)

Damit haben Sie eine Richtlinie erstellt und für die Benutzer bereitgestellt.

Von der Richtlinie sind nur Benutzer mit zugewiesenen Microsoft Intune-Lizenzen betroffen. Benutzer in der ausgewählten Sicherheitsgruppe, denen keine Intune-Lizenz zugewiesen wurde, sind nicht betroffen.

>[!IMPORTANT]
> Wenn Sie Intune mit Configuration Manager verwenden, um Ihre Geräte zu verwalten, wird die Richtlinie nur auf Benutzer in der Gruppe angewendet, die Sie ausgewählt haben. Mitglieder untergeordneter Gruppen, die in der ausgewählten Gruppe geschachtelt sind, sind nicht betroffen.

Endbenutzer können die Apps aus dem App Store oder aus Google Play herunterladen. Weitere Informationen finden Sie in folgenden Quellen:
* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](app-protection-enabled-apps-android.md)
* [Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](app-protection-enabled-apps-ios.md)

##  <a name="change-existing-policies"></a>Ändern vorhandener Richtlinien
Sie können eine vorhandene Richtlinie bearbeiten und sie auf die als Ziel festgelegten Benutzer anwenden. Wenn Sie vorhandene Richtlinien ändern, werden diese Änderungen für Benutzer, die bereits bei der App angemeldet sind, jedoch in den nächsten acht Stunden nicht wirksam.

Um die Auswirkungen der Änderungen sofort zu erfahren, muss der Endbenutzer sich bei der App abmelden und sich dann erneut anmelden.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>So ändern Sie die Liste der Apps, die einer Richtlinie zugeordnet sind

1.  Wählen Sie im Bereich **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten, um einen für die eben ausgewählte Richtlinie spezifischen Bereich zu öffnen.

2.  Wählen Sie im Richtlinienbereich **Ziel-Apps** aus, um eine Liste der Apps zu öffnen.

3.  Fügen Sie der Liste Apps hinzu, oder entfernen Sie Apps hieraus, und wählen Sie dann das Symbol **Speichern** aus, um die Änderungen zu speichern.

### <a name="to-change-the-list-of-user-groups"></a>So ändern Sie die Liste der Benutzergruppen


1.  Wählen Sie im Bereich **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten, um den für die ausgewählte Richtlinie spezifischen Bereich zu öffnen.

2.  Wählen Sie im Richtlinienbereich **Zuweisungen** aus, um den Bereich **Intune-App-Schutz – Zuweisungen** zu öffnen. Hier wird eine Liste mit aktuellen Benutzergruppen angezeigt, denen diese Richtlinie zugewiesen wurde.

3.  Um eine neue Benutzergruppe hinzuzufügen, wählen Sie auf der Registerkarte **Einschließen** die Option **Select groups to include** (Einzuschließende Gruppen auswählen) und anschließend die Benutzergruppe aus. Wählen Sie **Auswählen** aus, um die Richtlinie für die ausgewählte Gruppe bereitzustellen.

4.  Um eine Benutzergruppe zu löschen, wählen Sie auf der Registerkarte **Ausschließen** die Option **Select groups to exclude** (Auszuschließende Gruppen auswählen) und anschließend die Benutzergruppe aus. Wählen Sie **Auswählen** aus, um die Benutzergruppe zu entfernen.

### <a name="to-change-policy-settings"></a>So ändern Sie Richtlinieneinstellungen

1.  Wählen Sie im Bereich **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten, um einen für die eben ausgewählte Richtlinie spezifischen Bereich zu öffnen.

2.  Wählen Sie **Richtlinieneinstellungen** aus, um den Bereich **Richtlinieneinstellungen** zu öffnen.

3.  Ändern Sie die Einstellungen, und wählen Sie das Symbol **Speichern** aus, um die Änderungen zu speichern.

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Verwendung von App-Schutzrichtlinien als Ziel, basierend auf dem Status der Geräteverwaltung
Viele Organisationen erlauben Benutzern sowohl die Verwendung von mit Intune-MDM verwalteten Geräten, z.B. unternehmenseigene Geräte, als auch die Verwendung von nicht verwalteten Geräten, die nur mit Intune App-Schutzrichtlinien geschützt werden, wie BYO-Geräten.

Da die App-Schutzrichtlinien von Intune die Identität eines Benutzers ansteuern, gelten die Schutzeinstellungen üblicherweise jeweils für registrierte (MDM-verwaltete) und nicht registrierte Geräte (kein MDM). Aus diesem Grund können Sie mit einer App-Schutzrichtlinie von Intune entweder Intune-registrierte oder nicht registrierte iOS- und Android-Geräte als Ziel verwenden. Sie können über eine Schutzrichtlinie für nicht verwaltete Geräte verfügen, bei dem Steuerelemente für die Verhinderung von Datenverlust (DLP) vorhanden sind, und eine separate Schutzrichtlinie für mit MDM verwaltete Geräte, bei denen die DLP-Steuerelemente nicht so streng sind. 

Navigieren Sie in der Intune-Konsole zu **Client-Apps** > **App-Schutzrichtlinien**, und klicken Sie auf **Richtlinie hinzufügen**, um diese Richtlinien zu erstellen. Sie können auch eine vorhandene App-Schutzrichtlinie bearbeiten. Wenn die App-Schutzrichtlinie für verwaltete und nicht verwaltete Geräte angewendet werden soll, bestätigen Sie, dass **Target to all app types** (Alle App-Typen als Ziel verwenden) auf den Standardwert **Ja** festgelegt ist. Wenn Sie eine Basis granular einem Verwaltungsstatus zuweisen wollen, legen Sie die Option **Target to all app types** (Alle App-Typen als Ziel verwenden) auf **Nein** fest. 

![Screenshot vom Blatt „Richtlinie hinzufügen“ mit ausgewählter Option „Auf alle App-Typen ausrichten“](./media/app-protection-policies-target-all.png)

Damit iOS-Apps als „verwaltet“ erkannt werden, muss die Konfigurationsrichtlinieneinstellung **IntuneMAMUPN** für jede App bereitgestellt werden. Weitere Informationen finden Sie unter [Verwalten der Datenübertragung zwischen iOS-Apps in Microsoft Intune](https://docs.microsoft.com/intune/data-transfer-between-apps-manage-ios#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).

> [!NOTE]
> Spezifische iOS-Supportinfomationen über App-Schutzrichtlinien basierend auf dem Status der Geräteverwaltung finden Sie unter [MAM protection policies targeted based on management state (Angesteuerte MAM-Schutzrichtlinien basierend auf dem Verwaltungsstatus)](whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-).

## <a name="policy-settings"></a>Richtlinieneinstellungen
Eine vollständige Liste der Richtlinieneinstellungen für iOS und Android finden Sie unter den folgenden Links:

- [iOS-Richtlinien](app-protection-policy-settings-ios.md)
- [Android-Richtlinien](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Nächste Schritte
[Überwachen der Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](app-protection-policies-monitor.md)

### <a name="see-also"></a>Siehe auch
* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](app-protection-enabled-apps-android.md)
* [Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](app-protection-enabled-apps-ios.md)
