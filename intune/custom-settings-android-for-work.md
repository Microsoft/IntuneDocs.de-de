---
title: Benutzerdefinierte Intune-Profileinstellungen für Android for Work
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie benutzerdefinierte Microsoft Intune-Profileinstellungen für Android for Work-Geräte erstellen.
keywords: ''
author: vhorne
ms.author: victorh
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
ms.openlocfilehash: a3f2b85e4ebf01082f075feaac5100b43d4f1392
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
---
# <a name="create-intune-custom-profile-settings-for-android-for-work-devices"></a>Erstellen von benutzerdefinierten Intune-Profileinstellungen für Android for Work-Geräte

Weisen Sie mithilfe der benutzerdefinierten Intune-Konfigurationsrichtlinie für Android for Work die OMA-URI-Einstellungen zu, die zum Steuern von Features auf Android for Work-Geräten verwendet werden können. Dies sind die Standardeinstellungen, die viele Hersteller von mobilen Geräten verwenden, um Gerätefunktionen zu steuern.

Diese Funktion soll es Ihnen ermöglichen, Android-Einstellungen zuzuweisen, die nicht mit Intune-Richtlinien konfigurierbar sind. Intune unterstützt zurzeit eine begrenzte Anzahl von benutzerdefinierten Android-Richtlinien. Mit den Beispielen in diesem Thema finden Sie heraus, welche Richtlinien Sie konfigurieren können.

## <a name="create-a-custom-profile"></a>Erstellen eines benutzerdefinierten Profils

1. Anweisungen zu den ersten Schritten finden Sie unter [Konfigurieren von benutzerdefinierten Geräteeinstellungen](custom-settings-configure.md).
2. Wählen Sie auf dem Blatt **Benutzerdefinierte OMA-URI-Einstellungen** die Option **Hinzufügen** aus, um eine neue Einstellung hinzuzufügen.
3. Konfigurieren Sie auf dem Blatt **Zeile hinzufügen** Folgendes:
    - **Name**: Geben Sie einen eindeutigen Namen für die benutzerdefinierten Android for Work-Einstellungen ein, damit Sie diese im Azure-Portal leichter identifizieren können.
    - **Beschreibung**: Geben Sie eine Beschreibung mit einem Überblick über die benutzerdefinierte Android-Richtlinie sowie weitere relevante Informationen ein, die Ihnen die Suche nach der Richtlinie erleichtern.
    - **OMA-URI**: Geben Sie den OMA-URI ein, für den Sie eine Einstellung bereitstellen möchten.
    - **Datentyp:** Wählen Sie den Datentyp aus, in dem Sie diese OMA-URI-Einstellung angeben. Wählen Sie aus folgenden Typen aus: **Zeichenfolge**, **Zeichenfolge (XML-Datei)**, **Datum und Uhrzeit**, **Ganze Zahl**, **Gleitkomma**, **Boolesch** oder **Base64 (Datei)** aus.
    - **Wert**: Geben Sie den Wert an, der mit der zuvor angegebenen OMA-URI verknüpft werden soll. Mit welcher Methode Sie diesen Wert angeben, richtet sich nach dem ausgewählten Datentyp. Beim Datentyp **Datum und Uhrzeit** beispielsweise wählen Sie den Wert aus einer Datumsauswahl aus.
4. Wenn Sie fertig sind, klicken Sie auf „OK“, um zu **Benutzerdefinierte OMA-URI-Einstellungen** zurückzukehren. Fügen Sie dann weitere Einstellungen hinzu, oder wählen Sie **Erstellen** aus, um das benutzerdefinierte Profil zu erstellen.


## <a name="example"></a>Beispiel

In diesem Beispiel erstellen Sie ein benutzerdefiniertes Profil, mit dem Sie festlegen können, ob Kopier- und Einfügeaktionen zwischen Arbeits- und persönlichen Apps auf verwalteten Android for Work-Geräten zulässig sind oder nicht.

1. Verwenden Sie das Verfahren in diesem Thema, um ein benutzerdefiniertes Profil für Android for Work-Geräte mit den folgenden Werten zu erstellen:
    - **Name**: Geben Sie „Kopieren und Einfügen blockieren“ oder einen anderen Text Ihrer Wahl ein.
    - **Beschreibung**: Geben Sie „Blockiert Kopier- und Einfügevorgänge zwischen Arbeits- und persönlichen Apps“ oder einen anderen Text Ihrer Wahl ein.
    - **OMA-URI**: Geben Sie **./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste** ein.
    - **Datentyp**: Wählen Sie **Boolesch** aus, um anzugeben, dass der Wert für diesen OMA-URI entweder **True** oder **False** ist.
    - **Wert**: Wählen Sie **True**aus.
2. Die Einstellung sollte in etwa wie der folgende Screenshot aussehen.
![Blockieren von Kopier- und Einfügevorgängen für Android for Work](./media/custom-policy-afw-copy-paste.png)
3. Wenn Sie dieses benutzerdefinierte Profil einem von Ihnen verwalteten Android for Work-Gerät zuweisen, werden Kopier- und Einfügeaktionen zwischen Apps im Arbeitsprofil und im persönlichen Profil blockiert.