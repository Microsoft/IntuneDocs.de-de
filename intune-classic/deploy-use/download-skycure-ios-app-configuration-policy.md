---
title: Herunterladen der Skycure iOS-App-Konfigurationsrichtlinie
description: Laden Sie die Skycure iOS-App-Konfigurationsrichtlinie zur Verwendung mit der für Endbenutzer bereitgestellten Skycure iOS-App herunter.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d211b876-4d3a-473c-999f-843c0a16cd22
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0f8197146d8b4f42bcf199070551ba13aed92626
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="download-skycure-ios-app-configuration-policy"></a>Herunterladen der Skycure iOS-App-Konfigurationsrichtlinie

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

##<a name="before-you-begin"></a>Vorbereitung

Zur Ausführung der nächsten Schritte müssen Sie sich in der Skycure-Verwaltungskonsole anmelden.

> [!TIP] 
> Wenn Sie Microsoft Internet Explorer 11 oder Edge verwenden, müssen Sie die Skycure-Verwaltungskonsole möglicherweise im privaten Modus öffnen.

## <a name="to-download-the-ios-app-configuration-policy"></a>Herunterladen der iOS-App-Konfigurationsrichtlinie

1.  Gehen Sie zur [Skycure-Verwaltungskonsole](https://aad.skycure.com).

2.  Geben Sie Ihre **Skycure-Administratoranmeldeinformationen** ein, und klicken Sie dann auf **Continue** (Weiter).

    ![Skycure-Verwaltungskonsolenanmeldung](../media/mtp/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > Der Skycure-Administratorbenutzername ist ein E-Mail-Konto, das eine gültiges Benutzerkonto in Azure Active Directory sein muss, andernfalls schlägt die Anmeldung fehl. Skycure verwendet Azure Active Directory zum Authentifizieren des Administratorbenutzernamens mithilfe von einmaligem Anmelden (SSO).

3.  Wechseln Sie zu **Settings** &gt; **Device Management Integrations** &gt; **EMM Integration Selection** (Einstellungen > Geräteverwaltungsintegrationen > EMM-Integrationsauswahl), wählen Sie **Microsoft Intune** aus, und speichern Sie dann Ihre Auswahl.

2.  Klicken Sie auf den Link **Integration setup files** (Integrationssetupdateien), und speichern Sie die generierte \*.zip-Datei. Die ZIP-Datei enthält die Datei **skycure\_configuration.plist**, die zum Erstellen der iOS-App-Konfigurationsrichtlinie im klassischen Intune-Portal verwendet wird.

![Skycure-Integrationssetupdateien](../media/mtp/skycure-ios-app-2.png)

## <a name="next-steps"></a>Nächste Schritte

[Hinzufügen von Skycure-Apps, der Microsoft Authenticator-App und der iOS-Konfigurationsrichtlinie](/intune-classic/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)
