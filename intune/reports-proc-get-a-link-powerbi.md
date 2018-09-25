---
title: Verbinden mit dem Data Warehouse mit Power BI
titlesuffix: Microsoft Intune
description: Sie können eine Datei herunterladen, um Sie mit Microsoft Power BI zu verwenden, die es Ihnen ermöglicht, interaktive, dynamisch generierte Berichte für Ihren Microsoft Intune-Mandanten zu laden.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5020b1653dd92587805e471e80808e34f3007a84
ms.sourcegitcommit: 63b74a60aafa8d2d6af0594448ae0471fbd79194
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494029"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Verbinden mit dem Data Warehouse mit Power BI

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Sie können eine Datei herunterladen, um Sie mit Microsoft Power BI zu verwenden, die es Ihnen ermöglicht, interaktive, dynamisch generierte Berichte für Ihren Intune-Mandanten zu laden. Die Data Warehouse Power BI-Datei (PBIX) enthält die Verbindungseinstellungen für Ihren Mandanten und die folgenden Beispielberichte und Diagramme:  

  -  Geräte
  -  Anmeldung
  -  App-Schutzrichtlinie
  -  Kompatibilitätsrichtlinie
  -  Gerätekonfigurierungsprofile
  -  Softwareupdates
  -  Protokolle zum Gerätebestand

Es werden auch Trends für die Registrierung, die Konformität, das Gerätekonfigurierungsprofil und Softwareupdates hervorgehoben. Beispieldiagramme und Berichte wenden benutzerfreundliche Filter auf den Zeichenbereich an. Um erweiterte Filter zu verwenden, sehen Sie sich den Bereich **Filter** in Power BI Desktop an.

Die folgenden Schritte zeigen, wie Sie die Power BI-Datei herunterladen und wie Sie den OData-Link mit Power BI verwenden.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>Installieren von Power BI

Installieren Sie die neueste Version von Power BI Desktop. Sie können Power BI Desktop aus [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop) herunterladen.

## <a name="load-the-data-and-reports-using-the-power-bi-file-pbix"></a>Laden der Daten und Berichte mit der Power BI-Datei (PBIX)

Die Power BI-Datei (PBIX) enthält Verbindungsinformationen für Ihren Mandanten und eine Reihe von vordefinierten Berichten, die auf dem Data Warehouse-Datenmodell basieren. Öffnen Sie die Datei in Power BI Desktop, und melden Sie sich bei Azure AD an. Der Bericht lädt die Daten aus Ihrem Intune-Mandanten.

> [!Important]  
> Jede Power BI-Datei (PBIX) kann je nach Standortort des Mandanten unterschiedlich sein. Wenn Sie mehrere Intune-Mandanten verwalten, sollten Sie darauf achten, dass Sie die Datei verwenden, die Sie aus dem Azure-Portal heruntergeladen haben, während Sie in diesem Mandanten angemeldet waren.  

1.  Wählen Sie im Azure-Portal **Überwachung + Verwaltung** > **Intune** aus. Sie können auch Ressourcen nach **Intune** durchsuchen.  
2.  Öffnen Sie das Blatt **Microsoft Intune Data Warehouse API (Preview)** (Microsoft Intune Data Warehouse-API (Vorschau)).
3.  Wählen Sie **Power BI-Datei herunterladen** aus. Die Datei mit der Erweiterung PBIX wird an den angegebenen Speicherort heruntergeladen.
4.  Öffnen Sie die Datei mit Power BI. Die *Intune Data Warehouse-Berichte* werden geladen. Es kann jedoch eine Weile dauern, Ihre Mandantendaten abzurufen.
5.  Wählen Sie **Aktualisieren** aus, um Ihre Mandantendaten zu laden und die Berichte zu überprüfen.
6.  Wenn Power BI Ihre Azure Active Directory-Anmeldeinformationen noch nicht authentifiziert hat, werden Sie von Power BI aufgefordert, Ihre Anmeldeinformationen bereitzustellen. Wenn Sie Ihre Anmeldeinformationen auswählen, wählen Sie **Organisationskonto** als Authentifizierungsmethode aus.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>Laden der Daten in Power BI mit dem OData-Link

Wenn der Client bei Azure AD authentifiziert ist, verbindet sich die OData-URL mit dem RESTful-Endpunkt in der Data Warehouse-API, der das Datenmodell für Ihren Berichtserstellungsclient verfügbar macht. Um mit Power BI Desktop eine Verbindung herzustellen und Ihre eigene Berichte zu erstellen, gehen Sie wie folgt vor. Sie sind nicht auf Power BI Desktop festgelegt, sondern können Ihres bevorzugtes analytisches Tools mit der OData-URL verwenden. Die gilt unter der Voraussetzung, dass der Client die OAuth 2.0-Authentifizierung und den OData v4. 0-Standard unterstützt.

1.  Wählen Sie im Azure-Portal **Überwachung + Verwaltung** > **Intune** aus. Sie können auch Ressourcen nach **Intune** durchsuchen.  
2.  Öffnen Sie das Blatt **Microsoft Intune Data Warehouse API (Preview)** (Microsoft Intune Data Warehouse-API (Vorschau)).
3. Rufen Sie die benutzerdefinierte Feed-URL aus dem Berichtsblatt ab, z.B. `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`.
4. Öffnen Sie **Power BI Desktop**.
5. Wählen Sie **Startseite** > **Daten abrufen** aus. Wählen Sie **OData-Feed** aus.
6. Wählen Sie **Standard**.
7. Geben Sie die **OData-URL** in das URL-Feld ein, oder fügen Sie sie ein.
8. Wählen Sie **OK** aus.
9. Wenn Sie Ihren Mandanten noch nicht über den Power BI Desktop-Client bei Azure AD authentifiziert haben, geben Sie Ihre Anmeldeinformationen ein. Um auf Ihre Daten zugreifen zu können, müssen Sie mithilfe von OAuth 2.0 bei Azure Active Directory (Azure AD) eine Autorisierung durchführen.  
    1.  Wählen Sie **Organisationskonto** aus.  
    2.  Geben Sie Ihren Benutzernamen und Ihr Kennwort ein.  
    3.  Wählen Sie **Anmelden** aus.  
    4.  Wählen Sie **Verbinden** aus.  
10. Wählen Sie **Laden** aus.

## <a name="next-steps"></a>Nächste Schritte

Hier finden Sie Informationen zu Ihrer Umgebung, z.B. der Anzahl der registrierten Geräte, nach Tagen innerhalb der letzten Woche sortiert. Mithilfe der Berichte und mithilfe der Intune Data Warehouse-Power BI-Datei (PBIX), die aus dem Blatt in Azure abgerufen wurde, erhalten Sie auch Einblicke in Ihren Intune-Mandanten und die Clientauffüllung. Intune bietet jedoch eine Anzahl von weitere Möglichkeiten, um die Daten zu erweitern oder wiederzuverwenden. Power BI und die Intune Data-Warehouse-API bieten Ihnen noch viele weiter Vorteile:

<!-- -  You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
 -  Ihre Mandantendaten sind organisiert, damit Sie die Daten auswerten können. Weitere Informationen dazu, wie die Daten organisiert werden, finden Sie unter [Data Warehouse-Datenmodell](reports-ref-data-model.md).
 -  Sie können von einer RESTful-Schnittstelle auf die Daten zugreifen und die Daten in Ihre eigene App einbeziehen. Weitere Informationen finden Sie unter [Abrufen von Daten aus der Intune-Data Warehouse-API mit einem REST-Client)](reports-proc-data-rest.md).
