---
title: "Konfigurieren von Microsoft Intune für einmaliges Anmelden von iOS-Geräten"
titlesuffix: 
description: "Erfahren Sie, wie Sie Microsoft Intune für einmaliges Anmelden von iOS-Geräten konfigurieren."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b11f2b3a560d33503e381f96804bfe5489fe367d
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="configure-microsoft-intune-for-ios-device-single-sign-on"></a>Konfigurieren von Microsoft Intune für einmaliges Anmelden von iOS-Geräten

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Die meisten branchenspezifischen Apps erfordern eine bestimmte Form von Benutzerauthentifizierung, um Sicherheitsfeatures unterstützen zu können. In vielen Fällen muss der Benutzer hierfür die gleichen Anmeldeinformationen mehrfach eingeben, was sich als frustrierend erweisen kann. Zur Verbesserung der Benutzerfreundlichkeit können Entwickler Apps erstellen, die einmaliges Anmelden verwenden. So kann die Häufigkeit reduziert werden, mit der ein Benutzer Anmeldeinformationen angeben muss.

Um einmaliges Anmelden von iOS-Geräten nutzen zu können, müssen folgende Bedingungen erfüllt sein:

- Es muss eine App vorhanden sein, die dafür codiert ist, den Anmeldeinformationsspeicher des Benutzers in der Nutzlast zum einmaligen Anmelden auf dem iOS-Gerät zu durchsuchen.
- Intune muss für einmaliges Anmelden von iOS-Geräten konfiguriert sein.

## <a name="to-configure-intune-for-ios-device-single-sign-on"></a>Konfigurieren von Intune für einmaliges Anmelden von iOS-Geräten


1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3. Wählen Sie auf der Seite **Intune** die Option **Gerätekonfiguration** aus.
2. Wählen Sie auf der Seite **Gerätekonfiguration** die Option **Profile** aus.
3. Wählen Sie auf der Seite „Profile“ die Option **Profil erstellen**, geben Sie einen Namen und eine Beschreibung ein, und konfigurieren Sie die folgenden Einstellungen:
   - **Plattform**: Wählen Sie **iOS**. 
   - **Profiltyp**: Wählen Sie **Gerätefunktionen**.
4. Wählen Sie auf der Seite **Gerätefeatures** die Option **Einmaliges Anmelden** aus.

   ![Seite „Einmaliges Anmelden“](./media/sso-blade.png)

2. Verwenden Sie die folgende Zusammenfassungstabelle, um die Felder in der Seite **Einmaliges Anmelden** auszufüllen. Weitere Informationen finden Sie in den Abschnitten nach der Tabelle.
   
   |Feld  |Hinweise|
   |---------|---------|
   |**Benutzernamensattribut aus AAD**|Das Attribut, nach dem Intune vor Generierung der auf dem Gerät zu installierenden XML-Nutzlast für jeden Benutzer in AAD sucht und das entsprechende Feld (z.B. UPN) auffüllt|
   |**Bereich**|Der Domänenteil der URL|
   |**URL-Präfixe, die einmaliges Anmelden verwenden**|Alle URLs in Ihrer Organisation, für die Benutzer eine Authentifizierung durch einmaliges Anmelden durchführen müssen|
   |**Apps, die einmaliges Anmelden verwenden**|Apps auf dem Gerät des Endbenutzers, die die Nutzlast zum einmaligen Anmelden verwenden|
   |**Zertifikat zum Erneuern der Anmeldeinformationen**|Erfolgt die Authentifizierung anhand von Zertifikaten, wählen Sie als für den Benutzer bereitgestelltes Authentifizierungszertifikat das SCEP- oder PFX-Zertifikat aus.|

Die folgenden Abschnitte enthalten weitere Informationen zu den Feldern bei der einmaligen Anmeldung.

### <a name="username-attribute-from-aad-and-realm"></a>Benutzernamensattribut aus AAD und dem Bereich

- Wenn für dieses Feld **Benutzerprinzipalname** ausgewählt ist, wird es wie folgt analysiert:

   ![Benutzernamensattribut](media/User-name-attribute.png)

   Sie haben auch die Möglichkeit, den Bereich mit dem Text, den Sie in das Textfeld **Bereich** eingeben, zu überschreiben.

   Zum Beispiel könnte Contoso mehrere Teilregionen wie Europa, Asien und Nordamerika umfassen. Möchte Contoso, dass dessen Benutzer in Asien die SSO-Nutzlast verwenden, erfordert die App den UPN im Format *username@asia.contoso.com*. Wenn Sie in diesem Fall **Benutzerprinzipalname** wählen, wird standardmäßig der Bereich für die einzelnen Benutzer aus AAD übernommen, der z.B. einfach *contoso.com* lauten kann. So können Sie insbesondere für Benutzer in Asien diese Nutzlast erstellen und den Bereich mit dem Wert *asia.contoso.com* überschreiben. Daraufhin wird als UPN des Endbenutzers *username@asia.contoso.com* und nicht *username@contoso.com* verwendet.

- Wenn Sie **Geräte-ID** wählen, wählt Intune automatisch die Intune-Geräte-ID aus.

   Standardmäßig müssen Apps lediglich die Geräte-ID verwenden. Wenn Ihre App neben der Geräte-ID jedoch den Bereich verwendet, können Sie den Bereich in das Textfeld **Bereich** eingeben.

   > [!NOTE]
   > Der Bereich sollte standardmäßig leer gelassen werden, wenn Sie die Geräte-ID verwenden.

### <a name="url-prefixes-that-will-use-single-sign-on"></a>URL-Präfixe, die einmaliges Anmelden verwenden

Geben Sie hier alle in Ihrer Organisation vorhandene URLs ein, die eine Benutzerauthentifizierung erfordern.

Wenn ein Benutzer beispielsweise mit einer dieser Websites eine Verbindung herstellt, verwendet das iOS-Gerät die Anmeldeinformationen für einmaliges Anmelden, und der Benutzer muss keine zusätzlichen Anmeldeinformationen eingeben. Wenn Sie jedoch die mehrstufige Authentifizierung aktiviert haben, müssen Benutzer die zweite Authentifizierungsmethode anwenden.

> [!NOTE]
> Bei diesen URLs muss es sich um ordnungsgemäß formatierte FQDNs handeln. Bei Apple müssen diese im Format `http://<yourURL.domain>` sein.

Die URL-Übereinstimmungsmuster müssen entweder mit `http://` oder `https://` beginnen. Es wird ein einfacher Zeichenfolgenabgleich durchgeführt, sodass das URL-Präfix `http://www.contoso.com/` nicht mit `http://www.contoso.com:80/` übereinstimmt. Ab iOS 9.0 kann jedoch ein einzelnes Platzhalterzeichen \* verwendet werden, um alle übereinstimmenden Werte anzugeben. Beispielsweise entspricht `http://*.contoso.com/` sowohl `http://store.contoso.com/` als auch `http://www.contoso.com`.
Die Muster `http://.com` und `https://.com` stimmen mit allen HTTP- bzw. HTTPS-URLs überein.

### <a name="apps-that-will-use-single-sign-on"></a>Apps, die einmaliges Anmelden verwenden

Gibt die Apps auf dem Gerät des Endbenutzers an, die die Nutzlast zum einmaligen Anmelden verwenden

Das `AppIdentifierMatches`-Array muss Zeichenfolgen enthalten, die mit App-Bündel-IDs übereinstimmen. Bei diesen Zeichenfolgen können exakte Übereinstimmungen (z.B. `com.contoso.myapp`) oder Präfixübereinstimmungen der Bundle-ID unter Verwendung des Platzhalterzeichens *\ gefunden werden. Das Platzhalterzeichen muss nach einem Punkt (.) folgen und kann nur einmal am Ende der Zeichenfolge verwendet werden (z.B. `com.contoso.*`). Wenn ein Platzhalter enthalten ist, erhält jede App, deren Bündel-ID mit dem Präfix beginnt, Zugriff auf das Konto.

Das Feld **App-Name** wird verwendet, um einen Anzeigenamen hinzuzufügen, mit dem Sie die Bündel-ID identifizieren können.

### <a name="credential-renewal-certificate"></a>Zertifikat zum Erneuern der Anmeldeinformationen

Wenn Sie Ihre Endbenutzer mit Zertifikaten (nicht mit Kennwörtern) authentifizieren, wählen Sie in diesem Feld das SCEP- oder PFX-Zertifikat aus, das Benutzern als Authentifizierungszertifikat bereitgestellt wird. In der Regel handelt es sich dabei um dasselbe Zertifikat, das dem Benutzer für andere Profile wie VPN, WLAN oder E-Mail bereitgestellt wird.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Konfiguration von Gerätefeatures finden Sie unter [Konfigurieren der Einstellungen für Gerätefunktionen in Microsoft Intune](device-features-configure.md).
