---
title: Hinzufügen von branchenspezifischen macOS-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie branchenspezifische (Line-of-Business, LOB) macOS-Apps zu Microsoft Intune hinzufügen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81a084528fdc500bf9b6de0ca5fa847c2e0b3797
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563920"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>Hinzufügen von branchenspezifischen (Line-of-Business, LOB) macOS-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Fügen Sie mithilfe der Informationen in diesem Artikel Microsoft Intune branchenspezifische macOS-Apps hinzu. Sie müssen ein externes Tool zur Vorverarbeitung Ihrer *PKG*-Dateien herunterladen, bevor Sie Ihre branchenspezifische Datei in Microsoft Intune hochladen können. Die Vorverarbeitung Ihrer *PKG*-Dateien muss auf einem macOS-Gerät erfolgen.

> [!NOTE]
> Ab dem Release von macOS Catalina 10.15: Überprüfen Sie vor dem Hinzufügen Ihrer Apps zu Intune, ob Ihre branchenspezifische macOS-Apps notariell beglaubigt sind. Wenn die Entwickler Ihrer branchenspezifischen Apps ihre Apps nicht beglaubigt haben, können die Apps nicht auf den macOS-Geräten Ihrer Benutzer ausgeführt werden. Weitere Informationen darüber, wie Sie überprüfen, ob eine App notariell beglaubigt ist, finden Sie unter [Notarielles Beglaubigen Ihrer macOS-Apps zur Vorbereitung für macOS Catalina](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Notarizing-your-macOS-apps-to-prepare-for-macOS/ba-p/808579).

> [!NOTE]
> Während Benutzer von macOS-Geräten einige der integrierten macOS-Apps wie Stocks und Maps entfernen können, können Sie diese Apps über Intune nicht erneut bereitstellen. Wenn Endbenutzer diese Apps löschen, müssen sie zum App Store navigieren und die Apps manuell erneut installieren.

## <a name="before-your-start"></a>Vor Ihrem Start

Sie müssen ein externes Tool herunterladen, das heruntergeladene Tool als ausführbare Datei markieren und Ihre *PKG*-Dateien mit dem Tool vorab verarbeiten, bevor Sie Ihre branchenspezifische Datei in Microsoft Intune hochladen können. Die Vorverarbeitung Ihrer *PKG*-Dateien muss auf einem macOS-Gerät erfolgen. Verwenden Sie das Intune App Wrapping Tool für Mac, um die Verwaltung von Mac-Apps mit Microsoft Intune zu ermöglichen.

> [!IMPORTANT]
> Die *PKG*-Datei muss mit dem Zertifikat „Developer ID Installer“ signiert werden, das von einem Apple Developer-Konto abgerufen wird. Nur *PKG*-Dateien können verwendet werden, um macOS-LOB-Apps in Microsoft Intune hochzuladen. Konvertierung anderer Formate, z.B. *.dmg* in *.pkg*, wird nicht unterstützt.
>

1. Laden Sie das [Intune App Wrapping Tool für Mac](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac) herunter.

    > [!NOTE]
    > Das **Intune App Wrapping Tool für Mac** muss auf einem macOS-Computer ausgeführt werden. 

2. Markieren Sie das heruntergeladene Tool als ausführbare Datei:
   - Starten Sie die Terminal-App.
   - Ändern Sie das Verzeichnis in den Speicherort, unter dem sich `IntuneAppUtil` befindet.
   - Führen Sie den folgenden Befehl aus, um das Tool als ausführbare Datei zu erstellen:<br> 
       `chmod +x IntuneAppUtil`

3. Umschließen Sie mit dem `IntuneAppUtil`-Befehl im **Intune App Wrapping Tool für Mac** die *PKG*-LOB-App-Datei aus einer *INTUNEMAC*-Datei.<br>

    Beispiele für Befehle, die für das Microsoft Intune App Wrapping Tool für macOS verwendet werden können:
    
    - `IntuneAppUtil -h`<br>
    Dieser Befehl zeigt Nutzungsinformationen für das Tool an.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Mit diesem Befehl wird eine *PKG*-LOB-App-Datei zu einer *INTUNEMAC*-Datei umschlossen.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Mit diesem Befehl werden die erkannten Parameter und die Version für die erstellte *INTUNEMAC*-Datei extrahiert.

## <a name="step-1---specify-the-software-setup-file"></a>Schritt 1: Angeben der Softwaresetupdatei

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie im Bereich **App hinzufügen** die Option **Branchenspezifische App** als **App-Typ** aus.

## <a name="step-2---configure-the-app-package-file"></a>Schritt 2: Konfigurieren der App-Paketdatei

1. Klicken Sie im Bereich **App hinzufügen** auf die Option **App-Paketdatei**.
2. Wählen Sie im Bereich **App-Paketdatei** die Schaltfläche „Durchsuchen“ aus, und wählen Sie eine macOS-Installationsdatei mit der Erweiterung *INTUNEMAC* aus.
3. Wenn Sie fertig sind, wählen Sie **OK** aus.


## <a name="step-3---configure-app-information"></a>Schritt 3: Konfigurieren von App-Informationen

1. Klicken Sie im Bereich **App hinzufügen** auf die Option **App-Informationen**.
2. Fügen Sie im Bereich **App-Informationen** Details zu Ihrer App hinzu. Abhängig von der ausgewählten App wurden einige der Werte in diesem Bereich möglicherweise automatisch ausgefüllt:
    - **Name:** Geben Sie den Namen der App ein, der im Unternehmensportal angezeigt werde soll. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein, die den Benutzern im Unternehmensportal angezeigt werden soll.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    - **Mindestens erforderliches Betriebssystem:** Wählen Sie in der Liste die mindestens erforderliche Betriebssystemversion aus, auf der die App installiert werden kann. Wenn Sie die App einem Gerät mit einem älteren Betriebssystem zuweisen, wird sie nicht installiert.
    - **Kategorie:** Wählen Sie eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen:** Zeigen Sie die App auf der Hauptseite des Unternehmensportal hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL:** Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen:** Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler:** Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer:** Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. **Personalabteilung**.
    - **Anmerkungen:** Geben Sie Hinweise zu dieser App ein.
    - **Logo:** Laden Sie ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird gemeinsam mit der App angezeigt, wenn der Benutzer das Unternehmensportal durchsucht.
3. Wenn Sie fertig sind, wählen Sie **OK** aus.

## <a name="step-4---finish-up"></a>Schritt 4: Fertig stellen

1. Prüfen Sie Ihre Angaben im Bereich **App hinzufügen**.
2. Wählen Sie **Hinzufügen** aus, um die App in Intune hochzuladen.

Die von Ihnen erstellte App erscheint in der Liste der Apps, in der Sie sie den ausgewählten Gruppen zuweisen können. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

> [!NOTE]
> Wenn die *PKG*-Datei mehrere Apps oder App-Installer enthält, meldet Microsoft Intune nur dann, wenn alle installierten Apps auf dem Gerät erkannt werden, dass die *App* erfolgreich installiert wurde.

## <a name="step-5---update-a-line-of-business-app"></a>Schritt 5: Aktualisieren einer branchenspezifischen App

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Damit der Intune-Dienst erfolgreich eine neue *PKG*-Datei auf dem Gerät bereitstellt, müssen Sie die Paket-`version` und `CFBundleVersion`-Zeichenfolge in der Datei *packageinfo* in Ihrem *PKG*-Paket inkrementieren.

## <a name="next-steps"></a>Nächste Schritte

- Die von Ihnen erstellte App wird in der Liste der Apps angezeigt. Sie können sie jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

- Erfahren Sie mehr darüber, wie Sie die Eigenschaften und Zuweisungen Ihrer App überwachen können. Weitere Informationen finden Sie unter [Überwachen von App-Informationen und -Zuweisungen](apps-monitor.md).

- Erfahren Sie mehr über den Kontext Ihrer App in Intune. Weitere Informationen finden Sie unter [Übersicht über die Lebenszyklen von Geräten und Apps](../fundamentals/device-lifecycle.md).
