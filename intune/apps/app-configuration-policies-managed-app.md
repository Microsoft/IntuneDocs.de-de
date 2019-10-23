---
title: Konfigurationsrichtlinien für verwaltete Apps ohne Geräteregistrierung
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Richtlinien für verwaltete Apps ohne Geräteregistrierung konfigurieren.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a31a4777537db6f656dbf9eaf0b30a6e95412a8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72499765"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Apps ohne Geräteregistrierung

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Sie können App-Konfigurationsrichtlinien mit verwalteten Apps, die das Intune App-SDK unterstützen, sogar auf nicht registrierten Geräten verwenden. 

> [!NOTE]
> Apps müssen durch die Intune-App-Schutzrichtlinie involviert werden, sodass App-Konfigurationsrichtlinien für sie gelten. Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie die Workload **Client-Apps** aus.
4. Wählen Sie in der Gruppe **Verwalten** **App-Konfigurationsrichtlinien** und dann **Hinzufügen** aus.
5. Legen Sie die folgenden Details fest:
    - **Name**  
      Der Name des Profils, das im Azure-Portal angezeigt wird
    - **Beschreibung**  
      Die Beschreibung des Profils, das im Azure-Portal angezeigt wird
    - **Geräteregistrierungstyp**  
      Klicken Sie auf **Apps verwalten**.
6. Klicken Sie auf **Zugeordnete App**, um die App auszuwählen, die Sie konfigurieren möchten. Wählen Sie die App aus der Liste der Apps aus, die Sie genehmigt und mit Intune synchronisiert haben.
7. Geben Sie für jede von der App unterstützte Konfigurationseinstellung den **Namen** und den **Wert** ein, und wählen Sie die Auslassungspunkte ( **…** ) aus.  
    Wählen Sie zum Löschen einer Konfiguration die Auslassungspunkte ( **...** ) und dann auf **Löschen** aus.  
    
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
