---
title: Verwenden von OEMConfig auf Android Enterprise-Geräten in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie Microsoft InTune, um Android-Geräte mit oemconfig zu verwalten und zu verwenden. Sehen Sie sich alle Schritte einschließlich einer Übersicht an, sehen Sie sich die Voraussetzungen an, erstellen Sie das Konfigurations Profil in InTune, und sehen Sie sich eine Liste der unterstützten oemconfig-apps an.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e8747f3dfa9169a4f1f2de9dcf45db0f5cccadd1
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73756757"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Verwenden und Verwalten von Android-Unternehmens Geräten mit oemconfig in Microsoft InTune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In Microsoft InTune können Sie oemconfig verwenden, um OEM-spezifische Einstellungen für Android-Unternehmens Geräte hinzuzufügen, zu erstellen und anzupassen. Oemconfig wird normalerweise verwendet, um Einstellungen zu konfigurieren, die nicht in InTune integriert sind. Verschiedene Originalgerätehersteller (OEM) enthalten unterschiedliche Einstellungen. Welche Einstellungen verfügbar sind, hängt davon ab, was der OEM in der oemconfig-app enthält.

Diese Funktion gilt für:  

- Android Enterprise

Dieser Artikel beschreibt oemconfig, listet die Voraussetzungen auf, zeigt, wie ein Konfigurations Profil erstellt wird, und listet die unterstützten oemconfig-apps in InTune auf.

## <a name="overview"></a>Übersicht

Oemconfig-Richtlinien sind eine besondere Art von Geräte Konfigurationsrichtlinie, die der [App-Konfigurationsrichtlinie](../apps/app-configuration-policies-overview.md)ähnelt. Oemconfig ist ein von Google definierter Standard, der die APP-Konfiguration in Android nutzt, um Geräteeinstellungen an Apps zu senden, die von OEMs (Originalgerätehersteller) geschrieben wurden. Dieser Standard ermöglicht OEMs und emms (Enterprise Mobility Management), OEM-spezifische Features auf standardisierte Weise zu erstellen und zu unterstützen. [Erfahren Sie mehr über oemconfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

In der Vergangenheit wurde von Emms, wie z. b. InTune, die Unterstützung für OEM-spezifische Features nach der Einführung durch den OEM manuell erstellt. Dieser Ansatz führt zu doppelten Anstrengungen und langsamen Akzeptanz.

Mit oemconfig erstellt ein OEM ein Schema, das OEM-spezifische Verwaltungs Features definiert. Der OEM bettet das Schema in eine APP ein und legt diese APP dann auf Google Play. Der EMM liest das Schema aus der APP und macht das Schema in der EMM-Administrator Konsole verfügbar. Die-Konsole ermöglicht InTune-Administratoren, die Einstellungen im Schema zu konfigurieren.

Wenn die oemconfig-App auf einem Gerät installiert wird, werden die in der EMM-Administrator Konsole konfigurierten Einstellungen verwendet, um das Gerät zu verwalten. Die Einstellungen auf dem Gerät werden von der oemconfig-APP und nicht von einem MDM-Agent ausgeführt, der vom EMM erstellt wurde.

Wenn der OEM Verwaltungs Features hinzufügt und verbessert, aktualisiert der OEM die APP auch in Google Play. Als Administrator erhalten Sie diese neuen Features und Updates (einschließlich Korrekturen), ohne darauf zu warten, dass EMMS diese Updates einschließt.

> [!TIP]
> Sie können oemconfig nur mit Geräten verwenden, die dieses Feature unterstützen und über eine entsprechende oemconfig-App verfügen. Wenden Sie sich an ihren OEM, um bestimmte Details anzuzeigen.

## <a name="before-you-begin"></a>Vorbereitung

Beachten Sie bei der Verwendung von oemconfig die folgenden Informationen:

- InTune macht das Schema der oemconfig-app verfügbar, damit Sie es konfigurieren können. InTune überprüft oder ändert nicht das von der APP bereitgestellte Schema. Wenn das Schema falsch ist oder falsche Daten enthält, werden diese Daten weiterhin an Geräte gesendet. Wenn Sie ein Problem finden, das aus dem Schema stammt, wenden Sie sich an den OEM.
- InTune beeinflusst oder steuert den Inhalt des App-Schemas nicht. InTune hat z. b. keine Kontrolle über Zeichen folgen, Sprache, zulässige Aktionen usw. Es wird empfohlen, den OEM zu kontaktieren, um ausführliche Informationen und bewährte Methoden für die Verwaltung Ihrer Geräte mit oemconfig zu erhalten.
- OEMs können jederzeit Ihre unterstützten Features und Schemas aktualisieren und eine neue app in Google Play hochladen. InTune synchronisiert immer die neueste Version der oemconfig-APP von Google Play. InTune verwaltet keine älteren Versionen des Schemas oder der app. Wenn Versions Konflikte auftreten, empfiehlt es sich, den OEM zu kontaktieren, um weitere Informationen zu erhalten.
- Zuweisen eines oemconfig-Profils zu einem Gerät. Wenn dem gleichen Gerät mehrere Profile zugewiesen sind, wird möglicherweise ein inkonsistentes Verhalten feststellen. Das oemconfig-Modell unterstützt nur eine einzelne Richtlinie pro Gerät.

## <a name="prerequisites"></a>Voraussetzungen

Um oemconfig auf Ihren Geräten zu verwenden, stellen Sie sicher, dass Sie die folgenden Anforderungen erfüllen:

- Ein in InTune registriertes Android-Unternehmens Gerät.
- Eine oemconfig-APP, die vom OEM erstellt und in Google Play hochgeladen wurde. Wenn dies Google Play nicht der Fall ist, wenden Sie sich an den OEM, um weitere Informationen zu erhalten.
- Der InTune-Administrator verfügt überrollen basierte Zugriffs Steuerungs Berechtigungen (Role-Based Access Control, RBAC) für **Mobile Apps**, **Geräte Konfigurationen**und die Berechtigung "lesen" unter **Android for Work**. Diese Berechtigungen sind erforderlich, da oemconfig-profile verwaltete App-Konfigurationen verwenden, um Geräte Konfigurationen zu verwalten.

## <a name="prepare-the-oemconfig-app"></a>Vorbereiten der oemconfig-App

Stellen Sie sicher, dass das Gerät oemconfig unterstützt, dass die richtige oemconfig-APP zu InTune hinzugefügt wird und die APP auf dem Gerät installiert ist. Wenden Sie sich für diese Informationen an den OEM.

> [!TIP] 
> Oemconfig-apps sind spezifisch für OEM. Beispielsweise führt eine auf einem Zebra Technologies-Gerät installierte app "oemconfig" auf einem Gerät nichts aus.

1. Laden Sie die oemconfig-App aus der verwalteten Google Play Store. Unter [Hinzufügen von verwalteten Google Play-Apps zu Android Enterprise-Geräten](../apps/apps-add-android-for-work.md) werden die Schritte erläutert.
2. Einige OEMs können Geräte mit vorinstallierter oemconfig-App versenden. Wenn die APP nicht vorinstalliert ist, verwenden Sie InTune zum [Hinzufügen und Bereitstellen der APP auf Geräten](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Erstellen eines oemconfig-Profils

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431)an.
2. Wählen Sie **Geräte** > **Konfigurations profile** > **Profil erstellen**aus.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform:** Wählen Sie **Android Enterprise** aus.
    - **Profiltyp**: Wählen Sie " **oemconfig**" aus.

4. Wählen Sie **zugehörige App**aus, wählen Sie eine vorhandene oemconfig-App aus, die Sie zuvor **hinzu > gefügt**haben Stellen Sie sicher, dass Sie die richtige oemconfig-App für die Geräte auswählen, denen Sie die Richtlinie zuweisen.

    Wenn keine aufgelisteten apps angezeigt werden, richten Sie verwaltete Google Play ein, und holen Sie Apps aus dem verwalteten Google Play Store. Unter [Hinzufügen von verwalteten Google Play-Apps zu Android Enterprise-Geräten](../apps/apps-add-android-for-work.md) werden die Schritte erläutert.

    > [!IMPORTANT]
    > Wenn Sie eine oemconfig-app hinzugefügt und Sie mit Google Play synchronisiert haben, diese aber nicht als **zugehörige App**aufgeführt ist, müssen Sie möglicherweise InTune kontaktieren, um die APP zu integrieren. Weitere Informationen finden Sie unter [Hinzufügen einer neuen App](#supported-oemconfig-apps) (in diesem Artikel).

5. Wählen Sie unter **Einstellungen konfigurieren mit**den Konfigurations- **Designer** oder den **JSON-Editor**aus:

    > [!TIP]
    > Lesen Sie die OEM-Dokumentation, um sicherzustellen, dass Sie die Eigenschaften ordnungsgemäß konfigurieren. Diese APP-Eigenschaften werden vom OEM, nicht von InTune, eingeschlossen. InTune führt nur eine minimale Überprüfung der Eigenschaften durch, oder was Sie eingeben. Wenn Sie z. b. `abcd` für eine Portnummer eingeben, speichert das Profil unverändert und wird auf Ihren Geräten mit den von Ihnen konfigurierten Werten bereitgestellt. Stellen Sie sicher, dass Sie die richtigen Informationen eingeben.

    - **Konfigurations-Designer**: Wenn Sie diese Option auswählen, werden die Eigenschaften, die im App-Schema verfügbar sind, für die Konfiguration angezeigt.

      - Kontextmenüs im Konfigurations-Designer zeigen an, dass weitere Optionen verfügbar sind. Beispielsweise können Sie mit dem Kontextmenü Einstellungen hinzufügen, löschen und neu anordnen. Diese Optionen sind im OEM enthalten. Lesen Sie unbedingt die Dokumentation zu OEM-apps, um zu erfahren, wie diese Optionen zum Erstellen von Profilen verwendet werden sollten.

      - Viele Einstellungen verfügen über Standardwerte, die vom OEM bereitgestellt werden. Um festzustellen, ob ein Standardwert vorhanden ist, bewegen Sie den Mauszeiger über das Info-Symbol neben der Einstellung. Eine QuickInfo zeigt die Standardwerte für diese Einstellung (falls zutreffend) und weitere Details an, die der OEM bereitstellt.

      - Wenn Sie auf **Löschen** klicken, wird eine Einstellung aus dem Profil gelöscht. Wenn eine Einstellung nicht im Profil angezeigt wird, ändert sich der Wert auf dem Gerät nicht, wenn das Profil angewendet wird.

      - Wenn Sie im Konfigurations-Designer ein leeres (nicht konfiguriertes) Paket erstellen, wird es beim Wechseln zum JSON-Editor gelöscht.

    - **JSON-Editor**: Wenn Sie diese Option auswählen, wird ein JSON-Editor mit einer Vorlage für das vollständige Konfigurations Schema geöffnet, das in der APP eingebettet ist. Passen Sie im Editor die Vorlage mit Werten für die anderen Einstellungen an. Wenn Sie den- **Konfigurations-Designer** verwenden, um die Werte zu ändern, überschreibt der JSON-Editor die Vorlage mit Werten aus dem Konfigurations-Designer.

      - Wenn Sie ein vorhandenes Profil aktualisieren, zeigt der JSON-Editor die Einstellungen an, die zuletzt mit dem Profil gespeichert wurden.

      - Oemconfig-Schemas können groß und komplex sein. Wenn Sie diese Einstellungen mit einem anderen Editor aktualisieren möchten, klicken Sie auf die Schaltfläche **JSON-Vorlage herunterladen** . Verwenden Sie einen Editor Ihrer Wahl, um ihrer Vorlage Konfigurationswerte hinzuzufügen. Kopieren Sie anschließend den aktualisierten JSON-Code, und fügen Sie ihn in die **JSON-Editor** -Eigenschaft ein.

      - Sie können den JSON-Editor verwenden, um eine Sicherung Ihrer Konfiguration zu erstellen. Nachdem Sie die Einstellungen konfiguriert haben, verwenden Sie diese Funktion, um die JSON-Einstellungen mit ihren Werten zu erhalten. Kopieren Sie den JSON-Code in eine Datei, und speichern Sie ihn. Nun verfügen Sie über eine Sicherungsdatei.

    Alle Änderungen, die im Konfigurations-Designer vorgenommen werden, werden auch automatisch im JSON-Editor vorgenommen. Ebenso werden alle im JSON-Editor vorgenommenen Änderungen automatisch im Konfigurations-Designer vorgenommen. Wenn Ihre Eingabe ungültige Werte enthält, können Sie erst zwischen dem Konfigurations-Designer und dem JSON-Editor wechseln, wenn Sie die Probleme behoben haben.

6. Klicken Sie auf **OK** > **Hinzufügen**, um die Änderungen zu speichern. Die Richtlinie wird erstellt und in der Liste angezeigt.

Denken Sie daran, das [Profil zuzuweisen](device-profile-assign.md) und [seinen Status zu überwachen](device-profile-monitor.md).

 > [!NOTE]
 > Weisen Sie jedem Gerät ein Profil zu. Das oemconfig-Modell unterstützt nur eine Richtlinie pro Gerät.

Wenn das Gerät das nächste Mal nach Konfigurations Updates sucht, werden die von Ihnen konfigurierten OEM-spezifischen Einstellungen auf die oemconfig-App angewendet.

> [!NOTE]
> Der oemconfig-Standard enthält derzeit keine Status Berichterstattung. Standardmäßig zeigen Profile einen **ausstehenden** Status an.

## <a name="supported-oemconfig-apps"></a>Unterstützte oemconfig-apps

Im Vergleich zu Standard-apps erweitern oemconfig-Apps die von Google gewährten Berechtigungen für verwaltete Konfigurationen, um komplexere Schemas zu unterstützen. InTune unterstützt derzeit die folgenden oemconfig-apps:

-----------------

| OEM | Paket-ID | OEM-Dokumentation (falls verfügbar) |
| --- | --- | ---|
| Samsung | com. Samsung. Android. Knox. KPU | [Administrator Handbuch für Knox Service Plugin](https://docs.samsungknox.com/knox-service-plugin/admin-guide/welcome.htm) |
| Zebra Technologien | com. Zebra. oemconfig. Common | [Übersicht über "Zebra oemconfig"](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com. Datalogic. oemconfig | [Benutzerdokumentation für Datalogic oemconfig](https://datalogic.github.io/oemconfig/) |
| Honeywell | com. Honeywell. oemconfig |  |
| Kyocera | JP. Kyocera. enterprisseabviceconfig |  |

-----------------

Wenn eine oemconfig-Anwendung für Ihr Gerät vorhanden ist, Sie sich aber nicht in der obigen Tabelle befindet oder nicht in der InTune-Konsole angezeigt wird, senden Sie eine e-Mail an `IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> Oemconfig-apps müssen von InTune integriert werden, bevor Sie mit oemconfig-Profilen konfiguriert werden können. Sobald eine App unterstützt wird, müssen Sie sich nicht mehr an Microsoft wenden, um Sie in Ihrem Mandanten einzurichten. Befolgen Sie einfach die Anweisungen auf dieser Seite.

## <a name="next-steps"></a>Nächste Schritte

- [Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
