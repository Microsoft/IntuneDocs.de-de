---
title: Kategorisieren von Geräten in Gruppen in Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Geräte zur einfacheren Verwaltung in Gruppen kategorisieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ee8bc3cdee9f61a901854e08000e9e2cbbb2864
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955370"
---
# <a name="categorize-devices-into-groups"></a>Kategorisieren von Geräten in Gruppen

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Zur einfacheren Geräteverwaltung können Sie Microsoft Intune-Gerätekategorien verwenden, um Geräte automatisch zu Gruppen hinzuzufügen, die auf von Ihnen definierten Kategorien basieren.

Gerätekategorien verwenden den folgenden Workflow:
1. Erstellen Sie Kategorien, die Benutzer beim Registrieren ihrer Geräte verwenden können.
2. Wenn Benutzer von iOS- und Android-Geräten ihre Geräte registrieren, müssen sie aus der Liste der von Ihnen konfigurierten Kategorien eine Kategorie auswählen. Benutzer müssen die Unternehmensportalwebsite verwenden, um einem Windows-Gerät eine Kategorie zuzuweisen.
3. Dann können Sie Richtlinien und Apps für diese Gruppen bereitstellen.

Sie können beliebige Gerätekategorien erstellen. Beispiel:
- Point-of-Sale-Gerät
- Demogerät
- Sales
- Kontoführung
- Manager

## <a name="how-to-configure-device-categories"></a>Konfigurieren von Gerätekategorien

### <a name="step-1-create-device-categories-on-the-intune-blade-of-the-azure-portal"></a>Schritt 1: Erstellen von Gerätekategorien auf dem Blatt „Intune“ im Azure-Portal
1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an, und navigieren Sie zu **Geräte** > **Gerätekategorien**.
2. Wählen Sie auf der Seite **Gerätekategorien** die Option **Erstellen** aus, um eine neue Kategorie hinzuzufügen.
3. Geben Sie auf dem Blatt **Gerätekategorie erstellen** einen **Namen** für die neue Kategorie und optional eine **Beschreibung** ein.
4. Wenn Sie fertig sind, klicken Sie auf **Erstellen**. Sie können die neue Kategorie in der Liste der Kategorien sehen.

Verwenden Sie den Kategorienamen des Geräts zum Erstellen von Azure Active Directory-Sicherheitsgruppen (Azure AD) in Schritt 2.

### <a name="step-2-create-azure-active-directory-security-groups"></a>Schritt 2: Erstellen von Azure Active Directory-Sicherheitsgruppen
In diesem Schritt erstellen Sie dynamische Gruppen im Azure-Portal auf Basis der Gerätekategorie und des Gerätekategorienamens.

Wenn Sie fortfahren möchten, erhalten Sie weitere Informationen zum [Verwenden von Attributen zum Erstellen erweiterter Regeln](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) in der Dokumentation zu Azure Active Directory.

Verwenden Sie die Informationen in diesem Abschnitt zum Erstellen einer Gerätegruppe mit einer erweiterten Regel mithilfe des Attributs **deviceCategory**. Beispiel: **device.deviceCategory -eq** *Gerätekategoriename, den Sie über die Intune-Verwaltungskonsole erhalten haben*.

Wenn nach dem Konfigurieren von Gerätegruppen Benutzer ihre Geräte registrieren, wird ihnen eine Liste der von Ihnen konfigurierten Kategorien angezeigt. Nachdem sie eine Kategorie ausgewählt und die Registrierung abgeschlossen haben, wird ihr Gerät der Active Directory-Sicherheitsgruppe hinzugefügt, die der gewählten Kategorie entspricht.

### <a name="view-the-categories-of-devices-that-you-manage"></a>Anzeigen der Kategorien von Geräten, die Sie verwalten

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an, und navigieren Sie zu **Geräte** > **Alle Geräte**.

2. Sehen Sie sich in der Liste der Geräte die Spalte **Gerätekategorie** an.

Wenn die Spalte **Gerätekategorie** nicht angezeigt wird, klicken Sie auf **Spalten** > **Kategorie** > **Übernehmen**.

### <a name="change-the-category-of-a-device"></a>Ändern der Gerätekategorie

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an, und navigieren Sie zu **Geräte** > **Alle Geräte** > das hinzuzufügende Gerät auswählen > **Eigenschaften**.
2. Auf dem nächsten Blatt können Sie die **Gerätekategorie** des ausgewählten Geräts in einen beliebigen Kategorienamen ändern, den Sie zuvor konfiguriert haben.

## <a name="after-you-configure-device-groups"></a>Nach dem Konfigurieren von Gerätegruppen

Wenn Benutzer von iOS- und Android-Geräten ihre Geräte registrieren, müssen sie aus der Liste der von Ihnen konfigurierten Kategorien eine Kategorie auswählen. Nachdem sie eine Kategorie ausgewählt und die Registrierung abgeschlossen haben, wird ihr Gerät zu der Intune-Gerätegruppe oder der Active Directory-Sicherheitsgruppe hinzugefügt, die der gewählten Kategorie entspricht.

Benutzer unter Windows sollten die Unternehmensportalwebsite verwenden, um eine Kategorie auszuwählen.

Unabhängig von der Plattform können Ihre Endbenutzer nach der Registrierung des Geräts jederzeit auf „portal.manage.microsoft.com“ zugreifen. Weisen Sie den Benutzer dazu an, auf die Unternehmensportalwebsite zuzugreifen und zu **Meine Geräte** zu navigieren. Er hat dann die Möglichkeit, ein auf der Seite aufgeführtes registriertes Gerät sowie eine Kategorie auszuwählen.

Nach Auswahl der Kategorie wird das Gerät automatisch zur entsprechenden Gruppe hinzugefügt, die Sie erstellt haben. Wenn ein Gerät bereits registriert wurde, bevor Sie die Kategorien konfigurieren konnten, wird dem Benutzer auf der Unternehmensportalwebsite eine Benachrichtigung zu dem Gerät angezeigt. Darüber erfährt der Benutzer, wie er das nächste Mal, wenn er unter iOS oder Android auf die Unternehmensportal-App zugreift, eine Kategorie auswählt.

## <a name="further-information"></a>Weitere Informationen
- Sie können zwar die Gerätekategorien im Azure-Portal bearbeiten, müssen dann aber alle Azure Active Directory-Sicherheitsgruppen, die auf diese Kategorie verweisen, manuell aktualisieren.

- Wenn Sie eine Kategorie löschen, tragen die ihr zugewiesenen Geräte den Kategorienamen **Nicht zugewiesen**.
