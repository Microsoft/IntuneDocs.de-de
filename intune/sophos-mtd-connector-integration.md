---
title: Einrichten der Sophos Mobile-Integration in Intune
titleSuffix: Intune on Azure
description: Einrichten der Sophos Mobile-Lösung in Microsoft Intune, um den Zugriff mobiler Geräte auf Ihre Unternehmensressourcen zu steuern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: eeddbf39093210e640125db3be6ddd6bcad7d59b
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66045002"
---
# <a name="integrate-sophos-mobile-with-intune"></a>Integrieren von Sophos Mobile in Intune  

Führen Sie die folgenden Schritte aus, um die Sophos Mobile Threat Defense-Lösung in Intune zu integrieren.  

## <a name="before-you-begin"></a>Vorbereitung  

Stellen Sie vor der Integration von Sophos Mobile in Intune sicher, dass Sie über Folgendes verfügen:  
- Microsoft Intune-Abonnement  
- Azure Active Directory-Administratoranmeldeinformationen zum Erteilen folgender Berechtigungen:  
  - Anmelden und Lesen des Benutzerprofils  
  - Zugriff auf das Verzeichnis als angemeldeter Benutzer  
  - Lesen der Verzeichnisdaten  
  - Senden von Geräteinformationen an Intune  
- Administratoranmeldeinformationen für den Zugriff auf die Sophos Mobile-Verwaltungskonsole  


### <a name="sophos-mobile-app-authorization"></a>Sophos Mobile-App-Autorisierung  
  
Der Prozess zur Autorisierung der Sophos Mobile-App umfasst Folgendes:  
- Erteilen Sie dem Sophos Mobile-Dienst die Berechtigung, Informationen zum Integritätszustand des Geräts an Intune zu übertragen.  
- Sophos Mobile wird mit der Azure AD Enrollment Group-Mitgliedschaft synchronisiert, um die Datenbank des Geräts aufzufüllen.  
- Erteilen Sie der Sophos Mobile-Verwaltungskonsole die Berechtigung, Azure AD-SSO (Single Sign On) zu verwenden.  
- Erteilen Sie der Sophos Mobile-App die Berechtigung, die Azure AD-SSO-Anmeldung zu verwenden.  


## <a name="to-set-up-sophos-mobile-integration"></a>So richten Sie die Sophos Mobile-Integration ein:  

1. Melden Sie sich beim [Azure-Portal]( https://portal.azure.com/) an, wechseln Sie zu **Intune** > **Gerätekonformität** > **Mobile Threat Defense**, und wählen Sie **Hinzufügen** aus.  
2. Wählen Sie auf der Seite **Connector hinzufügen** in der Dropdownliste den Eintrag **Sophos** aus. Wählen Sie dann **Erstellen** aus.  
3. Wählen Sie den Link *Open the Sophos admin console (Die Sophos-Verwaltungskonsole öffnen)* aus.  
4. Melden Sie sich bei der [Sophos-Verwaltungskonsole](https://central.sophos.com/) mit Ihren Sophos-Anmeldeinformationen an.  
5. Wechseln Sie zu **Mobile** > **Einstellungen** > **Setup** > **Sophos-Setup**.  
6. Wählen Sie auf der Seite **Sophos-Setup** die Registerkarte **Intune MTD** aus.  
   ![Sophos-Setup](./media/sophos-mtd-connector-integration/sophos-setup.png) 
 
7. Wählen Sie **Binden** und dann **Ja** aus. Sophos stellt eine Verbindung mit Intune her und fordert Sie auf, sich bei Ihrem Intune-Abonnement anzumelden. 
8. Geben Sie im Microsoft Intune-Fenster „Authentifizierung“ Ihre Intune-Anmeldeinformationen ein, und akzeptieren Sie die Berechtigungsanforderung für **Sophos Mobile Threat Defense** mit *Ich stimme zu*.  
   ![Intune-Authentifizierung](./media/sophos-mtd-connector-integration/intune-authentication.png)

9. Wählen Sie auf der Seite **Sophos-Setup** die Option **Speichern** aus, um die Konfiguration für Intune abzuschließen:  
   ![Speichern von Sophos-Setup](./media/sophos-mtd-connector-integration/save-sophos-configuration.png)  

1. Wenn die Nachricht **Successful Integration** (Die Integration wurde erfolgreich abgeschlossen) angezeigt wird, ist die Integration abgeschlossen.  
1. In der Intune-Konsole steht Sophos nun zur Verfügung.  


## <a name="next-steps"></a>Nächste Schritte  
[Konfigurieren von Sophos-Client-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md)
