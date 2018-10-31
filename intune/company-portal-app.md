---
title: Konfigurieren der Unternehmensportal-App
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie unternehmensspezifisches Branding auf die Intune-Unternehmensportal-App anwenden können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 01de402a48362f04680c569c40a812b6a4b83cc6
ms.sourcegitcommit: 38afcff149f9c86e92e5f1eccaa927859c395926
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307405"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Konfigurieren der Microsoft Intune-Unternehmensportal-App

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Im Microsoft Intune-Unternehmensportal können Benutzer auf Unternehmensdaten zugreifen, häufige Aufgaben wie das Registrieren von Geräten und das Installieren von Apps ausführen und sich über Unterstützungsmöglichkeiten durch Ihre IT-Abteilung informieren.        

> [!Tip]        
> Wenn Sie das Unternehmensportal anpassen, gelten die Konfigurationen sowohl für die Unternehmensportal-Website als auch für die Unternehmensportal-Apps.       

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


## <a name="company-branding-customization"></a>Anpassen des Unternehmensbrandings       
Sie können Ihr Unternehmensportal mit Ihrem Firmenlogo, Firmennamen, Farbdesign und Hintergrund anpassen. Um schnell ohne Testgerät eine Vorschau von der Brandingkonfiguration anzuzeigen, besuchen Sie [portal.manage.microsoft.com](https://portal.manage.microsoft.com). Beachten Sie, dass das Logo, das Sie hochladen, für E-Mail-Vorlagen verwendet wird.      

### <a name="theme-color"></a>Farbdesign
Wenden Sie ein Farbdesign auf das Unternehmensportal an. Wählen Sie eine Standardfarbe aus, oder geben Sie einen sechsstelligen Hexadezimalcode ein, um eine benutzerdefinierte Farbe festzulegen.

|Feldname|Weitere Informationen|
|---|---|
|**Farbtyp**| Wählen Sie ein Farbdesign aus, das auf das Unternehmensportal angewendet werden soll. Sie können aus einer Standardfarbe auswählen oder einen bestimmten Hexadezimalcode angeben. |
|**Farbe auswählen** oder **Code für Hexadezimalfarbe**| Wählen Sie ein Farbdesign aus, das auf das Unternehmensportal angewendet werden soll. Sie können aus einer Standardfarbe auswählen oder einen bestimmten Hexadezimalcode angeben. Diese Optionen werden auf Grundlage des von Ihnen ausgewählten **Farbtyps** bereitgestellt.  |

### <a name="company-logo"></a>Firmenlogo
Laden Sie Ihr Firmenlogo hoch, damit es auf der Intune-Benutzeroberfläche angezeigt wird.

|Feldname|Weitere Informationen|
|---|---|
|**Firmenlogo anzeigen**|Wenn Sie diese Option aktivieren, können Sie Ihr Firmenlogo hochladen. Dieses wird dann im Unternehmensportal angezeigt. Sie können zwei Logos hochladen: ein Logo, das angezeigt wird, wenn der Hintergrund des Unternehmensportals weiß ist, und eines, das angezeigt wird, wenn für den Hintergrund des Unternehmensportals das von Ihnen ausgewählte Farbdesign verwendet wird. |
|**Upload a logo to use on theme color backgrounds** (Ein Logo für die Verwendung auf Hintergründen in der Designfarbe hochladen)| Diese Option ist verfügbar, wenn Sie ausgewählt haben, dass das Firmenlogo angezeigt werden soll. Die Logodateien müssen PNG- oder JPG-Dateien sein. Ihre Auflösung darf maximal 400×400 Pixel betragen, und die Größe darf 750 KB nicht überschreiten. |
|**Upload logo to use on light backgrounds** (Logo für die Verwendung auf hellen Hintergründen hochladen)| Diese Option ist verfügbar, wenn Sie ausgewählt haben, dass das Firmenlogo angezeigt werden soll. Die Logodateien müssen PNG- oder JPG-Dateien sein. Ihre Auflösung darf maximal 400×400 Pixel betragen, und die Größe darf 750 KB nicht überschreiten. |
|**Show company name next to logo** (Firmenname neben Logo anzeigen)| Wählen Sie diese Option aus, um den eingegebenen Firmennamen neben dem hochgeladenen Logo anzuzeigen. |

Nachdem Sie Ihre Änderungen gespeichert haben, können Sie im oberen Bereich des Blatts **Preview your settings in the Intune Web Portal** (Vorschau Ihrer Einstellungen im Intune-Webportal anzeigen) aktivieren, um Ihre Konfiguration zu überprüfen.

## <a name="windows-company-portal-keyboard-shortcuts"></a>Tastenkombinationen für die Windows-Unternehmensportal-App

Endbenutzer können mithilfe von Tastenkombinationen (Tastenkombinations-Editor) Navigations-, App- und Geräteaktionen in der Windows-Unternehmensportal-App auslösen.

Die folgenden Tastenkombinationen stehen Ihnen in der Windows-Unternehmensportal-App zur Verfügung.

| Bereich | Beschreibung | Tastenkombination |
|:------------------:|:--------------:|:-----------------:|
| Navigationsmenü | Navigation | ALT+M |
|  | Startseite | ALT+H |
|  | Alle Apps | ALT+A |
|  | Installierte Apps | ALT+I |
|  | Feedback senden | ALT+F |
|  | Mein Profil | ALT+U |
|  | Einstellung | ALT+T |
| Start – Gerätekachel | Umbenennen | F2 |
|  | Remove | STRG+D oder ENTF-TASTE |
|  | Zugriff prüfen | STRG+M oder F9 |
| Gerätedetails | Umbenennen | F2 |
|  | Remove | STRG+D oder ENTF-TASTE |
|  | Zugriff prüfen | STRG+M oder F9 |
| App-Details | „Installieren“ zu klicken. | STRG+I |

## <a name="next-steps"></a>Nächste Schritte

- [Manuelles Hinzufügen der Windows 10-Unternehmensportal-App mithilfe von Microsoft Intune](store-apps-company-portal-app.md)