---
title: Erstellen und Bereitstellen von App-Schutzrichtlinien
titleSuffix: Microsoft Intune
description: In diesem Thema wird beschrieben, wie Sie Microsoft Intune-App-Schutzrichtlinien (APP) erstellen und zuweisen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a8e105dae43c4e7139c8e44a8c6535baebe31cc4
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585466"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Erstellen und Zuweisen von App-Schutzrichtlinien

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Informieren Sie sich, wie Sie Microsoft Intune-App-Schutzrichtlinien (APP) für Benutzer Ihrer Organisation erstellen und diesen zuweisen. In diesem Thema wird beschrieben, wie Änderungen an bestehenden Richtlinien vorgenommen werden.

## <a name="before-you-begin"></a>Vorbereitung

App-Schutzrichtlinien können unabhängig davon auf Apps angewendet werden, ob die Geräte, auf denen die Apps ausgeführt werden, von Intune verwaltet werden. Eine ausführlichere Beschreibung der Funktionsweise von App-Schutzrichtlinien und der von Intune-App-Schutzrichtlinien unterstützten Szenarien finden Sie unter [Was sind Microsoft Intune-App-Schutzrichtlinien?](app-protection-policy.md).

Wenn Sie nach einer Liste der unterstützten MAM-Apps suchen, finden Sie weitere Informationen in der [Liste der MAM-Apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Informationen zum Hinzufügen von Line-of-Business-Apps (LOB) Ihrer Organisation zu Microsoft Intune in Vorbereitung auf App-Schutzrichtlinien finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).

Derzeit unterscheidet sich der Prozessablauf zum Erstellen einer App-Schutzrichtlinie je nach Plattform:
- App-Schutzrichtlinien für iOS-/iPadOS- und Android-Apps
- App-Schutzrichtlinien für Windows 10-Apps

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>App-Schutzrichtlinien für iOS-/iPadOS- und Android-Apps

Befolgen Sie beim Erstellen neuer App-Schutzrichtlinien für iOS-/iPadOS- und Android-Apps einen modernen Intune-Prozessablauf für App-Schutzrichtlinien.

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>Erstellen einer iOS-/iPadOS- oder Android-App-Schutzrichtlinie
1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie im Intune-Portal auf **Client-Apps** > **App protection policies** (App-Schutzrichtlinien). Mit dieser Auswahl werden die Details zu **App-Schutzrichtlinien** geöffnet und Sie können neue Richtlinien erstellen und vorhandene bearbeiten.
3. Klicken Sie auf **Richtlinie erstellen**, und wählen Sie entweder **iOS/iPadOS** oder **Android** aus. Das Blatt **Richtlinie erstellen** wird angezeigt.
4. Fügen Sie auf der Seite **Basics** (Grundeinstellungen) die folgenden Werte hinzu:

    | Wert | Beschreibung |
    |--------------|------------------------------------------------|
    | Name | Name der App-Schutzrichtlinie |
    | Beschreibung | [Optional] Beschreibung der App-Schutzrichtlinie |


    Der Wert **Plattform** wird basierend auf der oben von Ihnen ausgewählten Option festgelegt.

    ![Screenshot der Seite „Basiscs“ (Grundeinstellungen) auf dem Blatt „Richtlinie erstellen“](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. Klicken Sie auf **Weiter**, um die Seite **Apps** anzuzeigen.<br>
    Auf der Seite **Apps** können Sie auswählen, wie Sie diese Richtlinie auf Apps auf verschiedenen Geräten anwenden möchten. Sie müssen mindestens eine App hinzufügen.<p>
    
    | Wert/Option | Beschreibung |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Auf Apps auf allen Gerätetypen anwenden | Verwenden Sie diese Option, um die Richtlinie auf Apps auf Geräten mit beliebigem Verwaltungsstatus anzuwenden. Klicken Sie auf **Nein**, um die Richtlinie auf Apps auf bestimmten Gerätetypen anzuwenden. |
    |     Device types (Gerätetypen) | Verwenden Sie diese Option, um anzugeben, ob diese Richtlinie für mit MDM verwaltete oder nicht verwaltete Geräte gilt. Wählen Sie für iOS-App-Richtlinien **Unmanaged devices** (Nicht verwaltete Geräte) und **Managed devices** (Verwaltete Geräte) aus. Wählen Sie für Android-App-Richtlinien **Unmanaged Devices** (Nicht verwaltete Geräte), **Android device administrator** (Android-Geräteadministrator) und **Android Enterprise** aus.  |
    | Public apps (Öffentliche Apps) | Klicken Sie auf **Select public apps** (Öffentliche Apps auswählen), um die gewünschten Apps als Ziel auszuwählen. |
    | Custom apps (Benutzerdefinierte Apps) | Klicken Sie auf **Select custom apps** (Benutzerdefinierte Apps auswählen), um basierend auf einer Paket-ID benutzerdefinierte Apps als Ziel auszuwählen. |
    
    Die ausgewählten Apps werden in der öffentlichen und benutzerdefinierten App-Liste angezeigt. 
6. Klicken Sie auf **Weiter**, um die Seite **Datenschutz** anzuzeigen.<br>
    Auf dieser Seite finden Sie Einstellungen für Steuerelemente zur Verhinderung von Datenverlust (DLP) einschließlich Einschränkungen für „Ausschneiden“, „Kopieren“, „Einfügen“ und „Speichern unter“. Diese Einstellungen bestimmen, wie Benutzer mit Daten in den Apps interagieren können, für die diese Schutzrichtlinie gilt.

    **Datenschutzeinstellungen:**<br>
    - **Datenschutz bei iOS-/iPadOS-Apps:** Weitere Informationen finden Sie unter [Einstellungen für iOS-App-Schutzrichtlinien – Datenschutz](~/apps/app-protection-policy-settings-ios.md#data-protection).
    - **Datenschutz für Android-Apps:** Weitere Informationen finden Sie unter [Einstellungen für Android-App-Schutzrichtlinien – Datenschutz](~/apps/app-protection-policy-settings-android.md#data-protection).

7. Klicken Sie auf **Weiter**, um die Seite **Zugriffsanforderungen** anzuzeigen.<br>
    Auf dieser Seite finden Sie Einstellungen, mit denen Sie die PIN und die Anforderungen bezüglich der Anmeldeinformationen konfigurieren können, die Benutzer für den Zugriff auf Apps in einem Arbeitskontext erfüllen müssen. 
 
    **Einstellungen für Zugriffsanforderungen:**<br>
    - **Zugriffsanforderungen für iOS-/iPadOS-Apps:** Weitere Informationen finden Sie unter [Einstellungen für iOS-App-Schutzrichtlinien – Zugriffsanforderungen](~/apps/app-protection-policy-settings-ios.md#access-requirements).
    - **Zugriffsanforderungen für Android-Apps:** Weitere Informationen finden Sie unter [Einstellungen für Android-App-Schutzrichtlinien – Zugriffsanforderungen](~/apps/app-protection-policy-settings-android.md#access-requirements).

8. Klicken Sie auf **Weiter**, um die Seite **Conditional launch (Bedingter Start)** anzuzeigen.<br>
    Auf dieser Seite finden Sie Einstellungen zum Festlegen der Sicherheitsanforderungen für Anmeldeinformationen für die App-Schutzrichtlinien. Wählen Sie eine **Einstellung** aus, und geben Sie den **Wert** an, den Benutzer erfüllen müssen, um sich bei Ihrer Unternehmens-App anzumelden. Klicken Sie dann auf die **Aktion**, die Benutzer ausführen sollen, wenn Sie Ihre Anforderungen nicht erfüllen. In einigen Fällen können mehrere Aktionen für eine einzelne Einstellung konfiguriert werden.

    **Einstellungen für den bedingten Start:**<br>
    - **Bedingter Start von iOS-/iPadOS-Apps:** Weitere Informationen finden Sie unter [Einstellungen für Schutzrichtlinien für iOS-Apps](~/apps/app-protection-policy-settings-ios.md#conditional-launch).
    - **Bedingter Start von Android-Apps:** Weitere Informationen finden Sie unter [Einstellungen für Schutzrichtlinien für Android-Apps](~/apps/app-protection-policy-settings-android.md#conditional-launch).

7. Klicken Sie auf **Weiter**, um die Seite **Zuweisungen** anzuzeigen.<br>
   Mit der Seite **Zuweisungen** können Sie die App-Schutzrichtlinie bestimmten Gruppen von Benutzern zuweisen. 
8. Klicken Sie auf **Next: Review and create** (Weiter: Überprüfen und erstellen), um die Werte und Einstellungen zu überprüfen, die Sie für diese App-Schutzrichtlinie eingegeben haben.
9. Klicken Sie abschließend auf **Erstellen**, um die App-Schutzrichtlinie in Intune zu erstellen. 

## <a name="app-protection-policies-for-windows-10-apps"></a>App-Schutzrichtlinien für Windows 10-Apps

Befolgen Sie beim Erstellen einer App-Schutzrichtlinie für Windows 10-Apps einen klassischen Intune-Prozessablauf.

### <a name="create-a-windows-10-app-protection-policy"></a>Erstellen einer Windows 10-App-Schutzrichtlinie
1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie im Intune-Portal auf **Client-Apps** > **App protection policies** (App-Schutzrichtlinien). Mit dieser Auswahl werden die Details zu **App-Schutzrichtlinien** geöffnet und Sie können neue Richtlinien erstellen und vorhandene bearbeiten.
3. Klicken Sie auf **Richtlinie erstellen**.

    <img alt="Screenshot of the 'Create policy' blade for Windows 10" src="~/apps/media/app-protection-policies/app-protection-add-policy.png" width="350">

4. Geben Sie einen Namen für die Richtlinie sowie eine kurze Beschreibung an, und wählen Sie den Plattformtyp für Ihre Richtlinie aus. Sie können für jede Plattform mehr als eine Richtlinie erstellen.

4. Sie können die Option **Target to all app types** (Auf alle App-Typen anwenden) auswählen. Mit dieser Option können Sie die Richtlinie auf Apps auf Geräten mit beliebigem Verwaltungsstatus anwenden. Bei der Auflösung von Richtlinienkonflikten wird diese Einstellung ersetzt, wenn ein Benutzer über eine Richtlinie für einen bestimmten Verwaltungsstatus verfügt. Weitere Informationen finden Sie unter [Erstellen und Zuweisen von App-Schutzrichtlinien](~/apps/app-protection-policies.md#target-app-protection-policies-based-on-device-management-state).

5. Wählen Sie **Apps** aus, um das Blatt **Apps** zu öffnen, das eine Liste der verfügbaren Apps anzeigt. Wählen Sie eine oder mehrere Apps in der Liste aus, mit denen Sie die von Ihnen zu erstellende Richtlinie verknüpfen möchten. Wählen Sie mindestens eine App aus, um eine Richtlinie zu erstellen.  

6. Nachdem Sie die Apps ausgewählt haben, wählen Sie **Auswählen** aus, um Ihre Auswahl zu speichern.

7. Wählen Sie auf dem Blatt **Richtlinie hinzufügen** die Option **Erforderliche Einstellungen konfigurieren** aus, um **Einstellungen** zu öffnen.

   Es gibt drei Kategorien von Richtlinieneinstellungen:
   - **Datenschutz**: Diese Gruppe umfasst Steuerelemente zur Verhinderung von Datenverlust (DLP), wie z. B. Einschränkungen für Ausschneiden, Kopieren, Einfügen und „Speichern unter“. Diese Einstellungen bestimmen, wie Benutzer mit Daten in den Apps interagieren können.
   - **Zugriffsanforderungen**: Diese Gruppe enthält die PIN-Optionen pro App. Sie bestimmen, wie der Endbenutzer in einem Arbeitskontext auf die Apps zugreifen kann.  
   - **Bedingter Start**: Diese Gruppe enthält Einstellungen wie z.B. die mindestens erforderliche Betriebssystemversion, Einstellungen zur Erkennung von Jailbreak und entfernten Nutzungsbeschränkungen und die Offlinetoleranzperiode.

   Um Ihnen bei den ersten Schritten zu helfen, enthalten die Richtlinieneinstellung Standardwerte. Sie müssen keine Änderungen vornehmen, wenn die Standardwerte Ihren Anforderungen entsprechen.

   > [!TIP]
   > Diese Richtlinieneinstellungen werden nur durchgesetzt, wenn Apps im beruflichen Kontext verwendet werden. Wenn der Endbenutzer die App zum Erledigen einer privaten Aufgabe verwendet, ist er von diesen Richtlinien nicht betroffen. Beachten Sie, dass Dateien, die Sie neu erstellen, als persönliche Dateien angesehen werden. 

8. Wählen Sie **OK** aus, um diese Konfiguration zu speichern. Damit befinden Sie sich wieder im Bereich **Richtlinie hinzufügen**.
9. Wählen Sie **Erstellen** aus, um die Richtlinie zu erstellen und Ihre Einstellungen zu speichern.

Neu erstellte Windows 10-Richtlinien werden keinem Benutzer zugewiesen, bis Sie dies explizit tun. Informationen zum Zuweisen von Windows 10-Richtlinien finden Sie unter [Zuweisen einer Windows 10-Richtlinie zu Benutzern](~/apps/app-protection-policies.md#assign-a-windows-10-policy-to-users).

### <a name="assign-a-windows-10-policy-to-users"></a>Zuweisen einer Windows 10-Richtlinie zu Benutzern 

1. Wählen Sie im Bereich **App-Schutzrichtlinien** eine Richtlinie aus.

2. Wählen Sie im Bereich ***Intune-App-Schutz** die Option **Zuweisungen** aus, um den Bereich **Intune-App-Schutz – Zuweisungen** zu öffnen. Klicken Sie auf der Registerkarte *Einschließen* auf **Einzuschließende Gruppen auswählen**. 

   ![Screenshot des Bereichs „Zuweisungen“ mit dem Menü „Select groups to include“ (Einzuschließende Gruppen auswählen)](./media/app-protection-policies/app-protection-policy-add-users.png)

3. Es wird eine Liste aller Sicherheitsgruppen in Ihrem **Azure Active Directory**-Verzeichnis angezeigt. Wählen Sie die Benutzergruppen aus, auf die diese Richtlinie angewendet werden soll, und klicken Sie dann auf **Auswählen**. 

    ![Screenshot des Bereichs „Add user group“ (Benutzergruppe hinzufügen) mit einer Liste der Azure AD-Benutzer](./media/app-protection-policies/azure-ad-user-group-list.png)

4. Wählen Sie nach dem Einschließen und Ausschließen von Gruppen **Speichern** zum Speichern der Konfiguration und Bereitstellen der Richtlinie für Benutzer aus. Wenn Sie **Verwerfen** auswählen, bevor Sie Ihre Konfiguration speichern, verwerfen Sie alle Änderungen, die Sie auf den Registerkarten *Einschließen* und *Ausschließen* vorgenommen haben.   
 
     ![Screenshot mit Optionen zum Speichern und Verwerfen](./media/app-protection-policies/save-assignment.png)
  
Damit haben Sie eine Richtlinie erstellt und für die Benutzer bereitgestellt.

Von der Richtlinie sind nur Benutzer mit zugewiesenen Microsoft Intune-Lizenzen betroffen. Benutzer in der ausgewählten Sicherheitsgruppe, denen keine Intune-Lizenz zugewiesen wurde, sind nicht betroffen.

>[!IMPORTANT]
> Wenn Sie Intune mit Configuration Manager verwenden, um Ihre Geräte zu verwalten, wird die Richtlinie nur auf Benutzer in der Gruppe angewendet, die Sie ausgewählt haben. Mitglieder untergeordneter Gruppen, die in der ausgewählten Gruppe geschachtelt sind, sind nicht betroffen.

Endbenutzer können die Apps aus dem App Store oder aus Google Play herunterladen. Weitere Informationen finden Sie in folgenden Quellen:
* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-android.md)
* [Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-ios.md)

### <a name="change-existing-windows-10-policies"></a>Ändern vorhandener Windows 10-Richtlinien
Sie können eine vorhandene Richtlinie bearbeiten und sie auf die als Ziel festgelegten Benutzer anwenden. Wenn Sie vorhandene Richtlinien ändern, werden diese Änderungen für bei der App angemeldete Benutzer erst nach 8 Stunden sichtbar.

Für eine sofortige Anzeige der Änderungen muss der Endbenutzer sich von der App abmelden und dann erneut anmelden.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>So ändern Sie die Liste der Apps, die einer Richtlinie zugeordnet sind

1. Wählen Sie auf dem Blatt **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten.

2. Wählen Sie im Bereich *Intune-App-Schutz* die Option **Ziel-Apps** aus, um die Liste der Apps anzuzeigen.

3. Fügen Sie der Liste Apps hinzu, oder entfernen Sie Apps aus der Liste, und klicken Sie dann auf das Symbol **Speichern**, um die Änderungen zu speichern.

#### <a name="to-change-the-list-of-user-groups"></a>So ändern Sie die Liste der Benutzergruppen

1. Wählen Sie im Bereich **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten.

2. Wählen Sie im Bereich *Intune-App-Schutz* die Option **Zuweisungen** aus, um den Bereich **Intune-App-Schutz – Zuweisungen** zu öffnen. Hier wird die Liste mit aktuellen Benutzergruppen angezeigt, denen diese Richtlinie zugewiesen ist.

3. Um eine neue Benutzergruppe hinzuzufügen, wählen Sie auf der Registerkarte *Einschließen* die Option **Select groups to include** (Einzuschließende Gruppen auswählen) und anschließend die Benutzergruppe aus. Wählen Sie **Auswählen** aus, um die Gruppe hinzuzufügen. 

4. Um eine Benutzergruppe auszuschließen, wählen Sie auf der Registerkarte *Ausschließen* die Option **Wählen Sie die Gruppen aus, die ausgeschlossen werden sollen.** und anschließend die Benutzergruppe aus. Wählen Sie **Auswählen** aus, um die Benutzergruppe zu entfernen.  

5. Um Gruppen zu löschen, die zuvor auf einer der Registerkarten *Einschließen* oder *Ausschließen* hinzugefügt wurden, wählen Sie die Auslassungspunkte (...) und **Löschen** aus. 

5. Nachdem Ihre Änderungen der Zuweisungen bereit sind, wählen Sie **Speichern** zum Speichern der Konfiguration und Bereitstellen der Richtlinie für die neue Gruppe von Benutzern aus. Wenn Sie **Verwerfen** auswählen, bevor Sie Ihre Konfiguration speichern, verwerfen Sie alle Änderungen, die Sie auf den Registerkarten *Einschließen* und *Ausschließen* vorgenommen haben.

### <a name="to-change-windows-10-policy-settings"></a>Ändern der Einstellungen für Windows 10-Richtlinien

1. Wählen Sie im Bereich **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten.

2. Klicken Sie im Bereich *Intune-App-Schutz* auf **Eigenschaften**, um die Liste der Einstellungsbereiche zu öffnen, die Sie bearbeiten können. 

3. Wählen Sie den Einstellungsbereich aus, für den Sie Einstellungen ändern möchten, z.B. **Datenverschiebung** oder **Zugriffsanforderungen**. Legen Sie für die gewünschten Einstellungen neue Werte fest.

4. Klicken Sie auf das Symbol **Speichern**, um Ihre Änderungen zu speichern. Wiederholen Sie ggf. den Vorgang, um einen anderen Einstellungsbereich zu öffnen und die gewünschten Änderungen durchzuführen und zu speichern. Anschließend können Sie den Bereich *Intune-App-Schutz – Zuweisungen* schließen. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Verwendung von App-Schutzrichtlinien als Ziel, basierend auf dem Status der Geräteverwaltung
Viele Organisationen erlauben Benutzern sowohl die Verwendung von mit Intune-MDM verwalteten Geräten (z.B. unternehmenseigene Geräte) als auch die Verwendung von nicht verwalteten Geräten, die nur mit Intune App-Schutzrichtlinien geschützt werden. Nicht verwaltete Geräte werden häufig als BYOD-Geräte (Bring Your Own Device) bezeichnet.

Da die App-Schutzrichtlinien von Intune an die Identität eines Benutzers gekoppelt sind, können die Schutzeinstellungen sowohl auf registrierte (MDM-verwaltete) als auch auf nicht registrierte Geräte (kein MDM) angewendet werden. Aus diesem Grund können Sie mit einer App-Schutzrichtlinie von Intune entweder Intune-registrierte oder nicht registrierte iOS- und Android-Geräte als Ziel verwenden. Sie können über eine Schutzrichtlinie für nicht verwaltete Geräte verfügen, bei denen Steuerelemente für die Verhinderung von Datenverlust (DLP) vorhanden sind, und über eine separate Schutzrichtlinie für mit MDM-verwaltete Geräte, bei denen die DLP-Steuerelemente nicht so streng sind. Weitere Informationen dazu, wie dies bei persönlichen Android Enterprise-Geräten funktioniert, finden Sie unter [App-Schutzrichtlinien und Arbeitsprofile](android-deployment-scenarios-app-protection-work-profiles.md).

Um diese Richtlinien zu erstellen, navigieren Sie in der Intune-Konsole zu **Client-Apps** > **App-Schutzrichtlinien**, und klicken Sie dann auf **Richtlinie hinzufügen**. Sie können auch eine vorhandene App-Schutzrichtlinie bearbeiten. Navigieren Sie zur Seite **Apps**, und bestätigen Sie, dass die Option **Auf Apps auf allen Gerätetypen anwenden** auf den Standardwert **Ja** festgelegt ist, wenn die App-Schutzrichtlinie sowohl auf verwaltete als auch auf nicht verwaltete Geräte angewendet werden soll. Wenn Sie eine feiner abgestufte Zuweisung basierend auf dem Verwaltungszustand durchführen möchten, legen Sie die Option **Auf Apps auf allen Gerätetypen anwenden** auf **Nein** fest. 

![Screenshot vom Blatt „Richtlinie hinzufügen“ mit der Option „Auf alle App-Typen ausrichten“](./media/app-protection-policies/app-protection-policies-target-all.png)

### <a name="app-types"></a>App-Typen

- **Apps auf nicht verwalteten Geräten:** Nicht verwaltete Geräte sind Geräte, auf denen die Verwaltung mobiler Geräte von Intune nicht erkannt wurde. Dazu gehören auch MDM-Anbieter von Drittanbietern.
- **Apps auf von Intune verwalteten Geräten:** Verwaltete Geräte werden von der Verwaltung mobiler Geräte von Intune verwaltet.
- **Apps im Android-Arbeitsprofil:** Verwaltete Geräte, die als Android Enterprise-Arbeitsprofilgeräte registriert wurden.

> Beachten Sie, dass Android-Geräte aufgefordert werden, die Intune-Unternehmensportal-App zu installieren, unabhängig davon, welcher App-Typ gewählt wurde. Wenn Sie beispielsweise „Apps auf durch Intune verwalteten Geräten“ auswählen, werden Benutzer mit nicht verwalteten Android-Geräten weiterhin dazu aufgefordert.

Für iOS sind zusätzliche App-Konfigurationseinstellungen erforderlich, um App-Schutzrichtlinieneinstellungen für Apps auf in Intune registrierten Geräten bereitzustellen:

- **IntuneMAMUPN** muss für alle mit MDM verwalteten Anwendungen konfiguriert sein. Weitere Informationen finden Sie unter [Verwalten der Datenübertragung zwischen iOS-Apps in Microsoft Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- **IntuneMAMDeviceID** muss für alle mit MDM verwalteten Drittanbieter- und Branchenanwendungen konfiguriert sein. **IntuneMAMDeviceID** sollte auf das Geräte-ID-Token konfiguriert sein. Beispiel: `key=IntuneMAMDeviceID, value={{deviceID}}`. Weitere Informationen finden Sie unter [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete iOS-Geräte](app-configuration-policies-use-ios.md).
- Wenn nur **IntuneMAMDeviceID** konfiguriert ist, betrachtet die Intune-APP das Gerät als nicht verwaltet.

> [!NOTE]
> Spezifische iOS-Supportinfomationen über App-Schutzrichtlinien basierend auf dem Status der Geräteverwaltung finden Sie unter [MAM protection policies targeted based on management state (Angesteuerte MAM-Schutzrichtlinien basierend auf dem Verwaltungsstatus)](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-).

## <a name="policy-settings"></a>Richtlinieneinstellungen
Eine vollständige Liste der Richtlinieneinstellungen für iOS und Android finden Sie unter den folgenden Links:

- [iOS-Richtlinien](app-protection-policy-settings-ios.md)
- [Android-Richtlinien](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Nächste Schritte
[Überwachen der Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](app-protection-policies-monitor.md)

## <a name="see-also"></a>Siehe auch
* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-android.md)
* [Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-ios.md)
