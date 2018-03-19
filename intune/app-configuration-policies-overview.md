---
title: "App-Konfigurationsrichtlinien für Intune"
titlesuffix: Microsoft Intune
description: "Erfahren Sie, wie Sie App-Konfigurationsrichtlinien in Intune für iOS- oder Android-Geräte verwenden."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 52e0906b58680fa0b5628b2b5fc7445f8135658a
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="app-configuration-policies-for-intune"></a>App-Konfigurationsrichtlinien für Intune

Geben Sie Einstellungen dafür an, wenn Benutzer eine iOS- oder Android-App mit App-Konfigurationsrichtlinien in Microsoft Intune ausführen. Beispielsweise kann eine App vom Benutzer Folgendes anfordern:

- Eine benutzerdefinierte Portnummer
- Spracheinstellungen
- Sicherheitseinstellungen
- Brandingeinstellungen, z. B. ein Unternehmenslogo

Wenn Benutzer diese Einstellungen nicht ordnungsgemäß eingeben, kann dies zur erhöhten Belastung Ihres Helpdesks führen und die Annahme der neuen Apps verlangsamen.

Mit App-Konfigurationsrichtlinien können Sie diese Probleme beseitigen, da Sie diese Einstellungen in einer Richtlinie Benutzern zuweisen können, bevor diese die App ausführen. Die Einstellungen werden dann automatisch bereitgestellt, und die Benutzer müssen keine weitere Aktion durchführen.

Sie weisen diese Richtlinien nicht direkt Benutzern und Geräten zu. Stattdessen verknüpfen Sie eine Richtlinie mit einer App und weisen dann die App zu. Die Richtlinieneinstellungen werden immer dann verwendet, wenn die Anwendung danach sucht (in der Regel beim ersten Ausführen).

Ihnen stehen zwei Optionen für das Verwenden der App-Konfigurationen mit Intune zur Verfügung:
 - **Verwaltete Geräte**  
   Das Gerät wird von Intune als MDM-Anbieter (mobile device manager, mobile Geräteverwaltung) verwaltet.
 - **Verwaltete Apps**  
   Eine App wird ohne Geräteregistrierung verwaltet.

## <a name="apps-that-support-app-configuration"></a>Apps, die die App-Konfiguration unterstützen

Sie können App-Konfigurationsrichtlinien für Apps verwenden, die diese unterstützen. Für die Unterstützung der App-Konfiguration in Intune müssen Apps dafür geschrieben sein, die Verwendung von App-Konfigurationen zu unterstützen. Wenden Sie sich für Details an Ihren App-Anbieter.

Sie können Ihre branchenspezifischen Apps dafür vorbereiten, indem Sie entweder das Intune App SDK in die App integrieren oder die App nach der Entwicklung damit umschließen. Das für IOS und Android verfügbare Intune App SDK aktiviert Ihre App für Intune-App-Schutzrichtlinien. Es zielt darauf ab, die vom App-Entwickler vorzunehmenden Codeänderungen zu minimieren. Weitere Informationen finden Sie unter [Übersicht über das Intune App SDK](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Graph-API-Unterstützung für die App-Konfiguration

Zusätzlich können Sie die Graph-API verwenden, um die App-Konfiguration abzuschließen. Weitere Informationen finden Sie in der [Graph-API-Referenz für die MAM-Zielkonfiguration](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>Nächste Schritte

### <a name="managed-devices"></a>Verwaltete Geräte

 - Erfahren Sie, wie Sie die App-Konfiguration mit Ihren iOS-Geräten verwenden.  Siehe [Add app configuration policies for managed iOS devices (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete iOS-Geräte)](app-configuration-policies-use-ios.md).
 - Erfahren Sie, wie Sie die App-Konfiguration mit Ihren Android-Geräten verwenden.  Siehe [Add app configuration policies for managed Android devices (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android-Geräte)](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Verwaltete Apps

 - Erfahren Sie, wie Sie die App-Konfiguration mit verwalteten Geräten verwenden. Siehe [Add app configuration policies for managed apps without device enrollment (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Apps ohne Geräteregistrierung)](app-configuration-policies-managed-app.md).