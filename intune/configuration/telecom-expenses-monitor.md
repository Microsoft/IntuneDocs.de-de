---
title: Einrichten eines TEM-Diensts (Telecom Expense Management) in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Integrieren Sie Microsoft Intune in den TEM-Dienst (Telecom Expense Management) von Saaswedo, um die Datennutzung zu überwachen und Schwellen- oder Grenzwerte auf Android- und iOS-Geräten festzulegen.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ce9a6916cc77714a87aeac33555c0be1e59463f5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506628"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Einrichten eines TEM-Diensts (Telecom Expense Management) in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Über Intune können Sie Telekommunikationsausgaben aufgrund von Datennutzung auf organisationseigenen mobilen Geräten verwalten. Intune lässt sich in das [TEM-System „Datalert“](http://datalert.biz/get-started) von Saaswedo integrieren. Datalert ist eine TEM-Lösung, mit der Sie die Nutzung von Telekommunikationsdaten in Echtzeit verwalten können. Diese Lösung hilft Ihnen dabei, unerwartete und teure Daten- und Roaminggebühren für Ihre mit Intune verwalteten Geräte zu vermeiden.

Durch die Integration in Datalert können Sie Datennutzungslimits im In- und Ausland festlegen, überwachen und erzwingen. Wenn die definierten Schwellenwerte überschritten werden, werden automatisch Warnungen ausgelöst. Sie können den Dienst auch so konfigurieren, dass verschiedene Aktionen für Einzelpersonen oder Gruppen angewendet werden: z. B. kann das Roaming deaktiviert oder Schwellenwerten können überschritten werden. Die Datalert-Verwaltungskonsole enthält Berichte mit Informationen zur Datennutzung und Überwachung.

Die folgende Abbildung zeigt, wie Intune in Datalert integriert wird:

  ![Diagramm der Integration von Intune und Datalert](./media/telecom-expenses-monitor/tem-datalert-intune-solution-diagram.png)

Um den Datalert-Dienst mit Intune zu verwenden, müssen Sie einige Konfigurationseinstellungen in Datalert und Intune einrichten. In diesem Artikel erfahren Sie, wie Sie Folgendes durchführen:

- Konfigurieren Sie Einstellungen in der Datalert-Konsole, um den Datalert-Dienst mit Intune zu verbinden.
- Überprüfen Sie, ob die Verbindung aktiv und in Intune aktiviert ist.
- Verwenden Sie Intune, um die Datalert-App zu Ihren Geräten hinzuzufügen.
- Deaktivieren Sie den Datalert-Dienst für Intune (optional).

## <a name="supported-platforms"></a>Unterstützte Plattformen

- Geräte unter Android 4.4 und höher, auf denen Knox verwendet werden kann (Samsung)

  Auf dieser [Samsung-Website](https://seap.samsung.com/faq/what-versions-android-support-knox-standard-and-knox-premium-sdks-0) werden die Android-Versionen aufgelistet, die Knox unterstützen.

- iOS 8.0 und höher

## <a name="prerequisites"></a>Voraussetzungen

- Ein Abonnement für Microsoft Intune und Zugriff auf das [Azure-Portal](https://portal.azure.com)
- Ein Abonnement für [Datalert](http://www.datalert.biz/) (öffnet die Datalert-Website)

## <a name="telecom-expense-management-providers"></a>Anbieter von Telecom Expense Management-Lösungen

Intune lässt sich in folgende TEM-Anbieter integrieren:

- [Datalert-TEM-Dienst von Saaswedo](http://www.datalert.biz/) (öffnet die Datalert-Website)

## <a name="deploy-the-intune-and-datalert-solution"></a>Bereitstellen der Lösung mit Intune und Datalert

### <a name="step-1-connect-the-datalert-service-to-intune"></a>Schritt 1: Verbinden des Datalert-Diensts mit Intune

1. Melden Sie sich mit Administratoranmeldeinformationen bei der Datalert-Verwaltungskonsole an.

2. Wechseln Sie in der Konsole zur Registerkarte **Settings** (Einstellungen) > **MDM configuration** (MDM-Konfiguration).

3. Klicken Sie auf **Unblock** (Entsperren). Mit **Unblock** können Sie die Einstellungen auf der Seite ändern oder aktualisieren.

4. Wählen Sie unter **Intune / Datalert Connection** > **Server MDM** (Verbindung zwischen Intune und Datalert > Server-MDM) die Option **Microsoft Intune** aus.

5. Geben Sie unter **Azure AD domain** (Azure AD-Domäne) Ihre Azure-Mandanten-ID ein. Klicken Sie auf **Connection** (Verbindung).

    Nach der Auswahl von **Connection** wird der Datalert-Dienst bei Intune eingecheckt. Der Dienst bestätigt, dass keine bestehenden Datalert-Verbindungen vorhanden sind. Nach wenigen Augenblicken wird eine Microsoft-Anmeldeseite angezeigt, gefolgt von der Datalert-Azure-Authentifizierung.

6. Wählen Sie auf Microsoft-Authentifizierungsseite **Annehmen** aus.

    Sie werden zu einer Datalert-Seite mit einem **Dank** weitergeleitet, die nach einigen Augenblicken wieder geschlossen wird. Datalert überprüft die Verbindung und zeigt grüne Häkchen neben den überprüften Elementen an. Wenn bei der Überprüfung ein Fehler auftritt, wird eine Meldung in Rot angezeigt. Wenden Sie sich an den Datalert-Support, um Hilfe zu erhalten.

    Die folgende Abbildung zeigt die grünen Häkchen bei erfolgreich hergestellter Verbindung:

      ![Die Datalert-Seite bei erfolgreicher Verbindung](./media/telecom-expenses-monitor/tem-datalert-connection.png)

7. Stellen Sie unter **Datalert App / ADAL Consent** (Datalert-App/ADAL-Einwilligung) den Schalter auf **Ein**. Wählen Sie auf Microsoft-Authentifizierungsseite **Annehmen** aus.

    Sie werden zu einer Datalert-Seite mit einem **Dank** weitergeleitet, die nach einigen Augenblicken wieder geschlossen wird. Datalert überprüft die Verbindung und zeigt grüne Häkchen neben den überprüften Elementen an. Wenn bei der Überprüfung ein Fehler auftritt, wird eine Meldung in Rot angezeigt. Wenden Sie sich an den Datalert-Support, um Hilfe zu erhalten.

    Die folgende Abbildung zeigt die grünen Häkchen bei erfolgreich hergestellter Verbindung:

      ![Die Datalert-Seite bei erfolgreicher Verbindung](./media/telecom-expenses-monitor/tem-datalert-adal-consent.png)

8. Stellen Sie unter **MDM Profiles management (optional)** (MDM-Profilverwaltung [optional]) den Schalter auf **Ein**. Diese Einstellung ermöglicht es Datalert, die verfügbaren Profile in Intune zu lesen, um Sie bei der Einrichtung von Richtlinien zu unterstützen. 

    Wählen Sie auf Microsoft-Authentifizierungsseite **Annehmen** aus.

    Sie werden zu einer Datalert-Seite mit einem **Dank** weitergeleitet, die nach einigen Augenblicken wieder geschlossen wird. Datalert überprüft die Verbindung und zeigt grüne Häkchen neben den überprüften Elementen an. Wenn bei der Überprüfung ein Fehler auftritt, wird eine Meldung in Rot angezeigt. Wenden Sie sich an den Datalert-Support, um Hilfe zu erhalten.

    Die folgende Abbildung zeigt die grünen Häkchen bei erfolgreich hergestellter Verbindung:

   ![Die Datalert-Seite bei erfolgreicher Verbindung](./media/telecom-expenses-monitor/tem-datalert-mdm-profiles.png)

### <a name="step-2-confirm-telecom-expense-management-is-active-in-intune"></a>Schritt 2: Bestätigen, dass Telecom Expense Management in Intune aktiv ist

Nachdem Sie Schritt 1 ausgeführt haben, ist Ihre Verbindung automatisch aktiviert. In Intune wird **Aktiv** als Verbindungsstatus angezeigt. Um zu bestätigen, dass der Status tatsächlich „aktiv“ ist, führen Sie folgende Schritte aus:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.

2. Wählen Sie **Gerätekonfiguration** > **Telecom Expense Management** aus. Suchen Sie nach dem Verbindungsstatus **Aktiv**:

   ![Intune-Seite mit aktivem Datalert-Verbindungsstatus](./media/telecom-expenses-monitor/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-devices"></a>Schritt 3: Bereitstellen der Datalert-App auf Geräten

Um zu bestätigen, dass nur die Datennutzung von organisationseigenen Leitungen erfasst wird, gehen Sie folgendermaßen vor:

- Erstellen Sie Gerätekategorien in Intune.
- Verwenden Sie nur organisationseigene Smartphones als Ziel für die App.

Im folgenden Abschnitt werden die erforderlichen Schritte beschrieben.

#### <a name="create-device-categories-and-device-groups-mapped-to-your-categories"></a>Erstellen von Gerätekategorien und Gerätegruppen, die Ihren Kategorien zugeordnet sind

Erstellen Sie je nach Anforderungen Ihrer Organisation mindestens zwei Gerätekategorien, z. B. „Unternehmen“ und „Persönlich“. Erstellen Sie anschließend dynamische Gerätegruppen für alle Kategorien. Sie können je nach Bedarf weitere Kategorien für Ihre Organisation erstellen.

Schritte zum Erstellen von Gerätekategorien in Intune finden Sie unter [Zuweisen von Geräten zu Gruppen](../enrollment/device-group-mapping.md).

Diese Kategorien werden Benutzern während der Registrierung ([Registrieren von Android-Geräten](../enrollment/android-enroll.md)) angezeigt. Je nachdem, welche Kategorie Benutzer auswählen, wird das registrierte Gerät in die entsprechende Gerätegruppe eingeordnet.

  ![Screenshot des Bereichs „Richtlinie hinzufügen“](./media/telecom-expenses-monitor/tem-dynamic-membership-rules.png)

#### <a name="add-the-datalert-app-to-intune"></a>Hinzufügen der Datalert-App zu Intune

Mit den folgenden Schritten wird die Datalert-App hinzugefügt. Als Beispiel wird hier iOS verwendet. Unter [Hinzufügen von Apps](../apps/apps-add.md) und [Verwenden von Bereichsmarkierungen](../fundamentals/scope-tags.md) finden Sie detailliertere Informationen zu diesen Schritten.

1. Klicken Sie in **[Intune](https://go.microsoft.com/fwlink/?linkid=2090973)** auf **Client-Apps** > **Apps** > **Hinzufügen**.

2. Wählen Sie Ihren **App-Typ** aus. Für iOS wählen Sie beispielsweise **Store-App – iOS** aus.

3. Geben Sie unter **App Store durchsuchen** den Suchbegriff **Datalert** ein, um die Datalert-App zu suchen.

4. Markieren Sie die **Datalert-App**, und klicken Sie auf **Auswählen**:

   ![Hinzufügen der Datalert-App aus dem App Store zu Intune-Client-Apps](./media/telecom-expenses-monitor/tem-select-app-from-apple-app-store.png)

5. Geben Sie weitere Eigenschaften ein, z. B. Informationen zur App und Bereichsmarkierungen:

   ![Eingeben der App-Eigenschaften, einschließlich Namen, Beschreibung, Betriebssystemauswahl und weiterer Einstellungen für die App in Intune](./media/telecom-expenses-monitor/tem-steps-to-create-the-app.png)

6. Klicken Sie auf **OK** > **Hinzufügen**, um die Änderungen zu speichern. Die Datalert-App wird in der Liste angezeigt.

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Zuweisen der Datalert-App zur Unternehmensgerätegruppe

1. Wählen Sie unter **Client-Apps – Apps** die Datalert-App aus, die Sie im vorherigen Schritt hinzugefügt haben.

2. Klicken Sie auf **Zuweisungen** > **Gruppe hinzufügen**. Wählen Sie aus, wie die App zugewiesen werden soll. Unter [Zuweisen von Apps zu Gruppen in Intune](../apps/apps-deploy.md) finden Sie weitere Informationen zu diesen Einstellungen.

    In diesen Schritten legen Sie fest, ob die Installation der App für die Gruppe erforderlich oder optional ist. Das folgende Beispiel zeigt eine als erforderlich festgelegte Installation. Wenn die Datalert-App als erforderlich festgelegt wurde, müssen Benutzer diese nach dem Registrieren ihres Geräts installieren.

   ![Screenshot des Bereichs „Richtlinie hinzufügen“](./media/telecom-expenses-monitor/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-organization-phone-lines-to-the-datalert-console"></a>Schritt 4: Hinzufügen von organisationseigenen Telefonleitungen zur Datalert-Konsole

Die Intune- und Datalert-Dienste sind jetzt so konfiguriert, dass sie miteinander kommunizieren können. Als Nächstes fügen Sie der Datalert-Konsole organisationseigene kostenpflichtige Telefonleitungen hinzu. Sie geben auch Schwellenwerte und Aktionen für Verstöße gegen die zulässige Mobilfunk- oder Roamingnutzung an. Sie können der Datalert-Konsole unternehmenseigene kostenpflichtige Telefonleitungen manuell hinzufügen oder diese nach der Registrierung eines Geräts in Intune automatisch hinzufügen lassen.

Um diese Elemente festzulegen, wechseln Sie zur [Datalert-Einrichtung für Microsoft Intune auf der Datalert-Website](http://www.datalert.fr/microsoft-intune/intune-setup). Führen Sie auf der Registerkarte **Settings** (Einstellungen) die Schritte des Assistenten aus.

  ![Screenshot des Bereichs „Richtlinie hinzufügen“](./media/telecom-expenses-monitor/tem-add-phone-lines-to-datalert-console.png)

Der Datalert-Dienst ist jetzt aktiv. Der Dienst beginnt damit, die Datennutzung zu überwachen und auf Geräten, auf denen die konfigurierten Nutzungsgrenzwerte überschritten werden, Mobilfunk- und Roamingdaten zu deaktivieren.

## <a name="end-user-enrollment"></a>Endbenutzerregistrierung

Bei der Einrichtung der Endbenutzerfunktionen sind folgende Artikel hilfreich:

- [Registrieren Ihres iOS-Geräts im Telecom Expense Management](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
- [Registrieren Ihres Android-Gerät im Telecom Expense Management](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turn-off-the-datalert-service"></a>Deaktivieren des Datalert-Diensts

1. Wählen Sie in **[Intune](https://go.microsoft.com/fwlink/?linkid=2090973)** die Option **Gerätekonfiguration** > **Telecom Expense Management** aus.
2. Legen Sie **Aktivieren Sie Telecom Expense Management, und blockieren Sie mobile und/oder Roamingdaten auf Geräten, die die konfigurierten Nutzungskontingente überschritten haben** auf **Deaktivieren** fest.
3. **Speichern** Sie die Änderungen.

> [!IMPORTANT]
> Wenn Sie den Datalert-Dienst in Intune deaktivieren, geschieht Folgendes:
>
> - Alle Aktionen, die aufgrund vergangener Verstöße gegen die Nutzungsgrenzwerte auf Geräte angewendet werden, werden rückgängig gemacht.
> - Datenzugriffe und Roaming werden für Benutzer nicht mehr blockiert.
> - Intune empfängt die Signale vom Dienst weiterhin, ignoriert diese jedoch.

## <a name="next-steps"></a>Nächste Schritte

Die Nutzungsberichte sind in der Datalert-Verwaltungskonsole von Saaswedo verfügbar.
