---
title: Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android-Geräte
titlesuffix: Microsoft Intune
description: Verwenden Sie App-Konfigurationsrichtlinien in Microsoft Intune, um Einstellungen anzugeben, wenn Benutzer eine Android-Arbeitsprofil-App ausführen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c837f9a5a2cb1a6f267f85f888453725da6acb66
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905749"
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android-Geräte

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Verwenden Sie App-Konfigurationsrichtlinien in Microsoft Intune, um Einstellungen für Android-Arbeitsprofil-Apps anzugeben. Der App-Entwickler muss Konfigurationseinstellungen für mit Android verwaltete Apps zur Verfügung stellen, damit Konfigurationseinstellungen für die App angegeben werden können. Weisen Sie die Konfigurationsrichtlinien für die App der Benutzergruppe zu, für die die Einstellungen gelten sollen.  Die Richtlinieneinstellungen werden verwendet, wenn die App danach sucht (in der Regel beim ersten Ausführen).

> [!Note]  
> Nicht jede App unterstützt App-Konfigurationen. Fragen Sie den App-Entwickler, um herauszufinden, ob er die App so erstellt hat, dass App-Konfigurationsrichtlinien unterstützt werden.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie die Workload **Mobile Apps** aus.
4. Wählen Sie in der Gruppe **Verwalten** **App-Konfigurationsrichtlinien** und dann **Hinzufügen** aus.
5. Legen Sie die folgenden Details fest:
    - **Name:** Der Name des Profils, das im Azure-Portal angezeigt wird
    - **Beschreibung:** Die Beschreibung des Profils, das im Azure-Portal angezeigt wird
    - **Geräteregistrierungstyp:** Wählen Sie die **verwalteten Geräte** aus.
6. Wählen Sie **Android** als **Plattform** aus.
7. Klicken Sie auf **Zugeordnete App**, um die App auszuwählen, für die Sie eine App-Konfigurationsrichtlinie definieren möchten. Wählen Sie diese aus der Liste der Android-Arbeitsprofil-Apps aus, die Sie genehmigt und mit Intune synchronisiert haben.
8. Klicken Sie auf **Berechtigungen**. Sie können Konfigurationen auf diese Weise festlegen:
    - im [Konfigurations-Designer](#Use-the-configuration-designer)
    - im [JSON-Editor](#Enter-the-JSON-editor)
9. Wählen Sie **OK** und dann **Hinzufügen** aus.

## <a name="use-the-configuration-designer"></a>Verwenden des Konfigurations-Designers

Sie können den Konfigurations-Designer für Android-Apps verwenden, die die Konfiguration unterstützen. Die Konfiguration wird nur auf Geräten angewendet, die in Intune registriert sind. Der Designer ermöglicht Ihnen die Konfiguration bestimmter Konfigurationswerte für die Einstellungen, die eine App zur Verfügung stellt.

Klicken Sie auf **Hinzufügen**, um die Liste der Konfigurationseinstellungen auszuwählen, die Sie für die App angeben möchten.  
Legen Sie für jeden Schlüssel und jeden Wert in der Konfiguration Folgendes fest:

  - **Werttyp**  
    Der Datentyp des Konfigurationswerts. Für Werttypen von Zeichenfolgen können Sie auch ein Variablen- oder Zertifikatprofil als Werttyp auswählen.
  - **Konfigurationswert**  
    Der Wert für die Konfiguration. Sie können aus einer Liste von Variablen- oder Zertifikatprofilen in der Dropdownliste der Konfigurationswerte eine Variable oder ein Zertifikat für den Werttyp auswählen.  Wenn Sie ein Zertifikat auswählen, wird der Zertifikatalias des auf dem Gerät bereitgestellten Zertifikats zur Laufzeit aufgefüllt.
    
### <a name="supported-variables-for-configuration-values"></a>Unterstützte Variablen für Konfigurationswerte

Wenn Sie eine Variable als Werttypen auswählen möchten, haben Sie folgende Optionen:
- Benutzerprinzipalnamen: z.B. **John@contoso.com**
- Mail: z.B. **John@contoso.com**
- Teil-UPN: z.B. **John**
- Konto-ID: z.B. **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- Geräte-ID: z.B. **b9841cd9-9843-405f-be28-b2265c59ef97**
- Benutzer-ID: z.B. **3ec2c00f-b125-4519-acf0-302ac3761822**
- Benutzername: z.B. **John Doe**


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
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie **Mobile Apps** aus.
3. Wählen Sie unter **Verwalten** die Option **App-Konfigurationsrichtlinien** und dann **Hinzufügen** aus.
4. Legen Sie die folgenden Details fest:
    - **Name**. Der Name des Profils, das im Azure-Portal angezeigt wird
    - **Beschreibung**. Die Beschreibung des Profils, das im Azure-Portal angezeigt wird
    - **Geräteregistrierungstyp** Wählen Sie **Verwaltete Geräte** aus.
    - **Plattform** Wählen Sie **Android** aus.
5. Wählen Sie **Zugeordnete App** aus, um die App auszuwählen, für die Sie eine Konfigurationsrichtlinie definieren möchten. Wählen Sie diese aus der Liste der Android-Arbeitsprofil-Apps aus, die Sie genehmigt und mit Intune synchronisiert haben.
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

