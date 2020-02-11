---
title: Hinzufügen von branchenspezifischen macOS-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie branchenspezifische (Line-of-Business, LOB) macOS-Apps zu Microsoft Intune hinzufügen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
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
ms.openlocfilehash: c7aa6af751e5ab3e1e3cdff6b1d2e3d6693f65df
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755169"
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
    > [!IMPORTANT]
    > Stellen Sie sicher, dass das Argument `<source_file>` keine Leerzeichen enthält, bevor Sie die `IntuneAppUtil`-Befehle ausführen.

    - `IntuneAppUtil -h`<br>
    Dieser Befehl zeigt Nutzungsinformationen für das Tool an.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Mit diesem Befehl wird eine *PKG*-LOB-App-Datei zu einer *INTUNEMAC*-Datei umschlossen.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Mit diesem Befehl werden die erkannten Parameter und die Version für die erstellte *INTUNEMAC*-Datei extrahiert.

## <a name="select-the-app-type"></a>Auswählen des App-Typs

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie im Bereich **App-Typ auswählen** unter den App-Typen **Sonstige** die Option **Branchenspezifische App** aus.
4. Klicken Sie auf **Auswählen**. Die **App hinzufügen**-Schritte werden angezeigt.

## <a name="step-1---app-information"></a>Schritt 1: App-Informationen

### <a name="select-the-app-package-file"></a>Auswählen der App-Paketdatei

1. Klicken Sie im Bereich **App hinzufügen** auf **App-Paketdatei auswählen**. 
2. Wählen Sie im Bereich **App-Paketdatei** die Schaltfläche zum Durchsuchen. Wählen Sie dann eine macOS-Installationsdatei mit der Erweiterung *INTUNEMAC* aus.
   Die App-Details werden angezeigt.
3. Wenn Sie fertig sind, wählen Sie im Bereich **App-Paketdatei** die Option **OK** aus, um die App hinzuzufügen.

### <a name="set-app-information"></a>Festlegen von App-Informationen

1. Fügen Sie auf der Seite **App-Informationen** die Details zu Ihrer App hinzu. Abhängig von der ausgewählten App wurden einige der Werte in diesem Bereich möglicherweise automatisch ausgefüllt.
    - **Name:** Geben Sie den Namen der App so ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Die Beschreibung wird im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **Mindestens erforderliches Betriebssystem**: Wählen Sie aus der Liste die mindestens erforderliche Betriebssystemversion aus, unter der die App installiert werden kann. Wenn Sie die App einem Gerät mit einem älteren Betriebssystem zuweisen, wird sie nicht installiert.
    - **Kategorie**: Wählen Sie eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Kategorien erleichtern es dem Benutzer, die App über das Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Präsentieren Sie die App herausgehoben auf der Hauptseite des Unternehmensportals, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **URL der Datenschutzrichtlinien:** Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein. Ein Beispiel ist **Personalabteilung**.
    - **Anmerkungen**: Geben Sie Hinweise zu dieser App ein.
    - **Logo**: Laden Sie ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
2. Klicken Sie auf **Weiter**, um die Seite **Bereichsmarkierungen** anzuzeigen.

## <a name="step-2---select-scope-tags-optional"></a>Schritt 2: Auswählen von Bereichsmarkierungen (optional)
Sie können Bereichsmarkierungen verwenden, um zu bestimmen, wer Client-App-Informationen in Intune anzeigen kann. Ausführliche Informationen zu Bereichsmarkierungen finden Sie unter [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen für verteilte IT).

1. Klicken Sie auf **Bereichstags auswählen**, um optional Bereichsmarkierungen für die App hinzuzufügen. 
2. Klicken Sie auf **Weiter**, um die Seite **Zuweisungen** anzuzeigen.

## <a name="step-3---assignments"></a>Schritt 3: Zuweisungen

1. Wählen Sie die Gruppenzuweisungen **Erforderlich**, **Für registrierte Geräte verfügbar** oder **Deinstallieren** für die App aus. Weitere Informationen finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](~/fundamentals/groups-add.md) und [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md).
2. Klicken Sie auf **Weiter**, um die Seite **Überprüfen + erstellen** anzuzeigen. 

## <a name="step-4---review--create"></a>Schritt 4: Überprüfen und Erstellen

1. Überprüfen Sie die Werte und Einstellungen, die Sie für die App eingegeben haben.
2. Klicken Sie abschließend auf **Erstellen**, um Intune die App hinzuzufügen.

    Das Blatt **Übersicht** für die branchenspezifische App wird angezeigt.

Die von Ihnen erstellte App erscheint in der Liste der Apps, in der Sie sie den ausgewählten Gruppen zuweisen können. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

> [!NOTE]
> Wenn die *PKG*-Datei mehrere Apps oder App-Installer enthält, meldet Microsoft Intune nur dann, wenn alle installierten Apps auf dem Gerät erkannt werden, dass die *App* erfolgreich installiert wurde.

## <a name="update-a-line-of-business-app"></a>Aktualisieren einer branchenspezifischen App

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Damit der Intune-Dienst erfolgreich eine neue *PKG*-Datei auf dem Gerät bereitstellt, müssen Sie die Paket-`version` und `CFBundleVersion`-Zeichenfolge in der Datei *packageinfo* in Ihrem *PKG*-Paket inkrementieren.

## <a name="next-steps"></a>Nächste Schritte

- Die von Ihnen erstellte App wird in der Liste der Apps angezeigt. Sie können sie jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

- Erfahren Sie mehr darüber, wie Sie die Eigenschaften und Zuweisungen Ihrer App überwachen können. Weitere Informationen finden Sie unter [Überwachen von App-Informationen und -Zuweisungen](apps-monitor.md).

- Erfahren Sie mehr über den Kontext Ihrer App in Intune. Weitere Informationen finden Sie unter [Übersicht über die Lebenszyklen von Geräten und Apps](../fundamentals/device-lifecycle.md).
