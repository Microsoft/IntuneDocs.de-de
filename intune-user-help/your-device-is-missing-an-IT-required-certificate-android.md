---
title: Auf Ihrem Gerät ist ein Zertifikat nicht vorhanden | Microsoft-Dokumentation
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 25ec84946aec9562aedce12b4199269f8de06f76
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72500014"
---
# <a name="install-missing-certificate-required-by-your-organization"></a>Installieren des fehlenden Zertifikats, das für Ihre Organisation erforderlich ist  

Wenn Ihr Gerät nicht bei InTune registriert ist und ein erforderliches Zertifikat fehlt, können Sie sich nicht bei der Unternehmensportal-App anmelden. Wenn Sie versuchen, sich anzumelden, sehen Sie die folgende Meldung:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Es gibt zwei Möglichkeiten, das erforderliche Zertifikat herunterzuladen und das Gerät zu registrieren. 

- Aktivieren Sie den Browser Zugriff in Unternehmensportal-app.
- Identifizieren Sie das fehlende Zertifikat auf einem Unternehmens- oder Schul-PC. Durchsuchen Sie dann das Internet, um das fehlende Zertifikat herunterzuladen. 

Führen Sie zuerst die Schritte zum Aktivieren des Browser Zugriffs aus. Wenn Sie das Gerät noch immer nicht registrieren können, führen Sie die Schritte aus, um das Zertifikat im Internet zu suchen. 

## <a name="enable-browser-access"></a>Browser Zugriff aktivieren
Führen Sie diese Schritte zum Aktivieren des Browser Zugriffs aus. Nachdem Sie den Zugriff aktiviert haben, wird Unternehmensportal das entsprechende Zertifikat installieren und die Registrierung fortsetzen.    

1. Wechseln Sie in der Unternehmensportal-App zur rechten Ecke, und wählen Sie das Menü aus.  
2. Klicken Sie auf **Einstellungen**.  
3. Wählen Sie neben **Browser Zugriff aktivieren** die Option **aktivieren aus**.  
4. Wählen Sie auf dem Bildschirm Geräte Administrator die Option **aktivieren**aus. 

## <a name="identify-and-download-the-missing-certificate-through-web-search"></a>Identifizieren und Herunterladen des fehlenden Zertifikats über die Websuche
Führen Sie diese Schritte aus, um das Zertifikat manuell auf Ihrem Gerät zu identifizieren und zu installieren.  

1. Öffnen Sie auf einem PC den Internet Explorer. Wenn Ihnen dafür kein PC zur Verfügung steht, wenden Sie sich an die Supportabteilung Ihres Unternehmens. Die Kontaktinformationen für die Supportabteilung Ihres Unternehmens finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).

2. Öffnen Sie die [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980), und melden Sie sich mit Ihren Geschäfts- oder Schulanmeldeinformationen an.

3. Wählen Sie ganz rechts in der Adressleiste des Browsers das Symbol aus, das wie ein Vorhängeschloss aussieht, wie im nachstehenden Screenshot dargestellt.

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    Wenn das Vorhängeschlosssymbol nicht angezeigt wird, beenden Sie den Vorgang, und wenden Sie sich an die Supportabteilung Ihres Unternehmens. Das Vorhängeschlosssymbol bedeutet, dass Sie sicher angemeldet sind, Sie sollten also nicht fortfahren, solange dieses Symbol nicht angezeigt wird.

4. Wählen Sie **Zertifikate anzeigen** aus.

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. Wählen Sie die Registerkarte **Zertifizierungspfad** aus, und identifizieren Sie das Zertifikat, das Sie aus dem Internet abrufen müssen. Der Name des Zertifikats, das Sie benötigen, befindet sich an der gleichen Position wie der, der im vorherigen Beispielscreenshot hervorgehoben ist.

6. Suchen Sie mithilfe einer Suchmaschine wie Bing oder Google nach dem Namen des fehlenden Zertifikats, das Sie im vorherigen Abschnitt angegeben haben. Das Zertifikat kann mit verschiedenen Erweiterungen wie CRT oder PEM usw. enden.

7. Laden Sie das Stammzertifikat von der Website herunter.

8. Ziehen Sie nach dem Herunterladen des Zertifikats vom oberen Rand Ihres Geräts nach unten, um Ihre Benachrichtigungen zu öffnen, und tippen Sie dann in der Liste der Benachrichtigungen auf den Namen des Zertifikats.

4. Übernehmen Sie im Dialogfeld **Name the Certificate** (Zertifikat benennen), das im folgenden Screenshot angezeigt wird, den Standardzertifikatnamen.

5. Stellen Sie sicher, dass **Verwendung von Anmeldeinformationen** auf **Für VPN und Apps** festgelegt ist, und tippen Sie dann auf **OK**.

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. Schließen Sie die Unternehmensportal-App.

7. Öffnen Sie die Unternehmensportal-App erneut. Sie sollten sich jetzt bei der Unternehmensportal-App anmelden können. Wenn Sie Hilfe benötigen, wenden Sie sich an die Supportabteilung Ihres Unternehmens.

Wenn Ihnen die gleiche „Zertifikat fehlt“-Meldung wie in der Abbildung oben angezeigt wird, und Sie den oben beschriebenen Vorgang bereits ausgeführt haben, benötigt die Supportabteilung Ihres Unternehmens wahrscheinlich noch ein anderes Zertifikat, um Ihnen bei der Installation helfen zu können. Verwenden Sie die Kontaktinformationen auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980), wenn Sie sich an die Supportabteilung Ihres Unternehmens wenden möchten.

## <a name="next-steps"></a>Nächste Schritte  

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  
