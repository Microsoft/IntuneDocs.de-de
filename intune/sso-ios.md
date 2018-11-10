---
title: Hinzufügen von Single Sign-On für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Sie können mit Microsoft Intune Single Sign-On (SSO) für iOS-Geräte anstelle der Authentifizierung über ein Kennwort für den Zugriff auf die Ressourcen und Daten Ihrer Organisation erstellen, konfigurieren, aktivieren bzw. zulassen. Wenn Sie SSO verwenden möchten, erstellen Sie ein Gerätekonfigurationsprofil, und geben Sie den UPN, die Geräte-ID, Ihre Apps und ein Zertifikat an, um den Benutzer und das Gerät zu authentifizieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d1add113222c2aa7eaea10679c329e877b1a136f
ms.sourcegitcommit: 437eaf364c3b8a38d294397310c770ea4d8a8015
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "49992008"
---
# <a name="use-single-sign-on-ios-device-in-microsoft-intune"></a>Verwenden eines iOS-Geräts für Single Sign-On in Microsoft Intune

Die meisten branchenspezifischen Apps erfordern eine bestimmte Form von Benutzerauthentifizierung, um Sicherheitsfeatures unterstützen zu können. Häufig muss der Benutzer bei dieser Art von Authentifizierung die gleichen Anmeldeinformationen mehrfach eingeben. Dies kann frustrierend sein. Zur Verbesserung der Benutzerfreundlichkeit können Entwickler Apps erstellen, die Single Sign-On verwenden. Dadurch muss der Benutzer die Anmeldeinformationen weniger häufig eingeben.

In diesem Artikel erfahren Sie, wie Sie mithilfe eines Gerätekonfigurationsprofils in Microsoft Intune Single Sign-On für iOS-Geräte aktivieren können.

## <a name="before-you-begin"></a>Vorbereitung

Sie müssen über eine App verfügen, die dafür codiert ist, den Anmeldeinformationsspeicher des Benutzers in der SSO-Nutzlast auf dem iOS-Gerät zu durchsuchen.

## <a name="create-the-sso-profile"></a>Erstellen des SSO-Profils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen Profilnamen ein, z.B. `ios sso profile`.
    - **Beschreibung:** Geben Sie eine Beschreibung mit Schlüsselbegriffen ein, um das Profil in der Liste leichter finden zu können.
    - **Plattform**: Wählen Sie **iOS**.
    - **Profiltyp**: Wählen Sie **Gerätefunktionen**.

4. Klicken Sie auf **Single Sign-On**.

    ![Bereich „Einmaliges Anmelden“](./media/sso-blade.png)

5. Legen Sie folgende Einstellungen fest: 

    - **Benutzernamensattribut aus Azure AD:** Intune sucht für jeden Azure AD-Benutzer nach diesem Attribut. Intune füllt anschließend das entsprechende Feld (z.B. „UPN“) auf, bevor die auf dem Gerät zu installierende XML-Nutzlast generiert wird. Folgende Optionen sind verfügbar:
    
        - **Benutzerprinzipalname:** Der Benutzerprinzipalname wird wie folgt analysiert:

            ![Benutzernamensattribut](media/User-name-attribute.png)

            Sie können den Bereich auch mit dem Text überschreiben, den Sie in das Textfeld **Bereich** eingeben.

            Zum Beispiel könnte Contoso mehrere Teilregionen wie Europa, Asien und Nordamerika umfassen. Möchte Contoso, dass die Benutzer in Asien die SSO-Nutzlast verwenden, verlangt die App den UPN im Format `username@asia.contoso.com`. Wenn Sie in diesem Fall auf **Benutzerprinzipalname** klicken, wird standardmäßig der Bereich für die einzelnen Benutzer aus Azure AD übernommen, z.B. *contoso.com*. So können Sie insbesondere für Benutzer in Asien diese Nutzlast erstellen und den Bereich mit dem Wert *asia.contoso.com* überschreiben. Daraufhin wird für den UPN des Endbenutzers username@asia.contoso.com anstelle von username@contoso.com verwendet.

        - **Intune-Geräte-ID:** Intune wählt die Intune-Geräte-ID automatisch aus. 

            Standardmäßig müssen Apps lediglich die Geräte-ID verwenden. Wenn Ihre App den Bereich *und* die Geräte-ID verwendet, können Sie den Bereich in das Textfeld **Bereich** eingeben.

            > [!NOTE]
            > Der Bereich sollte standardmäßig leer gelassen werden, wenn Sie die Geräte-ID verwenden.

    - **Bereich:** der Domänenteil der URL.
    
    - **URL prefixes that will use Single Sign On** (URL-Präfixe, die Single Sign-On verwenden): **Fügen**Sie alle URLs in Ihrer Organisation hinzu, für die Benutzer eine Single Sign-On-Authentifizierung durchführen müssen. 

        Wenn ein Benutzer beispielsweise mit einer dieser Websites eine Verbindung herstellt, verwendet das iOS-Gerät die Anmeldeinformationen für Single Sign-On. Der Benutzer muss keine zusätzlichen Anmeldeinformationen eingeben. Wenn Sie jedoch die mehrstufige Authentifizierung aktiviert haben, müssen Benutzer die zweite Authentifizierungsmethode anwenden.

        > [!NOTE]
        > Bei diesen URLs muss es sich um ordnungsgemäß formatierte FQDNs handeln. Bei Apple müssen diese URLs im Format `http://<yourURL.domain>` angegeben sein.

        Die URL-Übereinstimmungsmuster müssen entweder mit `http://` oder `https://` beginnen. Es wird ein einfacher Zeichenfolgenabgleich durchgeführt, sodass das URL-Präfix `http://www.contoso.com/` nicht mit `http://www.contoso.com:80/` übereinstimmt. Ab iOS 10.0 oder höher kann jedoch ein einzelnes Platzhalterzeichen (\*) verwendet werden, um alle übereinstimmenden Werte anzugeben. Beispielsweise entspricht `http://*.contoso.com/` sowohl `http://store.contoso.com/` als auch `http://www.contoso.com`.

        Die Muster `http://.com` und `https://.com` stimmen mit allen HTTP- bzw. HTTPS-URLs überein.
    
    - **Apps, die Single Sign-On verwenden:** **Fügen Sie Apps auf Endbenutzergeräten hinzu, die Single Sign-On verwenden können**. 

        Das `AppIdentifierMatches`-Array muss Zeichenfolgen enthalten, die mit App-Bündel-IDs übereinstimmen. Bei diesen Zeichenfolgen kann es sich um exakte Übereinstimmungen (z.B. `com.contoso.myapp`) handeln. Sie können aber auch Präfixübereinstimmungen der Bündel-ID unter Verwendung des Platzhalterzeichens \* angeben. Das Platzhalterzeichen muss nach einem Punkt (.) folgen und kann nur einmal am Ende der Zeichenfolge verwendet werden (z.B. `com.contoso.*`). Wenn ein Platzhalter enthalten ist, erhält jede App, deren Bündel-ID mit dem Präfix beginnt, Zugriff auf das Konto.

        Verwenden Sie den **App-Namen** als benutzerfreundlichen Namen, um die Bündel-ID einfacher identifizieren zu können.
    
    - **Credential renewal certificate** (Zertifikat zum Erneuern der Anmeldeinformationen): Erfolgt die Authentifizierung anhand von Zertifikaten anstelle von Kennwörtern, wählen Sie als für den Benutzer bereitgestelltes Authentifizierungszertifikat das SCEP- oder das PFX-Zertifikat aus. In der Regel handelt es sich dabei um dasselbe Zertifikat, das dem Benutzer für andere Profile wie VPN, WLAN oder E-Mail bereitgestellt wird.

6. Klicken Sie auf **OK** > **OK** > **Erstellen**, um Ihre Änderungen zu speichern und das Profil zu erstellen. Sobald das Profil erstellt wurde, wird es in der Liste **Device configuration - profiles** (Gerätekonfiguration: Profile) angezeigt. 

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Konfiguration von Gerätefeatures finden Sie unter [Konfigurieren der Einstellungen für Gerätefunktionen in Microsoft Intune](device-features-configure.md).

[Weisen Sie dieses Profil Ihren iOS-Geräten zu](device-profile-assign.md).
