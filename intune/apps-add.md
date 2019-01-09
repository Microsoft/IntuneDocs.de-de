---
title: Hinzufügen von Apps zu Microsoft Intune
titlesuffix: ''
description: Erfahren Sie, wie Sie Apps zu Microsoft Intune hinzufügen, damit Sie sie Benutzern und Geräten zuweisen können. Intune unterstützt eine Vielzahl von App-Typen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9cd03d4953376d20e96ec146ece91120d592cb99
ms.sourcegitcommit: 1c9ef5cfac2fc024528d2cfc9d590fa68dd58080
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53429779"
---
# <a name="add-apps-to-microsoft-intune"></a>Hinzufügen von Apps zu Microsoft Intune 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Bevor Sie Apps zuweisen, überwachen, konfigurieren oder schützen können, müssen Sie sie zu Microsoft Intune hinzufügen.

Die App-Anforderungen der Benutzer von Apps und Geräten in Ihrem Unternehmen (also der Mitarbeiter Ihres Unternehmens) können unterschiedlich sein. Bevor Sie Apps zu Intune hinzufügen und den Mitarbeitern zur Verfügung stellen, müssen Sie einige Grundlagen zu Apps kennen. Sie müssen die verschiedenen Arten von Apps kennen, die für Intune verfügbar sind. Sie müssen die App-Anforderungen bewerten, beispielsweise die erforderlichen Plattformen sowie die Funktionen, die die Mitarbeiter benötigen. Sie müssen festlegen, ob Sie Intune zum Verwalten der Geräte (einschließlich Apps) oder nur zum Verwalten von Apps, also ohne Geräteverwaltung, verwenden möchten. Schließlich müssen Sie die Apps und Funktionen bestimmen, die Ihre Mitarbeiter benötigen, und wer im Einzelnen was benötigt. Die Informationen in diesem Artikel erleichtern Ihnen den Einstieg.

## <a name="app-types-in-microsoft-intune"></a>App-Typen in Microsoft Intune

Intune unterstützt eine Vielzahl von App-Typen. Jeder App-Typ hat unterschiedliche Optionen. Über Intune können Sie folgende App-Typen hinzufügen und zuweisen:

| App-Typen | Installation | Updates |
|---|---|---|
| Apps aus dem Store (Store-Apps) | Intune installiert die App auf dem Gerät.  | App-Updates werden automatisch ausgeführt.   |
| Interne (branchenspezifische) Apps  | Intune installiert die App auf dem Gerät (Sie stellen die Installationsdatei zur Verfügung).     | Sie müssen ein Update für die App ausführen.  |
| Apps, die bereits integriert sind (integrierte Apps)    | Intune installiert die App auf dem Gerät.  | App-Updates werden automatisch ausgeführt.  |
| Apps im Web (Weblink) | Intune erstellt eine Verknüpfung zu der Web-App auf dem Startbildschirm des Geräts.  | App-Updates werden automatisch ausgeführt.    |

### <a name="specific-app-type-details"></a>Details zu den jeweiligen App-Typen
 
Die folgende Tabelle führt die verschiedenen App-Typen auf und erläutert, wie Sie diese in Intune im Bereich **App hinzufügen** hinzufügen können:

| **App-spezifischer Typ** | **Allgemeiner Typ** | **App-spezifische Vorgehensweisen** |
| --- | --- | --- |
| Android Store-Apps  | Store-App  | Wählen Sie **Android** als **App-Typ** aus, und geben Sie die Google Play Store-URL für die App ein. |
| iOS Store-Apps  | Store-App  | Wählen Sie **iOS** als **App-Typ** aus, suchen Sie nach der App, und wählen Sie die App in Intune aus. |
| Windows Phone 8.1 Store-Apps  | Store-App  | Wählen Sie **Windows Phone 8.1** als **App-Typ** aus, und geben Sie die Microsoft Store-URL für die App ein. |
| Microsoft Store-Apps  | Store-App  | Wählen Sie **Windows** als **App-Typ** aus, und geben Sie die Microsoft Store-URL für die App ein. |
| Android-Arbeitsprofil-Apps | Store-App  | Suchen und genehmigen Sie die Android-Arbeitsprofil-App über den verwalteten Google Play Store.  |
| Office 365-Apps für Windows 10  | Store-App (Office 365) | Wählen Sie **Windows 10** in der **Office 365 Suite** als **App-Typ** aus, und wählen Sie dann die Office 365-App aus, die Sie installieren möchten.  |
| Office 365-Apps für macOS | Store-App (Office 365) | Wählen Sie **macOS** in der **Office 365 Suite** als **App-Typ** aus, und wählen Sie dann die Office 365-App-Suite aus. |
| Branchenspezifische Android-Apps | LOB-App | Wählen Sie **Branchenspezifische App** als **App-Typ** aus, wählen Sie **App-Paketdatei** aus, und geben Sie dann eine Android-Installationsdatei mit der Erweiterung **APK** an.  |
| Branchenspezifische iOS-Apps | LOB-App | Wählen Sie **Branchenspezifische App** als **App-Typ** aus, wählen Sie **App-Paketdatei** aus, und geben Sie dann eine iOS-Installationsdatei mit der Erweiterung **IPA** an.  |
| Branchenspezifische Windows Phone-Apps | LOB-App | Wählen Sie **Branchenspezifische App** als **App-Typ** aus, wählen Sie die **App-Paketdatei** aus, und geben Sie dann eine Windows Phone-Installationsdatei mit der Erweiterung **XAP** an.  |
| Branchenspezifische Windows-Apps | LOB-App | Wählen Sie **Branchenspezifische App** als App-Typ und die **App-Paketdatei** aus, und geben Sie dann eine Windows-Installationsdatei mit der Erweiterung **.msi**, **.appx**, **.appxbundle**, **.msix** oder **.msixbundle** an. |
| Integrierte iOS-App  | Integrierte App | Wählen Sie **Integrierte App** als **App-Typ** aus, und wählen Sie dann aus der Liste der bereitgestellten Apps die gewünschte integrierte App aus.  |
| Integrierte Android-App  | Integrierte App | Wählen Sie **Integrierte App** als **App-Typ** aus, und wählen Sie dann aus der Liste der bereitgestellten Apps die gewünschte integrierte App aus.  |
| Web-Apps  | Web-App  | Wählen Sie **Weblink** als **App-Typ** aus, und geben Sie eine gültige URL ein, die auf die Web-App verweist.  |
| Windows-App (Win32)  | LOB-App  | Wählen Sie **Windows-App (Win32)** als **App-Typ** aus, wählen Sie **App-Paketdatei** aus, und geben Sie dann eine Installationsdatei mit der Erweiterung **.intunewin** an.  |

Sie können eine App in Microsoft Intune hinzufügen, indem Sie **Client-Apps** > **Apps** > **Hinzufügen** auswählen. Der Bereich **App hinzufügen** wird geöffnet. Dort können Sie den **App-Typ** auswählen. 

>[!TIP]
> Eine branchenspezifische App wird über eine App-Installationsdatei hinzugefügt. Fügen Sie beispielweise die Anwendung hinzu, um eine branchenspezifische iOS-App zu installieren, indem Sie im Bereich **App hinzufügen** **Branchenspezifische App** als **App-Typ** auswählen. Wählen Sie dann die App-Paketdatei (mit der Erweiterung „IPA“) aus. Solche Apps werden in der Regel intern geschrieben.

## <a name="assess-app-requirements"></a>Bewerten der App-Anforderungen
Sie müssen als IT-Administrator nicht nur festlegen, welche Apps Ihre Gruppe verwenden soll, sondern auch die Funktionen bestimmen, die jede Gruppe bzw. Untergruppe benötigt. Für jede App bestimmen Sie die benötigten Plattformen und legen fest, welche Gruppen von Benutzern die App verwenden müssen, welche Konfigurationsrichtlinien für diese Gruppen gelten und welche Schutzrichtlinien angewendet werden sollen.  

Darüber hinaus müssen Sie bestimmen, ob Sie sich auf die Verwaltung mobiler Geräte (MDM) oder die Verwaltung mobiler Anwendungen (MAM) konzentrieren. 

Es ist nützlich, Intune zur Verwaltung mobiler Geräte (MDM) zu verwenden, wenn die folgenden Bedingungen zutreffen:
- Benutzer benötigen ein unternehmensinternes WLAN- oder VPN-Konnektivitätsprofil, damit sie produktiv arbeiten können.
- Benutzer benötigen mehrere Apps, die mit Push auf ihre Geräte übertragen werden.
- Ihre Organisation muss mit den vorgeschriebenen und anderen Richtlinien kompatibel sein, die bestimmte MDM-Steuerelemente wie die Sicherheit oder die Verschlüsselung aufrufen.

Es ist nützlich, Intune für die Verwaltung mobiler Anwendungen zu verwenden, ohne das Gerät zu verwalten, wenn die folgenden Bedingungen zutreffen:
- Sie möchten zulassen, dass Benutzer ihre eigenen Geräte verwenden (Bring Your Own Device, BYOD).
- Sie möchten eine einmalige Popupmeldung zur Verfügung stellen, um die Benutzer darüber zu informieren, dass die MAM-Schutzfunktionen funktionieren, anstatt kontinuierlich Benachrichtigungen auf Geräteebene zu versenden.
- Sie möchten konform mit den Richtlinien handeln, die weniger Verwaltungsfunktionen auf persönlichen Geräten erfordern. Beispielsweise wenn Sie die Unternehmensdaten für die Apps verwalten möchten, anstatt die Unternehmensdaten für das gesamte Gerät zu verwalten.

Weitere Informationen finden Sie unter [Compare MDM and MAM (Vergleich von MDM und MAM)](byod-technology-decisions.md).

### <a name="determine-who-will-use-the-app"></a>Festlegen, wer die App verwendet

Wenn Sie bestimmen, welche Apps Ihre Mitarbeiter benötigen, berücksichtigen Sie die verschiedenen Gruppen von Benutzern und die verschiedenen Apps, die sie verwenden. Diese Gruppen zu kennen, ist auch nach dem Hinzufügen einer App sehr nützlich. Nachdem Sie eine App hinzugefügt haben, weisen Sie eine Gruppe von Benutzern zu, die die App verwenden können. 

Zunächst müssen Sie auf der Grundlage der Vertraulichkeitsstufe der in der App enthaltenen Daten bestimmen, welche Gruppe Zugriff auf die App haben sollte. Sie müssen möglicherweise bestimmte Rollentypen innerhalb Ihrer Organisation einschließen bzw. ausschließen. Beispielsweise kann es sein, dass für die Vertriebsgruppe nur bestimmte branchenspezifische Apps erforderlich sind, wohingegen Mitarbeiter, die im Zusammenhang mit der Technik, den Finanzen bzw. der Personal- oder Rechtsabteilung stehen, gar keine branchenspezifischen Apps verwenden müssen. Außerdem sind für die Vertriebsgruppe möglicherweise ein zusätzlicher Schutz von Daten und der Zugriff auf unternehmensinterne Dienste auf mobilen Geräten erforderlich. Sie müssen festlegen, wie diese Gruppe über die App eine Verbindung mit den Ressourcen herstellt. Sollen die Daten, auf die die App zugreift, in der Cloud oder lokal gespeichert werden? Außerdem müssen Sie festlegen, wie die Benutzer über die App eine Verbindung mit den Ressourcen herstellen. 

Neben E-Mails unterstützt Intune auch das Ermöglichen des Zugriffs auf Client-Apps, die den sicheren Zugriff auf lokale Daten erfordern, z.B. ein branchenspezifischer Anwendungsserver. Sie stellen diesen Zugriffstyp in der Regel mithilfe von [Zertifikaten, die von Intune verwaltet werden](certificates-configure.md), in Kombination mit einem VPN-Standardgateway oder -proxy im Umkreis, z.B. dem Azure Active Directory-Anwendungs-Proxy, bereit. Darüber hinaus können das [App Wrapping Tool und App SDK](apps-prepare-mobile-application-management.md) von Intune dabei helfen, dass die Daten, auf die zugegriffen wird, in der branchenspezifischen App verbleiben und diese App keine Unternehmensdaten an Verbraucher-Apps oder -Dienste übergeben kann.

Verwenden Sie das [Handbuch zur Bereitstellungs-, Entwurfs- und Implementierungsplanung für Intune](planning-guide.md), um zu ermitteln, wie Sie die Gruppen der Organisation identifizieren, die jedem App-Szenario für Anwendungsfälle und untergeordnete Anwendungsfälle zugewiesen sind. Weitere Informationen zum Zuweisen von Apps an Gruppen finden Sie unter [Zuweisen von Apps an Gruppen mit Microsoft Intune](apps-deploy.md).

### <a name="determine-the-type-of-app-for-your-solution"></a>Bestimmen des App-Typs für Ihre Lösung

Sie können unter folgenden App-Typen wählen:
- **Apps aus dem Store**: Apps, die in die Stores von Microsoft, iOS oder Android hochgeladen wurden, sind Store-Apps. Der Anbieter der Store-App verwaltet die Updates für die App und stellt sie bereit. Wählen Sie die App aus der Store-Liste aus, und machen Sie sie mithilfe von Intune für alle Benutzer verfügbar.
- **Intern erstellte (branchenspezifische) Apps**: Intern erstelle Apps gelten als branchenspezifische Apps. Die Funktionen dieses App-Typs wurden für eine der von Intune unterstützten Plattformen wie Windows, iOS oder Android erstellt. Ihre Organisation erstellt Updates als unabhängige Dateien und stellt sie für Sie bereit. Sie fügen dann mithilfe von Intune die Updates für die App-Benutzer hinzu und stellen sie bereit.
- **Apps im Web**: Web-Apps sind Client-Server-Anwendungen. Der Server stellt die Web-App bereit, welche die Benutzeroberfläche, den Inhalt und die Funktionen umfasst. Außerdem bieten moderne Webhostingplattformen häufig Vorteile bei Sicherheit und Lastenausgleich. Der App-Typ wird separat im Web verwaltet. Verwenden Sie Intune, um auf diesen App-Typ zu verweisen. Sie legen ebenfalls fest, welche Benutzergruppen auf diese App zugreifen können. Beachten Sie, dass Android keine Web-Apps unterstützt.

Wenn Sie festlegen, welche Apps Ihre Organisation benötigt, überprüfen Sie, wie die Apps mit Clouddiensten zusammenarbeiten, auf welche Daten die App zugreift, ob die Apps für BYOD-Benutzer verfügbar sind und ob die Apps Internetzugriff erfordern.

Weitere Informationen zu den App-Typen, die für Ihre Organisation erforderlich sind, finden Sie unter [Erstellen eines Entwurfs](planning-guide-design.md#feature-requirements) im Abschnitt „Featureanforderungen“ unter „Apps“.

### <a name="understanding-app-management-and-protection-policies"></a>Grundlegendes zu Richtlinien zur Verwaltung und zum Schutz von Apps
Mithilfe von Intune können Sie die Funktionen der von Ihnen bereitgestellten Apps verändern, um sie an die Konformitäts- und Sicherheitsrichtlinien Ihres Unternehmens anzupassen. Dadurch können Sie auch bestimmen, wie die Daten Ihres Unternehmens geschützt werden sollen. Mit Intune verwaltete Apps verfügen über umfangreiche Richtlinien zum Schutz von mobilen Anwendungen. Dazu gehört z.B.:

- das Einschränken von Funktionen für „Kopieren und Einfügen“ und „Speichern unter“.
- das Konfigurieren von Weblinks, sodass sie in der Intune Managed Browser-App geöffnet werden.
- das Aktivieren der Unterstützung von mehreren Identitäten und des bedingten Zugriffs auf App-Ebene.

Mit Intune verwaltete Apps können außerdem ohne Registrierung den App-Schutz aktivieren. Dadurch können Sie entscheiden, ob Sie Richtlinien zum Verhindern von Datenverlust anwenden möchten, ohne das Gerät des Benutzers zu verwalten. Darüber hinaus können Sie die Verwaltung mobiler Apps in Ihre mobilen und branchenspezifischen Apps integrieren. Verwenden Sie dafür das Intune App SDK und das App Wrapping Tool. Weitere Informationen zu diesen Tools finden Sie unter [Übersicht über das Intune App SDK](app-sdk.md).

### <a name="understanding-licensed-apps"></a>Grundlegendes zu lizenzierten Apps
Sie sollten nicht nur zwischen Web-Apps, Store-Apps und branchenspezifischen Apps unterscheiden können, sondern auch zwischen Apps, die über ein Volumenlizenzprogramm (Volume Purchase Program) bezogen wurden, und lizenzierten Apps, wie z.B. folgende: 
- **Apple Volume Purchasing Program für Unternehmen (iOS)**: Im iOS-App-Store können Sie mehrere Lizenzen für eine App erwerben, die in Ihrem Unternehmen ausgeführt werden soll. Durch den Erwerb mehrerer Kopien können Sie Apps in Ihrem Unternehmen effizient verwalten. Weitere Informationen finden Sie unter [Verwalten von iOS-Apps, die per Volumenlizenz erworben wurden](vpp-apps-ios.md).
- **Android-Arbeitsprofil**: Das Zuweisen von Apps zu Android-Arbeitsprofilgeräten unterscheidet sich von deren Zuweisung zu „normalen“ Android-Geräten. Alle Apps, die für Android-Arbeitsprofile installiert werden, stammen aus dem verwalteten Google Play Store. Melden Sie sich beim Store an, suchen Sie nach den gewünschten Apps, und genehmigen Sie diese. Die App wird dann im Knoten **Lizenzierte Apps** des Azure-Portals angezeigt, und Sie können die Zuweisung der App wie bei jeder anderen App verwalten.
- **Microsoft Store für Unternehmen (Windows 10)**: Im Microsoft Store für Unternehmen können Sie Apps für Ihre Organisation suchen und einzeln oder mit Volumenlizenz erwerben. Indem Sie den Store mit Microsoft Intune verbinden, können Sie per Volumenlizenz erworbene Apps über das Azure-Portal verwalten. Weitere Informationen finden Sie unter [Verwalten von Apps aus dem Microsoft Store für Unternehmen](windows-store-for-business.md).

    > [!NOTE]
    > Zu den Dateierweiterungen für Windows-Apps gehören **.msi**, **.appx**, **.appxbundle**, **.msix** und **.msixbundle**.  

## <a name="before-you-add-apps"></a>Vor dem Hinzufügen von Apps
Bevor Sie damit beginnen, Apps hinzuzufügen und zuzuweisen, beachten Sie die folgenden Punkte:

- Wenn Sie eine App aus einem Store hinzufügen und zuweisen, müssen Ihre Benutzer über ein Konto bei diesem Store verfügen, um die App installieren zu können.
- Einige von Ihnen zugewiesene Apps oder Elemente sind möglicherweise von integrierten iOS-Apps abhängig. Wenn Sie z.B. ein Buch aus dem iOS-Store zuweisen, muss die iBooks-App auf dem Gerät vorhanden sein. Wenn Sie die integrierte iBooks-App entfernt haben, können Sie Intune nicht dazu verwenden, sie wieder zu aktivieren.

> [!IMPORTANT]
> Wenn Sie den Namen der App über das Intune Azure-Portal ändern, nachdem Sie sie bereitgestellt und installiert haben, kann die App mit Befehlen nicht mehr erreicht werden.

## <a name="cloud-storage-space"></a>Cloudspeicherplatz
Alle Apps, die Sie mithilfe des Software-Installationsprogrammtyps erstellen (beispielsweise eine branchenspezifische App), werden paketiert und in den Intune-Cloudspeicher hochgeladen. Ein Testabonnement von Intune enthält 2 GB cloudbasierten Speicher, der zum Speichern von verwalteten Apps und Updates verwendet wird. Der Gesamtspeicherplatz wird nicht durch ein vollständiges Abonnement beeinflusst.

Anforderungen für Cloudspeicherplatz:

- Alle App-Installationsdateien müssen sich im selben Ordner befinden.
- Die maximale Dateigröße für hochgeladene Dateien beträgt 8 GB.

## <a name="create-and-edit-categories-for-apps"></a>Erstellen und Bearbeiten von Kategorien für Apps

Mithilfe von App-Kategorien können Sie Apps sortieren, damit Benutzer sie einfacher im Unternehmensportal finden können. Sie können einer App auch mehrere Kategorien zuweisen, z.B. *Entwickler-Apps* oder *Kommunikations-Apps*.

Wenn Sie eine App in Intune hinzufügen, können Sie die gewünschte Kategorie auswählen. Verwenden Sie die plattformspezifischen Themen, um eine App hinzuzufügen und Kategorien zuzuweisen. Gehen Sie zum Erstellen und Bearbeiten Ihre eigenen Kategorien folgendermaßen vor:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie im Workloadbereich **Client-Apps** unter **Setup** die Option **App-Kategorien** aus.  
    Im Bereich **App-Kategorien** wird eine Liste der aktuellen Kategorien angezeigt. 
5. Führen Sie einen der folgenden Schritte aus:
    - Um eine Kategorie hinzuzufügen, wählen Sie im Bereich **Kategorie erstellen** die Option **Hinzufügen** aus, und geben Sie dann einen Namen für die Kategorie ein.  
    Namen können in nur einer Sprache eingegeben werden und werden von Intune nicht übersetzt.
    - Um eine Kategorie zu bearbeiten, wählen Sie die Auslassungspunkte (**...** ) neben der Kategorie aus und dann **An Dashboard anheften** oder **Löschen**.
6. Wählen Sie **Erstellen** aus.

## <a name="apps-that-are-added-automatically-by-intune"></a>Von Intune automatisch hinzugefügte Apps

Zuvor enthielt Intune eine Reihe integrierter Apps, die Sie rasch zuweisen konnten. Basierend auf Intune-Kundenfeedback haben wir diese Liste entfernt, und die integrierten Apps werden nicht mehr angezeigt. Wenn Sie jedoch schon integrierte Apps zugewiesen haben, werden sie weiterhin in der App-Liste angezeigt. Sie können diese Apps weiter nach Bedarf zuweisen.

> [!NOTE]
> Intune versucht, eine erforderliche App, die nicht branchenspezifisch ist, durch Senden eines Installationsbefehls zu installieren, sobald das Gerät eingecheckt wird. Voraussetzung dafür ist, dass die App nicht erkannt wird und der Installationsstatus der App nicht *Installation steht an* ist.

## <a name="installing-updating-or-removing-required-apps"></a>Installieren, Aktualisieren oder Entfernen von erforderlichen Apps

Eine erforderliche App wird durch Intune innerhalb von 24 Stunden neu installiert, aktualisiert oder entfernt. Der siebentägige Auswertungszyklus wird dabei von Intune ignoriert.

Die automatische Neuinstallation, Aktualisierung oder Entfernung einer erforderlichen App wird von Intune unter Berücksichtigung der folgenden Bedingungen durchgeführt:
- Wenn ein Endbenutzer eine App deinstalliert, deren Installation Sie auf seinem Gerät als erforderlich festgelegt haben, installiert Intune die App erneut, sobald der im Zeitplan festgelegte Zyklus beendet ist.
- Wenn die Installation der erforderlichen App fehlschlägt oder die App nicht auf dem Gerät vorhanden ist, überprüft Intune die Kompatibilität und installiert die App erneut, sobald der im Zeitplan festgelegte Zyklus beendet ist.  
- Ein Administrator machte eine App für eine Benutzergruppe verfügbar, und ein Endbenutzer installiert die App über das Unternehmensportal auf dem Gerät. Später aktualisiert der Administrator die App von Version 1 auf Version 2. Intune aktualisiert dann die App, sobald der im Zeitplan festgelegte Zyklus beendet ist. Voraussetzung dafür ist, dass die vorherige Version der App immer noch auf dem Gerät vorhanden ist.
- Wenn der Administrator eine Lösung für eine Deinstallationsabsicht bereitstellt, die App auf dem Gerät vorhanden ist und ein Fehler bei der Deinstallation auftritt, überprüft Intune die Kompatibilität und deinstalliert die App, sobald der im Zeitplan festgelegte Zyklus beendet ist.   

## <a name="app-installation-errors"></a>App-Installationsfehler

Weitere Informationen zu Intune-App-Installationsfehlern finden Sie unter [App-Installationsfehler](troubleshoot-app-install.md#app-installation-errors).

## <a name="next-steps"></a>Nächste Schritte

Wie Sie Apps für jede Plattform in Intune hinzufügen, erfahren Sie unter:

- [Android Store-Apps](store-apps-android.md)
- [Android-Branchen-Apps](lob-apps-android.md)
- [iOS Store-Apps](store-apps-ios.md)
- [iOS-Branchen-Apps](lob-apps-ios.md)
- [Web-Apps (für alle Plattformen)](web-app.md)
- [Windows Phone 8.1 Store-Apps](store-apps-windows-phone-8-1.md)
- [Branchenspezifische Windows Phone-Apps](lob-apps-windows-phone.md)
- [Microsoft Store-Apps](store-apps-windows.md)
- [Branchenspezifische Windows-Apps](lob-apps-windows.md)
- [Office 365 apps for Windows 10 (Office 365-Apps für Windows 10)](apps-add-office365.md)
- [Office 365-Apps für macOS](apps-add-office365-macos.md)
- [Integrierte Apps](apps-add-built-in.md)
- [Win32-Apps](apps-win32-app-management.md) 
