---
title: Erstellen eines Berichts aus dem OData-Feed mit Power BI
titleSuffix: Microsoft Intune
description: Erstellen Sie eine Treemap-Visualisierung mithilfe von Power BI Desktop mit einem interaktiven Filter der Intune Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: d8d8e1d1bb20f222b202e8c854fc4d1a8ba694fa
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648915"
---
# <a name="create-a-report-from-the-odata-feed-with-power-bi"></a>Erstellen eines Berichts aus dem OData-Feed mit Power BI

In diesem Artikel wird erläutert, wie Sie eine Treemap-Visualisierung mithilfe von Power BI Desktop mit einem interaktiven Filter erstellen können. Beispielsweise möchte Ihr Finanzdirektor möglicherweise wissen, in welchem Zusammenhang die Verteilung aller Geräte mit den Geräten, die nur im Besitz von Unternehmen sind, bzw. mit persönlichen Geräten steht. Die Treemap gibt einen Überblick über die Gesamtanzahl von Gerätetypen. Sie können die Anzahl von iOS-, Android- und Windows-Geräten prüfen, die weder einem Unternehmen noch einer Privatperson gehören.

### <a name="overview-of-creating-the-chart"></a>Übersicht zum Erstellen des Diagramms

Gehen Sie wie folgt vor, um dieses Diagramm zu erstellen:
1. Falls noch nicht geschehen, installieren Sie Power BI Desktop.
2. Stellen Sie eine Verbindung mit dem Intune Data Warehouse-Datenmodell her, und rufen Sie aktuelle Daten für das Modell ab.
3. Erstellen oder verwalten Sie die Beziehungen des Datenmodells.
4. Erstellen Sie das Diagramm mit Daten aus der **Gerätetabelle**.
5. Erstellen Sie einen interaktiven Filter.
6. Lassen Sie sich das fertige Diagramm anzeigen.

### <a name="a-note-about-tables-and-entities"></a>Hinweis zu Tabellen und Entitäten

In Power BI arbeiten Sie mit Tabellen. Eine Tabelle enthält Datenfelder. Jedes Datenfeld ist einem Datentypen zugeordnet. Das Feld kann nur Daten dieses Datentyps enthalten. Datentypen sind u.a. Nummern, Text oder Datumsangaben. Die Tabellen in Power BI füllen sich mit kürzlich erfassten Daten aus Ihrem Mandanten, wenn Sie das Modell laden. Obwohl sich die spezifischen Daten mit der Zeit ändern, bleibt die Tabellenstruktur solange unverändert, bis das zugrunde liegende Datenmodell aktualisiert worden ist.

Die Verwendung der Begriffe _Entität_ und _Tabelle_ erscheint Ihnen möglicherweise nicht ganz eindeutig. Sie können über einen OData-Feed auf das Datenmodell zugreifen. Im Zusammenhang mit OData gelten die Container, die in Power BI als Tabellen bezeichnet werden, als Entitäten. Beide Begriffe beziehen sich auf dasselbe Konzept zum Speichern Ihrer Daten.

## <a name="install-power-bi-desktop"></a>Installieren von Power BI Desktop

Installieren Sie die neueste Version von Power BI Desktop. Sie können Power BI Desktop aus [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop) herunterladen.

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Stellen Sie eine Verbindung zum OData-Feed für das Intune Data Warehouse für Ihren Mandanten her.

> [!Note]  
> Sie benötigen in Intune eine Berechtigung, um auf **Berichte** zugreifen zu können. Weitere Informationen finden Sie unter [Autorisierung](reports-api-url.md).

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Öffnen Sie den Bereich **Intune Data Warehouse**, indem Sie den Data Warehouse-Link unter **Weitere Aufgaben** auf der rechten Seite des Blatts **Microsoft Intune – Übersicht** auswählen.
4. Kopieren Sie die benutzerdefinierte Feed-URL. Beispiel: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
1. Öffnen Sie Power BI Desktop.
2. Klicken Sie auf **Daten abrufen** > **OData-Feed**.
3. Fügen Sie die benutzerdefinierte Feed-URL in das URL-Feld im Fenster **OData-Feed** ein.
4. Wählen Sie **Basic** aus.

    ![OData-Feed für Intune Data Warehouse für Ihren Mandanten](media/reports-create-01-odatafeed.png)

9. Klicken Sie auf **OK**.
10. Wählen Sie **Organisationskonto** aus, und melden Sie sich anschließend mit Ihren Anmeldeinformationen für Intune an.

    ![Anmeldeinformationen für das Organisationskonto](media/reports-create-02-org-account.png)

11. Wählen Sie **Verbinden** aus. Der Navigator öffnet sich und zeigt Ihnen eine Liste mit Tabelle im Intune Data Warehouse an.

    ![Screenshot des Navigators mit der Liste der Data Warehouse-Tabellen](media/reports-create-02-loadentities.png)

12. Wählen Sie die **Geräte** und die **OwnerTypes**-Tabellen aus.  Wählen Sie **Laden** aus. Power BI lädt die Daten in das Modell.

## <a name="create-a-relationship"></a>Erstellen einer Beziehung

Sie können mehrerer Tabellen importieren, um nicht nur die Daten in einer einzigen Tabelle zu analysieren, sondern auch tabellenübergreifende Daten.  In Power BI gibt es eine Funktion, die **Autodetect** genannt wird und Beziehungen findet sowie erstellt. Die Tabellen im Data Warehouse wurden so konzipiert, dass sie mit der Autodetect-Funktion von Power BI kompatibel sind. Auch wenn Power BI die Beziehungen nicht automatisch finden sollte, verwalten Sie sie trotzdem.

![Tabellenübergreifendes Verwalten von Beziehungen verwandter Daten](media/reports-create-03-managerelationships.png)

1. Wählen Sie **Beziehungen verwalten** aus.
2. Wählen Sie **Autodetect...** aus, wenn Power BI die Beziehungen noch nicht erkannt hat.

Die Beziehung wird von einer „From“-Spalte zu einer „To“-Spalte angezeigt. In diesem Beispiel ist das Datenfeld **ownerTypeKey** in der **Gerätetabelle** mit dem Datenfeld **ownerTypeKey** in der Tabelle **ownerTypes** verknüpft. Sie können die Beziehung verwenden, um den einfachen Namen eines Gerätetypcodes in der **Gerätetabelle** nachzuschauen.

## <a name="create-a-treemap-visualization"></a>Erstellen einer Treemap-Visualisierung

In einem Treemap-Diagramm werden hierarchische Daten als Felder in Feldern angezeigt. Jede Verzweigung der Hierarchie ist ein Feld, das kleinere Felder enthält, die untergeordnete Verzweigungen darstellen. Sie können Power BI Desktop verwenden, um eine Treemap Ihrer Intune-Daten zu erstellen.

![Power BI-Treemap-Visualisierungen](media/reports-create-03-treemap.png)

1. Wählen Sie einen Diagrammtypen und **Treemap** aus.
2. Suchen Sie im Datenmodell die **Gerätetabelle**.
3. Erweitern Sie die **Gerätetabelle**, und wählen Sie das Datenfeld **Hersteller** im Bereich **Felder** aus.
4. Ziehen Sie das Datenfeld **Hersteller** auf das Treemap-Diagramm im Berichtszeichenbereich.
5. Ziehen Sie das Datenfeld **deviceKey** aus der **Gerätetabelle** in den Abschnitt **Werte** im Bereich **Visualisierung**, und legen Sie es auf dem Feld mit der Bezeichnung **Drag data field here** (Datenfeld hierherziehen) ab.  

Jetzt verfügen Sie über eine Visualisierung der Verteilung von Herstellern und Geräten innerhalb Ihrer Organisation.

![Treemap mit Daten: Verteilung der Gerätehersteller](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Hinzufügen eines Filters

Sie können Ihrer Treemap einen Filter hinzufügen, damit Sie mithilfe Ihrer App zusätzliche Fragen beantworten können.


1. Um einen Filter hinzuzufügen, wählen Sie zunächst die Berichtscanvas aus, und klicken Sie anschließend unter **Visualisierungen** auf das **Slicer-Symbol** (![Treemap mit Datenmodell und unterstützten Beziehungen](media/reports-create-slicer.png)).
2. Suchen Sie die Tabelle **ownerTypes** ziehen Sie das Datenfeld **ownerTypeName** im Abschnitt **Filter** auf den Bereich **Visualisierungen**.  

   In der Gerätetabelle gibt es ein Datenfeld mit der Bezeichnung **OwnerTypeKey**, das einen Code enthält, der darauf hinweist, ob ein Gerät Eigentum eines Unternehmens oder einer Privatperson ist. Da Sie Anzeigenamen in diesem Filter anzeigen wollen, suchen Sie nach der Tabelle **ownerTypes**, und ziehen Sie den **ownerTypeName** dorthin. Das folgende Beispiel zeigt, wie das Datenmodell Beziehungen zwischen den Tabellen unterstützt.

![Treemap mit Filter: Unterstützung von Beziehungen zwischen Tabellen](media/reports-create-08_ownertype.png)

Nun verfügen Sie über einen interaktiven Filter, der zum Wechseln zwischen unternehmenseigenen und privaten Geräten verwendet werden kann. Mit diesem Filter können Sie Veränderungen in der Verteilung nachvollziehen.

1. Wählen Sie **Unternehmen** aus, damit Ihnen die Verteilung der unternehmenseigenen Geräte angezeigt wird.
2. Wählen Sie **Persönlich** aus, damit Ihnen die privaten Geräte angezeigt werden.

## <a name="next-steps"></a>Nächste Schritte

 - Erfahren Sie mehr über das [Erstellen und Verwalten von Beziehungen](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) in Power BI Desktop in der Power BI-Dokumentation.
 - Lesen Sie den Artikel [Datenmodell von Intune Data Warehouse](https://docs.microsoft.com/intune/reports-ref-data-model).
