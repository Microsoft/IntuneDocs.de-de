---
title: Festlegen von Registrierungseinschränkungen in Microsoft Intune
titleSuffix: ''
description: Schränken Sie die Registrierung plattformbezogen ein, und legen Sie in Intune einen Grenzwert für die Geräteregistrierung fest.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1263df126b371780b3c5c14ae619f0cb7c83d475
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415304"
---
# <a name="set-enrollment-restrictions"></a>Festlegen von Registrierungseinschränkungen

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Als Intune-Administrator können Sie Registrierungsbeschränkungen erstellen und verwalten, mit denen definiert wird, welche Geräte für die Verwaltung mit Intune registriert werden können. Hierzu gehört Folgendes:
- Die Anzahl von Geräten.
- Betriebssysteme und Versionen.

Sie können mehrere Beschränkungen definieren und diese verschiedenen Benutzergruppen zuordnen. Für Ihre verschiedenen Beschränkungen können Sie eine [Prioritätsreihenfolge](#change-enrollment-restriction-priority) festlegen.

>[!NOTE]
>Registrierungseinschränkungen stellen keine Sicherheitsfunktionen dar. Gefährdete Geräte können falsche Angaben zu ihren Eigenschaften enthalten. Diese Einschränkungen sind eine bestmögliche Barriere für nicht böswillige Benutzer.

Sie können u.a. die folgenden spezifischen Registrierungsbeschränkungen festlegen:

- Maximale Anzahl registrierter Geräte
- Geräteplattformen, die registriert werden können:
  - Android-Geräteadministrator
  - Android Enterprise-Arbeitsprofil
  - iOS/iPadOS
  - macOS
  - Windows
  - Windows Mobile
- Plattformbetriebssystem-Version für iOS/iPadOS, Android-Geräteadministrator, Android Enterprise-Arbeitsprofil, Windows und Windows Mobile. (Es können nur Windows 10-Versionen verwendet werden. Dieses Feld bleibt leer, wenn Windows 8.1 zulässig ist.)
  - Mindestens erforderliche Version
  - Maximal zulässige Version
- Beschränken von [persönlichen Geräten](device-enrollment.md#bring-your-own-device) (nur iOS, Android-Geräteadministrator, Android Enterprise-Arbeitsprofil, macOS, Windows und Windows Mobile).

## <a name="default-restrictions"></a>Standardbeschränkungen

Auf den Gerätetyp und das Gerätelimit bezogene Registrierungsbeschränkungen werden standardmäßig vorgeschlagen. Sie können die Optionen für die Standardeinstellungen ändern. Standardbeschränkungen gelten für alle Benutzer- und benutzerlosen Registrierungen. Sie können diese Standardeinstellungen überschreiben, indem Sie neue Beschränkungen mit höheren Prioritäten definieren.

## <a name="create-a-device-type-restriction"></a>Erstellen einer Gerätetypeinschränkung

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an, und navigieren Sie zu  > **Geräte** > **Registrierungsbeschränkungen** > **Einschränkung erstellen** > **Gerätetypeinschränkung**.
2. Geben Sie auf der Seite **Grundlagen** einen **Name** und optional eine **Beschreibung** für die Beschränkung ein.
3. Klicken Sie auf **Weiter**, um zur Seite **Plattformeinstellungen** zu gelangen.
4. Wählen Sie unter **Plattform** die Option **Zulassen** für diejenigen Plattformen aus, für die diese Einschränkung zulässig sein soll.
    ![Screenshot: Auswählen der Plattformeinstellungen](./media/enrollment-restrictions-set/choose-platform-settings.png)
5. Wählen Sie unter **Versionen** die Mindest- und die Maximalversion aus, die von den Plattformen unterstützt werden soll. Versionseinschränkungen gelten nur für Geräte, die beim Unternehmensportal registriert sind.
     Folgende Versionsformate werden unterstützt:
    - Android-Geräteadministrator und Android Enterprise-Arbeitsprofil unterstützen „Hauptversion.Nebenversion.Revision.Build“.
    - iOS/iPadOS unterstützt major.minor.rev. Die Betriebssystemversionen gelten nicht für Apple-Geräte, die mit dem Programm zur Geräteregistrierung, dem Apple School Manager oder der App Apple Configurator registriert werden.
    - Windows unterstützt major.minor.build.rev nur für Windows 10.
    
    > [!IMPORTANT]
    > Android Enterprise (Arbeitsprofile) und Administratorplattformen für Android-Geräte verhalten sich wie folgt:
    > - Wenn beide Plattformen für die gleiche Gruppe zugelassen sind, werden die Benutzer mit einem Arbeitsprofil registriert, wenn ihr Gerät es unterstützt, andernfalls werden sie als Geräteadministrator angemeldet. 
    > - Wenn beide Plattformen für die Gruppe zugelassen und für bestimmte und nicht überschneidende Versionen verbessert sind, erhalten die Benutzer den für ihre Betriebssystemversion definierten Registrierungsflow. 
    > - Wenn beide Plattformen zugelassen sind, aber für die gleichen Versionen blockiert sind, dann werden Benutzer auf Geräten mit den blockierten Versionen aus dem Registrierungsflow des Android-Geräteadministrators entfernt und dann von der Registrierung ausgeschlossen und zur Abmeldung aufgefordert. 
    >
    > Es ist zu beachten, dass weder das Arbeitsprofil noch die Registrierung als Geräteadministrator funktionieren, es sei denn, die entsprechenden Voraussetzungen wurden bei der Android-Registrierung erfüllt. 
    
   > [!Note]
   > Windows 10 gibt die Buildnummer während der Registrierung nicht an. Wenn Sie zum Beispiel in Build 10.0.17134.100 eine Eingabe vornehmen und das Gerät über Build 10.0.17134.174 verfügt, wird es während der Registrierung blockiert.

6. Wählen Sie unter **Persönliches Eigentum** die Option **Zulassen** für die Plattformen, die Sie als Geräte im persönlichen Besitz zulassen möchten.
7. Geben Sie unter **Gerätehersteller** eine durch Trennzeichen getrennte Liste der Hersteller ein, die Sie blockieren möchten.
8. Klicken Sie auf **Weiter**, um zur Seite **Zuweisungen** zu gelangen.
9. Klicken Sie auf **Wählen Sie die Gruppen aus, die eingeschlossen werden sollen.** , und verwenden Sie dann das Suchfeld, um die Gruppen zu finden, die Sie in diese Einschränkung einschließen möchten. Die Beschränkung gilt nur für Gruppen, denen sie zugewiesen ist. Wenn Sie nicht mindestens einer Gruppe eine Beschränkung zuweisen, hat sie keine Wirkung. Klicken Sie anschließend auf **Auswählen**. 
    ![Screenshot: Auswählen der Plattformeinstellungen](./media/enrollment-restrictions-set/select-groups.png)
10. Klicken Sie auf **Weiter**, um zur Seite **Überprüfen + erstellen** zu gelangen.
11. Klicken Sie auf **Erstellen**, um die Einschränkung zu erstellen.
12. Die neue Beschränkung wird mit einer Priorität knapp über dem Standardwert erstellt. Sie können [die Priorität ändern](#change-enrollment-restriction-priority).


## <a name="create-a-device-limit-restriction"></a>Erstellen einer Gerätelimiteinschränkung

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an, und navigieren Sie zu  > **Geräte** > **Registrierungsbeschränkungen** > **Einschränkung erstellen** > **Gerätelimiteinschränkung**.
2. Geben Sie auf der Seite **Grundlagen** einen **Name** und optional eine **Beschreibung** für die Beschränkung ein.
3. Klicken Sie auf **Weiter**, um zur Seite **Gerätelimit** zu gelangen.
4. Wählen Sie unter **Gerätelimit** die maximale Anzahl von Geräten aus, die ein Benutzer registrieren kann.
    ![Screenshot: Auswählen des Gerätelimits](./media/enrollment-restrictions-set/choose-device-limit.png)
5. Klicken Sie auf **Weiter**, um zur Seite **Zuweisungen** zu gelangen.
6. Klicken Sie auf **Wählen Sie die Gruppen aus, die eingeschlossen werden sollen.** , und verwenden Sie dann das Suchfeld, um die Gruppen zu finden, die Sie in diese Einschränkung einschließen möchten. Die Beschränkung gilt nur für Gruppen, denen sie zugewiesen ist. Wenn Sie nicht mindestens einer Gruppe eine Beschränkung zuweisen, hat sie keine Wirkung. Klicken Sie anschließend auf **Auswählen**. 
    ![Screenshot: Auswählen von Gruppen](./media/enrollment-restrictions-set/select-groups-device-limit.png)
7. Klicken Sie auf **Weiter**, um zur Seite **Überprüfen + erstellen** zu gelangen.
8. Klicken Sie auf **Erstellen**, um die Einschränkung zu erstellen.
9. Die neue Beschränkung wird mit einer Priorität knapp über dem Standardwert erstellt. Sie können [die Priorität ändern](#change-enrollment-restriction-priority).

Während der BYOD-Registrierung erhalten Benutzer eine Benachrichtigung darüber, wenn das Limit registrierter Geräte erreicht ist. Diese sieht bei iOS beispielsweise folgendermaßen aus:

![iOS-Gerätelimitbenachrichtigung](./media/enrollment-restrictions-set/enrollment-restrictions-ios-set-limit-notification.png)

> [!IMPORTANT]
> Einschränkungen des Gerätelimits gelten nicht für die folgenden Windows-Registrierungstypen:
> - Gemeinsam verwaltete Registrierungen
> - GPO-Registrierungen
> - Registrierungen mit Azure Active Directory-Verknüpfung
> - Massenregistrierungen mit Azure Active Directory-Verknüpfung
> - Autopilot-Registrierungen
> - Registrierungen über den Geräteregistrierungs-Manager
>
> Gerätelimiteinschränkungen werden für diese Registrierungstypen nicht erzwungen, da diese als Szenarien mit gemeinsam genutzten Geräten gelten.
> Sie können für diese Registrierungstypen [in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal#configure-device-settings) harte Grenzwerte festlegen.


## <a name="change-enrollment-restrictions"></a>Ändern von Registrierungseinschränkungen

Sie können die Einstellungen für eine Registrierungseinschränkung ändern, indem Sie die folgenden Schritte ausführen. Diese Einschränkungen haben keine Auswirkungen auf Geräte, die bereits registriert wurden. Geräte, die mit dem [Intune-PC-Agent](../fundamentals/manage-windows-pcs-with-microsoft-intune.md) registriert sind, können nicht über dieses Feature blockiert werden.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an, und navigieren Sie zu  > **Geräte** > **Registrierungsbeschränkungen** > die zu ändernde Einschränkung auswählen > **Eigenschaften**.
2. Klicken Sie neben den Einstellungen, die Sie ändern möchten, auf **Bearbeiten**.
3. Nehmen Sie auf der Seite **Bearbeiten** die gewünschten Änderungen vor, und fahren Sie auf der Seite **Überprüfen und speichern** fort. Klicken Sie abschließend auf **Speichern**.


## <a name="blocking-personal-android-devices"></a>Blockieren privater Android-Geräte
- Wenn Sie die Registrierung persönlicher Android-Geräteadministrator-Geräte blockieren, können persönliche Android Enterprise-Arbeitsprofilgeräte weiterhin registriert werden.
- Standardmäßig sind die Einstellungen Ihrer Android Enterprise-Arbeitsprofilgeräte die gleichen wie bei Ihren Android-Geräteadministratorgeräten. Nachdem Sie die Einstellungen für Ihr Android Enterprise-Arbeitsprofil oder Ihren Android-Geräteadministrator geändert haben, ist dies nicht mehr der Fall.
- Wenn Sie die Registrierung persönlicher Android Enterprise-Arbeitsprofile blockieren, können sich nur unternehmenseigene Android-Geräte mit Android Enterprise-Arbeitsprofilen registrieren.

## <a name="blocking-personal-windows-devices"></a>Blockieren privater Windows-Geräte
Wenn Sie die Registrierung privater Windows-Geräte blockieren, überprüft Intune, ob jede neue Windows-Registrierungsanforderung als Unternehmensregistrierung autorisiert wurde. Nicht autorisierte Registrierungen werden blockiert.

Die folgenden Methoden sind als Windows-Unternehmensregistrierung autorisiert:
- Der Benutzer, der sich registriert, verwendet ein [Konto für den Geräteregistrierungs-Manager]( device-enrollment-manager-enroll.md).
- Das Gerät wird über [Windows Autopilot](enrollment-autopilot.md) registriert.
- Das Gerät ist bei Windows Autopilot registriert, jedoch ohne die Option „MDM enrollment only“ (Nur MDM-Registrierung) in den Windows-Einstellungen.
- Die IME-Nummer des Geräts ist unter **Geräteregistrierung** >  **[Bezeichner von Unternehmensgeräten](corporate-identifiers-add.md)** aufgeführt. (für Windows Phone 8.1 nicht unterstützt)
- Das Gerät wird über ein [Massenbereitstellungspaket](windows-bulk-enroll.md) registriert.
- Die Geräteregistrierung erfolgt über ein GPO oder eine [automatische Registrierung aus Configuration Manager für die Co-Verwaltung](https://docs.microsoft.com/configmgr/comanage/quickstart-paths#bkmk_path1).
 
Die folgenden Registrierungen werden von Intune als unternehmenseigen gekennzeichnet. Da sie die Steuerung pro Gerät durch den Intune-Administrator jedoch nicht unterstützen, werden sie blockiert:
- [Automatische MDM-Registrierung](windows-enroll.md#enable-windows-10-automatic-enrollment) mit der [Azure Active Directory-Einbindung während der Windows-Einrichtung](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Automatische MDM-Registrierung](windows-enroll.md#enable-windows-10-automatic-enrollment) mit der [Azure Active Directory-Einbindung aus den Windows-Einstellungen](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
Die folgenden persönlichen Registrierungsmethoden werden ebenso blockiert:
- [Automatische MDM-Registrierung](windows-enroll.md#enable-windows-10-automatic-enrollment) durch [Hinzufügen eines Geschäftskontos über die Windows-Einstellungen](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- Die Option [MDM enrollment only]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) (Nur MDM-Registrierung) in den Windows-Einstellungen.

\* Diese werden nicht blockiert, wenn sie bei Autopilot registriert sind.


## <a name="blocking-personal-iosipados-devices"></a>Blockieren privater iOS-/iPadOS-Geräte
Standardmäßig klassifiziert Intune iOS-/iPadOS-Geräte als privat. Um als unternehmenseigen klassifiziert zu werden, muss ein iOS-/iPadOS-Gerät eine der folgenden Bedingungen erfüllen:
- Mit einer Seriennummer oder IMEI registriert.
- Registriert mithilfe der automatisierten Geräteregistrierung (früher Programm zur Geräteregistrierung)


## <a name="change-enrollment-restriction-priority"></a>Ändern der Priorität der Registrierungsbeschränkung

Die Priorität wird verwendet, wenn ein Benutzer in mehreren Gruppen vorhanden ist, denen Beschränkungen zugewiesen sind. Benutzer unterliegen nur der Beschränkung mit der höchsten Priorität, die einer Gruppe zugewiesen wurde, zu der sie gehören. Beispiel: Joe gehört zu Gruppe A, der Beschränkungen der Priorität 5 zugewiesen sind, und zu Gruppe B, der Beschränkungen der Priorität 2 zugeordnet sind. Joe unterliegt also nur Einschränkungen der Priorität 2.

Wenn Sie eine Beschränkung definieren, wird sie der Liste direkt über dem Standardwert hinzugefügt.

Zur Geräteregistrierung gehören Standardbeschränkungen für den Gerätetyp und das Gerätelimit. Diese beiden Beschränkungen gelten für alle Benutzer, es sei denn, sie werden durch Beschränkungen höherer Priorität außer Kraft gesetzt.

Sie können die Priorität jeder nicht standardmäßigen Beschränkung ändern.

1. Melden Sie sich im Azure-Portal an.
2. Klicken Sie auf **Weitere Dienste**, suchen Sie nach **Intune**, und klicken Sie dann auf **Intune**.
3. Klicken Sie auf **Geräteregistrierung** > **Registrierungsbeschränkungen**.
4. Zeigen Sie in der Prioritätenliste auf die Beschränkung.
5. Ziehen Sie mithilfe der drei vertikalen Punkte die Priorität an die gewünschte Position in der Liste.
