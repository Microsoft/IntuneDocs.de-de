---
title: Konfigurieren der Unternehmensportal-App
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie unternehmensspezifisches Branding auf die Intune-Unternehmensportal-App anwenden können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c61eb47f29b201997d04fa6b1405ad2f186e4fcc
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57237188"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Konfigurieren der Microsoft Intune-Unternehmensportal-App

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Im Microsoft Intune-Unternehmensportal können Benutzer auf Unternehmensdaten zugreifen, häufige Aufgaben wie das Registrieren von Geräten und das Installieren von Apps ausführen und sich über Unterstützungsmöglichkeiten durch Ihre IT-Abteilung informieren.        

> [!Tip]        
> Wenn Sie das Unternehmensportal anpassen, gelten die Konfigurationen sowohl für die Unternehmensportal-Website als auch für die Unternehmensportal-Apps. Beachten Sie, dass Benutzern eine Intune-Lizenz zugewiesen werden muss, damit sie auf die Unternehmensportalwebsite zugreifen können.

Durch Anpassen des Unternehmensportals können Sie Ihren Endbenutzern eine vertraute und sinnvolle Benutzeroberfläche bereitstellen. Klicken Sie hierzu in der Workload **Client-Apps** auf **Setup** > **Branding des Unternehmensportals**, und konfigurieren Sie die erforderlichen Einstellungen.  

> [!Note]       
> Wenn Sie Azure Government verwenden, werden dem Endbenutzer App-Protokolle angeboten. Er kann nun entscheiden, wie er diese teilen möchte, wenn der er den Prozess zum Abrufen von Hilfe zu einem Problem startet. Wird Azure Government jedoch nicht verwendet, sendet das Unternehmensportal für Windows 10 App-Protokolle direkt an Microsoft, wenn der Benutzer den Prozess zum Abrufen von Hilfe zu einem Problem startet. Das Senden der App-Protokolle an Microsoft erleichtert die Problembehandlung und -behebung. 

## <a name="company-information-and-privacy-statement"></a>Unternehmensinformationen und Datenschutzerklärung        
Der Unternehmensname wird als Titel des Unternehmensportals angezeigt. Die Datenschutzerklärung wird angezeigt, wenn ein Benutzer auf den Datenschutzlink klickt.

Mit einem Sternchen (*) gekennzeichnete Felder sind obligatorisch.       


| Feldname | Max. Länge | Weitere Informationen |
|---|---|---|
|**Firmenname**| 40 | Der Name wird als Titel des Unternehmensportals und auf der Intune-Benutzeroberfläche als Text angezeigt. |
| **URL der Datenschutzerklärung** |     79     | Sie können eine eigene Datenschutzerklärung für Ihr Unternehmen angeben. Diese wird angezeigt, wenn die Benutzer im Unternehmensportal auf die Datenschutzlinks klicken. Sie müssen eine gültige URL im Format `<https://www.contoso.com>` eingeben. |

## <a name="support-information"></a>Supportinformationen      
Geben Sie die Supportinformationen Ihres Unternehmens ein, um Ihrem Mitarbeiter einen Kontakt für auf Intune bezogene Fragen bereitzustellen.          

|Feldname|Max. Länge|Weitere Informationen|
|---|---|---|
|**Kontaktname** | 40 | Dieser Name wird auf der Seite **An IT-Abteilung wenden** angezeigt. |
|**Telefonnummer** | 20 | Diese Kontaktnummer wird auf der Seite **An IT-Abteilung wenden** angezeigt, damit sich Mitarbeiter an Sie wenden können, wenn Sie Unterstützung benötigen. |
|**E-Mail-Adresse**| 40 | Diese Kontaktadresse wird auf der Seite **An IT-Abteilung** wenden angezeigt. Sie müssen eine gültige E-Mail-Adresse im Format `alias@domainname.com` eingeben. |
|**Name der Website**| 40 | Dies ist der Anzeigename der URL für die Supportwebsite. Wenn Sie für die Supportwebsite eine URL, aber keinen Anzeigenamen angeben, wird im Unternehmensportal auf der Seite **An IT-Abteilung wenden** der Text „Zur IT-Website wechseln“ angezeigt. |
|**Website-URL**| 150 | Wenn Sie über eine Supportwebsite verfügen, die Ihre Benutzer verwenden sollen, geben Sie hier die URL an. Die URL muss das Format `https://www.contoso.com` aufweisen. Wenn Sie keine URL angeben, wird im Unternehmensportal auf der Seite **An IT-Abteilung wenden** keine Supportwebsite angezeigt. |
| **Weitere Informationen**| 120 | Dies wird auf der Seite **An IT-Abteilung wenden** angezeigt. |


## <a name="company-identity-branding-customization"></a>Anpassen der Unternehmensmarkenidentität      
Sie können Ihr Unternehmensportal mit Ihrem Firmenlogo, Firmennamen, Farbdesign und Hintergrund anpassen.     

### <a name="theme-color-and-logo-in-the-company-portal"></a>Farbdesign und Logo im Unternehmensportal
Wenden Sie ein Farbdesign auf das Unternehmensportal an. Wählen Sie eine Standardfarbe aus, oder geben Sie einen sechsstelligen Hexadezimalcode ein, um eine benutzerdefinierte Farbe festzulegen.

|Feldname|Weitere Informationen|
|---|---|
|**Select a standard color or enter a six-digit hex code** (Standardfarbe auswählen oder sechsstelligen Hexadezimalcode eingeben)| Wählen Sie **Standard** aus, um eine angezeigte Farbe auszuwählen. Wählen Sie **Benutzerdefiniert** aus, um eine bestimmte Farbe anhand eines Hexadezimalcodes auszuwählen.|
|**Choose theme color** (Farbdesign auswählen)| Wählen Sie ein Farbdesign aus, das auf das Unternehmensportal angewendet werden soll. Sie können aus einer Standardfarbe auswählen oder einen bestimmten Hexadezimalcode angeben. |
|**Anzeige**| Wählen Sie aus, ob **Unternehmenslogo und -name**, **nur das Unternehmenslogo** oder **nur der Unternehmensname** angezeigt werden soll. |
|**Upload your company logo** (Firmenlogo hochladen)|Sie können Ihr Unternehmenslogo hochladen, damit es im Unternehmensportal angezeigt wird. Beachten Sie, dass die Textfarbe automatisch auf die Option mit dem höchsten Kontrast festgelegt wird. Für die optimale Darstellung laden Sie ein Logo mit transparentem Hintergrund hoch.<p><ul><li>Maximale Bildgröße: 400 x 400 px</li><li>Maximale Dateigröße: 750 KB</li><li>Dateityp: PNG, JPG oder JPEG</li></ul>|

Nachdem Sie das Logo hochgeladen haben, wird das Logo mit dem Farbdesign im Vorschaubereich angezeigt. Wenn Sie den Unternehmensnamen anzeigen möchten, wird dieser in schwarz oder weiß im Unternehmensportal angezeigt. Die Farbe wird anhand des höchsten Kontrasts zur Designfarbe automatisch ausgewählt. Der Unternehmensname wird nicht im Vorschaubereich angezeigt. 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>Logo für die Verwendung auf weißen oder hellen Hintergründen
Wählen Sie ein Logo aus, das auf weißen oder hellen Hintergründen am besten aussieht.

|Feldname|Weitere Informationen|
|---|---|
|**Upload your logo** (Logo hochladen)| Diese Option ist verfügbar, wenn Sie ausgewählt haben, dass das Firmenlogo angezeigt werden soll. Für die optimale Darstellung laden Sie ein Logo mit transparentem Hintergrund hoch.<p><ul><li>Maximale Bildgröße: 400 x 400 px</li><li>Maximale Dateigröße: 750 KB</li><li>Dateityp: PNG, JPG oder JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>Markenbild für das Unternehmensportal

Zeigen Sie ein Markenbild an, das Ihre Unternehmensmarke widerspiegelt. Nachdem Sie Ihre Änderungen gespeichert haben, können Sie im Intune-Webportal im oberen Bereich des Blatts auf **Preview your settings** (Vorschau Ihrer Einstellungen) klicken, um Ihre Konfiguration zu überprüfen. Beachten Sie, dass Sie das Markenbild nur auf einem iOS-Gerät in der Vorschau anzeigen können und nicht im Intune-Webportal. 

|Feldname|Weitere Informationen|
|---|---|
|**Upload your brand image** (Markenbild hochladen)| Mit dieser Option können Sie ein Hintergrundbild auf der Benutzerprofilseite in der Unternehmensportal-App anzeigen.<p>*Hinweis*: Das Bild wird auf verschiedenen Plattformen möglicherweise unterschiedlich dargestellt.<p><ul><li>Empfohlene Bildbreite: Weniger als 1125 px, aber nicht weniger als 640 px</li><li>Maximale Bildgröße: 1,3 MB</li><li>Dateityp: PNG, JPG oder JPEG</li></ul>|

Mit einem richtigen Markenbild kann das Vertrauen von Benutzern in das Unternehmensportal gesteigert werden, indem die Identität des Unternehmens aussagekräftig dargestellt wird. Im Folgenden finden Sie einige Tipps, die Sie beim Erwerben, Auswählen und Optimieren des Bilds für das Unternehmensportal beachten sollten. 

- Wenden Sie sich an Ihre Marketing- oder Designabteilung. Möglicherweise verfügt sie bereits über zulässige Markenbilder. Eventuell können sie Sie bei Bedarf auch beim Optimieren der Bilder unterstützen. 

- Beachten Sie die Komposition sowohl im Querformat als auch im Hochformat. Das Bild sollte ausreichend Hintergrundfläche um den Fokus herum aufweisen. Das Bild wird möglicherweise je nach Größe, Ausrichtung und Plattform des Geräts anders zugeschnitten. 

- Vermeiden Sie typische Archivbilder. Das Bild sollte die Marke Ihres Unternehmens widerspiegeln und für Benutzer vertraut wirken. Wenn Sie keines besitzen, ist es besser, keines zu verwenden, anstatt ein allgemeines Bild zu nutzen, das keine Bedeutung für Ihre Benutzer hat. 

- Entfernen Sie unnötige Metadaten. Bilddateien können Metadaten enthalten, z.B. das Kameraprofil, der geografische Standort, Titel, Beschreibung usw. Verwenden Sie ein Bildbearbeitungstool, um diese Informationen zu entfernen, die Qualität beizubehalten und die maximale Dateigröße einzuhalten. 

Nachdem ein Markenbild in Intune hinzugefügt oder geändert wurde, wird dem Endbenutzer auf iOS-Geräten möglicherweise erst eine Änderung angezeigt, wenn das Unternehmensportal die Änderung beim Start erkannt hat und zur Anzeige des Markenbilds neu gestartet wurde. 

### <a name="brand-image-examples"></a>Beispiele für Markenbilder

Die folgende Abbildung zeigt ein iPad-Beispielmarkenbild:

![Screenshot eines iPhone-Beispielmarkenbilds](media/company-portal-app/company-portal-app-03.png)

Die folgende Abbildung zeigt ein iPhone-Beispielmarkenbild:

![Screenshot eines iPad-Beispielmarkenbilds](media/company-portal-app/company-portal-app-02.png)

## <a name="windows-company-portal-keyboard-shortcuts"></a>Tastenkombinationen für die Windows-Unternehmensportal-App

Endbenutzer können mithilfe von Tastenkombinationen (Tastenkombinations-Editor) Navigations-, App- und Geräteaktionen in der Windows-Unternehmensportal-App auslösen.

Die folgenden Tastenkombinationen stehen Ihnen in der Windows-Unternehmensportal-App zur Verfügung.

| Bereich | Beschreibung | Tastenkombination |
|:------------------:|:--------------:|:-----------------:|
| Navigationsmenü | Navigation | ALT+M |
|  | Startseite | ALT+H |
|  | Alle Apps | ALT+A |
|  | Installierte Apps | ALT+I |
|  | Senden von Feedback | ALT+F |
|  | Mein Profil | ALT+U |
|  | Einstellung | ALT+T |
| Start – Gerätekachel | Umbenennen | F2 |
|  | Remove | STRG+D oder ENTF-TASTE |
|  | Zugriff prüfen | STRG+M oder F9 |
| Gerätedetails | Umbenennen | F2 |
|  | Remove | STRG+D oder ENTF-TASTE |
|  | Zugriff prüfen | STRG+M oder F9 |
| App-Details | „Installieren“ zu klicken. | STRG+I |

Endbenutzer können zudem die verfügbaren Tastenkombinationen in der Windows-Unternehmensportal-App einsehen.

![Screenshot der verfügbaren Tastenkombinationen im Windows-Unternehmensportal](media/company-portal-app/company-portal-app-01.png)

## <a name="next-steps"></a>Nächste Schritte

- [Manuelles Hinzufügen der Windows 10-Unternehmensportal-App mithilfe von Microsoft Intune](store-apps-company-portal-app.md)
