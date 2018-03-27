---
title: Registrieren von iOS-Geräten mithilfe des Setup-Assistenten
description: Registrieren von unternehmenseigenen iOS-Geräten mithilfe des Apple Configurator-Tools, um die Geräte auf die Werkseinstellungen zurückzusetzen und für die Ausführung des Setup-Assistenten vorzubereiten.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 03/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a33c383cb65d0edfa94117278e3f473699588aa3
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="enroll-ios-devices-with-apple-configurator-by-using-setup-assistant"></a>Registrieren von iOS-Geräten mithilfe von Apple Configurator und Setup-Assistent

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune unterstützt die Registrierung unternehmenseigener iOS-Geräte mithilfe des Tools [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017), das auf einem Mac-Computer ausgeführt wird. Dieser Prozess setzt das Gerät auf die Werkseinstellungen zurück und bereitet es auf die Ausführung des Setup-Assistenten vor, um die Unternehmensrichtlinien für den neuen Benutzer des Geräts zu installieren.

>[!NOTE]
>Diese Registrierungsmethode kann nicht mit dem [Geräteregistrierungs-Manager](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) verwendet werden.

Mit Apple Configurator können Sie ein iOS-Gerät auf die Werkseinstellungen zurücksetzen und auf die Einrichtung für den neuen Benutzer des Geräts vorbereiten. Bei dieser Methode muss das iOS-Gerät über USB mit einem Mac-Computer verbunden werden, um die Registrierung beim Unternehmen einzurichten. Vorausgesetzt wird die Verwendung von Apple Configurator 2.0. Bei den meisten Szenarien ist es erforderlich, dass die auf das iOS-Gerät angewendete Richtlinie **Benutzeraffinität** einschließt, um das Intune-Unternehmensportal zu aktivieren.

## <a name="prerequisites-for-enrolling-ios-devices-by-using-apple-configurator-with-setup-assistant"></a>Voraussetzungen für die Anmeldung von iOS-Geräten mithilfe von Apple Configurator mit dem Setup-Assistenten

- [Installieren eines APNS-Zertifikats](set-up-ios-and-mac-management-with-microsoft-intune.md)

- Stellen Sie sicher, dass Sie über physischen Zugriff auf iOS-Geräte verfügen&mdash;Geräte müssen auf die Werkseinstellungen zurückgesetzt sein und dürfen keinen Kennwortschutz aufweisen

- Rufen Sie die Geräteseriennummern ab&mdash; siehe [Abrufen einer iOS-Seriennummer](https://support.apple.com/HT204308)

- Haben Sie ein USB-Verbindungskabel zur Hand

- Verfügen Sie über einen Mac-Computer mit [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)


## <a name="steps-to-enroll-ios-devices-by-using-apple-configurator-with-setup-assistant"></a>Schritte für die Registrierung von iOS-Geräten mithilfe von Apple Configurator mit dem Setup-Assistenten

In den folgenden Schritten wird erläutert, wie Sie iOS-Geräte am „Tag 0“ mithilfe von Apple Configurator mit dem Setup-Assistenten registrieren. Da Geräte zu Ihrer Organisation hinzugefügt und auch wieder aus dieser entfernt werden, werden Sie wahrscheinlich einige dieser Schritte wiederholen, z.B. das Hinzufügen und Entfernen von Seriennummern, so wie unten beschrieben.

### <a name="create-mobile-device-groups-optional"></a>Erstellen von mobilen Gerätegruppen (optional)

Wenn Ihr Unternehmen mobile Gerätegruppen zur Verwaltung von Geräten erfordert, können Sie optional diese Gruppen erstellen. Weitere Informationen finden Sie unter [Verwenden von Gruppen zum Verwalten von Benutzern und Geräten in Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

### <a name="create-a-profile-for-devices"></a>Erstellen eines Profils für Geräte

Ein Registrierungsprofil für Geräte definiert die Einstellungen für eine Gruppe von Geräten.

1. Wechseln Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) zu **Richtlinie** &gt; **Unternehmensgeräteregistrierung**, und wählen Sie anschließend **Hinzufügen** aus.

  ![Erstellen eines Geräteregistrierungsprofils](../media/pol-sa-corp-enroll.png)

2. Geben Sie die Details für die Geräteprofile ein:

   -   **Name:** Der Name des Geräteregistrierungsprofils (für Benutzer nicht sichtbar).

   -   **Beschreibung:** Eine Beschreibung des Geräteregistrierungsprofils (für Benutzer nicht sichtbar).

   -   **Registrierungsdetails**: Gibt an, wie Geräte registriert werden.

       -   **Benutzeraffinität anfordern**: Das Gerät muss während der ersten Installation einem Benutzer zugewiesen werden und kann dann die Berechtigung erhalten, auf Daten und E-Mails des Unternehmens zuzugreifen. **Benutzeraffinität** muss für verwaltete Geräte eingerichtet werden, die Benutzern gehören und das Unternehmensportal verwenden müssen, um Dienste wie die Installation von Apps nutzen zu können.

       -   **Keine Benutzeraffinität**: Das Gerät ist keinem Benutzer zugeordnet. Verwenden Sie diese Zuweisung für Geräte, die Aufgaben ohne den Zugriff auf lokale Benutzerdaten ausführen. Apps, die eine Benutzerzugehörigkeit erfordern (einschließlich der Unternehmensportal-App, die für die Installation branchenspezifischer Apps verwendet wird), funktionieren nicht.

   -   **Gerätegruppen-Vorabzuweisung**: Alle Geräte, die mit diesem Profil bereitgestellt werden, gehören anfänglich zu dieser Gruppe. Sie können die Geräte nach der Registrierung erneut zuweisen.

   > [!Important]
   > Gruppenzuweisungen werden von Intune zu Azure Active Directory verschoben. Sobald Ihr Intune-Konto die anwendbaren Updates erhält, wird Ihnen nicht mehr die Option **Geräte folgender Gruppe zuweisen** angezeigt. [Erfahren Sie mehr](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune#changes-to-intune-group-assignments).

   -  **Geräteregistrierungsprogramm**: Das Apple-Programm zur Geräteregistrierung (Device Enrollment Program, DEP) kann bei der Registrierung mit dem Setup-Assistenten nicht verwendet werden. Stellen Sie sicher, dass die Umschaltfläche auf **aus** festgelegt ist.

3.  Wählen Sie **Profil speichern**, um das Profil hinzuzufügen.

### <a name="add-ios-devices-to-enroll-with-setup-assistant"></a>Mit dem Setup-Assistenten zu registrierende Geräte hinzufügen

1. Wechseln Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) zu **Gruppen** &gt; **Alle Geräte** &gt; **Alle unternehmenseigenen Geräte** &gt; **Alle Geräte**, und wählen Sie dann **Geräte hinzufügen** aus.

   Sie können Geräte auf zwei Arten hinzufügen:

   ![Dialogfeld „Geräte hinzufügen“](../media/pol-SA-enroll-iOS-SetupAssistant.png)

   -  **Hochladen einer CSV-Datei mit Seriennummern**: Erstellen Sie eine durch Trennzeichen getrennte Liste (CSV-Datei) mit zwei Spalten ohne Überschrift, die auf 5.000 Geräte oder 5 MB pro CSV-Datei beschränkt ist.

    |||
    |-|-|
    |&lt;Seriennummer 1&gt;|&lt;Details zu Gerät 1&gt;|
    |&lt;Seriennummer 2&gt;|&lt;Details zu Gerät 2&gt;|

  Diese CSV-Datei sieht bei Anzeige in einem Text-Editor folgendermaßen aus:

    ```
    0000000,PO 1234
    111111111,PO 1234
    ```

  -  **Manuelles Hinzufügen von Gerätedetails**&mdash;Geben Sie die Seriennummer und alle Anmerkungen und Details von bis zu 15 Geräten ein.

  Bestätigen Sie im Bereich **Geräte überprüfen** die Seriennummern. Sie können auch entscheiden, ob Sie die **Details** für Seriennummern überschreiben, die wieder importiert werden. Alternativ können Sie das Kontrollkästchen **Überschreiben** deaktivieren, um die aktuellen Informationen zu erhalten.

  > [!NOTE]
  > In der vorhandenen Intune-Administratorkonsole können Administratoren zugehörige Details einer hochgeladenen CSV-Datei akzeptieren und die vorhandenen Details für einzelne Seriennummern überschreiben. Sie können im neuen Azure-Portal nur die Details für alle Seriennummern überschreiben oder die Details für ebendiese ignorieren.

  > [!NOTE]
  > Wenn Sie später unternehmenseigene Geräte aus der Intune-Verwaltung entfernen müssen, kann es notwendig sein, aus der Gerätegruppe **Nach iOS-Seriennummer** unter **Vorabregistrierte Unternehmensgeräte** die Seriennummer der Geräte in Intune zu entfernen, um die Geräteregistrierung zu deaktivieren. Wenn Intune eine Notfallwiederherstellung durchführt, während oder nachdem Sie Seriennummern entfernt haben, müssen Sie sicherstellen, dass in dieser Gruppe nur die Seriennummern aktiver Geräte vorhanden sind.

2. Klicken Sie auf **Weiter**.

3. Wählen Sie die zu registrierenden Geräte aus. Bereits registrierte oder anderweitig registrierte Seriennummern werden nicht importiert. Klicken Sie auf **Weiter**, um fortzufahren.

### <a name="assign-a-profile"></a>Zuweisen eines Profils

Geben Sie das Profil an, das hinzugefügten Geräten aus der Liste der verfügbaren Profile zugewiesen werden soll, überprüfen Sie die **Registrierungsprofildetails**, und wählen Sie dann **Fertig stellen** aus. Manuell hinzugefügte Geräte können einem beliebigen Registrierungsprofil zugewiesen werden.

> [!Important]
> Derzeit können Sie in Intune ein „Standard“-Geräteregistrierungsprofil bestimmen. Das bedeutet, dass neue Seriennummern automatisch diesem Standardprofil hinzugefügt werden, wenn Sie neue Seriennummern mit dem Apple-Dienst synchronisieren. Wenn Ihr Mandant demnächst zum Azure-Portal migriert wird, können Sie kein Standardprofil mehr festlegen, und Seriennummern werden nicht mehr automatisch diesem Profil zugewiesen. Sie müssen stattdessen einem Profil Seriennummern zuweisen. [Erfahren Sie mehr](https://docs.microsoft.com/intune/device-enrollment-program-enroll-ios)

### <a name="export-a-profile-to-deploy-to-ios-devices"></a>Exportieren eines Profils zum Bereitstellen auf iOS-Geräten

1. Wechseln Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) zu **Richtlinie** &gt; **Unternehmensgeräteregistrierung**, und wählen Sie das Geräteprofil aus, das auf mobilen Geräten bereitgestellt werden soll.

2. Wählen Sie in der Taskleiste **Exportieren** aus. Kopieren und speichern Sie die **Profil-URL**. Sie werden sie später in Apple Configurator hochladen, um das von iOS-Geräten verwendete Intune-Profil zu definieren.

   Sie laden im folgenden Verfahren diese Profil-URL mit Apple Configurator in den Apple-Dienst hoch, um das von iOS-Geräten verwendete Intune-Profil zu definieren.

### <a name="prepare-the-device-with-apple-configurator"></a>Vorbereiten des Geräts mit Apple Configurator

iOS-Geräte werden mit dem Mac-Computer verbunden und für die Verwaltung mobiler Geräte registriert.

1.  Öffnen Sie auf einem Mac-Computer **Apple Configurator 2**. Wählen Sie in der Menüleiste **Apple Configurator 2**, und wählen Sie dann **Voreinstellungen**.

   > [!WARNING]
   > Während des Registrierungsprozesses werden die Geräte auf Werkseinstellungen zurückgesetzt. Als bewährte Methode empfiehlt es sich, das Gerät zurückzusetzen und einzuschalten. Nach dem Verbinden eines Geräts sollte der **Begrüßungsbildschirm** angezeigt werden.

2. Wählen Sie im Bereich „Voreinstellungen“ die Option **Server** aus, und wählen Sie das Pluszeichen, um den MDM-Server-Assistenten zu starten. Klicken Sie auf **Weiter**.

3. Geben Sie den **Hostnamen oder die URL** und die **Registrierungs-URL** für den MDM-Server unter „Registrierung von iOS-Geräten bei Microsoft Intune über den Setup-Assistenten“. Geben Sie für die Registrierungs-URL die aus Intune exportierte Registrierungsprofil-URL ein. Klicken Sie auf **Weiter**.  

   Sie können die Warnung, dass die Server-URL nicht überprüft wird, problemlos ignorieren. Um den Vorgang fortzusetzen, wählen Sie **Weiter**, bis der Assistent abgeschlossen ist.

4.  Verbinden Sie die mobilen iOS-Geräte über einen USB-Adapter mit dem Mac-Computer.

    > [!WARNING]
    > Während des Registrierungsprozesses werden die Geräte auf Werkseinstellungen zurückgesetzt. Als bewährte Methode empfiehlt es sich, das Gerät zurückzusetzen und einzuschalten. Wenn Sie den Setup-Assistenten starten, sollte der **Begrüßungsbildschirm** zu sehen sein.

5.  Wählen Sie **Vorbereiten**. Wählen Sie im Bereich „iOS-Gerät vorbereiten“ die Option **Manuell** aus, und wählen Sie dann **Weiter**.

6. Wählen Sie im Bereich „Beim MDM-Server registrieren“ den erstellten Servernamen aus, und wählen Sie dann **Weiter**.

7. Wählen Sie im Bereich „Geräte überwachen“ den Grad der Überwachung aus, und wählen Sie dann **Weiter**.

8. Wählen Sie im Bereich „Organisation erstellen“ die **Organisation** aus, oder erstellen Sie eine neue Organisation, und wählen Sie dann **Weiter**.

9. Wählen Sie im Bereich „iOS-Setup-Assistenten konfigurieren“ die Schritte aus, die dem Benutzer angezeigt werden sollen, und wählen Sie dann **Vorbereiten**. Authentifizieren Sie sich, wenn Sie dazu aufgefordert werden, um die Vertrauenseinstellungen zu aktualisieren.  

10. Trennen Sie das USB-Kabel, wenn die Vorbereitung des iOS-Geräts abgeschlossen ist.  

### <a name="distribute-devices"></a>Verteilen von Geräten

Die Geräte sind nun für die Unternehmensregistrierung bereit. Schalten Sie die Geräte aus, und verteilen Sie sie an Benutzer. Wenn die Benutzer die Geräte einschalten, wird der Setup-Assistent gestartet.



### <a name="see-also"></a>Siehe auch
[Voraussetzungen für die Registrierung von Geräten](prerequisites-for-enrollment.md)
