---
title: Verbinden mit dem Data Warehouse mit Power BI
titleSuffix: Microsoft Intune
description: Sie können eine Datei herunterladen, um Sie mit Microsoft Power BI zu verwenden, die es Ihnen ermöglicht, interaktive, dynamisch generierte Berichte für Ihren Microsoft Intune-Mandanten zu laden.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/07/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d7a5f67dfd8f7256559cb54d873ed48205ad751
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490424"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Verbinden mit dem Data Warehouse mit Power BI

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Mit der Power BI-App „Konformität“ können Sie interaktive, dynamisch generierte Berichte für Ihren Intune-Mandanten laden. Darüber hinaus können Sie Ihre Mandantendaten über den OData-Link in Power BI laden. Intune stellt Ihrem Mandanten Verbindungseinstellungen zur Verfügung, sodass Sie die folgenden Beispielberichte und -diagramme in Bezug auf Folgendes anzeigen können:  

- Geräte
- Anmeldung
- App-Schutzrichtlinie
- Kompatibilitätsrichtlinie
- Gerätekonfigurierungsprofile
- Softwareupdates
- Protokolle zum Gerätebestand

Es werden auch Trends für die Registrierung, die Konformität, das Gerätekonfigurierungsprofil und Softwareupdates hervorgehoben. Beispieldiagramme und Berichte wenden benutzerfreundliche Filter auf den Zeichenbereich an. Um erweiterte Filter zu verwenden, sehen Sie sich den Bereich **Filter** in Power BI Desktop an.

Die folgenden Schritte zeigen, wie Sie die Power BI-Datei herunterladen und wie Sie den OData-Link mit Power BI verwenden.

[!INCLUDE [reports-credential-reqs](../includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>Installieren von Power BI

Installieren Sie die neueste Version von [Power BI Desktop](https://aka.ms/intune/datawarehouseapi/installpowerbi). Weitere Informationen finden Sie unter [Power BI Desktop](https://powerbi.microsoft.com/desktop).

## <a name="load-the-data-and-reports-using-the-power-bi-intune-compliance-data-warehouse-app"></a>Laden der Daten und Berichte mit der Power BI-App „Intune-Konformität (Data Warehouse)“

Die Power BI-App [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) enthält Informationen zu Ihrem Mandanten und verschiedene vordefinierte auf dem Datenmodell „Data Warehouse“ basierende Berichte.

1. Navigieren Sie zur Seite **AppSource** der App [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp), um den Installationsvorgang zu starten.
2. Klicken Sie auf die Schaltfläche **jetzt starten** , und klicken Sie dann auf **weiter**.
3. Wenn Sie aufgefordert werden, die Power BI APP zu installieren, klicken Sie auf **Installieren**.
4. Nachdem die Installation abgeschlossen ist, klicken Sie auf die APP-Kachel **InTune-Konformität (Data Warehouse)** .
5. Klicken Sie auf die Schaltfläche **Verbinden**. Dann wird das Dialogfeld **Connect to Intune Compliance (Data Warehouse)** (Verbindung mit der App „Intune Compliance (Data Warehouse)“ herstellen) angezeigt.
6. Klicken Sie auf die Schaltfläche **Anmelden**.
7. Melden Sie sich mit einem Benutzerkonto an, das Zugriff auf das Intune Data Warehouse für den Mandanten hat und Berichte enthält, die Sie sich ansehen möchten.
8. Um das enthaltene Dashboard anzuzeigen, klicken Sie auf die Registerkarte **Dashboards** , und klicken Sie dann auf das Dashboard Kompatibilitäts **Übersicht** .
9. Wenn Sie alle verfügbaren Berichte anzeigen möchten, klicken Sie auf die Registerkarte **Berichte** , und klicken Sie dann auf den Bericht **Konformität v 1.0** . Durchsuchen Sie die Berichts Seiten, indem Sie auf die Registerkarten am unteren Rand klicken.
10. Um später einfacher zu diesen Berichten zurückzukehren, klicken Sie auf den Stern neben dem Bericht **Compliance V1.0**. Dadurch wird den Bericht Ihren Power BI-Favoriten hinzugefügt.

Alternativ können Sie die App aus dem Intune-Portal installieren:

1. Wählen Sie im Azure-Portal **Überwachung + Verwaltung** > **Intune** aus. Sie können auch Ressourcen für Intune suchen.
2. Öffnen Sie das Blatt **Intune Data Warehouse einrichten**.
3. Wählen Sie **Power BI-App abrufen** aus, um auf vorab erstellte Power BI-Berichte zuzugreifen und diese für Ihren Mandanten im Browser freizugeben.
4. Führen Sie die oben aufgeführten Schritte 2 bis 10 aus.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>Laden der Daten in Power BI mit dem OData-Link

Wenn der Client bei Azure AD authentifiziert ist, verbindet sich die OData-URL mit dem RESTful-Endpunkt in der Data Warehouse-API, der das Datenmodell für Ihren Berichtserstellungsclient verfügbar macht. Um mit Power BI Desktop eine Verbindung herzustellen und Ihre eigene Berichte zu erstellen, gehen Sie wie folgt vor. Sie sind nicht auf Power BI Desktop festgelegt, sondern können Ihres bevorzugtes analytisches Tools mit der OData-URL verwenden. Die gilt unter der Voraussetzung, dass der Client die OAuth 2.0-Authentifizierung und den OData v4. 0-Standard unterstützt.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf der rechten Seite des Übersichts Blatts im Abschnitt **andere Tasks** auf **InTune-Data Warehouse einrichten** . Das Blatt **InTune-Data Warehouse** wird angezeigt.
3. Rufen Sie die benutzerdefinierte Feed-URL auf dem Blatt „Berichterstellung“ ab, z. B:<br>
    `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`
4. Öffnen Sie **Power BI Desktop**.
5. Wählen Sie **Datei**aus,  > **Daten erhalten**. Wählen Sie **OData-Feed** aus.
6. Wählen Sie **Standard**.
7. Geben Sie die **OData-URL** in das URL-Feld ein, oder fügen Sie sie ein.
8. Wählen Sie **OK** aus.
9. Wenn Sie Ihren Mandanten noch nicht über den Power BI Desktop-Client bei Azure AD authentifiziert haben, geben Sie Ihre Anmeldeinformationen ein. Um auf Ihre Daten zugreifen zu können, müssen Sie mithilfe von OAuth 2.0 bei Azure Active Directory (Azure AD) eine Autorisierung durchführen.  
    1. Wählen Sie **Organisationskonto** aus.  
    2. Geben Sie Ihren Benutzernamen und Ihr Kennwort ein.  
    3. Wählen Sie **Anmelden** aus.  
    4. Wählen Sie **Verbinden** aus.  
10. Wählen Sie **Laden** aus.

## <a name="next-steps"></a>Nächste Schritte

Hier finden Sie Informationen zu Ihrer Umgebung, z.B. der Anzahl der registrierten Geräte, nach Tagen innerhalb der letzten Woche sortiert. Mit den Power BI-Berichten auf dem entsprechenden Blatt in Azure zu Intune Data Warehouse können Sie sich einen Überblick über die Zusammensetzung Ihrer Intune-Mandanten- und Clients verschaffen. Intune bietet jedoch eine Anzahl von weitere Möglichkeiten, um die Daten zu erweitern oder wiederzuverwenden. Power BI und die Intune Data Warehouse-API bieten zusätzliche Funktionen wie z.B:

<!-- - You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
- Ihre Mandantendaten sind organisiert, damit Sie die Daten auswerten können. Weitere Informationen dazu, wie die Daten organisiert werden, finden Sie unter [Data Warehouse-Datenmodell](reports-ref-data-model.md).
- Sie können von einer RESTful-Schnittstelle auf die Daten zugreifen und die Daten in Ihre eigene App einbeziehen. Weitere Informationen finden Sie unter [Abrufen von Daten aus der Intune-Data Warehouse-API mit einem REST-Client)](../reports-proc-data-rest.md).
