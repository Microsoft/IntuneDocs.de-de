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
ms.subservice: end-user
ms.technology: ''
ms.assetid: df973b18-9166-417d-8aa3-49edd2bda256
searchScope:
- User help
ROBOTS: NOINDEX, NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 753fce1e37014e0ad4dac44f1eeb9284482e8f83
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72500169"
---
# <a name="your-android-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>Auf Ihrem Android-Gerät fehlt ein Zertifikat, das in der Regel auf Ihrem Telefon installiert ist.

Wenn Ihr Gerät nicht bei Intune registriert ist und ein Zertifikat fehlt, das normalerweise auf Ihrem Telefon installiert ist, können Sie sich nicht bei der Unternehmensportal-App anmelden. Wenn Sie versuchen, sich anzumelden, sehen Sie die folgende Meldung:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Sie können dieses Problem beheben, indem Sie das erforderliche Zertifikat von der [Zertifikatseite von Digicert](https://www.digicert.com/digicert-root-certificates.htm) abrufen.

1. Suchen Sie das Zertifikat __Baltimore CyberTrust Root__, und laden Sie es herunter. Sie können es auch direkt [hier](https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt) herunterladen.

2. Ziehen Sie vom oberen Bildschirmrand nach unten, um die Liste der aktuellen Benachrichtigungen zu öffnen, und tippen Sie auf **BaltimoreCyberTrustRoot.crt**.

3. Das Gerät fordert Sie zum **Benennen des Zertifikats** auf. Ändern Sie den angezeigten standardmäßigen Zertifikatnamen nicht.

4. Stellen Sie sicher, dass **Verwendung von Anmeldeinformationen** auf **Für VPN und Apps** festgelegt ist, und tippen Sie dann auf **OK**.

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

5. Schließen Sie den Browser und die Unternehmensportal-App.

6. Öffnen Sie die Unternehmensportal-App erneut. Sie sollten sich jetzt bei der Unternehmensportal-App anmelden können. Wenn Sie die Unternehmensportal-App weiterhin nicht verwenden können, wenden Sie sich mithilfe der Informationen auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980) an die Supportabteilung Ihres Unternehmens, um weitere Anweisungen zu erhalten.

>[!NOTE]
> Wenn das Problem durch Installieren dieses Zertifikats nicht behoben werden kann und Ihnen eine Meldung zu einem anderen fehlenden Zertifikat angezeigt wird, müssen Sie weitere Schritte ausführen, um [das fehlende Zertifikat zu installieren](your-device-is-missing-an-IT-required-certificate-android.md).

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).
