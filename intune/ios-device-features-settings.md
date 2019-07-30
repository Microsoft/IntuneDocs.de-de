---
title: iOS-Gerätefunktionseinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Schauen Sie sich alle Einstellungen an, um iOS-Geräte für AirPrint, das Layout des Startbildschirms, App-Benachrichtigungen, freigegebene Geräte, einmaliges Anmelden und Webinhaltsfiltereinstellungen in Microsoft Intune zu konfigurieren. Verwenden Sie diese Einstellungen in einem Gerätekonfigurationsprofil, um iOS-Geräte so zu konfigurieren, dass sie diese Apple-Funktionen in Ihrem Unternehmen nutzen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/27/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bac591a625fd915056234a75b26bc2f90f50cae7
ms.sourcegitcommit: 8023ba7d42e61bd37305c69f52a649cf83bf72e2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387106"
---
# <a name="ios-device-settings-to-use-common-ios-features-in-intune"></a>iOS-Geräteeinstellungen zur Verwendung gängiger iOS-Features in Intune

Intune enthält einige eingebaute Einstellungen, damit iOS-Benutzer verschiedene Apple-Funktionen auf ihren Geräten nutzen können. Administratoren können beispielsweise steuern, wie iOS-Benutzer AirPrint-Drucker verwenden, Apps und Ordner zum Dock und zu den Seiten auf dem Startbildschirm hinzufügen, App-Benachrichtigungen anzeigen, Details zu Bestandskennzeichen auf dem Sperrbildschirm anzeigen, Authentifizierung für einmaliges Anmelden verwenden und Benutzer mit Zertifikaten authentifizieren.

Nutzen Sie diese Features, um iOS-Geräte im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) zu verwalten.

In diesem Artikel werden diese Einstellungen mit ihren Funktionsbeschreibungen aufgeführt.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein iOS-Gerätekonfigurationsprofil.](device-features-configure.md#create-a-device-profile)

## <a name="airprint"></a>AirPrint

- **IP-Adresse**: Geben Sie die IPv4- oder IPv6-Adresse des Druckers ein. Wenn Sie den Hostnamen verwenden, um Drucker zu identifizieren, erhalten Sie die IP-Adresse, indem Sie den Drucker am Terminal pingen. Der Abschnitt über das Abrufen von IP-Adresse und Pfad (in diesem Artikel) enthält weitere Details.
- **Pfad**: Der Pfad lautet für Drucker in Ihrem Netzwerk in der Regel `ipp/print`. Der Abschnitt über das Abrufen von IP-Adresse und Pfad (in diesem Artikel) enthält weitere Details.
- **Port**: Geben Sie den Lauschport des AirPrint-Ziels ein. Wenn Sie diese Eigenschaft leer lassen, verwendet AirPrint den Standardport. In iOS 11.0 und höher verfügbar.
- **TLS**: Wählen Sie **Aktivieren** aus, um AirPrint-Verbindungen mit Transport Layer Security (TLS) zu sichern. In iOS 11.0 und höher verfügbar.

Über **Hinzufügen** wird der AirPrint-Server der Liste hinzugefügt. Viele airprint-Server können hinzugefügt werden. Sie können auch eine durch Kommas getrennte Datei (.csv) mit diesen Informationen **importieren**. Beim **Export** wird eine Liste der von Ihnen hinzugefügten airprint-Server erstellt.

Klicken Sie auf **OK**, um Ihre Liste zu speichern.

### <a name="get-server-ip-address-resource-path-and-port"></a>Abrufen der IP-Adresse des Servers, des Ressourcenpfads und Ports

Um AirPrinter-Server hinzuzufügen, benötigen Sie die IP-Adresse des Druckers, den Ressourcenpfad und den Port. Die folgenden Schritte zeigen Ihnen, wie Sie diese Informationen abrufen.

1. Öffnen Sie das **Terminal** auf einem Mac, der mit dem gleichen lokalen Netzwerk (Subnetz) verbunden ist wie die AirPrint-Drucker (über **/Anwendungen/Hilfsprogramme**).
2. Geben Sie im Terminal `ippfind` ein, und wählen Sie „Eingabe“ aus.

    Beachten Sie die Druckerinformationen. Es könnte z.B. `ipp://myprinter.local.:631/ipp/port1` zurückgegeben werden. Der erste Teil ist der Name des Druckers. Der letzte Teil (`ipp/port1`) ist der Pfad der Ressource.

3. Geben Sie im Terminal `ping myprinter.local` ein, und wählen Sie „Eingabe“ aus.

   Beachten Sie die IP-Adresse. Es könnte z.B. `PING myprinter.local (10.50.25.21)` zurückgegeben werden.

4. Verwenden Sie die Werte von IP-Adresse und Ressourcenpfad. In diesem Beispiel ist die IP-Adresse `10.50.25.21` und der Ressourcenpfad `/ipp/port1`.

## <a name="home-screen-layout-settings"></a>Einstellungen des Startbildschirmlayouts

Mit diesen Einstellungen konfigurieren Sie das Layout von Apps und Ordner auf dem iOS-Start- und Dockbildschirm. Um diese Funktion nutzen zu können, müssen sich iOS-Geräte im überwachten Modus befinden und iOS 9.3 oder höher ausführen.

### <a name="dock"></a>Dock

Mit der Einstellung **Dock** können Sie dem Dock des iOS-Bildschirms bis zu sechs Elemente oder Ordner hinzufügen. Viele Geräte unterstützen weniger Elemente. Beispielsweise unterstützen iPhone-Geräte bis zu vier Elemente. In diesem Fall werden nur die ersten vier Elemente, die Sie hinzugefügt haben, auf dem Gerät angezeigt.

Sie können für den Gerätedock bis zu **sechs** Elemente hinzufügen (Apps und Ordner kombiniert).

- **Hinzufügen**: Fügt dem Dock auf dem Gerät Apps oder Ordner hinzu.
- **Typ**: Fügen Sie eine **App** oder einen **Ordner** hinzu:

  - **App**: Wählen Sie diese Option, um Apps zum Dock auf dem Bildschirm hinzuzufügen. Geben Sie folgenden Code ein:

    - **App-Namen**: Geben Sie einen Namen für die app. Dieser Name wird im Azure-Portal zur Referenz verwendet. Er wird *nicht* auf dem iOS-Gerät angezeigt.
    - **App-Bündel-ID**: Geben Sie die Bündel-ID der App ein. Einige Beispiele finden Sie unter [Bündel-IDs für integrierte iOS-Apps](bundle-ids-built-in-ios-apps.md).

    Klicken Sie auf **OK**, um die Änderungen zu speichern.

  - **Ordner**: Wählen Sie diese Option, um einen Ordner zum Dock auf dem Bildschirm hinzuzufügen.

    Apps, die Sie zu einer Seite in einem Ordner hinzufügen, werden von links nach rechts und in der gleichen Reihenfolge wie die Liste angeordnet. Wenn Sie mehr Apps hinzufügen, als auf eine Seite passen, werden die Apps auf eine andere Seite verschoben.

    - **Ordnername**: Geben Sie den Namen des Ordners ein. Dieser Name wird Benutzern auf ihren Geräten angezeigt.
    - **Liste der Seiten**: Wählen Sie **Hinzufügen** aus, und geben Sie die folgenden Eigenschaften ein:

      - **Seitenname**: Geben Sie einen Namen für die Seite. Dieser Name wird im Azure-Portal zur Referenz verwendet. Er wird *nicht* auf dem iOS-Gerät angezeigt.
      - **App-Namen**: Geben Sie einen Namen für die app. Dieser Name wird im Azure-Portal zur Referenz verwendet. Er wird *nicht* auf dem iOS-Gerät angezeigt.
      - **App-Bündel-ID**: Geben Sie die Bündel-ID der App ein. Einige Beispiele finden Sie unter [Bündel-IDs für integrierte iOS-Apps](bundle-ids-built-in-ios-apps.md).

      Sie können für den Gerätedock bis zu **20** Seiten hinzufügen.

    Klicken Sie auf **OK**, um die Änderungen zu speichern.

> [!NOTE]
> Wenn Sie Symbole mithilfe der Dock-Einstellungen hinzufügen, sind die Symbole auf dem Startbildschirm und den Seiten gesperrt und können nicht verschoben werden. Dies kann bei iOS und MDM-Richtlinien von Apple absichtlich der Fall sein.

#### <a name="example"></a>Beispiel

Im folgenden Beispiel zeigt der Dockbildschirm nur die Anwendungen Safari, Mail und Stocks an. Die Mail-App wird ausgewählt, um deren Eigenschaften anzuzeigen:

![Beispiel für iOS-Dockeinstellungen](./media/FfFiUcP.png)

Wenn Sie einem iPhone die Richtlinie zuweisen, sieht der Dock etwa so aus:

![Beispiel für das iOS-Docklayout eines iPhones](./media/bAgCe8F.png)

### <a name="pages"></a>Seiten

Fügen Sie die Seiten hinzu, die auf dem Startbildschirm angezeigt werden sollen, und die Apps, die auf jeder Seite angezeigt werden. Apps, die Sie zu einer Seite hinzufügen, werden von links nach rechts und in der gleichen Reihenfolge wie die Liste angeordnet. Wenn Sie mehr Apps hinzufügen, als auf eine Seite passen, werden die Apps auf eine andere Seite verschoben.

> [!TIP]
> Elemente auf jedem Startbildschirm und auf allen Seiten können Sie mittels Ziehen und Ablegen sortieren.

Sie können bis zu **40** Seiten zu einem Gerät hinzufügen.

- **Liste der Seiten**: Wählen Sie **Hinzufügen** aus, und geben Sie die folgenden Eigenschaften ein:

  - **Seitenname**: Geben Sie einen Namen für die Seite. Dieser Name wird im Azure-Portal zur Referenz verwendet und auf dem iOS-Gerät *nicht* angezeigt.

  Sie können auf einem Gerät bis zu **60** Elemente hinzufügen (Apps und Ordner kombiniert).

  - **Hinzufügen**: Fügt einer Seite auf dem Gerät Apps oder Ordner hinzu.

    - **Typ**: Fügen Sie eine **App** oder einen **Ordner** hinzu:

      - **App**: Verwenden Sie diese Option, um Apps einer Seite auf dem Bildschirm hinzuzufügen. Geben Sie außerdem Folgendes ein:

        - **App-Namen**: Geben Sie einen Namen für die app. Dieser Name wird im Azure-Portal zur Referenz verwendet. Er wird *nicht* auf dem iOS-Gerät angezeigt.
        - **App-Bündel-ID**: Geben Sie die Bündel-ID der App ein. Einige Beispiele finden Sie unter [Bündel-IDs für integrierte iOS-Apps](bundle-ids-built-in-ios-apps.md).

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

      - **Ordner**: Wählen Sie diese Option, um einen Ordner zum Dock auf dem Bildschirm hinzuzufügen.

        Apps, die Sie zu einer Seite in einem Ordner hinzufügen, werden von links nach rechts und in der gleichen Reihenfolge wie die Liste angeordnet. Wenn Sie mehr Apps hinzufügen, als auf eine Seite passen, werden die Apps auf eine andere Seite verschoben.

        - **Ordnername:** Geben Sie einen Namen für den Ordner ein. Dieser Name wird Benutzern auf dem Gerät angezeigt.
        - **Hinzufügen**: Fügt dem Ordner Seiten hinzu. Geben Sie auch die folgenden Eigenschaften ein:

          - **Seitenname**: Geben Sie einen Namen für die Seite. Dieser Name wird im Azure-Portal zur Referenz verwendet. Er wird *nicht* auf dem iOS-Gerät angezeigt.
          - **App-Namen**: Geben Sie einen Namen für die app. Dieser Name wird im Azure-Portal zur Referenz verwendet. Er wird *nicht* auf dem iOS-Gerät angezeigt.
          - **App-Bündel-ID**: Geben Sie die Bündel-ID der App ein. Einige Beispiele finden Sie unter [Bündel-IDs für integrierte iOS-Apps](bundle-ids-built-in-ios-apps.md).

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

#### <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine neue Seite mit dem Namen **Contoso** hinzugefügt. Diese Seite zeigt die Apps „Find Friends“ und „Settings“ an. Die Settings-App wird ausgewählt, um deren Eigenschaften anzuzeigen:

![Beispiel für Einstellungen des iOS-Startbildschirms](./media/Jc2OxyX.png)

Wenn Sie einem iPhone die Richtlinie zuweisen, sieht die Seite etwa so aus:

![iOS-Gerät mit geändertem Startbildschirm](./media/Bd37PHa.png)

## <a name="app-notifications-settings"></a>App-Benachrichtigungseinstellungen

Wählen Sie aus, wie installierte Apps auf iOS-Geräten Benachrichtigungen senden. Diese Einstellungen unterstützen überwachte Geräte, auf denen iOS 9.3 oder höher ausgeführt wird.

- **Hinzufügen**: Hinzufügen von Benachrichtigungen für Apps:

    ![Hinzufügen von App-Benachrichtigungen in einem iOS-Profil in Intune](./media/ios-macos-app-notifications.png)

  - **App-Bündel-ID**: Geben Sie die **App-Bündel-ID** der App ein, die Sie hinzufügen möchten. Einige Beispiele finden Sie unter [Bündel-IDs für integrierte iOS-Apps](bundle-ids-built-in-ios-apps.md).
  - **App-Name**: Geben Sie den Namen der App ein, die Sie hinzufügen möchten. Dieser Name wird im Azure-Portal zur Referenz verwendet. Er wird *nicht* auf dem Gerät angezeigt.
  - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein, die Sie hinzufügen. Dieser Name wird im Azure-Portal zur Referenz verwendet. Er wird *nicht* auf dem Gerät angezeigt.
  - **Benachrichtigungen**: **Aktivieren** oder **deaktivieren** Sie das Senden von Benachrichtigungen von der App an das Gerät.
    - **In Mitteilungszentrale anzeigen**: Mit **Aktivieren** lassen Sie zu, dass Benachrichtigungen der App in der Mitteilungszentrale des Geräts angezeigt werden. **Deaktivieren** Sie diese Option, um zu verhindern, dass Benachrichtigungen in der Mitteilungszentrale angezeigt werden.
    - **In Sperrbildschirm anzeigen**: Wählen Sie **Aktivieren** aus, damit Benachrichtigungen der App auf dem Sperrbildschirm des Geräts angezeigt werden. **Deaktivieren** Sie diese Option, um zu verhindern, dass Benachrichtigungen im Sperrbildschirm angezeigt werden.
    - **Benachrichtigungstyp**: Wählen Sie aus, wie die Benachrichtigung angezeigt wird, wenn das Gerät entsperrt wird. Folgende Optionen sind verfügbar:
      - **Keine**: Es werden keine Benachrichtigungen angezeigt.
      - **Banner**: Es wird kurz ein Banner mit der Benachrichtigung angezeigt.
      - **Modal**: Die Benachrichtigung wird angezeigt, und der Benutzer muss sie manuell schließen, um das Gerät weiter verwenden zu können.
    - **Badge für app-Symbol**: Wählen Sie **aktivieren** so das app-Symbol einen Badge hinzu. Das Badge bedeutet, dass die App eine Benachrichtigung gesendet hat.
    - **Sounds**: Wählen Sie **Aktivieren**, um einen Sound wiederzugeben, wenn eine Benachrichtigung eintrifft.

Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="lock-screen-message-settings"></a>Einstellungen der Sperrbildschirmnachricht

Verwenden Sie diese Einstellungen, um eine benutzerdefinierte Nachricht oder einen Text im Anmeldefenster und auf dem Sperrbildschirm anzuzeigen. So können Sie z.B. eine „Wenn verloren, zurück an“-Nachricht und Bestandskennzeicheninformationen eingeben. 

Dieses Feature unterstützt überwachte Geräte, auf denen iOS 9.3 oder höher ausgeführt wird.

- **Bestandskennzeicheninformationen**: Geben Sie Informationen zum Bestandskennzeichen des Geräts ein. Geben Sie beispielsweise `Owned by Contoso Corp` oder `Serial Number: {{serialnumber}}` ein.

  Der von Ihnen eingegebene Text wird im Anmeldefenster und Sperrbildschirm auf dem Gerät angezeigt.

- **Fußnote zum Sperrbildschirm**: Geben Sie einen Hinweis ein, der Ihnen helfen könnte, das Gerät zurückzuerhalten, wenn es verloren geht oder gestohlen wird. Sie können einen beliebigen Text eingeben. Geben Sie zum Beispiel `If found, call Contoso at ...` ein.

  Gerätetoken können auch verwendet werden, um gerätespezifische Informationen zu diesen Feldern hinzuzufügen. Geben Sie zum Beispiel zur Anzeige der Seriennummer `Serial Number: {{serialnumber}}` ein. Auf dem Sperrbildschirm sieht der Text dann in etwa so aus: `Serial Number 123456789ABC`. Achten Sie darauf, bei der Eingabe von Variablen geschweifte Klammern `{{ }}` zu verwenden. [App-Konfigurationstoken](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) umfassen eine Reihe von Variablen, die Sie nutzen können. Zudem können Sie `deviceName` oder einen anderen gerätespezifischen Wert verwenden.

  > [!NOTE]
  > Variablen werden nicht in der Benutzeroberfläche überprüft und beachten die Groß-/Kleinschreibung. Daher gibt es möglicherweise Profile, die mit fehlerhaften Eingaben gespeichert wurden. Wenn Sie beispielsweise `{{DeviceID}}` anstelle von `{{deviceid}}` eingeben, wird die Zeichenfolge anstelle der eindeutigen Geräte-ID angezeigt. Stellen Sie sicher, dass Sie die richtigen Informationen eingeben.

Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="single-sign-on-settings"></a>Einstellungen für einmaliges Anmelden

Die meisten branchenspezifischen Apps erfordern eine bestimmte Form von Benutzerauthentifizierung, um Sicherheitsfeatures unterstützen zu können. Häufig muss der Benutzer bei dieser Art von Authentifizierung die gleichen Anmeldeinformationen mehrfach eingeben. Dies kann frustrierend für Benutzer sein. Um die Benutzerfreundlichkeit zu verbessern, können Entwickler Apps erstellen, die einmaliges Anmelden (SSO) verwenden. Dadurch wird die Anzahl der Male reduziert, die ein Benutzer Anmeldeinformationen eingeben muss.

Um einmaliges Anmelden zu verwenden, achten Sie darauf, dass Sie folgende Anforderungen erfüllen:

- Es muss eine App vorhanden sein, die dafür codiert ist, den Anmeldeinformationsspeicher des Benutzers zum einmaligen Anmelden auf dem Gerät zu durchsuchen.
- Intune muss für einmaliges Anmelden von iOS-Geräten konfiguriert sein.

![Bereich „Einmaliges Anmelden“](./media/sso-blade.png)

- **Benutzernamensattribut aus Azure AD:** Intune sucht für jeden Azure AD-Benutzer nach diesem Attribut. Intune füllt anschließend das entsprechende Feld (z.B. „UPN“) auf, bevor die auf dem Gerät zu installierende XML-Nutzlast generiert wird. Folgende Optionen sind verfügbar:

  - **Benutzerprinzipalname**: Der Benutzerprinzipalname wird wie folgt analysiert:

    ![Benutzernamensattribut](media/User-name-attribute.png)

    Sie können den Bereich auch mit dem Text überschreiben, den Sie in das Textfeld **Bereich** eingeben.

    Beispielsweise verfügt Contoso über mehrere Regionen, wie z.B. Europa, Asien und Nordamerika. Contoso möchte, dass seine Benutzer in Asien das einmalige Anmelden verwenden und der UPN muss laut App im Format `username@asia.contoso.com` vorliegen. Wenn Sie den **Benutzerprinzipalname** auswählen, wird der Bereich für die einzelnen Benutzer aus Azure AD übernommen, z.B. `contoso.com`. Wählen Sie für Benutzer in Asien, also **Benutzerprinzipalname**, und geben Sie `asia.contoso.com` ein. Daraufhin wird für den UPN des Endbenutzers `username@asia.contoso.com` anstelle von `username@contoso.com` verwendet.

  - **Intune-Geräte-ID**: Intune wählt die Intune-Geräte-ID automatisch aus.

    Standardmäßig müssen Apps lediglich die Geräte-ID verwenden. Wenn Ihre App den Bereich und die Geräte-ID verwendet, können Sie den Bereich in das Textfeld „Bereich“ eingeben.

    > [!NOTE]
    > Der Bereich sollte standardmäßig leer gelassen werden, wenn Sie die Geräte-ID verwenden.

  - **Azure AD-Geräte-ID**

- **Bereich**: Geben Sie den Domänenteil der URL ein. Geben Sie beispielsweise `contoso.com` ein.
- **URL prefixes that will use Single Sign On** (URL-Präfixe, die Single Sign-On verwenden): **Fügen**Sie alle URLs in Ihrer Organisation hinzu, für die Benutzer eine Single Sign-On-Authentifizierung durchführen müssen.

  Wenn ein Benutzer beispielsweise mit einer dieser Websites eine Verbindung herstellt, verwendet das iOS-Gerät die Anmeldeinformationen für Single Sign-On. Der Benutzer muss keine zusätzlichen Anmeldeinformationen eingeben. Wenn Sie die mehrstufige Authentifizierung aktiviert haben, müssen Benutzer die zweite Authentifizierungsmethode anwenden.

  > [!NOTE]
  > Bei diesen URLs muss es sich um ordnungsgemäß formatierte FQDNs handeln. Bei Apple müssen diese im Format `http://<yourURL.domain>` sein.

  Die URL-Übereinstimmungsmuster müssen entweder mit `http://` oder `https://` beginnen. Es wird ein einfacher Zeichenfolgenabgleich ausgeführt, sodass das URL-Präfix `http://www.contoso.com/` nicht mit `http://www.contoso.com:80/` übereinstimmt. Ab iOS 10.0 oder höher kann ein einzelnes Platzhalterzeichen (\*) verwendet werden, um alle übereinstimmenden Werte anzugeben. Beispielsweise entspricht `http://*.contoso.com/` sowohl `http://store.contoso.com/` als auch `http://www.contoso.com`.

  Die Muster `http://.com` und `https://.com` stimmen mit allen HTTP- bzw. HTTPS-URLs überein.

- **Apps, die Single Sign-On verwenden:** **Fügen Sie Apps auf Endbenutzergeräten hinzu, die Single Sign-On verwenden können**.

  Das `AppIdentifierMatches`-Array muss Zeichenfolgen enthalten, die mit App-Bündel-IDs übereinstimmen. Bei diesen Zeichenfolgen kann es sich um exakte Übereinstimmungen (z.B. `com.contoso.myapp`) handeln. Sie können aber auch Präfixübereinstimmungen der Bündel-ID unter Verwendung des Platzhalterzeichens \* angeben. Das Platzhalterzeichen muss nach einem Punkt (.) folgen und kann nur einmal am Ende der Zeichenfolge verwendet werden (z.B. `com.contoso.*`). Wenn ein Platzhalter enthalten ist, erhält jede App, deren Bündel-ID mit dem Präfix beginnt, Zugriff auf das Konto.

  Verwenden Sie den **App-Namen** als benutzerfreundlichen Namen, um die Bündel-ID einfacher identifizieren zu können.

- **Zertifikat zum Erneuern der Anmeldeinformationen**: Erfolgt die Authentifizierung anhand von Zertifikaten (nicht Kennwörtern), wählen Sie als Authentifizierungszertifikat das vorhandene SCEP- oder PFX-Zertifikat aus. In der Regel handelt es sich dabei um dasselbe Zertifikat, das dem Benutzer für andere Profile wie VPN, WLAN oder E-Mail bereitgestellt wird.

Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="web-content-filter-settings"></a>Filtereinstellungen für Webinhalt

Diese Einstellungen steuern den Browser-URL-Zugriff auf überwachten iOS-Geräten.

- **Filtertyp**: Wählen, ob bestimmte Websites zugelassen werden sollen. Folgende Optionen sind verfügbar:

  - **URLs konfigurieren**: Verwenden Sie den integrierten Webfilter von Apple, der nach nicht jugendfreien Inhalten wie Anzüglichkeiten oder Obszönitäten sucht. Diese Funktion wertet jede Webseite beim Laden aus und identifiziert und blockiert ungeeignete Inhalte. Sie können auch URLs hinzufügen, die nicht vom Filter überprüft werden sollen. Alternativ können bestimmte URLs blockiert werden, unabhängig von den Apple-Filtereinstellungen.

    - **Zulässige URLs**: **Fügen** Sie die URLs hinzu, die Sie zulassen möchten. Diese URLs umgehen den Apple-Webfilter.

      > [!NOTE]
        > Die eingegebene URLs sind die URLs, die Sie nicht vom Apple-Webfilter überprüfen lassen möchten. Diese URLs sind keine Liste der zulässigen Websites. Um eine Liste der zulässigen Websites zu erstellen, legen Sie **Filtertyp** auf **Nur bestimmte Websites** fest.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

    - **Blockierte URLs**: Verwenden Sie **Hinzufügen**, um die URLs hinzuzufügen, die Sie unabhängig von den Einstellung für den Apple-Webfilter nicht öffnen möchten.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

  - **Nur bestimmte Websites** (nur für den Safari-Webbrowser): Diese URLs werden zu den Lesezeichen des Safari-Browsers hinzugefügt. Benutzer dürfen **nur** diese Websites besuchen, der Zugriff auf andere Websites ist nicht möglich. Verwenden Sie diese Option nur, wenn Sie genau wissen, auf welche URLs Benutzer zugreifen können.

    - **URL**: Geben Sie die URL der Website ein, die Sie zulassen möchten. Geben Sie beispielsweise `https://www.contoso.com` ein.
    - **Pfad als Lesezeichen**: Geben Sie den Pfad zum Speichern des Lesezeichens. Geben Sie beispielsweise `/Contoso/Business Apps` ein. Wenn Sie keinen Pfad angeben, wird das Lesezeichen zum Standardordner für Lesezeichen auf dem Gerät hinzugefügt.
    - **Titel**: Geben Sie einen beschreibenden Titel für das Lesezeichen ein.

    Wenn Sie keine URLs eingeben, können Endbenutzer nur auf `microsoft.com`, `microsoft.net` und `apple.com` zugreifen. Diese URLs werden von Intune automatisch zugelassen.

    Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="wallpaper-settings"></a>Hintergrundbild-Einstellungen

Fügen Sie ein benutzerdefiniertes PNG-, JPG- oder JPEG-Bild auf Ihren überwachten iOS-Geräten hinzu. Verwenden Sie z.B. ein Unternehmenslogo auf dem Sperrbildschirm.

Möglicherweise kommt es zu unerwartetem Verhalten, wenn ein Profil ohne Bild einem Gerät mit einem Bild zugewiesen wird. Angenommen, Sie erstellen z.B. ein Profil ohne Bild. Dieses Profil wird dann Geräten zugewiesen, für die bereits Bilder vorhanden sind. In diesem Szenario ändert sich das Bild möglicherweise in den Gerätestandard, oder es wird weiter das ursprüngliche Bild auf dem Gerät verwendet. Dieses Verhalten wird von der MDM-Plattform von Apple kontrolliert und eingeschränkt.

- **Position für die Anzeige des Hintergrundbilds**: Wählen Sie die Position auf dem Gerät, an dem das Bild angezeigt werden soll. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**: ein benutzerdefiniertes Image wird nicht auf dem Gerät hinzugefügt. Das Gerät nutzt den Standard des Betriebssystems.
  - **Sperrbildschirm**: Hinzufügen des Images auf dem Sperrbildschirm angezeigt.
  - **Home-Bildschirm**: Hinzufügen des Images an die Startseite.
  - **Sperrbildschirm und Startbildschirm**:Verwendet das gleiche Bild auf dem Sperr- und dem Startbildschirm.
- **Hintergrundbild**: Laden Sie ein vorhandenes PNG-, JPG- oder JPEG-Bild hoch, das Sie verwenden möchten. Achten Sie darauf, dass die Dateigröße kleiner als 750 KB ist. Sie können ein hinzugefügtes Bild auch **entfernen**.

> [!TIP]
> Um verschiedene Bilder auf dem Sperrbildschirm und dem Startbildschirm anzuzeigen, erstellen Sie ein Profil mit dem Sperrbildschirmbild. Erstellen Sie ein anderes Profil mit dem Startbildschirmbild. Fügen Sie beide Profile zu Ihren iOS-Benutzer- oder Gerätegruppen hinzu.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Sie können auch Gerätefunktionsprofile für [macOS](macos-device-features-settings.md)-Geräte erstellen.
