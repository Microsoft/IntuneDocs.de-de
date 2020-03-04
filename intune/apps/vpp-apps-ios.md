---
title: Verwalten von Apps aus dem Apple Volume Purchase Program
titleSuffix: Microsoft Intune
description: In diesem Artikel erfahren Sie, wie Sie Apps, die Sie über ein Volumenprogramm im iOS/iPadOS oder macOS App Store erworben haben, in Microsoft Intune synchronisieren und dann deren Nutzung verwalten und nachverfolgen können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e3efa4a354a71846a5add46794ed853696d04560
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216089"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Verwalten von iOS- und macOS-Apps, die über das Apple Volume Purchase Program mit Microsoft Intune erworben wurden


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple bietet Ihnen die Möglichkeit, mithilfe von [Apple Business Manager](https://business.apple.com/) oder [Apple School Manager](https://school.apple.com/) mehrere Lizenzen für eine App zu erwerben, die Sie in Ihrer Organisation auf iOS/iPadOS- und macOS-Geräten verwenden möchten. Anschließend können Sie Ihre Informationen zum Volumenerwerb mit Intune synchronisieren und die Verwendung der im Rahmen des Volumenprogramms erworbenen App verfolgen. Der Erwerb von App-Lizenzen hilft Ihnen, Apps in Ihrem Unternehmen effizient zu verwalten sowie Besitz und Kontrolle über die erworbenen Apps zu behalten. 

Microsoft Intune hilft Ihnen wie folgt beim Verwalten von Apps, die Sie über dieses Programm erworben haben:

- Synchronisieren von Standorttoken, die Sie aus Apple Business Manager herunterladen
- Nachverfolgen, wie viele Lizenzen verfügbar sind und für erworbene Apps im Einsatz sind
- Helfen bei der Installation von Apps bis zur Anzahl der Lizenzen in Ihrem Besitz

Außerdem können Sie mit Intune E-Books, die Sie über Apple Business Manager erworben haben, auf iOS/iPadOS-Geräten synchronisieren, verwalten und zuweisen. Weitere Informationen finden Sie unter [Verwalten von iOS-/iPadOS-E-Books, die über ein Volumenprogramm erworben wurden, mit Microsoft Intune](vpp-ebooks-ios.md).

## <a name="what-are-location-tokens"></a>Was sind Standorttoken?
Standorttoken werden auch als VPP-Token (Volume Purchase Program) bezeichnet. Diese Token dienen zum Zuweisen und Verwalten von Lizenzen, die über Apple Business Manager erworben wurden. Inhalts-Manager können Lizenzen erwerben und Standorttoken zuordnen, für die sie in Apple Business Manager Berechtigungen haben. Diese Standorttoken werden dann über Apple Business Manager heruntergeladen und in Microsoft Intune hochgeladen. Microsoft Intune unterstützt das Hochladen mehrerer Standorttoken pro Mandant. Jedes Token ist ein Jahr lang gültig.

## <a name="how-are-purchased-apps-licensed"></a>Wie werden erworbene Apps lizenziert?
Erworbene Apps können mit zwei Arten von Lizenzen, die Apple für iOS/iPadOS- und macOS-Geräte anbietet, Gruppen zugeordnet werden.

|   | Gerätelizenzierung | Benutzerlizenzierung |
|-----|------------------|----------------|
| **App Store-Anmeldung** | Nicht erforderlich. | Endbenutzer müssen eine eindeutige Apple ID verwenden, wenn sie zur Anmeldung beim App Store aufgefordert werden. |
| **Gerätekonfiguration, die den Zugriff auf den App Store blockiert** | Apps können über das Unternehmensportal installiert und aktualisiert werden. | Die Einladung zur Teilnahme am Apple VPP erfordert Zugriff auf den App Store. Wenn Sie eine Richtlinie zum Deaktivieren des App Store festgelegt haben, funktioniert die Benutzerlizenzierung für VPP-Apps nicht. |
| **Automatisches App-Update** | Wie vom Intune-Administrator in den Einstellungen von Apple VPP-Token konfiguriert, wobei der **Zuweisungstyp** der App **Erforderlich** ist. <br> <br> Wenn der **Zuweisungstyp** auf **Für registrierte Geräte verfügbar** festgelegt ist, können verfügbare App-Updates über das Unternehmensportal installiert werden. | Gemäß der Konfiguration durch den Endbenutzer in persönlichen App Store-Einstellungen. Kann nicht vom Intune-Administrator verwaltet werden. |
| **Benutzerregistrierung** | Nicht unterstützt. | Unterstützt bei Verwenden verwalteter Apple-IDs. |
| **Bücher** | Nicht unterstützt. | Unterstützt. |
| **Verwendete Lizenzen** | 1 Lizenz pro Gerät. Die Lizenz ist dem Gerät zugeordnet. | 1 Lizenz für bis zu 5 Geräte, die dieselbe persönliche Apple-ID verwenden. Die Lizenz ist dem Benutzer zugeordnet. <br> <br> Ein Endbenutzer, der in Intune einer persönlichen Apple-ID und einer verwalteten Apple-ID zugeordnet ist, beansprucht 2 App-Lizenzen.|
| **Lizenzmigration** | Apps können Lizenzen automatisch von Benutzer- zu Gerätelizenzen migrieren. | Apps können nicht von Geräte- zu Benutzerlizenzen migrieren. |

> [!NOTE]  
> Im Unternehmensportal werden keine Apps mit Gerätelizenz unter Geräten mit Benutzerregistrierung angezeigt, da nur Apps mit Benutzerlizenz auf Geräten mit Benutzerregistrierung installiert werden können.

## <a name="what-app-types-are-supported"></a>Welche App-Typen werden unterstützt?
Sie können mit Apple Business Manager öffentliche und private Apps erwerben und verteilen.
- **Store-Apps:** Mit Apple Business Manager können Inhalts-Manager sowohl kostenlose als auch kostenpflichtige im App Store erhältliche Apps kaufen.
- **Benutzerdefinierte Apps:** Mit Apple Business Manager können Inhalts-Manager auch benutzerdefinierte Apps kaufen, die Ihrer Organisation privat bereitgestellt werden. Diese Apps werden von Entwicklern, mit denen Sie direkt zusammenarbeiten, auf die spezifischen Bedürfnisse Ihres Unternehmens abgestimmt. Erfahren Sie mehr über das [Verteilen benutzerdefinierter Apps](https://developer.apple.com/business/custom-apps/).

## <a name="prerequisites"></a>Voraussetzungen
- Ein [Apple Business Manager](https://business.apple.com/)- oder [Apple School Manager](https://school.apple.com/)-Konto für Ihre Organisation 
- Erworbene App-Lizenzen, die einem oder mehreren Standorttoken zugewiesen sind 
- Heruntergeladene Standorttoken 

> [!IMPORTANT]
> - Ein Standorttoken kann immer nur mit einer Geräteverwaltungslösung gleichzeitig verwendet werden. Bevor Sie erworbene Apps mit Intune verwenden, sollten Sie alle vorhandenen Standorttoken widerrufen und entfernen, die mit anderen MDM-Anbietern (Mobile Device Management, Verwaltung mobiler Geräte) verwendet werden. 
> - Ein Standorttoken wird immer nur für einen Intune-Mandanten gleichzeitig unterstützt. Vermeiden Sie die Wiederverwendung desselben Tokens für mehrere Intune-Mandanten.
> - Standardmäßig synchronisiert Intune die Standorttoken zweimal täglich mit Apple. Sie können jedoch in Intune jederzeit eine manuelle Synchronisierung einleiten.
> - Nachdem Sie das Standorttoken in Intune importiert haben, importieren Sie dasselbe Token in keine andere Geräteverwaltungslösung. Andernfalls kann dies zu einem Verlust von Lizenzzuweisung und Benutzerdatensätzen führen.

## <a name="migrate-from-volume-purchase-program-vpp-to-apps-and-books"></a>Migrieren vom Volume Purchase Program (VPP) zu „Apps und Bücher“
Wenn Ihr Unternehmen noch nicht zu Apple Business Manager oder Apple School Manager migriert ist, lesen Sie die [Hinweise von Apple zur Migration zu „Apps und Bücher“](https://support.apple.com/HT208257), bevor Sie mit der Verwaltung erworbener Apps in Intune fortfahren.

> [!IMPORTANT]
> - Migrieren Sie zur Optimierung der Migration nur einen VPP-Einkäufer pro Standort. Wenn jeder Einkäufer zu einem bestimmten Standort migriert, werden alle Lizenzen, ob zugewiesen oder nicht, zu „Apps und Bücher“ verschoben.
> - Löschen Sie nicht das vorhandene VPP-Token der Vorgängerversion in Intune oder Apps und Zuweisungen, die mit dem vorhandenen VPP-Token der Vorgängerversion in Intune verknüpft sind. Diese Aktionen erfordern, dass alle App-Zuweisungen in Intune neu erstellt werden.

Migrieren Sie in Apple Business Manager oder Apple School Manager vorhandene erworbene VPP-Inhalte und -Token wie folgt zu „Apps und Bücher“:

1. Laden Sie VPP-Einkäufer zum Beitritt zu Ihrer Organisation ein, und weisen Sie jeden Benutzer an, einen eindeutigen Standort auszuwählen. 
2. Stellen Sie sicher, dass alle VPP-Einkäufer in Ihrer Organisation Schritt 1 abgeschlossen haben, bevor Sie fortfahren.
3. Überprüfen Sie, ob alle erworbenen Apps und Lizenzen in Apple Business Manager oder Apple School Manager zu „Apps und Bücher“ migriert wurden.
4. Laden Sie das neue Standorttoken herunter, indem Sie zu **Apple Business (oder School) Manager** > **Einstellungen** > **Apps und Bücher** > **Meine Servertoken** wechseln.
5. Aktualisieren Sie das Standorttoken im Admin Center von Microsoft Endpoint Manager, indem Sie zu **Mandantenverwaltung** > **Connectors und Token** > **Apple VPP-Token** navigieren und das Token synchronisieren.

## <a name="upload-an-apple-vpp-or-location-token"></a>Hochladen eines Apple VPP- oder Standorttokens

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
3. Wählen Sie **Mandantenverwaltung** > **Connectors und Token** > **Apple-VPP-Token** aus.
4. Klicken Sie im Bereich mit der Liste der VPP-Token auf **Erstellen**.
5. Geben Sie im Bereich **VPP-Token erstellen** die folgenden Informationen an:
    - **VPP-Tokendatei**: Falls noch nicht geschehen, registrieren Sie sich für Apple Business Manager oder Apple School Manager. Sobald Sie registriert sind, laden Sie das Apple-VPP-Token für Ihr Konto herunter und wählen es hier aus.
    - **Apple-ID:** Geben Sie die verwaltete Apple-ID des Kontos ein, das dem hochgeladenen Konto zugeordnet ist.
    - **Steuerung des Tokens aus anderer MDM-Lösung übernehmen**: Wenn Sie diese Option auf **Ja** festlegen, kann das Token von einer anderen MDM-Lösung zu Intune neu zugewiesen werden.
    - **Tokenname** – ein administratives Feld zum Festlegen des Tokennamens.    
    - **Land/Region**: Wählen Sie den VPP Store für Ihr Land bzw. Ihre Region aus.  Intune synchronisiert VPP-Apps für alle Gebietsschemas aus dem angegebenen VPP Store für das Land oder die Region.
        > [!WARNING]  
        > Wenn Sie das Land oder die Region ändern, werden bei der nächsten Synchronisierung mit dem Apple-Dienst die Metadaten und die App Store-URL für Apps aktualisiert, die mit diesem Token erstellt wurden. Eine App wird nicht aktualisiert, wenn sie in dem neuen Store für das Land bzw. die Region nicht vorhanden ist.

    - **Typ des VPP-Kontos:** Wählen Sie **Unternehmen** oder **Bildungswesen** aus.
    - **Automatische App-Updates**: Mit **On** (Ein) und **Off** (Aus) können Sie automatische Updates aktivieren oder deaktivieren. Wenn diese Option aktiviert ist, erkennt Intune Updates für VPP-Apps in App Store und überträgt diese beim Geräte-Check-In automatisch mithilfe von Push auf das Gerät. 
        
        > [!NOTE] 
        > Automatische App-Updates für Apple VPP-Apps aktualisieren nur die Apps automatisch, die mit der Installationsabsicht **Erforderlich** bereitgestellt wurden. Bei Apps, die mit der Installationsabsicht **Verfügbar** bereitgestellt wurden, generiert das automatische Update eine Statusmeldung für den IT-Administrator, die darüber informiert, dass eine neue Version der App verfügbar ist. Diese Statusmeldung wird angezeigt, wenn Sie die App auswählen, den Geräteinstallationsstatus auswählen und die Statusdetails überprüfen.  

    - **Ich erteilen Microsoft die Berechtigung, sowohl Benutzer- und Geräteinformationen an Apple zu senden.** – Sie müssen **Ich stimme zu** auswählen, um fortzufahren. Informationen dazu, welche Daten Microsoft an Apple sendet, finden Sie unter [Von Intune an Apple gesendete Daten](~/protect/data-intune-sends-to-apple.md).

6. Wenn Sie fertig sind, klicken Sie auf **Erstellen**. Das Token wird im Bereich mit der Liste der Token angezeigt.

## <a name="synchronize-a-vpp-token"></a>Synchronisieren eines VPP-Tokens
Sie können die App-Namen, Metadaten und Lizenzinformationen für Ihre erworbenen Apps in Intune synchronisieren, indem Sie für ein ausgewähltes Token **Synchronisieren** auswählen.

## <a name="assign-a-volume-purchased-app"></a>Zuweisen einer per Volumenlizenz erworbenen App

1. Wählen Sie **Apps** > **Alle Apps** aus.
2. Wählen Sie im Bereich mit der Liste der Apps die App aus, die Sie zuweisen möchten, und klicken Sie dann auf **Zuweisungen**.
3. Klicken Sie im Bereich **App-Name** - **Zuweisungen** auf **Gruppe hinzufügen**. Wählen Sie dann im Bereich **Gruppe hinzufügen** einen **Zuweisungstyp** aus. Anschließend wählen Sie die Azure AD-Benutzer- oder Gerätegruppen aus, denen Sie die App zuweisen möchten.
5. Wählen Sie für jede von Ihnen ausgewählte Gruppe die folgenden Einstellungen aus:
    - **Typ**: Wählen Sie aus, ob die App **verfügbar** (Benutzer können die App vom Unternehmensportal aus installieren) oder **erforderlich** (die App wird automatisch auf Benutzergeräten installiert) sein soll.
    - **Lizenztyp**: Wählen Sie zwischen **Benutzerlizenzierung** oder **Gerätelizenzierung**.
6. Wählen Sie abschließend **Speichern** aus.


>[!NOTE]
>Die Absicht „Verfügbare Bereitstellung“ wird nur für Benutzergruppen unterstützt, nicht für Gerätegruppen. Dies angezeigte App-Liste ist mit einem Token verknüpft. Wenn Sie eine App haben, die mit mehreren VPP-Token verknüpft ist, wird die App mehrmals angezeigt: für jedes Token einmal.

> [!NOTE]  
> Über Intune (oder eine beliebige andere MDM) werden keine VPP-Apps installiert. Stattdessen stellt Intune eine Verbindung mit dem VPP-Konto her und teilt Apple mit, welche App-Lizenzen welchen Geräten zugewiesen werden sollen. Von diesem Punkt aus wird die eigentliche Installation zwischen Apple und dem Gerät verarbeitet.
> 
> [Referenz für das Apple-MDM-Protokoll, Seite 135](https://developer.apple.com/business/documentation/MDM-Protocol-Reference.pdf)

## <a name="end-user-prompts-for-vpp"></a>Benutzeraufforderungen für VPP

Der Benutzer erhält Aufforderungen zur VPP-App-Installation im Zusammenhang mit verschiedenen Szenarios. In der folgenden Tabelle werden die einzelnen Bedingungen erläutert:

| # | Szenario                                | Einladen zum Apple VPP-Programm                              | Aufforderung zur App-Installation | Aufforderung für die Apple-ID |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD: vom Benutzer lizenziert (kein unter „Benutzerregistrierung“ fallendes Gerät)                             | J                                                                                               | J                                           | J                                 |
| 2 | Corp: lizenzierter Benutzer (Gerät wird nicht überwacht)     | J                                                                                               | J                                           | J                                 |
| 3 | Corp: lizenzierter Benutzer (Gerät wird überwacht)         | J                                                                                               | N                                           | J                                 |
| 4 | BYOD: lizenziertes Gerät                           | N                                                                                               | J                                           | N                                 |
| 5 | Corp: lizenziertes Gerät (Gerät wird nicht überwacht)                           | N                                                                                               | J                                           | N                                 |
| 6 | Corp: lizenziertes Gerät (Gerät wird überwacht)                           | N                                                                                               | N                                           | N                                 |
| 7 | Kioskmodus (Gerät wird überwacht): lizenziertes Gerät | N                                                                                               | N                                           | N                                 |
| 8 | Kioskmodus (Gerät wird überwacht): lizenzierter Benutzer   | --- | ---                                          | ---                                |

> [!Note]  
> Es wird nicht empfohlen, VPP-Apps mithilfe der Benutzerlizenzierung Geräten im Kiosk-Modus zuzuweisen.

## <a name="revoking-app-licenses"></a>Widerrufen von App-Lizenzen

Sie können alle zugeordneten iOS/iPadOS- oder macOS-App-Lizenzen des Volume Purchase Program basierend auf einem angegebenen Gerät, einem angegebenen Benutzer oder einer angegebenen App widerrufen.  Es gibt jedoch einige Unterschiede zwischen den Plattformen iOS/iPadOS und macOS. 

|   | iOS/iPadOS | macOS |
|-----|------------------|----------------|
| **Entfernen der App-Zuweisung** | Wenn Sie eine App entfernen, die einem Benutzer zugewiesen war, gibt Intune die Benutzer- oder Gerätelizenz frei und deinstalliert die App auf dem Gerät. | Wenn Sie eine App entfernen, die einem Benutzer zugewiesen war, fordert Intune die Benutzer- oder Gerätelizenz zurück. Die App wird nicht vom Gerät deinstalliert. |
| **Widerrufen einer App-Lizenz** | Durch Widerrufen einer App-Lizenz wird diese vom Benutzer oder Gerät zurückgefordert. Sie müssen die Zuweisung in **Deinstallieren** ändern, um die App vom Gerät zu entfernen. | Durch Widerrufen einer App-Lizenz wird diese vom Benutzer oder Gerät zurückgefordert. Die macOS-App mit der widerrufenen Lizenz kann auf dem Gerät weiter genutzt werden. Sie kann jedoch erst dann wieder aktualisiert werden, wenn dem Gerät oder dem Benutzer wieder eine Lizenz zugewiesen wurde. Laut Apple werden solche Apps nach einem Übergangszeitraum von 30 Tagen entfernt. Apple bietet allerdings keine Möglichkeit, mit der Intune die App mit einer Zuweisungsaktion zum Deinstallieren entfernen könnte.

>[!NOTE]
> - Intune fordert App-Lizenzen zurück, wenn ein Mitarbeiter das Unternehmen verlässt und nicht mehr zu den AAD-Gruppen gehört.
> - Wenn Sie eine erworbene App mit der Absicht  **Deinstallieren** zuweisen, fordert Intune die Lizenz zurück und deinstalliert die App.
> - App-Lizenzen werden nicht zurückgefordert, wenn ein Gerät aus der Intune-Verwaltung entfernt wird. 

## <a name="deleting-vpp-tokens"></a>Löschen von VPP-Token
<!-- 820879 -->  
Sie können ein VPP-Token (Apple Volume Purchase Program) über die Konsole löschen. Dies kann erforderlich sein, wenn doppelte Instanzen eines VPP-Tokens vorliegen. Wenn Sie ein Token löschen, werden auch alle zugehörigen Apps und Zuweisungen gelöscht. Beim Löschen eines Tokens werden App-Lizenzen jedoch nicht widerrufen und es werden keine Apps deinstalliert. 

>[!NOTE]
>Intune kann keine App-Lizenzen widerrufen, nachdem ein Token gelöscht wurde. 

<!-- 820870 -->  
Um die Lizenz aller VPP-Apps für ein bestimmtes VPP-Token zu widerrufen, müssen Sie zunächst alle mit dem Token verknüpften App-Lizenzen widerrufen und anschließend das Token löschen.

## <a name="renewing-app-licenses"></a>Erneuern von App-Lizenzen

Sie können ein Apple VPP-Token erneuern, indem Sie ein neues Token aus Apple Business Manager oder Apple School Manager herunterladen und das vorhandene Token in Intune aktualisieren.

## <a name="deleting-a-vpp-app"></a>Löschen einer VPP-App

Momentan ist es nicht möglich, eine iOS/iPadOS-VPP-App aus Microsoft Intune zu löschen.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Zuweisen von benutzerdefinierten Rollenberechtigungen für VPP

Der Zugriff auf Apple-VPP-Token und VPP-Apps kann unabhängig gesteuert werden: Verwenden Sie hierzu Benutzerberechtigungen, die benutzerdefinierten Administratorrollen in Intune zugewiesen sind.

* Um einer benutzerdefinierten Intune-Rolle die Verwaltung von Apple-VPP-Token zu gestatten, weisen Sie unter **Apps** > **Apple-VPP-Token** Berechtigungen für **Verwaltete Apps** zu.
* Weisen Sie unter **Apps**  >  **Alle Apps** Berechtigungen für **Mobile Apps** zu, um einer benutzerdefinierten Intune-Rolle die Verwaltung von mit iOS/iPadOS-VPP-Token erworbenen Apps zu gestatten. 

## <a name="additional-information"></a>Zusätzliche Informationen

Sie erhalten direkt über Apple Hilfe beim Erstellen und Erneuern von VPP-Token. Weitere Informationen finden Sie unter [Verteilen von Inhalten an Ihre Benutzer mit dem Programm für Volumenlizenzen (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661) in der Apple-Dokumentation. 

Wenn **Externer MDM zugewiesen** im Intune-Portal gekennzeichnet ist, müssen Sie als Administrator das VPP-Token aus der Drittanbieter-MDM entfernen, damit Sie das VPP-Token in Intune verwenden können.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

### <a name="how-many-tokens-can-i-upload"></a>Wie viele Token kann ich hochladen?
Sie können bis zu 3.000 Token in Intune hochladen.

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Wie lange dauert es, bis das Portal die Anzahl der Lizenzen aktualisiert hat, nachdem eine App auf dem Gerät installiert bzw. von diesem entfernt wurde?
Die Lizenz sollte innerhalb weniger Stunden aktualisiert werden, nachdem eine App (de-)installiert wurde. Beachten Sie, dass die Lizenz immer noch dem Endbenutzer des Geräts zugewiesen ist, wenn dieser die App von dem Gerät entfernt.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>Können Apps zu viele Abonnements zugewiesen werden, und wenn ja, wie?
Ja. Der Intune-Administrator kann einer App zu viele Abonnements zuweisen. Dies ist z.B der Fall, wenn der Administrator 100 Lizenzen für die App XYZ erwirbt und dann die App einer Gruppe zuweist, die aus 500 Mitgliedern besteht. Den ersten 100 Mitgliedern (Benutzer oder Geräte) werden dann Lizenzen zugewiesen, den übrigen Mitgliedern hingegen nicht.


## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Überwachen von App-Zuweisungen finden Sie unter [Überwachen von Apps](apps-monitor.md).

Informationen zur Behandlung App-bezogener Probleme finden Sie unter [Problembehandlung bei Apps](~/apps/troubleshoot-app-install.md).
