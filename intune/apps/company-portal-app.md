---
title: Konfigurieren der Unternehmensportal-App
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie unternehmensspezifisches Branding auf die Intune-Unternehmensportal-App anwenden können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7a4d6db4f61dea1b073ccce7c4c3f727a91402c1
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563638"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Konfigurieren der Microsoft Intune-Unternehmensportal-App

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Im Microsoft Intune-Unternehmensportal können Benutzer auf Unternehmensdaten zugreifen, häufige Aufgaben wie das Registrieren von Geräten und das Installieren von Apps ausführen und sich über Unterstützungsmöglichkeiten durch Ihre IT-Abteilung informieren. Darüber hinaus ermöglicht die Unternehmensportal-App Benutzern den sicheren Zugriff auf Unternehmensressourcen. Die Unternehmensportal-App bietet verschiedene Seiten, z. B. „Startseite“, „Apps“, „App-Details“, „Geräte“ und „Gerätedetails“. Um Apps im Unternehmensportal schnell zu finden, können Sie die Apps auf der Seite „Apps“ filtern.

> [!IMPORTANT]
> Zur Unterstützung des Firebase Cloud Messaging (FCM) von Google müssen Sie Ihre Android-Unternehmensportal-App auf die neueste Version aktualisieren.  

> [!Tip]
> Wenn Sie das Unternehmensportal anpassen, gelten die Konfigurationen sowohl für die Unternehmensportal-Website als auch für die Unternehmensportal-Apps. Beachten Sie, dass Benutzern eine Intune-Lizenz zugewiesen werden muss, damit sie auf die Unternehmensportalwebsite zugreifen können.

Durch Anpassen des Unternehmensportals können Sie Ihren Endbenutzern eine vertraute und hilfreiche Benutzeroberfläche bereitstellen. Wählen Sie hierzu im Intune-Portal **Apps** > **Branding und Anpassung** aus, und konfigurieren Sie anschließend die erforderlichen Einstellungen.

Wenn ein Benutzer eine iOS-Anwendung über das Unternehmensportal installiert, wird eine Eingabeaufforderung angezeigt. Dies passiert, wenn die iOS-App mit dem App-Store, einem Volumenlizenzprogramm (Volume-Purchase Program, VPP) oder einer branchenspezifischen App (Line-Of-Business, LOB) verknüpft ist. In der Eingabeaufforderung kann der Benutzer die Aktion akzeptieren oder die Verwaltung der App erlauben. Die Eingabeaufforderung zeigt den Namen Ihres Unternehmens oder – wenn dieser nicht verfügbar ist – den Text **Unternehmensportal** an. 

> [!Note]
> Wenn Sie Azure Government verwenden, werden dem Endbenutzer App-Protokolle angeboten. Er kann nun entscheiden, wie er diese teilen möchte, wenn der er den Prozess zum Abrufen von Hilfe zu einem Problem startet. Wird Azure Government jedoch nicht verwendet, sendet das Unternehmensportal für Windows 10 App-Protokolle direkt an Microsoft, wenn der Benutzer den Prozess zum Abrufen von Hilfe zu einem Problem startet. Das Senden der App-Protokolle an Microsoft erleichtert die Problembehandlung und -behebung. 

## <a name="company-information-and-privacy-statement"></a>Unternehmensinformationen und Datenschutzerklärung
Der Unternehmensname wird als Titel des Unternehmensportals angezeigt. Die Datenschutzerklärung wird angezeigt, wenn ein Benutzer auf den Datenschutzlink klickt.

| Feldname | Max. Länge | Weitere Informationen |
|---|---|---|
|**Firmenname**| 40 | Der Name wird als Titel des Unternehmensportals und auf der Intune-Benutzeroberfläche als Text angezeigt. |
| **URL der Datenschutzerklärung** |     79     | Sie können eine eigene Datenschutzerklärung für Ihr Unternehmen angeben. Diese wird angezeigt, wenn die Benutzer im Unternehmensportal auf die Datenschutzlinks klicken. Sie müssen eine gültige URL im Format `<https://www.contoso.com>` eingeben. |

> [!NOTE]
> In Übereinstimmung mit den Richtlinien von Microsoft und Apple werden die von unserem Dienst gesammelten Daten keinesfalls an Dritte verkauft.

## <a name="support-information"></a>Supportinformationen
Geben Sie die Supportinformationen Ihres Unternehmens ein, um Ihrem Mitarbeiter einen Kontakt für auf Intune bezogene Fragen bereitzustellen.

|Feldname|Max. Länge|Weitere Informationen|
|---|---|---|
|**Kontaktname** | 40 | Dieser Name wird auf der Seite **Hilfe und Support** angezeigt. |
|**Telefonnummer** | 20 | Diese Kontaktnummer wird auf der Seite **Hilfe und Support** angezeigt, damit sich Mitarbeiter an Sie wenden können, wenn sie Unterstützung benötigen. |
|**E-Mail-Adresse**| 40 | Diese Kontaktadresse wird auf der Seite **Hilfe und Support** angezeigt. Sie müssen eine gültige E-Mail-Adresse im Format `alias@domainname.com` eingeben. |
|**Name der Website**| 40 | Dies ist der Anzeigename der URL für die Supportwebsite. Wenn Sie für die Supportwebsite eine URL, aber keinen Anzeigenamen angeben, wird im Unternehmensportal auf der Seite **Hilfe und Support** der Text „Zur IT-Website wechseln“ angezeigt. |
|**Website-URL**| 150 | Wenn Sie über eine Supportwebsite verfügen, die Ihre Benutzer verwenden sollen, geben Sie hier die URL an. Die URL muss das Format `https://www.contoso.com` aufweisen. Wenn Sie keine URL angeben, wird im Unternehmensportal auf der Seite **Hilfe und Support** keine Supportwebsite angezeigt. |
| **Weitere Informationen**| 120 | Werden auf der Seite **Hilfe und Support** angezeigt. |


## <a name="company-identity-branding-customization"></a>Anpassen der Unternehmensmarkenidentität
Sie können Ihr Unternehmensportal mit Ihrem Firmenlogo, Firmennamen, Farbdesign und Hintergrund anpassen.

### <a name="theme-color-and-logo-in-the-company-portal"></a>Farbdesign und Logo im Unternehmensportal
Wenden Sie ein Farbdesign auf das Unternehmensportal an. Wählen Sie eine Standardfarbe aus, oder geben Sie einen sechsstelligen Hexadezimalcode ein, um eine benutzerdefinierte Farbe festzulegen.

|Feldname|Weitere Informationen|
|---|---|
|**Select a standard color or enter a six-digit hex code** (Standardfarbe auswählen oder sechsstelligen Hexadezimalcode eingeben)| Wählen Sie **Standard** aus, um eine angezeigte Farbe auszuwählen. Wählen Sie **Benutzerdefiniert** aus, um eine bestimmte Farbe anhand eines Hexadezimalcodes auszuwählen.|
|**Choose theme color** (Farbdesign auswählen)| Wählen Sie ein Farbdesign aus, das auf das Unternehmensportal angewendet werden soll. Sie können aus einer Standardfarbe auswählen oder einen bestimmten Hexadezimalcode angeben. |
|**Anzeige**| Wählen Sie aus, ob **Unternehmenslogo und -name**, **nur das Unternehmenslogo** oder **nur der Unternehmensname** angezeigt werden soll. |
|**Upload your company logo** (Firmenlogo hochladen)|Sie können Ihr Unternehmenslogo hochladen, damit es im Unternehmensportal angezeigt wird. Beachten Sie, dass die Textfarbe automatisch auf die Option mit dem höchsten Kontrast festgelegt wird. Für die optimale Darstellung laden Sie ein Logo mit transparentem Hintergrund hoch.<p><ul><li>Maximale Bildgröße: 400 x 400 px</li><li>Maximale Dateigröße: 750 KB</li><li>Dateityp: PNG, JPG oder JPEG</li></ul>|

Nachdem Sie das Logo hochgeladen haben, wird das Logo mit dem Farbdesign im Vorschaubereich angezeigt. Wenn Sie den Unternehmensnamen anzeigen möchten, wird dieser in schwarz oder weiß im Unternehmensportal angezeigt. Die Farbe wird anhand des höchsten Kontrasts zur Designfarbe automatisch ausgewählt. Der Unternehmensname wird nicht im Vorschaubereich angezeigt. 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>Logo für die Verwendung auf weißen oder hellen Hintergründen
Wählen Sie ein Logo aus, das auf weißen oder hellen Hintergründen am besten aussieht.

|Feldname|Weitere Informationen|
|---|---|
|**Upload your logo** (Logo hochladen)| Diese Option ist verfügbar, wenn Sie ausgewählt haben, dass das Firmenlogo angezeigt werden soll. Für die optimale Darstellung laden Sie ein Logo mit transparentem Hintergrund hoch.<p><ul><li>Maximale Bildgröße: 400 x 400 px</li><li>Maximale Dateigröße: 750 KB</li><li>Dateityp: PNG, JPG oder JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>Markenbild für das Unternehmensportal

Zeigen Sie ein Markenbild an, das Ihre Unternehmensmarke widerspiegelt. Nachdem Sie Ihre Änderungen gespeichert haben, können Sie im Intune-Webportal im oberen Fensterbereich **Vorschau Ihrer Einstellungen** auswählen, um Ihre Konfiguration zu überprüfen. Beachten Sie, dass Sie das Markenbild nur auf einem iOS-Gerät in der Vorschau anzeigen können und nicht im Intune-Webportal. 

|Feldname|Weitere Informationen|
|---|---|
|**Upload your brand image** (Markenbild hochladen)| Mithilfe dieser Option können Sie ein Markenbild anzeigen. Im iOS-Unternehmensportal wird dieses als Hintergrundbild auf der Profilseite des Benutzers angezeigt.<p><ul><li>Empfohlene Bildbreite: Größer als 1125 px (mindestens 650 px)</li><li>Maximale Bildgröße: 1,3 MB</li><li>Dateityp: PNG, JPG oder JPEG</li></ul>|

Mit einem richtigen Markenbild kann das Vertrauen von Benutzern in das Unternehmensportal gesteigert werden, indem die Identität des Unternehmens aussagekräftig dargestellt wird. Im Folgenden finden Sie einige Tipps, die Sie beim Erwerben, Auswählen und Optimieren des Bilds für das Unternehmensportal beachten sollten. 

- Wenden Sie sich an Ihre Marketing- oder Designabteilung. Möglicherweise verfügt sie bereits über zulässige Markenbilder. Eventuell können sie Sie bei Bedarf auch beim Optimieren der Bilder unterstützen. 

- Beachten Sie die Komposition sowohl im Querformat als auch im Hochformat. Das Bild sollte ausreichend Hintergrundfläche um den Fokus herum aufweisen. Das Bild wird möglicherweise je nach Größe, Ausrichtung und Plattform des Geräts anders zugeschnitten. 

- Vermeiden Sie typische Archivbilder. Das Bild sollte die Marke Ihres Unternehmens widerspiegeln und für Benutzer vertraut wirken. Wenn Sie keines besitzen, ist es besser, keines zu verwenden, anstatt ein allgemeines Bild zu nutzen, das keine Bedeutung für Ihre Benutzer hat. 

- Entfernen Sie unnötige Metadaten. Bilddateien können Metadaten enthalten, z.B. das Kameraprofil, der geografische Standort, Titel, Beschreibung usw. Verwenden Sie ein Bildbearbeitungstool, um diese Informationen zu entfernen, die Qualität beizubehalten und die maximale Dateigröße einzuhalten. 

Nachdem ein Markenbild in Intune hinzugefügt oder geändert wurde, wird dem Endbenutzer auf iOS-Geräten möglicherweise erst eine Änderung angezeigt, wenn das Unternehmensportal die Änderung beim Start erkannt hat und zur Anzeige des Markenbilds neu gestartet wurde. 

### <a name="brand-image-examples"></a>Beispiele für Markenbilder

Die folgende Abbildung zeigt ein iPad-Beispielmarkenbild:

![Screenshot eines iPhone-Beispielmarkenbilds](./media/company-portal-app/company-portal-app-03.png)

Die folgende Abbildung zeigt ein iPhone-Beispielmarkenbild:

![Screenshot eines iPad-Beispielmarkenbilds](./media/company-portal-app/company-portal-app-02.png)

## <a name="privacy-statement-customization"></a>Anpassen der Datenschutzerklärung

Sie können die Datenschutzerklärung anpassen, die für Organisationsgeräte oder verwaltete iOS-Geräte angezeigt wird. In dieser Meldung werden diejenigen Elemente aufgelistet, die Ihre Organisation auf verwalteten iOS-Geräten nicht anzeigen oder ausführen kann.

Unter **Anpassung des Unternehmensportals** > **Meldung zu Geräteverwaltung und Datenschutz** können Sie folgende Aktionen ausführen:

- Sie können die **Standardeinstellung** übernehmen, um die Liste wie angezeigt zu verwenden.
- Sie können **Benutzerdefiniert** auswählen, um die Liste derjenigen Elemente anzupassen, die Ihre Organisation auf verwalteten iOS-Geräten nicht anzeigen oder ausführen kann. Mithilfe von [Markdown](https://daringfireball.net/projects/markdown/) können Sie Aufzählungspunkte, Fett- und Kursivformatierung sowie Links hinzufügen.

## <a name="company-portal-derived-credentials-for-ios-devices"></a>Vom Unternehmensportal abgeleitete Anmeldeinformationen für iOS-Geräte
Intune unterstützt von Personal Identity Verification (PIV) und Common Access Card (CAC) abgeleitete Anmeldeinformationen in Partnerschaft mit den Anmeldeinformationsanbietern DISA Purebred, Entrust Datacard und Intercede. Endbenutzer durchlaufen nach der Registrierung ihres iOS-Geräts weitere Schritte, um ihre Identität in der Unternehmensportalanwendung zu bestätigen. Abgeleitete Anmeldeinformationen werden für Benutzer aktiviert, indem zuerst ein Anmeldeinformationsanbieter für Ihren Mandanten eingerichtet und dann ein Profil als Ziel verwendet wird, das abgeleitete Anmeldeinformationen für Benutzer oder Geräte verwendet.

> [!NOTE]
> Der Benutzer erhält Anweisungen zu abgeleiteten Anmeldeinformationen, die auf dem Link basieren, den Sie über Intune angegeben haben.

Weitere Informationen zu abgeleiteten Anmeldeinformationen für iOS-Geräte finden Sie unter [Verwenden abgeleiteter Anmeldeinformationen in Microsoft Intune](~/protect/derived-credentials.md).

## <a name="dark-mode-for-ios-company-portal"></a>Dunkler Modus für iOS-Unternehmensportal

Der dunkle Modus ist für das iOS-Unternehmensportal verfügbar. Benutzer können Unternehmens-Apps herunterladen, ihre Geräte verwalten und IT-Support im Farbschema Ihrer Wahl basierend auf den Geräteeinstellungen erhalten. Das iOS-Unternehmensportal passt sich automatisch den Einstellungen des Endbenutzergeräts für den hellen oder dunklen Modus an. 

## <a name="windows-company-portal-keyboard-shortcuts"></a>Tastenkombinationen für die Windows-Unternehmensportal-App

Endbenutzer können mithilfe von Tastenkombinationen (Tastenkombinations-Editor) Navigations-, App- und Geräteaktionen in der Windows-Unternehmensportal-App auslösen.

Die folgenden Tastenkombinationen stehen Ihnen in der Windows-Unternehmensportal-App zur Verfügung.

| Bereich | Beschreibung | Tastenkombination |
|:------------------:|:--------------:|:-----------------:|
| Navigationsmenü | Navigation | ALT+M |
|  | Startseite | ALT+H |
|  | Alle Apps | ALT+A |
|  | Installierte Apps | ALT+I |
|  | Senden von Feedback | ALT+F |
|  | Mein Profil | ALT+U |
|  | Einstellung | ALT+T |
| Start – Gerätekachel | Umbenennen | F2 |
|  | Remove | STRG+D oder ENTF-TASTE |
|  | Zugriff prüfen | STRG+M oder F9 |
| Gerätedetails | Umbenennen | F2 |
|  | Remove | STRG+D oder ENTF-TASTE |
|  | Zugriff prüfen | STRG+M oder F9 |
| App-Details | „Installieren“ zu klicken. | STRG+I |
| Geräte | Verfügbar | Strg+D |

Endbenutzer können zudem die verfügbaren Tastenkombinationen in der Windows-Unternehmensportal-App einsehen.

![Screenshot der verfügbaren Tastenkombinationen im Windows-Unternehmensportal](./media/company-portal-app/company-portal-app-01.png)

## <a name="user-self-service-device-actions-from-the-company-portal"></a>Self-Service-Geräteaktionen für Benutzer im Unternehmensportal

Benutzer können über die Unternehmensportal-App oder die Unternehmensportal-Website Aktionen auf ihren lokalen oder Remotegeräten ausführen. Die von Benutzern ausführbaren Aktionen variieren je nach Geräteplattform und -konfiguration. In allen Fällen können Remotegeräteaktionen nur vom primären Benutzer eines Geräts ausgeführt werden.
- **Außerbetriebnahme**: Entfernt das Gerät aus der Intune-Verwaltung. In der Unternehmensportal-App und der Unternehmensportal-Website wird dies als **Entfernen** angezeigt.
- **Zurücksetzen**: Diese Aktion initiiert eine Rücksetzung des Geräts. In der Unternehmensportal-Website wird dies als **Zurücksetzen** angezeigt, in der iOS-Unternehmensportal-App als **Auf Werkseinstellungen zurücksetzen**.
- **Umbenennen**: Diese Aktion ändert den Gerätenamen, der dem Benutzer im Unternehmensportal angezeigt wird. Diese Aktion ändert nur die Liste im Unternehmensportal, nicht den lokalen Gerätenamen.
- **Synchronisieren**: Diese Aktion initiiert das Check-In eines Geräts beim Intune-Dienst. Diese Aktion wird im Unternehmensportal als **Status überprüfen** angezeigt.
- **Remotesperre**: Diese Aktion sperrt das Gerät und erfordert eine PIN zum Entsperren.
- **Passcode zurücksetzen**: Diese Aktion wird zum Zurücksetzen des Passcodes eines Geräts verwendet. Auf iOS-Geräten wird der Passcode entfernt, und der Endbenutzer muss in den Einstellungen einen neuen Code eingeben. Auf unterstützten Android-Geräten wird ein neuer Passcode von Intune generiert und temporär im Unternehmensportal angezeigt.
- **Schlüsselwiederherstellung**: Diese Aktion wird verwendet, um einen persönlichen Wiederherstellungsschlüssel für verschlüsselte macOS-Geräte von der Unternehmensportalwebsite wiederherzustellen. 

### <a name="self-service-actions"></a>Self-Service-Aktionen

Einige Plattformen und Konfigurationen lassen keine Self-Service-Geräteaktionen zu. In der folgenden Tabelle finden Sie weitere Informationen zu Self-Service-Aktionen:

|  | Windows 10<sup>(3)</sup> | iOS/iPadOS<sup>(3)</sup> | MacOS<sup>(3)</sup> | Android<sup>(3)</sup> |
|----------------------|--------------------------|-------------------|-----------------------------------|-------------------------|
| Außerkraftsetzen | Verfügbar<sup>(1)</sup> | Verfügbar | Verfügbar | Verfügbar<sup>(7)</sup> |
| Zurücksetzen | Verfügbar | Verfügbar<sup>(5)</sup> | N/V | Verfügbar<sup>(7)</sup> |
| Umbenennen<sup>(4)</sup> | Verfügbar | Verfügbar | Verfügbar | Verfügbar |
| Synchronisierung | Verfügbar | Verfügbar | Verfügbar | Verfügbar |
| Remotesperre | Nur Windows Phone | Verfügbar | Verfügbar | Verfügbar |
| Passcode zurücksetzen | Nur Windows Phone | Verfügbar<sup>(8)</sup> | N/V | Verfügbar<sup>(6)</sup> |
| Schlüsselwiederherstellung | N/V | N/V | Verfügbar<sup>(2)</sup> | N/V |

<sup>(1)</sup> Die **Außerbetriebnahme** ist auf Windows-Geräten, die Azure AD beigetreten sind, immer blockiert.<br>
<sup>(2)</sup> Die **Schlüsselwiederherstellung** für macOS ist nur über das Webportal verfügbar.<br>
<sup>(3)</sup> Bei Verwendung einer Registrierung über den Geräteregistrierungs-Manager sind alle Remoteaktionen deaktiviert.<br>
<sup>(4)</sup> Durch **Umbenennen** wird nur der Gerätename in der Unternehmensportal-App oder im Webportal geändert, nicht auf dem Gerät selbst.<br>
<sup>(5)</sup> **Löschen** ist auf iOS-Geräten, die vom Benutzer registriert werden, nicht verfügbar.<br>
<sup>(6)</sup> Das **Zurücksetzen von Passcodes** wird in einigen Android- und Android Enterprise-Konfigurationen nicht unterstützt. Weitere Informationen finden Sie unter [Zurücksetzen oder Entfernen eines Gerätepasscodes in Intune](../remote-actions/device-passcode-reset.md).<br>
<sup>(7)</sup> Aktionen für **Außerbetriebnahme** und **Zurücksetzen** sind in Szenarios mit Android Enterprise-Gerätebesitzern (COPE, COBO, COSU) nicht verfügbar.<br> 
<sup>(8)</sup> **Kennung zurücksetzen** wird auf von Benutzern registrierten iOS-Geräten nicht unterstützt.

## <a name="next-steps"></a>Nächste Schritte

- [Manuelles Hinzufügen der Windows 10-Unternehmensportal-App mithilfe von Microsoft Intune](company-portal-app.md)
