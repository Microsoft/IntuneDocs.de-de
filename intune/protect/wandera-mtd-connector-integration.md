---
title: Einrichten der Wandera Mobile Threat Protection-Integration mit Intune
titleSuffix: Intune on Azure
description: Einrichten der Wandera Mobile Threat Protection-Lösung in Microsoft Intune, um den Zugriff mobiler Geräte auf Ihre Unternehmensressourcen zu steuern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3bf8fd189e50a704e96fc24d0804c5c5d6f91bb4
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728220"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>Integrieren von Wandera Mobile Threat Protection in Intune  

Führen Sie die folgenden Schritte aus, um die Wandera Mobile Threat Defense-Lösung in Intune zu integrieren.  

## <a name="before-you-begin"></a>Vorbereitung  

Bevor Sie mit der Integration von Wandera in Intune beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
- Microsoft Intune-Abonnement  
- Azure Active Directory-Administratoranmeldeinformationen zum Erteilen folgender Berechtigungen:  
  - Anmelden und Lesen des Benutzerprofils  
  - Zugriff auf das Verzeichnis als angemeldeter Benutzer  
  - Lesen der Verzeichnisdaten  
  - Senden von Geräteinformationen an Intune  

- Wandera-Abonnement:
  - Ein oder mehrere Wandera-Konten, die für EMM Connect lizenziert sind  
  - Ein Konto mit Superadministratorberechtigungen in Wandera  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Autorisierung für die Wandera Mobile Threat Defense-App  

Der Autorisierungsprozess für die Wandera Mobile Threat Defense-App:  
- Erteilen Sie dem Dienst „Wandera Mobile Threat Defense“ die Berechtigung, Informationen zum Integritätszustand des Geräts an Intune zu übertragen.  
- Wandera wird mit der Mitgliedschaft in der Azure AD-Registrierungsgruppe synchronisiert, um die Datenbank des Geräts aufzufüllen.  
- Ermöglichen Sie dem Wandera RADAR -Verwaltungsportal das Verwenden von Azure AD SSO (einmaliges Anmelden).  
- Ermöglichen Sie der Wandera Mobile Threat Defense-App, sich über Azure AD SSO anzumelden.  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>Einrichten der Wandera Mobile Threat Defense-Integration  
Die Einrichtung von *EMM Connect* für Wandera erfordert einen einmaligen Konfigurationsprozess, den Sie sowohl in der Intune als auch in der Wandera-Konsole durchführen können. Der Konfigurationsvorgang dauert etwa 15 Minuten. Sie können die Konfiguration ohne Abstimmung mit einem technischen Kundenbetreuer oder Supportmitarbeiter von Wandera vornehmen.  

### <a name="enable-support-for-wandera-in-intune"></a>Aktivieren der Unterstützung für Wandera in Intune
1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an, wechseln Sie zu **Gerätekonformität** > **Mobile Threat Defense**, und klicken Sie auf **Hinzufügen**.

2. Wählen Sie auf der Seite **Connector hinzufügen** in der Dropdownliste den Eintrag **Wandera** aus. Wählen Sie dann **Erstellen** aus.  

3. Wählen Sie im Bereich „Mobile Threat Defense“ den **Wandera** MTD-Connector in der Liste der Connectors aus, um den Bereich *Connector bearbeiten* zu öffnen. Wählen Sie **Open the Wandera admin console** (Die Wandera-Verwaltungskonsole öffnen) aus, um [RADAR](https://radar.wandera.com/login), die Wandera-Verwaltungskonsole, zu öffnen und sich anzumelden. 

4. Wechseln Sie in der Wandera-Konsole zu **Settings** (Einstellungen) > **EMM Integration**, und wählen Sie die Registerkarte **EMM Connect** aus. Wählen Sie in der Dropdownliste *EMM Vendor* (EMM-Anbieter) *Microsoft Intune* aus.

   ![Auswählen von Intune](./media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

5. Klicken Sie auf **Grant permissions** (Berechtigungen erteilen), um eine Verbindung mit dem Intune-Portal zu öffnen. Melden Sie sich mit Ihren Anmeldeinformationen für Intune-Administratoren an, aktivieren Sie das Kontrollkästchen, und **akzeptieren** Sie dann die Berechtigungsanforderung.  

   ![Akzeptieren von Berechtigungen](./media/wandera-mtd-connector-integration/permissions.png) 

6. Wandera stellt die Verbindung her und kehrt zur Verwaltungskonsole RADAR zurück. Wiederholen Sie den Vorgang, um den Zugriff auf weitere Konfigurationen nach Bedarf zu **gewähren**.  

   ![Integrationen und Berechtigungen](./media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

7. Kopieren Sie in der RADAR-Konsole den Namen der Gruppe **SyncOnly**, die unter **EMM Label** angezeigt wird. Unter diesem Namen können Sie in Intune eine Gruppe für die Synchronisierung mit Wandera konfigurieren.

   ![Integrationen und Berechtigungen](./media/wandera-mtd-connector-integration/sync-group-name.png) 

8. Wechseln Sie zurück zur [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-Konsole, und bearbeiten Sie den Wandera MTD-Connector. Legen Sie die verfügbaren Optionen auf **Ein** fest, und **speichern** Sie die Konfiguration.  

   ![Aktivieren von Wandera](./media/wandera-mtd-connector-integration/enable-wandera.png) 

Intune und Wandera sind nun verbunden.  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>Konfigurieren der Wandera-Anwendungen und Synchronisierungsgruppe  
Um Wandera bereitzustellen, fügen Sie die mobilen Wandera-Apps für die von Ihnen verwendeten Plattformen (iOS und Android) zu Intune hinzu, und weisen Sie sie für die Synchronisierung der Gruppe *SyncOnly* zu. 

In den folgenden Abschnitten und Verfahren werden Sie durch diesen Prozess geleitet.

Um weitere Informationen über diesen Prozess von Wandera zu erhalten, melden Sie sich bei Wandera [RADAR](https://radar.wandera.com/login) an. Wechseln Sie zu **Settings** > **EMM Integration**, und wählen Sie die Registerkarte **App Push** und dann **Microsoft Intune** aus. Die Registerkarte „App Push“ wird mit Anweisungen aktualisiert, die speziell für Intune gelten.  

### <a name="add-the-wandera-apps"></a>Hinzufügen der Wandera-Apps  
Erstellen Sie Client-Apps in Intune, um die Wandera-App auf Android- und iOS-Geräten bereitzustellen. Unter [Hinzufügen von MTD-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md) finden Sie die für die Wandera-Apps spezifischen Verfahren und benutzerdefinierten Details.  

Nachdem Sie die Apps erstellt haben, kehren Sie hierher zurück, um die Synchronisierungsgruppe zu erstellen und die Apps zuzuweisen.  


### <a name="create-the-synchronization-group-and-assign-the-apps"></a>Erstellen der Synchronisierungsgruppe und Zuweisen der Apps

1. Ermitteln Sie in der Wandera RADAR-Konsole den Namen der Gruppe **SyncOnly**, die unter **EMM Label** angezeigt wird. Möglicherweise haben Sie diesen Namen in Schritt 7 gespeichert, während Sie [die Unterstützung für Wandera in Intune](#enable-support-for-wandera-in-intune) aktiviert haben. Verwenden Sie diesen Namen als Namen der Gruppe in Intune für die Wandera-Synchronisierung.  

2. Wechseln Sie in der Intune-Konsole zu **Gruppen**, und wählen Sie **Neue Gruppe** aus. Geben Sie Folgendes an, um die Synchronisierungsgruppe für die Verwendung durch Wandera zu konfigurieren:
   - **Gruppentyp**: **Sicherheit**
   - **Gruppenname**: Geben Sie den **SyncOnly**-Namen an, den Sie über die Wandera RADAR-Verwaltungskonsole abgerufen haben.

   ![Konfigurieren der Synchronisierungsgruppe](./media/wandera-mtd-connector-integration/configure-sync-group.png)

3. Wählen Sie **Mitglieder** aus, und weisen Sie Gruppen zu, die die Android- und iOS-Geräte enthalten, die Sie mit Wandera verwenden möchten.

4. Klicken Sie auf **Gerät**, um die Gruppe zu speichern.

Weitere Informationen finden Sie unter [Bereitstellen von Apps](../apps/apps-deploy.md).

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>Zuweisen der Wandera-Apps zur Synchronisierungsgruppe  
Wiederholen Sie das folgende Verfahren für die Wandera-App, die Sie für iOS und Android erstellt haben.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an. Wechseln Sie zu **Client-Apps** > **Apps**, und wählen Sie die Wandera-App aus.  

2. Klicken Sie auf **Zuweisungen** und dann auf **Gruppe hinzufügen**.  

3. Wählen Sie im Bereich **Gruppe hinzufügen** für *Zuweisungstyp* die Option *Erforderlich* aus.

4. Klicken Sie auf **Eingeschlossene Gruppen** und dann auf **Einzuschließende Gruppen auswählen**. Geben Sie die Gruppe an, die Sie für die Wandera-Synchronisierung erstellt haben, und klicken Sie dann auf **Auswählen** > **OK** > **OK**. Klicken Sie auf **Speichern**, um die Gruppenzuweisung abzuschließen.  
 

## <a name="next-steps"></a>Nächste Schritte  
Nachdem Sie die Integration konfiguriert haben, können Sie mit der Konfiguration von Richtlinien beginnen, den erweiterten bedingten Zugriff einrichten und Berichte in der Wandera-Verwaltungskonsole anzeigen. Weitere Informationen zum Verwalten und Konfigurieren von Wandera finden Sie im [Support Center Getting Started Guide](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started) in der Dokumentation zu Wandera.  
 