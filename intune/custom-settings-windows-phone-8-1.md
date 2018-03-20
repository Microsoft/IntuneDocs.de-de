---
title: "Benutzerdefinierte Microsoft Intune-Einstellungen für Windows Phone 8.1-Geräte"
titleSuffix: 
description: "Erfahren Sie etwas über die Einstellungen, die Sie in einem benutzerdefinierten Windows Phone 8.1-Profil verwenden können."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f45b2dd9cab0ccfd912d1f1348d90264bf8906b8
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-phone-81"></a>Benutzerdefinierte Microsoft Intune-Geräteeinstellungen für Windows Phone 8.1-Geräte

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Weisen Sie mithilfe des **benutzerdefinierten** Profils für Windows Phone 8.1 von Microsoft Intune die OMA-URI-Einstellungen zu, um Features auf Windows Phone 8.1-Geräten zu steuern. Dies sind die Standardeinstellungen, die viele Hersteller von mobilen Geräten verwenden, um Gerätefunktionen zu steuern.

Diese Funktion soll es Ihnen ermöglichen, Einstellungen zuzuweisen, die nicht mit anderen Intune-Richtlinien konfigurierbar sind.

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Benutzerdefinierte Richtlinieneinstellungen für Windows Phone 8.1-Geräte

1. Anweisungen zu den ersten Schritten finden Sie unter [Konfigurieren von benutzerdefinierten Geräteeinstellungen in Microsoft Intune](custom-settings-configure.md).
2. Klicken Sie im Bereich **Custom OMA-URI Settings** (Benutzerdefinierte OMA-URI-Einstellungen) auf die Option **Hinzufügen**, um mindestens eine OMA-URI-Einstellung hinzuzufügen.
3. Konfigurieren Sie im Bereich **Zeile hinzufügen** die folgenden Werte für jede Einstellung:
    - **Name:** Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie sie in der Liste der Einstellungen einfacher identifizieren können.
    - **Beschreibung:** Geben Sie eine Beschreibung ein, die eine Übersicht über die Einstellung bietet, und andere relevante Informationen, die Ihnen die Suche danach erleichtern.
    - **OMA-URI:** Geben Sie den OMA-URI an, für den Sie eine Einstellung bereitstellen möchten.
    - **Datentyp:** Wählen Sie den Datentyp aus, in dem Sie diese OMA-URI-Einstellung angeben. Wählen Sie aus folgenden Typen aus: **Zeichenfolge**, **Zeichenfolge (XML)**, **Datum und Uhrzeit**, **Integer**, **Gleitkomma**, **Boolesch** oder **Base64** aus.
    - **Wert:** Geben Sie den gewünschten Wert oder die Datei an, der bzw. die dem von Ihnen eingegebenen OMA-URI zugeordnet werden soll.

4. Klicken Sie abschließend auf **OK**, und fahren Sie bei Bedarf mit dem Hinzufügen weiterer Einstellungen fort.
