---
title: Einrichten eines TEM-Diensts (Telecom Expense Management)
titleSuffix: Microsoft Intune
description: Integrieren von Intune in den Saaswedo-TEM-Dienst (Telecom Expense Management)
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 031db83302dfef8b99fc83ab7975e233c3eeb799
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57396861"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Einrichten eines TEM-Diensts (Telecom Expense Management) in Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune ermöglicht es Ihnen, durch Datenverwendung auf firmeneigenen mobilen Geräten Telekommunikationsausgaben zu verwalten. Die [TEM-Lösung Datalert](http://datalert.biz/get-started) des Softwareentwicklers Saaswedo wurde in Intune integriert, um diese Funktion zu aktivieren. Bei Datalert handelt es sich um eine TEM-Software, über die Sie in Echtzeit die Nutzung von Telekommunikationsdaten verwalten können. Diese Software vermeidet aufwändige und unerwartete Daten- und Roamingüberschreitungen für Ihre mit Intune verwalteten Geräte.

Durch die Intune-Integration mit Datalert können Sie Datennutzungsgrenzwerte im In- und Ausland zentral festlegen, überwachen und erzwingen. Es werden automatisierte Warnungen ausgelöst, wenn die definierten Schwellenwerte überschritten werden. Sie können den Dienst so konfigurieren, dass verschiedene Aktionen für Einzelpersonen oder Gruppen von Endbenutzern ausgeführt werden (z.B. das Deaktivieren von Roaming oder das Überschreiten von Schwellenwerten). Berichte für Datennutzungs- und Überwachungsinformationen stehen in der Datalert-Verwaltungskonsole zur Verfügung.

Das folgende Diagramm zeigt, wie Intune mit Datalert integriert.

  ![Diagramm der Integration von Intune und Datalert](./media/tem-datalert-intune-solution-diagram.png)

Bevor Sie den Datalert-Dienst mit Intune verwenden können, müssen Sie in der Datalert-Konsole und in Intune Einstellungen konfigurieren. Die Verbindung muss für den Datalert-Dienst und für Intune aktiviert werden. Wenn die Datalert-Seite der Verbindung aktiviert ist, aber nicht die Intune-Seite, empfängt Intune die Kommunikation, ignoriert sie jedoch.

## <a name="supported-platforms"></a>Unterstützte Plattformen

- Samsung KNOX
- iOS 8.0 und höher

## <a name="prerequisites"></a>Voraussetzungen

- Ein Abonnement für Microsoft Intune und Zugriff auf das Azure-Portal.
- Ein Abonnement des TEM-Diensts Datalert

## <a name="list-of-telecom-expense-management-providers"></a>Liste von TEM-Anbietern

In Intune sind derzeit die folgenden TEM-Anbieter integriert:

[TEM-Dienst Saaswedo Datalert](http://www.datalert.biz/)

## <a name="deploy-the-intune-and-datalert-integrated-solution"></a>Bereitstellen von integrierten Intune- und Datalertlösungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie bereits ein TEM-Dienst-Abonnement für Intune und Datalert haben.

### <a name="step-1-connect-the-datalert-service-to-microsoft-intune"></a>Schritt 1: Verbinden des Datalert-Diensts mit Microsoft Intune

1. Melden Sie sich in der Datalert-Verwaltungskonsole mit Ihren Administratoranmeldeinformationen an.

2. Gehen Sie in der Datalert-Verwaltungskonsole zur Registerkarte **Einstellungen** und anschließend zu **MDM-Konfiguration**.

3. Klicken Sie unten auf der Seite auf **Unblock** (Zulassen), um Einstellungen auf der Seite zu ändern.

4. Klicken Sie im Bereich **Intune / Datalert Connection** (Intune/Datalert-Verbindung) für **Server MDM** (Server-MDM) auf **Microsoft Intune**.    

5. Geben Sie für die **Azure AD-Domäne** Ihre Azure-Mandanten-ID ein, und klicken Sie anschließend auf **Verbindung**.

    Wenn Sie auf **Verbindung** klicken, überprüft Datalert Intune, um sicherzustellen, dass nicht bereits Verbindungen zwischen Datalert und Intune bestehen. Nach wenigen Sekunden wird eine Microsoft-Anmeldeseite angezeigt, gefolgt von der Azure-Authentifizierung für Datalert.

6. Wählen Sie auf Microsoft-Authentifizierungsseite **Annehmen** aus. Sie werden zu einer Seite von Datalert mit dem Inhalt **Danke** weitergeleitet, die nach einigen Sekunden wieder geschlossen wird. Datalert überprüft die Verbindung und zeigt grüne Häkchen neben einer Liste von bereits überprüften Elementen an. Wenn die Überprüfung fehlschlägt, wird Ihnen in rot eine Meldung angezeigt. dann sollten Sie den Datalert-Support kontaktieren.

    Der folgende Screenshot zeigt die grünen Häkchen, die angezeigt werden, sobald die Verbindung erfolgreich aufgebaut wurde.

   ![Die Datalert-Seite bei erfolgreicher Verbindung](./media/tem-datalert-connection.png)

7. Aktivieren Sie den Abschnitt **Datalert App / ADAL Consent** (Datalert-App/ADAL-Einwilligung) über den Schalter **Ein**. Wählen Sie auf Microsoft-Authentifizierungsseite **Annehmen** aus. Sie werden zu einer Seite von Datalert mit dem Inhalt **Danke** weitergeleitet, die nach einigen Sekunden wieder geschlossen wird. Datalert überprüft die Verbindung und zeigt grüne Häkchen neben einer Liste von bereits überprüften Elementen an. Wenn die Überprüfung fehlschlägt, wird Ihnen in rot eine Meldung angezeigt. dann sollten Sie den Datalert-Support kontaktieren.    

    Der folgende Screenshot zeigt die grünen Häkchen, die angezeigt werden, sobald die Verbindung erfolgreich aufgebaut wurde.

   ![Die Datalert-Seite bei erfolgreicher Verbindung](./media/tem-datalert-adal-consent.png)

8. Aktivieren Sie den Abschnitt **MDM Profiles management (optional)** (Verwaltung von MDM-Profilen (optional)) über den Schalter **Ein**, damit Datalert die verfügbaren Profile in Intune lesen kann und Sie beim Einrichten von Richtlinien unterstützt. Wählen Sie auf Microsoft-Authentifizierungsseite **Annehmen** aus. Sie werden zu einer Seite von Datalert mit dem Inhalt **Danke** weitergeleitet, die nach einigen Sekunden wieder geschlossen wird. Datalert überprüft die Verbindung und zeigt grüne Häkchen neben einer Liste von bereits überprüften Elementen an. Wenn die Überprüfung fehlschlägt, wird Ihnen in rot eine Meldung angezeigt. dann sollten Sie den Datalert-Support kontaktieren.    

    Der folgende Screenshot zeigt die grünen Häkchen, die angezeigt werden, sobald die Verbindung erfolgreich aufgebaut wurde.

   ![Die Datalert-Seite bei erfolgreicher Verbindung](./media/tem-datalert-mdm-profiles.png)

### <a name="step-2-check-that-the-telecom-expense-management-feature-is-active-in-intune"></a>Schritt 2: Überprüfen, ob die TEM-Funktion in Intune aktiv ist

Nach Abschluss von Schritt 1 sollte die Verbindung automatisch aktiviert werden und der Verbindungsstatus **Aktiv** im Azure-Portal angezeigt werden. Diese Schritte zeigen Ihnen, wie Sie auf den Status **Aktiv** prüfen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.

3. Klicken Sie im Bereich **Intune** auf die Option **Gerätekonfiguration**.

4. Klicken Sie im Bereich **Gerätekonfiguration** auf die Option **Setup** > **Telecom Expense Management**.

   Suchen Sie nach dem **Aktiv**-Verbindungsstatus oben auf der Seite.

   ![Intune-Seite mit aktivem Datalert-Verbindungsstatus](./media/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-corporate-enrolled-devices"></a>Schritt 3: Bereitstellen der Datalert-App für in Unternehmen registrierte Geräte

Wenn Sie sicherstellen wollen, dass nur Informationen zur Datennutzung durch unternehmenseigene Leitungen gesammelt werden, müssen Sie die folgenden beiden Schritte ausführen:
- Erstellen Sie Gerätekategorien in Intune
- Richten Sie die Datalert-App nur auf unternehmenseigene Smartphones aus.

#### <a name="define-device-categories-and-device-groups-mapped-to-the-categories"></a>Definieren Sie Gerätekategorien und Gerätegruppen, die den Kategorien zugeordnet sind

Abhängig von den Bedürfnissen Ihrer Organisation müssen Sie mindestens zwei Gerätekategorien (z.B. Unternehmen und Privat) erstellen. Erstellen Sie anschließend dynamische Gerätegruppen für alle Kategorien. Sie können je nach Bedarf weitere Kategorien für Ihre Organisation erstellen.

Diese Kategorien werden Benutzern während der Registrierung angezeigt. Je nachdem, welche Kategorie Benutzer auswählen, wird das registrierte Gerät in die entsprechende Gerätegruppe verschoben. Schritte zum Erstellen von Gerätekategorien finden Sie unter [Zuweisen von Geräten zu Gruppen](device-group-mapping.md).

  ![Screenshot des Bereichs „Richtlinie hinzufügen“](./media/tem-dynamic-membership-rules.png)

#### <a name="create-the-datalert-app-in-intune"></a>Erstellen einer Datalert-App in Intune

Um die Datalert-App in Intune für jede Plattform zu erstellen, gehen Sie wie folgt vor. iOS wird in den folgenden Schritten als Beispiel verwendet.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) im Bereich **Intune** die Option **Client-Apps** aus.

2. Wählen Sie im Bereich **Client-Apps** die Option **Verwalten** > **Apps** aus.

3. Wählen Sie **Hinzufügen** aus, um eine App hinzuzufügen.

4. Wählen Sie den Anwendungstyp aus. Für iOS würden Sie zum Beispiel **iOS Store-App** auswählen.

5. In **App Store durchsuchen**, suchen Sie nach der Datalert-App durch Eingabe von **Datalert** im Suchfenster.

6. Wählen Sie die **Datalert**-App aus, und klicken Sie auf **Select** (Auswählen).

   ![Screenshot des Bereichs „Richtlinie hinzufügen“](./media/tem-select-app-from-apple-app-store.png)

7. Schließen Sie die verbleibenden Schritte zum Erstellen einer App für iOS ab.

   ![Screenshot des Bereichs „Richtlinie hinzufügen“](./media/tem-steps-to-create-the-app.png)

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Zuweisen der Datalert-App zur Unternehmensgerätegruppe

1. Wählen Sie im Bereich **Client-Apps – Apps** die Datalert-App für iOS aus, die Sie im vorherigen Schritt erstellt haben.

2. Klicken Sie im Bereich **Apps** auf **Verwalten** > **Zuweisungen**.

3. Klicken Sie auf **Gruppe hinzufügen**, und befolgen Sie die Schritte zum Auswählen der Unternehmensgerätegruppe.

4. Legen Sie fest, ob die Installation der App für die Gruppe erforderlich oder optional ist. Auf dem folgenden Beispiel-Screenshot wird die Installation als erforderlich angezeigt, was bedeutet, dass Benutzer die Datalert-App nach der Registrierung ihres Geräts installieren müssen.

   ![Screenshot des Bereichs „Richtlinie hinzufügen“](./media/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-corporate-paid-phone-lines-to-the-datalert-console"></a>Schritt 4: Hinzufügen von kostenpflichtigen Firmentelefonleitungen zur Datalert-Konsole

Sie haben nun die Intune- und Datalert-Dienste so konfiguriert, dass sie miteinander kommunizieren können. Sie müssen jetzt die kostenpflichtigen Firmentelefonleitungen zur Datalert-Konsole hinzufügen und Schwellenwerte und Aktionen für alle Funk- oder Roaming-Verwendungsverstöße definieren. Sie können vom Unternehmen bezahlte Telefonleitungen der Datalert-Konsole manuell hinzufügen oder diese nach der Registrierung des Geräts in Intune automatisch hinzufügen lassen.

Um diese Elemente festzulegen, gehen Sie zur Seite [Datalert setup for Microsoft Intune (Datalert-Setup für Microsoft Intune)](http://www.datalert.fr/microsoft-intune/intune-setup) (http://www.datalert.fr/microsoft-intune/intune-setup)), und führen Sie die Schritte im Setupassistenten unter der Registerkarte **Einstellungen** aus.

  ![Screenshot des Bereichs „Richtlinie hinzufügen“](./media/tem-add-phone-lines-to-datalert-console.png)


Der Datalert-Dienst ist jetzt aktiv, und es wird damit begonnen, die Datennutzung zu überwachen und auf Geräten, die die Verwendung der konfigurierten Grenzwerte überschreiten, Mobilfunk- und Roamingdaten zu deaktivieren.

## <a name="client-enrollment-experience"></a>Clientregistrierung
Beachten Sie Folgendes bei der Clientregistrierung:
-   [Registrieren Ihres iOS-Geräts im Telecom Expense Management](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
-   [Registrieren Ihres Android-Gerät im Telecom Expense Management](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turning-off-the-datalert-service"></a>Deaktivieren des Datalert-Diensts

Wenn Sie den Datalert-Dienst im Azure-Portal zu deaktivieren, geschieht Folgendes:

- Alle Aktionen, die aufgrund vergangener Verstöße gegen die Nutzungsgrenzwerte auf Geräte angewendet wurden, werden rückgängig gemacht.
- Datenzugriffe und Roaming werden für Benutzer nicht mehr blockiert.
- Intune weiterhin empfängt die Signale vom Dienst, ignoriert diese jedoch.

**So deaktivieren Sie den Dienst**

1. Klicken Sie im Bereich **Telecom Expense Management** im Azure-Portal auf die Option **Deaktivieren**.

2. Wählen Sie **Speichern** aus.

## <a name="viewing-data-usage-and-roaming-reports"></a>Anzeigen der Datennutzungs- und Roamingberichte

Zum aktuellen Zeitpunkt sind Nutzungsberichte nur in der Datalert-Verwaltungskonsole von Saaswedo verfügbar.

Die Anweisungen, denen Ihre Endbenutzer befolgen, um die Datalert-App zu installieren, werden bald verfügbar sein.
