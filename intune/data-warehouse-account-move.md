---
title: Verschieben Ihrer Intune Data Warehouse-Kontodaten
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Ihre Intune Data Warehouse-Daten sichern, wenn Sie Ihr Konto verschieben.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ee3ccbf9-82fc-4fbf-9d3d-8f05e431d090
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.openlocfilehash: 470bafba548c38870e57a545c4514459dde219b4
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189389"
---
# <a name="move-your-intune-data-warehouse-account-data"></a>Verschieben Ihrer Intune Data Warehouse-Kontodaten 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mit dem Anfordern einer Kontoverschiebung fordern Sie an, dass der Speicherort Ihres Rechenzentrums geändert wird. Nach dem Verschieben wird das Data Warehouse zurückgesetzt und beginnt, ab dem Tag, der für den Beginn der Kontoverschiebung angegeben ist, Daten am neuen Speicherort aufzuzeichnen. Um Ihre vorherigen Data Warehouse-Daten zu sichern, führen Sie die folgenden Schritte aus, **bevor** Sie Ihr Konto verschieben. Die meisten Data Warehouse-Tabellen behalten Daten für 30 Tage bei, sodass Datenlücken in diesen Tabellen 30 Tage nach Ihrer Kontoverschiebung nicht mehr verfügbar sind. Weitere Informationen zur Aufbewahrungsdauer für bestimmte Tabellen finden Sie unter [Datenmodell von Data Warehouse](reports-ref-data-model.md). 

## <a name="back-up-your-data-warehouse-data"></a>Sichern Ihrer Data Warehouse-Datenbanken 

Um Ihre Data Warehouse-Daten zu sichern, müssen Sie die Data Warehouse-Daten mithilfe der Data Warehouse-API in einer *CSV*-Datei speichern:  

1. Wenn Sie ein erstmaliger Benutzer der Data Warehouse-API sind, führen Sie den im folgenden Artikel, [Abrufen von Daten aus der Intune-Data Warehouse-API mit einem REST-Client](reports-proc-data-rest.md), vorgestellten einmaligen Prozess aus.
2. Verwenden Sie das PowerShell-Beispiel mit dem Titel [Access the Intune Data Warehouse with PowerShell (Zugriff auf das Intune Data Warehouse mit PowerShell)](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell), um alle Ihre Daten in CSV-Dateien herunterzuladen. 

## <a name="back-up-your-trend-charts-from-the-azure-portal"></a>Sichern Ihrer Trenddiagramme aus dem Azure-Portal

Einige Trenddiagramme in Ihrer Ansicht des Azure-Portals werden zurückgesetzt. Sie können diese Diagramme durch Ausführen des folgenden Skripts in **Graph** sichern:   

### <a name="terms--conditions-acceptance-reports"></a>Berichte zur Akzeptanz von Nutzungsbedingungen
1. Navigieren Sie im Azure-Portal zu **Microsoft Intune** -> **Geräteregistrierung** -> **Nutzungsbedingungen**.
2. Wählen Sie für jedes Element der **Nutzungsbedingungen** den **Akzeptanzbericht** gefolgt von **Exportieren** aus.
3. Speichern Sie den Bericht lokal.
 
### <a name="app-protection-reports"></a>Hinzufügen von Schutzberichten  
1. Navigieren Sie im Azure-Portal zu **Microsoft Intune** -> **Client-Apps** -> **Status des App-Schutzes**.
2. Klicken Sie zum Speichern jedes Berichts auf das Downloadsymbol (⤓).

### <a name="device-configuration-charts"></a>Gerätekonfigurationsdiagramme 
1. Navigieren Sie im Azure-Portal zu **Microsoft Intune** -> **DeviceConfiguration**.
2. Laden Sie mithilfe des [Graph-Testers](https://developer.microsoft.com/graph/graph-explorer) von Microsoft die Daten hinter den Diagrammen herunter. 
    - Informationen zum Bereitstellungsstatus aller Gerätekonfigurationsprofile für alle Geräte finden Sie unter [Gerätebereitstellungsstatus](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content).

    - Informationen zum Bereitstellungsstatus aller Gerätekonfigurationsprofile für alle Benutzer finden Sie unter [Benutzerbereitstellungsstatus](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content).

    - Informationen zum Profilbereitstellungsstatus finden Sie unter [Bereitstellungsstatus zur Verfügung stellen](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&$expand=deviceStatusOverview).
  
    > [!NOTE]
    > Für den Zugriff auf die Gerätekonfigurations- und Bereitstellungsstatusinformationen benötigen Sie ein gültiges Authentifizierungstoken.

## <a name="device-enrollment-charts"></a>Geräteregistrierungsdiagramme
1. Navigieren Sie im Azure-Portal zu **Microsoft Intune** -> **DeviceEnrollment**.
2. Laden Sie mithilfe des [Graph-Testers](https://developer.microsoft.com/graph/graph-explorer) von Microsoft die Daten hinter den Diagrammen herunter.
    - Für Informationen zum Registrierungsstatus kopieren Sie diese [Registrierungsstatusabfrage](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends()/content), und fügen Sie sie in den [Graph-Tester](https://developer.microsoft.com/graph/graph-explorer) ein.
    - Für Informationen über die gravierendsten Registrierungsfehler dieser Woche kopieren Sie diese [Registrierungsfehlerabfrage](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures(period=null)/content), und fügen Sie sie in den [Graph-Tester](https://developer.microsoft.com/graph/graph-explorer) ein.

    > [!NOTE]
    > Für den Zugriff auf die Geräteregistrierungsdaten benötigen Sie ein gültiges Authentifizierungstoken. 

## <a name="after-a-data-warehouse-account-move"></a>Nach einer Data Warehouse-Kontoverschiebung

Nach der Data Warehouse-Kontoverschiebung sehen Sie in Intune, dass das Data Warehouse zurückgesetzt wurde und Ihre Daten nun an dem neuen Speicherort gespeichert sind. Die Diagramme und Exportoptionen werden zurückgesetzt, und Sie erhalten eine Benachrichtigung. Wenn Sie darauf klicken, werden Sie zu einem Artikel geleitet, in dem erläutert wird, warum die Diagramme zurückgesetzt wurden.  

## <a name="data-warehouse-move-example"></a>Data Warehouse-Verschiebungsbeispiel 

Kunde X fordert eine Kontoverschiebung beginnend am 06.01.2018 an. Als Antwort auf die Anforderung erhält der Kunde einen Link zu einer Dokumentation, in der ausführlich die Schritte zum Sichern seines vorherigen Data Warehouse beschrieben werden. Am 06.01.2018 werden das Data Warehouse und die von ihm unterstützten Diagramme zurückgesetzt und das Speichern von Daten im neuen Rechenzentrum beginnt. 

## <a name="next-steps"></a>Nächste Schritte

 - Erfahren Sie [jede Woche die Neuerungen in Intune](whats-new.md). Sie erhalten auch Informationen zu bevorstehenden Änderungen, wichtige Hinweise zum Dienst und Informationen zu vorherigen Releases.
 - Lesen Sie den [Microsoft Intune-Blog](http://go.microsoft.com/fwlink/?LinkID=273882).
