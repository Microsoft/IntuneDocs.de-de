---
title: Umstellen Ihrer MDM-Autorität auf Configuration Manager (hybride Verwaltung mobiler Geräte)
description: Erfahren Sie, wie Sie die MDM-Autorität von eigenständigem Intune in Configuration Manager (hybride Verwaltung mobiler Geräte) ändern können.
keywords: ''
author: dougeby
manager: dougeby
ms.date: 10/04/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f1b4bce3-7932-4a0d-aa92-6dacc7060f42
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: dc73befb46f1f159d9a8c023bb5604517b9f73f4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="change-the-mdm-authority"></a>Ändern der MDM-Autorität
Ab Configuration Manager Version 1610 können Sie Ihre MDM-Autorität ohne Unterstützung durch den Microsoft-Support und ohne Aufheben der Registrierung und erneutes Registrieren Ihrer vorhandenen verwalteten Geräte umstellen. Dieses Thema zeigt Ihnen erforderliche Schritte, um einen vorhandenen Microsoft Intune-Mandanten, der über Intune konfiguriert wurde und dessen MDM-Autorität auf **Microsoft Intune** (standalone) festgelegt ist, ohne Aufheben der Registrierung und erneutes Registrieren vorhandener verwalteter Geräte auf **Configuration Manager** (hybride Verwaltung mobiler Geräte) umzustellen.

> [!Note]    
> Wenn Sie einen vorhandenen Microsoft Intune-Mandanten, der über die Configuration Manager-Konsole (hybrid) konfiguriert wurde und für den die MDM-Autorität auf **Configuration Manager** (hybrid) festgelegt ist, in eigenständiges **Microsoft Intune** ändern möchten, gehen Sie unter [Change the MDM authority from Configuration Manager (hybrid MDM) to Intune standalone (Umstellen der MDM-Autorität von Configuration Manager (hybride Verwaltung mobiler Geräte) auf Intune (standalone))](https://docs.microsoft.com/sccm/mdm/deploy-use/change-mdm-authority). 


## <a name="key-considerations"></a>Wichtige Überlegungen
Nachdem Sie auf die neue MDM-Autorität umgestellt haben, gibt es wahrscheinlich eine Übergangszeit (bis zu acht Stunden), bevor das Gerät eingecheckt und mit dem Dienst synchronisiert wird. Sie müssen Einstellungen in der neuen MDM-Autorität (hybrid) konfigurieren, um sicherzustellen, dass registrierte Geräte nach der Umstellung weiterhin verwaltet und geschützt werden. 
- Geräte müssen nach der Umstellung eine Verbindung mit dem Dienst herstellen, damit die Einstellungen der neuen MDM-Autorität (Intune standalone) die vorhandenen Einstellungen auf dem Gerät ersetzen.
- Nach dem Ändern der MDM-Autorität verbleiben einige der grundlegenden Einstellungen (z.B. Profile) aus der vorherigen MDM-Autorität (Intune standalone) für bis zu sieben Tage oder bis zur ersten Verbindung des Geräts mit dem Dienst auf dem Gerät. Es wird empfohlen, dass Sie Apps und Einstellungen (Richtlinien, Profile, Apps usw.) so bald wie möglich in der neuen MDM-Autorität (hybrid) konfigurieren und die Einstellung den Benutzergruppen bereitstellen, die Benutzer mit gegenwärtig registrierten Geräten enthalten. Sobald ein Gerät nach der Umstellung der MDM-Autorität eine Verbindung mit dem Dienst herstellt, werden die neuen Einstellungen der neuen MDM-Autorität übertragen, und Lücken bei Verwaltung und Schutz werden verhindert.
- Wenn in Intune und Configuration Manager die gleichen Gerätekategorien vorhanden sind, werden Zuweisungen von Gerätekategorien für Geräte beim Wechsel zur neuen MDM-Autorität nicht übernommen. Um weiterhin Gerätekategorien verwenden zu können, müssen migrierte Geräte manuell zu den entsprechenden Sammlungen hinzugefügt werden, nachdem die MDM-Autorität geändert wurde und die Geräte in der Configuration Manager-Konsole angezeigt werden.
- Geräte, denen keine Benutzer zugeordnet sind (dies ist typischerweise der Fall, wenn Sie das iOS-Programm zur Geräteregistrierung oder die Massenregistrierung verwenden), werden nicht zur neuen MDM-Autorität migriert. Für diese Geräte müssen Sie sich mit dem Support in Verbindung setzen, um Hilfe beim Verschieben dieser Geräte zur neuen MDM-Autorität zu erhalten.

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager-hybrid"></a>Vorbereiten der Umstellung der MDM-Autorität auf Configuration Manager (hybrid)
Überprüfen Sie die folgenden Informationen, um die Umstellung der MDM-Autorität vorzubereiten:
- Sie benötigen Configuration Manager, Version 1610 oder höher, damit die Option zum Umstellen der MDM-Autorität verfügbar ist.
- Es kann bis zu acht Stunden dauern, bis ein Gerät eine Verbindung mit dem Dienst herstellt, nachdem Sie auf die neue MDM-Autorität umgestellt haben.
- Erstellen Sie eine Configuration Manager-Benutzersammlung mit allen Benutzern, die zurzeit von Intune standalone verwaltet werden, um sie beim Einrichten des Intune-Abonnements in der Configuration Manager-Konsole zu nutzen. So können Sie sicherstellen, dass diesen Benutzern und ihren Geräten eine Configuration Manager-Lizenz zugewiesen wird und dass sie nach der Umstellung der MDM-Autorität in der Hybridumgebung verwaltet werden.
- Stellen Sie sicher, dass der IT-Administratorbenutzer auch in dieser Benutzersammlung enthalten ist.  
- Vor der Umstellung wird in der Intune-Verwaltungskonsole für die MDM-Autorität **Auf Microsoft Intune setzen** (Intune standalone) angezeigt.
- Für die MDM-Autorität sollte in der Microsoft Intune-Verwaltungskonsole vor der Umstellung der MDM-Autorität **Auf Microsoft Intune setzen** (eigenständiger Mandant) angezeigt werden.
    > [!NOTE]    
    > Wenn für die MDM-Autorität **Von Intune und Office 365 verwaltet** angezeigt wird, werden Ihre von Office 365 verwalteten MDM-Geräte nicht mehr verwaltet, wenn Sie die MDM-Autorität auf **Configuration Manager** (hybrid) umstellen. Es wird empfohlen, dass Sie die Benutzer für Intune oder Enterprise Mobility Suite lizenzieren, bevor Sie die MDM-Autorität umstellen.   

- Entfernen Sie in der [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) die Geräteregistrierungs-Manager-Rolle. Weitere Informationen finden Sie unter [Löschen eines Geräteregistrierungs-Managers aus Intune](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune#delete-a-device-enrollment-manager-from-intune).
- Deaktivieren Sie alle konfigurierten Gerätegruppenzuordnungen. Weitere Informationen finden Sie unter [Kategorisieren von Geräten mithilfe der Gerätegruppenzuordnung in Microsoft Intune](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune).
- Während der Umstellung der MDM-Autorität sollte es keine wahrnehmbaren Auswirkungen auf die Endbenutzer geben. Möglicherweise sollten Sie jedoch die Benutzer über die Umstellung informieren, um sicherzustellen, dass ihre Geräte eingeschaltet sind und dass sie kurz nach der Umstellung eine Verbindung mit dem Dienst herstellen. Dadurch wird sichergestellt, dass so viele Geräte wie möglich eine Verbindung herstellen und so bald wie möglich über die neue Autorität beim Dienst registriert werden.
- Wenn Sie vor der Umstellung der MDM-Autorität Intune standalone zum Verwalten von iOS-Geräten verwenden, müssen Sie sicherstellen, dass das gleiche Apple Push Notification Service-Zertifikat (APNs), das zuvor in Intune verwendet wurde, erneuert und wieder zum Einrichten des Mandanten in Configuration Manager (hybrid) verwendet wird.    

    > [!IMPORTANT]  
    > Wenn ein anderes APNs-Zertifikat für die hybride Verwaltung verwendet wird, wird die Registrierung ALLER zuvor registrierten iOS-Geräte aufgehoben, und Sie müssen sie erneut registrieren. Stellen Sie vor der Umstellung der MDM-Autorität sicher, dass Sie genau wissen, welches APNs-Zertifikat zum Verwalten von iOS-Geräten in Intune verwendet wurde. Suchen Sie nach dem Zertifikat im Apple Push Certificates-Portal (https://identity.apple.com)), und stellen Sie sicher, dass der Benutzer, mit dessen Apple-ID das ursprüngliche APNs-Zertifikat erstellt wurde, identifiziert wird und verfügbar ist, um das gleiche APNs-Zertifikat als Teil der Umstellung auf die neue MDM-Autorität zu erneuern.  

## <a name="change-the-mdm-authority-to-configuration-manager"></a>Umstellen der MDM-Autorität auf Configuration Manager
Die Umstellung der MDM-Autorität auf Configuration Manager (hybrid) umfasst die folgenden allgemeinen Schritte:  
- Fügen Sie das Microsoft Intune-Abonnement in der Configuration Manager-Konsole hinzu.
- Konfigurieren Sie das Apple APNs-Zertifikat mit dem gleichen APNs-Zertifikat, das Sie erneuert haben.
- Konfigurieren Sie in der Configuration Manager-Verwaltungskonsole die neuen Einstellungen und Apps der neuen MDM-Autorität (hybrid), und stellen Sie sie bereit.
- Wenn Geräte das nächste Mal eine Verbindung mit dem Dienst herstellen, werden sie synchronisiert und erhalten die neuen Einstellungen von der neuen MDM-Autorität.

#### <a name="to-change-the-mdm-authority-to-configuration-manager"></a>So stellen Sie die MDM-Autorität auf Configuration Manager um
1. Wechseln Sie in der Configuration Manager-Konsole zu **Verwaltung** &gt; **Übersicht** &gt; **Clouddienste** &gt; **Microsoft Intune-Abonnement**, und wählen Sie aus, dass Sie ein Intune-Abonnement hinzufügen möchten.
2. Melden Sie sich bei dem Intune-Mandanten an, den Sie ursprünglich beim Festlegen der MDM-Autorität in Intune verwendet haben, und klicken Sie auf **Weiter**.
3. Wählen Sie **MDM-Autorität auf Configuration Manager umstellen** aus, und klicken Sie auf **Weiter**.
4. Wählen Sie die Benutzersammlung aus, die alle Benutzer enthält, die von der neuen hybriden MDM-Autorität verwaltet werden sollen.
5. Klicken Sie auf **Weiter** , und schließen Sie den Assistenten ab. Die MDM-Autorität wurde jetzt auf **Configuration Manager** umgestellt.
6. Melden Sie sich bei der [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) mit dem gleichen Intune-Mandanten an, und überprüfen Sie, ob die MDM-Autorität in **Auf Configuration Manager setzen** geändert wurde.


## <a name="enable-ios-enrollment"></a>Aktivieren der iOS-Registrierung
Wenn Sie iOS-Geräte verwenden, müssen Sie das APNs-Zertifikat in Configuration Manager konfigurieren.

#### <a name="to-enable-ios-enrollment-and-configure-the-apns-certificate"></a>So aktivieren Sie die iOS-Registrierung und konfigurieren das APNs-Zertifikat

1. **Laden Sie eine Zertifikatsignieranforderung herunter**.

   1. Wechseln Sie in der Configuration Manager-Konsole zu **Verwaltung** &gt; **Clouddienste** &gt; **Microsoft Intune-Abonnements**, und wählen Sie **APNs-Zertifikatanforderung erstellen** aus, um das Dialogfeld **APNs-Zertifikatsignieranforderung anfordern** zu öffnen.  
   2. **Navigieren** Sie zu dem Pfad, um die neue CSR-Datei (Zertifikatsignieranforderung) zu speichern. Speichern Sie die Zertifikatsignierungsanforderung (CSR-Datei) lokal.  
   3. Klicken Sie auf **Herunterladen**. Die neue CSR-Datei von Microsoft Intune wird heruntergeladen und von Configuration Manager gespeichert.   

      > [!IMPORTANT]
      > Sie müssen eine neue Zertifikatsignieranforderung herunterladen. Verwenden Sie keine vorhandene Datei, da dies zu einem Fehler führt.  

2. Wechseln Sie zum [Apple Push Certificates-Portal](http://go.microsoft.com/fwlink/?LinkId=269844), und melden Sie sich mit der **gleichen** Apple-ID an, die verwendet wurde, um zuvor das APNs-Zertifikat zu erstellen und zu erneuern, das Sie in Intune standalone verwendet haben.

   ![Anmeldeseite des Apple Push Certificates-Portals](../media/mdm-change-apns-portal.png)

3. Wählen Sie das APNs-Zertifikat aus, das Sie in Intune standalone verwendet haben, und klicken Sie dann auf **Erneuern**.

    ![Dialogfeld zur APNs-Erneuerung](../media/mdm-change-renew-apns.png)

4. Wählen Sie die APNs-Zertifikatsignieranforderung (CSR-Datei) aus, die Sie lokal heruntergeladen haben, und klicken Sie dann auf **Hochladen**.

    ![Anmeldeseite des Apple Push Certificates-Portals](../media/mdm-change-renew-apns-upload.png)
 
5. Wählen Sie das gleiche APNs-Zertifikat aus, und klicken Sie dann auf **Herunterladen**. Laden Sie das APNs-Zertifikat (.pem) herunter, und speichern Sie die Datei lokal.  

    ![Anmeldeseite des Apple Push Certificates-Portals](../media/mdm-change-renew-apns-download.png)

6. Laden Sie das erneuerte APNs-Zertifikat mit der gleichen Apple-ID wie zuvor auf den hybriden Mandanten hoch.

    1.  Wechseln Sie in der Configuration Manager-Konsole zu **Verwaltung** &gt; **Clouddienste** &gt; **Microsoft Intune-Abonnement**, und wählen Sie **Plattformen konfigurieren** &gt; **iOS** aus.  
    2.  Wählen Sie im Dialogfeld **Eigenschaften von Microsoft Intune-Abonnement** die Registerkarte **APNs-Zertifikat** aus, und aktivieren Sie das Kontrollkästchen **Registrierung bei iOS und Mac OS X (MDM) aktivieren**.  
    3.  Klicken Sie auf **Durchsuchen**, und wechseln Sie zu der von Apple heruntergeladenen APNs-Zertifikatdatei (CER-Datei). Configuration Manager zeigt die APNs-Zertifikatinformationen an. Klicken Sie auf **OK** , um das APNs-Zertifikat in Intune zu speichern.  

        ![Eigenschaftenseite des Intune-Abonnements – iOS](../media/mdm-change-subscription-properties-ios.png)

## <a name="enable-android-enrollment"></a>Aktivieren der Android-Registrierung
1. Wechseln Sie in der Configuration Manager-Konsole zu **Verwaltung** &gt; **Clouddienste** &gt; **Microsoft Intune-Abonnement**, und wählen Sie **Plattformen konfigurieren** &gt; **Android** aus.  
2. Wählen Sie **Android-Registrierung aktivieren** aus, und klicken Sie auf **OK**.

### <a name="enable-windows-enrollment"></a>Aktivieren der Windows-Registrierung
1. Wechseln Sie in der Configuration Manager-Konsole zu **Verwaltung** &gt; **Clouddienste** &gt; **Microsoft Intune-Abonnement**, und wählen Sie **Plattformen konfigurieren** &gt; **Windows** aus.  
2. Wählen Sie **Windows-Registrierung aktivieren** aus, und klicken Sie auf **OK**.

### <a name="enable-windows-phone-enrollment"></a>Aktivieren der Windows Phone-Registrierung
1. Wechseln Sie in der Configuration Manager-Konsole zu **Verwaltung** &gt; **Clouddienste** &gt; **Microsoft Intune-Abonnement**, und wählen Sie **Plattformen konfigurieren** &gt; **Windows Phone** aus.  
2. Wählen Sie die Plattform aus, die Sie aktivieren möchten, und klicken Sie auf **OK**.


## <a name="next-steps"></a>Nächste Schritte
Sobald die Umstellung der MDM-Autorität abgeschlossen ist, überprüfen Sie die folgenden Schritte:
- Wenn der Intune-Dienst erkennt, dass die MDM-Autorität eines Mandanten umgestellt wurde, sendet er eine Benachrichtigung an alle registrierten Geräte, damit sie beim Dienst eingecheckt und synchronisiert werden (außerhalb der regelmäßigen geplanten Eincheckvorgänge). Nach der Umstellung der MDM-Autorität für den Mandanten von Intune standalone auf hybrid stellen daher alle Geräte, die eingeschaltet und online sind, eine Verbindung mit dem Dienst her, erhalten die neue MDM-Autorität und werden hybrid verwaltet. Es gibt keine Unterbrechung bei der Verwaltung und dem Schutz dieser Geräte.
- Selbst für Geräte, die während (oder kurz nach) der Umstellung der MDM-Autorität eingeschaltet und online sind, gibt es eine Verzögerung von bis zu acht Stunden (je nach Zeitpunkt des nächsten geplanten regulären Eincheckvorgangs), bevor Geräte unter der neuen MDM-Autorität beim Dienst registriert werden.    

  > [!IMPORTANT]    
  > In der Zeit zwischen der Umstellung der MDM-Autorität und dem Hochladen des erneuerten APNs-Zertifikats in die neue Autorität schlagen neue Registrierungen und Eincheckvorgänge für iOS-Geräte fehl. Aus diesem Grund ist es wichtig, dass Sie das APNs-Zertifikat so bald wie möglich nach der Umstellung der MDM-Autorität überprüfen und in die neue Autorität hochladen.

- Benutzer können schnell auf die neue MDM-Autorität umstellen, indem sie manuell einen Eincheckvorgang des Geräts beim Dienst starten. Benutzer können dies problemlos mithilfe der Unternehmensportal-App und dem Initiieren einer Überprüfung der Gerätekonformität erreichen.
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