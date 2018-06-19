---
title: Einblicke in Vorgänge durch Berichte
description: Erstellen und verwalten Sie Berichte zu Software, Hardware und Softwarelizenzen in Ihrem Unternehmen.
keywords: ''
author: dougeby
ms.author: angrobe
manager: angrobe
ms.date: 04/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 857309c2-61c9-4c22-becf-4839fedeaece
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: pbala
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b49f9d94e800a068015a357aaf105a92bb5882cc
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31023681"
---
# <a name="understand-microsoft-intune-operations-by-using-reports"></a>Einblicke in Microsoft Intune-Vorgänge durch Berichte

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Anhand der Informationen in diesem Thema können Sie Microsoft Intune-Berichte mit Informationen zu Software, Hardware sowie zu Softwarelizenzen in Ihrer Organisation erstellen und verwalten.

## <a name="using-reports"></a>Verwenden von Berichten
In den Intune-Berichten finden Sie Informationen zu Software, Hardware und Softwarelizenzen in Ihrem Unternehmen. Mithilfe von Berichten können Sie sich über den aktuellen Stand und den zukünftigen Bedarf informieren. Im Arbeitsbereich **Berichte** finden Sie Tools zum Erstellen und Verwalten von Berichten. 

## <a name="report-types"></a>Berichtstypen

|Berichtstyp|Beschreibung|
|---------------|---------------|
|**Updateberichte**|Zeigen die Softwareupdates, die auf Computern in Ihrer Organisation erfolgreich ausgeführt wurden. Es werden auch die Updates angezeigt, die fehlgeschlagen sind, ausstehend sind oder benötigt werden. Weitere Informationen zu Softwareupdates finden Sie unter [Aktualisieren Ihrer Windows-PCs mit Softwareupdates in Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).|
|**Berichte zu ermittelter Software**|Zeigen die Software an, die auf Computern in Ihrer Organisation installiert sind. Softwareversionen sind enthalten. Sie können die angezeigten Informationen nach Herausgeber und Kategorie der Software filtern. Durch Auswahl des Richtungspfeils neben dem Listenelement können Sie die Updates in der Liste erweitern, um weitere Details anzuzeigen (zum Beispiel die Computer, auf denen ein Update installiert ist).<br /><br />Wenn Sie Computer zurückziehen oder deren Gruppenmitgliedschaft in Intune ändern, kann es einige Minuten dauern, bis die Änderungen im Bericht zu ermittelter Software berücksichtigt werden. Um möglichst präzise Softwareinventardaten zu erhalten, warten Sie nach dem Abkoppeln von Computern oder Ändern ihrer Gruppenmitgliedschaft einige Minuten, bevor Sie einen Bericht über erkannte Software ausführen, der diese Computer enthält.|
|**Computerinventurberichte**|Hierin werden Informationen zu verwalteten Computern in Ihrer Organisation angezeigt. Mithilfe dieses Berichts können Sie den Erwerb von Hardware planen und den Hardwarebedarf der Benutzer in Ihrer Organisation besser nachvollziehen. Weitere Informationen zum Arbeiten mit verwalteten Computern finden Sie unter [Verwalten von Windows-PCs mit Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md).|
|**Inventurberichte für mobile Geräte**|Hierin werden Informationen zu den mobilen Geräten in Ihrer Organisation angezeigt. Sie können die angezeigten Informationen nach Gruppen, entfernten Nutzungsbeschränkungen und Betriebssystem filtern.|
|**Lizenzkaufberichte**|Hierin werden die Softwaretitel jeder lizenzierten Software in ausgewählten Lizenzgruppen auf Basis ihrer Lizenzverträge angezeigt. Wenn die Softwarelizenzinformationen seit mehr als 24 Stunden nicht aktualisiert wurden, werden sie beim Erstellen eines Lizenzberichts aktualisiert. Ein Lizenzbericht stellt keine genaue Berechnung von verwendeten Softwaretiteln und keinen Nachweis der Erfüllung von Verträgen dar. Der Bericht ist ein Tool, das Ihnen dabei hilft, Lizenzierungsentscheidungen für Ihre Organisation zu treffen. Von Intune werden möglicherweise nicht alle Produkte erkannt, für die Microsoft-Volumenlizenzen verfügbar sind. Folgende Filter sind verfügbar:<br /><br />**Alle Verträge** zeigt alle lizenzierten Softwareprodukte an, die mit Intune verwaltet werden.<br /><br />**Volumenlizenzverträge** zeigt nur VLSC-Softwareprodukte (Volume Licensing Service Center) an.<br /><br />**Andere Softwarelizenzverträge** zeigt Softwareprodukte an, die außerhalb des VLSC verwaltet werden.|
|**Lizenzinstallationsberichte**|Vergleichen von der Software, die auf Computern in Ihrer Organisation installiert ist, mit Ihrer aktuellen Lizenzvertragsabdeckung, laut des VLSC. Zu den Filtern gehören:<br /><br />**Alle Verträge** zeigt alle lizenzierten Softwareprodukte an, die mit Intune verwaltet werden.<br /><br />**Volumenlizenzverträge** zeigt nur VLSC-Softwareprodukte an.<br /><br />**Andere Softwarelizenzverträge** zeigt Softwareprodukte an, die außerhalb des VLSC verwaltet werden.|
|**Berichte zu Nutzungsbedingungen**|Zeigt an, ob die Benutzer die von Ihnen bereitgestellten Nutzungsbedingungen akzeptiert haben und welche Version sie akzeptiert haben. Sie können die Annahme beliebiger Nutzungsbedingungen anzeigen, die für bis zu 10 Benutzer angegeben wurden oder den Annahmestatus für eine bestimmte Bedingung anzeigen.|
|**Berichte über nicht richtlinienkonforme Apps**|Es werden Informationen zu den Benutzern mit installierten Apps angezeigt, die in Ihren Listen der konformen und nicht konformen Apps enthalten sind. Verwenden Sie diesen Bericht, um Benutzer und Geräte zu ermitteln, die nicht mit Ihren Unternehmens-App-Richtlinien konform sind.|
|**Berichte zur Zertifikatkompatibilität**|Zeigt an, welche Zertifikate für Benutzer und Geräte über SCEP oder PKCS #12 (.PFX) ausgestellt wurden. Verwenden Sie diesen Bericht, um ausgestellte, abgelaufene und gesperrte Zertifikate zu suchen.|
|**Geräteverlaufsberichte**|Zeigt ein Verlaufsprotokoll von Abkoppeln-, Zurücksetzen- und Löschen-Aktionen an. Verwenden Sie diesen Bericht, um zu ermitteln, welcher Benutzer in der Vergangenheit Aktionen auf Geräten initiiert hat.|
|**Integritätsnachweisberichte**|Zeigt die Integrität von mobilen Geräten an.|
|**Mac OS X-Hardwarebericht**|Hier werden Hardwaredetails zu allen registrierten Mac OS X-Geräten in den von Ihnen ausgewählten Gruppen angezeigt. Informationen zu dem von diesen Geräten erfassten Hardwareinventar finden Sie unter [Verstehen Sie Ihre Geräte mithilfe des Inventars in Microsoft Intune](understand-your-devices-with-inventory-in-microsoft-intune.md).|
|**Mac OS X-Softwarebericht**|Hierin wird die auf allen Mac OS X-Geräten in den von Ihnen ausgewählten Gruppen installierte Software angezeigt. Im Bericht werden der Softwarename (als Paket-ID), die Kurzversion des Namens (oder der Anzeigename), die Version und die Anzahl von Geräten, auf denen die Software installiert ist, aufgeführt.|
|**WIP-Berichte (Windows Information Protection)**|Zeigt Informationen zu WIP-Vorgängen (Windows Information Protection) auf Geräten an, die Sie verwalten.|
|**Integritätsnachweisberichte**|Zeigt Informationen an, die vom Windows Health Attestation-Dienst für die von Ihnen verwalteten Geräte gemeldet werden.|

## <a name="to-create-a-report"></a>So erstellen Sie einen Bericht

1.  Wählen Sie in der Intune-Verwaltungskonsole **Berichte** aus. Wählen Sie anschließend den Berichtstyp aus, den Sie wie in der vorangegangenen Tabelle beschrieben generieren möchten.

2.  Übernehmen Sie auf der Seite **Neuen Bericht erstellen** die Vorgaben, oder passen Sie sie an, um die im Bericht zurückgegebenen Ergebnisse zu filtern. Sie können beispielsweise auswählen, dass nur von Microsoft herausgegebene Software im Bericht über erkannte Software angezeigt werden soll.

3.  Wählen Sie **Bericht anzeigen** aus, um den Bericht in einem neuen Fenster zu öffnen.

Sie können den Bericht nach jeder Spalte sortieren, indem Sie die entsprechende Spaltenüberschrift auswählen. Zusätzlich können Sie bei einigen Berichten Listenelemente erweitern, um mehr Details anzeigen zu lassen.

## <a name="more-report-actions"></a>Weitere Berichtsaktionen
Zusätzlich werden von Berichten die folgenden Aktionen unterstützt:

|Aktion|Weitere Informationen|
|----------|--------------------|
|**Drucken**|Wählen Sie in einem geöffneten Bericht das Drucken-Symbol aus, und folgen Sie den Anweisungen.|
|**Exportierenieren**|Klicken Sie in einem geöffneten Bericht auf das Exportieren-Symbol, und folgen Sie den Anweisungen. Sie können einen Bericht im CSV- (durch Trennzeichen getrennte Werte) oder HTML-Format exportieren.|
|**Speichern**|Auf der Seite **Neuen Bericht erstellen** können von jedem Benutzer bis zu 100 Berichte gespeichert werden. Konfigurieren Sie die Berichtsparameter wie gewünscht, und wählen Sie anschließend **Speichern**oder auf **Speichern unter** aus, wenn Sie einen anderen Namen verwenden möchten.|
|**Laden**|Wählen Sie auf der Seite **Neuen Bericht erstellen** **Laden** aus, um zuvor gespeicherte Sätze von Berichtsparametern abzurufen.|
|**Löschen**|Wählen Sie im Arbeitsbereich **Berichte** den gewünschten Berichtstyp aus, und wählen Sie anschließend **Laden** aus. Wählen Sie anschließend in der Liste der Berichte das Löschsymbol (x) neben dem Bericht aus.|


