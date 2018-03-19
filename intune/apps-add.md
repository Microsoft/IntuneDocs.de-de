---
title: "Hinzufügen von Apps zu Microsoft Intune"
titlesuffix: 
description: "Erfahren Sie, wie Sie Apps zu Microsoft Intune hinzufügen, damit Sie sie Benutzern und Geräten zuweisen können. Intune unterstützt eine Vielzahl verschiedener App-Typen."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 91762eafbba5f96ce04f3ffd4d83f63434a3ac74
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>So fügen Sie eine App zu Microsoft Intune hinzu

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Bevor Sie Apps zuweisen, überwachen, konfigurieren oder schützen können, müssen Sie sie zu Intune hinzufügen. Intune unterstützt eine Vielzahl verschiedener App-Typen. Jeder App-Typ hat unterschiedliche Optionen.

Über Intune können Sie folgende App-Typen hinzufügen und zuweisen:
| App-Typ                                  | Installation                                                                  | Updates                       |
|------------------------------------------ |----------------------------------------------------------------------------   |---------------------------    |
| Apps im Web                           | Intune erstellt eine Verknüpfung zu der Web-App auf dem Startbildschirm des Geräts          | App-Updates werden automatisch ausgeführt     |
| Interne (branchenspezifische) Apps  | Intune installiert die App auf dem Gerät (Sie stellen die Installationsdatei zur Verfügung)    | Sie müssen ein Update für die App ausführen       |
| Apps aus dem Store                       | Intune installiert die App auf dem Gerät                                       | App-Updates werden automatisch ausgeführt     |
| Integrierte Apps                        | Intune installiert die App auf dem Gerät                                       | App-Updates werden automatisch ausgeführt     |


Neben Web-Apps unterstützt Intune die folgenden spezifischen Plattformen für Store-Apps und branchenspezifische Apps:
- Store-Apps
    - Android Store-Apps
    - iOS Store-Apps
    - Windows Phone 8.1 Store-Apps
    - Windows Store-Apps
    - Android for Work-Apps
    - Office 365-Apps für Windows
    - Office 365-Apps für macOS
- Erstellen Sie Ihre branchenspezifische App
    - Branchenspezifische Android-Apps
    - Branchenspezifische iOS-Apps
    - Branchenspezifische Windows Phone-Apps (XAP-Dateien)
    - Branchenspezifische Windows-Apps (nur MSI-Dateien)
- Integrierte Apps    

>[!TIP]
> Branchenspezifische Apps werden über eine App-Installationsdatei hinzugefügt. Fügen Sie beispielweise die Anwendung hinzu, um eine branchenspezifische iOS-App zu installieren, indem Sie auf dem Blatt **App hinzufügen** **Branchenspezifische App** als **App-Typ** auswählen. Wählen Sie dann die App-Paketdatei (mit der Erweiterung .ipa) aus. Solche Apps werden in der Regel intern geschrieben.

## <a name="assess-application-requirements"></a>Überprüfen von Anforderungen an Anwendungen 
Sie müssen als IT-Administrator nicht nur festlegen, welche Apps Ihre Gruppe verwenden soll, sondern auch die Funktionen bestimmen, die jede Gruppe bzw. Untergruppe benötigt. Sie müssen für jede App die benötigten Plattformen bestimmen und festlegen, welche Gruppe von Benutzern die App verwenden müssen, welche Konfigurationsrichtlinien für diese Gruppen gelten und welche Schutzrichtlinien angewendet werden sollen.  

Darüber hinaus müssen Sie bestimmen, ob Sie sich auf die Verwaltung mobiler Geräte (MDM) oder die Verwaltung mobiler Anwendungen (MAM) konzentrieren möchten. Es ist nützlich, Intune zur Verwaltung mobiler Geräte zu verwenden, wenn die folgenden Bedingungen zutreffen:
- Benutzer benötigen ein unternehmensinternes WLAN- oder VPN-Konnektivitätsprofil, damit sie produktiv arbeiten können.
- Benutzer benötigen mehrere Apps, die mit Push auf ihre Geräte übertragen werden.
- Ihre Organisation muss mit den vorgeschriebenen und anderen Richtlinien kompatibel sein, die bestimmte MDM-Steuerelemente wie die Sicherheit oder die Verschlüsselung aufrufen.

Es ist nützlich, Intune für die Verwaltung mobiler Anwendungen zu verwenden, ohne das Gerät zu verwalten, wenn die folgenden Bedingungen zutreffen:
- Sie möchten zulassen, dass Benutzer ihre eigenen Geräte verwenden (Bring Your Own Device, BYOD).
- Sie möchten ein einmaliges Popupelement zur Verfügung stellen, um die Benutzer darüber zu informieren, dass die MAM-Schutzfunktionen funktionieren, anstatt kontinuierlich Benachrichtigungen auf Geräteebene zu versenden.
- Sie möchten konform mit den Richtlinien handeln, die weniger Verwaltungsfunktionen auf persönlichen Geräten erfordern. Beispielsweise wenn Sie die Unternehmensdaten für die Apps verwalten möchten, anstatt die Unternehmensdaten für das gesamte Gerät zu verwalten.

Weitere Informationen finden Sie unter [Compare MDM and MAM (Vergleich von MDM und MAM)](byod-technology-decisions.md).

### <a name="determine-who-will-use-the-app"></a>Festlegen, wer die App verwendet
Nachdem Sie eine App in Intune hinzugefügt haben, weisen Sie eine Gruppe von Benutzern zu, die die App verwenden können. Zunächst müssen Sie die entsprechende Gruppe bestimmen, die auf der Grundlage der Vertraulichkeitsstufe der in der App enthaltenen Daten Zugriff auf die App haben sollen. Sie müssen möglicherweise bestimmte Rollentypen innerhalb Ihrer Organisation einschließen bzw. ausschließen. Beispielsweise kann es sein, dass für die Vertriebsgruppe nur bestimmte branchenspezifische Apps erforderlich sind, wohingegen Mitarbeiter, die im Zusammenhang mit der Technik, den Finanzen bzw. der Personal- oder Rechtsabteilung stehen, gar keine branchenspezifischen Apps verwenden müssen. Außerdem sind für die Vertriebsgruppe möglicherweise ein zusätzlicher Schutz von Daten und der Zugriff auf unternehmensinterne Dienste auf mobilen Geräten erforderlich. Sie müssen festlegen, wie diese Gruppe über die App eine Verbindung mit den Ressourcen herstellt. Sollen die Daten, auf die die App zugreift, in der Cloud oder lokal gespeichert werden? Außerdem müssen Sie festlegen, wie die Benutzer über die App eine Verbindung mit den Ressourcen herstellen. Neben E-Mails unterstützt Intune auch das Ermöglichen des Zugriffs auf mobile Apps, die den sicheren Zugriff auf lokale Daten erfordern, z.B. ein branchenspezifischer Anwendungsserver. Dieser Zugriffstyp erfolgt in der Regel mithilfe von [Zertifikaten die von Intune verwaltet werden](certificates-configure.md), in Kombination mit einem VPN-Standardgateway oder -proxy im Umkreis, z.B. dem Microsoft Azure Active Directory-Anwendungs-Proxy. Darüber hinaus können das [App Wrapping Tool und App SDK](apps-prepare-mobile-application-management.md) von Intune dabei helfen, dass die Daten, auf die zugegriffen wird, in der branchenspezifischen App verbleiben und diese App keine Unternehmensdaten an Verbraucher-Apps oder -Dienste übergeben kann.

Verwenden Sie das [Handbuch zur Bereitstellungs-, Entwurfs- und Implementierungsplanung für Intune](planning-guide.md), um zu ermitteln, wie Sie die Gruppen der Organisation identifizieren, die jedem App-Szenario für Anwendungsfälle und untergeordnete Anwendungsfälle zugewiesen sind. Weitere Informationen zum Zuweisen von Apps an Gruppen finden Sie unter [Zuweisen von Apps an Gruppen mit Microsoft Intune](apps-deploy.md). 

### <a name="determine-the-type-of-app-for-your-solution"></a>Bestimmen des App-Typs für Ihre Lösung
Sie können zwischen den folgenden App-Typen auswählen:
- **Apps im Web:** Bei einer Web-App handelt es sich um eine Client/Server-Anwendung. Der Server stellt die Web-App bereit, die die Benutzeroberfläche, den Inhalt und die Funktionen umfasst. Außerdem bieten moderne Webhostingplattformen häufig Vorteile bei Sicherheit und Lastenausgleich. Der App-Typ wird separat im Web verwaltet. Verwenden Sie Intune, um auf diesen App-Typ zu verweisen. Sie legen ebenfalls fest, welche Benutzergruppen auf diese App zugreifen können. Beachten Sie, dass Android keine Web-Apps unterstützt.
- **Interne (branchenspezifische) Apps:** Intern erstelle Apps gelten als branchenspezifische Apps. Die Funktionen dieses App-Typs wurden für eine der von Intune unterstützten Plattformen wie Windows, iOS oder Android erstellt. Ihre Organisation erstellt Updates als unabhängige Dateien und stellt sie für Sie bereit. Sie fügen dann mithilfe von Intune die Updates für die App-Benutzer hinzu und stellen sie bereit. 
- **Apps aus dem Store:** Bei Store-Apps handelt es sich um Apps, die im Windows-, iOS- oder Android-Store hochgeladen wurden. Der Anbieter der Store-App verwaltet die Updates für die App und stellt sie bereit. Wählen Sie die App aus der Store-Liste aus, und machen Sie sie mithilfe von Intune für alle Benutzer verfügbar.

Wenn Sie festlegen, welche Apps Ihre Organisation benötigt, überprüfen Sie, wie die Apps mit Clouddiensten zusammenarbeiten, auf welche Daten die App zugreift, ob die Apps für BYOD-Benutzer verfügbar sind und ob die Apps Internetzugriff erfordern.

Weitere Informationen zum Festlegen, welche App-Typen für Ihre Organisation erforderlich sind, finden Sie unter [Erstellen eines Entwurfs](planning-guide-design.md#feature-requirements) im Abschnitt **Featureanforderungen** unter **Apps**.

### <a name="understanding-app-management-and-protection-policies"></a>Grundlegendes zu Richtlinien zur Verwaltung und zum Schutz von Apps
Mithilfe von Intune können Sie die Funktionen der von Ihnen bereitgestellten Apps verändern, um sie an die Konformitäts- und Sicherheitsrichtlinien Ihres Unternehmens anzupassen. Dadurch können Sie auch bestimmen, wie die Daten Ihres Unternehmens geschützt werden sollen. Mit Intune verwaltete Apps verfügen über umfangreiche Richtlinien zum Schutz von mobilen Anwendungen. Dazu gehört z.B.:

- das Einschränken von Funktionen zum Kopieren und Einfügen und zum Speichern
- das Konfigurieren von Weblinks, sodass sie in der Intune Managed Browser-App geöffnet werden
- das Aktivieren der Unterstützung von mehreren Identitäten und des bedingten Zugriffs auf App-Ebene

Mit Intune verwaltete Apps können außerdem ohne Registrierung den App-Schutz aktivieren. Dadurch können Sie entscheiden, ob Sie Richtlinien zum Verhindern von Datenverlust anwenden möchten, ohne das Gerät des Benutzers zu verwalten. Ebenfalls können Sie die Verwaltung mobiler Apps in Ihre mobilen und branchenspezifischen Apps integrieren. Verwenden Sie dafür das Intune App SDK und das App Wrapping Tool. Weitere Informationen zu diesem Tool finden Sie unter [Übersicht über das Intune App SDK](app-sdk.md).

### <a name="understanding-licensed-apps"></a>Grundlegendes zu lizenzierten Apps
Es wird nicht nur zwischen Web-Apps, Store-Apps und branchenspezifischen Apps unterschieden, sondern auch zwischen Volume Purchase Program-Apps und lizenzierten Apps. Z.B.:     
- **Apple Volume Purchase Program for Business (iOS und MacOS):** Der App Store von iOS bietet die Möglichkeit, mehrere Lizenzen für eine App zu erwerben, die in Ihrem Unternehmen ausgeführt werden soll. Durch den Erwerb mehrerer Kopien können Sie Apps in Ihrem Unternehmen effizient verwalten. Weitere Informationen finden Sie unter [Verwalten von iOS-Apps, die per Volumenlizenz erworben wurden](vpp-apps-ios.md).
- **Android for Work:** Apps werden Android for Work-Geräten anders zugewiesen als Standard-Android-Geräten. Alle Apps, die für Android for Work installiert werden, stammen aus dem Google Play for Work Store. Melden Sie sich beim Store an, suchen Sie nach den gewünschten Apps, und genehmigen Sie diese. Anschließend wird die App im Knoten „Lizenzierte Apps“ des Azure-Portals angezeigt. Ab dann können Sie die Zuweisung der App auf dieselbe Weise wie bei jeder anderen App durchführen.
- **Windows Store für Unternehmen (Windows 10):** Im Microsoft Store für Unternehmen können Sie Apps für Ihre Organisation suchen und einzeln oder im Rahmen einer Volumenlizenz erwerben. Indem Sie den Store mit Microsoft Intune verbinden, können Sie im Rahmen von per Volumenlizenz erworbenen Apps über das Azure-Portal verwalten. Weitere Informationen finden Sie unter [Verwalten von Apps aus dem Microsoft Store für Unternehmen](windows-store-for-business.md). 

## <a name="before-you-start"></a>Vorbereitung
Beachten Sie die folgenden Punkte, bevor Sie damit beginnen, Apps hinzuzufügen und zuzuweisen.

- Wenn Sie eine App aus einem Store hinzufügen und zuweisen, müssen Endbenutzer über ein Konto bei diesem Store verfügen, um die App installieren zu können.
- Einige von Ihnen zugewiesenen Apps oder Elemente sind möglicherweise von integrierten iOS-Apps abhängig. Wenn Sie z. B. ein Buch aus dem iOS-Store zuweisen, muss die iBooks-App auf dem Gerät vorhanden sein. Wenn Sie die integrierte iBooks-App entfernt haben, können Sie Intune nicht dazu verwenden, sie wieder zu aktivieren.

## <a name="cloud-storage-space"></a>Cloudspeicherplatz
Alle Apps, die Sie mithilfe des Software-Installationsprogrammtyps erstellen (beispielsweise eine branchenspezifische App), werden paketiert und in den Intune-Cloudspeicher hochgeladen. Ein Testabonnement von Intune enthält 2 GB cloudbasierten Speicher, der zum Speichern von verwalteten Apps und Updates verwendet wird. Ein vollständiges Abonnement enthält 20 GB Speicherplatz.

Sie können zusätzlichen Speicher für Intune mit Ihrer ursprünglichen Zahlungsweise erwerben.  Wenn Sie per Rechnung oder Kreditkarte gezahlt haben, besuchen Sie das [Portal zur Abonnementverwaltung](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  Wenden Sie sich alternativ an Ihren Partner oder Vertriebsmitarbeiter.

Anforderungen für Cloudspeicherplatz:

-   Alle App-Installationsdateien müssen sich im selben Ordner befinden.
-   Die maximale Dateigröße für hochgeladene Dateien beträgt 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Erstellen und Bearbeiten von Kategorien für Apps

Mithilfe von App-Kategorien können Sie Apps sortieren, damit Benutzer sie einfacher im Unternehmensportal finden können. Sie können einer App auch mehrere Kategorien zuweisen, z.B. **Entwickler-Apps** oder **Kommunikations-Apps**.
Wenn Sie eine App in Intune hinzufügen, können Sie die gewünschte Kategorie auswählen. Verwenden Sie die plattformspezifischen Themen, um eine App hinzuzufügen und Kategorien zuzuweisen. Gehen Sie zum Erstellen und Bearbeiten Ihre eigenen Kategorien folgendermaßen vor:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie auf dem Blatt **Intune** die Option **Mobile Apps** aus.
4. Wählen Sie in der Workload **Mobile Apps** die Option **Setup** > **App-Kategorien** aus.
5. Auf dem Blatt **App-Kategorien** wird eine Liste der aktuellen Kategorien angezeigt. Wählen Sie eine der folgenden Aktionen aus:
    - **Erstellen einer Kategorie:** Klicken Sie auf dem Blatt **Kategorie erstellen** auf **Hinzufügen**, und geben Sie dann einen Namen für die neue Kategorie ein. Namen können in nur einer Sprache eingegeben werden, und werden von Intune nicht übersetzt. Klicken Sie auf **Erstellen**, wenn Sie fertig sind.
    - **Bearbeiten einer Kategorie:** Wählen Sie für jede Kategorie in der Liste „**...**“ aus. Über diese Option wird ein Popupmenü angezeigt, über das Sie die Kategorie **an das Dashboard anheften** oder **löschen** können.

## <a name="apps-added-automatically-by-intune"></a>Von Intune automatisch hinzugefügte Apps

Zuvor enthielt Intune eine Reihe integrierter Apps, die Sie rasch zuweisen konnten. Auf Grundlage Ihres Feedbacks wurde diese Liste entfernt, und es werden keine integrierten Apps mehr angezeigt.
Wenn Sie jedoch schon integrierte Apps zugewiesen haben, werden diese noch immer auf der App-Liste angezeigt. Sie können diese Apps weiter nach Bedarf zuweisen.
Es ist geplant, in einer späteren Version eine einfachere Methode hinzuzufügen, um integrierte Apps über das Azure-Portal auszuwählen und zuzuweisen.

## <a name="next-steps"></a>Nächste Schritte

Wählen Sie eines der folgenden Themen, um zu erfahren, wie Sie Apps für jede Plattform in Intune hinzufügen:

- [Android Store-Apps](store-apps-android.md)
- [Android-Branchen-Apps](lob-apps-android.md)
- [iOS Store-Apps](store-apps-ios.md)
- [iOS-Branchen-Apps](lob-apps-ios.md)
- [Web-Apps (für alle Plattformen)](web-app.md)
- [Windows Phone 8.1 Store-Apps](store-apps-windows-phone-8-1.md)
- [Branchenspezifische Windows Phone-Apps](lob-apps-windows-phone.md)
- [Windows Store-Apps](store-apps-windows.md)
- [Branchenspezifische Windows-Apps](lob-apps-windows.md)
- [Office 365 apps for Windows 10 (Office 365-Apps für Windows 10)](apps-add-office365.md)
- [Integrierte Apps](apps-add-built-in.md)

