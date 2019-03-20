---
title: Auf Ihrem Gerät ist ein Zertifikat nicht vorhanden | Microsoft-Dokumentation
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0ef2bc644b537787bd5275e95a4ecc72c899393
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "55835876"
---
# <a name="your-android-device-is-missing-a-certificate-required-by-your-company-support"></a>Auf Ihrem Android-Gerät fehlt ein Zertifikat, das von der Supportabteilung Ihres Unternehmens verlangt wird.

Wenn Ihr Gerät nicht bei Intune registriert ist und ein bestimmtes Zertifikat fehlt, das von der Supportabteilung Ihres Unternehmens verlangt wird, können Sie sich nicht bei der Unternehmensportal-App anmelden. Wenn Sie versuchen, sich anzumelden, sehen Sie die folgende Meldung:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Um dieses Problem zu lösen und das erforderliche Zertifikat zu erhalten, müssen Sie zwei Hauptschritte ausführen:

- Identifizieren Sie das fehlende Zertifikat in einem Unternehmens oder Schul-PC.
- Laden Sie das fehlende Zertifikat mit Ihrem Gerät aus dem Internet herunter.

## <a name="identify-the-missing-certificate-by-looking-on-a-company-or-school-pc"></a>Identifizieren des fehlenden Zertifikats durch Suche auf einem Unternehmens oder Schul-PC

1. Öffnen Sie auf einem PC den Internet Explorer. Wenn Ihnen dafür kein PC zur Verfügung steht, wenden Sie sich an die Supportabteilung Ihres Unternehmens. Die Kontaktinformationen für die Supportabteilung Ihres Unternehmens finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).

2. Öffnen Sie die [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980), und melden Sie sich mit Ihren Geschäfts- oder Schulanmeldeinformationen an.

3. Wählen Sie ganz rechts in der Adressleiste des Browsers das Symbol aus, das wie ein Vorhängeschloss aussieht, wie im nachstehenden Screenshot dargestellt.

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    Wenn das Vorhängeschlosssymbol nicht angezeigt wird, beenden Sie den Vorgang, und wenden Sie sich an die Supportabteilung Ihres Unternehmens. Das Vorhängeschlosssymbol bedeutet, dass Sie sicher angemeldet sind, Sie sollten also nicht fortfahren, solange dieses Symbol nicht angezeigt wird.

4. Wählen Sie **Zertifikate anzeigen** aus.

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. Wählen Sie im Dialogfeld **Zertifikat** die Registerkarte **Zertifizierungspfad** aus, und identifizieren Sie das Zertifikat, das Sie aus dem Internet abrufen müssen. Der Name des Zertifikats, das Sie benötigen, befindet sich an der gleichen Position wie der, der im vorherigen Beispielscreenshot hervorgehoben ist.

## <a name="download-and-install-the-missing-certificate-on-your-android-mobile-device"></a>Herunterladen des fehlenden Zertifikats auf das Android-Gerät und Installation

1. Suchen Sie mithilfe einer Suchmaschine wie Bing oder Google nach dem Namen des fehlenden Zertifikats, das Sie im vorherigen Abschnitt angegeben haben. Das Zertifikat kann mit verschiedenen Erweiterungen wie CRT oder PEM usw. enden.

2. Laden Sie das Stammzertifikat von der Website herunter.

3. Ziehen Sie nach dem Herunterladen des Zertifikats vom oberen Rand Ihres Geräts nach unten, um Ihre Benachrichtigungen zu öffnen, und tippen Sie dann in der Liste der Benachrichtigungen auf den Namen des Zertifikats.

4. Übernehmen Sie im Dialogfeld **Name the Certificate** (Zertifikat benennen), das im folgenden Screenshot angezeigt wird, den Standardzertifikatnamen.

5. Stellen Sie sicher, dass **Verwendung von Anmeldeinformationen** auf **Für VPN und Apps** festgelegt ist, und tippen Sie dann auf **OK**.

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. Schließen Sie die Unternehmensportal-App.

7. Öffnen Sie die Unternehmensportal-App erneut. Sie sollten sich jetzt bei der Unternehmensportal-App anmelden können. Wenn Sie Hilfe benötigen, wenden Sie sich an die Supportabteilung Ihres Unternehmens.

Wenn Ihnen die gleiche „Zertifikat fehlt“-Meldung wie in der Abbildung oben angezeigt wird, und Sie den oben beschriebenen Vorgang bereits ausgeführt haben, benötigt die Supportabteilung Ihres Unternehmens wahrscheinlich noch ein anderes Zertifikat, um Ihnen bei der Installation helfen zu können. Verwenden Sie die Kontaktinformationen auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980), wenn Sie sich an die Supportabteilung Ihres Unternehmens wenden möchten.
