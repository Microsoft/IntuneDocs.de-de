---
title: Aktivieren von Google Play Protect-Konformität mit Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie eine Konformitätsrichtlinie für Android-Geräte erstellen, um Google Play Protect zu aktivieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E9810BEB-000A-4DFB-B5C7-A22A92082B22
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e99671c6c82a7652ba3489d5cc217dfedac72788
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-device-compliance-policy-to-enable-google-play-protect"></a>Informationen zum Erstellen einer Gerätekonformitätsrichtlinie zum Aktivieren von Google Play Protect

Sie können eine neue Konformitätsrichtlinie für die Android-Plattform erstellen, um die Konformität mit Google Play Protect (GPP) zu überprüfen.

Die Konformitätsrichtlinie, die diese Einstellungen erfordert, kann dann einer Gruppe von Android-Benutzern oder -Geräten zugeordnet werden. Wenn bei einem Gerät diese Einstellungen nicht aktiviert sind, ist keine Konformität gegeben.

## <a name="create-a-compliance-policy"></a>Erstellen einer Konformitätsrichtlinie

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
2. Wählen Sie **Gerätekonformität** in der Gruppe **Verwalten** aus. 
3. Klicken Sie auf **Richtlinien** > **Richtlinie erstellen**.
4. Füllen Sie die Felder **Name** und **Beschreibung** für die Richtlinie aus.
5. Wählen Sie **Android** als Plattform aus.
6. Wählen Sie **Einstellungen** > **Integrität für Geräte**.
7. Konfigurieren Sie die Einstellungen für **Google Play Protect**.
8. Wenn Sie die Einstellungen für Google Play Protect festgelegt haben, geben Sie die Einstellungen **Systemsicherheit** und **Geräteeigenschaften** an. Wählen Sie abschließend **OK** aus.

## <a name="configure-the-google-play-protect-settings"></a>Konfigurieren der Einstellungen für Google Play Protect

 - **Google Play Services ist konfiguriert**  
   Erfordert, dass die Google Play Services-App installiert und aktiviert ist. Google Play Services ermöglicht Sicherheitsupdates und stellt eine grundlegende Abhängigkeit für viele Sicherheitsfunktionen auf zertifizierten Google-Geräten dar.
 - **Aktueller Sicherheitsanbieter**  
   Dient zum Anfordern, dass ein aktueller Sicherheitsanbieter ein Gerät vor bekannten Sicherheitslücken schützen kann.
 - **Bedrohungsüberprüfung für Apps**  
   Dient zum Anfordern, dass die Android-Funktion **Apps überprüfen** aktiviert wird.
    > [!Note]  
    > Auf der älteren Android-Plattform ist diese Funktion eine Konformitätseinstellung. Intune kann nur prüfen, ob diese Einstellung auf Geräteebene aktiviert ist. Auf Geräten mit Arbeitsprofilen, früher Android for Work, ist diese Einstellung als Konfigurationsrichtlinieneinstellung zu finden. Dies ermöglicht Administratoren, die Einstellung für ein Gerät zu aktivieren.

    Wenn Ihr Unternehmen Android-Arbeitsprofile verwendet, können Sie **Bedrohungsüberprüfung für Apps** für Ihre registrierten Geräte aktivieren. Richten Sie ein Geräteprofil ein, und fordern Sie die Systemsicherheitseinstellung an. Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android for Work-Geräte in Microsoft Intune](device-restrictions-android-for-work.md).

 - **SafetyNet-Gerätenachweis**  
   Legen Sie die Integritätsstufe des SafetyNet-Gerätenachweises fest, die eingehalten werden muss. Zu den Stufen zählen **Nicht konfiguriert**, **Grundlegende Integrität prüfen** und **Grundlegende Integrität prüfen & zertifizierte Geräte**.




## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Arbeiten mit Gerätekonformitätsrichtlinien finden Sie unter [Erste Schritte mit Intune-Gerätekonformitätsrichtlinien](device-compliance-get-started.md).