---
title: Hinzufügen von branchenspezifischen Android-Apps zu Microsoft Intune
titlesuffix: ''
description: Erfahren Sie mehr über das Hinzufügen von branchenspezifischen Android-Apps in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a5b09f855b6da65edf3c560725b339528f2bcfaa
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-add-android-line-of-business-lob-apps-to-microsoft-intune"></a>Hinzufügen von branchenspezifischen Android-Apps (LOB) in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Eine branchenspezifische App (LOB) ist eine App, die Sie aus einer App-Installationsdatei zu Intune hinzufügen. Solche Apps werden in der Regel intern geschrieben. Intune installiert die branchenspezifische App auf dem Gerät des Benutzers. 

> [!Note]
> Weitere Informationen zu branchenspezifischen Apps aus dem Google Play for Work Store finden Sie unter [Working with a line-of-business app from the Google Play for Work store (Arbeiten mit einer branchenspezifischen App aus dem Google Play for Work Store)](apps-add-android-for-work.md?#working-with-a-line-of-business-app-from-the-google-play-for-work-store). 

## <a name="step-1---specify-the-software-setup-file"></a>Schritt 1: Angeben der Softwaresetupdatei

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Mobile Apps**.
4. Wählen Sie in der Workload **Mobile Apps** die Option **Verwalten** > **Apps** aus.
5. Wählen Sie über der Liste der Apps **Hinzufügen** aus.
6. Klicken Sie im Bereich **App hinzufügen** auf **Branchenspezifische App**.

## <a name="step-2---configure-the-app-package-file"></a>Schritt 2: Konfigurieren der App-Paketdatei

1. Klicken Sie im Bereich **App hinzufügen** auf die Option **App-Paketdatei**.
2. Klicken Sie im Bereich **App-Paketdatei** auf die Schaltfläche „Durchsuchen“, und wählen Sie eine Installationsdatei mit der Erweiterung **.apk** aus.
3. Wenn Sie fertig sind, wählen Sie **OK** aus.


## <a name="step-3---configure-app-information"></a>Schritt 3: Konfigurieren von App-Informationen

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Paketdatei** aus.
2. Fügen Sie im Bereich **App-Informationen** Details zu Ihrer App hinzu. Abhängig von der ausgewählten App wurden einige der Werte in diesem Bereich möglicherweise automatisch ausgefüllt:
    - **Name:** Geben Sie den Namen der App ein, der im Unternehmensportal angezeigt werden soll. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein, die den Benutzern im Unternehmensportal angezeigt werden soll.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    - **Mindestens erforderliches Betriebssystem:** Wählen Sie in der Liste die mindestens erforderliche Betriebssystemversion aus, auf der die App installiert werden kann. Wenn Sie die App einem Gerät mit einem älteren Betriebssystem zuweisen, wird sie nicht installiert.
    - **App-Version ignorieren**: Legen Sie **Ja** fest, wenn die App automatisch vom Entwickler aktualisiert wird.
    - **Kategorie:** Wählen Sie eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen:** Zeigen Sie die App auf der Hauptseite des Unternehmensportal hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL:** Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen:** Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler:** Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer:** Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. **Personalabteilung**.
    - **Anmerkungen:** Geben Sie Hinweise zu dieser App ein.
    - **Logo:** Laden Sie ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird gemeinsam mit der App angezeigt, wenn der Benutzer das Unternehmensportal durchsucht.
3. Wenn Sie fertig sind, wählen Sie **OK** aus.

## <a name="step-4---finish-up"></a>Schritt 4: Fertig stellen

1. Prüfen Sie Ihre App-Informationen im Bereich **App hinzufügen**.
2. Wählen Sie **Hinzufügen** aus, um die App in Intune hochzuladen.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie ausgewählten Gruppen zuweisen können. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

## <a name="step-5---update-a-line-of-business-app"></a>Schritt 5: Aktualisieren einer branchenspezifischen App

[!INCLUDE[shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!Note]
> Damit der Intune-Dienst eine neue APK-Datei erfolgreich auf dem Gerät bereitstellt, müssen Sie die Zeichenfolge „android:versionCode“ in der Datei „AndroidManifest.xml“ in Ihrem APK-Paket erhöhen.

## <a name="next-steps"></a>Nächste Schritte

- Die von Ihnen erstellte App wird in der Liste der Apps angezeigt. Sie können sie jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

- Erfahren Sie mehr darüber, wie Sie die Eigenschaften und Zuweisungen Ihrer App überwachen können. Weitere Informationen finden Sie unter [Überwachen von App-Informationen und -Zuweisungen](apps-monitor.md).

- Erfahren Sie mehr über den Kontext Ihrer App in Intune. Weitere Informationen finden Sie unter [Übersicht über die Lebenszyklen von Geräten und Apps](introduction-device-app-lifecycles.md).
