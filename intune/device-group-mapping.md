---
title: "Kategorisieren von Geräten in Gruppen in Intune"
titleSuffix: Microsoft Intune
description: "Erfahren Sie, wie Sie Geräte zur einfacheren Verwaltung in Gruppen kategorisieren."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 416ce4fb671494efabf805595426f25d027d256e
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="categorize-devices-into-groups-for-easier-management"></a>Kategorisieren von Geräten in Gruppen zur einfacheren Verwaltung

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Verwenden Sie die Gerätekategorien in Microsoft Intune, damit Geräte basierend auf Kategorien, die Sie definieren, automatisch Gruppen hinzugefügt werden, sodass Sie diese Geräte einfacher verwalten können.

Gerätekategorien verwenden den folgenden Workflow:
1. Erstellen Sie Kategorien, die Benutzer beim Registrieren ihrer Geräte verwenden können.
2. Wenn Endbenutzer von iOS- und Android-Geräten ihre Geräte registrieren, müssen sie aus der Liste der von Ihnen konfigurierten Kategorien eine Kategorie auswählen. Um einem Windows-Gerät eine Kategorie zuzuweisen, müssen Endbenutzer die Unternehmensportalwebsite verwenden (weitere Informationen dazu finden Sie in diesem Artikel unter **Nach dem Konfigurieren von Gerätegruppen**).
3. Dann können Sie Richtlinien und Apps für diese Gruppen bereitstellen.

Sie können beliebige Gerätekategorien erstellen, z.B.:
- POS-Gerät (Point of Sale)
- Demogerät
- Sales
- Kontoführung
- Manager

## <a name="how-to-configure-device-categories"></a>Konfigurieren von Gerätekategorien

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>Schritt 1: Erstellen von Gerätekategorien auf dem Blatt „Intune“ im Azure-Portal
1. Wählen Sie in [Azure-Portal](https://portal.azure.com) **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie auf dem Blatt **Intune** die Option **Geräteregistrierung** aus.
3. Wählen Sie im Blatt **Geräteregistrierung** die Option **Gerätekategorien** aus.
4. Wählen Sie auf der Seite **Gerätekategorien** die Option **Erstellen** aus, um eine neue Kategorie hinzuzufügen.
5. Geben Sie auf dem Blatt **Gerätekategorie erstellen** einen **Namen** für die neue Kategorie und optional eine **Beschreibung** ein.
6. Klicken Sie auf **Erstellen**, wenn Sie fertig sind. Sie können die neue Kategorie in der Liste der Kategorien sehen.

Verwenden Sie den Kategorienamen des Geräts zum Erstellen von Azure Active Directory-Sicherheitsgruppen in Schritt 2.

### <a name="step-2---create-azure-active-directory-security-groups"></a>Schritt 2: Erstellen von Active Directory-Sicherheitsgruppen
In diesem Schritt erstellen Sie dynamische Gruppen im Azure-Portal auf Basis der Gerätekategorie und des Gerätekategorienamens.

Um fortzufahren, lesen Sie den Artikel [Erstellen attributbasierter Regeln für dynamische Gruppenmitgliedschaft in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) in der Dokumentation zu Azure Active Directory.

Verwenden Sie die Informationen in diesem Abschnitt zum Erstellen einer Gerätegruppe mit einer erweiterten Regel mithilfe des Attributs **deviceCategory**. Beispiel: (**device.deviceCategory -eq** "*<the device category name you got from the Azure portal>*")

Wenn nach dem Konfigurieren von Gerätegruppen Benutzer ihre Geräte registrieren, wird ihnen eine Liste der von Ihnen konfigurierten Kategorien angezeigt. Nachdem sie eine Kategorie ausgewählt und die Registrierung abgeschlossen haben, wird ihr Gerät der Active Directory-Sicherheitsgruppe hinzugefügt, die der gewählten Kategorie entspricht.

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>Anzeigen der Kategorien von Geräten, die Sie verwalten

1.  Wählen Sie in [Azure-Portal](https://portal.azure.com) **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.

2. Wählen Sie im Azure-Portal auf dem Blatt „Intune“ die Option **Geräte** aus.

3.  Klicken Sie unter **Verwalten** auf **Alle Geräte**.

4.  Sehen Sie sich in der Liste der Geräte die Spalte **Gerätekategorie** an.

Wenn die Spalte **Gerätekategorie** nicht angezeigt wird, klicken Sie auf **Spalten**, wählen Sie in der Liste **Gerätekategorie** aus, und klicken Sie dann auf **Anwenden**.

### <a name="to-change-the-category-of-a-device"></a>So ändern Sie die Kategorie eines Geräts

1. Wählen Sie in [Azure-Portal](https://portal.azure.com) **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie auf dem Blatt **Intune** die Option **Geräte** aus.
4. Wählen Sie im Blatt **Geräte** im Abschnitt **Verwalten** **Alle Geräte** aus.
5. Wählen Sie in der Liste der Geräte das gewünschte Gerät und anschließend auf dem Blatt mit den Geräteeigenschaften unter **Verwalten** **Eigenschaften** aus.
6. Auf dem nächsten Blatt können Sie die **Gerätekategorie** des ausgewählten Geräts in einen beliebigen Kategorienamen ändern, den Sie zuvor konfiguriert haben.

## <a name="after-you-configure-device-groups"></a>Nach dem Konfigurieren von Gerätegruppen

Wenn Endbenutzer von iOS- und Android-Geräten ihre Geräte registrieren, müssen sie aus der Liste der von Ihnen konfigurierten Kategorien eine Kategorie auswählen. Nachdem sie eine Kategorie ausgewählt und die Registrierung abgeschlossen haben, wird ihr Gerät zu der Intune-Gerätegruppe oder Active Directory-Sicherheitsgruppe hinzugefügt, die der gewählten Kategorie entspricht.

Endbenutzer unter Windows sollten die Unternehmensportalwebsite verwenden, um eine Kategorie auszuwählen.

Unabhängig von der Plattform können Ihre Endbenutzer nach der Registrierung des Geräts jederzeit auf „portal.manage.microsoft.com“ zugreifen. Weisen Sie den Benutzer dazu an, auf die Unternehmensportalwebsite zuzugreifen und zu **Meine Geräte** zu navigieren. Er hat dann die Möglichkeit, ein auf der Seite aufgeführtes registriertes Gerät sowie eine Kategorie auszuwählen.

Nach Auswahl der Kategorie wird das Gerät automatisch zur entsprechenden Gruppe hinzugefügt, die Sie erstellt haben. Wenn ein Gerät bereits registriert wurde, bevor Sie Kategorien konfiguriert haben, wird dem Benutzer auf der Unternehmensportal-Website eine Benachrichtigung zu dem Gerät angezeigt, und der Benutzer wird aufgefordert, beim nächsten Zugriff auf die Unternehmensportal-App über ein iOS- oder Android-Gerät eine Kategorie auszuwählen.

## <a name="further-information"></a>Weitere Informationen
- Sie können eine Gerätekategorie im Azure-Portal bearbeiten, müssen dann aber alle Azure Active Directory-Sicherheitsgruppen, die auf diese Kategorie verweisen, manuell aktualisieren.

- Wenn Sie eine Kategorie löschen, tragen die ihr zugewiesenen Geräte den Kategorienamen **Nicht zugewiesen**.
