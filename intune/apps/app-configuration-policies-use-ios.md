---
title: Hinzufügen App-Konfigurationsrichtlinien für verwaltete iOS-Geräte
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie App-Konfigurationsrichtlinien zum Bereitstellen von Konfigurationsdaten für eine iOS-App beim Ausführen verwenden.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94480c8dcfe44dc451ea6a2409f52f06c2a87cf5
ms.sourcegitcommit: b8127c7a62d9ac4d0f768980fa1424567bb58733
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72350070"
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Hinzufügen App-Konfigurationsrichtlinien für verwaltete iOS-Geräte

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Verwenden Sie App-Konfigurationsrichtlinien in Microsoft Intune, um benutzerdefinierte Konfigurationseinstellungen für eine iOS-App anzugeben. Mit diesen Konfigurationseinstellungen kann eine App basierend auf den Anweisungen des App-Herstellers angepasst werden. Diese Konfigurationseinstellungen (Schlüssel und Werte) müssen Sie vom Hersteller der App abrufen. Sie geben diese Einstellungen als Schlüssel und Werte oder als XML-Daten an, die die Schlüssel und Werte enthalten, um die App zu konfigurieren.

Wie der Microsoft Intune-Administrator können Sie steuern, welche Benutzerkonten Microsoft Office-Anwendungen auf verwalteten Geräten hinzugefügt werden. Sie können den Zugriff auf zulässige Organisationsbenutzerkonten beschränken und persönliche Konten auf registrierten Geräten blockieren. Die unterstützenden Anwendungen verarbeiten die App-Konfiguration und entfernen und blockieren nicht genehmigte Konten. Die Konfigurationsrichtlinieneinstellungen werden verwendet, wenn die App danach sucht (in der Regel beim ersten Ausführen).

Nachdem Sie eine App-Konfigurationsrichtlinie hinzugefügt haben, können Sie die Zuweisungen für die App-Konfigurationsrichtlinie festlegen. Wenn Sie die Zuweisungen für die Richtlinie festlegen, können Sie entscheiden, ob Gruppen von Benutzern ein- und ausgeschlossen werden, für welche die Richtlinie angewendet wird. Wenn Sie entscheiden, eine oder mehrere Gruppen einzuschließen, können Sie bestimmte einzuschließende Gruppen oder integrierte Gruppen auswählen. Zu den integrierten Gruppen zählen **Alle Benutzer**, **Alle Geräte** und **Alle Benutzer und alle Geräte**. 

> [!NOTE]
> Intune bietet die vorab erstellten Gruppen **Alle Benutzer** und **Alle Geräte** in der Konsole zur Vereinfachung mit integrierten Optimierungen an. Sie sollten diese Gruppen unbedingt anstelle möglicherweise selbst erstellter „Alle Benutzer“- oder „Alle Geräte“-Gruppen verwenden, um alle Benutzer und alle Geräte zu erreichen.

Nachdem Sie die eingeschlossenen Gruppen für Ihre Anwendungskonfigurationsrichtlinie ausgewählt haben, können Sie auch die bestimmten auszuschließenden Gruppen auswählen. Weitere Informationen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](apps-inc-exl-assignments.md).

> [!TIP]
> Dieser Richtlinientyp ist zurzeit nur für Geräte unter iOS 8.0 und höher verfügbar. Er unterstützt die folgenden App-Installationstypen:
>
> - **Verwaltete iOS-App aus dem App Store**
> - **App-Paket für iOS**
>
> Weitere Informationen zu Installationstypen von Apps finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md). Weitere Informationen zum Einbinden der App-Konfiguration in das IPA-App-Paket für verwaltete Geräte finden Sie unter „Konfiguration einer verwalteten App“ in der [Entwicklerdokumentation von iOS](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html).

## <a name="create-an-app-configuration-policy"></a>Erstellen einer Konfigurationsrichtlinie für Apps

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie die Workload **Client-Apps** aus.
4. Wählen Sie in der Gruppe **Verwalten** **App-Konfigurationsrichtlinien** und dann **Hinzufügen** aus.
5. Legen Sie die folgenden Details fest:
    - **Name:** Der Name des Profils, das im Azure-Portal angezeigt wird.
    - **Beschreibung:** Die Beschreibung des Profils, das im Azure-Portal angezeigt wird.
    - **Geräteregistrierungstyp:** Wählen Sie für Geräte, die bei Intune registriert wurden, die Option **Verwaltete Geräte** aus.
6. Wählen Sie **iOS** als **Plattform** aus.
7. Wählen Sie **Zugeordnete App** aus. Wählen Sie anschließend im Bereich **Zugeordnete App** die verwaltete App aus, auf die Sie die Konfiguration anwenden möchten, und klicken Sie auf **OK**.
8. Wählen Sie im Bereich **Konfigurationsrichtlinie hinzufügen** die Option **Konfigurationseinstellungen** aus.
9. Wählen Sie das **Format der Konfigurationseinstellungen** aus. Wählen Sie zum Hinzufügen von Konfigurationsinformationen eine der folgenden Methoden aus:
    - **Verwenden des Konfigurations-Designers**
    - **Eingeben von XML-Daten**<br><br>
    Ausführliche Informationen zur Verwendung des Konfigurations-Designers finden Sie unter [Verwenden des Konfigurations-Designers](#use-configuration-designer). Ausführliche Informationen zum Eingeben von XML-Daten finden Sie unter [Eingeben von XML-Daten](#enter-xml-data). 
10. Nachdem Sie die Konfigurationsinformationen hinzugefügt haben, klicken Sie auf **OK**. Klicken Sie anschließend auf **Hinzufügen**, um die Konfigurationsrichtlinie hinzuzufügen. Der Übersichtsbereich für die Konfigurationsrichtlinie wird angezeigt.
11. Wählen Sie **Zuweisungen**, um die Ein- und Ausschlussoptionen anzuzeigen. 

    ![Screenshot der Registerkarte „Einschließen“ im Bereich „Richtlinienzuweisungen“](./media/app-configuration-policies-use-ios/app-config-policy01.png)
12. Wählen Sie **Alle Benutzer** auf der Registerkarte **Einschließen**.

    ![Screenshot der Dropdown-Option „Alle Benutzer“ im Bereich „Richtlinienzuweisungen“](./media/app-configuration-policies-use-ios/app-config-policy02.png)
13. Wählen Sie die Registerkarte **Ausschließen**. 
14. Klicken Sie auf **Select groups to exclude** (Auszuschließende Gruppen auswählen), um den zugehörigen Bereich anzuzeigen.

    ![Screenshot des Blatts „Select groups to exclude“ (Auszuschließende Gruppen auswählen) im Bereich „Richtlinienzuweisungen“](./media/app-configuration-policies-use-ios/app-config-policy03.png)
15. Wählen Sie die Gruppen aus, die Sie ausschließen möchten, und klicken Sie dann auf **Auswählen**.

    >[!NOTE]
    >Beachten Sie beim Hinzufügen einer Gruppe Folgendes: Wenn eine Gruppe bereits für einen bestimmten Zuweisungstyp eingeschlossen wurde, ist diese vorausgewählt und kann für andere Einschlusszuweisungstypen nicht mehr geändert werden. Darum kann die Gruppe, die verwendet wurde, nicht als ausgeschlossene Gruppe verwendet werden.
16. Klicken Sie auf **Speichern**.

## <a name="use-configuration-designer"></a>Verwenden des Konfigurations-Designers

Microsoft Intune bietet Konfigurationseinstellungen, die für eine App eindeutig sind. Sie können den Konfigurations-Designer für Apps auf Geräten verwenden, unabhängig davon, ob sie in Microsoft Intune registriert sind. Mit dem Designer können Sie spezifische Konfigurationsschlüssel und -werte konfigurieren, die Ihnen beim Erstellen der zugrundeliegenden XML-Daten helfen. Sie müssen ebenfalls den Datentyp für jeden Wert angeben. Diese Einstellungen werden Apps automatisch bereitgestellt, wenn sie installiert werden.

### <a name="add-a-setting"></a>Hinzufügen einer Einstellung

1. Legen Sie für jeden Schlüssel und jeden Wert in der Konfiguration Folgendes fest:
   - **Konfigurationsschlüssel:** Der Schlüssel, der die spezifische Einstellungskonfiguration eindeutig identifiziert.
   - **Werttyp:** Der Datentyp des Konfigurationswerts. Zu den Typen gehören Integer, Real, String oder Boolean.
   - **Konfigurationswert:** Der Wert für die Konfiguration.
2. Wählen Sie **OK** aus, um Ihre Konfigurationseinstellungen festzulegen.

### <a name="delete-a-setting"></a>Löschen einer Einstellung

1. Wählen Sie die Auslassungspunkte ( **...** ) neben der Einstellung aus.
2. Klicken Sie auf **Löschen**.

Die Zeichen \{\{ und \}\} werden nur von Tokentypen verwendet und dürfen nicht für andere Zwecke verwendet werden.

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Nur Zulassen von konfigurierten Organisationskonten in Apps mit mehreren Identitäten 

Verwenden Sie für iOS-Geräte die folgenden Schlüssel-Wert-Paare:

| **Key** | IntuneMAMAllowedAccountsOnly |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Werte** | <ul><li>**Aktiviert**: Das einzige zulässige Konto ist das verwaltete Benutzerkonto, das von dem Schlüssel [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm) definiert wird.</li><li>**Deaktiviert** (oder jeder andere Wert, der keine Übereinstimmung mit **Aktiviert** ohne Beachtung der Groß-/Kleinschreibung ist): Jedes Konto ist zulässig.</li></ul> |.

   > [!NOTE]
   > Sie müssen OneDrive für iOS 10.34 oder höher, Outlook für iOS 2.99.0 oder höher oder Edge für iOS 44.8.7 oder höher verwenden, und für die App müssen [Intune-App-Schutzrichtlinien](app-protection-policy.md) eingerichtet sein, wenn Sie nur konfigurierte Organisationskonten mit mehreren Identitäten zulassen.

## <a name="enter-xml-data"></a>Eingeben von XML-Daten

Sie können eine XML-Eigenschaftenliste eingeben oder einfügen, die die App-Konfigurationseinstellungen für in Intune registrierte Geräte enthält. Das Format der XML-Eigenschaftenliste variiert je nach der App, die Sie konfigurieren. Wenden Sie sich an den Hersteller der App, um ausführliche Informationen über das genau zu verwendende Format zu erhalten.

Intune überprüft das XML-Format. Intune überprüft jedoch nicht, ob die XML-Eigenschaftenliste (PList) mit der Ziel-App verwendet werden kann.

Weitere Informationen zu XML-Eigenschaftenlisten:

- Lesen Sie unter [Understand XML Property Lists (Grundlegendes zu XML-Eigenschaftenlisten)](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) in der iOS-Entwicklerbibliothek nach.

### <a name="example-format-for-an-app-configuration-xml-file"></a>Beispielformat für eine App-Konfigurations-XML-Datei

Wenn Sie eine App-Konfigurationsdatei erstellen, können Sie die folgenden Werte in diesem Format angeben:

```xml
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
  <key>aaddeviceid</key>
  <string>{{aaddeviceid}}</string>
</dict>
```

### <a name="supported-xml-plist-data-types"></a>Unterstützte XML-PList-Datentypen

Intune unterstützt die folgenden Datentypen in einer Eigenschaftenliste:

- &lt;integer&gt;
- &lt;real&gt;
- &lt;string&gt;
- &lt;array&gt;
- &lt;dict&gt;
- &lt;true /&gt; oder &lt;false /&gt;

### <a name="tokens-used-in-the-property-list"></a>Tokens, die in der Eigenschaftenliste verwendet werden.

Darüber hinaus unterstützt Intune die folgenden Tokentypen in der Eigenschaftenliste:
- \{\{userPrincipalName\}\}: z.B. **John@contoso.com**
- \{\{Mail\}\}: z.B. **John@contoso.com**
- \{\{partialupn\}\}: z.B. **John**
- \{\{accountid\}\}: z.B. **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\}: z.B. **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\}: z.B. **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\}: z.B. **John Doe**
- \{\{serialnumber\}\}: z.B. **F4KN99ZUG5V2** (für iOS-Geräte)
- \{\{serialnumberlast4digits\}\}: z.B. **G5V2** (für iOS-Geräte)
- \{\{aaddeviceid\}\}: z.B. **ab0dc123-45d6-7e89-aabb-cde0a1234b56**

## <a name="configure-the-company-portal-app-to-support-ios-dep-devices"></a>Konfigurieren der Unternehmensportal-App zur Unterstützung von iOS-DEP-Geräten

DEP-Registrierungen (Apple-Programm zur Geräteregistrierung) sind nicht kompatibel mit der App Store-Version der Unternehmensportal-App. Sie können die Unternehmensportal-App jedoch für die Unterstützung von iOS-DEP-Geräten konfigurieren.

1. Führen Sie dazu im Azure-Portal in Intune die folgenden Schritte aus:
    - Fügen Sie ggf. das Intune-Unternehmensportal hinzu (**Intune** > **Client-Apps** > **Apps** > **Hinzufügen**).
    - Klicken Sie auf **Client-Apps** > **App-Konfigurationsrichtlinien**, um eine App-Konfigurationsrichtlinie für die Unternehmensportal-App zu erstellen.
2. Erstellen Sie mithilfe der unten stehenden XML-Daten eine App-Konfigurationsrichtlinie. Weitere Informationen zum Erstellen einer App-Konfigurationsrichtlinie und zum Eingeben von XML-Daten finden Sie unter [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete iOS-Geräte](app-configuration-policies-use-ios.md) oder für Hybrid-MDM unter [Anwenden von Einstellungen für iOS-Apps mit App-Konfigurationsrichtlinien in System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-ios-apps-with-app-configuration-policies).

    ``` xml
    <dict>
        <key>IntuneCompanyPortalEnrollmentAfterUDA</key>
        <dict>
            <key>IntuneDeviceId</key>
            <string>{{deviceid}}</string>
            <key>UserId</key>
            <string>{{userid}}</string>
        </dict>
    </dict>
    ```

3. Stellen Sie das Unternehmensportal mit der App-Konfigurationsrichtlinie für die gewünschten Zielgruppen bereit. Stellen Sie sicher, dass die Richtlinie nur für Gerätegruppen bereitgestellt wird, die bereits mit DEP registriert sind.
4. Fordern Sie die Benutzer bei der automatischen Installation auf, sich bei der Unternehmensportal-App anzumelden.

## <a name="monitor-ios--app-configuration-status-per-device"></a>Überwachen des Konfigurationsstatus von iOS-Apps pro Gerät 
Sobald eine Konfigurationsrichtlinie zugewiesen wurde, können Sie den Konfigurationsstatus von iOS-Apps für jedes verwaltete Gerät überwachen. Klicken Sie im Azure-Portal unter **Microsoft Intune** auf **Geräte** > **Alle Geräte**. Wählen Sie aus der Liste der verwalteten Geräte ein Gerät aus, für das ein Blatt angezeigt werden soll. Klicken Sie auf dem Geräteblatt auf **App-Konfiguration**.  

## <a name="additional-information"></a>Zusätzliche Informationen

- [Bereitstellen von Outlook für iOS- und Android-App-Konfigurationseinstellungen](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie damit fort, die App [zuzuweisen](apps-deploy.md) und zu [überwachen](apps-monitor.md).
