---
title: Benachrichtigungen durch Warnungen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit Warnungen über Ereignisse in Microsoft Intune auf dem Laufenden bleiben.
keywords: ''
author: nathbarn
ms.author: dougeby
manager: dougeby
ms.date: 8/31/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 396ea714 0433 4bd5 a934 8d0b477f28e4
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune classic
ms.openlocfilehash: 35b47dbc789e7f2ea2b200b8c22ff3bae6152f40
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
#  <a name="use-alerts-to-get-notified-by-microsoft-intune"></a>Verwenden von Warnungen, um Benachrichtigungen durch Microsoft Intune zu erhalten

[!INCLUDE [classic portal](../includes/classic-portal.md)]

Warnungen halten Sie über Ereignisse in Microsoft Intune auf dem Laufenden. Warnungen können Sie z. B. bei den folgenden Ereignissen benachrichtigen:
- Ein Problem mit dem Exchange-Connector beeinflusst die Verwaltung mobiler Geräte.
- Auf einem Computer wurde Malware gefunden.
- Ein Konflikt zwischen zwei Intune-Richtlinien wurde erkannt.
- Bei der Bereitstellung eines Intune-Softwareclients tritt ein Fehler auf.

## <a name="how-alerts-work"></a>Funktionsweise von Warnungen

Warnungen werden auf der Grundlage von **Warnungstypen**generiert, einem Satz von vorkonfigurierten, in Intune integrierten Regeln. Der Warnungstyp **Im Cloudspeicher ist nur noch weniger als 10 % freier Speicherplatz vorhanden** warnt Sie beispielsweise, wenn der Speicherplatz zum Speichern von Apps in der Cloud zu Neige geht. Sie können jeden Warnungstyp aktivieren oder deaktivieren und die Eigenschaften konfigurieren. Wenn Sie den oben genannten Warnungstyp verwenden, können Sie z. B. folgende Eigenschaften konfigurieren:

- **Status:** Legt fest, ob der Warnungstyp aktiviert oder deaktiviert ist.
- **Schweregrad:** Wie schwerwiegend ist diese Warnung?

|Schweregrad|Details|
|--|---|
|**Kritische Warnung**|Weist auf ein schwerwiegendes Problem hin, das Sie so bald wie möglich untersuchen sollten, z.B. wenn Schadsoftware auf einem Computer erkannt wurde.|
|**Warnung**|Weist auf ein Problem hin, das aktuell nicht kritisch ist, aber möglicherweise ernsthaft werden kann, wenn Sie sich nicht darum kümmern, z.B. wenn Sicherheitsupdates zum Installieren vorhanden sind.|
|**Informationsmeldung**|Weist auf Informationen hin, die für den Betrieb unkritisch sind, z. B., wenn eine neue Version von Exchange Connector verfügbar ist.|

Andere Warnungstypen können verschiedene konfigurierbare Elemente enthalten, z.B. den Prozentsatz der Geräte, die durch ein Problem betroffen sein müssen, bevor eine Warnung generiert wird.

**Wenn die Kriterien eines Warnungstyps erfüllt sind, wird eine Warnung generiert und in der Intune-Verwaltungskonsole angezeigt.**

Darüber hinaus können Sie Intune so konfigurieren, dass Sie per E-Mail benachrichtigt werden, wenn eine Warnung generiert wird.

## <a name="set-up-alerts"></a>Einrichten von Warnungen

Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Verwaltung** &gt; **Warnungen und Benachrichtigungen** aus, und wählen Sie anschließend eine der folgenden Aufgaben aus:

|Aufgabe|Beschreibung|
|---|------|
|**Warnungstypen**|Wählen Sie den Warnungstyp aus, den Sie konfigurieren möchten, und führen Sie anschließend eine der folgenden Aktionen aus:<br /><br />Wählen Sie **Konfigurieren** aus. Konfigurieren Sie im Dialogfeld **Warnungstyp konfigurieren** die gewünschten Einstellungen, und wählen Sie anschließend **OK** aus.<br /><br />**Aktivieren** oder **deaktivieren** Sie die Warnung.<br /><br />Erweitern Sie den Knoten **Warnungstypen**, und wählen Sie eine Kategorie aus, um nur die Warnungstypen dieser Kategorie anzuzeigen.|
|**Empfänger**|Wählen Sie **Hinzufügen** aus, um eine neue E-Mail-Adresse hinzuzufügen, an die die eingerichteten E-Mail-Benachrichtigungen gesendet werden sollen.<br /><br />Sie können auch vorhandene Empfänger **bearbeiten** oder **löschen** .<br /><br />Um Benachrichtigungen zu erhalten, müssen Sie diese E-Mail-Adresse zudem als Empfänger unter **Benachrichtigungsregeln** hinzufügen.|
|**Benachrichtigungsregeln**|Konfiguriert Regeln, die definieren, an wen eine E-Mail-Warnung gesendet wird. Sie können entweder:<br /><br />**Eine vorhandene Regel auswählen**: Wählen Sie eine Regel aus, und wählen Sie anschließend **Empfänger auswählen** aus. Dann können Sie alle Empfänger auswählen, an die eine E-Mail gesendet werden soll, wenn eine Warnung generiert wird, die diese Regel erfüllt.<br /><br />**Eine neue Regel erstellen**: Geben Sie einen Namen für die Regel ein, und wählen Sie dann die für die Regel geltenden Warnungskategorien und den Schweregrad aus. Wählen Sie die Benutzer aus, die eine E-Mail erhalten, wenn eine Warnung generiert wird.<br /><br />Sie können auch eine vorhandene Regel **aktivieren**, **deaktivieren**, **bearbeiten**oder **löschen** .|

## <a name="working-with-alerts"></a>Arbeiten mit Warnungen

Um in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) Warnungen anzuzeigen, wählen Sie **Warnungen** und anschließend die Art der anzuzeigenden Warnung aus.

Die folgenden Optionen erleichtern die Arbeit mit Warnungen in der die Intune-Verwaltungskonsole.

|Option|Beschreibung|
|-----|----|
|**Anzeigen aktiver Warnungen**|Wählen Sie eine der folgenden:<br /><br />**Warnungszusammenfassung anzeigen**: Im Arbeitsbereich **Dashboard** werden die wichtigsten Fehler im Bereich „Warnungen“ angezeigt. Wählen Sie den Bereich aus, um ausführlichere Informationen anzuzeigen:<br /><br />Darüber hinaus können Sie eine Warnungszusammenfassung auf der Seite **Übersicht** im Arbeitsbereich **Warnungen** anzeigen.<br /><br />**Alle Warnungen anzeigen**: Wählen Sie im Arbeitsbereich **Warnungen** die Option **Alle Warnungen** aus.|
|**Anzeigen von Benachrichtigungen**|Wählen Sie eine der folgenden:<br /><br />Wählen Sie im Arbeitsbereich **Dashboard** die Option **Benachrichtigungen** aus.<br /><br />Wählen Sie im Arbeitsbereich **Warnungen** die Optionen **Alle Warnungen** &gt; **Benachrichtigungen** aus.|
|**Schließen einer Warnung**|Wählen Sie in der Liste der Warnungen die Warnung aus, die Sie schließen möchten, und wählen Sie anschließend **Warnung schließen** aus.<br /><br />Geschlossene Warnungen werden nach 90 Tagen dauerhaft gelöscht.|
|**Erneutes Aktivieren einer geschlossenen Warnung**|Legen Sie in der Liste der Warnungen die Dropdownliste **Filter** auf **Geschlossen** fest.<br /><br />Wählen Sie in der Liste geschlossener Warnungen die Warnung aus, die Sie erneut aktivieren möchten, und wählen Sie anschließend **Warnung erneut aktivieren** aus.|

Intune-Warnungen bleiben 30 Tage lang aktiv, oder bis Folgendes eintritt:

- Das Problem, das die Warnung verursacht hat, wurde behoben.
- Die Warnung wird manuell geschlossen.

Geschlossene Warnungen können bis 30 Tage nach der Schließung erneut aktiviert werden. Nach 30 Tagen werden geschlossene und inaktive Warnungen aus Intune entfernt.

> [!TIP]
> Wenn dieselbe Warnung von Geräten mit verschiedenen Betriebssystemen generiert wird, werden möglicherweise mehrere Versionen der gleichen Warnung in der Warnungsliste angezeigt.
