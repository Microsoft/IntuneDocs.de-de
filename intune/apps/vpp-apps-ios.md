---
title: Verwalten von Apps aus dem Apple Volume Purchase Program
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Apps, die Sie über ein Volumenprogramm im iOS oder macOS App Store erworben haben, in Microsoft Intune synchronisieren und dann deren Nutzung verwalten und nachverfolgen können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
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
ms.openlocfilehash: 9625243698bffc93ed969a8c2e4b06b4f3093f4d
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72785531"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Verwalten von iOS- und macOS-Apps, die über das Apple Volume Purchase Program mit Microsoft Intune erworben wurden


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple ermöglicht den Erwerb von mehreren Lizenzen für eine App, die auf iOS- und macOS-Geräten in Ihrem Unternehmen ausgeführt werden soll. Durch den Erwerb mehrerer Kopien können Sie Apps in Ihrem Unternehmen effizient verwalten.

Durch folgende Aktionen unterstützt Microsoft Intune Sie bei der Verwaltung mehrerer Kopien von Apps, die Sie über dieses Programm erworben haben:

- Melden von Lizenzinformationen aus dem App Store
- Nachverfolgen der Anzahl bereits verwendeter Lizenzen
- Verhindern der Installation überzähliger Kopien der App

Es gibt zwei Methoden, die Sie zum Zuweisen von per Volumenlizenz erworbenen Apps verwenden können:

## <a name="device-licensing"></a>Gerätelizenzierung

Wenn Sie eine App einem Gerät zuweisen, wird eine App-Lizenz verwendet, und die Zuordnung dieser App zu diesem Gerät, zu dem Sie sie zugewiesen haben, bleibt erhalten.

Wenn Sie per Volumenlizenz erworbene Apps einem Gerät zuweisen, muss der Endbenutzer des Geräts keine Apple-ID für den Zugriff auf den Store bereitstellen.

## <a name="user-licensing"></a>Benutzerlizenzierung

Wenn Sie einem Benutzer eine App zuweisen, wird eine App-Lizenz für diesen Benutzer verwendet und ihm zugewiesen. Die App kann auf bis zu fünf Geräten des Benutzers ausgeführt werden (das Gerätelimit wird von Apple gesteuert).

Wenn Sie Benutzern eine per Volumenlizenz erworbene App zuweisen, muss jeder Benutzer über eine gültige und eindeutige Apple-ID verfügen, um auf den App Store zugreifen zu können.

Außerdem können Sie Bücher, die Sie im Apple Volume Purchase Program Store (VPP Store) erworben haben, mit Intune auf iOS-Geräten synchronisieren, verwalten und zuweisen. Weitere Informationen finden Sie unter [Verwalten von iOS-E-Books, die über ein Volumenprogramm erworben wurden, mit Microsoft Intune](vpp-ebooks-ios.md).

## <a name="manage-volume-purchased-apps-for-ios-and-macos-devices"></a>Verwalten von per Volumenlizenz erworbenen Apps für iOS- und macOS-Geräte

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps"></a>Unterstützung von Apps, die über das Apple Volume Purchase Program (VPP) erworben wurden

Erwerben Sie mehrere Lizenzen für iOS- und macOS-Apps über das [Apple Volume Purchase Program für Unternehmen](https://www.apple.com/business/vpp/) oder das [Apple Volume Purchase Program für Bildungseinrichtungen](https://volume.itunes.apple.com/us/store). Dieser Vorgang umfasst das Einrichten eines Apple VPP-Kontos auf der Apple-Website und das Hochladen des Apple VPP-Tokens in Intune.  Anschließend können Sie Ihre Informationen zum Volumenerwerb mit Intune synchronisieren und die Verwendung der im Rahmen des Volumenprogramms erworbenen App verfolgen.

### <a name="supports-business-to-business-volume-purchased-apps"></a>Unterstützung von per Volumenlizenz erworbenen B2B-Apps

Drittentwickler können Apps auch privat an autorisierte Mitglieder im Volume Purchase Program für Unternehmen verteilen, die in App Store Connect angegeben sind. Diese Mitglieder des VPP für Unternehmen können sich im VPP-App Store registrieren und ihre Apps dort erwerben. VPP-Apps für Unternehmen, die vom Benutzer erworben werden, werden mit den Intune-Mandanten synchronisiert.

## <a name="before-you-start"></a>Vorbereitung
Bevor Sie beginnen, müssen Sie ein VPP-Token von Apple abrufen und es in Ihr Intune-Konto hochladen. Beachten Sie darüber hinaus die folgenden Kriterien:

* Sie können Ihrem Intune-Konto mehrere VPP-Token zuordnen.
* Wenn Sie zuvor ein VPP-Token für ein anderes Produkt verwendet haben, müssen Sie für die Verwendung mit Intune ein neues erstellen.
* Jedes Token ist ein Jahr lang gültig.
* Standardmäßig wird Intune zweimal täglich mit dem Apple VPP-Dienst synchronisiert. Eine manuelle Synchronisierung können Sie jederzeit starten.
* Bevor Sie Apple VPP mit Intune starten, entfernen Sie alle vorhandenen, mit anderen Anbietern für das mobile Gerätemanagement erstellten VPP-Benutzerkonten. Aus Sicherheitsgründen synchronisiert Intune diese Benutzerkonten nicht. Intune synchronisiert nur Daten aus dem Apple VPP-Dienst, der von Intune erstellt wurde.
* Intune unterstützt bis zu 256 VPP-Token.
* Mit dem Device Enrollment Profile-Programm (DEP) von Apple wird die Registrierung für die mobile Geräteverwaltung automatisiert. Mit DEP können Sie Firmengeräte automatisch synchronisieren. Sie können sich für das DEP-Programm registrieren, indem Sie dasselbe Programm-Agent-Konto verwenden wie für VPP von Apple. Die ID des Deployment Program von Apple ist für alle Programme, die auf der [Apple Deployment Programs](https://deploy.apple.com)-Website aufgelistet werden, eindeutig und kann nicht zur Anmeldung bei Apple-Diensten wie dem iTunes Store verwendet werden.
* Wenn Sie Benutzern oder Geräten mit einem Benutzerlizenzierungsmodell VPP-Apps (mit Benutzeraffinität) zuweisen, muss jeder Intune-Benutzer mit einer eindeutigen Apple-ID oder einer E-Mail-Adresse verknüpft sein, wenn er die allgemeinen Geschäftsbedingungen von Apple auf ihrem Gerät akzeptiert.
* Achten Sie beim Einrichten eines Geräts für einen neuen Intune-Benutzer darauf, dass Sie es mit der eindeutigen Apple-ID oder der E-Mail-Adresse des Benutzers konfigurieren. Die Apple-ID bzw. E-Mail-Adresse und der Intune-Benutzer sind ein eindeutiges Paar, das auf bis zu fünf Geräten verwendet werden kann.
* Sie können ein VPP-Token nur mit einem Intune-Konto gleichzeitig verwenden. Verwenden Sie nicht das gleiche VPP-Token für mehrere Intune-Mandanten gleichzeitig.

>[!IMPORTANT]
>Nachdem Sie den VPP-Token in Intune importiert haben, importieren Sie denselben Token in keine andere Geräteverwaltungslösung. Andernfalls kann dies zu einem Verlust von Lizenzzuweisung und Benutzerdatensätzen führen.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>So können Sie einen Apple VPP-Token abrufen und hochladen

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** unter **Setup** die Option **Client-Apps** > **Apple-VPP-Token** aus.
4. Klicken Sie im Bereich mit der Liste der VPP-Token auf **Erstellen**.
5. Geben Sie im Bereich **VPP-Token erstellen** die folgenden Informationen an:
    - **VPP-Tokendatei**: Wenn Sie dies noch nicht getan haben, registrieren Sie sich für das Volume Purchase Program für Unternehmen oder für Bildungseinrichtungen. Sobald Sie registriert sind, laden Sie das Apple-VPP-Token für Ihr Konto herunter und wählen es hier aus.
    - **Apple-ID:** Geben Sie die Apple-ID des Kontos ein, das dem Programm für Volumenlizenzen zugeordnet ist.
    - **Land/Region**: Wählen Sie den VPP Store für Ihr Land bzw. Ihre Region aus.  Intune synchronisiert VPP-Apps für alle Gebietsschemas aus dem angegebenen VPP Store für das Land oder die Region.
        > [!WARNING]  
        > Wenn Sie das Land oder die Region ändern, werden bei der nächsten Synchronisierung mit dem Apple-Dienst die Metadaten und die Store-URL für Apps aktualisiert, die mit diesem Token erstellt wurden. Eine App wird nicht aktualisiert, wenn sie in dem neuen Store für das Land bzw. die Region nicht vorhanden ist.

    - **Typ des VPP-Kontos:** Wählen Sie **Unternehmen** oder **Bildungswesen** aus.
    - **Automatische App-Updates**: Mit **On** (Ein) und **Off** (Aus) können Sie automatische Updates aktivieren oder deaktivieren. Wenn diese Option aktiviert ist, erkennt Intune Updates für VPP-Apps in App Store und überträgt diese beim Geräte-Check-In automatisch mithilfe von Push auf das Gerät. Automatische App-Updates für Apple VPP-Apps aktualisieren nur die Apps automatisch, die mit der Installationsabsicht **Erforderlich** bereitgestellt wurden. Bei Apps, die mit der Installationsabsicht **Verfügbar** bereitgestellt wurden, generiert das automatische Update eine Statusmeldung für den IT-Administrator, die darüber informiert, dass eine neue Version der App verfügbar ist. Diese Statusmeldung wird angezeigt, wenn Sie die App auswählen, den Geräteinstallationsstatus auswählen und die Statusdetails überprüfen. Darüber hinaus wird dem Benutzer die App als nicht installiert im Unternehmensportal angezeigt, obwohl eine frühere Version der App installiert ist. In diesem Fall kann der Benutzer die App erneut installieren, indem er in der Unternehmensportal-App auf dem Bildschirm mit den Details zur App auf **Installieren** klickt. Damit wird die neuere Version der App installiert.

        > [!NOTE]
        > Für iOS 11.0 und höher oder macOS 10.12 und höher können automatische App-Updates für Apps ausgeführt werden, die für Geräte und Benutzer lizenziert sind.
6. Wenn Sie fertig sind, klicken Sie auf **Erstellen**.

Das Token wird im Bereich mit der Liste der Token angezeigt.

Sie können die von Apple gespeicherten Daten jederzeit mit Intune synchronisieren, indem Sie **Jetzt synchronisieren** wählen.

## <a name="to-assign-a-volume-purchased-app"></a>So weisen Sie per Volumenlizenz erworbene Apps zu

1. Wählen Sie im Bereich **Intune** unter **Verwalten** die Optionen **Client-Apps** > **Apps** aus.
2. Wählen Sie im Bereich mit der Liste der Apps die App aus, die Sie zuweisen möchten, und klicken Sie dann auf **Zuweisungen**.
3. Klicken Sie im Bereich ***App-Name*** - **Zuweisungen** auf **Gruppe hinzufügen**. Wählen Sie dann im Bereich **Gruppe hinzufügen** einen **Zuweisungstyp** aus. Anschließend wählen Sie die Azure AD-Benutzer- oder Gerätegruppen aus, denen Sie die App zuweisen möchten.
5. Wählen Sie für jede von Ihnen ausgewählte Gruppe die folgenden Einstellungen aus:
    - **Typ**: Wählen Sie aus, ob die App **verfügbar** (Benutzer können die App vom Unternehmensportal aus installieren) oder **erforderlich** (die App wird automatisch auf Benutzergeräten installiert) sein soll.
    - **Lizenztyp**: Wählen Sie zwischen **Benutzerlizenzierung** oder **Gerätelizenzierung**.
6. Wählen Sie abschließend **Speichern** aus.


>[!NOTE]
>Die Absicht „Verfügbare Bereitstellung“ wird nur für Benutzergruppen unterstützt, nicht für Gerätegruppen. Dies angezeigte App-Liste ist mit einem Token verknüpft. Wenn Sie eine App haben, die mit mehreren VPP-Token verknüpft ist, wird die App mehrmals angezeigt: für jedes Token einmal.

## <a name="end-user-prompts-for-vpp"></a>Benutzeraufforderungen für VPP

Der Benutzer erhält Aufforderungen zur VPP-App-Installation im Zusammenhang mit verschiedenen Szenarios. In der folgenden Tabelle werden die einzelnen Bedingungen erläutert:

| # | Szenario                                | Einladen zum Apple VPP-Programm                              | Aufforderung zur App-Installation | Aufforderung für die Apple-ID |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD: lizenzierter Benutzer                             | J                                                                                               | J                                           | J                                 |
| 2 | Corp: lizenzierter Benutzer (Gerät wird nicht überwacht)     | J                                                                                               | J                                           | J                                 |
| 3 | Corp: lizenzierter Benutzer (Gerät wird überwacht)         | J                                                                                               | N                                           | J                                 |
| 4 | BYOD: lizenziertes Gerät                           | N                                                                                               | J                                           | N                                 |
| 5 | Corp: lizenziertes Gerät (Gerät wird nicht überwacht)                           | N                                                                                               | J                                           | N                                 |
| 6 | Corp: lizenziertes Gerät (Gerät wird überwacht)                           | N                                                                                               | N                                           | N                                 |
| 7 | Kioskmodus (Gerät wird überwacht): lizenziertes Gerät | N                                                                                               | N                                           | N                                 |
| 8 | Kioskmodus (Gerät wird überwacht): lizenzierter Benutzer   | --- | ---                                          | ---                                |

> [!Note]  
> Es wird davon abgeraten, VPP-Apps Geräten im Kioskmodus zuzuweisen, die die VPP-Benutzerlizenzierung verwenden.

## <a name="revoking-app-licenses"></a>Widerrufen von App-Lizenzen

Sie können alle zugeordneten iOS- oder macOS-App-Lizenzen des Volume Purchase Program basierend auf einem angegebenen Gerät, einem angegebenen Benutzer oder einer angegebenen App widerrufen.  Es gibt jedoch einige Unterschiede zwischen den Plattformen iOS und macOS. 

### <a name="revoking-app-licenses-on-ios"></a>Widerrufen von App-Lizenzen unter iOS
Sie können Benutzer benachrichtigen, wenn ihnen eine App nicht mehr zugewiesen ist. Durch das Widerrufen einer App-Lizenz wird die zugehörige VPP-App jedoch nicht vom Gerät deinstalliert. Um eine VPP zu deinstallieren und eine einem Benutzer oder Gerät zugewiesene App-Lizenz freizugeben, müssen Sie die Zuweisungsaktion auf **Uninstall** (Deinstallieren) festlegen. Wenn Sie eine App entfernen, die einem Benutzer zugewiesen war, gibt Intune die Benutzer- oder Gerätelizenz frei und deinstalliert die App auf dem Gerät. Die Anzahl der widerrufenen Lizenzen wird innerhalb der Intune-**App**-Workload im Knoten **Lizenzierte Apps** angezeigt. Sobald eine VPP-App deinstalliert und die App-Lizenz freigegeben wurde, können Sie die App-Lizenz einem anderen Benutzer oder Gerät zuweisen.


### <a name="revoking-app-licenses-on-macos"></a>Widerrufen von App-Lizenzen unter macOS
Durch das Widerrufen einer App-Lizenz wird die VPP-App nicht vom Gerät deinstalliert. Wenn Sie eine App-Lizenz widerrufen, die einem Benutzer zugewiesen war, gibt Intune die Benutzer- oder Gerätelizenz frei. Die macOS-App mit der widerrufenen Lizenz kann auf dem Gerät weiter genutzt werden. Sie kann jedoch erst dann wieder aktualisiert werden, wenn dem Gerät oder dem Benutzer wieder eine Lizenz zugewiesen wurde. Laut Apple werden solche Apps nach einem Übergangszeitraum von 30 Tagen entfernt. Apple bietet allerdings keine Möglichkeit, mit der Intune die App mit einer Zuweisungsaktion zum **Deinstallieren** entfernen könnte. Sie können die freigegebene App-Lizenz aber einem anderen Benutzer oder Gerät zuweisen.

>[!NOTE]
>Intune ruft sowohl iOS- als auch macOS-VPP-Apps-Lizenzen für den Benutzer ab, wenn ein Mitarbeiter das Unternehmen verlässt und nicht mehr zu den AAD-Gruppen gehört.

## <a name="deleting-vpp-tokens"></a>Löschen von VPP-Token
<!-- 820879 -->  
Sie können ein VPP-Token (Apple Volume Purchase Program) über die Konsole löschen. Dies kann erforderlich sein, wenn doppelte Instanzen eines VPP-Tokens vorliegen. Wenn Sie ein Token löschen, werden auch alle zugehörigen Apps und Zuweisungen gelöscht. Beim Löschen eines Tokens werden App-Lizenzen jedoch nicht widerrufen und es werden keine Apps deinstalliert. 

>[!NOTE]
>Intune kann keine App-Lizenzen widerrufen, nachdem ein Token gelöscht wurde. 

<!-- 820870 -->  
Um die Lizenz aller VPP-Apps für ein bestimmtes VPP-Token zu widerrufen, müssen Sie zunächst alle mit dem Token verknüpften App-Lizenzen widerrufen und anschließend das Token löschen.

## <a name="renewing-app-licenses"></a>Erneuern von App-Lizenzen

Sie können ein Apple VPP-Token erneuern, indem Sie ein neues Token aus dem Apple Volume Purchase Program-Portal herunterladen und das vorhandene Token in Intune aktualisieren.

## <a name="deleting-a-vpp-app"></a>Löschen einer VPP-App

Momentan ist es nicht möglich, eine iOS-VPP-App aus Microsoft Intune zu löschen.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Zuweisen von benutzerdefinierten Rollenberechtigungen für VPP

Der Zugriff auf Apple-VPP-Token und VPP-Apps kann unabhängig gesteuert werden: Verwenden Sie hierzu Benutzerberechtigungen, die benutzerdefinierten Administratorrollen in Intune zugewiesen sind.

* Um einer benutzerdefinierten Intune-Rolle die Verwaltung von Apple-VPP-Token zu gestatten, weisen Sie unter **Client-Apps** > **Apple-VPP-Token** Berechtigungen für **Verwaltete Apps** zu.
* Um einer benutzerdefinierten Intune-Rolle die Verwaltung von mit iOS-VPP-Token erworbenen Apps zu gestatten, weisen Sie unter **Client-Apps** > **Apple-VPP-Token** Berechtigungen für **Mobile Apps** zu. 

## <a name="additional-information"></a>Zusätzliche Informationen

Wenn ein Benutzer mit einem geeigneten Gerät erstmals versucht, eine VPP-App auf einem Gerät zu installieren, wird er aufgefordert, am Volume Purchase Program (VPP) von Apple teilzunehmen. Die Teilnahme muss erfolgen, bevor die App-Installation fortgesetzt wird. Die Einladung zur Teilnahme am Apple Volume Purchase Program erfordert, dass der Benutzer die App Store-App auf dem iOS- oder macOS-Gerät verwenden kann. Wenn Sie eine Richtlinie eingerichtet haben, um die App Store-App zu deaktivieren, funktioniert die benutzerbasierte Lizenzierung für VPP-Apps nicht. Die Lösung besteht darin, die App Store-App durch Entfernen der Richtlinie zuzulassen oder die gerätebasierte Lizenzierung zu verwenden.

Sie erhalten direkt über Apple Hilfe beim Erstellen und Erneuern von VPP-Token. Weitere Informationen finden Sie unter [Verteilen von Inhalten an Ihre Benutzer mit dem Programm für Volumenlizenzen (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661) in der Apple-Dokumentation. 

Wenn **Externer MDM zugewiesen** im Intune-Portal gekennzeichnet ist, müssen Sie als Administrator das VPP-Token aus der Drittanbieter-MDM entfernen, damit Sie das VPP-Token in Intune verwenden können.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Wie lange dauert es, bis das Portal die Anzahl der Lizenzen aktualisiert hat, nachdem eine App auf dem Gerät installiert bzw. von diesem entfernt wurde?
Die Lizenz sollte innerhalb weniger Stunden aktualisiert werden, nachdem eine App (de-)installiert wurde. Beachten Sie, dass die Lizenz immer noch dem Endbenutzer des Geräts zugewiesen ist, wenn dieser die App von dem Gerät entfernt.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>Können Apps zu viele Abonnements zugewiesen werden, und wenn ja, wie?
Ja. Der Intune-Administrator kann einer App zu viele Abonnements zuweisen. Dies ist z.B der Fall, wenn der Administrator 100 Lizenzen für die App XYZ erwirbt und dann die App einer Gruppe zuweist, die aus 500 Mitgliedern besteht. Den ersten 100 Mitgliedern (Benutzer oder Geräte) werden dann Lizenzen zugewiesen, den übrigen Mitgliedern hingegen nicht.

### <a name="how-frequently-does-intune-sync-vpp-tokens-with-apple"></a>Wie häufig synchronisiert Intune VPP-Token mit Apple?
Intune synchronisiert VPP-Token und Lizenzen zweimal täglich mit Apple. Der Intune-Administrator kann unter **Client-Apps** > **Apple-VPP-Token** eine manuelle Synchronisierung initiieren.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Überwachen von App-Zuweisungen finden Sie unter [Überwachen von Apps](apps-monitor.md).
