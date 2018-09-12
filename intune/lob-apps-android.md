---
title: Hinzufügen von branchenspezifischen Android-Apps zu Microsoft Intune
titlesuffix: ''
description: Erfahren Sie mehr über das Hinzufügen von branchenspezifischen Android-Apps in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a49811200cd84882fe9f80708edefde7614e5cee
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347864"
---
# <a name="add-an-android-line-of-business-app-to-microsoft-intune"></a>Hinzufügen von branchenspezifischen Android-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Eine branchenspezifische App (LOB) ist eine App, die Sie aus einer App-Installationsdatei zu Intune hinzufügen. Diese Art von App wird in der Regel intern geschrieben. Intune installiert die branchenspezifische App auf dem Gerät des Benutzers. 

> [!Note]
> Weitere Informationen zu branchenspezifischen Apps aus dem Managed Google Play Store finden Sie unter [Arbeiten mit einer branchenspezifischen App aus dem Managed Google Play Store](apps-add-android-for-work.md?#working-with-a-line-of-business-app-from-the-managed-google-play-store). 

## <a name="step-1-specify-the-software-setup-file"></a>Schritt 1: Angeben der Softwaresetupdatei

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** die Option **Client-Apps** aus.
4. Wählen Sie in der Workload **Client-Apps** die Option **Verwalten** > **Apps** aus.
5. Wählen Sie oberhalb der App-Liste **Hinzufügen** aus.
6. Wählen Sie im Bereich **App hinzufügen** die Option **Branchenspezifische App** aus.

## <a name="step-2-configure-the-app-package-file"></a>Schritt 2: Konfigurieren der App-Paketdatei

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Paketdatei** aus.
2. Wählen Sie im Bereich **App-Paketdatei** die Schaltfläche zum Durchsuchen. Wählen Sie dann eine Android-Installationsdatei mit der Erweiterung **XAP**.
3. Wählen Sie danach **OK**.


## <a name="step-3-configure-app-information"></a>Schritt 3: Konfigurieren von App-Informationen

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Informationen**.
2. Fügen Sie im Bereich **App-Informationen** Details zu Ihrer App hinzu. Abhängig von der ausgewählten App wurden einige der Werte in diesem Bereich möglicherweise automatisch ausgefüllt.
    - **Name:** Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Die Beschreibung wird im Unternehmensportal angezeigt.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    - **Mindestens erforderliches Betriebssystem**: Wählen Sie aus der Liste die mindestens erforderliche Betriebssystemversion aus, auf der die App installiert werden kann. Wenn Sie die App einem Gerät mit einem älteren Betriebssystem zuweisen, wird sie nicht installiert.
    - **App-Version ignorieren**: Legen Sie **Ja** fest, wenn der Entwickler die App automatisch aktualisiert.
    - **Kategorie:** Wählen Sie eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Kategorien erleichtern es dem Benutzer, die App über das Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Zeigen Sie die App auf der Hauptseite des Unternehmensportals hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL:** Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen:** Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **Entwickler:** Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer:** Geben Sie optional einen Namen für den Besitzer dieser App ein. Ein Beispiel ist **Personalabteilung**.
    - **Anmerkungen:** Geben Sie Hinweise zu dieser App ein.
    - **Logo**: Laden Sie ein Symbol für die App hoch. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
3. Wählen Sie danach **OK**.

## <a name="step-4-finish-up"></a>Schritt 4: Fertig stellen

1. Prüfen Sie Ihre Angaben im Bereich **App hinzufügen**.
2. Wählen Sie **Hinzufügen**, um die App in Intune hochzuladen.

Die von Ihnen erstellte App wird nun in der Liste der Apps angezeigt. Sie können die App über die Liste den von Ihnen ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

## <a name="step-5-update-a-line-of-business-app"></a>Schritt 5: Aktualisieren einer branchenspezifischen App

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!Note]
> Damit der Intune-Dienst eine neue APK-Datei erfolgreich auf dem Gerät bereitstellt, müssen Sie die Zeichenfolge „`android:versionCode`“ in der Datei „AndroidManifest.xml“ in Ihrem APK-Paket erhöhen.

## <a name="next-steps"></a>Nächste Schritte

- Die von Ihnen erstellte App wird in der Liste der Apps angezeigt. Sie können sie jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

- Erfahren Sie mehr darüber, wie Sie die Eigenschaften und Zuweisungen Ihrer App überwachen können. Siehe [Überwachen von App-Informationen und -Zuweisungen](apps-monitor.md).

- Erfahren Sie mehr über den Kontext Ihrer App in Intune. Siehe [Übersicht über die Lebenszyklen von Geräten und Apps](introduction-device-app-lifecycles.md).
