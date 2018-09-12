---
title: Erstellen und Bereitstellen von WIP-App-Schutzrichtlinien (Windows Information Protection)
titlesuffix: Microsoft Intune
description: Erstellen und Bereitstellen von WIP-App-Schutzrichtlinien (Windows Information Protection) in Microsoft Intune
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 425dce514d9cf0288a5e84ef5fa89790e6cee8be
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347306"
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Erstellen und Bereitstellen von WIP-App-Schutzrichtlinien (Windows Information Protection) in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Sie können App-Schutzrichtlinien bei Windows 10-Apps verwenden, um Apps ohne Geräteregistrierung zu schützen.

## <a name="before-you-begin"></a>Vorbereitung

Sie müssen mit einigen Konzepten vertraut sein, wenn Sie eine WIP-Richtlinie hinzufügen:

### <a name="list-of-allowed-and-exempt-apps"></a>Liste der zulässigen und ausgenommenen Apps

-   **Geschützte Apps:** Diese Apps müssen dieser Richtlinie entsprechen.

-   **Ausgenommene Apps:** Diese Apps sind von dieser Richtlinie ausgenommen und können ohne Einschränkungen auf Unternehmensdaten zugreifen.

### <a name="types-of-apps"></a>App-Typen

-   **Empfohlene Apps** Eine vorab aufgefüllte Liste von Apps (hauptsächlich Microsoft Office), die Ihnen einen einfachen Import in die Richtlinie ermöglicht.
-   **Store-Apps:** Sie können der Richtlinie eine beliebige App aus dem Windows Store hinzufügen.
-   **Windows Desktop-Apps:** Sie haben außerdem die Möglichkeit,der Richtlinie traditionelle Windows Desktop-Apps hinzufügen (z.B. .exe, .dll, usw.)

## <a name="prerequisites"></a>Voraussetzungen

Sie müssen den MAM-Anbieter konfigurieren, bevor Sie eine WIP-App-Schutzrichtlinie erstellen können. Weitere Informationen finden Sie unter [Konfigurieren Ihres MAM-Anbieters in Intune](app-protection-policies-configure-windows-10.md).

Darüber hinaus benötigen Sie folgende Lizenz und folgendes Update:

-   [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)-Lizenz
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP unterstützt nicht mehrere Identitäten; nur jeweils eine verwaltete Identität darf vorhanden sein.

## <a name="to-add-a-wip-app-protection-policy"></a>So erstellen Sie eine WIP-App-Schutzrichtlinie

Nachdem Sie Intune in Ihrer Organisation eingerichtet haben, können Sie eine WIP-spezifische Richtlinie erstellen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**.
3. Wählen Sie auf dem Blatt **Microsoft Intune** die Option **Client-Apps** aus.
4. Wählen Sie auf dem Blatt **Client-Apps** die Option **App-Schutzrichtlinien** aus.
5. Klicken Sie auf **Richtlinie hinzufügen**, um das Blatt **Richtlinie hinzufügen** anzuzeigen.
6. Fügen Sie die folgenden Werte hinzu:
    - **Name:** Geben Sie einen Namen (Pflichtfeld) für Ihre neue Richtlinie ein.
    - **Beschreibung**: Geben Sie eine Beschreibung ein (optional).
    - **Plattform:** Wählen Sie **Windows 10** als unterstützte Plattform für Ihre App-Schutzrichtlinie aus.
    - **Registrierungsstatus:** Wählen Sie **Ohne Registrierung** als Registrierungsstatus für Ihre Richtlinie aus.
7.  Wählen Sie **Erstellen** aus. Die Richtlinie wird erstellt und in der Tabelle auf dem Blatt **App-Schutzrichtlinien** angezeigt.

## <a name="to-add-recommended-apps-to-your-protected-apps-list"></a>Hinzufügen von empfohlenen Apps zur Liste der geschützten Apps

1. Wählen Sie auf dem Blatt **Microsoft Intune** die Option **Client-Apps** aus.
2. Wählen Sie auf dem Blatt **Client-Apps** die Option **App-Schutzrichtlinien** aus.
3. Wählen Sie auf dem Blatt **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten. Das Blatt **Intune-App-Schutz** wird angezeigt.
4. Wählen Sie auf dem Blatt **Intune-App-Schutz** die Option **Geschützte Apps** aus. Das Blatt **Geschützte Apps** wird geöffnet und zeigt alle Apps an, die bereits in der Liste für diese App-Schutzrichtlinie enthalten sind.
5. Klicken Sie auf **Apps hinzufügen**. Die Informationen bei **Apps hinzufügen** zeigen eine gefilterte Liste von Apps. Mit der Liste im oberen Bereich des Blatts können Sie den Listenfilter ändern.
6. Wählen Sie alle Apps aus, denen Sie Zugriff auf Ihre Unternehmensdaten gewähren möchten.
7. Klicken Sie auf **OK**. Das Blatt **Geschützte Apps** wird aktualisiert und zeigt alle ausgewählten Apps an.
8. Klicken Sie auf **Speichern**.

## <a name="add-a-store-app-to-your-protected-apps-list"></a>Hinzufügen einer Store-App zur Liste der geschützten Apps

**Hinzufügen eine Store-App**
1. Wählen Sie auf dem Blatt **Microsoft Intune** die Option **Client-Apps** aus.
2. Wählen Sie auf dem Blatt **Client-Apps** die Option **App-Schutzrichtlinien** aus.
3. Wählen Sie auf dem Blatt **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten. Das Blatt **Intune-App-Schutz** wird angezeigt.
4. Wählen Sie auf dem Blatt **Intune-App-Schutz** die Option **Geschützte Apps** aus. Das Blatt **Geschützte Apps** wird geöffnet und zeigt alle Apps an, die bereits in der Liste für diese App-Schutzrichtlinie enthalten sind.
5. Klicken Sie auf **Apps hinzufügen**. Die Informationen bei **Apps hinzufügen** zeigen eine gefilterte Liste von Apps. Mit der Liste im oberen Bereich des Blatts können Sie den Listenfilter ändern.
6. Wählen Sie **Store-Apps** aus der Liste aus.
7. Geben Sie Werte für **Name**, **Herausgeber**, **Produktname** und **Aktion** ein. Stellen Sie sicher, dass der Wert für **Aktion** auf **Zulassen** festgelegt ist, damit die App auf Ihre Unternehmensdaten zugreifen kann.
9. Klicken Sie auf **OK**. Das Blatt **Geschützte Apps** wird aktualisiert und zeigt alle ausgewählten Apps an.
10. Klicken Sie auf **Speichern**.

## <a name="add-a-desktop-app-to-your-protected-apps-list"></a>Hinzufügen einer Desktop-App zur Liste der geschützten Apps

**So fügen Sie eine Desktop-App hinzu**
1. Wählen Sie auf dem Blatt **Microsoft Intune** die Option **Client-Apps** aus.
2. Wählen Sie auf dem Blatt **Client-Apps** die Option **App-Schutzrichtlinien** aus.
3. Wählen Sie auf dem Blatt **App-Schutzrichtlinien** die Richtlinie aus, die Sie ändern möchten. Das Blatt **Intune-App-Schutz** wird angezeigt.
4. Wählen Sie auf dem Blatt **Intune-App-Schutz** die Option **Geschützte Apps** aus. Das Blatt **Geschützte Apps** wird geöffnet und zeigt alle Apps an, die bereits in der Liste für diese App-Schutzrichtlinie enthalten sind.
5. Klicken Sie auf **Apps hinzufügen**. Die Informationen bei **Apps hinzufügen** zeigen eine gefilterte Liste von Apps. Mit der Liste im oberen Bereich des Blatts können Sie den Listenfilter ändern.
6. Wählen Sie **Desktop-Apps** aus der Liste aus.
7. Geben Sie Werte für **Name**, **Herausgeber**, **Produktname**, **Datei**, **Mindestversion**, **Maximale Version** und **Aktion** ein. Stellen Sie sicher, dass der Wert für **Aktion** auf **Zulassen** festgelegt ist, damit die App auf Ihre Unternehmensdaten zugreifen kann.
9. Klicken Sie auf **OK**. Das Blatt **Geschützte Apps** wird aktualisiert und zeigt alle ausgewählten Apps an.
10. Klicken Sie auf **Speichern**.

## <a name="wip-learning"></a>WIP Learning
Nachdem Sie die Apps hinzugefügt haben, die durch WIP geschützt werden sollen, müssen Sie mittels **WIP Learning** einen Schutzmodus anwenden.

### <a name="before-you-begin"></a>Vorbereitung

WIP Learning ist ein Bericht, mit dem Sie Ihre WIP-tauglichen und WIP-unbekannten Apps überwachen können. Unbekannte Apps sind Apps, die nicht von der IT-Abteilung Ihrer Organisation bereitgestellt wurden. Sie können diese Apps vor der Erzwingung von WIP im Modus „Blockieren“ über den Bericht exportieren und zu Ihren WIP-Richtlinien hinzufügen, um Produktivitätseinbußen zu verhindern.

<!-- 1631908 --> Neben der Anzeige von Informationen über WIP-fähige Apps können Sie eine Zusammenfassung der Geräte anzeigen, die Arbeitsdaten für Websites freigegeben haben. Anhand dieser Informationen können Sie festlegen, welche Websites zu WIP-Gruppen- und Benutzerrichtlinien hinzugefügt werden sollen. Die Zusammenfassung zeigt, auf welche Website-URLs von WIP-aktivierten Apps zugegriffen werden kann.

Beim Arbeiten mit WIP-tauglichen und WIP-unbekannten Apps sollten Sie mit **Automatisch** oder **Außerkraftsetzungen zulassen** beginnen und bei einer kleinen Gruppe überprüfen, ob die Liste der geschützten Apps die richtigen Apps enthält. Wenn Sie fertig sind, können Sie Ihre endgültige Erzwingungsrichtlinie in **Blockieren** ändern.

### <a name="what-are-the-protection-modes"></a>Was sind Schutzmodi?

#### <a name="block"></a>Blockieren
WIP prüft auf ungeeignete Datenfreigabeverfahren und hindert den Benutzer an der Durchführung der Aktion. Dies kann die Freigabe von Informationen über nicht geschützte Unternehmens-Apps hinweg sowie die Freigabe von Unternehmensdaten zwischen anderen Personen und Geräten außerhalb Ihrer Organisation einschließen.

#### <a name="allow-overrides"></a>Außerkraftsetzungen zulassen
WIP prüft auf ungeeignete Datenfreigabeverfahren, bei dem Benutzer gewarnt werden, wenn sie einen potenziell unsicheren Vorgang durchführen. In diesem Modus können Benutzer jedoch die Richtlinie überschreiben und die Daten freigeben. Die Aktion wird dabei in Ihrem Überwachungsprotokoll protokolliert.

#### <a name="silent"></a>Automatisch
WIP wird automatisch ausgeführt, wobei ungeeignete Datenfreigabeverfahren protokolliert werden. Dabei werden im Modus „Außerkraftsetzungen zulassen“ keine Vorgänge blockiert, die zu einer Mitarbeiterinteraktion auffordern würden. Unzulässige Aktionen wie bei Apps, die unzulässigerweise versuchen, auf eine Netzwerkressource oder auf WIP-geschützte Daten zuzugreifen, werden trotzdem angehalten.

#### <a name="off-not-recommended"></a>Inaktiv (nicht empfohlen)
WIP ist deaktiviert und unterstützt nicht beim Schutz oder der Überwachung Ihrer Daten.

Nachdem Sie WIP deaktiviert haben, wird versucht, WIP-getaggte Dateien auf den lokalen Laufwerken zu entschlüsseln. Denken Sie daran, dass Ihre vorherigen Informationen zu Entschlüsselungen und Richtlinien nicht automatisch erneut angewendet werden, wenn Sie den WIP-Schutz wieder aktivieren.

### <a name="add-a-protection-mode"></a>Hinzufügen eines Schutzmodus

1.  Wählen Sie auf dem Blatt **App-Richtlinie** den Namen Ihrer Richtlinie und anschließend die Option **Erforderliche Einstellungen** aus.

    ![Screenshot des Learning-Modus](./media/learning-mode-sc1.png)

1.  Wählen Sie eine Einstellung aus, und klicken Sie auf **Speichern**.

### <a name="use-wip-learning"></a>Verwenden von WIP Learning

1. Öffnen Sie das [Azure-Portal](https://portal.azure.com). Wählen Sie **Alle Dienste** aus. Geben Sie **Intune** in das Filtertextfeld ein.

3. Wählen Sie **Intune** > **Client-Apps** aus.

4. Klicken Sie anschließend auf **Status des App-Schutzes** > **Berichte** > **Windows Information Protection-Tutorial**.  

    Wenn dann die Apps im WIP Learning-Protokollierungsbericht angezeigt werden, können Sie sie zu Ihren App-Schutzrichtlinien hinzufügen.

## <a name="allow-windows-search-indexer-to-search-encrypted-items"></a>Der Windows Search-Indexerstellung die Suche nach verschlüsselten Elementen gestatten
Hiermit wird die Indizierung von Elementen zugelassen oder verweigert. Diese Option ist für die Windows Search-Indexerstellung bestimmt und steuert, ob verschlüsselte Elemente wie beispielsweise WIP-geschützte Dateien (Windows Information Protection) indiziert werden.

Diese App-Schutzrichtlinienoption befindet sich in den **erweiterten Einstellungen** der WIP-Richtlinie (Windows Information Protection). Für die App-Schutzrichtlinie muss die *Windows 10*-Plattform und für die App-Richtlinie **Registrierungsstatus** muss **Mit Registrierung** festgelegt werden.

Wenn die Richtlinie aktiviert ist, werden WIP-geschützte Elemente indiziert und die zugehörigen Metadaten werden an einem nicht verschlüsselten Speicherort gespeichert. Die Metadaten umfassen beispielsweise den Dateipfad und das Änderungsdatum.

Wenn die Richtlinie deaktiviert ist, werden WIP-geschützte Elemente nicht indiziert und sie werden nicht in den Ergebnissen in Cortana oder im Datei-Explorer angezeigt. Ferner sind bei Fotos und Groove-Apps Leistungseinbußen möglich, wenn sich auf dem Gerät große Mengen an WIP-geschützten Mediendateien befinden.

## <a name="add-encrypted-file-extensions"></a>Hinzufügen von verschlüsselten Dateierweiterungen

Sie können nicht nur die Option **Der Windows Search-Indexerstellung die Suche nach verschlüsselten Elementen gestatten** festlegen, sondern auch eine Liste mit Dateierweiterungen angeben. Dateien mit diesen Erweiterungen werden beim Kopieren aus einer SMB-Freigabe innerhalb der Unternehmensgrenzen (gemäß Definition in der Liste mit Netzwerkstandorten) verschlüsselt. Wenn diese Richtlinie nicht festgelegt ist, wird das vorhandene Verhalten zur automatischen Verschlüsselung angewendet. Wenn diese Richtlinie konfiguriert ist, werden nur Dateien mit den in der Liste enthaltenen Erweiterungen verschlüsselt.

## <a name="deploy-your-wip-app-protection-policy"></a>Bereitstellen der WIP-App-Schutzrichtlinie

> [!IMPORTANT]
> Diese Informationen gelten für WIP ohne Geräteregistrierung.

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

Nachdem Sie Ihre WIP-App-Schutzrichtlinie erstellt haben, müssen Sie sie Ihrer Organisation über MAM bereitstellen.

1.  Wählen Sie auf dem Blatt **App-Richtlinie** die neu erstellte App-Schutzrichtlinie aus. Wählen Sie anschließend **Benutzergruppen** > **Benutzergruppe hinzufügen** aus.

    Auf dem Blatt **Benutzergruppe hinzufügen** wird eine Liste von Benutzergruppen geöffnet, die aus allen Sicherheitsgruppen in Azure Active Directory besteht.

2.  Wählen Sie die Gruppe aus, auf die Ihre Richtlinie angewendet werden soll, und klicken Sie dann auf **Auswählen**, um die Richtlinie bereitzustellen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Windows Information Protection finden Sie unter [Protect your enterprise data using Windows Information Protection (WIP) (Schützen Ihrer Unternehmensdaten mit Windows Information Protection (WIP))](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip).
