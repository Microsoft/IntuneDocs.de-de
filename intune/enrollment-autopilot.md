---
title: Registrieren von Geräten mithilfe von AutoPilot
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Windows 10-Geräte mithilfe des Windows AutoPilot registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: 4c268f9061ae624c1f85e386e5633b14334860b7
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313137"
---
# <a name="enroll-windows-devices-by-using-the-windows-autopilot"></a>Registrieren von Windows-Geräten mithilfe des Windows AutoPilot
Windows AutoPilot vereinfacht die Bereitstellung von Geräten. Das Erstellen und Warten von benutzerdefinierten Images des Betriebssystems ist ein langwieriger Prozess. Es kann ebenfalls Zeit in Anspruch nehmen, diese benutzerdefinierten Images von Betriebssystemen auf neue Geräte anzuwenden, um diese für die Verwendung vorzubereiten, bevor Sie sie Ihren Benutzern zur Verfügung stellen. Mit Microsoft Intune und AutoPilot können Sie Ihren Benutzern neue Geräte geben, ohne die benutzerdefinierten Images des Betriebssystems auf den Geräten erstellen, verwalten und auf diese anwenden zu müssen. Wenn Sie Intune zum Verwalten von AutoPilot-Geräten verwenden, können Sie Richtlinien, Profile und Apps usw. verwalten, nachdem diese registriert sind. Eine Übersicht über die Vorteile, Szenarios und Voraussetzungen finden Sie unter [Overview of Windows AutoPilot (Übersicht über Windows AutoPilot)](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

## <a name="prerequisites"></a>Voraussetzungen
- [Die automatische Windows-Registrierung muss aktiviert sein](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment).
- [Azure Active Directory Premium-Abonnement](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="add-devices"></a>Hinzufügen von Geräten

Sie können Windows AutoPilot-Geräte durch Importieren einer CSV-Datei mit ihren Informationen hinzufügen.

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Windows-Registrierung** > **Geräte** > **Importieren** aus.

    ![Screenshot von Windows AutoPilot-Geräten](media/enrollment-autopilot/autopilot-import-device.png)

2. Navigieren Sie unter **Windows AutoPilot-Geräte hinzufügen** zu einer CSV-Datei, die allen Geräte aufführt, die Sie hinzufügen möchten. Die Datei sollte die Seriennummern, Windows-Produkt-IDs, Hardware-Hashes und optionale Bestell-IDs der Geräte enthalten.

    ![Screenshot des Hinzufügens von Windows AutoPilot-Geräten](media/enrollment-autopilot/autopilot-import-device2.png)

3. Wählen Sie **Importieren** aus, um mit dem Importieren von Informationen zu den Geräten zu beginnen. Der Import kann mehrere Minuten dauern.

4. Nachdem der Importvorgang abgeschlossen ist, wählen Sie **Geräteregistrierung** > **Windows-Registrierung** > **Windows AutoPilot** >  **Geräte** > **Synchronisieren**. Eine Meldung zeigt an, dass die Synchronisierung ausgeführt wird. Der Prozess kann ein paar Minuten in Anspruch nehmen, je nachdem, wie viele Geräte synchronisiert werden.

5. Aktualisieren Sie die Ansicht, um neue Geräte anzuzeigen.

## <a name="create-an-autopilot-device-group"></a>Erstellen einer AutoPilot-Gerätegruppe

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Option **Gruppen** aus.
2. Auf dem Blatt **Gruppe**:
    1. Wählen Sie für **Gruppentyp** die Option **Sicherheit**.
    2. Geben Sie einen **Gruppennamen** und eine **Gruppenbeschreibung** ein.
    3. Für **Mitgliedschaftstyp** wählen Sie entweder **Zugewiesen** oder **Dynamisches Gerät**.
3. Wenn Sie **Zugewiesen** als **Mitgliedschaftstyp** im vorherigen Schritt ausgewählt haben, wählen Sie anschließend auf dem Blatt **Gruppe** die Option **Mitglieder**, und fügen Sie AutoPilot Geräte zur Gruppe hinzu.
    AutoPilot-Geräte, die noch nicht registriert sind, sind Geräte, deren Name der Seriennummer des Geräts entspricht.
4. Wenn Sie oben **Dynamisches Geräte** als **Mitgliedschaftstyp** ausgewählt haben,wählen Sie anschließend auf dem Blatt **Gruppe** die Option **Dynamische Gerätemitglieder**, und geben Sie einen der folgenden Codes in das Feld **Erweiterte Regel** ein.
    - Wenn Sie eine Gruppe mit all Ihren AutoPilot-Geräten erstellen möchten, geben Sie `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")` ein.
    - Wenn Sie eine Gruppe mit all Ihren AutoPilot-Geräten mit einer bestimmten Bestell-ID erstellen möchten, geben Sie `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") ` ein.
    - Wenn Sie eine Gruppe mit all Ihren AutoPilot-Geräten mit einer bestimmten Bestellungs-ID erstellen möchten, geben Sie `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")` ein.
    
    Wählen Sie nach dem Hinzufügen des Codes im Feld **Erweiterte Regel** die Option **Speichern**.
5. Wählen Sie **Erstellen** aus.



## <a name="create-an-autopilot-deployment-profile"></a>Erstellen eines AutoPilot-Bereitstellungsprofils
AutoPilot-Bereitstellungsprofile werden verwendet, um die AutoPilot-Geräte zu konfigurieren.
1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofil** > **Profil erstellen** aus.
2. Geben Sie einen **Namen** und optional eine **Beschreibung** ein.
3. Für **Bereitstellungsmodus** wählen Sie eine der beiden folgenden Optionen:
    - **Benutzergesteuert**: Geräte mit diesem Profil werden dem Benutzer zugeordnet, der das Gerät registriert. Für die Bereitstellung des Geräts sind Anmeldeinformationen erforderlich.
    - **Selbstbereitstellend (Vorschauversion)**: (Windows 10 Insider Preview Build 17672 oder höher) Geräte mit diesem Profil werden nicht dem Benutzer zugeordnet, der das Gerät registriert. Für die Bereitstellung des Geräts sind keine Anmeldeinformationen erforderlich.
4. Wählen Sie im Feld **Verknüpfen mit Azure AD als** die Option **In Azure AD eingebunden**.
5. Wählen Sie **Willkommensseite**, konfigurieren Sie die folgenden Optionen, und wählen Sie **Speichern**:
    - ** Sprache (Region) ***: Wählen Sie die Sprache, die für das Gerät verwendet werden soll. Diese Option ist nur verfügbar, wenn Sie **Selbstbereitstellend** als **Bereitstellungsmodus** ausgewählt haben.
    - **Tastatur automatisch konfigurieren:*** Wenn eine **Sprache (Region)** ausgewählt ist, können Sie mit **Ja** die Tastaturauswahlseite überspringen. Diese Option ist nur verfügbar, wenn Sie **Selbstbereitstellend** als **Bereitstellungsmodus** ausgewählt haben.
    - **Lizenzbedingungen**: (Windows 10, Version 1709 oder höher) Wählen Sie, ob die Lizenzbedingungen den Benutzern angezeigt werden sollen.
    - **Datenschutzeinstellungen**: Wählen Sie aus, ob die Datenschutzeinstellungen den Benutzern angezeigt werden sollen.
    - **Optionen zum Ändern des Kontos ausblenden (nur Windows Insider):** Wählen Sie **Ausblenden** aus, um zu verhindern, dass Optionen zum Ändern des Kontos auf der Anmeldeseite des Unternehmens und den Domänenfehlerseiten angezeigt werden. Für diese Option muss das [Unternehmensbranding in Azure Active Directory konfiguriert](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) sein.
    - **Benutzerkontotyp**: Wählen Sie, ob der Kontotyp des Benutzers **Administrator** oder **Standardbenutzer** sein soll.
    - **Vorlage für den Computernamen anwenden (nur Windows Insider)**: Klicken Sie auf **Ja**, um eine Vorlage für die Benennung eines Geräts während der Bereitstellung zu erstellen. Namen dürfen höchstens 15 Zeichen lang sein und können Buchstaben, Zahlen und Bindestriche enthalten. Ein Name darf nicht nur aus Zahlen bestehen. Verwenden Sie das [%SERIAL%-Makro](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp), um eine hardwarespezifische Seriennummer hinzuzufügen. Verwenden Sie alternativ das [%RAND:x%-Makro](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) um eine zufällige Zeichenfolge von Zahlen hinzuzufügen, bei der x der Anzahl der hinzuzufügenden Ziffern entspricht. 

6. Wählen Sie **Erstellen** aus, um das Profil zu erstellen. Das AutoPilot-Bereitstellungsprofil ist nun verfügbar und kann Geräten zugewiesen werden.

* Sowohl **Sprache (Region)** als auch **Tastatur automatisch konfigurieren** sind nur verfügbar, wenn **Selbstbereitstellend (Vorschauversion)** für den **Bereitstellungsmodus**  (Windows 10 Insider Preview Build 17672 oder höher) ausgewählt ist.


## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Zuweisen eines AutoPilot-Bereitstellungsprofils zu einer Gerätegruppe

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofil** ein Profil aus.
2. Wählen Sie auf dem entsprechenden Profilblatt die Option **Zuweisungen**. 
3. Wählen Sie **Gruppen auswählen** und dann auf dem Blatt **Gruppen auswählen** die Gruppe(n), die Sie dem Profil zuweisen möchten, und wählen Sie anschließend **Auswählen**.

## <a name="edit-an-autopilot-deployment-profile"></a>Bearbeiten eines AutoPilot-Bereitstellungsprofils
Nachdem Sie ein AutoPilot-Bereitstellungsprofil erstellt haben, können Sie bestimmte Teile des Bereitstellungsprofils bearbeiten.   

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Option **Geräteregistrierung** aus.
2. Wählen Sie unter **Windows-Registrierung** im Abschnitt **Windows AutoPilot** die Option **Bereitstellungsprofile**.
3. Wählen Sie das Profil aus, das Sie bearbeiten möchten.
4. Klicken Sie auf der linken Seite auf **Eigenschaften**, um den Namen oder die Beschreibung des Bereitstellungsprofils zu ändern. Klicken Sie auf **Speichern**, wenn Sie Änderungen vorgenommen haben.
5. Klicken Sie auf **Einstellungen**, um Änderungen an den OOBE-Einstellungen vorzunehmen. Klicken Sie auf **Speichern**, wenn Sie Änderungen vorgenommen haben.

> [!NOTE]
> Änderungen am Profil werden für die diesem Profil zugewiesenen Geräte angewendet. Das aktualisierte Profil wird jedoch nicht auf ein Gerät angewendet, das bereits bei Intune registriert ist, bis das Gerät zurückgesetzt und erneut registriert wurde.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Warnungen für nicht zugewiesene Windows AutoPilot-Geräte <!-- 163236 -->
Sie können eine Warnung anzeigen, um zu sehen, wie vielen Geräten aus dem AutoPilot-Programm keine AutoPilot-Bereitstellungsprofile zugewiesen wurden. Verwenden Sie die Informationen aus der Warnung, um Profile zu erstellen und sie den nicht zugeordneten Geräten zuzuweisen. Wenn Sie auf die Warnung klicken, sehen Sie die vollständige Liste der Windows AutoPilot-Geräte zusammen mit detaillierten Informationen.

Um Warnungen für nicht zugewiesene Geräte anzuzeigen, wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Übersicht** > **Nicht zugewiesene Geräte**.  


## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Hinzufügen eines Benutzers zu einem bestimmten Autopilot-Gerät

Sie können einen Benutzer zu einem bestimmten Autopilot-Gerät hinzufügen. Durch diese Zuweisung werden während der Windows-Einrichtung auf der [unternehmensspezifischen](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) Anmeldeseite schon vorab die Informationen für einen Benutzer eingetragen, der in Azure Active Directory verwaltet wird. Sie können auch eine benutzerdefinierte Begrüßung festlegen. Dadurch wird die Windows-Anmeldung nicht vorab ausgefüllt. Nur lizenzierte Intune-Benutzer können so zugewiesen werden.

Voraussetzung: das Azure Active Directory-Unternehmensportal wurde konfiguriert.

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Windows-Registrierung** > **Geräte** aus, wählen Sie anschließend das Gerät aus, und klicken Sie auf **Benutzer zuweisen**.
    ![Screenshot von „Benutzer zuweisen“](media/enrollment-autopilot/assign-user.png)
2. Wählen Sie einen für Intune lizenzierten Azure-Benutzer aus, und klicken Sie auf **Auswählen**.
    ![Screenshot der Benutzerauswahl](media/enrollment-autopilot/select-user.png)
3. Geben Sie im Feld **User Friendly Name** (Anzeigename) einen Anzeigenamen ein, oder akzeptieren Sie die Standardeinstellung. Dies ist der Anzeigename, der angezeigt wird, wenn sich der Benutzer während der Windows-Einrichtung anmeldet.
    ![Screenshot des Anzeigenamens](media/enrollment-autopilot/friendly-name.png)
4. Klicken Sie auf **OK**.


## <a name="delete-autopilot-devices"></a>Löschen von AutoPilot-Geräten

Sie können Windows AutoPilot-Geräte löschen, die nicht registriert sind.

1. Wenn Geräte bei Intune registriert sind, müssen Sie sie zunächst [aus Azure Active Directory-Portal löschen](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Windows-Registrierung** > **Geräte** aus.

3. Wählen Sie unter **Windows AutoPilot-Geräte** die Geräte aus, die Sie löschen möchten, und wählen Sie dann **Löschen**.

4. Bestätigen Sie den Löschvorgang mit **Ja**. Der Löschvorgang kann einige Minuten dauern.

## <a name="using-autopilot-in-other-portals"></a>Verwenden von AutoPilot in anderen Portalen
Wenn die mobile Geräteverwaltung für Sie nicht von Interesse ist, können Sie AutoPilot beispielsweise in Microsoft Store für Unternehmen verwenden. Die Verwendung von anderen Portalen ist ebenfalls möglich, es wird jedoch empfohlen, ausschließlich Intune zum Verwalten Ihrer AutoPilot-Bereitstellungen zu verwenden. Wenn Sie Intune und ein anderes Portal verwenden, kann Intune folgende Funktionen nicht verwenden:
- Anzeigen von Änderungen an Profilen, die in Intune erstellt, aber in einem anderen Portal bearbeitet wurden
- Synchronisieren von Profilen, die in einem anderen Portal erstellt wurden
- Anzeigen von Profilzuweisungen, die in einem anderen Portal vorgenommen wurden
- Synchronisieren von Profilzuweisungen, die in einem anderen Portal vorgenommen wurden
- Anzeigen von Änderungen an der Geräteliste, die in einem anderen Portal vorgenommen wurden

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie Windows AutoPilot für registrierte Windows 10-Geräte konfiguriert haben, erfahren Sie mehr über die Verwaltung dieser Geräte. Weitere Informationen finden Sie unter [Was ist die Microsoft Intune-Geräteverwaltung?](https://docs.microsoft.com/intune/device-management).
