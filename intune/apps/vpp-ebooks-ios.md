---
title: Verwalten von per Volumenlizenz erworbenen iOS-/iPadOS-E-Books
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Bücher, die Sie über ein Volumenprogramm im iOS Store erworben haben, in Intune synchronisieren und dann ihre Nutzung verwalten und nachverfolgen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff2ed62695bad781b7b55ac590e9b97490ba2416
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216082"
---
# <a name="how-to-manage-iosipados-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Verwalten von iOS-/iPadOS-E-Books, die über ein Volumenprogramm erworben wurden, mit Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Mit dem Apple Volume Purchase Program (VPP) können Sie mehrere Lizenzen für ein Buch kaufen, das Sie an Benutzer in Ihrem Unternehmen verteilen möchten. Sie können Bücher aus den Stores für Unternehmen oder für Bildungseinrichtungen verteilen.

Microsoft Intune hilft Ihnen beim Synchronisieren, Verwalten und Zuweisen der Bücher, die Sie über dieses Programm erworben haben. Sie können die Lizenzinformationen aus dem Store importieren und verfolgen, wie viele Lizenzen Sie verwendet haben.

Die Verfahren zum Verwalten von Büchern ähneln denen zum [Verwalten von VPP-Apps](../vpp-apps-ios.md).

## <a name="manage-volume-purchased-books-for-ios-devices"></a>Verwalten von per Volumenlizenz erworbenen Büchern für iOS-Geräte
Sie erwerben mehrere Lizenzen für iOS-/iPadOS-Bücher über das [Apple Volume Purchase Program für Unternehmen](https://www.apple.com/business/vpp/) oder das [Apple Volume Purchase Program für Bildungseinrichtungen](https://volume.itunes.apple.com/us/store). Dieser Vorgang umfasst das Einrichten eines Apple VPP-Kontos auf der Apple-Website und das Hochladen des Apple VPP-Tokens in Intune.  Anschließend können Sie Ihre Informationen zum Volumenerwerb mit Intune synchronisieren und die Verwendung des per Volumenlizenz erworbenen Buchs verfolgen.

## <a name="before-you-start"></a>Vorbereitung
Bevor Sie beginnen, rufen Sie ein VPP-Token von Apple ab und laden es in Ihr Intune-Konto hoch. Darüber hinaus gilt:

* Wenn Sie zuvor ein VPP-Token für ein anderes Produkt verwendet haben, müssen Sie für die Verwendung mit Intune ein neues erstellen.
* Jedes Token ist ein Jahr lang gültig.
* Standardmäßig wird Intune zweimal täglich mit dem Apple VPP-Dienst synchronisiert. Eine manuelle Synchronisierung können Sie jederzeit starten.
* Nachdem Sie den VPP-Token in Intune importiert haben, importieren Sie denselben Token in keine andere Geräteverwaltungslösung. Andernfalls kann dies zu einem Verlust von Lizenzzuweisung und Benutzerdatensätzen führen.
* Bevor Sie iOS-/iPadOS-Bücher mit Intune verwenden, entfernen Sie alle vorhandenen, mit anderen Anbietern für die mobile Geräteverwaltung (MDM) erstellten VPP-Benutzerkonten. Aus Sicherheitsgründen synchronisiert Intune diese Benutzerkonten nicht. Intune synchronisiert nur Daten aus dem Apple VPP-Dienst, der von Intune erstellt wurde.
* Wenn Sie ein Buch einem Gerät zuweisen, muss auf dem Gerät die integrierte iBooks-App installiert sein. Wenn dies nicht der Fall ist, muss der Endbenutzer die App erneut installieren, bevor er das Buch lesen kann. Sie können Intune derzeit nicht zum Wiederherstellen entfernt integrierter Apps verwenden.
* Sie können nur Bücher von der Apple Volume Purchase Program-Website zuweisen. Sie können keine Bücher hochladen und dann zuweisen, die Sie intern erstellt haben.
* Sie können derzeit keine Bücher zu Endbenutzerkategorien zuweisen, so wie Sie Apps zuweisen können.
* Das Freigeben einer Lizenz ist nicht möglich, nachdem das Buch zugewiesen wurde.
* Wenn ein Benutzer mit einem geeigneten Gerät erstmals versucht, ein VPP-Buch zu installieren, muss er dem Apple Volume Purchase Program beitreten, bevor er ein Buch installieren kann. Sie können auch Sicherheitsgruppen mit verwalteten Apple-IDs Lizenzen zuweisen. In diesem Fall müssen die Benutzer nicht ihre Apple-ID angeben, wenn ein Buch installiert wird.
* Die Registrierung von Geräten muss Benutzeraffinität aufweisen, da E-Books nur Benutzergruppen zugeordnet werden können.   


## <a name="to-get-and-upload-an-apple-vpp-token"></a>So können Sie einen Apple VPP-Token abrufen und hochladen

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Mandantenverwaltung** > **Connectors und Token** > **Apple-VPP-Token** aus.
3. Klicken Sie im Bereich mit der Liste der VPP-Token auf **Erstellen**.
5. Geben Sie im Bereich **Neues VPP-Token** die folgenden Informationen an:
    - **VPP-Tokendatei:** Stellen Sie sicher, dass Sie sich für das Volume Purchase Program für Unternehmen oder das Volume Purchase Program für Bildungseinrichtungen registriert haben. Laden Sie dann das Apple-VPP-Token für Ihr Konto herunter und wählen es hier aus.
    - **Apple-ID:** Geben Sie die Apple-ID des Kontos ein, das dem Programm für Volumenlizenzen zugeordnet ist.
    - **Typ des VPP-Kontos:** Wählen Sie **Unternehmen** oder **Bildungswesen** aus.
5. Klicken Sie auf **Erstellen**, wenn Sie fertig sind.

Das Token wird im Bereich mit der Liste der Token angezeigt.


Sie können die von Apple gespeicherten Daten jederzeit mit Intune synchronisieren, indem Sie **Jetzt synchronisieren** wählen.

## <a name="to-assign-a-volume-purchased-app"></a>So weisen Sie per Volumenlizenz erworbene Apps zu

1. Wählen Sie **Apps** > **eBooks** > **Alle eBooks** aus.
2. Wählen Sie im Bereich mit der Liste der Bücher das Buch aus, das Sie zuweisen möchten, und klicken Sie dann auf **...** > **Gruppen zuweisen**.
3. Klicken Sie im Bereich <*Buchname*> - **Zugewiesene Gruppen** auf **Verwalten** > **Zugewiesene Gruppen**.
4. Klicken Sie auf **Gruppen zuweisen**, und wählen Sie dann im Bereich **Gruppen auswählen** die Azure AD-Benutzergruppen aus, denen Sie das Buch zuweisen möchten. Gerätegruppen werden momentan nicht unterstützt.
Wählen Sie eine Zuweisungsaktion vom Typ **Verfügbar** oder **Erforderlich** aus. 
5. Wählen Sie abschließend **Speichern** aus.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Überwachen von Buchzuweisungen finden Sie unter [Überwachen von Apps](apps-monitor.md).






