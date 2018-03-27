---
title: Informationen zum Hinzufügen branchenspezifischer Windows-Apps zu Microsoft Intune
titlesuffix: ''
description: Informationen zum Hinzufügen branchenspezifischer Windows-Apps zu Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f975f2018d2ce1d7affded3c3386c479e6877388
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-add-windows-line-of-business-lob-apps-to-microsoft-intune"></a>Informationen zum Hinzufügen branchenspezifischer Windows-Apps zu Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Branchenspezifische Apps werden über eine App-Installationsdatei hinzugefügt. Solche Apps werden in der Regel intern geschrieben. Die folgenden Schritte enthaltenen Informationen zum Hinzufügen einer LOB-Windows-App mit Microsoft Intune.

## <a name="step-1---specify-the-software-setup-file"></a>Schritt 1: Angeben der Softwaresetupdatei

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Mobile Apps**.
4. Wählen Sie in der Workload **Mobile Apps** die Option **Verwalten** > **Apps** aus.
5. Wählen Sie über der Liste der Apps **Hinzufügen** aus.
6. Klicken Sie im Bereich **App hinzufügen** auf **Branchenspezifische App**.

## <a name="step-2---configure-the-app-package-file"></a>Schritt 2: Konfigurieren der App-Paketdatei

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Paketdatei** aus.
2. Klicken Sie im Bereich **App-Paketdatei** auf die Schaltfläche „Durchsuchen“, und wählen Sie eine Windows-Installationsdatei mit der Erweiterung **.msi**, **.appx** oder **.appxbundle** aus.
3. Wenn Sie fertig sind, wählen Sie **OK** aus.


## <a name="step-3---configure-app-information"></a>Schritt 3: Konfigurieren von App-Informationen

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Paketdatei** aus.
2. Konfigurieren Sie im Bereich **App-Informationen** folgende Informationen (einige der Werte in diesem Bereich wurden möglicherweise bereits automatisch ausgefüllt):
    - **Name:** Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Die Beschreibung wird Benutzern im Unternehmensportal angezeigt.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    - **App-Version ignorieren**: Legen Sie **Ja** fest, wenn die App automatisch vom Entwickler aktualisiert wird.
    - **Kategorie:** Wählen Sie eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Durch die Kategorisierung von Apps wird es für die Benutzer leichter, die Apps im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen:** Zeigen Sie die App auf der Hauptseite des Unternehmensportal hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL:** Geben Sie optional die URL zu einer Website ein, die Informationen über die App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen:** Geben Sie optional die URL zu einer Website ein, die Datenschutzinformationen für die App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Befehlszeilenargumente:** Geben Sie optional Befehlszeilenargumente ein, die für die .msi-Datei gelten sollen, wenn sie ausgeführt wird, wie z.B. **/q**.
    - **Entwickler:** Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer:** Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. **Personalabteilung**.
    - **Anmerkungen:** Geben Sie Hinweise zu dieser App ein.
    - **Logo:** Laden Sie ein Symbol hoch, das der App zugeordnet wird. Das Symbol wird gemeinsam mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
3. Wenn Sie fertig sind, wählen Sie **OK** aus.

## <a name="step-4---finish-up"></a>Schritt 4: Fertig stellen

1. Überprüfen Sie im Bereich **App hinzufügen**, ob die App-Informationen richtig konfiguriert sind.
2. Wählen Sie **Hinzufügen** aus, um die App in Intune hochzuladen.

## <a name="step-5---update-a-line-of-business-app"></a>Schritt 5: Aktualisieren einer branchenspezifischen App

[!INCLUDE[shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="configuring-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Konfigurieren Sie eine mobile MSI-App, die sich selbst aktualisiert, um den Prozess der Versionsüberprüfung zu ignorieren.

Sie können eine bekannte mobile MSI-App konfigurieren, die sich selbst aktualisiert, um den Prozess der Versionsüberprüfung zu ignorieren. Einige auf den MSI-Installer basierende Apps werden vom App-Entwickler automatisch aktualisiert. Für diese automatisch aktualisierten MSI-Apps können Sie die Einstellung **App-Version ignorieren** auf dem Blatt **App-Informationen** konfigurieren. Wenn diese Einstellung auf **Ja** festgelegt wird, erzwingt Microsoft Intune keine App-Version, die auf dem Windows-Client installiert ist. Diese Einstellung ist nützlich, um Racebedingungen zu vermeiden. Diese Racebedingungen können z.B. auftreten, wenn die App vom App-Entwickler automatisch und gleichzeitig aber auch von Intune aktualisiert wird. Beide könnten dann eine Version der App auf dem Windows-Client erzwingen, was einen Konflikt auslösen kann.

## <a name="next-steps"></a>Nächste Schritte

- Die von Ihnen erstellte App wird in der Liste der Apps angezeigt. Sie können sie jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

- Erfahren Sie mehr darüber, wie Sie die Eigenschaften und Zuweisungen Ihrer App überwachen können. Weitere Informationen finden Sie unter [Überwachen von App-Informationen und -Zuweisungen](apps-monitor.md).

- Erfahren Sie mehr über den Kontext Ihrer App in Intune. Weitere Informationen finden Sie unter [Übersicht über die Lebenszyklen von Geräten und Apps](introduction-device-app-lifecycles.md).
