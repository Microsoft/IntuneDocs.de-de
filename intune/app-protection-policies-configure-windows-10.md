---
title: Vorbereitungen zum Konfigurieren von App-Schutzrichtlinien für Windows 10
titleSuffix: Microsoft Intune
description: Einrichten des MAM-Anbieters (Mobile Application Management) in Azure AD
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0f8e5c6319e01404500f5a31fabd1baeb3520067
ms.sourcegitcommit: 0f8d46d644f78609fae8bf91197ae77c7af45d23
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2018
ms.locfileid: "40251752"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Vorbereitungen zum Konfigurieren von App-Schutzrichtlinien für Windows 10 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Aktivieren Sie die Verwaltung für mobile Anwendungen (Mobile Application Management, MAM) für Windows 10, indem Sie den MAM-Anbieter in Azure AD festlegen. Durch die Festlegung eines MAM-Anbieters in Azure AD können Sie den Registrierungsstatus definieren, wenn Sie eine neue WIP-Richtlinie (Windows Information Protection) in Intune erstellen. Der Registrierungsstatus kann entweder „MAM“ oder „Mobile Geräteverwaltung (MDM)“ lauten.

## <a name="to-configure-the-mam-provider"></a>Konfigurieren des MAM-Anbieters

1. Melden Sie sich beim Azure-Portal an, und klicken Sie auf **Azure Active Directory**.

2. Wählen Sie **Mobilität (MDM und MAM)** in der Gruppe **Verwalten** aus.

3. Klicken Sie auf **Microsoft Intune**.

4. Konfigurieren Sie die Einstellungen in der Gruppe **Standard-MAM-URLs wiederherstellen** auf dem Blatt **Konfigurieren**.

   **MAM-Benutzerbereich**  
   Verwenden Sie die automatische Registrierung von MAM, um Unternehmensdaten auf den Windows-Geräten Ihrer Mitarbeiter zu verwalten. Die automatische MAM-Registrierung wird für BYOD-Szenarios konfiguriert.<ul><li>**Keine**<br>Wählen Sie diese Option, wenn kein Benutzer in MAM registriert werden kann.</li><li>**Einige**<br>Wählen Sie Azure AD-Gruppen aus, die Benutzer enthalten, die in MAM registriert werden.</li><li>**Alle**<br>Wählen Sie diese Option, wenn alle Benutzer in MAM registriert werden können.</li></ul>

   **URL für MDM-Nutzungsbedingungen**  
   Die URL für MAM-Nutzungsbedingungen wird unter Microsoft Intune nicht unterstützt. Dieses Eingabefeld muss leer bleiben, damit die Schutzrichtlinien angewendet werden können.

   **URL für MDM-Ermittlung**  
   Die URL des Endpunkt der Registrierung des MAM-Diensts. Der Registrierungsendpunkt wird zum Registrieren von Geräten für die Verwaltung mit dem MAM-Dienst verwendet.

   **URL für MAM-Kompatibilität**  
   Die URL für MAM-Konformität wird für Microsoft Intune nicht unterstützt. Dieses Eingabefeld muss leer bleiben, damit die Schutzrichtlinien angewendet werden können. 

5.  Klicken Sie auf **Speichern**.

## <a name="next-steps"></a>Nächste Schritte

[Erstellen einer WIP-App-Schutzrichtlinie](windows-information-protection-policy-create.md)
