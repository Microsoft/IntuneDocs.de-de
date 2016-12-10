---
title: Anpassen des Unternehmensportals | Microsoft Intune
description: "Mit dem Unternehmensportal können Benutzer gängige Aufgaben ausführen und z.B. Geräte registrieren, Apps installieren und Informationen zur IT-Abteilung abrufen."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb4a9f01-f857-4563-ab6f-5d0d7dfa659d
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 04cccd410417dca4477c0d6cd61b0940dda8c389


---

# <a name="customize-the-company-portal"></a>Anpassen des Unternehmensportals
Im Intune-Unternehmensportal können Benutzer auf Unternehmensdaten zugreifen, häufige Aufgaben wie das Registrieren von Geräten und das Installieren von Apps ausführen und sich über Unterstützungsmöglichkeiten durch Ihre IT-Abteilung informieren.

Das Intune-Unternehmensportal stellt Benutzern Zugriff auf Unternehmensdaten und -Apps bereit. Das Unternehmensportal ist in zwei Varianten verfügbar:

-   **Die Unternehmensportal-App**: Diese Anwendung ist auf Geräten verfügbar, die Sie mit Intune verwalten. Erfahren Sie mehr über die Unternehmensportal-Apps für [Android](/Intune/EndUser/using-your-android-device-with-intune), [iOS](/Intune/EndUser/using-your-ios-or-mac-os-x-device-with-intune) und [Windows](/Intune/EndUser/using-your-windows-device-with-intune).


- **Die Unternehmensportal-Website**: Eine Website, mit der Endbenutzer die meisten der Aufgaben ausführen können, die mit der Unternehmensportal-App ausgeführt werden können. Die URL zum Intune-Unternehmensportal lautet [http://portal.manage.microsoft.com](http://portal.manage.microsoft.com). Weitere Informationen zu dieser Website finden Sie unter [Verwenden der Intune-Unternehmensportal-Website](/Intune/EndUser/using-the-intune-company-portal-website).

> [!TIP]
> Wenn Sie das Unternehmensportal anpassen, gelten die Konfigurationen sowohl für die Unternehmensportalwebsite als auch für die Unternehmensportal-Apps.

Dies sind einige der Aufgaben, die Benutzern im Unternehmensportal ausführen können:

-   Registrieren von Geräten
-   Anzeigen des Gerätestatus
-   Zurücksetzen des Geräts
-   Zurücksetzen des Kennworts
-   Remotesperren des Geräts
-   Herunterladen von Software, die von der Organisation bereitgestellt wird
-   Wenden Sie sich zu Supportzwecken an die IT-Abteilung.

> [!NOTE]
> Die Unternehmensportal-App ist in einigen Ländern noch nicht verfügbar.
> __iOS__: Die Unternehmensportal-App für iOS wird [in allen verfügbaren Gebieten](https://go.microsoft.com/fwlink/?linkid=831284) für den Apple iOS App Store veröffentlicht.
> __Android__: Die Unternehmensportal-App für Android ist in China zurzeit nicht verfügbar. Für diese Länder ist eine alternative Lösung, [die Android-Version der Unternehmensportal-App querzuladen](https://www.microsoft.com/en-us/download/details.aspx?id=49140).  

## <a name="customize-company-portal-settings"></a>Anpassen von Unternehmensportaleinstellungen
Durch Anpassen des Unternehmensportals können Sie Ihren Endbenutzern eine vertraute und sinnvolle Benutzeroberfläche bereitstellen. Melden Sie sich zu diesem Zweck einfach als Mandanten- oder Dienstadministrator bei der [Microsoft Intune-Administratorkonsole](https://manage.microsoft.com) an, wählen Sie **Verwaltung** &gt; **Unternehmensportal** aus, und konfigurieren Sie die Einstellungen für das Unternehmensportal.

![admin-console-admin-workspace-comp-portal-settings](./media/companyportal.png)

## <a name="company-contact-information-and-privacy-statement"></a>Kontaktdaten und Datenschutzerklärung des Unternehmens
Der Unternehmensname wird als Titel des Unternehmensportals angezeigt. Die Kontaktinformationen werden Benutzern im Unternehmensportal auf dem Bildschirm für die Kontaktaufnahme mit der IT-Abteilung angezeigt. Die Datenschutzerklärung wird angezeigt, wenn ein Benutzer auf den Datenschutzlink klickt.

|Feldname|Max. Länge|Weitere Informationen|
    |----------|------------------------|----------------|
    |Firmenname|40|Dieser Name wird als Titel des Unternehmensportals angezeigt.|
    |Kontaktname für IT-Abteilung|40|Dieser Name wird auf der Seite **An IT-Abteilung wenden** angezeigt.|
    |Telefonnummer der IT-Abteilung|20|Diese Telefonnummer wird auf der Seite **An IT-Abteilung wenden** angezeigt.|
    |E-Mail-Adresse der IT-Abteilung|40|Diese Kontaktadresse wird auf der Seite **An IT-Abteilung** wenden angezeigt. Sie müssen eine gültige E-Mail-Adresse im Format **alias@domainname.com** eingeben.|
    |Weitere Informationen|120|Dies wird auf der Seite **An IT-Abteilung wenden** angezeigt.|
    |URL der Datenschutzrichtlinie des Unternehmens|79|Sie können eine eigene Datenschutzerklärung für Ihr Unternehmen angeben. Diese wird angezeigt, wenn die Benutzer im Unternehmensportal auf die Datenschutzlinks klicken. Sie müssen eine gültige URL im Format https://www.contoso.com eingeben.|

## <a name="support-contacts"></a>Supportkontakte
Die Supportwebsite wird Benutzern im Unternehmensportal angezeigt, um ihnen Zugriff auf Onlinesupport zu ermöglichen.

|Feldname|Max. Länge|Weitere Informationen|
    |----------|------------------------|----------------|
    |URL der Supportwebsite|150|Wenn Sie über eine Supportwebsite verfügen, die Ihre Benutzer verwenden sollen, geben Sie hier die URL an. Die URL muss das Format https://www.contoso.com aufweisen. Wenn Sie keine URL angeben, wird im Unternehmensportal auf der Seite **An IT-Abteilung wenden** keine Supportwebsite angezeigt.|
    |Name der Website|40|Dies ist der Anzeigename der URL für die Supportwebsite. Wenn Sie für die Supportwebsite eine URL, aber keinen Anzeigenamen angeben, wird im Unternehmensportal auf der Seite **An IT-Abteilung wenden** der Text **Zur IT-Website wechseln** angezeigt.|

## <a name="company-branding-customization"></a>Anpassen des Unternehmensbrandings
Sie können Ihr Unternehmensportal mit Ihrem Firmenlogo, Firmennamen, Farbdesign und Hintergrund anpassen.

|Feldname|Weitere Informationen|
    |----------|----------------|
    |Farbdesign|Wählen Sie ein Farbdesign aus, das auf das Unternehmensportal angewendet werden soll.|
    |Firmenlogo einschließen|Wenn Sie diese Option aktivieren, können Sie Ihr Firmenlogo hochladen. Dieses wird dann im Unternehmensportal angezeigt. Sie können zwei Logos hochladen: ein Logo, das angezeigt wird, wenn der Hintergrund des Unternehmensportals weiß ist, und eines, das angezeigt wird, wenn für den Hintergrund des Unternehmensportals das von Ihnen ausgewählte Farbdesign verwendet wird. Die Logodateien müssen PNG- oder JPG-Dateien sein. Ihre Auflösung darf maximal 400 x 100 Pixel betragen, und die Größe darf 750 KB nicht überschreiten.|
    |Hintergrund für die [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]-Unternehmensportal- App auswählen|Diese Einstellung betrifft nur den Hintergrund der Unternehmensportal-App für [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)].|


Nach dem Speichern Ihrer Änderungen können Sie über die Links, die am unteren Rand der Seite **Unternehmensportal** in der Administratorkonsole angegeben sind, die Unternehmensportalwebsite anzeigen. Diese Links können nicht geändert werden. Wenn ein Benutzer sich anmeldet, werden über diese Links Ihre Abonnements im Unternehmensportal angezeigt.

>[!div class="step-by-step"]

>[&larr; **Erstellen von Richtlinien und Apps**](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)       [**Registrieren von Geräten** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)  



<!--HONumber=Dec16_HO2-->

