---
title: Erstellen und Bereitstellen von App-Schutzrichtlinien
titleSuffix: Microsoft Intune
description: In diesem Thema wird beschrieben, wie Sie Microsoft Intune-App-Schutzrichtlinien (APP) erstellen und zuweisen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: c7a6914e8174023704cfc593ec08a525ec5889f3
ms.sourcegitcommit: ecaff388038fb800f2e646f8efcf8f3b1e2fd1b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2020
ms.locfileid: "77437901"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Erstellen und Zuweisen von App-Schutzrichtlinien

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Informieren Sie sich, wie Sie Microsoft Intune-App-Schutzrichtlinien (APP) für Benutzer Ihrer Organisation erstellen und diesen zuweisen. In diesem Thema wird beschrieben, wie Änderungen an bestehenden Richtlinien vorgenommen werden.

## <a name="before-you-begin"></a>Vorbereitung

App-Schutzrichtlinien können unabhängig davon auf Apps angewendet werden, ob die Geräte, auf denen die Apps ausgeführt werden, von Intune verwaltet werden. Eine ausführlichere Beschreibung der Funktionsweise von App-Schutzrichtlinien und der von Intune-App-Schutzrichtlinien unterstützten Szenarien finden Sie unter [Was sind Microsoft Intune-App-Schutzrichtlinien?](app-protection-policy.md).

Wenn Sie nach einer Liste der unterstützten MAM-Apps suchen, finden Sie weitere Informationen in der [Liste der MAM-Apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Informationen zum Hinzufügen von Line-of-Business-Apps (LOB) Ihrer Organisation zu Microsoft Intune in Vorbereitung auf App-Schutzrichtlinien finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>App-Schutzrichtlinien für iOS-/iPadOS- und Android-Apps

Befolgen Sie beim Erstellen neuer App-Schutzrichtlinien für iOS-/iPadOS- und Android-Apps einen modernen Intune-Prozessablauf für App-Schutzrichtlinien.

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>Erstellen einer iOS-/iPadOS- oder Android-App-Schutzrichtlinie
1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie im Intune-Portal **Apps** > **App-Schutzrichtlinien** aus. Mit dieser Auswahl werden die Details zu **App-Schutzrichtlinien** geöffnet und Sie können neue Richtlinien erstellen und vorhandene bearbeiten.
3. Klicken Sie auf **Richtlinie erstellen**, und wählen Sie entweder **iOS/iPadOS** oder **Android** aus. Der Bereich **Richtlinie erstellen** wird angezeigt.
4. Fügen Sie auf der Seite **Basics** (Grundeinstellungen) die folgenden Werte hinzu:

    | Wert | Beschreibung |
    |--------------|------------------------------------------------|
    | Name | Name der App-Schutzrichtlinie |
    | Beschreibung | [Optional] Beschreibung der App-Schutzrichtlinie |


    Der Wert **Plattform** wird basierend auf der oben von Ihnen ausgewählten Option festgelegt.

    ![Screenshot der Seite „Grundeinstellungen“ im Bereich „Richtlinie erstellen“](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. Klicken Sie auf **Weiter**, um die Seite **Apps** anzuzeigen.<br>
    Auf der Seite **Apps** können Sie auswählen, wie Sie diese Richtlinie auf Apps auf verschiedenen Geräten anwenden möchten. Sie müssen mindestens eine App hinzufügen.<p>
    
    | Wert/Option | Beschreibung |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Auf Apps auf allen Gerätetypen anwenden | Verwenden Sie diese Option, um die Richtlinie auf Apps auf Geräten mit beliebigem Verwaltungsstatus anzuwenden. Klicken Sie auf **Nein**, um die Richtlinie auf Apps auf bestimmten Gerätetypen anzuwenden. Weitere Informationen finden Sie unter [Verwendung von App-Schutzrichtlinien als Ziel, basierend auf dem Status der Geräteverwaltung](#target-app-protection-policies-based-on-device-management-state). |
    |     Device types (Gerätetypen) | Verwenden Sie diese Option, um anzugeben, ob diese Richtlinie für mit MDM verwaltete oder nicht verwaltete Geräte gilt. Wählen Sie für iOS-/iPadOS-App-Richtlinien **Unmanaged devices** (Nicht verwaltete Geräte) und **Managed devices** (Verwaltete Geräte) aus. Wählen Sie für Android-App-Richtlinien **Unmanaged Devices** (Nicht verwaltete Geräte), **Android device administrator** (Android-Geräteadministrator) und **Android Enterprise** aus.  |
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

9. Klicken Sie auf **Weiter**, um die Seite **Zuweisungen** anzuzeigen.<br>
   Mit der Seite **Zuweisungen** können Sie die App-Schutzrichtlinie bestimmten Gruppen von Benutzern zuweisen.

10. Klicken Sie auf **Next: Review and create** (Weiter: Überprüfen und erstellen), um die Werte und Einstellungen zu überprüfen, die Sie für diese App-Schutzrichtlinie eingegeben haben.

11. Klicken Sie abschließend auf **Erstellen**, um die App-Schutzrichtlinie in Intune zu erstellen. 

    > [!TIP]
    > Diese Richtlinieneinstellungen werden nur durchgesetzt, wenn Apps im beruflichen Kontext verwendet werden. Wenn der Endbenutzer die App zum Erledigen einer privaten Aufgabe verwendet, ist er von diesen Richtlinien nicht betroffen. Beachten Sie, dass Dateien, die Sie neu erstellen, als persönliche Dateien angesehen werden. 

Endbenutzer können die Apps aus dem App Store oder aus Google Play herunterladen. Weitere Informationen finden Sie in folgenden Quellen:
* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-android.md)
* [Was Sie erwartet, wenn Ihre iOS-/iPadOS-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-ios.md)

## <a name="change-existing-policies"></a>Ändern vorhandener Richtlinien
Sie können eine vorhandene Richtlinie bearbeiten und sie auf die als Ziel festgelegten Benutzer anwenden. Wenn Sie vorhandene Richtlinien ändern, werden diese Änderungen für bei der App angemeldete Benutzer erst nach 8 Stunden sichtbar.

Für eine sofortige Anzeige der Änderungen muss der Endbenutzer sich von der App abmelden und dann erneut anmelden.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>So ändern Sie die Liste der Apps, die einer Richtlinie zugeordnet sind

1. Wählen Sie auf dem Blatt **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten.

2. Wählen Sie im Bereich *Intune-App-Schutz* die Option **Eigenschaften** aus.

3. Wählen Sie neben dem Abschnitt *Apps* die Option **Bearbeiten** aus.

4. Auf der Seite **Apps** können Sie auswählen, wie Sie diese Richtlinie auf Apps auf verschiedenen Geräten anwenden möchten. Sie müssen mindestens eine App hinzufügen.<p>
    
    | Wert/Option | Beschreibung |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Auf Apps auf allen Gerätetypen anwenden | Verwenden Sie diese Option, um die Richtlinie auf Apps auf Geräten mit beliebigem Verwaltungsstatus anzuwenden. Klicken Sie auf **Nein**, um die Richtlinie auf Apps auf bestimmten Gerätetypen anzuwenden. Weitere Informationen finden Sie unter [Verwendung von App-Schutzrichtlinien als Ziel, basierend auf dem Status der Geräteverwaltung](#target-app-protection-policies-based-on-device-management-state). |
    |     Device types (Gerätetypen) | Verwenden Sie diese Option, um anzugeben, ob diese Richtlinie für mit MDM verwaltete oder nicht verwaltete Geräte gilt. Wählen Sie für iOS-/iPadOS-App-Richtlinien **Unmanaged devices** (Nicht verwaltete Geräte) und **Managed devices** (Verwaltete Geräte) aus. Wählen Sie für Android-App-Richtlinien **Unmanaged Devices** (Nicht verwaltete Geräte), **Android device administrator** (Android-Geräteadministrator) und **Android Enterprise** aus.  |
    | Public apps (Öffentliche Apps) | Klicken Sie auf **Select public apps** (Öffentliche Apps auswählen), um die gewünschten Apps als Ziel auszuwählen. |
    | Custom apps (Benutzerdefinierte Apps) | Klicken Sie auf **Select custom apps** (Benutzerdefinierte Apps auswählen), um basierend auf einer Paket-ID benutzerdefinierte Apps als Ziel auszuwählen. |

    Die ausgewählten Apps werden in der öffentlichen und benutzerdefinierten App-Liste angezeigt. 

5. Klicken Sie auf **Überprüfen + erstellen**, um die für diese Richtlinie ausgewählten Apps zu überprüfen.

6. Klicken Sie abschließend auf **Speichern**, um die App-Schutzrichtlinie zu aktualisieren.
 
#### <a name="to-change-the-list-of-user-groups"></a>So ändern Sie die Liste der Benutzergruppen

1. Wählen Sie auf dem Blatt **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten.

2. Wählen Sie im Bereich *Intune-App-Schutz* die Option **Eigenschaften** aus.

3. Wählen Sie neben dem Abschnitt *Zuweisungen* die Option **Bearbeiten** aus.

4. Um eine neue Benutzergruppe hinzuzufügen, wählen Sie auf der Registerkarte *Einschließen* die Option **Select groups to include** (Einzuschließende Gruppen auswählen) und anschließend die Benutzergruppe aus. Wählen Sie **Auswählen** aus, um die Gruppe hinzuzufügen. 

5. Um eine Benutzergruppe auszuschließen, wählen Sie auf der Registerkarte *Ausschließen* die Option **Wählen Sie die Gruppen aus, die ausgeschlossen werden sollen.** und anschließend die Benutzergruppe aus. Wählen Sie **Auswählen** aus, um die Benutzergruppe zu entfernen.  

6. Um Gruppen zu löschen, die zuvor auf einer der Registerkarten *Einschließen* oder *Ausschließen* hinzugefügt wurden, wählen Sie die Auslassungspunkte (...) und **Löschen** aus.

7. Klicken Sie auf **Überprüfen + erstellen**, um die für diese Richtlinie ausgewählten Benutzergruppen zu überprüfen.

8. Nachdem Ihre Änderungen der Zuweisungen bereit sind, wählen Sie **Speichern** zum Speichern der Konfiguration und Bereitstellen der Richtlinie für die neue Gruppe von Benutzern aus. Wenn Sie **Abbrechen** auswählen, bevor Sie Ihre Konfiguration speichern, verwerfen Sie alle Änderungen, die Sie auf den Registerkarten *Einschließen* und *Ausschließen* vorgenommen haben.

### <a name="to-change-policy-settings"></a>So ändern Sie Richtlinieneinstellungen

1. Wählen Sie auf dem Blatt **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten.

2. Wählen Sie im Bereich *Intune-App-Schutz* die Option **Eigenschaften** aus.

3. Wählen Sie neben dem Abschnitt, der den Einstellungen entspricht, die Sie ändern möchten, **Bearbeiten** aus. Legen Sie für die gewünschten Einstellungen neue Werte fest.

7. Klicken Sie auf **Überprüfen + erstellen**, um die für diese Richtlinie aktualisierten Einstellungen zu überprüfen.

4. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern. Wiederholen Sie ggf. den Vorgang, um einen anderen Einstellungsbereich zu öffnen und die gewünschten Änderungen durchzuführen und zu speichern. Anschließend können Sie den Bereich *Intune-App-Schutz – Zuweisungen* schließen. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Verwendung von App-Schutzrichtlinien als Ziel, basierend auf dem Status der Geräteverwaltung
Viele Organisationen erlauben Benutzern sowohl die Verwendung von mit Intune-MDM verwalteten Geräten (z.B. unternehmenseigene Geräte) als auch die Verwendung von nicht verwalteten Geräten, die nur mit Intune App-Schutzrichtlinien geschützt werden. Nicht verwaltete Geräte werden häufig als BYOD-Geräte (Bring Your Own Device) bezeichnet.

Da die App-Schutzrichtlinien von Intune an die Identität eines Benutzers gekoppelt sind, können die Schutzeinstellungen sowohl auf registrierte (MDM-verwaltete) als auch auf nicht registrierte Geräte (kein MDM) angewendet werden. Aus diesem Grund können Sie mit einer App-Schutzrichtlinie von Intune entweder Intune-registrierte oder nicht registrierte iOS-/iPadOS- und Android-Geräte als Ziel verwenden. Sie können über eine Schutzrichtlinie für nicht verwaltete Geräte verfügen, bei denen Steuerelemente für die Verhinderung von Datenverlust (DLP) vorhanden sind, und über eine separate Schutzrichtlinie für mit MDM-verwaltete Geräte, bei denen die DLP-Steuerelemente nicht so streng sind. Weitere Informationen dazu, wie dies bei persönlichen Android Enterprise-Geräten funktioniert, finden Sie unter [App-Schutzrichtlinien und Arbeitsprofile](android-deployment-scenarios-app-protection-work-profiles.md).

Um diese Richtlinien zu erstellen, navigieren Sie in der Intune-Konsole zu **Apps** > **App-Schutzrichtlinien**, und wählen Sie dann **Richtlinie hinzufügen** aus. Sie können auch eine vorhandene App-Schutzrichtlinie bearbeiten. Navigieren Sie zur Seite **Apps**, und bestätigen Sie, dass die Option **Auf Apps auf allen Gerätetypen anwenden** auf den Standardwert **Ja** festgelegt ist, wenn die App-Schutzrichtlinie sowohl auf verwaltete als auch auf nicht verwaltete Geräte angewendet werden soll. Wenn Sie eine feiner abgestufte Zuweisung basierend auf dem Verwaltungszustand durchführen möchten, legen Sie die Option **Auf Apps auf allen Gerätetypen anwenden** auf **Nein** fest. 

### <a name="device-types"></a>Device types (Gerätetypen)

- **Nicht verwaltet**: Nicht verwaltete Geräte sind Geräte, auf denen die Verwaltung mobiler Geräte von Intune nicht erkannt wurde. Dies umfasst auch Geräte, die von MDM-Drittanbietern verwaltet werden.
- **Mit Intune verwaltete Geräte**: Verwaltete Geräte werden von der Verwaltung mobiler Geräte von Intune verwaltet.
- **Android-Geräteadministrator**: Von Intune verwaltete Geräte, die die Android-Geräteverwaltungs-API verwenden.
- **Android Enterprise**: Von Intune verwaltete Geräte, die Android Enterprise-Arbeitsprofile oder Android Enterprise-Full Device Management verwenden.

> [!NOTE]
> Android-Geräte fordern dazu auf, die Intune-Unternehmensportal-App zu installieren, unabhängig davon, welcher Gerätetyp gewählt wurde. Wenn Sie beispielsweise „Android Enterprise“ auswählen, werden Benutzer mit nicht verwalteten Android-Geräten weiterhin dazu aufgefordert.

Für iOS sind zusätzliche App-Konfigurationseinstellungen erforderlich, um App-Schutzrichtlinieneinstellungen für Apps auf in Intune registrierten Geräten bereitzustellen:

- **IntuneMAMUPN** muss für alle mit MDM verwalteten Anwendungen konfiguriert sein. Weitere Informationen finden Sie unter [Verwalten der Datenübertragung zwischen iOS-/iPadOS-Apps in Microsoft Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- **IntuneMAMDeviceID** muss für alle mit MDM verwalteten Drittanbieter- und Branchenanwendungen konfiguriert sein. **IntuneMAMDeviceID** sollte auf das Geräte-ID-Token konfiguriert sein. Beispiel: `key=IntuneMAMDeviceID, value={{deviceID}}`. Weitere Informationen finden Sie unter [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete iOS-/iPadOS-Geräte](app-configuration-policies-use-ios.md).
- Wenn nur **IntuneMAMDeviceID** konfiguriert ist, betrachtet die Intune-APP das Gerät als nicht verwaltet.

> [!NOTE]
> Spezifische iOS-/iPadOS-Supportinfomationen über App-Schutzrichtlinien basierend auf dem Status der Geräteverwaltung finden Sie unter [Anwenden von MAM-Schutzrichtlinien je nach Verwaltungsstatus](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state).

## <a name="policy-settings"></a>Richtlinieneinstellungen
Eine vollständige Liste der Richtlinieneinstellungen für iOS/iPadOS und Android finden Sie unter den folgenden Links:

- [iOS-Richtlinien](app-protection-policy-settings-ios.md)
- [Android-Richtlinien](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Nächste Schritte
[Überwachen der Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](app-protection-policies-monitor.md)

## <a name="see-also"></a>Weitere Informationen:
* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-android.md)
* [Was Sie erwartet, wenn Ihre iOS-/iPadOS-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-ios.md)
