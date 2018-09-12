---
title: Hinzufügen branchenspezifischer Windows-Apps zu Microsoft Intune
titlesuffix: ''
description: Erfahren Sie, wie Sie branchenspezifische Windows-Apps zu Microsoft Intune hinzufügen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5c64b915f240cab2faac84a6a78b213a5fffa0a6
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347897"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Hinzufügen branchenspezifischer Windows-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Branchenspezifische Apps werden über eine App-Installationsdatei hinzugefügt. Diese Art von App wird in der Regel intern geschrieben. Die folgenden Schritte enthaltenen Informationen zum Hinzufügen einer LOB-Windows-App mit Microsoft Intune.

## <a name="step-1-specify-the-software-setup-file"></a>Schritt 1: Angeben der Softwaresetupdatei

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** die Option **Client-Apps** aus.
4. Wählen Sie in der Workload **Client-Apps** die Option **Verwalten** > **Apps** aus.
5. Wählen Sie oberhalb der App-Liste **Hinzufügen** aus.
6. Wählen Sie im Bereich **App hinzufügen** die Option **Branchenspezifische App** aus.

## <a name="step-2-configure-the-app-package-file"></a>Schritt 2: Konfigurieren der App-Paketdatei

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Paketdatei** aus.
2. Wählen Sie im Bereich **App-Paketdatei** die Schaltfläche zum Durchsuchen. Wählen Sie dann eine Windows-Installationsdatei mit der Erweiterung **MSI**. **APPX** oder **APPXBUNDLE**.
3. Wählen Sie danach **OK**.


## <a name="step-3-configure-app-information"></a>Schritt 3: Konfigurieren von App-Informationen

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Informationen**.
2. Konfigurieren Sie im Bereich **App-Informationen** die folgenden Informationen. Einige der Werte in diesem Bereich wurden möglicherweise automatisch ausgefüllt.
    - **Name:** Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Die Beschreibung wird im Unternehmensportal angezeigt.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    - **App-Version ignorieren**: Legen Sie **Ja** fest, wenn der Entwickler die App automatisch aktualisiert.
    - **Kategorie:** Wählen Sie eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Kategorien erleichtern es dem Benutzer, die App über das Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Zeigen Sie die App auf der Hauptseite des Unternehmensportals hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL:** Geben Sie optional die URL zu einer Website ein, die Informationen über die App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen:** Geben Sie optional die URL zu einer Website ein, die Datenschutzinformationen für die App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **Befehlszeilenargumente:** Geben Sie optional Befehlszeilenargumente ein, die für die .msi-Datei gelten sollen, wenn sie ausgeführt wird. Ein Beispiel ist **/q**.
    - **Entwickler:** Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer:** Geben Sie optional einen Namen für den Besitzer dieser App ein. Ein Beispiel ist **Personalabteilung**.
    - **Anmerkungen:** Geben Sie Hinweise zu dieser App ein.
    - **Logo**: Laden Sie ein Symbol für die App hoch. Das Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
3. Wählen Sie danach **OK**.

## <a name="step-4-finish-up"></a>Schritt 4: Fertig stellen

1. Überprüfen Sie im Bereich **App hinzufügen**, ob die konfigurierten App-Informationen richtig sind.
2. Wählen Sie **Hinzufügen**, um die App in Intune hochzuladen.

## <a name="step-5-update-a-line-of-business-app"></a>Schritt 5: Aktualisieren einer branchenspezifischen App

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Konfigurieren Sie eine mobile MSI-App, die sich selbst aktualisiert, um den Prozess der Versionsüberprüfung zu ignorieren.

Sie können eine bekannte mobile MSI-App konfigurieren, die sich selbst aktualisiert, um den Prozess der Versionsüberprüfung zu ignorieren. 

Einige auf den MSI-Installer basierende Apps werden vom App-Entwickler automatisch aktualisiert. Für diese automatisch aktualisierten MSI-Apps können Sie die Einstellung **App-Version ignorieren** im Bereich **App-Informationen** konfigurieren. Wenn diese Einstellung auf **Ja** festgelegt wird, erzwingt Microsoft Intune keine App-Version, die auf dem Windows-Client installiert ist. 

Diese Einstellung ist nützlich, um Racebedingungen zu vermeiden. Beispielsweise kann eine Racebedingung auftreten, wenn die App automatisch vom App-Entwickler und von Intune aktualisiert wird. Beide könnten dann eine Version der App auf dem Windows-Client erzwingen, was einen Konflikt auslösen kann.

## <a name="next-steps"></a>Nächste Schritte

- Die von Ihnen erstellte App wird in der Liste der Apps angezeigt. Sie können sie jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

- Erfahren Sie mehr darüber, wie Sie die Eigenschaften und Zuweisungen Ihrer App überwachen können. Siehe [Überwachen von App-Informationen und -Zuweisungen](apps-monitor.md).

- Erfahren Sie mehr über den Kontext Ihrer App in Intune. Siehe [Übersicht über die Lebenszyklen von Geräten und Apps](introduction-device-app-lifecycles.md).
