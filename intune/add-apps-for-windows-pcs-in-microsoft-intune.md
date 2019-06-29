---
title: Hinzufügen von Apps für Windows-PCs, auf denen der Intune-Softwareclient ausgeführt wird
titleSuffix: Microsoft Intune
description: In diesem Thema erfahren Sie, wie Sie Apps für Windows-PCs zu Intune hinzufügen, bevor Sie sie bereitstellen.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/29/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: bc8c8be9-7f4f-4891-9224-55fc40703f0b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e24bd79fbceba1834d02af8512e5dd52676d471
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403300"
---
# <a name="add-apps-for-windows-pcs-that-run-the-intune-software-client"></a>Hinzufügen von Apps für Windows-PCs, auf denen der Intune-Softwareclient ausgeführt wird

[!INCLUDE [classic-portal](includes/classic-portal.md)]

In diesem Thema erfahren Sie, wie Sie Apps zu Intune hinzufügen, bevor Sie sie bereitstellen.

> [!IMPORTANT]
> Die Informationen in diesem Thema helfen Ihnen beim Hinzufügen von Apps für Windows-PCs, die Sie mithilfe des Intune-Softwareclients verwalten. Informationen zum Hinzufügen von Apps für registrierte Windows-Computer und andere mobile Geräte finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).

Damit Apps für PCs installiert werden können, müssen Sie automatisch ohne Benutzereingriff installiert werden können. Wenn dies nicht der Fall ist, schlägt die Installation fehl.

## <a name="additional-security-settings-for-windows-installer"></a>Zusätzliche Sicherheitseinstellungen für Windows Installer
Sie können Benutzern erlauben, App-Installationen zu steuern. Wenn diese Option aktiviert ist, werden Installationen, die normalerweise wegen Sicherheitsverstößen unterbrochen werden würden, weiterhin ausgeführt. Sie können festlegen, dass Windows Installer bei der Installation eines beliebigen Programms auf einem System erhöhte Berechtigungen verwendet. Zusätzlich können Sie festlegen, dass Windows Information Protection-Elemente (WIP) indiziert und die zugehörigen Metadaten an einem nicht verschlüsselten Speicherort gespeichert werden. Wenn die Richtlinie deaktiviert ist, werden WIP-geschützte Elemente nicht indiziert und sie werden nicht in den Ergebnissen in Cortana oder im Datei-Explorer angezeigt. Diese Funktionalität für diese Optionen ist standardmäßig deaktiviert. 

## <a name="add-the-app"></a>Hinzufügen der App
Mithilfe der folgenden Vorgehensweise verwenden Sie den Intune-Softwareherausgeber, um die Eigenschaften der App zu konfigurieren und sie in Ihren Cloudspeicher hochzuladen:

1. Wählen Sie in der [Microsoft Intune-Administratorkonsole](https://manage.microsoft.com) die Option **Apps** &gt; **Apps hinzufügen**, um den Intune-Softwareherausgeber zu starten.

   > [!TIP]
   > Möglicherweise müssen Sie Ihren Intune-Benutzernamen und das Kennwort eingeben, bevor der Softwareherausgeber gestartet wird.

2. Wählen Sie auf der Seite **Softwaresetup** des Herausgebers unter **Wählen Sie aus, wie diese Software für Geräte bereitgestellt werden soll** die Option **Softwareinstallationsprogramm** aus, und geben Sie dann Folgendes an:

   - **Wählen Sie den Dateityp des Softwareinstallationsprogramms aus**. Hiermit wird die Art der Software angegeben, die Sie bereitstellen möchten. Wählen Sie für einen Windows-PC **Windows Installer** aus.
   - **Geben Sie den Speicherort der Softwaresetupdateien an**. Geben Sie den Speicherort der Installationsdateien ein, oder wählen Sie **Durchsuchen** aus, um den Speicherort in einer Liste auszuwählen.
   - **Weitere Dateien und Unterordner aus dem gleichen Ordner einschließen**. Einige Programme, die Windows Installer verwenden, erfordern unterstützende Dateien. Diese müssen sich im selben Ordner wie die Installationsdatei befinden. Wählen Sie diese Option aus, wenn Sie auch diese unterstützenden Dateien bereitstellen möchten.

   Wenn Sie z. B. eine App namens „Application.msi“ für Intune veröffentlichen möchten, würde die Seite wie folgt aussehen: ![Seite „Softwaresetup“ des Herausgebers](media/publisher-for-pc.png).

   Bei diesem Installationstyp wird etwas Cloudspeicherplatz in Anspruch genommen.

3. Konfigurieren Sie auf der Seite **Softwarebeschreibung** Folgendes.

   > [!NOTE]
   > Je nach verwendeter Installationsdatei werden einige dieser Werte möglicherweise automatisch eingetragen, oder sie werden nicht angezeigt.

   - **Herausgeber**. Geben Sie den Namen des Herausgebers der App ein.
   - **Name**. Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt wird.<br />Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
   - **Beschreibung**. Geben Sie eine Beschreibung der App ein. Diese Beschreibung wird den Benutzern im Unternehmensportal angezeigt.
   - **URL für Softwareinformationen** (optional). Geben Sie die URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird den Benutzern im Unternehmensportal angezeigt.
   - **URL zu den Datenschutzbestimmungen** (optional). Geben Sie die URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird den Benutzern im Unternehmensportal angezeigt.
   - **Kategorie** (optional). Wählen Sie eine der integrierten App-Kategorien aus. Dadurch wird es für die Benutzer leichter, die App im Unternehmensportal zu finden.
   - **Symbol** (optional). Laden Sie ein Symbol hoch, das der App zugeordnet wird. Dies ist das Symbol, das gemeinsam mit der App angezeigt wird, wenn die Benutzer das Unternehmensportal durchsuchen.

4. Legen Sie auf der Seite **Anforderungen** die Anforderungen fest, die erfüllt sein müssen, bevor die App installiert werden kann. Es stehen die folgenden Optionen zur Auswahl:

   - **Architektur**. Wählen Sie aus, ob die App auf 32-Bit-Betriebssystemen, 64-Bit-Betriebssystemen oder auf beiden Betriebssystemarten installiert werden kann.
   - **Betriebssystem**. Wählen Sie die niedrigste Betriebssystemvariante aus, unter der die App installiert werden kann.

5. Auf der Seite **Erkennungsregeln** können Sie Regeln konfigurieren, um festzustellen, ob die zu konfigurierende App bereits auf einem PC installiert ist. Sie können auch die Standarderkennungsregeln verwenden, um alle zuvor installierten Versionen der App automatisch zu überschreiben. Diese Option gilt für Windows Installer (nur EXE-Dateien).

   Sie können folgende Regeln konfigurieren:
   - **Die Datei ist vorhanden**. Geben Sie den Pfad zu der Datei an, die Sie erkennen möchten. Sie können den PC unter **%ProgramFiles%** durchsuchen (dabei wird **Programme**\&lt;Pfad&gt; und **Programme (x86)** \&lt;Pfad&gt; durchsucht) oder unter **%SystemDrive%** (dabei wird das Stammlaufwerk des PCs durchsucht, in der Regel Laufwerk „C:“)
   - **Der MSI-Produktcode ist vorhanden**. Wählen Sie **Durchsuchen**, um die zu erkennende Windows Installer-Datei (MSI-Datei) auszuwählen.
   - <strong>Der Registrierungsschlüssel ist vorhanden</strong>. Geben Sie einen Registrierungsschlüssel an, der mit <strong>HKEY_LOCAL_MACHINE\</strong> beginnt. Es werden 32-Bit- und 64-Bit-Registrierungspfade durchsucht. Wenn der angegebene Schlüssel an einem der beiden Speicherorte vorhanden ist, ist die Erkennungsregel erfüllt.

   Wenn die App eine der konfigurierten Regeln erfüllt, wird sie nicht installiert.

6. Nur für den **Windows Installer**-Dateityp (MSI und EXE): Geben Sie auf der Seite **Befehlszeilenargumente** an, ob Sie optionale Befehlszeilenargumente für das Installationsprogramm angeben möchten.
   Die folgenden Parameter werden automatisch von Intune hinzugefügt:
   - Für EXE-Dateien wird **/install** hinzugefügt.
   - Für MSI-Dateien wird **/quiet** hinzugefügt.
   Beachten Sie, dass diese Optionen nur funktionieren, wenn der Ersteller des App-Pakets diese Funktion aktiviert hat.

7. Nur für den **Windows Installer**-Dateityp (nur EXE): Auf der Seite **Rückgabecodes** können Sie neue Fehlercodes eingeben, die von Intune interpretiert werden, wenn die App auf einem verwalteten Windows-PC installiert wird.

   Standardmäßig werden in Intune die branchenüblichen Rückgabecodes verwendet, um eine fehlerhafte oder erfolgreiche Installation eines Anwendungspakets zu melden: **0** (Erfolg) oder **3010** (Erfolg mit Neustart). Sie können der Liste auch Ihre eigenen Rückgabecodes hinzufügen. Wenn Sie eine Liste von Rückgabecodes angeben und bei der App-Installation ein in der Liste nicht enthaltener Code zurückgegeben wird, wird er als Fehler interpretiert.

8. Überprüfen Sie auf der Seite **Zusammenfassung** die von Ihnen angegebenen Informationen. Sobald Sie bereit sind, wählen Sie **Hochladen** aus.

9. Wählen Sie **Schließen**, um den Vorgang abzuschließen.

Die App wird im Arbeitsbereich **Apps** im Knoten **Apps** angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie eine App erstellt haben, umfasst der nächste Schritt die Bereitstellung. Weitere Informationen finden Sie unter [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md).

Wenn Sie weitere Informationen zu Tipps und Tricks zum Bereitstellen von Software auf Windows-PCs lesen möchten, lesen Sie den Blogbeitrag [Support Tip: Best Practices for Intune Software Distribution to PC’s (Tipp des Supports: Bewährte Methoden zur Intune-Softwareverteilung auf PCs)](https://support.microsoft.com/en-US/help/2583929).
