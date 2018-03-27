---
title: Zulässige und blockierte Apps für KNOX
description: Benutzerdefiniertes Profil, um eine Liste der zulässigen und blockierten Apps für KNOX zu erstellen.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/02/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a47e1388f640f96c2650e284ae0a5311fd816ba7
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Verwenden von benutzerdefinierten Richtlinien zum Zulassen und Blockieren von Apps für Samsung KNOX Standard-Geräte

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Verwenden Sie die Verfahren in diesem Thema, um eine benutzerdefinierte Microsoft Intune-Richtlinie zu erstellen, die eine der folgenden Listen erstellt:

- Eine Liste von Apps, deren Ausführung auf dem Gerät blockiert wird. Die Ausführung der Apps in dieser Liste wird blockiert, auch wenn diese bereits vor der Anwendung der Richtlinie installiert waren.
- Eine Liste von Apps, die Benutzer des Geräts aus dem Google Play Store installieren dürfen. Nur die aufgelisteten Apps können installiert werden. Es können keine anderen Apps aus dem Store installiert werden.

Diese Einstellungen können nur von Geräten verwendet werden, auf denen Samsung KNOX Standard ausgeführt wird.

## <a name="to-create-an-allowed-or-blocked-app-list"></a>So erstellen Sie eine Liste mit zulässigen oder blockierten Apps

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) die Optionen **Richtlinie** &gt; **Konfigurationsrichtlinien** &gt; **Hinzufügen**.
2. Erweitern Sie im Dialogfeld **Neue Richtlinie erstellen** **Android**, wählen Sie **Benutzerdefinierte Konfiguration** und anschließend **Richtlinie erstellen** aus.
3. Geben Sie einen Namen und optional eine Beschreibung für die Richtlinie an, und wählen Sie anschließend im Abschnitt **OMA-URI-Einstellungen** **Hinzufügen** aus.
4. Geben Sie im Dialogfeld **OMA-URI-Einstellung hinzufügen oder bearbeiten** Folgendes an: Für eine Liste von Apps, deren Ausführung auf dem Gerät blockiert wird:
    
    - **Name der Einstellung.** Geben Sie **PreventStartPackages** ein.
    - **Beschreibung der Einstellung.** Geben Sie optional eine Beschreibung wie z.B. „Liste der Apps, deren Ausführung blockiert wird“ ein.
    -   **Datentyp.** Wählen Sie in der Dropdownliste **Zeichenfolge** aus.
    -   **OMA-URI.** Geben Sie **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages** ein.
    -   **Wert.** Geben Sie eine Liste mit den Namen der App-Pakete ein, die Sie blockieren möchten. Sie können **; : ,** oder **|** als Trennzeichen verwenden. (Beispiel: Paket1; Paket2;)

    Für eine Liste von Apps, die Benutzer des Geräts aus Google Play Store installieren dürfen, wobei alle anderen Apps ausgeschlossen werden:

    - **Name der Einstellung.** Geben Sie **AllowInstallPackages** ein.
    - **Beschreibung der Einstellung.** Geben Sie optional eine Beschreibung wie z.B. „Liste der Apps, die Benutzer aus Google Play Store installieren dürfen“ ein.
    - **Datentyp.** Wählen Sie in der Dropdownliste **Zeichenfolge** aus.
    - **OMA-URI.** Geben Sie **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages** ein.
    - **Wert.** Geben Sie eine Liste mit den Namen der App-Pakete ein, die Sie zulassen möchten. Sie können **; : ,** oder **|** als Trennzeichen verwenden. (Beispiel: Paket1; Paket2;)

4. Klicken Sie auf **OK**, und klicken Sie anschließend auf **Richtlinie speichern**. 

>[!TIP]
> Sie finden die Paket-ID einer App, indem Sie im Google Play Store zu der App navigieren. Die Paket-ID ist in der URL der Seite der App enthalten. Die Paket-ID der Microsoft Word-App lautet z.B. **com.microsoft.office.word**.

Die App-Einstellungen werden beim nächsten Einchecken jedes Zielgeräts angewendet.


## <a name="deploy-the-policy"></a>Bereitstellen der Richtlinie

1.  Wählen Sie im Arbeitsbereich **Richtlinie** die Richtlinie aus, die Sie bereitstellen möchten, und klicken Sie dann auf **Bereitstellung verwalten**.

2.  Wählen Sie im Dialogfeld **Bereitstellung verwalten** mindestens eine Gruppe aus, für die die Richtlinie bereitgestellt werden soll. Klicken Sie anschließend auf **Hinzufügen** &gt; **OK**.

 
Wenn Sie eine bereitgestellte Richtlinie auswählen, können Sie weitere Informationen zur Bereitstellung im unteren Teil der Richtlinienliste anzeigen.

### <a name="see-also"></a>Siehe auch
[Einstellungen für Android- und Samsung KNOX-Richtlinien in Microsoft Intune](android-policy-settings-in-microsoft-intune.md)
