---
title: Festlegen der Autorität für die Verwaltung mobiler Geräte
titlesuffix: Microsoft Intune
description: Festlegen der Autorität für die Verwaltung mobiler Geräte in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 889e298d3d04429c1b9be2ee70519d68063953ab
ms.sourcegitcommit: 0dc977795ff80abb6a3b989ca633cba410f06c64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54006300"
---
# <a name="set-the-mobile-device-management-authority"></a>Festlegen der Autorität für die Verwaltung mobiler Geräte

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Die Einstellung für die Autorität für die Verwaltung mobiler Geräte (Mobile Device Management, MDM) bestimmt, wie Sie Ihre Geräte verwalten. Als IT-Administrator müssen Sie eine MDM-Autorität festlegen, damit Benutzer Geräte zur Verwaltung registrieren können.

Die möglichen Konfigurationen sind Folgende:

- **Intune Standalone:** Ausschließliche Verwaltung in der Cloud, die Sie mithilfe des Azure-Portals konfigurieren. Ihnen stehen alle Funktionen von Intune zur Verfügung. [Legen Sie die MDM-Autorität in der Intune-Konsole fest](#set-mdm-authority-to-intune).

- **Intune Hybrid:** Integration der Intune-Cloudlösung in System Center Configuration Manager. Sie konfigurieren Intune mithilfe der Configuration Manager-Konsole. [Legen Sie die MDM-Autorität im Configuration Manager fest](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription). 

    > [!Important]
    >Das Onboarding neuer MDM-Kunden (hybrid) wird in einem kommenden Release deaktiviert. Weitere Informationen finden Sie im Blogbeitrag [Move from Hybrid Mobile Device Management to Intune on Azure (Wechsel von der hybriden Verwaltung mobiler Geräte zu Intune unter Azure)](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150).

- **Verwaltung mobiler Geräte für Office 365:** Integration von Office 365 in die Intune-Cloudlösung. Sie konfigurieren Intune über das Office 365 Admin Center. Ihnen steht eine Teilmenge der Funktionen von Intune Standalone zur Verfügung. Legen Sie die MDM-Autorität im Office 365 Admin Center fest.

> [!IMPORTANT]
> In Configuration Manager, Version 1610 oder höher, und Microsoft Intune, Version 1705, können Sie Ihre MDM-Autorität ändern, ohne sich an den Microsoft Support wenden und die Aufhebung der Registrierung sowie die erneute Registrierung vorhandener verwalteten Geräte durchführen zu müssen. Ausführliche Informationen finden Sie unter [Vorbereiten der Umstellung der MDM-Autorität auf Configuration Manager](mdm-authority-set.md#prepare-to-change-the-mdm-authority-to-configuration-manager).

## <a name="set-mdm-authority-to-intune"></a>Festlegen der MDM-Autorität in Intune

Führen Sie folgende Schritte durch, wenn Sie die MDM-Autorität noch nicht festgelegt haben. Weitere Informationen zum Wechsel von einer MDM-Autorität zu einer anderen finden Sie im Abschnitt zum [Ändern der MDM-Autorität](#prepare-to-change-the-mdm-authority-to-configuration-manager).

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie den orangefarbenen Banner aus, um die Einstellung **Autorität für die Verwaltung mobiler Geräte** zu öffnen. Der orangefarbene Banner wird nur angezeigt, wenn Sie die MDM-Autorität noch nicht festgelegt haben.
4. Wählen Sie unter **Autorität für die Verwaltung mobiler Geräte** Ihre MDM-Autorität aus den folgenden Optionen aus:
   - **Intune-MDM-Autorität**
   - **Configuration Manager-MDM-Autorität**
   - **Keine**

   ![Screenshot vom Intune-Bildschirm zum Festlegen der Autorität für die mobile Geräteverwaltung](media/set-mdm-auth.png)

   Eine Meldung zeigt an, dass Sie die MDM-Autorität erfolgreich auf Intune festgelegt haben.

### <a name="workflow-of-intune-administration-ui"></a>Workflow der Intune-Verwaltungsbenutzeroberfläche
Wenn die Verwaltung von Android- oder Apple-Geräten aktiviert ist, sendet Intune Geräte- und Benutzerinformationen zur Integration mit diesen Drittanbieterdiensten, um die jeweiligen Geräte zu verwalten.

Szenarios, die eine Zustimmung zur Datenfreigabe hinzufügen, werden unter den folgenden Bedingungen eingeschlossen:
- Sie aktivieren Android-Arbeitsprofile.
- Apple-MDM-Push-Zertifikate werden aktiviert und hochgeladen.
- Einer der Apple-Dienste wie das Programm zur Geräteregistrierung, School Manager oder Volume Purchase Program wird aktiviert.

In jedem Fall muss die Zustimmung erteilt werden, wenn ein Verwaltungsdienst für mobile Geräte ausgeführt wird. Beispielsweise zum Bestätigen, dass ein IT-Administrator Google- oder Apple-Geräte zur Registrierung autorisiert hat. An den folgenden Speicherorten finden Sie die Dokumentation zur Frage, welche Informationen freigegeben werden, wenn die neuen Workflows live sind:
- [Von Intune an Google gesendete Daten](https://aka.ms/Data-intune-sends-to-google)
- [Von Intune an Apple gesendete Daten](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>Wichtige Überlegungen
Nachdem Sie auf die neue MDM-Autorität umgestellt haben, gibt es wahrscheinlich eine Übergangszeit (bis zu acht Stunden), bevor das Gerät eingecheckt und mit dem Dienst synchronisiert wird. Sie müssen die Einstellungen in der neuen MDM-Autorität (hybrid) konfigurieren, um sicherzustellen, dass registrierte Geräte nach der Umstellung weiterhin verwaltet und geschützt werden. 
- Geräte müssen nach der Umstellung eine Verbindung mit dem Dienst herstellen, damit die Einstellungen der neuen MDM-Autorität (Intune standalone) die vorhandenen Einstellungen auf dem Gerät ersetzen.
- Nach dem Ändern der MDM-Autorität verbleiben einige der grundlegenden Einstellungen (z.B. Profile) aus der vorherigen MDM-Autorität (Intune standalone) für bis zu sieben Tage oder bis zur ersten Verbindung des Geräts mit dem Dienst auf dem Gerät. Es wird empfohlen, dass Sie Apps und Einstellungen (Richtlinien, Profile, Apps usw.) so bald wie möglich in der neuen MDM-Autorität (hybrid) konfigurieren und die Einstellung den Benutzergruppen bereitstellen, die Benutzer mit gegenwärtig registrierten Geräten enthalten. Sobald ein Gerät nach der Umstellung der MDM-Autorität eine Verbindung mit dem Dienst herstellt, werden die neuen Einstellungen der neuen MDM-Autorität übertragen, und Lücken bei Verwaltung und Schutz werden verhindert.
- Wenn in Intune und Configuration Manager die gleichen Gerätekategorien vorhanden sind, werden Zuweisungen von Gerätekategorien für Geräte beim Wechsel zur neuen MDM-Autorität nicht übernommen. Um weiterhin Gerätekategorien verwenden zu können, müssen migrierte Geräte manuell zu den entsprechenden Sammlungen hinzugefügt werden, nachdem die MDM-Autorität geändert wurde und die Geräte in der Configuration Manager-Konsole angezeigt werden.
- Geräte, denen keine Benutzer zugeordnet sind (dies ist typischerweise der Fall, wenn Sie das iOS-Programm zur Geräteregistrierung oder die Massenregistrierung verwenden), werden nicht zur neuen MDM-Autorität migriert. Für diese Geräte müssen Sie sich mit dem Support in Verbindung setzen, um Hilfe beim Verschieben dieser Geräte zur neuen MDM-Autorität zu erhalten.

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager"></a>Vorbereiten der Umstellung der MDM-Autorität auf Configuration Manager

Überprüfen Sie die folgenden Informationen, um die Umstellung der MDM-Autorität vorzubereiten:
- Sie benötigen Configuration Manager, Version 1610 oder höher, damit die Option zum Umstellen der MDM-Autorität verfügbar ist.
- Es kann bis zu acht Stunden dauern, bis ein Gerät eine Verbindung mit dem Dienst herstellt, nachdem Sie auf die neue MDM-Autorität umgestellt haben.
- Erstellen Sie eine Configuration Manager-Benutzersammlung mit allen Benutzern, die zurzeit von Intune standalone verwaltet werden, um sie beim Einrichten des Intune-Abonnements in der Configuration Manager-Konsole zu nutzen. Mit dieser Sammlung können Sie sicherstellen, dass diesen Benutzern und ihren Geräten eine Configuration Manager-Lizenz zugewiesen wird und dass sie nach der Umstellung der MDM-Autorität in der Hybridumgebung verwaltet werden.
- Stellen Sie sicher, dass der IT-Administratorbenutzer auch in dieser Benutzersammlung enthalten ist.  
- Vor der Umstellung wird in der Intune-Verwaltungskonsole für die MDM-Autorität **Auf Microsoft Intune setzen** (Intune standalone) angezeigt.
- Für die MDM-Autorität sollte in der Microsoft Intune-Verwaltungskonsole vor der Umstellung der MDM-Autorität **Auf Microsoft Intune setzen** (eigenständiger Mandant) angezeigt werden.
    > [!NOTE]    
    > Wenn für die MDM-Autorität **Von Intune und Office 365 verwaltet** angezeigt wird, werden Ihre von Office 365 verwalteten MDM-Geräte nicht mehr verwaltet, wenn Sie die MDM-Autorität auf **Configuration Manager** (hybrid) umstellen. Es wird empfohlen, dass Sie die Benutzer für Intune oder Enterprise Mobility Suite lizenzieren, bevor Sie die MDM-Autorität umstellen.   

- Entfernen Sie in der [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) die Geräteregistrierungs-Manager-Rolle. Weitere Informationen finden Sie unter [Löschen eines Geräteregistrierungs-Managers aus Intune](device-enrollment-manager-enroll.md#remove-device-enrollment-manager-permissions).
- Deaktivieren Sie alle konfigurierten Gerätegruppenzuordnungen. Weitere Informationen finden Sie unter [Kategorisieren von Geräten mithilfe der Gerätegruppenzuordnung in Microsoft Intune](device-group-mapping.md).
- Während der Umstellung der MDM-Autorität sollte es keine wahrnehmbaren Auswirkungen auf die Endbenutzer geben. Möglicherweise sollten Sie jedoch die Benutzer über die Umstellung informieren, um sicherzustellen, dass ihre Geräte eingeschaltet sind und dass sie kurz nach der Umstellung eine Verbindung mit dem Dienst herstellen. Diese Maßnahme stellt sicher, dass so viele Geräte wie möglich eine Verbindung herstellen und so bald wie möglich über die neue Autorität beim Dienst registriert werden.
- Wenn Sie vor der Umstellung der MDM-Autorität Intune eigenständig zum Verwalten von iOS-Geräten verwenden, müssen Sie sicherstellen, dass das gleiche Apple Push Notification Service-Zertifikat (APNs), das zuvor in Intune verwendet wurde, erneuert und wieder zum Einrichten des Mandanten in Configuration Manager (hybrid) verwendet wird.    

    > [!IMPORTANT]  
    > Wenn ein anderes APNs-Zertifikat für die hybride Verwaltung verwendet wird, wird die Registrierung ALLER zuvor registrierten iOS-Geräte aufgehoben, und Sie müssen sie erneut registrieren. Stellen Sie vor der Umstellung der MDM-Autorität sicher, dass Sie genau wissen, welches APNs-Zertifikat zum Verwalten von iOS-Geräten in Intune verwendet wurde. Suchen Sie nach dem Zertifikat im Apple Push Certificates-Portal (https://identity.apple.com)), und stellen Sie sicher, dass der Benutzer, mit dessen Apple-ID das ursprüngliche APNs-Zertifikat erstellt wurde, identifiziert wird und verfügbar ist, um das gleiche APNs-Zertifikat als Teil der Umstellung auf die neue MDM-Autorität zu erneuern.

## <a name="change-the-mdm-authority-to-configuration-manager"></a>Umstellen der MDM-Autorität auf Configuration Manager

1. Wechseln Sie in der Configuration Manager-Konsole zu **Verwaltung** &gt; **Übersicht** &gt; **Clouddienste** &gt; **Microsoft Intune-Abonnement**, und wählen Sie aus, dass Sie ein Intune-Abonnement hinzufügen möchten.
2. Melden Sie sich bei dem Intune-Mandanten an, den Sie ursprünglich beim Festlegen der MDM-Autorität in Intune verwendet haben, und klicken Sie auf **Weiter**.
3. Wählen Sie **MDM-Autorität auf Configuration Manager umstellen** aus, und klicken Sie auf **Weiter**.
4. Wählen Sie die Benutzersammlung aus, die alle Benutzer enthält, die von der neuen hybriden MDM-Autorität verwaltet werden sollen.
5. Klicken Sie auf **Weiter** , und schließen Sie den Assistenten ab. Die MDM-Autorität wurde jetzt auf **Configuration Manager** umgestellt.
6. Melden Sie sich bei der [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) mit dem gleichen Intune-Mandanten an, und überprüfen Sie, ob die MDM-Autorität in **Auf Configuration Manager setzen** geändert wurde.
7. Nach der Umstellung der MDM-Autorität auf Configuration Manager können Sie die [iOS-Registrierung](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac) und die [Android-Registrierung](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-android) einrichten.
8. Konfigurieren Sie in der Configuration Manager-Verwaltungskonsole die neuen Einstellungen und Apps der neuen MDM-Autorität (hybrid), und stellen Sie sie bereit.

Wenn Geräte das nächste Mal eine Verbindung mit dem Dienst herstellen, werden sie synchronisiert und erhalten die neuen Einstellungen von der neuen MDM-Autorität.

## <a name="change-mdm-authority-to-office-365"></a>Ändern der MDM-Autorität in Office 365

Navigieren Sie zu [https://protection.office.com](https://protection.office.com), und wählen Sie **Data Loss Prevention** > **Device Security Policies** > **View list of Managed Devices** > **Let's get started** (Verhinderung von Datenverlust > Gerätesicherheitsrichtlinien > Liste verwalteter Geräte anzeigen > Erste Schritte) aus, um Office 365 MDM zusätzlich zu Ihrem vorhandenen Intune-Dienst zu aktivieren.

Weitere Informationen finden Sie unter [Einrichten der Verwaltung mobiler Geräte (MDM) in Office 365](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd).

Wenn die Endbenutzer nur durch Office 365 MDM verwaltet werden sollen, müssen Sie zugewiesene Intune- und bzw. oder EMS-Lizenzen nach der Aktivierung von Office 365 MDM entfernen.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Bereinigen mobiler Geräte nach Ablauf des MDM-Zertifikats

Das MDM-Zertifikat wird automatisch erneuert, wenn mobile Geräte mit dem Intune-Dienst kommunizieren. Wenn mobile Geräte zurückgesetzt werden oder für längere Zeit keine Kommunikation mit dem Intune-Dienst stattfindet, wird das MDM-Zertifikat nicht erneuert. Das Gerät wird 180 Tage nach Ablauf des MDM-Zertifikats aus dem Azure-Portal entfernt.

## <a name="remove-mdm-authority"></a>Entfernen der MDM-Autorität

Die MDM-Autorität kann nicht in „Unbekannt“ geändert werden. Microsoft Server verwenden die MDM-Autorität, um zu bestimmen, an welches Portal diese registrierten Geräte melden (ConfigMGR, Azure Intune, Office 365 MDM).

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>Was passiert nach der Umstellung der MDM-Autorität

- Wenn der Intune-Dienst erkennt, dass die MDM-Autorität eines Mandanten umgestellt wurde, sendet er eine Benachrichtigung an alle registrierten Geräte, damit sie beim Dienst eingecheckt und synchronisiert werden (diese Benachrichtigung befindet sich außerhalb der regelmäßig geplanten Eincheckvorgänge). Nach der Umstellung der MDM-Autorität für den Mandanten von Intune standalone auf hybrid stellen daher alle Geräte, die eingeschaltet und online sind, eine Verbindung mit dem Dienst her, erhalten die neue MDM-Autorität und werden hybrid verwaltet. Es gibt keine Unterbrechung bei der Verwaltung und dem Schutz dieser Geräte.
- Selbst für Geräte, die während (oder kurz nach) der Umstellung der MDM-Autorität eingeschaltet und online sind, gibt es eine Verzögerung von bis zu acht Stunden (je nach Zeitpunkt des nächsten geplanten regulären Eincheckvorgangs), bevor Geräte unter der neuen MDM-Autorität beim Dienst registriert werden.    

  > [!IMPORTANT]    
  > In der Zeit zwischen der Umstellung der MDM-Autorität und dem Hochladen des erneuerten APNs-Zertifikats in die neue Autorität schlagen neue Registrierungen und Eincheckvorgänge für iOS-Geräte fehl. Aus diesem Grund ist es wichtig, dass Sie das APNs-Zertifikat so bald wie möglich nach der Umstellung der MDM-Autorität überprüfen und in die neue Autorität hochladen.

- Benutzer können schnell auf die neue MDM-Autorität umstellen, indem sie manuell einen Eincheckvorgang des Geräts beim Dienst starten. Benutzer können diese Änderung problemlos mithilfe der Unternehmensportal-App und dem Initiieren einer Überprüfung der Gerätekonformität vornehmen.
- Um zu überprüfen, ob nach der Umstellung der MDM-Autorität und dem Einchecken und Synchronisieren der Geräte beim Dienst alles ordnungsgemäß funktioniert, suchen Sie in der Configuration Manager-Konsole nach den Geräten. Die Geräte, die zuvor von Intune verwaltet wurden, werden jetzt in der Configuration Manager-Konsole als verwaltete Geräte angezeigt.    
- Es gibt eine Übergangszeit, bis ein Gerät beim Dienst eingecheckt wird, wenn das Gerät während der Umstellung der MDM-Autorität offline war. Um sicherzustellen, dass das Gerät während dieser Übergangszeit geschützt und funktionsfähig bleibt, verbleiben die folgenden Profile bis zu sieben Tage lang auf dem Gerät (oder bis das Gerät eine Verbindung mit der neuen MDM-Autorität herstellt und die neuen Einstellungen empfängt, die die vorhandenen überschreiben):
    - E-Mail-Profil
    - VPN-Profil
    - Zertifikatprofil
    - WLAN-Profil
    - Konfigurationsprofile
- Nachdem Sie auf die neue MDM-Autorität umgestellt haben, kann es bis zu einer Woche dauern, bis die Kompatibilitätsinformationen in der Microsoft Intune-Verwaltungskonsole richtig gemeldet werden. Allerdings sind die Konformitätszustände in Azure Active Directory und auf dem Gerät richtig, sodass das Gerät weiterhin geschützt ist.
- Stellen Sie sicher, dass die neuen Einstellungen, mit denen die vorhandenen Einstellungen überschrieben werden sollen, den gleichen Namen aufweisen wie die vorherigen, damit die alten Einstellungen tatsächlich überschrieben werden. Andernfalls weisen die Geräte möglicherweise redundante Profile und Richtlinien auf.    

  > [!TIP]    
  > Es empfiehlt sich, alle Verwaltungseinstellungen und Konfigurationen sowie Bereitstellungen kurz nach Abschluss der Umstellung der MDM-Autorität zu erstellen. Dadurch wird sichergestellt, dass Geräte in der Übergangszeit geschützt und aktiv verwaltet werden.

-  Führen Sie nach der Umstellung der MDM-Autorität die folgenden Schritte aus, um zu überprüfen, ob neue Geräte erfolgreich bei der neuen Autorität registriert werden:   
    - Registrieren eines neuen Geräts
    - Stellen Sie sicher, dass das neu registrierte Gerät in der Configuration Manager-Konsole angezeigt wird.
    - Führen Sie über die Verwaltungskonsole auf dem Gerät eine Aktion aus, z.B. Remotesperre. Wenn sie erfolgreich ist, wird das Gerät durch die neue MDM-Autorität verwaltet.
- Wenn Sie Probleme mit bestimmten Geräten haben, können Sie die Registrierung der Geräte aufheben und sie erneut registrieren, damit sie so schnell wie möglich mit der neuen Autorität verbunden und von ihr verwaltet werden.

## <a name="next-steps"></a>Nächste Schritte

Da die MDM-Autorität nun festgelegt ist, können Sie mit der [Geräteregistrierung](device-enrollment.md) beginnen.
