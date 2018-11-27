---
title: Konfigurationsrichtlinien für verwaltete Apps ohne Geräteregistrierung
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Richtlinien für verwaltete Apps ohne Geräteregistrierung konfigurieren.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2407225bfd0cdb5892663bf2e66de36157aaf4e0
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182005"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Apps ohne Geräteregistrierung

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Sie können App-Konfigurationsrichtlinien mit verwalteten Apps, die das Intune App-SDK unterstützen, sogar auf nicht registrierten Geräten verwenden. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie die Workload **Client-Apps** aus.
4. Wählen Sie in der Gruppe **Verwalten** **App-Konfigurationsrichtlinien** und dann **Hinzufügen** aus.
5. Legen Sie die folgenden Details fest:
    - **Name**  
      Der Name des Profils, das im Azure-Portal angezeigt wird
    - **Beschreibung**  
      Die Beschreibung des Profils, das im Azure-Portal angezeigt wird
    - **Geräteregistrierungstyp**  
      Klicken Sie auf **Apps verwalten**.
6. Klicken Sie auf  **Zugeordnete App** , um die App auszuwählen, die Sie konfigurieren möchten. Wählen Sie die App aus der Liste der Apps aus, die Sie genehmigt und mit Intune synchronisiert haben.
7. Geben Sie für jede von der App unterstützte Konfigurationseinstellung den **Namen** und den **Wert** ein, und wählen Sie die Auslassungspunkte (**…**) aus.  
    Wählen Sie zum Löschen einer Konfiguration die Auslassungspunkte (**...**) und dann auf **Löschen** aus.  
    
Für das Intune App SDK aktivierte Apps unterstützen Konfigurationen in Schlüssel-Wert-Paaren. Weitere Informationen zu den unterstützten Schlüssel-Wert-Konfigurationen finden Sie in der Dokumentation zu den einzelnen Apps. Beachten Sie, dass Sie Tokens verwenden können, die dynamisch mit den von der Anwendung generierten Daten aufgefüllt werden. Informationen zu den Konfigurationsrichtlinieneinstellungen für die Outlook für iOS-App finden Sie unter [Verwalten der Konfiguration der Outlook für iOS-App mit Microsoft Intune](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx).

## <a name="configuration-values-for-using-tokens"></a>Konfigurationswerte für das Verwenden von Token

Intune kann bestimmte Token generieren und sie an die verwaltete Anwendung senden. Wenn Ihre App-Konfiguration beispielsweise eine E-Mail-Einstellung verwenden kann, können Sie mithilfe eines Tokens dynamische E-Mail hinzufügen. Geben Sie den Namen, der von der App erwartet wird, in das Feld **Name** und anschließend `\{\{mail\}\}` in das Feld **Wert** ein.

Intune unterstützt folgende Tokentypen in den Konfigurationseinstellungen. Andere benutzerdefinierte Schlüssel-Wert-Paare werden nicht unterstützt.

- \{\{userPrincipalName\}\}: z.B.John@contoso.com
- \{\{mail\}\}: z.B.John@contoso.com
- \{\{partialupn\}\}: z.B. John
- \{\{accountid\}\}: z.B. fc0dc142-71d8-4b12-bbea-bae2a8514c81
- \{\{userid\}\}: z.B. 3ec2c00f-b125-4519-acf0-302ac3761822
- \{\{username\}\}: z.B. John Doe
- \{\{PrimarySMTPAddress\}\}. z.B.testuser@ad.domain.com


> [!Note]  
> Die Zeichen \{\{ und \}\} werden nur von Tokentypen verwendet und dürfen nicht für andere Zwecke verwendet werden.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie wie gewöhnlich mit dem [Zuweisen](apps-deploy.md) und [Überwachen](apps-monitor.md) der App fort.
