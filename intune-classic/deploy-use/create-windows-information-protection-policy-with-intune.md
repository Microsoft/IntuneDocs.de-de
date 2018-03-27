---
title: Erstellen und Bereitstellen von WIP-App-Schutzrichtlinien (Windows Information Protection) in Intune
description: Erstellen und Bereitstellen von WIP-App-Schutzrichtlinien in Intune
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 9/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 51e53e28-5c34-4d0f-a4b1-6390a337514c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 34e3112141e8bc0125ae320fa7ab8093d3b4ffc5
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Erstellen und Bereitstellen von WIP-App-Schutzrichtlinien (Windows Information Protection) in Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Ab Version Intune 1704 können Sie bei Windows 10 App-Schutzrichtlinien ohne Registrierungsszenario in der mobilen Anwendungsverwaltung (Mobile Application Management, MAM) verwenden.

## <a name="before-you-begin"></a>Vorbereitung

Sprechen Sie wir über einige Konzepte, wenn Sie eine WIP-Richtlinie hinzufügen.

### <a name="list-of-allowed-and-exempt-apps"></a>Liste der zulässigen und ausgenommenen Apps

-   **Zulässige Apps:** Dies sind die Apps, die dieser Richtlinie entsprechen müssen.

-   **Ausgenommene Apps:** Diese Apps sind von dieser Richtlinie ausgenommen und können ohne Einschränkungen auf Unternehmensdaten zugreifen.

### <a name="types-of-apps"></a>App-Typen

-   **Empfohlene Apps:** Eine vorab aufgefüllte Liste von Apps (hauptsächlich Microsoft Office), die Administratoren einen einfachen Import in die Richtlinie ermöglichen.

-   **Store-Apps:** Administratoren können eine beliebige App aus dem Windows Store in die Richtlinie einfügen.

-   **Windows Desktop-Apps:** Administratoren können traditionelle Windows Desktop-Apps der Richtlinie hinzufügen (z.B. .exe, .dll, usw.)

## <a name="pre-requisites"></a>Voraussetzungen

Sie müssen den MAM-Anbieter konfigurieren, bevor Sie eine WIP-App-Schutzrichtlinie erstellen können.

-   Weitere Informationen finden Sie unter [Konfigurieren Ihres MAM-Anbieters in Intune](/intune-classic/deploy-use/get-ready-to-configure-app-protection-policies-for-windows-10).

Darüber hinaus benötigen Sie Folgendes:

-   [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)-Lizenz
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP unterstützt nicht mehrere Identitäten; nur jeweils eine verwaltete Identität darf vorhanden sein.

## <a name="to-add-a-wip-policy"></a>Hinzufügen einer WIP-Richtlinie

Nachdem Sie in Ihrer Organisation Intune eingerichtet haben, können Sie eine WIP-spezifische Richtlinie durch das [Azure-Portal](/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies) erstellen.

1.  Wechseln Sie zum **Intune-Dashboard für die mobile Anwendungsverwaltung**, wählen Sie **Alle Einstellungen** und anschließend **App-Richtlinie** aus.

2.  Wählen Sie auf dem Blatt **App-Richtlinie** die Option **Richtlinie hinzufügen** aus und geben Sie folgende Werte ein:

    ein.  **Name:** Geben Sie einen Namen (Pflichtfeld) für Ihre neue Richtlinie ein.

    b.  **Beschreibung:** Geben Sie eine optionale Beschreibung ein.

    c.  **Plattform:** Wählen Sie **Windows 10** als unterstützte Plattform für Ihre App-Schutzrichtlinie aus.

    d.  **Registrierungsstatus:** Wählen Sie **Ohne Registrierung** als Registrierungsstatus für Ihre Richtlinie aus.

3.  Wählen Sie **Erstellen** aus. Die Richtlinie wird erstellt und in der Tabelle auf dem Blatt **App-Richtlinie** angezeigt.

## <a name="to-add-recommended-apps-to-your-allowed-apps-list"></a>Hinzufügen von empfohlenen Apps zur Liste der zulässigen Apps

1.  Wählen Sie auf dem Blatt **App-Richtlinie** den Namen Ihrer Richtlinie und anschließend die Option **Zulässige Apps** auf dem Blatt **Richtlinie hinzufügen** aus. Das Blatt **Zulässige Apps** wird geöffnet, auf dem alle Apps angezeigt werden, die bereits in der Liste für diese App-Schutzrichtlinie enthalten sind.

2.  Wählen Sie auf dem Blatt **Zulässige Apps** die Option **Apps hinzufügen** aus. Das Blatt **Apps hinzufügen** wird geöffnet, auf dem alle zu dieser Liste gehörenden Apps angezeigt werden.

3.  Wählen Sie alle Apps aus, die auf Ihre Unternehmensdaten zugreifen dürfen, und wählen Sie dann **OK** aus. Das Blatt **Zulässige Apps** wird aktualisiert und zeigt alle ausgewählten Apps an.

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>Hinzufügen einer Store-App zur Liste der zulässigen Apps

**Hinzufügen eine Store-App**

1.  Wählen Sie auf dem Blatt **App-Richtlinie** den Namen Ihrer Richtlinie und im angezeigten Menü **Zulässige Apps** aus. Daraufhin werden alle Apps angezeigt, die bereits in der Liste für diese App-Schutzrichtlinie enthalten sind.

2.  Wählen Sie auf dem Blatt **Zulässige Apps** die Option **Apps hinzufügen** aus.

3.  Wählen Sie auf dem Blatt **Apps hinzufügen** die Option **Store-Apps** aus der Dropdownliste aus. Auf dem Blatt werden dann Felder angezeigt, mit denen Sie einen **Herausgeber** und App-**Namen** hinzufügen können.

4.  Geben Sie den Namen der App und des jeweiligen Herausgebers ein und wählen Sie dann **OK** aus.

    > [!TIP]
    > Im Folgenden wird ein Beispiel für eine App gezeigt: Der **Herausgeber** ist dabei *CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S = Washington, C = US* und der **Name** des Produkts lautet *Microsoft.MicrosoftAppForWindows*.

5.  Nachdem Sie die Informationen in die Felder eingegeben haben, wählen Sie **OK** aus, um die App zur Liste **Zulässige Apps** hinzuzufügen.

> [!NOTE]
> Um mehrere Store-Apps gleichzeitig hinzuzufügen, können Sie auf das Menü **(...)** am Ende der App-Zeile klicken. Anschließend können Sie weitere Apps hinzufügen. Wenn Sie fertig sind, wählen Sie **OK** aus.

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>Hinzufügen einer Desktop-App zur Liste der zulässigen Apps

**Hinzufügen einer Desktop-App**

1.  Wählen Sie auf dem Blatt **App-Richtlinie** den Namen Ihrer Richtlinie und anschließend die Option **Zulässige Apps** aus. Das Blatt **Zulässige Apps** wird geöffnet, auf dem alle Apps angezeigt werden, die bereits in der Liste für diese App-Schutzrichtlinie enthalten sind.

2.  Wählen Sie auf dem Blatt **Zulässige Apps** die Option **Apps hinzufügen** aus.

3.  Wählen Sie auf dem Blatt **Apps hinzufügen** die Option **Desktop-Apps** aus der Dropdownliste aus.

4.  Nachdem Sie die Informationen in die Felder eingegeben haben, wählen Sie **OK** aus, um die App zur Liste **Zulässige Apps** hinzuzufügen.

> [!NOTE]
> Um mehrere **Desktop-Apps** gleichzeitig hinzuzufügen, können Sie auf das Menü **(...)** am Ende der App-Zeile klicken. Anschließend können Sie weitere Apps hinzufügen. Wenn Sie fertig sind, wählen Sie **OK** aus.

## <a name="windows-information-protection-wip-learning"></a>WIP Learning (Windows Information Protection)

Nachdem Sie die Apps hinzugefügt haben, die durch WIP geschützt werden sollen, müssen Sie mittels **WIP Learning** einen Schutzmodus anwenden.

### <a name="before-you-begin"></a>Vorbereitung

WIP Learning (Windows Information Protection) ist ein Bericht, mit dem Administratoren ihre für WIP unbekannten Apps überwachen können. Unbekannte Apps sind Apps, die nicht von der IT-Abteilung Ihrer Organisation bereitgestellt wurden. Administratoren können diese Apps vor der Erzwingung von WIP im Modus „Außerkraftsetzungen ausblenden“ über den Bericht exportieren und zu ihren WIP-Richtlinien hinzufügen, um Produktivitätseinbußen zu verhindern.

Es wird empfohlen, mit **Automatisch** oder **Außerkraftsetzungen zulassen** zu beginnen und bei einer kleinen Gruppe zu überprüfen, ob die Liste der zulässigen Apps die richtigen Apps enthält. Wenn Sie fertig sind, können Sie Ihre endgültige Erzwingungsrichtlinie in **Außerkraftsetzungen ausblenden** ändern.

#### <a name="what-the-protection-modes-are"></a>Welche Schutzmodi sind verfügbar?

- **Außerkraftsetzungen ausblenden:**
    - WIP prüft auf ungeeignete Datenfreigabeverfahren und hindert den Benutzer an der Durchführung der Aktion.
    - Dies kann die Freigabe von Informationen über nicht geschützte Unternehmens-Apps hinweg sowie die Freigabe von Unternehmensdaten zwischen anderen Personen und Geräten außerhalb Ihrer Organisation einschließen.
<br></br>

- **Außerkraftsetzungen zulassen:**
    - WIP prüft auf ungeeignete Datenfreigabeverfahren, bei dem Benutzer gewarnt werden, wenn sie einen potenziell unsicheren Vorgang durchführen.
    - In diesem Modus können Benutzer jedoch die Richtlinie überschreiben und die Daten freigeben. Die Aktion wird dabei in Ihrem Überwachungsprotokoll protokolliert.
<br></br>
- **Automatisch:**
    - WIP wird automatisch ausgeführt, wobei ungeeignete Datenfreigabeverfahren protokolliert werden. Dabei werden im Modus „Außerkraftsetzungen zulassen“ keine Vorgänge blockiert, die zu einer Mitarbeiterinteraktion auffordern würden.
    - Unzulässige Aktionen wie bei Apps, die unzulässigerweise versuchen, auf eine Netzwerkressource oder auf WIP-geschützte Daten zuzugreifen, werden trotzdem angehalten.
<br></br>
- **Aus (nicht empfohlen):**
    - WIP ist deaktiviert und unterstützt nicht beim Schutz oder der Überwachung Ihrer Daten.
    - Nachdem Sie WIP deaktiviert haben, wird versucht, WIP-getaggte Dateien auf den lokalen Laufwerken zu entschlüsseln. Denken Sie daran, dass Ihre vorherigen Informationen zu Entschlüsselungen und Richtlinien nicht automatisch erneut angewendet werden, wenn Sie den WIP-Schutz wieder aktivieren.

### <a name="to-add-a-protection-mode"></a>Hinzufügen eines Schutzmodus

1.  Wählen Sie auf dem Blatt **App-Richtlinie** den Namen Ihrer Richtlinie und anschließend die Option **Erforderliche Einstellungen** auf dem Blatt **Richtlinie hinzufügen** aus.

    ![Screenshot des Learning-Modus](../media/AppManagement/learning-mode-sc1.png)

1.  Wählen Sie **Speichern** aus.

### <a name="to-use-wip-learning"></a>Verwenden von WIP Learning

1. Navigieren Sie zum Azure-Dashboard.

2. Wählen Sie im linken Menü **Weitere Dienste** aus, und geben Sie in das Filtertextfeld die Zeichenfolge **Intune** ein.

3. Wählen Sie **Intune** aus. Daraufhin wird das **Intune-Dashboard** geöffnet. Wählen Sie dann **Mobile Apps** aus.

4. Wählen Sie im Abschnitt **Überwachung** die Option **WIP Learning** aus. Es werden die unbekannten Apps angezeigt, die von WIP Learning protokolliert wurden.

> [!IMPORTANT]
> Wenn die Apps im WIP Learning-Protokollierungsbericht angezeigt werden, können Sie sie in Ihre App Schutzrichtlinien importieren.

## <a name="to-deploy-your-wip-app-protection-policy"></a>Bereitstellen der WIP-App-Schutzrichtlinie

> [!IMPORTANT]
> Dies gilt für WIP mit mobiler Anwendungsverwaltung (MAM) ohne Registrierungsszenario.

Nachdem Sie Ihre WIP-App-Schutzrichtlinie erstellt haben, müssen Sie sie Ihrer Organisation über MAM bereitstellen.

1.  Wählen Sie auf dem Blatt **App Richtlinie** die neu erstellte App-Schutzrichtlinie aus. Wählen Sie anschließend **Benutzergruppen** und **Benutzergruppe hinzufügen** aus.

    Auf dem Blatt **Benutzergruppe hinzufügen** wird eine Liste von Benutzergruppen geöffnet, die aus allen Sicherheitsgruppen in Azure Active Directory besteht.

1.  Wählen Sie die Gruppe aus, auf die Ihre Richtlinie angewendet werden soll, und klicken Sie dann auf **Auswählen**, um die Richtlinie bereitzustellen.
