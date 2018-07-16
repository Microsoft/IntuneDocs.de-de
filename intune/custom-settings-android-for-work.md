---
title: Benutzerdefinierte Intune-Profileinstellungen für Android-Arbeitsprofile
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie benutzerdefinierte Microsoft Intune-Profileinstellungen für Android-Arbeitsprofilgeräte erstellen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/12/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 109c50acf194598017aa507a0979ad3b9298de9e
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905290"
---
# <a name="create-intune-custom-profile-settings-for-android-work-profile-devices"></a>Erstellen von benutzerdefinierten Intune-Profileinstellungen für Android-Arbeitsprofilgeräte

Verwenden Sie die benutzerdefinierte Intune-Konfigurationsrichtlinie für Android-Arbeitsprofile, um OMA-URI-Einstellungen zuzuweisen, die zum Steuern von Features auf Android-Arbeitsprofilgeräten verwendet werden können. Dies sind die Standardeinstellungen, die viele Hersteller von mobilen Geräten verwenden, um Gerätefunktionen zu steuern.

Diese Funktion soll es Ihnen ermöglichen, Android-Einstellungen zuzuweisen, die nicht mit Intune-Richtlinien konfigurierbar sind. Intune unterstützt zurzeit eine begrenzte Anzahl von benutzerdefinierten Android-Richtlinien. Anhand der Beispiele in diesem Artikel finden Sie heraus, welche Richtlinien Sie konfigurieren können.

## <a name="create-a-custom-profile"></a>Erstellen eines benutzerdefinierten Profils

1. Anweisungen zu den ersten Schritten finden Sie unter [Konfigurieren von benutzerdefinierten Geräteeinstellungen](custom-settings-configure.md). Wählen Sie **Android Enterprise** für die **Plattform** und **Benutzerdefiniert** für den **Profiltyp** aus.
2. Wählen Sie auf dem Blatt **Benutzerdefinierte OMA-URI-Einstellungen** die Option **Hinzufügen** aus, um eine neue Einstellung hinzuzufügen.
3. Konfigurieren Sie auf dem Blatt **Zeile hinzufügen** Folgendes:
    - **Name:** Geben Sie einen eindeutigen Namen für die benutzerdefinierten Einstellungen für das Android-Arbeitsprofil ein, damit Sie diese im Azure-Portal leichter identifizieren können.
    - **Beschreibung**: Geben Sie eine Beschreibung mit einem Überblick über die benutzerdefinierte Android-Richtlinie sowie weitere relevante Informationen ein, die Ihnen die Suche nach der Richtlinie erleichtern.
    - **OMA-URI**: Geben Sie den OMA-URI ein, für den Sie eine Einstellung bereitstellen möchten.
    - **Datentyp:** Wählen Sie den Datentyp aus, in dem Sie diese OMA-URI-Einstellung angeben. Wählen Sie aus folgenden Typen aus: **Zeichenfolge**, **Zeichenfolge (XML-Datei)**, **Datum und Uhrzeit**, **Ganze Zahl**, **Gleitkomma**, **Boolesch** oder **Base64 (Datei)** aus.
    - **Wert**: Geben Sie den Wert an, der mit der zuvor angegebenen OMA-URI verknüpft werden soll. Mit welcher Methode Sie diesen Wert angeben, richtet sich nach dem ausgewählten Datentyp. Beim Datentyp **Datum und Uhrzeit** beispielsweise wählen Sie den Wert aus einer Datumsauswahl aus.
4. Wenn Sie fertig sind, klicken Sie auf „OK“, um zu **Benutzerdefinierte OMA-URI-Einstellungen** zurückzukehren. Fügen Sie dann weitere Einstellungen hinzu, oder wählen Sie **Erstellen** aus, um das benutzerdefinierte Profil zu erstellen.


## <a name="example"></a>Beispiel

In diesem Beispiel erstellen Sie ein benutzerdefiniertes Profil, mit dem Sie festlegen können, ob Kopier- und Einfügeaktionen zwischen Arbeits- und persönlichen Apps auf Android-Arbeitsprofilgeräten zugelassen sind.

1. Verwenden Sie das in diesem Artikel dargestellte Verfahren, um ein benutzerdefiniertes Profil für Android-Arbeitsprofilgeräte mit den folgenden Werten zu erstellen:
    - **Name**: Geben Sie „Kopieren und Einfügen blockieren“ oder einen anderen Text Ihrer Wahl ein.
    - **Beschreibung**: Geben Sie „Blockiert Kopier- und Einfügevorgänge zwischen Arbeits- und persönlichen Apps“ oder einen anderen Text Ihrer Wahl ein.
    - **OMA-URI**: Geben Sie **./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste** ein.
    - **Datentyp**: Wählen Sie **Boolesch** aus, um anzugeben, dass der Wert für diesen OMA-URI entweder **True** oder **False** ist.
    - **Wert**: Wählen Sie **True**aus.
2. Die Einstellung sollte in etwa wie der folgende Screenshot aussehen.
![Kopieren und Einfügen für das Android-Arbeitsprofil blockiert](./media/custom-policy-afw-copy-paste.png)
3. Wenn Sie dieses benutzerdefinierte Profil einem von Ihnen verwalteten Android-Arbeitsprofilgerät zuweisen, werden Kopier- und Einfügeaktionen zwischen Apps im Arbeitsprofil und im persönlichen Profil blockiert.