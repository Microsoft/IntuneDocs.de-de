---
title: Binden von Android-Geräten nach Netzwerkstandort in Microsoft Intune (Azure) | Microsoft-Dokumentation
description: Erstellen oder konfigurieren Sie Netzwerkstandorte für Android-Geräte in Microsoft Intune. Sie können Geräte aufgrund des Netzwerkstandorts als „Nicht konform“ markieren. Wenn das Gerät den Netzwerkstandort verlässt, können Sie den Zugriff auf die Unternehmensressourcen blockieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ayesham
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 648ccd889714c2ee4f7ee1fa04301490ad9fd001
ms.sourcegitcommit: c2e62f1ebdf75599c8e544287123c602f0f15f2b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72749442"
---
# <a name="use-locations-network-fence-in-intune"></a>Verwenden von Standorten (Netzwerk-Fencing) in Intune

Falls Sie den Zugriff auf ein Unternehmensnetzwerk blockieren möchten, wenn ein Gerät einen Standort verlässt, können Sie die Funktionalität verwenden, die vom Feature **Standorte** in Intune bereitgestellt wird. 

Sie können eine auf Netzwerkstandorten basierende Konformitätsrichtlinie erstellen. Dies wird auch als „Netzwerk-Fencing“ bezeichnet. Durch die Richtlinie wird sichergestellt, dass Geräte mit Firmennetzwerk verbunden sein müssen, um als konform zu gelten. Diese Richtlinie kann mit Richtlinien für bedingten Zugriff verwendet werden, sodass Geräte *nur* dann Zugriff auf geschäftliche Ressourcen haben, wenn das Gerät mit dem Firmennetzwerk verbunden ist. Wenn das Gerät nicht mit dem Firmennetzwerk verbunden ist, gilt es als nicht konform und verliert den Zugriff auf geschäftliche Ressourcen.

Als Beispiel dient das folgende Szenario:

In Ihrer Produktionsanlage verwenden einige Mitarbeiter Android-Geräte. Ein Mitarbeiter verlässt mit dem Android-Gerät das Werk oder die Anlage. Sie können Folgendes durchführen, um nicht autorisierten Zugriff zu verhindern:

1. Erstellen Sie einen Standort mit einem IPv4-Adressbereich namens **Produktionsbereich**.
2. Erstellen Sie eine Konformitätsrichtlinie, die erfordert, dass diese Geräte mit dem Firmennetzwerk verbunden sein müssen, und wenden Sie diese an.
3. Wenn das Gerät die Produktionsanlage verlässt, wird es als „Nicht konform“ betrachtet und hat keinen Zugriff auf geschäftliche Ressourcen.

Darüber hinaus können Sie [Aktionen bei Nichtkonformität](#configure-the-actions-for-noncompliance) hinzufügen. Wenn sich das Gerät wieder am lokalen Standort und im Netzwerkstandort befindet, erhält es erneut Zugriff auf Unternehmensressourcen.

## <a name="prerequisites"></a>Voraussetzungen

So erstellen Sie eine standortbasierte Konformitätsrichtlinie:

- Erstellen Sie einen Netzwerkstandort als IPv4-Netzwerkbereiche für den Gatewayserver, den DHCP-Server und/oder den DNS-Server, mit denen die Geräte Verbindungen herstellen.
- Erstellen Sie eine Konformitätsrichtlinie, die diese Standorte verwendet, und definieren Sie die durchzuführenden Aktionen, wenn das Gerät nicht mehr mit dem Netzwerkstandort verbunden ist.
- Android-Geräte (6.0 und höher) mit der aktualisierten Unternehmensportal-App

## <a name="create-a-location"></a>Erstellen eines Standorts

1. Klicken Sie in Intune auf **Gerätekonformität** > **Standorte** > **Erstellen**.

2. Geben Sie die folgenden Eigenschaften ein:  

   - Erforderlich. Geben Sie einen **Namen** für den Standort ein, z.B. **Produktionsbereich** oder **Gebäude 44–sicher**.
   - (Optional) Geben Sie einen **IPv4-Bereich** mit CIDR-Notation (Classless Interdomain Routing) ein, z.B. `aaa.bbb.ccc.ddd/n`.
   - (Optional) Geben Sie die Adresse des **IPv4-Gateways** ein, z.B. `aaa.bbb.ccc.ddd`.
   - (Optional) Geben Sie die Adresse des **IPv4-DHCP-Servers** ein, z.B. `aaa.bbb.ccc.ddd`.
   - (Optional) Geben Sie die Liste der Adressen der **IPv4-DNS-Server** ein. Diese Einstellung verwendet die **Übereinstimmung von Teilmengen**. Wenn es sich bei den IPv4-DNS-Servern auf dem Gerät um Teilmengen der definierten Werte handelt, gilt das Gerät als innerhalb der Grenze. Achten Sie darauf, eine Adresse pro Zeile einzugeben, z.B.:  
     `aaa.bbb.ccc.ddd`  
     `aaa.bbb.ccc.ddd`
   - (Optional) Geben Sie eine Liste von **DNS-Suffixen** ein. Diese Einstellung verwendet die **Übereinstimmung von Teilmengen**. Wenn es sich bei den DNS-Suffixen auf dem Gerät um Teilmengen der definierten Werte handelt, gilt das Gerät als innerhalb der Grenze. Achten Sie darauf, einen Domänennamen in jeder Zeile einzugeben, z.B.:  
     `contoso.com`  
     `contoso.org`

3. **Speichern** Sie die Änderungen.

## <a name="create-the-location-compliance-policy"></a>Erstellen der Konformitätsrichtlinie für den Standort

Wenn Sie [die Konformitätsrichtlinie erstellen](create-compliance-policy.md), wählen Sie **Android** für die **Plattform** aus. Unter **Standorte** können Sie einen oder mehr der hinzugefügten Netzwerkstandorte auswählen. Diese Standorte sind Teil des Netzwerk-Fencing-Bereichs, den Sie für Ihr Gerät erstellen. 


## <a name="configure-the-actions-for-noncompliance"></a>Konfigurieren der Aktionen bei Nichtkonformität

Nachdem die Konformitätsrichtlinie erstellt wurde, gilt die Standardaktion bei Nichtkonformität für das Gerät. Sie können weitere Aktionen hinzufügen. Fügen Sie beispielsweise eine Aktion hinzu, die eine E-Mail an den Benutzer sendet, wenn das Gerät nicht mehr mit dem Standort konform ist.

Unter [Hinzufügen von Aktionen bei Nichtkonformität](actions-for-noncompliance.md) finden Sie hilfreiche Informationen.

## <a name="company-portal-app"></a>Unternehmensportal-App

Wenn das Gerät mit Ihren Standorten verbunden ist, wird es in der Unternehmensportal-App als „Konform“ angezeigt. Wenn das Gerät nicht mit einem Ihrer Standorte verbunden ist, wird es als „Nicht konform“ angezeigt.

## <a name="next-steps"></a>Nächste Schritte
[Überwachen von Intune-Richtlinien zur Gerätekonformität](compliance-policy-monitor.md)  
[Erste Schritte mit Konformitätsrichtlinien](device-compliance-get-started.md)
