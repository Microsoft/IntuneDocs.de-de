---
title: Konfigurieren von App-Schutzrichtlinien für Windows 10
titleSuffix: Microsoft Intune
description: In diesem Thema wird beschrieben, wie Sie App-Schutzrichtlinien (App Protection Policies, APP) für Windows 10-Geräte konfigurieren können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66cf454290903705d8500c2b1f9a07c9097351bf
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781755"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Vorbereitungen zum Konfigurieren von App-Schutzrichtlinien für Windows 10 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Aktivieren Sie die Verwaltung für mobile Anwendungen (Mobile Application Management, MAM) für Windows 10, indem Sie den MAM-Anbieter in Azure AD festlegen. Durch die Festlegung eines MAM-Anbieters in Azure AD können Sie den Registrierungsstatus definieren, wenn Sie eine neue WIP-Richtlinie (Windows Information Protection) in Intune erstellen. Der Registrierungsstatus kann entweder „MAM“ oder „Mobile Geräteverwaltung (MDM)“ lauten.

## <a name="to-configure-the-mam-provider"></a>Konfigurieren des MAM-Anbieters

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Zum Wechseln von Dashboards wählen Sie **Alle Dienste** und dann **M365 Azure Active Directory** aus.
3. Wählen Sie **Azure Active Directory** aus.
4. Wählen Sie **Mobilität (MDM und MAM)** in der Gruppe **Verwalten** aus.
5. Klicken Sie auf **Microsoft Intune**.
6. Konfigurieren Sie die Einstellungen in der Gruppe **Standard-MAM-URLs wiederherstellen** im Bereich **Konfigurieren**.

   **MAM-Benutzerbereich**  
   Verwenden Sie die automatische Registrierung von MAM, um Unternehmensdaten auf den Windows-Geräten Ihrer Mitarbeiter zu verwalten. Die automatische MAM-Registrierung wird für BYOD-Szenarios konfiguriert.<ul><li>**Keine**<br>Wählen Sie diese Option, wenn kein Benutzer in MAM registriert werden kann.</li><li>**Einige**<br>Wählen Sie Azure AD-Gruppen aus, die Benutzer enthalten, die in MAM registriert werden.</li><li>**Alle**<br>Wählen Sie diese Option, wenn alle Benutzer in MAM registriert werden können.</li></ul>

   **URL für MDM-Nutzungsbedingungen**  
   Die URL für MAM-Nutzungsbedingungen wird unter Microsoft Intune nicht unterstützt. Dieses Eingabefeld muss leer bleiben, damit die Schutzrichtlinien angewendet werden können.

   **URL für MDM-Ermittlung**  
   Die URL des Endpunkt der Registrierung des MAM-Diensts. Der Registrierungsendpunkt wird zum Registrieren von Geräten für die Verwaltung mit dem MAM-Dienst verwendet.

   **URL für MAM-Kompatibilität**  
   Die URL für MAM-Konformität wird für Microsoft Intune nicht unterstützt. Dieses Eingabefeld muss leer bleiben, damit die Schutzrichtlinien angewendet werden können. 

7. Klicken Sie auf **Speichern**.

## <a name="next-steps"></a>Nächste Schritte

[Erstellen einer WIP-App-Schutzrichtlinie](windows-information-protection-policy-create.md)
