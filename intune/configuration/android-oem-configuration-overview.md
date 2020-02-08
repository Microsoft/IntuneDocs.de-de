---
title: Verwenden von OEMConfig auf Android Enterprise-Geräten in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Mit OEMConfig Microsoft Intune zum Verwalten und Verwenden von Geräten unter Android Enterprise einsetzen. Sie erhalten Informationen zu sämtlichen Schritten, einschließlich einer Übersicht, und zu den Voraussetzungen. Außerdem wird erläutert, wie Sie ein Konfigurationsprofil in Intune erstellen, und alle unterstützten OEMConfig-Apps werden aufgelistet.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2020
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
ms.openlocfilehash: 9cc568cbadb683f632ffd2365ab7023cd796f231
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886691"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Verwenden und Verwalten von Android Enterprise-Geräten mit OEMConfig in Microsoft Intune

Sie können OEMConfig in Microsoft Intune verwenden, um OEM-spezifische Einstellungen für Android Enterprise-Geräte hinzuzufügen, zu erstellen und anzupassen. OEMConfig wird in der Regel verwendet, um nicht in Intune integrierte Einstellungen zu konfigurieren. Jeder Originalgerätehersteller (Original Equipment Manufacturer, OEM) bietet eigene Einstellungen an. Welche Einstellungen verfügbar sind, ist davon abhängig, welche Elemente der OEM in seine OEMConfig-App integriert.

Diese Funktion gilt für:  

- Android Enterprise

Dieser Artikel enthält Informationen zu OEMConfig und zu den Voraussetzungen. Außerdem wird erläutert, wie Sie ein Konfigurationsprofil erstellen, und es werden alle in Intune unterstützten OEMConfig-Apps aufgelistet.

## <a name="overview"></a>Übersicht

OEMConfig-Richtlinien sind eine besondere Art von Richtlinien für die Gerätekonfiguration und ähneln den [Gerätekonfigurationsrichtlinien](../apps/app-configuration-policies-overview.md). OEMConfig ist ein von Google definierter Standard, bei dem die App-Konfiguration in Android verwendet wird, um Geräteeinstellungen an Apps von OEMs zu senden. Dieser Standard ermöglicht es OEMs und EMM-Anbietern (Enterprise Mobility Management), OEM-spezifische Features einheitlich zu erstellen und zu unterstützen. [Weitere Informationen zu OEMConfig.](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/)

In der Vergangenheit mussten EEM-Anbieter wie Intune manuell Unterstützung für OEM-spezifische Features integrieren, nachdem diese vom OEM eingeführt wurden. Dieser Ansatz ist sehr aufwendig und führt dazu, dass die Änderungen nur langsam übernommen werden.

Mit OEMConfig kann der OEM ein Schema erstellen, das OEM-spezifische Verwaltungsfeatures definiert. Der OEM bettet das Schema in eine App ein, und veröffentlicht diese dann im Google Play Store. Der EMM-Anbieter liest das Schema aus der App, und stellt es in der EMM-Administratorkonsole zur Verfügung. Mithilfe der Konsole können Intune-Administratoren die Einstellungen im Schema konfigurieren.

Wenn die OEMConfig-App auf einem Gerät installiert wird, verwendet diese die im EMM-Administrator konfigurierten Einstellungen, um das Gerät zu verwalten. Geräteeinstellungen werden von der OEMConfig-App und nicht von einem Agent für die Verwaltung mobiler Geräte ausgeführt, der vom EMM-Anbieter erstellt wurde.

Wenn der OEM Verwaltungsfeatures hinzufügt oder verbessert, aktualisiert er ebenfalls die App im Google Play Store. Als Administrator erhalten Sie diese neuen Features und Updates (einschließlich Korrekturen), ohne darauf warten zu müssen, dass der EMM-Anbieter diese integriert.

> [!TIP]
> Sie können OEMConfig nur mit Geräten verwenden, die dieses Feature unterstützen und über eine passende OEMConfig-App verfügen. Informationen zu Details erhalten Sie von Ihrem OEM.

## <a name="before-you-begin"></a>Vorbereitung

Beachten Sie bei der Verwendung von OEMConfig die folgenden Informationen:

- Intune stellt das Schema der OEMConfig-App zur Verfügung, damit Sie es konfigurieren können. Intune überprüft oder ändert das von der App bereitgestellte Schema nicht. Wenn das Schema falsch ist oder falsche Daten enthält, werden diese Daten weiterhin an Geräte gesendet. Wenn Sie ein Problem feststellen, das auf dieses Schema zurückzuführen ist, kontaktieren Sie den OEM, damit dieser Ihnen weiterhilft.
- Intune beeinflusst oder steuert die Inhalte des App-Schemas nicht. Beispielsweise hat Intune keine Kontrolle über Zeichenfolgen, Sprachen, zulässige Aktionen usw. Es wird empfohlen, den OEM zu kontaktieren und um Informationen zur Verwaltung seiner Geräte mit OEMConfig zu bitten.
- OEMs können ihre unterstützten Features und Schemas jederzeit aktualisieren und eine neue App im Google Play Store hochladen. Intune synchronisiert immer die neuste Version der OEMConfig-App aus dem Google Play Store. Ältere Versionen des Schemas oder der App verwaltet Intune nicht. Wenn Versionskonflikte auftreten, sollten Sie den OEM kontaktieren und um weitere Informationen bitten.
- Weisen Sie einem Gerät ein OEMConfig-Profil zu. Wenn einem Gerät mehrere Profile zugewiesen werden, kann dies zu inkonsistentem Verhalten führen. Das OEMConfig-Modell unterstützt nur eine einzelne Richtlinie pro Gerät.

## <a name="prerequisites"></a>Voraussetzungen

Damit Sie OEMConfig auf Ihren Geräten verwenden können, müssen Sie die folgenden Voraussetzungen erfüllen:

- Ein für Intune registriertes Android Enterprise-Gerät
- Eine vom OEM erstellte OEMConfig-App, die in den Google Play Store geladen wurde. Wenn sie nicht im Google Play Store zur Verfügung steht, kontaktieren Sie den OEM, um weitere Informationen zu erhalten.
- Der Intune-Administrator verfügt über RBAC-Berechtigungen (Role-based Access Control = rollenbasierte Zugriffssteuerung) für **Mobile Apps** und die **Gerätekonfiguration** sowie über Leseberechtigungen unter **Android for Work**. Diese Berechtigungen sind notwendig, da OEMConfig-Profile verwaltete App-Konfigurationen verwenden, um Gerätekonfigurationen zu verwalten.

## <a name="prepare-the-oemconfig-app"></a>Vorbereiten der OEMConfig-App

Vergewissern Sie sich, dass das Gerät OEMConfig unterstützt, dass die richtige OEMConfig-App zu Intune hinzugefügt wird und dass die App auf dem Gerät installiert wird. Wenden Sie sich dafür an den OEM.

> [!TIP] 
> OEMConfig-Apps sind OEM-spezifisch. Beispielswiese funktioniert eine OEMConfig-App von Sony nicht, wenn sie auf einem Zebra Technologies-Gerät installiert wird.

1. Laden Sie die OEMConfig-App aus dem verwalteten Google Play Store herunter. Unter [Hinzufügen von verwalteten Google Play-Apps zu Android Enterprise-Geräten](../apps/apps-add-android-for-work.md) werden die Schritte erläutert.
2. Einige OEMs liefern möglicherweise Geräte aus, auf denen die OEMConfig-App bereits vorinstalliert ist. Wenn die App nicht vorinstalliert ist, verwenden Sie Intune, um [die App hinzuzufügen und auf den Geräten bereitzustellen](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Erstellen eines OEMConfig-Profils

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Plattform**: Wählen Sie **Android Enterprise** aus.
    - **Profiltyp:** Wählen Sie **OEMConfig** aus.

4. Wählen Sie **Erstellen** aus.
5. Geben Sie in **Grundlagen** die folgenden Eigenschaften ein:

    - **Name:** Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **OEMConfig-App**: Wählen Sie **OEMConfig-App auswählen** aus.

6. Wählen Sie unter **Zugeordnete App** eine bereits vorhandene OEMConfig-App aus, die Sie zuvor hinzugefügt haben, und klicken Sie auf **Auswählen**. Vergewissern Sie sich, dass Sie die richtige OEMConfig-App für die Geräte auswählen, denen Sie die Richtlinie zuweisen.

    Wenn Ihnen keine Apps angezeigt werden, richten Sie den verwalteten Google Play Store ein, und laden Sie Apps aus diesem herunter. Unter [Hinzufügen von verwalteten Google Play-Apps zu Android Enterprise-Geräten](../apps/apps-add-android-for-work.md) wird erläutert, wie Sie dabei vorgehen müssen.

    > [!IMPORTANT]
    > Wenn Sie eine OEMConfig-App hinzugefügt und mit dem Google Play Store konfiguriert haben, diese aber nicht als **Zugeordnete App** aufgeführt ist, müssen Sie möglicherweise Intune kontaktieren, um die App zu integrieren. Weitere Informationen finden Sie im Abschnitt [Hinzufügen einer neuen App](#supported-oemconfig-apps) in diesem Artikel.

7. Wählen Sie **Weiter** aus.
8. Wählen Sie unter **Einstellungen konfigurieren** den **Konfigurations-Designer** oder den **JSON-Editor** aus:

    > [!TIP]
    > Lesen Sie sich die OEM-Dokumentation durch, um sich zu vergewissern, dass Sie die Eigenschaften richtig konfigurieren. Diese App-Eigenschaften werden vom OEM hinzugefügt, nicht von Intune. Intune führt nur eine Mindestüberprüfung der Eigenschaften oder Ihrer Eingabe durch. Wenn Sie z. B. die Portnummer `abcd` eingeben, wird das Profil ohne Änderungen gespeichert und mit den von Ihnen konfigurierten Werten auf Ihren Geräten bereitgestellt. Achten Sie darauf, alle Informationen richtig einzugeben.

    - **Konfigurations-Designer:** Wenn Sie diese Option auswählen, werden Ihnen die in diesem App-Schema verfügbaren Eigenschaften angezeigt, damit Sie diese konfigurieren können.

      - Kontextmenüs im Konfigurations-Designer enthalten Informationen zu weiteren verfügbaren Optionen. Sie können beispielsweise über das Kontextmenü Einstellungen hinzufügen, löschen oder neu anordnen. Diese Optionen sind im OEM enthalten. Lesen Sie unbedingt die App-Dokumentation des OEM, um sich darüber zu informieren, wie diese Optionen zum Erstellen von Profilen verwendet werden sollen.

      - Viele Einstellungen verfügen über Standardwerte, die vom OEM bereitgestellt werden. Sie können herausfinden, ob es einen Standardwert gibt, indem Sie den Mauszeiger auf das Infosymbol neben der jeweiligen Einstellung bewegen. In einer QuickInfo wird dann, falls vorhanden, der Standardwert für diese Einstellung sowie weitere vom OEM bereitgestellte Details angezeigt.

      - Wenn Sie auf **Löschen** klicken, wird eine Einstellung aus dem Profil gelöscht. Wenn eine Einstellung nicht im Profil enthalten ist, wird deren Wert nicht auf dem Gerät geändert, wenn das Profil angewendet wird.

      - Wenn Sie im Konfigurations-Designer ein leeres (nicht konfiguriertes) Bundle erstellen, wird es beim Wechsel zum JSON-Editor gelöscht.

    - **JSON-Editor**: Wenn Sie diese Option auswählen, wird ein JSON-Editor mit einer Vorlage für das vollständige Konfigurationsschema geöffnet, das in die App eingebettet ist. Passen Sie im Editor die Vorlage mit Werten für die anderen Einstellungen an. Wenn Sie den **Konfigurations-Designer** verwenden, um die Werte zu ändern, überschreibt der JSON-Editor die Vorlage mit Werten aus dem Konfigurations-Designer.

      - Wenn Sie ein bestehendes Profil aktualisieren, zeigt der JSON-Editor die Einstellungen an, die zuletzt mit dem Profil gespeichert wurden.

      - OEMConfig-Schemas können groß und komplex sein. Wenn Sie diese Einstellungen mit einem anderen Editor aktualisieren möchten, klicken Sie auf die Schaltfläche **JSON-Vorlage herunterladen**. Verwenden Sie einen Editor Ihrer Wahl, um Ihrer Vorlage Konfigurationswerte hinzuzufügen. Kopieren Sie anschließend den aktualisierten JSON-Code, und fügen Sie ihn in die Eigenschaft **JSON-Editor** ein.

      - Sie können den JSON-Editor verwenden, um eine Sicherung Ihrer Konfiguration zu erstellen. Nachdem Sie die Einstellungen konfiguriert haben, sollten Sie dieses Feature verwenden, um die JSON-Einstellungen mit ihren Werten abzurufen. Kopieren Sie den JSON-Code, fügen Sie ihn in eine Datei ein, und speichern Sie ihn. Nun verfügen Sie über eine Sicherungsdatei.

    Alle Änderungen, die im Konfigurations-Designer vorgenommen werden, werden vom JSON-Editor automatisch übernommen. Ebenso werden alle im JSON-Editor vorgenommenen Änderungen automatisch vom Konfigurations-Designer übernommen. Wenn Ihre Eingabe ungültige Werte enthält, können Sie erst zwischen dem Konfigurations-Designer und dem JSON-Editor wechseln, nachdem Sie die Probleme behoben haben.

9. Wählen Sie **Weiter** aus.
10. Weisen Sie in **Bereichstags** (optional) ein Tag zu, um das Profil nach bestimmten IT-Gruppen wie `US-NC IT Team` oder `JohnGlenn_ITDepartment` zu filtern. Weitere Informationen zu Bereichstags finden Sie unter [Verwenden der RBAC und von Bereichstags für verteilte IT](../fundamentals/scope-tags.md).

    Wählen Sie **Weiter** aus.

11. Wählen Sie unter **Zuweisungen** die Benutzer oder Gruppen aus, denen Ihr Profil zugewiesen werden soll. Weisen Sie jedem Gerät ein Profil zu. Das OEMConfig-Modell unterstützt nur eine Richtlinie pro Gerät.

    Weitere Informationen zum Zuweisen von Profilen finden Sie unter [Zuweisen von Benutzer- und Geräteprofilen](device-profile-assign.md).

    Wählen Sie **Weiter** aus.

12. Überprüfen Sie die Einstellungen unter **Überprüfen + erstellen**. Wenn Sie auf **Erstellen** klicken, werden die Änderungen gespeichert, und das Profil wird zugewiesen. Die Richtlinie wird auch in der Profilliste angezeigt.

Wenn das Gerät das nächste Mal nach Konfigurationsupdates sucht, werden die von Ihnen konfigurierten OEM-spezifischen Einstellungen auf die OEMConfig-App angewendet.

> [!NOTE]
> Der OEMConfig-Standard umfasst derzeit keine Statusberichterstattung. Daher haben Profile standardmäßig den Status **Ausstehend**.

## <a name="supported-oemconfig-apps"></a>Unterstützte OEMConfig-Apps

Im Vergleich zu Standard-Apps erweitern OEMConfig-Apps die verwalteten Konfigurationsberechtigungen, die von Google gewährt werden, um komplexere Schemas zu unterstützen. Intune unterstützt derzeit die folgenden OEMConfig-Apps:

-----------------

| OEM | Paket-ID | OEM-Dokumentation (falls verfügbar) |
| --- | --- | ---|
| Samsung | com.samsung.android.knox.kpu | [Administratorhandbuch für das Knox Service Plugin](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| Zebra Technologies | com.zebra.oemconfig.common | [Übersicht zu OEMConfig für Zebra](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com.datalogic.oemconfig | [Benutzerdokumentation zu OEMConfig für Datalogic](https://datalogic.github.io/oemconfig/) |
| Honeywell | com.honeywell.oemconfig |  |
| Kyocera | jp.kyocera.enterprisedeviceconfig |  |
| Spectralink: Barcodes | com.spectralink.barcode.service |  |
| Spectralink: Schaltflächen | com.spectralink.buttons |  |
| Spectralink: Gerät | com.spectralink.slnkdevicesettings  |  |
| Spectralink: Protokollierung | com.spectralink.slnklogger |  |
| Spectralink: VQO | com.spectralink.slnkvqo |  |
| HMD Global | com.hmdglobal.app.oemconfig.ironman |  |

-----------------

Wenn es eine OEMConfig-Anwendung für Ihr Gerät gibt, diese aber nicht in der obigen Tabelle aufgeführt wird oder nicht in der Intune-Konsole angezeigt wird, senden Sie eine E-Mail an `IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> OEMConfig-Apps müssen von Intune integriert werden, bevor sie mit OEMConfig-Profilen konfiguriert werden können. Sobald eine App unterstützt wird, müssen Sie sich nicht mehr an Microsoft wenden, um sie in Ihrem Mandanten einzurichten. Befolgen Sie einfach die Anweisungen auf dieser Seite.

## <a name="next-steps"></a>Nächste Schritte

[Überwachen des Profilstatus](device-profile-monitor.md)
