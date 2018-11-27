---
title: Verwalten von Softwarelizenzverträgen für PCs, auf denen der Intune-Softwareclient ausgeführt wird
titlesuffix: Microsoft Intune
description: Verwenden Sie Intune zum Verwalten von Lizenzvereinbarungen für Software, die im Rahmen von Microsoft-Volumenlizenzverträgen oder auf anderem Wege erworben wurde.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c59d8635-3f66-40f5-824a-a71c738e0341
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.openlocfilehash: f6559b10bb9e3c293a9719235d01d8c7b55ee62f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185388"
---
# <a name="manage-license-agreements-for-windows-pc-software-in-microsoft-intune"></a>Verwalten von Lizenzverträgen für Windows-PC-Software in Microsoft Intune

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Mit Microsoft Intune können Sie Lizenzvertragsinformationen für Software, die im Rahmen von Microsoft-Volumenlizenzverträgen gekauft wurde, hinzufügen und verwalten. Gleiches gilt für Microsoft- oder Nicht-Microsoft-Software, die auf anderem Wege erworben wurde. Diese Informationen lassen sich in logischen Gruppen organisieren.

> [!IMPORTANT]
> Die Funktion dient nur zum Komfort; es wird keine Genauigkeit garantiert. Sie sollten sich nicht darauf beziehen, um die Konformität von Microsoft-Volumenlizenzverträgen zu bestätigen. Die erfassten Daten werden nicht von Microsoft genutzt, um Verstöße gegen Lizenzverträge mit Microsoft bzw. um die Einhaltung solcher Verträge zu untersuchen.
>
> Lizenzen, die Sie zu Intune hinzufügen, wirken sich nicht auf Ihre Lizenzverträge oder auf die Nutzungsberechtigungen für Ihre Software aus. Wenn Sie beispielsweise ein Lizenzvertragsnummernpaar aus Intune löschen, werden keine Lizenzverträge zwischen Ihnen und Microsoft gelöscht oder annulliert.

Im Arbeitsbereich **Lizenzen** der Intune-Verwaltungskonsole können Sie folgende Aufgaben ausführen:

-   Hinzufügen und Bearbeiten von Microsoft-Volumenlizenzverträgen.

-   Hinzufügen und Bearbeiten anderer Softwarelizenzverträge.

-   Verwalten von Lizenzen und Gruppen.

-   Vergleichen der Berechtigungsinformationen, die von Intune aus dem Volume Licensing Service Center (VLSC) abgerufen werden, mit dem Bestand von Microsoft-Software, die von Intune auf den verwalteten Windows-PCs erkannt wird.

Darüber hinaus können Sie Berichte zur Zahl der Installationen und Lizenzen für Softwaretitel erstellen. Mit Lizenzberichten können Sie Ihren gesamten Lizenzierungsstand für Microsoft- und Nicht-Microsoft-Softwaretitel beurteilen.

> [!TIP]
> Der Arbeitsbereich **Lizenzen** wird erst dann in der Administratorkonsole angezeigt, wenn Sie mindestens einen Windows-PC mit dem Intune Windows PC-Client verwalten.

## <a name="add-microsoft-volume-licensing-agreements"></a>Hinzufügen von Microsoft-Volumenlizenzverträgen
In Intune-Volumenlizenzverträgen werden Lizenzinformationen für Software bereitgestellt, die über Microsoft-Volumenlizenzverträge erworben wurde. Sie können Intune Microsoft-Volumenlizenzverträge hinzufügen, indem Sie passende Paare von Vertragsnummern angeben. Die Vertrags- oder Autorisierungsnummern müssen der richtigen Lizenz- oder Registrierungsnummer zugeordnet werden. Vertragsnummernpaare erhalten Sie vom [Volume Licensing Service Center (VLSC)](http://go.microsoft.com/fwlink/?LinkID=223842), wenn Sie Lizenzverträge erwerben.

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://account.manage.microsoft.com/admin/default.aspx) die Option **Lizenzen** aus.

2.  Wählen Sie auf der Seite **Verträge hinzufügen** im Bereich **Vertragstyp auswählen**die Option **Volumenlizenzvertrag**aus.

3.  Geben Sie im Abschnitt **Vertragsdetails hinzufügen** an, ob Sie eine Datei hochladen oder die Details manuell hinzufügen möchten.

    -   **CSV-Datei mit Vertragsdetails hochladen**. Klicken Sie auf **Durchsuchen**, und wählen Sie dann die CSV-Datei aus, die Sie hochladen möchten.

        -   Die Datei kann entweder zwei oder drei Spalten enthalten; zwei nur für Vertragsnummernpaare oder drei, wenn Sie für jedes Vertragsnummernpaar einen Anzeigenamen hinzufügen möchten.

        -   Die Gesamtzahl der Zeichen in einem Vertragsnummernpaar darf 16 ASCII-Zeichen nicht überschreiten.

        -   Nur ASCII-Zeichen werden unterstützt.

        -   Folgende Zeichen sind im Vertragsnamen nicht zulässig: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Leerzeichen sind im Namen zulässig.

        -   Der Dateiname darf eine Länge von 128 Zeichen nicht überschreiten.

        -   Die Datei muss mindestens ein Vertragsnummernpaar und darf höchstens 5.000 Vertragsnummernpaare enthalten.

        **Format der Datei**

        Sie können diese Datei erstellen, indem Sie die Vertragsnummernpaare in ein Nur-Text-Dokument einfügen. Verwenden Sie dazu je nach Ihrem bei VLSC registrierten Organisationstyp eines der nachfolgend aufgeführten Formate. Geben Sie pro Zeile ein Vertragsnummernpaar an.

        -   **Open Value-Kunden:** *Vertragsnummer*, *Vertragsnummer wiederholen*, *Vertragsname*

        -   **Open-Kunden:** *Autorisierungsnummer*, *zugehörige Lizenznummer*, *Vertragsname*

        -   **Select- und Enterprise-Kunden:** *Vertragsnummer*, *zugehörige Registrierungsnummer*, *Vertragsname*

        Sie werden beim Hinzufügen eines neuen Vertrags von dem Formular **Verträge hinzufügen** aufgefordert, nach dieser Datei zu suchen.

        Dies ist ein Beispiel für den Inhalt einer CSV-Datei für einen Open Value-Kunden.

        `01-07001, 01-07001, Office agreements`

    -   **Vertragsdetails manuell hinzufügen**. Geben Sie die folgenden Informationen an, und geben Sie anschließend in den Feldern **Autorisierungs-/Vertragsnummer** und **Lizenz-/Registrierungs-/Kundennummer** die Vertragsnummernpaare ein. Klicken Sie nach Eingabe der beiden Nummern auf das Symbol **Paar hinzufügen**, um die Nummern zu speichern, und fügen Sie dann bei Bedarf ein neues Paar hinzu.

        -   **Vertragsname:** Geben Sie einen eindeutigen Namen für den Vertrag ein.

            Der Vertragsname darf höchstens 256 Zeichen umfassen. Folgende Zeichen sind nicht zulässig: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Leerzeichen sind im Namen zulässig.

        -   **Autorisierungs-/Vertragsnummer:** Geben Sie die Autorisierungs-/Vertragsnummer des Lizenzpaars ein.

        -   **Lizenz-/Registrierungs-/Kundennummer:** Geben Sie die Lizenz-/Registrierungs-/Kundennummer des Lizenzpaars ein.

        > [!NOTE]
        > Wenn Sie mehrere Vertragsnummernpaare hinzufügen, wird von Intune ein Vertrag mit dem Namen, den Sie angeben, erstellt, und alle Paare, die Sie hinzugefügt haben, werden Teil dieses Vertrags.

    Klicken Sie auf **+**, um ein weiteres Vertragsnummernpaar hinzuzufügen, bzw. auf **-**, um ein bereits eingegebenes Vertragsnummernpaar zu entfernen.

4.  Führen Sie im Bereich **Lizenzgruppe auswählen** einen der folgenden Schritte aus:

    -   **Die Verträge der Gruppe „Nicht zugewiesene Verträge“ hinzufügen**. Wählen Sie diese Option aus, wenn Sie die neuen Verträge zu keiner Lizenzgruppe hinzufügen möchten.

    -   **Die Verträge einer neuen Lizenzgruppe hinzufügen**. Geben Sie einen Namen für die neue Lizenzgruppe an.

    -   **Die Verträge einer vorhandenen Lizenzgruppe hinzufügen**. Wählen Sie in der Liste **Gruppenname** die Lizenzgruppe aus, der Sie die Verträge hinzufügen möchten.

5.  Wählen Sie **OK** aus.

Die Ansicht **Alle Verträge** wird angezeigt, und Intune stellt eine Verbindung mit dem Microsoft VLSC her, um die angegebenen Vertragsnummernpaare zu überprüfen.

Zum Aktualisieren der Volumenlizenzinformationen nach dem Hinzufügen von Lizenzverträgen in Intune klicken Sie auf der Seite **Übersicht über Lizenzen** auf **Jetzt aktualisieren**. Auf diese Weise werden die aktuellen Lizenzinformationen vom [Microsoft Volume Licensing Service Center (VLSC)](http://go.microsoft.com/fwlink/?LinkId=223842)abgerufen.

> [!IMPORTANT]
> Bis zur Aktualisierung der Volumenlizenzinformationen stimmen die Daten in der Vertragsliste möglicherweise nicht mit den Berechtigungsinformationen auf der Seite **Vertragsübersicht** überein

Nach dem Aktualisieren der Volumenlizenzinformationen können Sie die Lizenzinformationen mit Ihrer erkannten Microsoft-Software im Arbeitsbereich **Apps** vergleichen. Sie können zudem die folgenden Lizenzberichte ausführen:

-   **Lizenzkaufberichte:** Mit diesen Berichten können Sie die lizenzierte Software in ausgewählten Lizenzgruppen anzeigen, um Lücken in der Abdeckung zu ermitteln.

-   **Lizenzinstallationsberichte:** Anhand dieser Berichte lässt sich ermitteln, ob Sie über ausreichend Lizenzverträge verfügen.

> [!NOTE]
> Als **Produkttitel** wird für alle Microsoft-Volumenlizenzverträge **Nicht verfügbar**angezeigt.

## <a name="add-and-edit-other-software-licensing-agreements"></a>Hinzufügen und Bearbeiten anderer Softwarelizenzverträge
Außerdem können Sie zusätzlich zu Microsoft-Volumenlizenzverträgen weitere Typen von Lizenzverträgen zu Intune hinzufügen. Diese Verträge können sowohl Software einschließen, die nicht von Microsoft stammt, als auch Software, die von Microsoft stammt und über einen Händler erworben wurde.

> [!IMPORTANT]
> Es muss mindestens ein Windows-PC in Intune registriert sein, bevor Sie einen Vertrag hinzufügen können.  Zusätzlich muss auf mindestens einem registrierten Computer ein lizenzierbares Softwarepaket hochgeladen sein, das Sie zum Hinzufügen eines Lizenzvertrags verwenden möchten.

### <a name="to-add-other-software-agreements"></a>So fügen Sie andere Softwareverträge hinzu

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://account.manage.microsoft.com/admin/default.aspx) die Option **Lizenzen** aus.

2.  Wählen Sie im Bereich **Andere Softwarelizenzverträge** die Option **Verträge hinzufügen** aus.

3.  Wählen Sie auf der Seite **Verträge hinzufügen** im Bereich **Vertragstyp auswählen** die Option **Andere Softwarelizenzverträge** aus.

4.  Geben Sie im Bereich **Vertragsdetails hinzufügen** Folgendes an:

    -   **Agreement name** (erforderlich). Der Vertragsname darf höchstens 256 Zeichen umfassen. Folgende Zeichen sind nicht zulässig: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Leerzeichen sind im Namen zulässig.

    -   **Herausgeber** (erforderlich). Wenn Sie mit der Eingabe eines Herausgebers beginnen, werden die Namen aller Herausgeber abgerufen, die die eingegebenen Buchstaben enthalten. Wenn Sie beispielsweise "soft" eingeben, werden alle Herausgebernamen abgerufen, die die Zeichenfolge "soft" im Namen enthalten, z. B. "Microsoft" und "Microsoft Research". Die Herausgebernamen werden vom Software Asset-Katalog bezogen. Bevor Sie den Produkttitel eingeben, müssen Sie den Herausgeber auswählen.

        > [!IMPORTANT]
        > Das Unternehmen, das Sie hinzufügen möchten, wird möglicherweise nicht in dieser Liste angezeigt. Sie können nur Softwareverträge für Unternehmen hinzufügen, die bereits im Software Asset-Katalog vorhanden sind. Microsoft arbeitet jedoch kontinuierlich daran, die beliebtesten Softwaretitel hinzuzufügen. Wenn Sie eine Anforderung zum Hinzufügen eines Unternehmens zu dieser Liste absenden möchten, können Sie dies auf der [Intune Uservoice-Website](https://microsoftintune.uservoice.com/) durchführen.

    -   **Produkttitel** (erforderlich). Wenn Sie mit der Eingabe eines Produkttitels beginnen, werden die Titel aller Produkte abgerufen, die die eingegebenen Buchstaben enthalten. Bevor Sie einen **Produkttitel** angeben können, müssen Sie einen **Herausgeber**angeben.

    -   **Lizenzanzahl** (erforderlich). Geben Sie die Anzahl der erworbenen Lizenzen ein.

    -   **Startdatum der Lizenz**. Geben Sie das Startdatum der Lizenzdeckung ein.

    -   **Lizenzablaufdatum**. Geben Sie das Enddatum der Lizenzdeckung ein.

    -   **Vertragsdetails**. Sie können optional auch Kontaktinformationen, Registrierungsschlüssel und andere Informationen angeben.

5.  Führen Sie im Bereich **Lizenzgruppe auswählen** einen der folgenden Schritte aus:

    -   Wenn Sie die neuen Verträge keiner neuen oder vorhandenen Lizenzgruppe hinzufügen möchten, wählen Sie **Die Verträge der Gruppe "Nicht zugewiesene Verträge" hinzufügen** aus. Sie können die Verträge jederzeit zu benutzerdefinierten Lizenzgruppen hinzufügen.

    -   Wählen Sie **Die Verträge einer neuen Lizenzgruppe hinzufügen** aus, um die neuen Verträge einer neuen Lizenzgruppe hinzuzufügen. Sie werden aufgefordert, einen Namen für die neue Lizenzgruppe einzugeben.

    -   Wählen Sie **Die Verträge einer vorhandenen Lizenzgruppe hinzufügen** aus, um die neuen Verträge einer vorhandenen Lizenzgruppe hinzuzufügen Wählen Sie in der Liste **Gruppenname** die Lizenzgruppe aus, der Sie die Verträge hinzufügen möchten.

6.  Wählen Sie **OK** aus.

Die Listenansicht **Alle Verträge** wird angezeigt.

## <a name="manage-license-agreements"></a>Verwalten von Lizenzverträgen
Softwarelizenzverträge können zu Lizenzgruppen hinzugefügt werden. Sie können Lizenzgruppen verwenden, um Ihre Lizenzverträge in Einheiten zu organisieren, die für Ihre Organisation logisch sind. Darüber hinaus können Sie Lizenzverträge löschen, die Sie zuvor erstellt haben.


|                            |                                                                                                                                                                                                                                                                                                                                                                          |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Aufgabe            |                                                                                                                                                                                 Details                                                                                                                                                                                  |
|   Erstellen einer Lizenzgruppe   |                                                            Wählen Sie auf der Seite <strong>Übersicht</strong> des Arbeitsbereichs <strong>Lizenzen</strong> im Menü <strong>Aufgaben</strong> die Option <strong>Lizenzgruppe erstellen</strong> aus. <strong>Hinweis:</strong> Sie können insgesamt bis zu 500 Lizenzgruppen erstellen.                                                             |
|   Umbenennen einer Lizenzgruppe   |                                                                                                      Wählen Sie im Arbeitsbereich <strong>Lizenzen</strong> eine Lizenzgruppe aus, und klicken Sie anschließend im Menü <strong>Aufgaben</strong> auf die Option <strong>Lizenzgruppe bearbeiten</strong>.                                                                                                       |
|   Löschen einer Lizenzgruppe   |                                 Wählen Sie im Arbeitsbereich <strong>Lizenzen</strong> eine Lizenzgruppe aus, und klicken Sie anschließend im Menü <strong>Aufgaben</strong> auf die Option <strong>Lizenzgruppe löschen</strong>. <strong>Tipp:</strong> Alle Lizenzen in der Gruppe mit zu löschenden Lizenzen werden in die Lizenzgruppe <strong>Nicht zugewiesene Verträge</strong> verschoben.                                 |
| Löschen von Lizenzverträgen | Wählen Sie im Arbeitsbereich <strong>Lizenzen</strong> einen Vertrag aus, und klicken Sie auf <strong>Löschen</strong>. <strong>Tipp:</strong> Klicken Sie nach dem Löschen von Volumenlizenzverträgen zum Aktualisieren der Lizenzinformationen auf der Seite <strong>Übersicht über Lizenzen</strong> oder auf der Registerkarte <strong>Allgemein</strong> für eine bestimmte Lizenzgruppe auf <strong>Jetzt aktualisieren</strong>. |

