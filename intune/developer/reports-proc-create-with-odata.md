---
title: Erstellen eines Intune-Berichts aus dem OData-Feed mit Power BI
titleSuffix: Microsoft Intune
description: Erstellen Sie eine Treemap-Visualisierung mithilfe von Power BI Desktop mit einem interaktiven Filter der Intune Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 18815fb671e853bc0463fed750d40b80ccb285fb
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74784271"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>Erstellen eines Intune-Berichts aus dem OData-Feed mit Power BI

In diesem Artikel wird erläutert, wie Sie eine TreeMap-Visualisierung Ihrer InTune-Daten erstellen, indem Sie Power BI Desktop, dass Benutzer einen interaktiven Filter verwenden. Ihre Finanzdirektorin könnte beispielsweise wissen, wie die Gesamtverteilung von Geräten zwischen unternehmenseigenen Geräten und persönlichen Geräten vergleicht. Die Treemap gibt einen Überblick über die Gesamtanzahl von Gerätetypen. Sie können die Anzahl von iOS-, Android- und Windows-Geräten prüfen, die weder einem Unternehmen noch einer Privatperson gehören.

## <a name="overview-of-creating-the-chart"></a>Übersicht zum Erstellen des Diagramms

Gehen Sie wie folgt vor, um dieses Diagramm zu erstellen:
1. Falls noch nicht geschehen, installieren Sie Power BI Desktop.
2. Stellen Sie eine Verbindung mit dem Intune Data Warehouse-Datenmodell her, und rufen Sie aktuelle Daten für das Modell ab.
3. Erstellen oder verwalten Sie die Beziehungen des Datenmodells.
4. Erstellen Sie das Diagramm mit Daten aus der **Gerätetabelle**.
5. Erstellen Sie einen interaktiven Filter.
6. Lassen Sie sich das fertige Diagramm anzeigen.

### <a name="a-note-about-tables-and-entities"></a>Hinweis zu Tabellen und Entitäten

In Power BI arbeiten Sie mit Tabellen. Eine Tabelle enthält Datenfelder. Jedes Datenfeld ist einem Datentypen zugeordnet. Das Feld kann nur Daten dieses Datentyps enthalten. Datentypen sind u.a. Nummern, Text oder Datumsangaben. Die Tabellen in Power BI füllen sich mit kürzlich erfassten Daten aus Ihrem Mandanten, wenn Sie das Modell laden. Obwohl sich die spezifischen Daten mit der Zeit ändern, bleibt die Tabellenstruktur solange unverändert, bis das zugrunde liegende Datenmodell aktualisiert worden ist.

Die Verwendung der Begriffe *Entität* und *Tabelle* erscheint Ihnen möglicherweise nicht ganz eindeutig. Auf das Datenmodell kann über einen odata-Feed (Open Data Protocol) zugegriffen werden. Im Zusammenhang mit OData gelten die Container, die in Power BI als Tabellen bezeichnet werden, als Entitäten. Beide Begriffe beziehen sich auf dasselbe Konzept zum Speichern Ihrer Daten. Weitere Informationen zu odata finden Sie in der [Übersicht über odata](/odata/overview).

## <a name="install-power-bi-desktop"></a>Installieren von Power BI Desktop

Installieren Sie die neueste Version von Power BI Desktop. Sie können Power BI Desktop aus [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop) herunterladen.

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Stellen Sie eine Verbindung zum OData-Feed für das Intune Data Warehouse für Ihren Mandanten her.

> [!Note]  
> Sie benötigen in Intune eine Berechtigung, um auf **Berichte** zugreifen zu können. Weitere Informationen finden Sie unter [Autorisierung](../reports-api-url.md).

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Öffnen Sie den Bereich **Intune Data Warehouse**, indem Sie den Data Warehouse-Link unter **Weitere Aufgaben** auf der rechten Seite des Blatts **Microsoft Intune – Übersicht** auswählen.
3. Kopieren Sie die benutzerdefinierte Feed-URL. Beispiel: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. Öffnen Sie Power BI Desktop.
5. Wählen Sie in der Menüleiste **Datei** > **Daten** > **odata-Feed**erhalten.
6. Fügen Sie die benutzerdefinierte Feed-URL, die Sie aus dem vorherigen Schritt kopiert haben, in das URL-Feld im **odata-Feed** -Fenster ein.
7. Wählen Sie **Basic** aus.

    ![OData-Feed für Intune Data Warehouse für Ihren Mandanten](./media/reports-proc-create-with-odata/reports-create-01-odatafeed.png)

8. Wählen Sie **OK** aus.
9. Wählen Sie **Organisationskonto** aus, und melden Sie sich anschließend mit Ihren Anmeldeinformationen für Intune an.

    ![Anmeldeinformationen für das Organisationskonto](./media/reports-proc-create-with-odata/reports-create-02-org-account.png)

10. Wählen Sie **Verbinden** aus. Der Navigator öffnet sich und zeigt Ihnen eine Liste mit Tabelle im Intune Data Warehouse an.

    ![Screenshot des Navigators mit der Liste der Data Warehouse-Tabellen](./media/reports-proc-create-with-odata/reports-create-02-loadentities.png)

11. Wählen Sie die **Geräte** und die **OwnerTypes**-Tabellen aus.  Wählen Sie **Laden** aus. Power BI lädt die Daten in das Modell.

## <a name="create-a-relationship"></a>Erstellen einer Beziehung

Sie können mehrerer Tabellen importieren, um nicht nur die Daten in einer einzigen Tabelle zu analysieren, sondern auch tabellenübergreifende Daten. In Power BI gibt es eine Funktion namens **Automatische Erkennung**, mit der Sie Beziehungen finden und erstellen können. Die Tabellen im Data Warehouse wurden so konzipiert, dass sie mit der automatischen Erkennungsfunktion in Power BI kompatibel sind. Auch wenn Power BI die Beziehungen nicht automatisch finden sollte, können Sie sie dennoch verwalten.

![Tabellenübergreifendes Verwalten von Beziehungen verwandter Daten](./media/reports-proc-create-with-odata/reports-create-03-managerelationships.png)

1. Wählen Sie **Beziehungen verwalten** aus.
2. Wählen Sie **Automatische Erkennung** aus, wenn Power BI die Beziehungen noch nicht erkannt hat.

Die Beziehung wird von einer „From“-Spalte zu einer „To“-Spalte angezeigt. In diesem Beispiel ist das Datenfeld **ownerTypeKey** in der **Gerätetabelle** mit dem Datenfeld **ownerTypeKey** in der Tabelle **ownerTypes** verknüpft. Sie können die Beziehung verwenden, um den einfachen Namen eines Gerätetypcodes in der Tabelle **Geräte** nachzuschlagen.

## <a name="create-a-treemap-visualization"></a>Erstellen einer Treemap-Visualisierung

In einem Strukturdiagramm werden hierarchische Daten als Felder innerhalb von Feldern angezeigt. Jede Verzweigung der Hierarchie ist ein Feld, das kleinere Felder enthält, die untergeordnete Verzweigungen darstellen. Sie können Power BI Desktop verwenden, um eine TreeMap ihrer InTune-Mandanten Daten zu erstellen, die relative Mengen von Gerätehersteller Typen anzeigt.

![Power BI-Treemap-Visualisierungen](./media/reports-proc-create-with-odata/reports-create-03-treemap.png)

1. Suchen Sie im Bereich **Visualisierungen** die Option **TreeMap**, und wählen Sie Sie aus. Das **TreeMap** -Diagramm wird der Berichts Zeichenfläche hinzugefügt.
2. Suchen Sie im **Bereich "Felder** " die `devices` Tabelle.
3. Erweitern Sie die `devices` Tabelle, und wählen Sie das `manufacturer` Datenfeld aus.
4. Ziehen Sie das `manufacturer` Datenfeld in den Berichts Zeichenbereich, und legen Sie es im **TreeMap** -Diagramm ab.
5. Ziehen Sie das Feld `deviceKey` Data aus der Tabelle `devices` in den Bereich **Visualisierungen** , und legen Sie es unter dem Abschnitt **Werte** im Feld mit der Bezeichnung **Datenfelder hier hinzufügen**ab.  

Jetzt verfügen Sie über eine Visualisierung der Verteilung von Herstellern und Geräten innerhalb Ihrer Organisation.

![Treemap mit Daten: Verteilung der Gerätehersteller](./media/reports-proc-create-with-odata/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Hinzufügen eines Filters

Sie können Ihrer Treemap einen Filter hinzufügen, damit Sie mithilfe Ihrer App zusätzliche Fragen beantworten können.

1. Um einen Filter hinzuzufügen, wählen Sie zunächst die Berichtscanvas aus, und klicken Sie anschließend unter **Visualisierungen** auf das **Slicer-Symbol** (![Treemap mit Datenmodell und unterstützten Beziehungen](./media/reports-proc-create-with-odata/reports-create-slicer.png)). Die leere **slicervisualisierung** wird in der Canvas angezeigt.
2. Suchen Sie im **Bereich "Felder** " die `ownerTypes` Tabelle.
3. Erweitern Sie die `ownerTypes` Tabelle, und wählen Sie das `ownerTypeName` Datenfeld aus.
4. Ziehen Sie das Feld `onwerTypeName` Data aus der Tabelle `ownerTypes` in den Bereich **Filter** , und legen Sie es im Bereich **Filter auf dieser Seite** im Feld mit der Bezeichnung **Datenfelder hier hinzufügen**ab.  

   In der `OwnerTypes` Tabelle gibt es ein Datenfeld mit dem Namen `OwnerTypeKey`, das Daten enthält, die davon unterliegen, ob ein Gerät im Besitz des Unternehmens oder privat ist. Da Sie Anzeigenamen in diesem Filter anzeigen möchten, suchen Sie nach der Tabelle `ownerTypes`, und ziehen Sie den **ownerTypeName** auf den Slicer. Das folgende Beispiel zeigt, wie das Datenmodell Beziehungen zwischen den Tabellen unterstützt.

![Treemap mit Filter: Unterstützung von Beziehungen zwischen Tabellen](./media/reports-proc-create-with-odata/reports-create-08_ownertype.png)

Nun verfügen Sie über einen interaktiven Filter, der zum Wechseln zwischen unternehmenseigenen und privaten Geräten verwendet werden kann. Mit diesem Filter können Sie Veränderungen in der Verteilung nachvollziehen.

1. Wählen Sie im Slicer **Company (Unternehmen** ) aus, um zu sehen, dass die unternehmenseigene Geräte Verteilung
2. Wählen Sie im Slicer persönlich aus, um die **persönlichen** Geräte anzuzeigen.

## <a name="next-steps"></a>Nächste Schritte

- Erfahren Sie mehr über das [Erstellen und Verwalten von Beziehungen](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) in Power BI Desktop in der Power BI-Dokumentation.
- Lesen Sie den Artikel [Datenmodell von Intune Data Warehouse](reports-ref-data-model.md).
