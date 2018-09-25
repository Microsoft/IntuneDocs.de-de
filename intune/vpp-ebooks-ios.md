---
title: Verwalten von per Volumenlizenz erworbenen iOS-E-Books
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Bücher, die Sie über ein Volumenprogramm im iOS Store erworben haben, in Intune synchronisieren und dann ihre Nutzung verwalten und nachverfolgen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3d7e016f7ce797ba1873d3fe3e7dcd9065300844
ms.sourcegitcommit: 63b74a60aafa8d2d6af0594448ae0471fbd79194
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494097"
---
# <a name="how-to-manage-ios-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Verwalten von iOS-E-Books, die über ein Volumenprogramm erworben wurden, mit Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mit dem Apple Volume Purchase Program (VPP) können Sie mehrere Lizenzen für ein Buch kaufen, das Sie an Benutzer in Ihrem Unternehmen verteilen möchten. Sie können Bücher aus den Stores für Unternehmen oder für Bildungseinrichtungen verteilen.

Microsoft Intune hilft Ihnen beim Synchronisieren, Verwalten und Zuweisen der Bücher, die Sie über dieses Programm erworben haben. Sie können die Lizenzinformationen aus dem Store importieren und verfolgen, wie viele Lizenzen Sie verwendet haben.

Die Verfahren zum Verwalten von Büchern ähneln denen zum [Verwalten von VPP-Apps](vpp-apps-ios.md).

## <a name="manage-volume-purchased-books-for-ios-devices"></a>Verwalten von per Volumenlizenz erworbenen Büchern für iOS-Geräte
Sie erwerben mehrere Lizenzen für iOS-Bücher über das [Apple Volume Purchase Program für Unternehmen](http://www.apple.com/business/vpp/) oder das [Apple Volume Purchase Program für Bildungseinrichtungen](http://volume.itunes.apple.com/us/store). Dieser Vorgang umfasst das Einrichten eines Apple VPP-Kontos auf der Apple-Website und das Hochladen des Apple VPP-Tokens in Intune.  Anschließend können Sie Ihre Informationen zum Volumenerwerb mit Intune synchronisieren und die Verwendung des per Volumenlizenz erworbenen Buchs verfolgen.

## <a name="before-you-start"></a>Vorbereitungen
Bevor Sie beginnen, rufen Sie ein VPP-Token von Apple ab und laden es in Ihr Intune-Konto hoch. Darüber hinaus gilt:

* Sie können Ihrem Intune-Konto bis zu 256 VPP-Token zuordnen.
* Wenn Sie zuvor ein VPP-Token für ein anderes Produkt verwendet haben, müssen Sie für die Verwendung mit Intune ein neues erstellen.
* Jedes Token ist ein Jahr lang gültig.
* Standardmäßig wird Intune zweimal täglich mit dem Apple VPP-Dienst synchronisiert. Eine manuelle Synchronisierung können Sie jederzeit starten.
* Nachdem Sie den VPP-Token in Intune importiert haben, importieren Sie denselben Token in keine andere Geräteverwaltungslösung. Andernfalls kann dies zu einem Verlust von Lizenzzuweisung und Benutzerdatensätzen führen.
* Bevor Sie iOS-Bücher mit Intune verwenden, entfernen Sie alle vorhandenen, mit anderen Anbietern für die mobile Geräteverwaltung (MDM) erstellten VPP-Benutzerkonten. Aus Sicherheitsgründen synchronisiert Intune diese Benutzerkonten nicht. Intune synchronisiert nur Daten aus dem Apple VPP-Dienst, der von Intune erstellt wurde.
* Wenn Sie ein Buch einem Gerät zuweisen, muss auf dem Gerät die integrierte iBooks-App installiert sein. Wenn dies nicht der Fall ist, muss der Endbenutzer die App erneut installieren, bevor er das Buch lesen kann. Sie können Intune derzeit nicht zum Wiederherstellen entfernt integrierter Apps verwenden.
* Sie können nur Bücher von der Apple Volume Purchase Program-Website zuweisen. Sie können keine Bücher hochladen und dann zuweisen, die Sie intern erstellt haben.
* Sie können derzeit keine Bücher zu Endbenutzerkategorien zuweisen, so wie Sie Apps zuweisen können.
* Das Freigeben einer Lizenz ist nicht möglich, nachdem das Buch zugewiesen wurde.
* Wenn ein Benutzer mit einem geeigneten Gerät erstmals versucht, ein VPP-Buch zu installieren, muss er dem Apple Volume Purchase Program beitreten, bevor er ein Buch installieren kann. Sie können auch Sicherheitsgruppen mit verwalteten Apple-IDs Lizenzen zuweisen. In diesem Fall müssen die Benutzer nicht ihre Apple-ID angeben, wenn ein Buch installiert wird.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>So können Sie einen Apple VPP-Token abrufen und hochladen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** die Option **Client-Apps** aus.
1.  Wählen Sie in der Workload **Client-Apps** die Option **Setup** > **iOS-VPP-Token** aus.
2.  Klicken Sie im Bereich mit der Liste der VPP-Token auf **Erstellen**.
3.  Geben Sie im Bereich **Neues VPP-Token** die folgenden Informationen an:
    - **VPP-Tokendatei:** Stellen Sie sicher, dass Sie sich für das Volume Purchase Program für Unternehmen oder das Volume Purchase Program für Bildungseinrichtungen registriert haben. Laden Sie dann das Apple-VPP-Token für Ihr Konto herunter und wählen es hier aus.
    - **Apple-ID:** Geben Sie die Apple-ID des Kontos ein, das dem Programm für Volumenlizenzen zugeordnet ist.
    - **Typ des VPP-Kontos:** Wählen Sie **Unternehmen** oder **Bildungswesen** aus.
4. Klicken Sie auf **Erstellen**, wenn Sie fertig sind.

Das Token wird im Bereich mit der Liste der Token angezeigt.


Sie können die von Apple gespeicherten Daten jederzeit mit Intune synchronisieren, indem Sie **Jetzt synchronisieren** wählen.

## <a name="to-assign-a-volume-purchased-app"></a>So weisen Sie per Volumenlizenz erworbene Apps zu

3. Klicken Sie im Bereich **Intune** auf die Option **eBooks**.
1. Wählen Sie in der Workload **E-Books** die Option **Verwalten** > **Alle E-Books** aus.
2. Wählen Sie im Bereich mit der Liste der Bücher das Buch aus, das Sie zuweisen möchten, und klicken Sie dann auf **...** > **Gruppen zuweisen**.
3. Klicken Sie im Bereich <*Buchname*> - **Zugewiesene Gruppen** auf **Verwalten** > **Zugewiesene Gruppen**.
4. Klicken Sie auf **Gruppen zuweisen**, und wählen Sie dann im Bereich **Gruppen auswählen** die Azure AD-Benutzergruppen aus, denen Sie das Buch zuweisen möchten. Gerätegruppen werden momentan nicht unterstützt.
Wählen Sie eine Zuweisungsaktion vom Typ **Verfügbar** oder **Erforderlich** aus. 
5. Wählen Sie abschließend **Speichern** aus.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Überwachen von Buchzuweisungen finden Sie unter [Überwachen von Apps](apps-monitor.md).






