---
title: Konfigurieren der Unternehmensportal-App
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie unternehmensspezifisches Branding auf die Intune-Unternehmensportal-App anwenden können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5a7213608a8147178633ccd8129ab40eef5d4a15
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Konfigurieren der Microsoft Intune-Unternehmensportal-App

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Im Microsoft Intune-Unternehmensportal können Benutzer auf Unternehmensdaten zugreifen, häufige Aufgaben wie das Registrieren von Geräten und das Installieren von Apps ausführen und sich über Unterstützungsmöglichkeiten durch Ihre IT-Abteilung informieren.        

> [!Tip]        
> Wenn Sie das Unternehmensportal anpassen, gelten die Konfigurationen sowohl für die Unternehmensportal-Website als auch für die Unternehmensportal-Apps.       

Durch Anpassen des Unternehmensportals können Sie Ihren Endbenutzern eine vertraute und sinnvolle Benutzeroberfläche bereitstellen. Dazu wählen Sie in der Workload **Mobile Apps** die Option **Setup** > **Branding des Unternehmensportals** aus und konfigurieren die erforderlichen Einstellungen.      

## <a name="company-contact-information-and-privacy-statement"></a>Kontaktdaten und Datenschutzerklärung des Unternehmens        
Der Unternehmensname wird als Titel des Unternehmensportals angezeigt. Die Kontaktinformationen werden Benutzern im Unternehmensportal auf dem Bildschirm **An IT-Abteilung wenden** angezeigt. Die Datenschutzerklärung wird angezeigt, wenn ein Benutzer auf den Datenschutzlink klickt.

Mit einem Sternchen (*) gekennzeichnete Felder sind obligatorisch.       


| Feldname | Max. Länge | Weitere Informationen |
|---|---|---|
|**Firmenname**| 40 | Dieser Name wird als Titel des Unternehmensportals angezeigt. |
|**Kontaktname für IT-Abteilung** | 40 | Dieser Name wird auf der Seite **An IT-Abteilung wenden** angezeigt. |
|**Telefonnummer der IT-Abteilung** | 20 | Diese Telefonnummer wird auf der Seite **An IT-Abteilung wenden** angezeigt. |
|**E-Mail-Adresse der IT-Abteilung**| 40 | Diese Kontaktadresse wird auf der Seite **An IT-Abteilung** wenden angezeigt. Sie müssen eine gültige E-Mail-Adresse im Format `alias@domainname.com` eingeben. |
| **Weitere Informationen**|    120     | Dies wird auf der Seite **An IT-Abteilung wenden** angezeigt. |
| **URL der Datenschutzrichtlinie des Unternehmens** |     79     | Sie können eine eigene Datenschutzerklärung für Ihr Unternehmen angeben. Diese wird angezeigt, wenn die Benutzer im Unternehmensportal auf die Datenschutzlinks klicken. Sie müssen eine gültige URL im Format `<https://www.contoso.com>` eingeben. |

## <a name="support-contacts"></a>Supportkontakte     
Die Supportwebsite wird Benutzern im Unternehmensportal angezeigt, um ihnen Zugriff auf Onlinesupport zu ermöglichen.        

|Feldname|Max. Länge|Weitere Informationen|
|---|---|---|
|**URL der Supportwebsite**|150|Wenn Sie über eine Supportwebsite verfügen, die Ihre Benutzer verwenden sollen, geben Sie hier die URL an. Die URL muss das Format **https://www.contoso.com** aufweisen. Wenn Sie keine URL angeben, wird im Unternehmensportal auf der Seite **An IT-Abteilung wenden** keine Supportwebsite angezeigt.|
|**Name der Supportwebsite**|40|Dies ist der Anzeigename der URL für die Supportwebsite. Wenn Sie für die Supportwebsite eine URL, aber keinen Anzeigenamen angeben, wird im Unternehmensportal auf der Seite **An IT-Abteilung wenden** der Text „Zur IT-Website wechseln“ angezeigt.

## <a name="company-branding-customization"></a>Anpassen des Unternehmensbrandings       
Sie können Ihr Unternehmensportal mit Ihrem Firmenlogo, Firmennamen, Farbdesign und Hintergrund anpassen.     

|Feldname|Weitere Informationen|
|---|---|
|**Farbdesign**|Wählen Sie ein Farbdesign aus, das auf das Unternehmensportal angewendet werden soll. Sie können das Farbdesign entweder über den Farb-Editor auswählen oder einen bestimmten Hexadezimalcode angeben.|
|**Firmenlogo anzeigen**|Wenn Sie diese Option aktivieren, können Sie Ihr Firmenlogo hochladen. Dieses wird dann im Unternehmensportal angezeigt. Sie können zwei Logos hochladen: ein Logo, das angezeigt wird, wenn der Hintergrund des Unternehmensportals weiß ist, und eines, das angezeigt wird, wenn für den Hintergrund des Unternehmensportals das von Ihnen ausgewählte Farbdesign verwendet wird. Die Logodateien müssen PNG- oder JPG-Dateien sein. Ihre Auflösung darf maximal 400 x 100 Pixel betragen, und die Größe darf 750 KB nicht überschreiten.<br>Sie können auch den eingegebenen Firmennamen neben dem hochgeladenen Logo anzeigen.|

Nachdem Sie Ihre Änderungen gespeichert haben, können Sie **eine Vorschau der Einstellungen im Intune-Webportal anzeigen**, um Ihre Konfiguration zu überprüfen.
