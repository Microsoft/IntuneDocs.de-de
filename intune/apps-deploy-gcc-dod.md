---
title: Apps für GCC High- und DoD-Umgebungen
titleSuffix: Microsoft Intune
description: Informationen zu Apps in GCC High- und DoD-Umgebungen unter Verwendung von Microsoft Intune
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17d94252dd957c5699b34e0b8c2cbae2eee0b66f
ms.sourcegitcommit: 63b55e81122e5c15893302b109ae137c30855b55
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67713358"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>Bereitstellen von Apps mit Intune auf GCC High- und DoD-Umgebungen 

Microsoft Intune kann von Mandantenadministratoren verwendet werden, um Apps an die Belegschaft zu verteilen. Damit sind die Mitarbeiter des Unternehmens gemeint, also die Benutzer der Apps. Es gibt verschiedene Arten von Apps, die über Intune in GCC High- und DoD-Umgebungen bereitgestellt werden können. Wenn ein Administrator eine Windows-App hochladen und verteilen muss, die für GCC High- und DoD-Umgebungen bestimmt ist, die benutzerdefiniert sind, von Drittanbietern erstellt oder als Offline-Apps aus [Microsoft Store für Unternehmen](https://businessstore.microsoft.com/store) heruntergeladen wurden, kann der Administrator diese als [branchenspezifische App](apps-add.md#app-types-in-microsoft-intune) verteilen.  

> [!NOTE]
> Bei kommerziellen Umgebungen kann ein Mandantenadministrator Microsoft Store für Unternehmen mit Intune synchronisieren. Dies ist allerdings für GCC High- und DoD-Umgebungen nicht verfügbar. In dieser Situation müssen Administratoren Apps bereitstellen, indem sie sie direkt in Intune hochladen.  

## <a name="add-line-of-business-apps-using-intune"></a>Hinzufügen von branchenspezifischen Apps mithilfe von Intune 

Führen Sie die Anweisungen für [branchenspezifische Windows-Apps](lob-apps-windows.md) aus, um mithilfe von Intune eine branchenspezifische App für GCC High- und DoD-Umgebungen hinzuzufügen. Sie können auch zuerst das Unternehmensportal aus Microsoft Store für Unternehmen bereitstellen. Wenn Sie sich dazu entscheiden, das Portal zu verwenden, können Sie dieses manuell installieren und bereitstellen. Weitere Informationen finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](company-portal-app.md). 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>Verteilen von Offline-Apps aus Microsoft Store für Unternehmen mithilfe von Intune  

Wenn Sie eine [offline lizenzierte App](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app) aus Microsoft Store für Unternehmen herunterladen müssen, führen Sie die folgenden Schritte aus: 

1. Melden Sie sich bei [Store für Unternehmen](https://businessstore.microsoft.com/) an.
2. Klicken Sie auf **Verwalten** > **Einstellungen**.
3. Legen Sie unter **Shopping experience** (Einkaufserlebnis) die Option **Show offline apps** (Offline-Apps anzeigen) auf **On** (Aktiv) fest.

Wenn Sie Apps kaufen können Sie den Lizenztyp in „Offline“ ändern, wenn eine Offlineversion zur Verfügung steht. Wenn Sie die App dann erworben haben, können Sie diese verwalten, indem Sie in [Store für Unternehmen](https://businessstore.microsoft.com/) auf **Verwalten** > **Produkte und Dienste** klicken. Außerdem können Sie die App mitsamt ihrer Abhängigkeiten herunterladen. Anschließend können Sie diese heruntergeladene App (mitsamt ihrer Abhängigkeiten) mithilfe von Intune für Benutzer bereitstellen.  

## <a name="syncing-intune-to-the-store-for-business"></a>Synchronisieren von Intune mit Store für Unternehmen 

In kommerziellen Umgebungen (nicht in Regierungsumgebungen) können Administratoren Intune mit Microsoft Store für Unternehmen synchronisieren. Dieses Feature ist für Regierungsumgebungen nicht verfügbar. Weitere Informationen zu den Unterschieden zwischen Intune in kommerziellen Umgebungen und Regierungsumgebungen finden Sie unter [Beschreibung des Diensts Enterprise Mobility + Security für die US-Regierung](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description).  

Informationen zum Synchronisieren von Intune mit einem Store für Unternehmen-Konto finden Sie unter [Verwalten von Apps, die im Microsoft Store für Unternehmen mit Microsoft Intune erworben wurden](windows-store-for-business.md).  

## <a name="compliance"></a>Konformität 

Überprüfen Sie die Privacy- und Datenschutzgesetze sowie die Konformitätsanforderungen von Apps, und vergleichen Sie sie mit den Konformitäts-, Sicherheits- und Datenschutzanforderungen Ihrer Organisation, wenn Sie die Verwendung dieser Dienste bewerten.   

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Bereitstellen und Zuweisen von Apps finden Sie unter [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md).

 
