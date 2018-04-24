---
title: Einrichten Ihres Abonnements für Lookout
description: In diesem Thema werden Details zum Konfigurieren des Lookout-Schutzes vor Gerätebedrohungen erläutert.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: defd1373ac53d354ffb97a17ebdaeafe7ba460b2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-your-lookout-mobile-threat-defense-subscription"></a>Einrichten des Lookout Mobile Thread Defense-Abonnements

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Folgende Schritte sind erforderlich, um Lookout Mobile Threat Defense einzurichten:

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
| 1 | [Beobachten der Registrierung](#watching-enrollment) |


> [!IMPORTANT]
> Ein bestehender Lookout Mobile Endpoint Security-Mandant, der nicht bereits Ihrem Azure AD-Mandanten zugeordnet ist, kann nicht für die Integration in Azure AD und Intune verwendet werden. Wenden Sie sich an den Lookout-Support, um einen neuen Lookout Mobile Endpoint Security-Mandanten zu erstellen. Verwenden Sie den neuen Mandanten zur Integration Ihrer Azure AD-Benutzer.

## <a name="collect-azure-ad-information"></a>Sammeln von Azure AD-Informationen
Ihr Lookout Mobile Endpoint Security-Mandant wird zur Integration von Lookout in Intune Ihrem Azure AD-Abonnement zugeordnet. Um Ihr Abonnement für Lookout Mobile Threat Defense zu aktivieren, benötigt der Lookout-Support (enterprisesupport@lookout.com) folgende Informationen:  

* **Azure AD-Mandanten-ID**
* **Azure AD-Gruppenobjekt-ID** für einen **vollständigen** Lookout-Konsolenzugriff
* **Objekt-ID der Azure AD-Gruppe** für den **eingeschränkten** Zugriff auf die Lookout-Konsole (optional)

Führen Sie die folgenden Schritte aus, um die Informationen zusammenzustellen, die Sie an das Lookout-Supportteam übermitteln müssen.

1. Melden Sie sich beim [Azure AD-Verwaltungsportal](https://manage.windowsazure.com) an, und wählen Sie Ihr Abonnement aus. 
   ![Screenshot der Azure AD-Seite mit dem Namen des Mandanten](../media/mtp/aad_tenant_name.png)
2. Wenn Sie den Namen Ihres Abonnements auswählen, enthält die resultierende URL die Abonnement-ID.  Wenn Sie Probleme haben, Ihre Abonnement-ID zu finden, finden Sie in diesem [Microsoft-Supportartikel](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b) entsprechende Tipps. 
3. Suchen Sie Ihre Azure AD-Gruppen-ID. Die Lookout-Konsole unterstützt zwei Zugriffsebenen:  
   * **Vollzugriff:** Der Azure AD-Administrator kann eine Gruppe für Benutzer erstellen, die Vollzugriff erhalten sollen, und optional eine Gruppe für Benutzer erstellen, die eingeschränkten Zugriff erhalten sollen.  Nur die Benutzer in diesen Gruppen können sich dann bei der **Lookout-Konsole** anmelden.
   * **Eingeschränkter Zugriff:** Die Benutzer in dieser Gruppe haben keinen Zugriff auf verschiedene Module der Lookout-Konsole für die Konfiguration und Registrierung und schreibgeschützten Zugriff auf das Modul **Sicherheitsrichtlinie** der Lookout-Konsole.  

   Weitere Einzelheiten zu den Berechtigungen finden Sie in [ diesem Artikel](https://personal.support.lookout.com/hc/articles/114094105653) auf der Lookout-Website.

   Die **Gruppenobjekt-ID** befindet sich in der **Azure AD-Verwaltungskonsole** auf der Seite **Eigenschaften** der Gruppe.

   ![Screenshot der Eigenschaftenseite mit hervorgehobenem GroupID-Feld](../media/mtp/aad_group_object_id.png)

4. Nachdem Sie diese Informationen zusammengestellt haben, wenden Sie sich an den Lookout-Support (E-Mail-Adresse: enterprisesupport@lookout.com). Der Lookout-Support arbeitet mit Ihrem primären Kontakt zusammen, um Ihr Abonnement mithilfe der von Ihnen gesammelten Informationen zu integrieren und Ihr Lookout Enterprise-Konto zu erstellen.

## <a name="configure-your-subscription"></a>Konfigurieren des Abonnements
1. Nachdem das Lookout-Supportteam Ihr Lookout-Enterprise-Konto erstellt hat, wird von Lookout eine E-Mail an den primären Kontakt Ihres Unternehmens gesendet, die einen Link zur Anmelde-URL enthält: <https://aad.lookout.com/les?action=consent>.

2. Die erste Anmeldung bei der Lookout-Konsole muss mit einem Benutzerkonto mit der Azure AD-Rolle „Globaler Administrator“ erfolgen, um Ihren Azure AD-Mandanten zu registrieren. Bei späteren Anmeldungen ist diese Azure AD-Berechtigungsebene nicht erforderlich. Es wird eine Zustimmungsseite angezeigt. Wählen Sie **Akzeptieren** aus, um die Registrierung abzuschließen.

   ![Screenshot der Seite für die erstmalige Anmeldung der Lookout-Konsole](../media/mtp/lookout_mtp_initial_login.png) Sobald Sie akzeptiert und zugestimmt haben, werden Sie zur Lookout-Konsole weitergeleitet.

   Sollten Probleme mit der Anmeldung auftreten, finden Sie unter [Problembehandlung der Lookout-Integration mit Intune](/intune-classic/Troubleshoot/device-threat-protection-troubleshooting.md) weitere Informationen.

3. Wählen Sie in der [Lookout-Konsole](https://aad.lookout.com) im Modul **System** die Registerkarte **Connectors** und dann **Intune** aus.

   ![Screenshot der Lookout-Konsole mit geöffneter Registerkarte „Connectors“ und hervorgehobener Option „Intune“](../media/mtp/lookout_mtp_setup-intune-connector.png)

4. Wechseln Sie zu **Connectors** > **Verbindungseinstellungen**, und geben Sie die **Taktfrequenz** in Minuten an.

   ![Screenshot der Registerkarte „Verbindungseinstellungen“ mit konfigurierter Taktfrequenz](../media/mtp/lookout-mtp-connection-settings.png)

## <a name="configure-enrollment-groups"></a>Konfigurieren von Registrierungsgruppen
1. Es ist eine bewährte Methode, eine Azure AD-Sicherheitsgruppe im [Azure AD-Verwaltungsportal](https://manage.windowsazure.com) mit einer geringen Anzahl von Benutzern zu erstellen, um die Lookout-Integration zu testen.

   Alle identifizierten, von Lookout unterstützten und bei Intune registrierten Geräte von Benutzern in einer Registrierungsgruppe in Azure AD werden registriert und sind dann zur Aktivierung des Lookout-Schutzes vor Gerätebedrohungen berechtigt.

2. Wählen Sie in der [Lookout-Konsole](https://aad.lookout.com) im Modul **System** die Registerkarte **Connectors**, und wählen Sie **Registrierungsverwaltung**, um eine Gruppe von Benutzern zu definieren, deren Geräte bei Lookout registriert werden sollen. Fügen Sie die Azure AD-Sicherheitsgruppe **Anzeigename** für die Registrierung hinzu.

   ![Screenshot der Intune-Seite zur Connectorregistrierung](../media/mtp/lookout-mtp-enrollment.png)

   >[!IMPORTANT]
   > Beim **Anzeigenamen** muss die Groß- und Kleinschreibung beachtet werden, wie in den **Eigenschaften** der Sicherheitsgruppe im Azure-Portal dargestellt. Wie in der Abbildung unten gezeigt, wird der **Anzeigename** mit Groß- und Kleinbuchstaben geschrieben, der Titel dagegen nur mit Kleinbuchstaben. Verwenden Sie in der Lookout-Konsole für die Sicherheitsgruppe dieselbe Groß- und Kleinschreibung wie im **Anzeigenamen**.
   >![Screenshot des Azure-Portals, Azure Active Directory-Dienst, Seite „Eigenschaften“](../media/mtp/aad-group-display-name.png)

   Die bewährte Methode ist das Verwenden des Standardwerts (5 Minuten) für die Überprüfung auf neue Geräte.

   **Aktuelle Einschränkungen:**
   * Lookout kann keine Gruppenanzeigenamen überprüfen.  Stellen Sie sicher, dass das Feld **ANZEIGENAME** im Azure-Portal exakt mit der Azure AD-Sicherheitsgruppe übereinstimmt.
   * Das Erstellen von geschachtelten Gruppen wird nicht unterstützt.  In Lookout verwendete Azure AD-Sicherheitsgruppen dürfen nur Benutzer enthalten. Sie dürfen keine anderen Gruppen umfassen.

3. Wenn ein Benutzer nach dem Hinzufügen einer Gruppe die Lookout for Work-App auf einem unterstützten Gerät öffnet, wird das Gerät in Lookout aktiviert.

4. Wenn Sie mit den Ergebnissen zufrieden sind, erweitern Sie die Registrierung auf weitere Benutzergruppen.

## <a name="configure-state-sync"></a>Konfigurieren der Statussynchronisierung
Geben Sie in der Option **Statussynchronisierung** den Typ von Daten an, die an Intune gesendet werden sollen.  Damit die Lookout-Intune-Integration ordnungsgemäß funktioniert, sind sowohl der Gerätestatus als auch der Bedrohungsstatus erforderlich.  Diese sind standardmäßig aktiviert.

## <a name="configure-error-report-email-recipient-information"></a>Konfigurieren von Empfängerinformationen für Fehlerberichts-E-Mails
Geben Sie in der Option **Fehlerverwaltung** die E-Mail-Adresse ein, an die die Fehlerberichte gesendet werden sollen.

![Screenshot der Intune-Seite zur Connector-Fehlerverwaltung](../media/mtp/lookout-mtp-connector-error-notifications.png)

## <a name="configure-enrollment-settings"></a>Konfigurieren von Registrierungseinstellungen
Geben Sie im Modul **System** auf der Seite **Connectors** die Anzahl von Tagen an, bevor ein Gerät als getrennt bezeichnet werden kann.  Nicht verbundene Geräte gelten als nicht kompatibel und der Zugriff auf Unternehmensanwendungen wird ihnen auf Grundlage der Intune-Richtlinien für den bedingten Zugriff verwehrt. Sie können Werte zwischen 1 und 90 Tagen angeben.

![](../media/mtp/lookout-console-enrollment-settings.png)

## <a name="configure-email-notifications"></a>Konfigurieren von E-Mail-Benachrichtigungen
Wenn Sie bei Bedrohungen Warnungen per E-Mail erhalten möchten, melden Sie sich bei der [Lookout-Konsole](https://aad.lookout.com) mit dem Benutzerkonto an, das die Benachrichtigungen erhalten soll. Wählen Sie im Modul **System** auf der Registerkarte **Einstellungen** die Bedrohungsstufen aus, für die Benachrichtigungen gesendet werden sollen, und legen Sie sie auf **EIN** fest. Speichern Sie die Änderungen.

![Screenshot der Seite „Einstellungen“ mit angezeigtem Benutzerkonto](../media/mtp/lookout-mtp-email-notifications.png) Wenn Sie keine E-Mail-Benachrichtigungen mehr empfangen möchten, legen Sie die Benachrichtigungen auf **AUS** fest, und speichern Sie Ihre Änderungen.

### <a name="configure-threat-classification"></a>Konfigurieren der Bedrohungsklassifizierung
Lookout Mobile Threat Defense klassifiziert verschiedene Typen von Bedrohungen für mobile Geräte. Den [Lookout-Bedrohungsklassifizierungen](http://personal.support.lookout.com/hc/articles/114094130693) sind Standardrisikostufen zugeordnet. Sie können diese jederzeit gemäß den Anforderungen Ihres Unternehmens ändern.

![Screenshot der Richtlinienseite mit Bedrohung und Klassifikationen](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Risikostufen sind ein wichtiger Aspekt von Mobile Threat Defense, da die Intune-Integration die Gerätekompatibilität zur Laufzeit anhand dieser Risikostufen berechnet. Der Intune-Administrator legt in der Richtlinie eine Regel fest, um ein Gerät als nicht kompatibel zu identifizieren, wenn auf dem Gerät eine aktive Bedrohung mit der Mindeststufe **Hoch**, **Mittel** oder **Niedrig** erkannt wird. Die Richtlinie zur Bedrohungsklassifizierung von Lookout Mobile Threat Defense bildet die unmittelbare Grundlage zur Berechnung der Gerätekompatibilität in Intune.

## <a name="watching-enrollment"></a>Beobachten der Registrierung
Nachdem das Setup abgeschlossen wurde, beginnt Lookout Mobile Threat Defense mit der Abfrage von Azure AD nach Geräten, die den angegebenen Registrierungsgruppen entsprechen.  Informationen zu den registrierten Geräten finden Sie im Modul „Geräte“.  Der Ausgangsstatus für Geräte wird als „ausstehend“ angezeigt.  Dieser Status ändert sich, sobald die Lookout for Work-App installiert, geöffnet und auf dem Gerät aktiviert wird.  Details zur Übertragung der Lookout for Work-App per Push an die Geräte finden Sie im Thema [Konfigurieren und Bereitstellen von Lookout for Work-Apps](configure-deploy-lookout-for-work-app.md).
## <a name="next-steps"></a>Nächste Schritte
[Aktivieren der Lookout MTP-Verbindung mit Intune](/intune-classic/deploy-use/enable-lookout-mtd-connection)
