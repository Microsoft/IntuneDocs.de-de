---
title: Einrichten Ihrer Lookout-Integration in Microsoft Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Lookout Mobile Endpoint Security als Mobile Threat Defense-Lösung in Intune integrieren, um den Zugriff von mobilen Geräten auf Ihre Unternehmensressourcen zu steuern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b61281b0e82bcb839efdc31726d398eea08c364f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502189"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>Einrichten der Lookout Mobile Endpoint Security-Integration in Intune
In einer Umgebung, die die [Voraussetzungen](lookout-mobile-threat-defense-connector.md#prerequisites) erfüllt, können Sie Lookout Mobile Endpoint Security in Intune integrieren. Die Informationen in diesem Artikel helfen Ihnen dabei, die Integration einzurichten und wichtige Einstellungen in Lookout für die Verwendung mit Intune zu konfigurieren.  

> [!IMPORTANT]
> Ein bestehender Lookout Mobile Endpoint Security-Mandant, der nicht bereits Ihrem Azure AD-Mandanten zugeordnet ist, kann nicht für die Integration in Azure AD und Intune verwendet werden. Wenden Sie sich an den Lookout-Support, um einen neuen Lookout Mobile Endpoint Security-Mandanten zu erstellen. Verwenden Sie den neuen Mandanten zur Integration Ihrer Azure AD-Benutzer.

## <a name="collect-azure-ad-information"></a>Sammeln von Azure AD-Informationen  
Zur Integration von Lookout in Intune ordnen Sie Ihren Lookout Mobile Endpoint Security-Mandanten zu Ihrem Azure Active Directory-Abonnement zu.

Um die Integration des Lookout Mobile Endpoint Security-Abonnements in Intune zu aktivieren, stellen Sie dem Lookout-Support (enterprisesupport@lookout.com) folgende Informationen bereit:  

- **Verzeichnis-ID des Azure AD-Mandanten**  

- **Azure AD-Gruppenobjekt-ID** für die Gruppe mit **Vollzugriff** auf die Konsole von Lookout Mobile Endpoint Security (MES).  
  Sie erstellen diese Benutzergruppe in Azure AD und fügen alle Benutzer hinzu, die *Vollzugriff* für die Anmeldung bei der **Lookout-Konsole** haben. Benutzer müssen Mitglieder dieser Gruppe oder einer optionalen Gruppe mit *eingeschränktem Zugriff* sein, um sich bei der Lookout-Konsole anzumelden. 

- **Azure AD-Gruppenobjekt-ID** für die Gruppe mit **eingeschränktem** Zugriff auf die Lookout MES-Konsole *(optionale Gruppe)* . 
  Sie erstellen diese optionale Benutzergruppe in Azure AD und fügen alle Benutzer hinzu, die keinen Zugriff auf verschiedene konfigurations- und registrierungsbezogene Module der Lookout-Konsole haben sollen. Stattdessen sollen diese Benutzer schreibgeschützten Zugriff auf das **Security Policy**-Modul der Lookout-Konsole haben. Benutzer müssen Mitglieder dieser optionalen Gruppe oder der erforderlichen Gruppe mit *Vollzugriff* sein, um sich bei der Lookout-Konsole anzumelden.

 > [!TIP] 
 > Weitere Details zu den Berechtigungen finden Sie in [diesem Artikel](https://personal.support.lookout.com/hc/articles/114094105653) auf der Lookout-Website.

### <a name="collect-information-from-azure-ad"></a>Erfassen von Informationen aus Azure AD 

1. Melden Sie sich mit einem globalen Administratorkonto beim [Azure-Portal](https://portal.azure.com) an.

2. Wechseln Sie zu **Azure Active Directory** > **Eigenschaften**, und suchen Sie Ihre **Verzeichnis-ID**. Verwenden Sie die Schaltfläche *Kopieren*, um die Verzeichnis-ID zu kopieren, und speichern Sie sie in einer Textdatei.

   ![Azure AD-Eigenschaften](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. Suchen Sie als Nächstes die Azure AD-Gruppen-ID für die Konten, die Sie zum Zuweisen des Zugriffs auf die Lookout-Konsole durch Azure AD-Benutzer verwenden möchten. Eine Gruppe erhält *Vollzugriff*, die zweite Gruppe mit *eingeschränktem Zugriff* ist optional. So rufen Sie die *Objekt-ID* für die Konten ab:  
   1. Wechseln Sie zu **Azure Active Directory** > **Gruppen**, um den Bereich *Gruppen – alle Gruppen* zu öffnen.  

   2. Wählen Sie die Gruppe aus, die Sie für den *Vollzugriff* erstellt haben, um den Bereich *Übersicht* für diese Gruppe zu öffnen.  

   3. Verwenden Sie die Schaltfläche *Kopieren*, um die Objekt-ID zu kopieren, und speichern Sie sie in einer Textdatei.  

   4. Wiederholen Sie den Vorgang für die Gruppe mit *eingeschränktem Zugriff*, falls Sie diese Gruppe verwenden.  

      ![Azure AD-Gruppenobjekt-ID](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   Nachdem Sie diese Informationen zusammengestellt haben, wenden Sie sich an den Lookout-Support (E-Mail-Adresse: enterprisesupport@lookout.com). Der Lookout-Support arbeitet mit Ihrem primären Kontakt zusammen, um Ihr Abonnement mithilfe der von Ihnen bereitgestellten Informationen einzubinden und Ihr Lookout Enterprise-Konto zu erstellen.  

## <a name="configure-your-lookout-subscription"></a>Konfigurieren Ihres Lookout-Abonnements  
Nachdem der Lookout-Support Ihr Lookout Enterprise-Konto erstellt hat, sendet Lookout eine E-Mail an den primären Kontakt Ihres Unternehmens, die einen Link zur Anmelde-URL enthält: https://aad.lookout.com/les?action=consent. 

### <a name="initial-sign-in"></a>Erste Anmeldung  
Bei der ersten Anmeldung bei der Lookout MES-Konsole wird eine Zustimmungsseite angezeigt (https://aad.lookout.com/les?action=consent). Hier muss sich ein globaler Azure AD-Administrator anmelden und auf **Accept** klicken. Bei nachfolgenden Anmeldungen muss der Benutzer nicht über diese Berechtigungsstufe in Azure AD verfügen. 

 Es wird eine Zustimmungsseite angezeigt. Wählen Sie **Akzeptieren** aus, um die Registrierung abzuschließen. 
   ![Screenshot der Seite für die erste Anmeldung bei der Lookout-Konsole](./media/lookout-mtd-connector-integration/lookout_mtp_initial_login.png)

Wenn Sie die Bedingungen akzeptiert haben, werden Sie zur Lookout-Konsole weitergeleitet.

Nach der ersten Anmeldung und der Zustimmung werden Benutzer, die sich über https://aad.lookout.com anmelden, zur MES-Konsole weitergeleitet. Wenn die Zustimmung noch nicht erteilt wurde, führen alle Anmeldeversuche zu einem Anmeldefehler.

### <a name="configure-the-intune-connector"></a>Konfigurieren des Intune-Connectors  
Beim folgenden Verfahren wird davon ausgegangen, dass Sie bereits eine Benutzergruppe in Azure AD zum Testen Ihrer Lookout-Bereitstellung erstellt haben. Am besten beginnen Sie mit einer kleinen Gruppe von Benutzern, damit Ihre Lookout- und Intune-Administratoren sich mit den Produktintegrationen vertraut machen können. Wenn die Administratoren die Integrationen kennen, können Sie die Registrierung auf weitere Benutzergruppen ausdehnen.

1. Melden Sie sich bei der [Lookout MES-Konsole](https://aad.lookout.com) an, wechseln Sie zu **System** > **Connectors**, und wählen Sie **Add Connector** (Connector hinzufügen) aus.  Klicken Sie auf **Intune**.

   ![Darstellung der Lookout-Konsole mit der Intune-Option auf der Registerkarte „Connectors“](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. Wählen Sie im Bereich *Microsoft Intune* die Option **Connection Settings** (Verbindungseinstellungen) aus, und geben Sie die **Heartbeat Frequency** (Taktfrequenz) in Minuten an. 

   ![Darstellung der Registerkarte „Verbindungseinstellungen“ mit konfigurierter Taktfrequenz](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. Wählen Sie **Enrollment Management** (Registrierungsverwaltung) aus, und geben Sie unter **Use the following Azure AD security groups to identify devices that should be enrolled in Lookout for Work** (Folgende Azure AD-Sicherheitsgruppen zum Identifizieren von Geräten verwenden, die in Lookout for Work registriert werden sollen) den *Group name* (Gruppenname) einer Azure AD-Gruppe an, die mit Lookout verwendet werden soll. Klicken Sie dann auf **Save changes** (Änderungen speichern).

    ![Screenshot der Intune-Seite zur Connectorregistrierung](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **Informationen zu den von Ihnen verwendeten Gruppen**:
   - Es wird empfohlen, mit einer Azure AD-Sicherheitsgruppe zu beginnen, die eine geringe Anzahl von Benutzern enthält, um die Lookout-Integration zunächst zu testen.
   - Beim **Gruppennamen** muss die Groß- und Kleinschreibung beachtet werden, wie in den **Eigenschaften** der Sicherheitsgruppe im Azure-Portal gezeigt.  
   - Die Gruppen, die Sie unter **Enrollment Management** angeben, definieren diejenigen Benutzer, deren Geräte mit Lookout registriert werden. Wenn sich ein Benutzer in einer Registrierungsgruppe befindet, werden seine in Azure AD befindlichen Geräte registriert und sind dann für die Aktivierung in Lookout MES berechtigt. Wenn ein Benutzer die *Lookout for Work*-Anwendung zum ersten Mal auf einem unterstützten Gerät öffnet, wird er aufgefordert, sie zu aktivieren.

4. Wählen Sie **State Sync** (Statussynchronisierung) aus, und stellen Sie sicher, dass sowohl *Device Status* (Gerätestatus) als auch *Threat Status* (Bedrohungsstatus) auf **On** (Ein) festgelegt sind.  Damit die Lookout-Intune-Integration ordnungsgemäß funktioniert, sind beide Optionen erforderlich.  

5. Klicken Sie auf **Error Management** (Fehlerverwaltung), geben Sie die E-Mail-Adresse an, an die Fehlerberichte gesendet werden sollen, und klicken Sie dann auf **Save changes** (Änderungen speichern).
 
   ![Screenshot der Intune-Seite zur Connector-Fehlerverwaltung](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. Klicken Sie auf **Create Connector** (Connector erstellen), um die Konfiguration des Connectors abzuschließen. Wenn Sie mit den Ergebnissen zufrieden sind, können Sie die Registrierung später auf weitere Benutzergruppen ausdehnen.

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>Konfigurieren von Intune zur Verwendung von Lookout als Mobile Threat Defense-Anbieter
Nach dem Konfigurieren von Lookout MES müssen Sie eine Verbindung zu Lookout in Intune einrichten.  

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.

2. Wechseln Sie zu **Gerätekonformität** > **Mobile Threat Defense**, und klicken Sie auf **Hinzufügen**.

3. Wählen Sie im Bereich *Connector hinzufügen* die Option **Lookout for Work** aus der Dropdownliste aus.  

4. Wählen Sie **Erstellen** aus. Nachdem der Connector die Verbindung mit Lookout MES hergestellt hat, wird die Option *Connectoreinstellungen* verfügbar.

5. Legen Sie **App-Synchronisierung für iOS-Geräte aktivieren** auf **Ein** fest. 

6. Klicken Sie auf **Speichern**, um die Konfiguration abzuschließen.  Intune und Lookout MES sind jetzt integriert und einsatzbereit.


## <a name="additional-settings-in-the-lookout-mes-console"></a>Zusätzliche Einstellungen in der Lookout MES-Konsole
Im Folgenden finden Sie einige zusätzliche Einstellungen, die Sie in der Lookout MES-Konsole konfigurieren können.  

### <a name="configure-enrollment-settings"></a>Konfigurieren von Registrierungseinstellungen
Wählen Sie in der Lookout MES-Konsole **System** > **Manage Enrollment** > **Enrollment settings** (System > Registrierung verwalten > Registrierungseinstellungen) aus.  

- Geben Sie unter **Disconnected Status** (Getrennter Status) die Anzahl von Tagen an, bevor ein nicht verbundenes Gerät als „getrennt“ markiert wird.  

  Nicht verbundene Geräte gelten als nicht kompatibel und der Zugriff auf Unternehmensanwendungen wird ihnen auf Grundlage der Intune-Richtlinien für den bedingten Zugriff verwehrt. Sie können Werte zwischen 1 und 90 Tagen angeben.

  ![Lookout-Registrierungseinstellungen im Systemmodul](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>Konfigurieren von E-Mail-Benachrichtigungen
Um bei Bedrohungen Warnungen per E-Mail zu erhalten, melden Sie sich bei der [Lookout MES-Konsole](https://aad.lookout.com) mit dem Benutzerkonto an, das die Benachrichtigungen erhalten soll.  

- Wechseln Sie zu **Preferences** (Voreinstellungen), und legen Sie die Benachrichtigungen, die Sie erhalten möchten, auf **ON** (Ein) fest. Klicken Sie anschließend auf **Save**, um Ihre Änderungen zu speichern.  

- Wenn Sie keine E-Mail-Benachrichtigungen mehr erhalten möchten, legen Sie die Benachrichtigungen auf **OFF** (AUS) fest, und speichern Sie Ihre Änderungen.

  ![Screenshot der Seite mit Voreinstellungen mit angezeigtem Benutzerkonto](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)



## <a name="configure-threat-classifications"></a>Konfigurieren von Bedrohungsklassifizierungen  
Lookout Mobile Endpoint Security klassifiziert verschiedene Arten von Bedrohungen für mobile Geräte. Den Lookout-Bedrohungsklassifizierungen sind Standardrisikostufen zugeordnet. Diese Risikostufen können jederzeit entsprechend den Anforderungen Ihres Unternehmens geändert werden.

Informationen zu den Klassifizierungen von Bedrohungsstufen und dazu, wie die entsprechenden Risikostufen verwaltet werden, finden Sie unter [Lookout Threat Reference](https://enterprise.support.lookout.com/hc/articles/360011812974) (Referenz zu Bedrohungen in Lookout).

>[!IMPORTANT]
> Risikostufen sind ein wichtiger Aspekt von Mobile Endpoint Security, da die Intune-Integration die Gerätekonformität zur Laufzeit anhand dieser Risikostufen berechnet.  
> 
> Der Intune-Administrator legt in der Richtlinie eine Regel fest, um ein Gerät als nicht kompatibel zu identifizieren, wenn auf dem Gerät eine aktive Bedrohung mit der Mindeststufe **Hoch**, **Mittel** oder **Niedrig** erkannt wird. Die Richtlinie zur Bedrohungsklassifizierung von Lookout Mobile Endpoint Security bildet die unmittelbare Grundlage zur Berechnung der Gerätekonformität in Intune.  

## <a name="monitor-enrollment"></a>Überwachen der Registrierung
Nachdem das Setup abgeschlossen wurde, beginnt Lookout Mobile Endpoint Security mit der Abfrage von Azure AD nach Geräten, die den angegebenen Registrierungsgruppen entsprechen.  Informationen zu registrierten Geräten finden Sie in der Lookout MES-Konsole unter **Devices** (Geräte).  
- Der Ausgangsstatus für Geräte ist *pending* (ausstehend).  
- Der Gerätestatus wird aktualisiert, nachdem die *Lookout for Work*-App auf dem Gerät installiert, geöffnet und aktiviert wurde.

Details zur Bereitstellung der *Lookout for Work*-App auf einem Gerät finden Sie unter [Hinzufügen von Lookout for Work-Apps mit Intune](mtd-apps-ios-app-configuration-policy-add-assign.md).

## <a name="next-steps"></a>Nächste Schritte

[Einrichten von Lookout-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md)
