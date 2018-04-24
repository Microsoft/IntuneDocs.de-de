---
title: Schützen branchenspezifischer Apps auf nicht registrierten Geräten
description: In diesem Thema wird beschrieben, wie Sie Ihre benutzerdefinierte Reihe von Branchen-Anwendungen vorbereiten können, sodass Sie Verwaltungsrichtlinien für mobile Apps anwenden können, die helfen können, Datenverluste zu verhindern.
keywords: ''
author: mattbriggs
ms.author: mabriggs
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 00219467-a62e-43b6-954b-3084f54c45ba
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0fbc7ae1937aff60e8e494df06ee2c30e2fe8855
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="protect-line-of-business-apps-and-data-on-devices-that-are-not-enrolled-in-microsoft-intune"></a>Schützen von branchenspezifischen Apps und Daten auf nicht in Microsoft Intune registrierten Geräten

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Mit Richtlinien zur Verwaltung mobiler Anwendungen (Mobile App Management, MAM) können Sie Unternehmensdaten schützen, indem Aktionen, die zu Datenlecks führen könnten, eingeschränkt und Datenzugriffsanforderungen wie die Eingabe einer App-PIN erzwungen werden. Zum Anwenden von MAM-Richtlinien auf branchenspezifische iOS- und Android-Apps müssen Sie die App zunächst mit dem Microsoft Intune App Wrapping Tool umschließen. Bei diesem Prozess wird einer mobilen App eine Verwaltungsebene hinzugefügt, ohne dass diese geändert werden muss, und sie wird an Benutzer verteilt.  

In diesem Thema werden die erforderlichen Schritte zum Anwenden von MAM-Richtlinien auf Apps vorgestellt, auf die Benutzer auf **nicht verwalteten Geräten im Besitz von Mitarbeitern** und auf Geräten, die von einer **Lösung für die Verwaltung von Mobilgeräten (Mobile Device Management, MDM) eines Drittanbieters** verwaltet werden, zugreifen.  Informationen zum Vorbereiten branchenspezifischer Apps, die auf **bei Intune MDM registrierten Geräten** ausgeführt werden, finden Sie unter [Auswählen der Vorbereitung von Apps für die mobile Anwendungsverwaltung mit Microsoft Intune](/intune/apps-prepare-mobile-application-management).


##  <a name="step-1-prepare-the-app"></a>Schritt 1: Vorbereiten der App

Bevor Sie MAM-Richtlinien auf eine App anwenden können, müssen Sie die App zuerst mit dem Microsoft Intune App Wrapping Tool für [iOS](/intune/app-wrapper-prepare-ios) und [Android](/intune/app-wrapper-prepare-android) umschließen, oder das [Intune App SDK](/intune/app-sdk) verwenden, um die Schutzfunktionen der Intune-App manuell zu integrieren.

Weitere Informationen zur Entscheidung zwischen dem App Wrapping Tool und dem SDK finden Sie unter [Auswählen der Vorbereitung von Apps für die mobile Anwendungsverwaltung mit Microsoft Intune](/intune/apps-prepare-mobile-application-management).

## <a name="step-2-add-the-app"></a>Schritt 2: Hinzufügen der App

Um Ihre branchenspezifische App zu MAM-Richtlinien zuzuordnen, müssen Sie Ihrem Intune-Abonnement/-Mandanten die App-Details wie folgt hinzufügen:

1. Wechseln Sie im [Azure-Portal](https://portal.azure.com/) zu **Mobile Anwendungsverwaltung mit Intune** > **Einstellungen**, und wählen Sie **Branchenspezifische Apps**.

   ![Screenshot des Blatts „Einstellungen“ mit der Option „Branchenspezifische Apps“](../media/mam-azure-portal-lob-on-settings.png)

2. Wählen Sie auf dem Blatt **Branchenspezifische Apps** die Option **Benutzerdefinierte App hinzufügen** aus.

   ![Screenshot des Blatts „Branchenspezifische Apps“ mit der Schaltfläche „Benutzerdefinierte App hinzufügen“ oben](../media/mam-azure-portal-add-lob-app-action.png)
3. Geben Sie einen Namen für die App, die Paket-ID in das Feld „App-ID“ und die Plattform (iOS oder Android) an.

   ![Screenshot des Blatts „Benutzerdefinierte App hinzufügen“](../media/mam-azure-portal-add-app-details.png)

   Dieser Schritt dient zum Erstellen einer eindeutigen Auflistung Ihrer App. Die App wird auch in der Liste der Ziel-Apps für eine MAM-Richtlinie für Ihren Mandanten angezeigt (siehe den nächsten Schritt).

## <a name="step-3-apply-mam-policies"></a>Schritt 3: Anwenden von MAM-Richtlinien
Nachdem die App-Metadaten in den Dienst hochgeladen wurden, zeigt die App die Liste mit Apps an. Sie können jetzt [eine neue Richtlinie erstellen oder eine vorhandene Richtlinie verwenden](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) und sie auf die branchenspezifische App anwenden, die Sie in Schritt 2 hinzugefügt haben.

>[!IMPORTANT]
>Die MAM-Richtlinie muss für die Benutzer erstellt werden, die die umschlossene App verwenden werden.  Benutzer, für die diese Richtlinie nicht bereitgestellt wird, können die App nicht verwenden.


  ![Screenshot des Blatts mit der Zielliste der Apps mit der angezeigten neuen branchenspezifischen App](../media/mam-azure-portal-lob-on-targeted-app-list.png)
## <a name="step-4-distribute-the-app"></a>Schritt 4: Verteilen der App
Sie können Apps für Ihre Benutzer wie folgt bereitstellen:
* Für Geräte, die bei einer MDM-Lösung eines Drittanbieters registriert sind, können Sie die Apps über Ihre MDM-Lösung verteilen.
* Für Geräte, die von keiner MDM-Lösung verwaltet werden, benötigen Sie eine benutzerdefinierte Lösung. Benutzer müssen die App herunterladen und auf ihrem Gerät installieren.

## <a name="change-the-metadata"></a>Ändern der Metadaten
Falls Sie App-Details wie den Namen der App oder die Paket-ID ändern müssen, müssen Sie [die App entfernen](#remove-apps) und mit den neuen Metadaten [hinzufügen](#step-2-add-the-app).

##  <a name="remove-apps"></a>Entfernen von Apps
Sie können eine branchenspezifische App aus der App-Liste entfernen. Dadurch wird die App aus der Liste und die Zuordnung zu MAM-Richtlinien entfernt, ohne dass die App jedoch vom Gerät des Benutzers entfernt oder deinstalliert wird.  

1. Wechseln Sie im [Azure-Portal](https://portal.azure.com/) zu **Intune-Verwaltung von mobilen Anwendungen** > **Einstellungen**. Wählen Sie auf dem Blatt **Einstellungen** den Eintrag **Branchenspezifische Apps**, um die Liste vorhandener Apps anzuzeigen.  
2. Wählen Sie die App aus, die Sie entfernen möchten, und klicken Sie auf **(...)**, um das Kontextmenü zu öffnen.

   ![Screenshot des Blatts „Branchenspezifische Apps“ mit der Schaltfläche mit den Auslassungszeichen](../media/mam-azure-portal-lob-context-menu.png)
3. Wählen Sie **Anwendung löschen** aus, um die App zu löschen.

   ![Screenshot des Blatts „Branchenspezifische Apps“ mit der Option „Anwendung löschen“](../media/mam-azure-portal-delete-app.png)

   Dies entfernt Apps aus der Liste der branchenspezifischen Apps und der Zielliste von Apps in der MAM-Richtlinie.
