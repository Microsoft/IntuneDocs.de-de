---
title: Einrichten Ihrer Lookout-Integration in Microsoft Intune
titlesuffix: ''
description: Informationen zum Integrieren von Lookout Mobile Threat Defense in Intune, um den Zugriff von mobilen Geräten auf Ihre Unternehmensressourcen zu steuern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fe8a55153ccc2b28c23ec2f32a4285d20afaaf6a
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232178"
---
# <a name="set-up-your-lookout-mobile-threat-defense-integration-with-intune"></a>Einrichten Ihrer Lookout Mobile Threat Defense-Integration mit Intune

Folgende Schritte sind erforderlich, um ein Lookout Mobile Threat Defense-Abonnement einzurichten:

| #        |Schritt  |
| ------------- |:-------------|
| 1 | [Sammeln von Azure AD-Informationen](#collect-azure-ad-information) |
| 2 | [Konfigurieren des Abonnements](#configure-your-subscription) |
| 3 | [Konfigurieren von Registrierungsgruppen](#configure-enrollment-groups) |
| 4 | [Konfigurieren der Statussynchronisierung](#configure-state-sync) |
| 5 | [Konfigurieren von Empfängerinformationen für Fehlerberichts-E-Mails](#configure-error-report-email-recipient-information) |
| 6 | [Konfigurieren von Registrierungseinstellungen](#configure-enrollment-settings) |
| 7 | [Konfigurieren von E-Mail-Benachrichtigungen](#configure-email-notifications) |
| 8 | [Konfigurieren der Bedrohungsklassifizierung](#configure-threat-classification) |
| 9 | [Beobachten der Registrierung](#watching-enrollment) |

> [!IMPORTANT]
> Ein bestehender Lookout Mobile Endpoint Security-Mandant, der nicht bereits Ihrem Azure AD-Mandanten zugeordnet ist, kann nicht für die Integration in Azure AD und Intune verwendet werden. Wenden Sie sich an den Lookout-Support, um einen neuen Lookout Mobile Endpoint Security-Mandanten zu erstellen. Verwenden Sie den neuen Mandanten zur Integration Ihrer Azure AD-Benutzer.

## <a name="collect-azure-ad-information"></a>Sammeln von Azure AD-Informationen
Ihr Lookout Mobile Endpoint Security-Mandant wird zur Integration von Lookout in Intune Ihrem Azure AD-Abonnement zugeordnet. Um Ihr Abonnement für Lookout Mobile Threat Defense zu aktivieren, benötigt der Lookout-Support (enterprisesupport@lookout.com) folgende Informationen:

* **Azure AD-Mandanten-ID**
* **Azure AD-Gruppenobjekt-ID** für einen **vollständigen** Lookout-Konsolenzugriff
* **Objekt-ID der Azure AD-Gruppe** für den **eingeschränkten** Zugriff auf die Lookout-Konsole (optional)

Führen Sie die folgenden Schritte aus, um die Informationen zusammenzustellen, die Sie an das Lookout-Supportteam übermitteln müssen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an, und wählen Sie Ihr Abonnement aus. 

2. Wenn Sie den Namen Ihres Abonnements auswählen, enthält die resultierende URL die Abonnement-ID.  Wenn Sie Probleme haben, Ihre Abonnement-ID zu finden, finden Sie in diesem [Microsoft-Supportartikel](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b) entsprechende Tipps.

3. Suchen Sie Ihre Azure AD-Gruppen-ID. Die Lookout-Konsole unterstützt zwei Zugriffsebenen:  
   * **Vollzugriff:** Der Azure AD-Administrator kann eine Gruppe für Benutzer erstellen, die Vollzugriff erhalten sollen, und optional eine Gruppe für Benutzer erstellen, die eingeschränkten Zugriff erhalten sollen.  Nur die Benutzer in diesen Gruppen können sich dann bei der **Lookout-Konsole** anmelden.
   * **Eingeschränkter Zugriff:** Die Benutzer in dieser Gruppe haben keinen Zugriff auf verschiedene Module der Lookout-Konsole für die Konfiguration und Registrierung und schreibgeschützten Zugriff auf das Modul **Sicherheitsrichtlinie** der Lookout-Konsole.  

     > [!TIP] 
     > Weitere Details zu den Berechtigungen finden Sie in [diesem Artikel](https://personal.support.lookout.com/hc/articles/114094105653) auf der Lookout-Website.

     > [!NOTE] 
     > Die **Gruppenobjekt-ID** befindet sich im **Azure AD-Verwaltungsportal** auf der Seite **Eigenschaften** der Gruppe.

4. Nachdem Sie diese Informationen zusammengestellt haben, wenden Sie sich an den Lookout-Support (E-Mail-Adresse: enterprisesupport@lookout.com). Der Lookout-Support arbeitet mit Ihrem primären Kontakt zusammen, um Ihr Abonnement mithilfe der von Ihnen gesammelten Informationen zu integrieren und Ihr Lookout Enterprise-Konto zu erstellen.

## <a name="configure-your-subscription"></a>Konfigurieren des Abonnements

1. Nachdem das Lookout-Supportteam Ihr Lookout-Enterprise-Konto erstellt hat, wird von Lookout eine E-Mail an den primären Kontakt Ihres Unternehmens gesendet, die einen Link zur Anmelde-URL enthält: <https://aad.lookout.com/les?action=consent>.

2. Die erste Anmeldung bei der Lookout-Konsole muss mit einem Benutzerkonto mit der Azure AD-Rolle „Globaler Administrator“ erfolgen, um Ihren Azure AD-Mandanten zu registrieren. Bei späteren Anmeldungen ist diese Azure AD-Berechtigungsebene nicht erforderlich. Es wird eine Zustimmungsseite angezeigt. Wählen Sie **Akzeptieren** aus, um die Registrierung abzuschließen. Nachdem Sie die Bedingungen akzeptiert und ihnen zustimmt haben, werden Sie an die Lookout-Konsole weitergeleitet.

   ![Screenshot der Seite für die erste Anmeldung an der Lookout-Konsole](./media/lookout_mtp_initial_login.png)

3. Wählen Sie in der [Lookout-Konsole](https://aad.lookout.com) im Modul **System** die Registerkarte **Connectors** und dann **Intune** aus.

   ![Screenshot der Lookout-Konsole mit geöffneter Registerkarte „Connectors“ und hervorgehobener Option „Intune“](./media/lookout_mtp_setup-intune-connector.png)

4. Wechseln Sie zu **Connectors** > **Verbindungseinstellungen**, und geben Sie die **Taktfrequenz** in Minuten an.

   ![Screenshot der Registerkarte „Verbindungseinstellungen“ mit konfigurierter Taktfrequenz](./media/lookout-mtp-connection-settings.png)

## <a name="configure-enrollment-groups"></a>Konfigurieren von Registrierungsgruppen
1. Es ist eine bewährte Methode, eine Azure AD-Sicherheitsgruppe im [Azure AD-Verwaltungsportal](https://manage.windowsazure.com) mit einer geringen Anzahl von Benutzern zu erstellen, um die Lookout-Integration zu testen.

    > [!NOTE] 
    > Alle identifizierten, von Lookout unterstützten und bei Intune registrierten Geräte von Benutzern in einer Registrierungsgruppe in Azure AD werden registriert und sind dann zur Aktivierung in der Lookout MTD-Konsole berechtigt.

2. Klicken Sie in der [Lookout-Konsole](https://aad.lookout.com) im Modul **System** auf die Registerkarte **Connectors**, und wählen Sie **Registrierungsverwaltung** aus, um eine Gruppe von Benutzern zu definieren, deren Geräte mit Lookout registriert werden sollen. Fügen Sie die Azure AD-Sicherheitsgruppe **Anzeigename** für die Registrierung hinzu.

    ![Screenshot der Intune-Seite zur Connectorregistrierung](./media/lookout-mtp-enrollment.png)

    >[!IMPORTANT]
    > Beim **Anzeigenamen** muss die Groß- und Kleinschreibung beachtet werden, wie in den **Eigenschaften** der Sicherheitsgruppe im Azure-Portal dargestellt. Der **Anzeigename** der Sicherheitsgruppe wird wie in der folgenden Abbildung mit gemischter Groß-/Kleinschreibung angegeben, während der Titel kleingeschrieben wird. Verwenden Sie in der Lookout-Konsole für die Sicherheitsgruppe dieselbe Groß- und Kleinschreibung wie im **Anzeigenamen**.
    >![Screenshot des Azure-Portals, Azure Active Directory-Dienst, Seite „Eigenschaften“](./media/aad-group-display-name.png)

    >[!NOTE] 
    >Die bewährte Methode ist das Verwenden des Standardwerts (5 Minuten) für die Überprüfung auf neue Geräte. Aktuelle Einschränkungen: **Lookout kann Anzeigenamen von Gruppen nicht überprüfen:** Stellen Sie sicher, dass das Feld **ANZEIGENAME** im Azure-Portal genau mit der Azure AD-Sicherheitsgruppe übereinstimmt. **Das Erstellen geschachtelter Gruppen wird nicht unterstützt:** In Lookout verwendete Azure AD-Sicherheitsgruppen dürfen nur Benutzer enthalten. Sie dürfen keine anderen Gruppen umfassen.

3.  Wenn ein Benutzer nach dem Hinzufügen einer Gruppe die Lookout for Work-App auf einem unterstützten Gerät öffnet, wird das Gerät in Lookout aktiviert.

4.  Wenn Sie mit den Ergebnissen zufrieden sind, erweitern Sie die Registrierung auf weitere Benutzergruppen.

## <a name="configure-state-sync"></a>Konfigurieren der Statussynchronisierung
Geben Sie in der Option **Statussynchronisierung** den Typ von Daten an, die an Intune gesendet werden sollen.  Damit die Lookout-Intune-Integration ordnungsgemäß funktioniert, sind sowohl der Gerätestatus als auch der Bedrohungsstatus erforderlich. Standardmäßig sind diese Einstellungen aktiviert.

## <a name="configure-error-report-email-recipient-information"></a>Konfigurieren von Empfängerinformationen für Fehlerberichts-E-Mails
Geben Sie in der Option **Fehlerverwaltung** die E-Mail-Adresse ein, an die die Fehlerberichte gesendet werden sollen.

![Screenshot der Intune-Seite zur Connector-Fehlerverwaltung](./media/lookout-mtp-connector-error-notifications.png)

## <a name="configure-enrollment-settings"></a>Konfigurieren von Registrierungseinstellungen
Geben Sie im Modul **System** auf der Seite **Connectors** die Anzahl von Tagen an, bevor ein Gerät als getrennt bezeichnet werden kann.  Nicht verbundene Geräte gelten als nicht kompatibel und der Zugriff auf Unternehmensanwendungen wird ihnen auf Grundlage der Intune-Richtlinien für den bedingten Zugriff verwehrt. Sie können Werte zwischen 1 und 90 Tagen angeben.

![Lookout-Registrierungseinstellungen](./media/lookout-console-enrollment-settings.png)

## <a name="configure-email-notifications"></a>Konfigurieren von E-Mail-Benachrichtigungen
Wenn Sie bei Bedrohungen Warnungen per E-Mail erhalten möchten, melden Sie sich bei der [Lookout-Konsole](https://aad.lookout.com) mit dem Benutzerkonto an, das die Benachrichtigungen erhalten soll. Wählen Sie im Modul **System** auf der Registerkarte **Einstellungen** die Bedrohungsstufen aus, für die Benachrichtigungen gesendet werden sollen, und legen Sie sie auf **EIN** fest. Speichern Sie die Änderungen.

![Screenshot der Seite „Einstellungen“ mit angezeigtem Benutzerkonto](./media/lookout-mtp-email-notifications.png) Wenn Sie keine E-Mail-Benachrichtigungen mehr empfangen möchten, legen Sie die Benachrichtigungen auf **AUS** fest, und speichern Sie Ihre Änderungen.

### <a name="configure-threat-classification"></a>Konfigurieren der Bedrohungsklassifizierung
Lookout Mobile Threat Defense klassifiziert verschiedene Typen von Bedrohungen für mobile Geräte. Den [Lookout-Bedrohungsklassifizierungen](http://personal.support.lookout.com/hc/articles/114094130693) sind Standardrisikostufen zugeordnet. Sie können diese jederzeit gemäß den Anforderungen Ihres Unternehmens ändern.

![Screenshot der Richtlinienseite mit Bedrohung und Klassifikationen](./media/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Risikostufen sind ein wichtiger Aspekt von Mobile Threat Defense, da die Intune-Integration die Gerätekompatibilität zur Laufzeit anhand dieser Risikostufen berechnet. Der Intune-Administrator legt in der Richtlinie eine Regel fest, um ein Gerät als nicht kompatibel zu identifizieren, wenn auf dem Gerät eine aktive Bedrohung mit der Mindeststufe **Hoch**, **Mittel** oder **Niedrig** erkannt wird. Die Richtlinie zur Bedrohungsklassifizierung von Lookout Mobile Threat Defense bildet die unmittelbare Grundlage zur Berechnung der Gerätekompatibilität in Intune.

## <a name="watching-enrollment"></a>Beobachten der Registrierung
Nachdem das Setup abgeschlossen wurde, beginnt Lookout Mobile Threat Defense mit der Abfrage von Azure AD nach Geräten, die den angegebenen Registrierungsgruppen entsprechen.  Informationen zu den registrierten Geräten finden Sie im Modul „Geräte“.  Der Ausgangsstatus für Geräte wird als „ausstehend“ angezeigt.  Der Gerätestatus ändert sich, sobald die Lookout for Work-App auf dem Gerät installiert, geöffnet und aktiviert wurde.  Details zur Übertragung der Lookout for Work-App per Push an die Geräte finden Sie unter [Hinzufügen und Zuweisen von Mobile Threat Defense-Apps (MTD) mit Intune](mtd-apps-ios-app-configuration-policy-add-assign.md).

## <a name="next-steps"></a>Nächste Schritte

[Einrichten von Lookout-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md)
