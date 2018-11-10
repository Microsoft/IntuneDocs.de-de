---
title: Erstellen und Bereitstellen von App-Schutzrichtlinien
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Microsoft Intune-App-Schutzrichtlinien erstellen und zuweisen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3a7285edfa2dcb50cc5fd28e4fefc1be4c3b9e10
ms.sourcegitcommit: cac71802b2782700f0d52ea114089d73620cd1ed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50679269"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Erstellen und Zuweisen von App-Schutzrichtlinien

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Erfahren Sie, wie Sie Microsoft Intune-App-Schutzrichtlinien erstellen und Ihren Benutzern zuweisen. In diesem Thema wird beschrieben, wie Änderungen an bestehenden Richtlinien vorgenommen werden.

## <a name="before-you-begin"></a>Vorbereitung

App-Schutzrichtlinien können unabhängig davon auf Apps angewendet werden, ob die Geräte, auf denen die Apps ausgeführt werden, von Intune verwaltet werden. Eine ausführlichere Beschreibung der Funktionsweise von App-Schutzrichtlinien und der von Intune-App-Schutzrichtlinien unterstützten Szenarien finden Sie unter [Was sind Microsoft Intune-App-Schutzrichtlinien?](app-protection-policy.md).

Wenn Sie nach einer Liste der unterstützten MAM-Apps suchen, finden Sie weitere Informationen in der [Liste der MAM-Apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Informationen zum Hinzufügen von Line-of-Business-Apps (LOB) Ihrer Organisation zu Microsoft Intune in Vorbereitung auf App-Schutzrichtlinien finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).

##  <a name="create-an-app-protection-policy"></a>Erstellen einer App-Schutzrichtlinie
1. Klicken Sie im Intune-Portal auf **Client-Apps** > **App-Schutzrichtlinien**. Mit dieser Auswahl werden die Details zu **App-Schutzrichtlinien** geöffnet und Sie können neue Richtlinien erstellen und vorhandene bearbeiten.
2. Klicken Sie auf **Richtlinie erstellen**.

   ![Screenshot des Blatts „Richtlinie hinzufügen“](./media/app-protection-add-policy.png)

3. Geben Sie einen Namen für die Richtlinie sowie eine kurze Beschreibung an, und wählen Sie den Plattformtyp für Ihre Richtlinie aus. Sie können für jede Plattform mehr als eine Richtlinie erstellen.

4. Wählen Sie **Apps** aus, um das Blatt **Apps** zu öffnen, das eine Liste der verfügbaren Apps anzeigt. Wählen Sie eine oder mehrere Apps in der Liste aus, mit denen Sie die von Ihnen zu erstellende Richtlinie verknüpfen möchten. Wählen Sie mindestens eine App aus, um eine Richtlinie zu erstellen.  

5. Nachdem Sie die Apps ausgewählt haben, wählen Sie **Auswählen** aus, um Ihre Auswahl zu speichern.

6. Wählen Sie auf dem Blatt **Richtlinie hinzufügen** die Option **Erforderliche Einstellungen konfigurieren** aus, um **Einstellungen** zu öffnen.

   Es gibt drei Kategorien von Richtlinieneinstellungen:
   - **Datenverschiebung**: Diese Gruppe umfasst Steuerelemente zum Verhindern von Datenverlust, wie z.B. Einschränkungen für Ausschneiden, Kopieren, Einfügen und „Speichern unter“. Diese Einstellungen bestimmen, wie Benutzer mit Daten in den Apps interagieren kann.
   - **Zugriffsanforderungen**: Diese Gruppe enthält die PIN-Optionen pro App. Sie bestimmen, wie der Endbenutzer in einem Arbeitskontext auf die Apps zugreifen kann.  
   - **Bedingter Start**: Diese Gruppe enthält Einstellungen wie z.B. die mindestens erforderliche Betriebssystemversion, Einstellungen zur Erkennung von Jailbreak und entfernten Nutzungsbeschränkungen und die Offline-Toleranzperiode.

   Um Ihnen bei den ersten Schritten zu helfen, enthalten die Richtlinieneinstellung Standardwerte. Sie müssen keine Änderungen vornehmen, wenn die Standardwerte Ihren Anforderungen entsprechen.

   > [!TIP]
   > Diese Richtlinieneinstellungen werden nur durchgesetzt, wenn Apps im beruflichen Kontext verwendet werden. Wenn der Endbenutzer die App zum Erledigen einer privaten Aufgabe verwendet, ist er von diesen Richtlinien nicht betroffen. Beachten Sie, dass Dateien, die Sie neu erstellen, als persönliche Dateien angesehen werden. 

7. Wählen Sie **OK** aus, um diese Konfiguration zu speichern. Damit befinden Sie sich wieder im Bereich **Richtlinie hinzufügen**.
8. Wählen Sie **Erstellen** aus, um die Richtlinie zu erstellen und Ihre Einstellungen zu speichern.

Neu erstellte Richtlinien werden erst auf die Benutzer angewendet, wenn Sie sie explizit bereitstellen. Informationen zum Bereitstellen einer Richtlinie finden Sie unter [Bereitstellen einer Richtlinie für Benutzer](app-protection-policies.md#deploy-a-policy-to-users).

## <a name="deploy-a-policy-to-users"></a>Bereitstellen einer Richtlinie für Benutzer

1. Wählen Sie im Bereich **App-Schutzrichtlinien** eine Richtlinie aus.

2. Wählen Sie im Bereich ***Intune-App-Schutz** die Option **Zuweisungen** aus, um den Bereich **Intune-App-Schutz – Zuweisungen** zu öffnen. Klicken Sie auf der Registerkarte *Einschließen* auf **Einzuschließende Gruppen auswählen**. 

   ![Screenshot des Bereichs „Zuweisungen“ mit Hervorhebung der Menüoption „Einzuschließende Gruppen auswählen“](./media/app-protection-policy-add-users.png)

3.  Es wird eine Liste aller Sicherheitsgruppen in Ihrem **Azure Active Directory**-Verzeichnis angezeigt. Wählen Sie die Benutzergruppen aus, auf die diese Richtlinie angewendet werden soll, und klicken Sie dann auf **Auswählen**. Die Auswahl von **Auswählen** bewirkt die Bereitstellung der Richtlinie für Benutzer.

    ![Screenshot des Bereichs „Benutzergruppe hinzufügen“ mit der Liste der Azure Active Directory-Benutzer](./media/azure-ad-user-group-list.png)

Damit haben Sie eine Richtlinie erstellt und für die Benutzer bereitgestellt.

Von der Richtlinie sind nur Benutzer mit zugewiesenen Microsoft Intune-Lizenzen betroffen. Benutzer in der ausgewählten Sicherheitsgruppe, denen keine Intune-Lizenz zugewiesen wurde, sind nicht betroffen.

>[!IMPORTANT]
> Wenn Sie Intune mit Configuration Manager verwenden, um Ihre Geräte zu verwalten, wird die Richtlinie nur auf Benutzer in der Gruppe angewendet, die Sie ausgewählt haben. Mitglieder untergeordneter Gruppen, die in der ausgewählten Gruppe geschachtelt sind, sind nicht betroffen.

Endbenutzer können die Apps aus dem App Store oder aus Google Play herunterladen. Weitere Informationen finden Sie in folgenden Quellen:
* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](app-protection-enabled-apps-android.md)
* [Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](app-protection-enabled-apps-ios.md)

##  <a name="change-existing-policies"></a>Ändern vorhandener Richtlinien
Sie können eine vorhandene Richtlinie bearbeiten und sie auf die als Ziel festgelegten Benutzer anwenden. Wenn Sie vorhandene Richtlinien ändern, werden diese Änderungen für bei der App angemeldete Benutzer erst nach 8 Stunden sichtbar.

Für eine sofortige Anzeige der Änderungen muss der Endbenutzer sich von der App abmelden und dann erneut anmelden.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>So ändern Sie die Liste der Apps, die einer Richtlinie zugeordnet sind

1.  Wählen Sie auf dem Blatt **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten.

2.  Wählen Sie im Bereich *Intune-App-Schutz* die Option **Ziel-Apps** aus, um die Liste der Apps anzuzeigen.

3.  Fügen Sie der Liste Apps hinzu, oder entfernen Sie Apps aus der Liste, und klicken Sie dann auf das Symbol **Speichern**, um die Änderungen zu speichern.

### <a name="to-change-the-list-of-user-groups"></a>So ändern Sie die Liste der Benutzergruppen


1.  Wählen Sie im Bereich **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten.

2.  Wählen Sie im Bereich *Intune-App-Schutz* die Option **Zuweisungen** aus, um den Bereich **Intune-App-Schutz – Zuweisungen** zu öffnen. Hier wird die Liste mit aktuellen Benutzergruppen angezeigt, denen diese Richtlinie zugewiesen ist.

3.  Um eine neue Benutzergruppe hinzuzufügen, wählen Sie auf der Registerkarte **Einschließen** die Option **Einzuschließende Gruppen auswählen** und anschließend die Benutzergruppe aus. Wählen Sie **Auswählen** aus, um die Richtlinie für die ausgewählte Gruppe bereitzustellen.

4.  Um eine Benutzergruppe zu löschen, wählen Sie auf der Registerkarte **Ausschließen** die Option **Auszuschließende Gruppen auswählen** und anschließend die Benutzergruppe aus. Wählen Sie **Auswählen** aus, um die Benutzergruppe zu entfernen.

### <a name="to-change-policy-settings"></a>So ändern Sie Richtlinieneinstellungen

1.  Wählen Sie im Bereich **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten.

2.  Klicken Sie im Bereich *Intune-App-Schutz* auf **Eigenschaften**, um die Liste der Einstellungsbereiche zu öffnen, die Sie bearbeiten können. 

3.  Wählen Sie den Einstellungsbereich aus, für den Sie Einstellungen ändern möchten, z.B. **Datenverschiebung** oder **Zugriffsanforderungen**. Legen Sie für die gewünschten Einstellungen neue Werte fest.

4.  Klicken Sie auf das Symbol **Speichern**, um Ihre Änderungen zu speichern. Wiederholen Sie ggf. den Vorgang, um einen anderen Einstellungsbereich zu öffnen und die gewünschten Änderungen durchzuführen und zu speichern. Anschließend können Sie den Bereich *Intune-App-Schutz – Zuweisungen* schließen. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Verwendung von App-Schutzrichtlinien als Ziel, basierend auf dem Status der Geräteverwaltung
Viele Organisationen erlauben Benutzern sowohl die Verwendung von mit Intune-MDM verwalteten Geräten (z.B. unternehmenseigene Geräte) als auch die Verwendung von nicht verwalteten Geräten, die nur mit Intune App-Schutzrichtlinien geschützt werden. Nicht verwaltete Geräte werden häufig als BYOD-Geräte (Bring Your Own Device) bezeichnet.

Da die App-Schutzrichtlinien von Intune an die Identität eines Benutzers gekoppelt sind, können die Schutzeinstellungen sowohl auf registrierte (MDM-verwaltete) als auch auf nicht registrierte Geräte (kein MDM) angewendet werden. Aus diesem Grund können Sie mit einer App-Schutzrichtlinie von Intune entweder Intune-registrierte oder nicht registrierte iOS- und Android-Geräte als Ziel verwenden. Sie können über eine Schutzrichtlinie für nicht verwaltete Geräte verfügen, bei dem Steuerelemente für die Verhinderung von Datenverlust (DLP) vorhanden sind, und eine separate Schutzrichtlinie für mit MDM verwaltete Geräte, bei denen die DLP-Steuerelemente nicht so streng sind. 

Um diese Richtlinien zu erstellen, navigieren Sie in der Intune-Konsole zu **Client-Apps** > **App-Schutzrichtlinien**, und klicken Sie dann auf **Richtlinie hinzufügen**. Sie können auch eine vorhandene App-Schutzrichtlinie bearbeiten. Wenn die App-Schutzrichtlinie sowohl auf verwaltete als auch auf nicht verwaltete Geräte angewendet werden soll, bestätigen Sie, dass **Auf alle App-Typen ausrichten** auf den Standardwert **Ja** festgelegt ist. Wenn Sie eine feiner abgestufte Zuweisung basierend auf dem Verwaltungszustand durchführen möchten, legen Sie die Option **Auf alle App-Typen ausrichten** auf **Nein** fest. 

![Screenshot vom Blatt „Richtlinie hinzufügen“ mit ausgewählter Option „Auf alle App-Typen ausrichten“](./media/app-protection-policies-target-all.png)

Für iOS sind zusätzliche App-Konfigurationseinstellungen erforderlich, um APP-Einstellungen für Apps auf bei Intune registrierten Geräten bereitzustellen:
- **IntuneMAMUPN** muss für alle mit MDM verwalteten Anwendungen konfiguriert sein. Weitere Informationen finden Sie unter [Verwalten der Datenübertragung zwischen iOS-Apps in Microsoft Intune](https://docs.microsoft.com/intune/data-transfer-between-apps-manage-ios#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- **IntuneMAMDeviceID** muss für alle mit MDM verwalteten Drittanbieter- und Branchenanwendungen konfiguriert sein. **IntuneMAMDeviceID** sollte auf das Geräte-ID-Token konfiguriert sein. Beispiel: `key=IntuneMAMDeviceID, value={{deviceID}}`. Weitere Informationen finden Sie unter [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete iOS-Geräte](https://docs.microsoft.com/intune/app-configuration-policies-use-ios).
- Wenn nur **IntuneMAMDeviceID** konfiguriert ist, betrachtet die Intune-APP das Gerät als nicht verwaltet.  

> [!NOTE]
> Spezifische iOS-Supportinfomationen über App-Schutzrichtlinien basierend auf dem Status der Geräteverwaltung finden Sie unter [Anwenden von MAM-Richtlinien je nach Verwaltungsstatus](whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-).

## <a name="policy-settings"></a>Richtlinieneinstellungen
Eine vollständige Liste der Richtlinieneinstellungen für iOS und Android finden Sie unter den folgenden Links:

- [iOS-Richtlinien](app-protection-policy-settings-ios.md)
- [Android-Richtlinien](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Nächste Schritte
[Überwachen der Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](app-protection-policies-monitor.md)

### <a name="see-also"></a>Siehe auch
* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](app-protection-enabled-apps-android.md)
* [Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](app-protection-enabled-apps-ios.md)
