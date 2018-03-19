---
title: "Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android-Geräte"
titlesuffix: Microsoft Intune
description: "Verwenden Sie App-Konfigurationsrichtlinien in Microsoft Intune, um Einstellungen anzugeben, wenn Benutzer eine Android for Work-App ausführen."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a448c33e8324492c68d509a12d5901f41ed4873a
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android-Geräte

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Verwenden Sie App-Konfigurationsrichtlinien in Microsoft Intune, um Einstellungen anzugeben, wenn Benutzer eine Android for Work-App ausführen. Sie weisen diese Richtlinien nicht direkt Benutzern und Geräten zu. Stattdessen verknüpfen Sie eine Richtlinie mit einer App und weisen dann die App zu. Die Richtlinieneinstellungen werden verwendet, wenn die App danach sucht (in der Regel beim ersten Ausführen).

> [!Note]  
> Nicht jede App unterstützt App-Konfigurationen. Fragen Sie den App-Entwickler, um herauszufinden, ob er die App so erstellt hat, dass App-Konfigurationsrichtlinien unterstützt werden.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie die Workload **Mobile Apps** aus.
4. Wählen Sie in der Gruppe **Verwalten** **App-Konfigurationsrichtlinien** und dann **Hinzufügen** aus.
5. Legen Sie die folgenden Details fest:
    - **Name**  
      Der Name des Profils, das im Azure-Portal angezeigt wird
    - **Beschreibung**  
      Die Beschreibung des Profils, das im Azure-Portal angezeigt wird
    - **Geräteregistrierungstyp**  
      Klicken Sie auf **Verwaltete Geräte**.
6. Wählen Sie **Android for Work** als **Plattform** aus.
7. Wählen Sie **Zugeordnete App** aus, um die App auszuwählen, für die Sie eine App-Konfigurationsrichtlinie definieren möchten. Wählen Sie aus der Liste von Android for Work-Apps aus, die Sie genehmigt und mit Intune synchronisiert haben.
8. Wählen Sie **Konfigurationseinstellungen** aus. Sie können Konfigurationen auf diese Weise festlegen:
    - im [Konfigurations-Designer](#Use-the-configuration-designer)
    - im [JSON-Editor](#Enter-the-JSON-editor)
9. Wählen Sie **OK** und dann **Hinzufügen** aus.

## <a name="use-the-configuration-designer"></a>Verwenden des Konfigurations-Designers

Sie können den Konfigurations-Designer für Apps auf Geräten verwenden, die in Intune registriert sind oder nicht. Der Designer ermöglicht Ihnen das Konfigurieren bestimmter Konfigurationsschlüssel und -werte. Sie müssen ebenfalls den Datentyp für jeden Wert angeben.

Legen Sie für jeden Schlüssel und jeden Wert in der Konfiguration Folgendes fest:

  - **Konfigurationsschlüssel**  
     Der Schlüssel, der die bestimmte Einstellungskonfiguration eindeutig identifiziert.
  - **Werttyp**  
    Der Datentyp des Konfigurationswerts. Zu den Typen gehören Integer, Real, String oder Boolean.
  - **Konfigurationswert**  
    Der Wert für die Konfiguration. 

## <a name="enter-the-json-editor"></a>Eingabe mit dem JSON-Editor

Einige Konfigurationseinstellungen für Apps (z.B. die mit Bündeltypen) können nicht mit dem Konfigurations-Designer konfiguriert werden. Sie müssen den JSON-Editor für diese Werte verwenden. Einstellungen werden Apps automatisch bereitgestellt, wenn die App installiert wird.

1. Wählen Sie für **Format der Konfigurationseinstellungen** die Option **JSON-Editor aufrufen** aus.
2. Im Editor können Sie JSON-Werte für Konfigurationseinstellungen definieren. Sie können **JSON-Vorlage herunterladen** auswählen, um eine Beispieldatei herunterzuladen, die Sie dann konfigurieren können.
3. Wählen Sie **OK** und dann **Hinzufügen** aus.

Die Richtlinie wird erstellt und auf dem Blatt mit der Richtlinienliste angezeigt.

Wenn die zugewiesene App auf einem Gerät gestartet wird, wird sie mit den Einstellungen ausgeführt, die Sie in der App-Konfigurationsrichtlinie konfiguriert haben.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Vorkonfigurieren des Erteilungsstatus von Berechtigungen für Apps

Sie können auch die Berechtigung vorkonfigurieren, dass Apps auf Android-Gerätefeatures zugreifen können. Standardmäßig fordern Android-Apps, die Geräteberechtigungen erfordern – z.B. Zugriff auf den Standort oder die Gerätekamera –, die Benutzer zum Annehmen oder Ablehnen der Berechtigungen auf. Wenn eine App z.B. das Gerätemikrofon verwendet, wird der Benutzer aufgefordert, der App die Berechtigung zur Verwendung des Mikrofons zu erteilen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie **Mobile Apps** aus.
3. Wählen Sie unter **Verwalten** die Option **App-Konfigurationsrichtlinien** und dann **Hinzufügen** aus.
4. Legen Sie die folgenden Details fest:
    - **Name**. Der Name des Profils, das im Azure-Portal angezeigt wird
    - **Beschreibung**. Die Beschreibung des Profils, das im Azure-Portal angezeigt wird
    - **Geräteregistrierungstyp** Wählen Sie **Verwaltete Geräte** aus.
    - **Plattform** Wählen Sie **Android for Work** aus.
5. Wählen Sie **Zugeordnete App** aus, um die App auszuwählen, für die Sie eine Konfigurationsrichtlinie definieren möchten. Wählen Sie aus der Liste von Android for Work-Apps aus, die Sie genehmigt und mit Intune synchronisiert haben.
6. Wählen Sie **Berechtigungen** und dann **Hinzufügen** aus.
7. Wählen Sie aus der Liste der verfügbaren App-Berechtigungen und dann **OK** aus.
8. Wählen Sie eine Option für jede Berechtigung aus, die mit dieser Richtlinie erteilt werden soll:
    - **Aufforderung** Aufforderung des Benutzers zur Annahme oder Ablehnung
    - **Automatisch gewähren** Automatische Genehmigung ohne Benachrichtigung des Benutzers
    - **Automatisch verweigern** Automatische Ablehnung ohne Benachrichtigung des Benutzers
9. Um die App-Konfigurationsrichtlinie zuzuweisen, wählen Sie die App-Konfigurationsrichtlinie, dann **Zuweisung** und anschließend **Gruppen auswählen** aus.
10. Wählen Sie die zuzuweisenden Benutzergruppen und dann **Auswählen** aus.
11. Wählen Sie **Speichern** aus, um die Richtlinie zuzuweisen.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie damit fort, die App [zuzuweisen](apps-deploy.md) und zu [überwachen](apps-monitor.md).

