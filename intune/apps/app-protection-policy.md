---
title: Übersicht über App-Schutzrichtlinien
titleSuffix: Microsoft Intune
description: Lernen Sie, wie Ihnen App-Schutzrichtlinien von Microsoft Intune helfen, Ihre Unternehmensdaten zu schützen und Datenverluste zu verhindern.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0f36e648c404858332245c5b1b457c9f6824614
ms.sourcegitcommit: 5178aec0244e023e73546f3d10f1a76eaf1f4a3e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2020
ms.locfileid: "76971880"
---
# <a name="app-protection-policies-overview"></a>Übersicht über App-Schutzrichtlinien

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

App-Schutzrichtlinien sind Regeln, die sicherstellen, dass die Daten einer Organisation in einer verwalteten App jederzeit sicher sind und dort verbleiben. Eine Richtlinie kann eine Regel sein, die erzwungen wird, wenn ein Benutzer versucht, auf „unternehmenseigene“ Daten zuzugreifen oder diese zu verschieben. Es kann sich auch um eine Reihe von Aktionen handeln, die nicht zulässig sind oder überwacht werden, wenn sich ein Benutzer in der App befindet. Eine verwaltete App ist eine App, auf die App-Schutzrichtlinien angewendet wurden und die von Intune verwaltet werden kann.

Mit App-Schutzrichtlinien der Verwaltung mobiler Anwendungen (Mobile Application Management, MAM) können Sie die Daten Ihrer Organisation innerhalb einer Anwendung verwalten und schützen. Mit **MAM ohne Geräteregistrierung** (Mobile Application Management Without Enrollment, MAM-WE) kann eine Geschäfts-, Schul- oder Uni-App, die vertrauliche Daten enthält, auf nahezu jedem [Gerät](app-management.md#app-management-capabilities-by-platform) verwaltet werden, auch auf persönlichen Geräten in **BYOD**-Szenarien (Bring Your Own Device). Viele Produktivitäts-Apps, wie z. B. die Microsoft Office-Apps, können über Intune MAM verwaltet werden. Weitere Informationen finden Sie in der offiziellen Liste mit von [Microsoft Intune geschützten Apps](apps-supported-intune-apps.md), die für die Öffentlichkeit verfügbar sind.

## <a name="how-you-can-protect-app-data"></a>Wie Sie Ihre App-Daten schützen können
Ihre Mitarbeiter verwenden mobile Geräte für private und berufliche Aufgaben. Sie möchten einerseits die Produktivität Ihrer Mitarbeiter sicherstellen, möchten andererseits aber Datenverlust verhindern, sei er beabsichtigt oder unbeabsichtigt. Sie sollten außerdem Unternehmensdaten schützen, auf die über Geräte zugegriffen wird, die nicht von Ihnen verwaltet werden.

Sie können Intune-App-Schutzrichtlinien **unabhängig von jeglicher mobilen Geräteverwaltungslösung** verwenden. Diese Unabhängigkeit hilft Ihnen, die Daten Ihres Unternehmens zu schützen, egal, ob Geräte in einer Geräteverwaltungslösung registriert sind oder nicht. Durch die Implementierung von **Richtlinien auf App-Ebene** können Sie den Zugriff auf Unternehmensressourcen einschränken und Daten im Zuständigkeitsbereich der IT-Abteilung halten.

### <a name="app-protection-policies-on-devices"></a>App-Schutzrichtlinien auf Geräten

App-Schutzrichtlinien können für Apps konfiguriert werden, die auf Geräten ausgeführt werden, die folgende Voraussetzungen erfüllen:

- **Bei Microsoft Intune registriert:** In der Regel sind diese Geräte unternehmenseigene Geräte.

- **Bei einer Drittanbieterlösung für die Verwaltung mobiler Geräte (MDM, Mobile Device Management) registriert:** In der Regel sind diese Geräte unternehmenseigene Geräte.

  > [!NOTE]
  > Verwaltungsrichtlinien für mobile Apps sollten nicht in Verbindung mit Verwaltungslösungen für mobile Geräte von Drittanbietern oder sicheren Containerlösungen verwendet werden.

- **Nicht bei einer Lösung für die mobile Geräteverwaltung registriert:** Diese Geräte sind in der Regel eigene Geräte von Mitarbeitern, die nicht in Intune oder anderen MDM-Lösungen verwaltet oder registriert werden.

> [!IMPORTANT]
> Sie können Verwaltungsrichtlinien für mobile Apps für mobile Office-Apps erstellen, die eine Verbindung mit Office 365-Diensten herstellen. Außerdem können Sie den Zugriff auf lokale Exchange-Postfächer schützen, indem Sie Intune-App-Schutzrichtlinien für Outlook für iOS und Android erstellen, die mit hybrider moderner Authentifizierung aktiviert wurden. Bevor Sie dieses Feature verwenden, sollten Sie sicherstellen, dass Sie die [Anforderungen für Outlook für iOS und Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) erfüllen. App-Schutzrichtlinien werden nicht für andere Apps unterstützt, die eine Verbindung mit lokalen Exchange- oder SharePoint-Diensten herstellen.

## <a name="benefits-of-using-app-protection-policies"></a>Vorteile der Verwendung von App-Schutzrichtlinien

Im Folgenden finden Sie die wichtigsten Vorteile von App-Schutzrichtlinien:

- **Schutz Ihrer Unternehmensdaten auf App-Ebene.** Da die Verwaltung von mobilen Apps keine Geräteverwaltung voraussetzt, können Sie Unternehmensdaten auf verwalteten und auf nicht verwalteten Geräten schützen. Bei der Verwaltung wird die Benutzeridentität in den Mittelpunkt gestellt, wodurch sich die Geräteverwaltung erübrigt.

- **Die Produktivität der Endbenutzer wird nicht beeinträchtigt, und Richtlinien werden nicht angewendet, wenn die App in einem privaten Kontext verwendet wird.** Die Richtlinien werden nur auf den beruflichen Kontext angewendet, wodurch Sie die Möglichkeit haben, Unternehmensdaten zu schützen, ohne dass private Daten einbezogen werden.

- **App-Schutzrichtlinien stellen sicher, dass Schutzfunktionen auf App-Ebene vorhanden sind.** Beispielsweise können Sie folgende Aktionen ausführen:
  - Anfordern einer PIN zum Öffnen einer App in einem geschäftlichen Kontext 
  - Steuern des Teilens von Daten zwischen Apps 
  - Verhindern des Speicherns von Unternehmens-App-Daten an einem privaten Speicherort

- **Eine MDM-Lösung stellt zusätzlich zu MAM sicher, dass das Gerät geschützt ist.** So können Sie beispielsweise die Eingabe einer PIN für den Zugriff auf das Gerät anfordern, oder Sie können verwaltete Apps auf dem Gerät bereitstellen. Sie können Apps auch über die MDM-Lösung auf Geräten bereitstellen, um mehr Kontrolle über die App-Verwaltung zu haben.

Es gibt weitere Vorteile bei der Verwendung einer MDM mit App-Schutzrichtlinien, und Unternehmen können App-Schutzrichtlinien sowohl mit als auch ohne MDM gleichzeitig verwenden. Nehmen Sie beispielsweise weinen Mitarbeiter an, der sowohl ein unternehmenseigenes Smartphone als auch seinen privaten Tablet verwendet. Das unternehmenseigene Smartphone wird in einer MDM registriert und von App-Schutzrichtlinien geschützt, während das private Gerät nur von App-Schutzrichtlinien geschützt wird.

Wenn Sie eine MAM-Richtlinie auf den Benutzer anwenden, ohne den Gerätezustand festzulegen, erhält der Benutzer die MAM-Richtlinie sowohl auf dem BYOD-Gerät als auch auf dem mit Intune verwalteten Gerät. Sie können eine MAM-Richtlinie auch basierend auf dem verwalteten Zustand anwenden. Wenn Sie also eine App-Schutzrichtlinie erstellen, wählen Sie in diesem Fall neben **Auf alle App-Typen ausrichten** die Option **Nein** aus. Gehen Sie dann auf eine der folgenden Arten vor:
- Wenden Sie eine weniger strenge MAM-Richtlinie auf mit Intune verwaltete Geräte an, und wenden Sie eine restriktivere MAM-Richtlinie auf nicht bei MDM registrierte Geräte an.
- Wenden Sie eine MAM-Richtlinie nur auf nicht registrierte Geräte an.

## <a name="supported-platforms-for-app-protection-policies"></a>Unterstützte Plattformen für App-Schutzrichtlinien

Intune bietet eine Reihe von Funktionen, die die Installation der erforderlichen Apps auf den Geräten unterstützen, auf denen sie ausgeführt werden sollen. Weitere Informationen finden Sie unter [App-Verwaltungsfunktionen nach Plattform](app-management.md#app-management-capabilities-by-platform).

Die Plattform für Schutzrichtlinien für Intune-Apps ist auf die Plattformunterstützung für mobile Office-Anwendungen für Android- und iOS-Geräte ausgerichtet. Weitere Informationen finden Sie im Abschnitt **Mobile Apps** unter [Systemanforderungen für Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

> [!IMPORTANT]
> Das Intune-Unternehmensportal ist auf dem Gerät erforderlich, damit das Gerät App-Schutzrichtlinien unter Android empfangen kann. Weitere Informationen finden Sie unter [Zugriffsanforderungen für Apps im Intune-Unternehmensportal](../fundamentals/end-user-mam-apps-android.md#access-apps).

## <a name="how-app-protection-policies-protect-app-data"></a>So schützen App-Schutzrichtlinien Ihre App-Daten

### <a name="apps-without-app-protection-policies"></a>Apps ohne App-Schutzrichtlinien

Wenn Apps ohne Einschränkungen verwendet werden, können Unternehmensdaten und private Daten vermischt werden. Unternehmensdaten können damit an Speicherorten wie dem persönlichen Speicher abgelegt oder an Apps außerhalb Ihres Zuständigkeitsbereichs übermittelt werden, was Datenverlust bedeuten würde. Die Pfeile im folgenden Diagramm zeigen die uneingeschränkte Datenverschiebung zwischen sowohl unternehmenseigenen als auch persönlichen Apps sowie zu Speicherorten.

![Darstellung der Datenverschiebung zwischen Apps ohne Richtlinien](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>Datenschutz mit App-Schutzrichtlinien

Mit App-Schutzrichtlinien können Sie verhindern, dass Unternehmensdaten im lokalen Speicher des Geräts gespeichert werden (siehe folgende Abbildung). Außerdem können Sie das Verschieben von Daten in andere Apps einschränken, die nicht durch App-Schutzrichtlinien geschützt sind. Einstellungen für App-Schutzrichtlinien:
- Richtlinien zur Datenverschiebung wie **Kopien von Organisationsdaten speichern** und **Ausschneiden, Kopieren und Einfügen einschränken**.
- Einstellungen von Zugriffsrichtlinien wie **Einfache PIN für den Zugriff erforderlich** und **Ausführen verwalteter Apps auf mit Jailbreak oder Rooting manipulierten Geräten blockieren**.

![Darstellung von Unternehmensdaten, die durch Richtlinien geschützt werden](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>Schutz von Daten mit App-Schutzrichtlinien auf Geräten, die durch eine MDM-Lösung verwaltet werden

Die folgende Abbildung zeigt die Schutzebenen, die durch den gemeinsamen Einsatz von MDM und App-Schutzrichtlinien bereitgestellt werden.

![Die Abbildung zeigt, wie App-Schutzrichtlinien auf BYOD-Geräten funktionieren.](./media/app-protection-policy/app-protection-policies-with-mdm.png)

Die MDM-Lösung bietet einen Mehrwert durch Folgendes:

- Registrieren das Gerät
- Stellt die Apps auf dem Gerät bereit
- Sorgt für kontinuierliche Gerätekonformität und -verwaltung

Die App-Schutzrichtlinien bieten einen Mehrwert durch Folgendes:

- Schutz der Unternehmensdaten vor dem Zugriff durch Verbraucher-Apps und -Dienste
- Anwenden von Einschränkungen, z. B. für *Speichern unter*, *Zwischenablage* oder *PIN*, auf Client-Apps
- Löschen von Unternehmensdaten aus Apps bei Bedarf, ohne die Apps vom Gerät zu entfernen

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>Schutz von Daten mit App-Schutzrichtlinien für Geräte ohne Registrierung

Das folgende Diagramm zeigt, wie die Datenschutzrichtlinien auf App-Ebene ohne MDM funktionieren.

![Die Abbildung zeigt, wie App-Schutzrichtlinien auf Geräten ohne Registrierung (nicht verwalteten Geräten) funktionieren.](./media/app-protection-policy/app-protection-policies-without-mdm.png)

Bei BYOD-Geräten, die nicht in einer MDM-Lösung registriert sind, können App-Schutzrichtlinien dazu beitragen, Unternehmensdaten auf App-Ebene zu schützen.
Es gibt jedoch einige Einschränkungen, die Sie kennen sollten:

- Sie können auf dem Gerät keine Apps bereitstellen. Der Endbenutzer muss die Apps aus dem Store beziehen.
- Sie können auf diesen Geräten keine Zertifikatprofile bereitstellen.
- Sie können auf diesen Geräten keine unternehmensweiten WLAN- und VPN-Einstellungen bereitstellen.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Apps, die mit App-Schutzrichtlinien verwaltet werden können

Jede App, die in das [Intune SDK](../developer/app-sdk.md) integriert oder vom [Intune App Wrapping Tool](../developer/apps-prepare-mobile-application-management.md) umschlossen wurde, kann mithilfe von Intune-App-Schutzrichtlinien verwaltet werden. Weitere Informationen finden Sie in der offiziellen Liste der [durch Microsoft Intune geschützten Apps](apps-supported-intune-apps.md), die mithilfe dieser Tools erstellt wurden und für die öffentliche Nutzung verfügbar sind.

Das Intune SDK-Entwicklungsteam testet und unterstützt aktiv Apps, die mit dem nativen Android-, iOS- (Obj-C, Swift), Xamarin-, Xamarin.Forms- und Cordova-Plattformen erstellt wurden. Während einige Kunden das Intune SDK erfolgreich in andere Plattformen wie React Native und NativeScript integrieren konnten, bieten wir keine expliziten Anleitungen oder Plug-Ins für App-Entwickler, die andere als unsere unterstützten Plattformen verwenden.

Das [Intune SDK](../developer/app-sdk.md) nutzt einige erweiterte moderne Authentifizierungsfunktionen aus den [Azure Active Directory-Authentifizierungsbibliotheken](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (Azure Active Directory Authentication Libraries, ADAL) sowohl für die Erst- als auch Drittanbieterversionen des SDK. Die [Microsoft-Authentifizierungsbibliothek](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries) (Microsoft Authentication Library, MSAL) ist für viele wichtige Szenarien wie die Authentifizierung beim Intune-Dienst für den App-Schutz und den bedingten Start nicht gut geeignet. Da der allgemeine Leitfaden des Identity-Teams von Microsoft darin besteht, für alle Microsoft Office-Apps auf MSAL umzusteigen, wird das [Intune SDK](../developer/app-sdk.md) es letztlich unterstützen müssen, aber derzeit ist keine Unterstützung geplant.

## <a name="end-user-requirements-to-use-app-protection-policies"></a>Anforderungen an die Endbenutzer bei der Verwendung von App-Schutzrichtlinien

Die folgende Liste enthält die Anforderungen, die für Endbenutzer bei der Verwendung von App-Schutzrichtlinien in einer mit Intune verwalteten App erfüllt sein müssen:

- Der Endbenutzer muss über ein Azure Active Directory-Konto (AAD) verfügen. Informationen dazu, wie Sie Intune-Benutzer in Azure Active Directory erstellen, finden Sie unter [Hinzufügen von Benutzern und Gewähren von Administratorrechten für Intune](../fundamentals/users-add.md).

- Dem AAD-Konto des Endbenutzers muss eine Lizenz für Microsoft Intune zugewiesen sein. Informationen zum Zuweisen von Intune-Lizenzen zu Endbenutzern finden Sie unter [Verwalten von Intune-Lizenzen](../fundamentals/licenses-assign.md).

- Der Endbenutzer muss zu einer Sicherheitsgruppe gehören, für die eine App-Schutzrichtlinie gilt. Die gleiche App-Schutzrichtlinie muss für die verwendete App gelten. App-Schutzrichtlinien können in der Intune-Konsole im [Azure-Portal](https://portal.azure.com) erstellt und bereitgestellt werden. Sicherheitsgruppen können zurzeit im [Microsoft 365 Admin Center](https://admin.microsoft.com) erstellt werden.

- Der Endbenutzer muss sich mit seinem AAD-Konto bei der App anmelden.

## <a name="app-protection-policies-for-microsoft-office-apps"></a>App-Schutzrichtlinien für Microsoft Office-Apps

Es gibt einige zusätzliche Anforderungen, die Sie kennen müssen, wenn Sie App-Schutzrichtlinien für Microsoft Office-Apps verwenden.

### <a name="outlook-mobile-app"></a>Mobile Outlook-App
Für die Verwendung der [mobilen Outlook-App](https://products.office.com/outlook) gelten u. a. folgende zusätzliche Anforderungen:

- Die mobile Outlook-App muss auf dem Gerät des Endbenutzers installiert sein.
- Das [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online)-Postfach und die zugehörige Lizenz des Endbenutzers müssen mit dem AAD-Konto des Endbenutzers verknüpft sein.

  >[!NOTE]
  > Die mobile Outlook-App unterstützt derzeit nur den Intune-App-Schutz für Microsoft Exchange Online und [Exchange Server mit moderner hybrider Authentifizierung](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx), nicht jedoch lokales Exchange oder Exchange in Office 365.

### <a name="word-excel-and-powerpoint"></a>Word, Excel und PowerPoint
Für die Verwendung der Apps für [Word, Excel und PowerPoint](https://products.office.com/business/office) gelten u. a. folgende zusätzliche Anforderungen:

- Mit dem AAD-Konto des Endbenutzers muss eine Lizenz für [Office 365 Business oder Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) verknüpft sein. Das Abonnement muss die Office-Apps auf mobilen Geräten enthalten und kann ein Cloudspeicherkonto mit [OneDrive for Business](https://onedrive.live.com/about/business/) umfassen. Office 365-Lizenzen können im [Microsoft 365 Admin Center](https://admin.microsoft.com) zugewiesen werden. Befolgen Sie dazu diese [Anweisungen](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- Der Benutzer muss über einen verwalteten Speicherort verfügen, der mithilfe der Funktion „Speichern unter“ im Rahmen der Einstellung für die Anwendungsschutzrichtlinie „Kopien von Organisationsdaten speichern“ konfiguriert wird. Wenn beispielsweise der verwaltete Speicherort OneDrive ist, muss die [OneDrive](https://onedrive.live.com/about/)-App in der Word-, Excel- oder PowerPoint-App des Endbenutzer konfiguriert werden.

- Wenn der verwaltete Speicherort OneDrive ist, muss die App unter die App-Schutzrichtlinie fallen, die für den Endbenutzer angegeben ist.

  >[!NOTE]
  > Die mobilen Office-Apps unterstützen zurzeit nur SharePoint Online, nicht jedoch SharePoint lokal.

### <a name="managed-location-needed-for-office"></a>Verwalteter Speicherort für Office erforderlich
Für Office wird ein verwalteter Speicherort (z. B. OneDrive) benötigt. Intune kennzeichnet alle Daten in der App entweder als „unternehmenseigen“ oder „persönlich“. Daten werden als „unternehmenseigen“ betrachtet, wenn sie von einem Speicherort des Unternehmens stammen. Bei den Office-Apps betrachtet Intune Folgendes als Unternehmensspeicher: E-Mail-Speicher (Exchange) oder Cloudspeicher (OneDrive-App mit einem OneDrive for Business-Konto).

### <a name="skype-for-business"></a>Skype for Business
Für die Verwendung von Skype for Business gelten zusätzliche Anforderungen. Informationen hierzu finden Sie in den Lizenzanforderungen für [Skype for Business](https://products.office.com/skype-for-business/it-pros). Informationen zu Skype for Business (SfB)-Hybrid- und lokalen Konfigurationen finden Sie Informationen unter [Moderne Hybridauthentifizierung für SfB und Exchange wird allgemein verfügbar](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) bzw. [Moderne Authentifizierung für SfB OnPrem mit AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910).

## <a name="app-protection-global-policy"></a>Globale App-Schutzrichtlinie

Wenn ein OneDrive-Administrator zu **admin.onedrive.com** navigiert und **Gerätezugriff** auswählt, kann er Steuerelemente für die **Mobile Anwendungsverwaltung** für die OneDrive- und SharePoint-Client-Apps festlegen. 

Die Einstellungen, die für die OneDrive-Administratorkonsole zur Verfügung gestellt wurden, konfigurieren eine besondere App-Schutzrichtlinie für Intune, die **globale Richtlinie**. Diese globale Richtlinie gilt für alle Benutzer in Ihrem Mandanten und kann nicht eingeschränkt angewendet werden. 

Sobald sie aktiviert ist, werden die OneDrive- und SharePoint-Apps für iOS und Android standardmäßig über die ausgewählten Einstellungen geschützt. Ein IT-Experte kann diese Richtlinie in der Intune-Konsole bearbeiten, um weitere Ziel-Apps hinzuzufügen und Richtlinieneinstellungen zu ändern. 

Standardmäßig darf nur eine **globale Richtlinie** pro Mandant vorhanden sein. [Intune Graph-APIs](../developer/intune-graph-apis.md) können Sie jedoch verwenden, um zusätzliche globale Richtlinien pro Mandant zu erstellen, was jedoch nicht empfohlen wird. Das Erstellen zusätzlicher globaler Richtlinien wird nicht empfohlen, da die Problembehandlung bei der Implementierung einer solchen Richtlinie sehr kompliziert sein kann.

Obwohl die **globale Richtlinie** für alle Benutzer in Ihrem Mandanten gilt, werden diese Einstellungen von jeder standardmäßigen App-Schutzrichtlinie für Intune überschrieben.

## <a name="app-protection-features"></a>App-Schutzfunktionen

### <a name="multi-identity"></a>Mehrere Identitäten

Mit der Unterstützung mehrerer Identitäten kann eine App mehrere Zielgruppen unterstützen. Hierbei kann es sich sowohl um „Unternehmensbenutzer“ als auch um „persönliche Benutzer“ handeln. Geschäfts-, Schul- und Unikonten werden von „Unternehmensbenutzern“ verwendet, persönliche Konten dagegen von „Endbenutzern“, beispielsweise von Microsoft Office-Benutzern. Eine App, die mehrere Identitäten unterstützt, kann öffentlich freigegeben werden. Dabei werden App-Schutzrichtlinien nur angewendet, wenn die App im Kontext eines Geschäfts-, Schul- und Unikontos („Unternehmen“) verwendet wird. Bei der Unterstützung mehrerer Identitäten wird das [Intune SDK](../developer/app-sdk.md) verwendet, um App-Schutzrichtlinien nur auf das Geschäfts-, Schul- oder Unikonto anzuwenden, das bei der App angemeldet ist. Wenn ein persönliches Konto bei der App angemeldet ist, kann nicht auf die Daten zugegriffen werden.

Ein Beispiel: Wenn ein Benutzer ein neues Dokument in Word startet, wird dies als „persönlicher“ Kontext betrachtet, und die App-Schutzrichtlinien von Intune werden nicht angewendet. Sobald das Dokument im OneDrive-„Unternehmenskonto“ gespeichert wird, gilt dies als „Unternehmenskontext“, und die Intune-App-Schutzrichtlinien werden angewendet.

Ein Beispiel für „Unternehmenskontext“: Ein Benutzer startet die OneDrive-App über sein Geschäftskonto. Im geschäftlichen Kontext kann er keine Dateien an einen privaten Speicherort verschieben. Wenn der Benutzer OneDrive später jedoch mit einem persönlichen Konto verwendet, kann er Daten ohne Einschränkung aus dem persönlichen OneDrive kopieren und verschieben.

Outlook bietet eine kombinierte Ansicht für „persönliche“ und „geschäftliche“ E-Mails. In dieser Situation fordert die Outlook-App beim Start zur Eingabe der Intune-PIN auf.

Weitere Informationen zu mehreren Identitäten in Intune finden Sie unter [Durch Microsoft Intune geschützte Apps](apps-supported-intune-apps.md).

### <a name="intune-app-pin"></a>Intune-App-PIN

Die PIN (Personal Identification Number) ist eine Kennung, mit der sichergestellt wird, dass der richtige Benutzer in einer Anwendung auf die Daten der Organisation zugreift.

**Aufforderung zur Eingabe der PIN**<br>
Intune fordert den Benutzer zur Eingabe seiner App-PIN auf, wenn dieser versucht, auf „unternehmenseigene“ Daten zuzugreifen. In Apps mit Unterstützung mehrerer Identitäten – z. B. Word, Excel oder PowerPoint – wird der Benutzer zur PIN-Eingabe aufgefordert, wenn er versucht, ein „unternehmenseigenes“ Dokument oder eine „unternehmenseigene“ Datei zu öffnen. In Apps mit nur einer Identität – z. B. branchenspezifische Apps, die über das [Intune App Wrapping Tool](../developer/apps-prepare-mobile-application-management.md) verwaltet werden – wird der Benutzer beim Start der App zur Eingabe der PIN aufgefordert, da dem [Intune SDK](../developer/app-sdk.md) bekannt ist, dass die Verwendung der App immer „unternehmenseigen“ ist.

**Häufigkeit der Aufforderung zur Eingabe der PIN oder Administratoranmeldeaufforderung eines Unternehmens**<br>
Der IT-Administrator kann die Intune-App-Schutzrichtlinieneinstellung **Zugriffsanforderungen nach (Minuten) erneut überprüfen** in der Intune-Verwaltungskonsole definieren. Diese Einstellung gibt die Zeitspanne an, nach der die Zugriffsanforderungen auf dem Gerät überprüft werden und der Bildschirm zur Eingabe der PIN oder Administratoranmeldeaufforderung eines Unternehmens erneut angezeigt wird. Folgende Faktoren beeinflussen, wie häufig ein Benutzer zur PIN-Eingabe aufgefordert wird:

- **Eine PIN wird für alle Apps des gleichen Herausgebers genutzt, um die Benutzerfreundlichkeit zu erhöhen**:<br> In iOS wird eine gemeinsame App-PIN für alle Apps **des gleichen App-Herausgebers** genutzt. Beispielsweise verwenden alle Microsoft-Apps dieselbe PIN. Unter Android wird eine App-PIN für alle Apps genutzt.
- **Das Verhalten von *Zugriffsanforderungen nach (Minuten) erneut überprüfen* nach einem Geräteneustart:**<br> Ein Timer zählt die Anzahl von Minuten der Inaktivität, die angeben, wann die Intune-App-PIN oder Administratoranmeldeaufforderung eines Unternehmens das nächste Mal angezeigt werden soll. Unter iOS hat ein Neustart des Geräts keine Auswirkung auf den Timer. Das bedeutet, dass ein Neustart des Geräts keine Auswirkung auf die Anzahl der inaktiven Minuten des Benutzers einer iOS-App mit der Intune-PIN-Richtlinie (oder Administratoranmeldeaufforderungs-Richtlinie) hat. Unter Android wird der Timer beim Neustart des Geräts zurückgesetzt. Deshalb ist es wahrscheinlich, dass Android-Apps mit der Intune-PIN-Richtlinie (oder Administratoranmeldeaufforderungs-Richtlinie) den Benutzer unabhängig vom Wert der Einstellung „Zugriffsanforderungen erneut überprüfen nach (Minuten)“ nach dem **Neustart des Geräts** zur Eingabe einer PIN oder Administratoranmeldeaufforderung eines Unternehmens für die App auffordern.  
- **Das Wiederholungsverhalten des Timers für die PIN**:<br> Wenn für den Zugriff auf eine App (App A) eine PIN eingegeben wurde und diese App auf dem Gerät nicht mehr im Vordergrund (Haupteingabefokus) ausgeführt wird, wird der Timer für diese PIN zurückgesetzt. Eine andere App (App B), für die die gleiche PIN gilt, fordert den Benutzer nicht zur PIN-Eingabe auf, weil der Zeitgeber zurückgesetzt wurde. Die Aufforderung wird wieder angezeigt, wenn der Wert für „Zugriffsanforderungen nach (Minuten) erneut überprüfen“ erneut erreicht wurde.

Selbst wenn die PIN auf iOS-Geräten unter Apps von verschiedenen Herausgebern freigegeben wird, wird die Eingabeaufforderung erneut angezeigt, wenn der Wert für **Zugriffsanforderungen nach (Minuten) erneut überprüfen** erneut für die App erreicht wird, die nicht über den Eingabefokus verfügt. Beispiel: Der Benutzer verfügt über die App _A_ von Herausgeber _X_ und über die App _B_ von Herausgeber _Y_, und für diese Apps wird die gleiche PIN verwendet. Der Benutzer verwendet App _A_ (im Vordergrund), und die App _B_ ist minimiert. Wenn der Wert für **Zugriffsanforderungen nach (Minuten) erneut überprüfen** erreicht wurde und der Benutzer zur App _B_ wechselt, ist eine PIN erforderlich.

  >[!NOTE]
  > Um die Zugriffsanforderungen des Benutzers (besonders bei häufig verwendeten Apps) öfter zu überprüfen (z. B. die PIN-Eingabeaufforderung), empfiehlt es sich, den Wert für die Einstellung „Zugriffsanforderungen nach (Minuten) erneut überprüfen“ zu senken.

**Integrierte App-PINs für Outlook und OneDrive**<br>
Die Intune-PIN funktioniert mit einem auf Inaktivität basierten Timer, also dem Wert von **Zugriffsanforderungen nach (Minuten) erneut überprüfen**. Deshalb werden Aufforderungen zur Eingabe der Intune-PIN unabhängig von Aufforderungen zur Eingabe der integrierten App-PIN für Outlook und OneDrive, die standardmäßig beim Start der App angezeigt werden, angezeigt. Wenn der Benutzer gleichzeitig zur Eingabe beider PINs aufgefordert wird, sollte die Intune-PIN Vorrang haben.

**Sicherheit für Intune-PINs**<br>
Mit der PIN wird sichergestellt, dass nur der richtige Benutzer in der App auf Daten der Organisation zugreifen kann. Ein Endbenutzer muss sich daher mit seinem Geschäfts-, Uni- oder Schulkonto anmelden, bevor er seine Intune-App-PIN festlegen oder zurücksetzen kann. Diese Authentifizierung wird von Azure Active Directory über einen Austausch sicherer Token durchgeführt und ist für das [Intune SDK](../developer/app-sdk.md) nicht transparent. Hinsichtlich der Sicherheit ist die beste Möglichkeit, ein Geschäfts-, Uni- oder Schulkonto zu schützen, das Konto zu verschlüsseln. Die Verschlüsselung steht nicht in Zusammenhang mit der App-PIN, sondern stellt eine eigene App-Schutzrichtlinie dar.

**Schutz vor Brute-Force-Angriffen und der Intune-PIN**<br>
Im Rahmen der App-PIN-Richtlinie kann der IT-Administrator festlegen, wie oft ein Benutzer versuchen kann, die PIN zu authentifizieren, bevor die App gesperrt wird. Nachdem die maximale Anzahl von Versuchen erreicht wurde, kann das [Intune SDK](../developer/app-sdk.md) die „unternehmenseigenen“ Daten aus der App entfernen.

**Intune-PIN und selektives Zurücksetzen**<br>
Unter iOS werden die PIN-Informationen auf App-Ebene im Schlüsselbund gespeichert, der von Apps desselben Herausgebers, wie z. B. allen Apps von Microsoft als Erstanbieter, gemeinsam genutzt wird. Diese PIN-Informationen sind auch an ein Endbenutzerkonto gebunden. Ein selektives Zurücksetzen einer App darf keine Auswirkung auf eine andere App haben. 

Beispielsweise wird eine für Outlook festgelegte PIN für den angemeldeten Benutzer in einem gemeinsam genutzten Schlüsselbund gespeichert. Wenn sich der Benutzer bei OneDrive (auch ein Microsoft-Produkt) anmeldet, wird die gleiche PIN wie bei Outlook verwendet, da derselbe gemeinsam genutzte Schlüsselbund zum Einsatz kommt. Wenn sich der Benutzer aus Outlook abmeldet oder die Benutzerdaten in Outlook zurückgesetzt werden, löscht das Intune SDK diesen Schlüsselbund nicht, da OneDrive diese PIN möglicherweise noch immer verwendet. Aus diesem Grund wird beim selektiven Zurücksetzen der gemeinsam genutzte Schlüsselbund, einschließlich PIN, nicht gelöscht. Dieses Verhalten bleibt auch dann unverändert, wenn nur eine App eines Herausgebers auf dem Gerät vorhanden ist. 

Die PIN wird von Apps desselben Herausgebers gemeinsam genutzt. Wenn das Zurücksetzen für eine einzelne App erfolgt, weiß das Intune SDK nicht, ob sich auf dem Gerät weitere Apps desselben Herausgebers befinden. Daher löscht das Intune SDK die PIN nicht, da sie möglicherweise noch von anderen Apps verwendet wird. Es wird erwartet, dass die PIN der App zurückgesetzt wird, wenn die letzte App dieses Herausgebers im Rahmen einer Betriebssystembereinigung endgültig entfernt wird.
 
Wenn Sie bei einigen Geräten beobachten, dass die PIN gelöscht wird, passiert wahrscheinlich Folgendes: Da die PIN an eine Identität gebunden ist, wird der Benutzer, wenn er sich nach einer Zurücksetzen mit einem anderen Konto angemeldet hat, zur Eingabe einer neuen PIN aufgefordert. Wenn er sich jedoch mit einem zuvor bestehenden Konto anmeldet, kann eine bereits im Schlüsselbund gespeicherte PIN zur Anmeldung verwendet werden.

**Doppeltes Festlegen einer PIN für Apps vom gleichen Herausgeber?**<br>
MAM (für iOS) erlaubt derzeit eine PIN auf Anwendungsebene mit alphanumerischen Zeichen und Sonderzeichen (als „Passcode“ bezeichnet), was die Beteiligung von Anwendungen (z. B. WXP, Outlook, Managed Browser, Yammer) erfordert, damit das [Intune SDK für iOS](../developer/app-sdk-ios.md) integriert werden kann. Ohne das SDK werden die Kennungseinstellungen nicht ordnungsgemäß für die Zielanwendungen erzwungen. Hierbei handelte es sich um ein Feature, das im Intune SDK für iOS Version 7.1.12 veröffentlicht wurde.

Um dieses Feature zu unterstützen und die Abwärtskompatibilität mit früheren Versionen des Intune SDK für iOS zu gewährleisten, werden alle numerischen PINs oder Kennungen in Version 7.1.12 oder höher getrennt von der numerischen PIN in früheren Versionen des SDK verarbeitet. Wenn also ein Gerät Anwendungen mit Intune SDK für iOS-Versionen zwischen 7.1.12 UND 7.1.12 vom selben Hersteller aufweist, müssen sie zwei PINs einrichten. Die beiden PINs (für jede App) sind in keiner Weise miteinander verknüpft (sie müssen also für die jeweilige App geltende App-Schutzrichtlinie einhalten). Daher kann der Benutzer ein und dieselbe PIN *nur* dann zweimal einrichten, wenn für App A und App B die gleichen Richtlinien (in Bezug auf die PIN) gelten. 

Dieses Verhalten gilt speziell für die PIN für iOS-Anwendungen, die mit der Intune-Verwaltung mobiler Apps aktiviert sind. Wenn Anwendungen im Laufe der Zeit höhere Intune SDK-Versionen für iOS annehmen, ist das zweimalige Festlegen einer PIN für Apps desselben Herausgebers weniger entscheidend. Beachten Sie den Hinweis unterhalb eines Beispiels.

  >[!NOTE]
  > Beispiel: Wenn App A mit einer niedrigeren Version als 7.1.12 und App B mit einer höheren oder gleichen Version wie 7.1.12 vom selben Herausgeber erstellt wurde, muss der Endbenutzer die PINs für A und B separat einrichten, sofern beide auf einem iOS-Gerät installiert sind.
  > Wenn eine App C mit der SDK-Version 7.1.9 auf dem Gerät installiert ist, verwendet diese dieselbe PIN wie App A. Eine App D, die mit Version 7.1.14 erstellt wurde, verwendet die gleiche PIN wie App B.  
  > Wenn auf einem Gerät nur App A und C installiert sind, muss eine PIN festgelegt werden. Dasselbe gilt, wenn auf einem Gerät nur App B und D installiert sind.

### <a name="app-data-encryption"></a>Verschlüsselung von App-Daten
IT-Administratoren können eine App-Schutzrichtlinie bereitstellen, die erzwingt, dass App-Daten verschlüsselt werden. Im Rahmen einer solchen Richtlinie kann ein IT-Administrator auch angeben, wann die Inhalte verschlüsselt werden.

**Intune-Verfahren für die Datenverschlüsselung**<br> Ausführliche Informationen zur Verschlüsselungseinstellung im Rahmen von App-Schutzrichtlinien finden Sie unter [Android-Verwaltungsrichtlinieneinstellungen für mobile Apps in Microsoft Intune](app-protection-policy-settings-android.md) und [iOS-Richtlinieneinstellungen für die Verwaltung mobiler Apps](app-protection-policy-settings-ios.md).

**Verschlüsselte Daten**<br>
Nur Daten, die als „unternehmenseigen“ markiert sind, werden gemäß der vom IT-Administrator eingerichteten App-Schutzrichtlinie verschlüsselt. Daten werden als „unternehmenseigen“ betrachtet, wenn sie von einem Speicherort des Unternehmens stammen. Bei den Office-Apps betrachtet Intune Folgendes als unternehmenseigenen Speicherort:

- E-Mail (Exchange) 
- Cloudspeicher (OneDrive-App mit einem OneDrive for Business-Konto)

Bei Branchen-Apps, die vom [Intune App Wrapping Tool](../developer/apps-prepare-mobile-application-management.md) verwaltet werden, werden alle App-Daten als „unternehmenseigen“ betrachtet.

### <a name="selective-wipe"></a>Selektives Zurücksetzen

**Löschen von Daten per Remotezugriff**<br>
Intune kann App-Daten auf drei verschiedene Arten löschen: 
- Vollständiges Zurücksetzen des Geräts
- Selektives Zurücksetzen für MDM 
- Selektives Zurücksetzen für MAM

Weitere Informationen zur Remotezurücksetzung der MDM finden Sie unter [Entfernen von Geräten durch Zurücksetzen oder Abkoppeln](../remote-actions/devices-wipe.md). Weitere Informationen zum selektiven Zurücksetzen mit MAM finden Sie unter [the Retire action (Die Aktion „Abkoppeln“)](../remote-actions/devices-wipe.md#retire) und [Zurücksetzen von Unternehmensdaten in Apps](apps-selective-wipe.md).

Beim [vollständigen Zurücksetzen des Geräts](../remote-actions/devices-wipe.md) werden alle Benutzerdaten und -einstellungen vom **Gerät** entfernt, indem das Gerät auf die werkseitigen Standardeinstellungen zurückgesetzt wird. Das Gerät wird aus Intune entfernt.

  >[!NOTE]
  > Ein vollständiges Zurücksetzen des Geräts und selektives Zurücksetzen für MDM kann nur auf Geräten erreicht werden, die bei der Intune-Verwaltung mobiler Geräte (MDM) registriert sind.

**Selektives Zurücksetzen für MDM**<br>
Informationen zum Entfernen von Unternehmensdaten finden Sie unter [Remove devices - retire (Entfernen von Geräten: Abkoppeln)](../remote-actions/devices-wipe.md#retire).

**Selektives Zurücksetzen für MAM**<br>
Durch selektives Zurücksetzen für MAM können Unternehmensanwendungsdaten von einer App entfernt werden. Die Anforderung wird mithilfe des Azure-Portals für Intune initiiert. Informationen zum Initiieren einer Zurücksetzungsanforderung finden Sie unter [So setzen Sie nur die Unternehmensdaten in einer App zurück](apps-selective-wipe.md).

Wenn das selektive Zurücksetzen initiiert wird, während ein Benutzer die App verwendet, überprüft das [Intune SDK](../developer/app-sdk.md) alle 30 Minuten, ob eine Anforderung zum selektiven Zurücksetzen vom Intune MAM-Dienst vorhanden ist. Das SDK überprüft auch, ob eine Anforderung zum selektiven Zurücksetzen vorhanden ist, wenn ein Benutzer eine App zum ersten Mal startet und sich mit einem Geschäfts-, Uni- oder Schulkonto anmeldet.

**Wenn lokale Dienste nicht mit von Intune geschützten Apps funktionieren**<br>
Der Intune-App-Schutz hängt davon ab, dass die Identität des Benutzers in der App und im [Intune SDK](../developer/app-sdk.md) konsistent ist. Die einzige Möglichkeit, dies zu garantieren, ist eine moderne Authentifizierung. Es gibt Szenarien, in denen Apps möglicherweise mit einer lokalen Konfiguration funktionieren. Dies ist aber weder konsistent noch garantiert.

**Eine sichere Möglichkeit zum Öffnen von Weblinks in verwalteten Apps**<br>
Ein IT-Administrator kann eine App-Schutzrichtlinie für die [Intune Managed Browser-App](app-configuration-managed-browser.md) einrichten und bereitstellen, ein von Microsoft Intune entwickelter Webbrowser, der problemlos mit Intune verwaltet werden kann. Der IT-Administrator kann festlegen, dass alle Weblinks in über Intune verwaltete Apps mit der Managed Browser-App geöffnet werden müssen.

## <a name="app-protection-experience-for-ios-devices"></a>App-Schutzfunktionen für iOS-Geräte

### <a name="device-fingerprint-or-face-ids"></a>Erkennung von Fingerabdrücken oder Gesichtern auf dem Gerät 
Die Richtlinien für den Intune-App-Schutz ermöglichen es Ihnen, den App-Zugriff nur auf Benutzer mit Intune-Lizenz zu beschränken. Eine der Möglichkeiten, den Zugriff auf die App zu steuern, besteht darin, Apple Touch ID oder Face ID auf unterstützten Geräten zu erfordern. Intune implementiert ein Verhalten, bei dem Intune den Benutzer bei Änderungen an der biometrischen Datenbank des Geräts zur PIN-Eingabe auffordert, wenn der nächste Wert des Inaktivitätstimeouts erfüllt ist. Zu Änderungen an biometrischen Daten zählen das Hinzufügen oder Entfernen von Fingerabdrücken oder Gesichtern. Wenn der Intune-Benutzer keine PIN festgelegt hat, wird er zu einem Fenster für die Einrichtung einer Intune-PIN weitergeleitet.
 
Zweck dieses Verfahrens ist es, die Daten Ihrer Organisation innerhalb der App und auf App-Ebene kontinuierlich zu schützen. Dieses Feature ist nur für iOS verfügbar und erfordert, dass das Intune SDK für iOS, Version 9.0.1 oder höher in betreffende Anwendungen integriert wird. Die Integration des SDK ist erforderlich, damit das Verhalten für die Zielanwendungen erzwungen werden kann. Diese Integration erfolgt kontinuierlich und ist abhängig von den jeweiligen Anwendungsteams. Zu den betreffenden Apps zählen z. B. WXP, Outlook, Managed Browser und Yammer.
  
### <a name="ios-share-extension"></a>iOS-Freigabeerweiterung
Mithilfe der iOS-Freigabeerweiterung können Geschäfts-, Schul- oder Unidaten in nicht verwalteten Apps zu geöffnet werden, auch wenn die Datenübertragungsrichtlinie auf **Nur verwaltete Apps** oder **Keine Apps** festgelegt ist. Die Intune-App-Schutzrichtlinie kann die iOS-Freigabeerweiterung nicht steuern, ohne das Gerät zu verwalten. Daher _**verschlüsselt Intune „unternehmenseigene“ Daten, bevor diese außerhalb der App freigegeben werden**_ . Sie können dieses Verschlüsselungsverhalten überprüfen, indem Sie versuchen, eine „unternehmenseigene“ Datei außerhalb der verwalteten App zu öffnen. Die Datei sollte verschlüsselt sein und außerhalb der verwalteten App nicht geöffnet werden können.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Mehrere Zugriffseinstellungen des Intune-App-Schutzes für die gleiche Gruppe von Apps und Benutzern
Intune-App-Schutzrichtlinien für den Zugriff werden in einer bestimmten Reihenfolge auf Endbenutzergeräten angewendet, wenn die Benutzer versuchen, über ihr Unternehmenskonto auf eine App zuzugreifen. In der Regel hat ein Zurücksetzungsvorgang Vorrang vor einem Block. Verwerfbare Warnungen werden erst als letztes berücksichtigt. Es wird z. B. eine Einstellung der mindestens erforderlichen iOS-Version, die den Benutzer auffordert, ein Update des Betriebssystems auszuführen, im Anschluss an die Einstellung angewendet, die dem Benutzer den Zugriff verweigert (wenn dies auf den Benutzer/die App zutrifft). In diesem Szenario konfiguriert der IT-Administrator die Einstellung für die mindestens erforderliche iOS-Version auf Version 11.0.0.0 und die mindestens erforderliche iOS-Version, die nur für Warnungen gilt, auf 11.1.0.0. Gleichzeitig versucht das Gerät, auf dem noch die iOS-Version 10 installiert ist, auf die App zuzugreifen. In Folge dessen wird der Endbenutzer basierend auf restriktiveren Einstellungen für die mindestens erforderliche iOS-Version blockiert und erhält keinen Zugriff.

Wenn verschiedene Arten von Einstellungen verarbeitet werden müssen, haben die Anforderungen hinsichtlich bestimmter Versionen des Intune SDK Vorrang. Erst danach werden Anforderungen berücksichtigt, die eine Version einer App oder eines iOS-Betriebssystems betreffen. Anschließend werden in derselben Reihenfolge mögliche Warnungen für sämtliche Einstellungstypen überprüft. Es wird empfohlen, die Anforderung, die die Intune SDK-Version betrifft, nur unter Anleitung des Intune-Produktteams für grundlegende Blockierungsszenarien zu konfigurieren.

## <a name="app-protection-experience-for-android-devices"></a>App-Schutzfunktionen für Android-Geräte

### <a name="company-portal-app-and-intune-app-protection"></a>Unternehmensportal-App und Intune-App-Schutz
Ein Großteil der App-Schutzfunktionen ist in die Unternehmensportal-App integriert. Eine Registrierung der Geräte ist _nicht erforderlich_, allerdings wird immer die Unternehmensportal-App benötigt. Bei der Verwaltung mobiler Anwendungen ohne Registrierung (Mobile Application Management Without Enrollment, MAM-WE) muss lediglich die Unternehmensportal-App auf dem Gerät des Endbenutzers installiert sein.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Mehrere Zugriffseinstellungen des Intune-App-Schutzes für die gleiche Gruppe von Apps und Benutzern
Intune-App-Schutzrichtlinien für den Zugriff werden in einer bestimmten Reihenfolge auf Endbenutzergeräten angewendet, wenn die Benutzer versuchen, über ihr Unternehmenskonto auf eine App zuzugreifen. In der Regel haben Blöcke Vorrang vor verwerfbaren Warnungen. Es wird z. B. eine Einstellung der mindestens erforderlichen Android-Patch-Version, die den Benutzer auffordert, ein Patchupgrade auszuführen, im Anschluss an die Einstellung angewendet, die dem Benutzer den Zugriff verweigert (wenn dies auf den Benutzer/die App zutrifft). In diesem Szenario konfiguriert der IT-Administrator die Einstellung für die mindestens erforderliche Version des Android-Patch auf den 1.3.2018 und die für die mindestens erforderliche Version des Android-Patch, die nur für Warnungen gilt, auf den 1.2.2018. Gleichzeitig versucht das Gerät, das noch die Patch-Version vom 1.1.2018 verwendet, auf die App zuzugreifen. In Folge dessen wird der Endbenutzer basierend auf restriktiveren Einstellungen für die mindestens erforderliche Version des Android-Patch blockiert und erhält keinen Zugriff. 

Wenn verschiedene Arten von Einstellungen verarbeitet werden müssen, haben die Anforderungen hinsichtlich bestimmter App-Versionen Vorrang. Erst danach werden Anforderungen berücksichtigt, die eine Version des Android-Betriebssystems und Android-Patch-Versionen betreffen. Anschließend werden in derselben Reihenfolge mögliche Warnungen für sämtliche Einstellungstypen überprüft.

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>Intune-App-Schutzrichtlinien und SafetyNet Attestation von Google für Android-Geräte 
Administratoren können in Intune-App-Schutzrichtlinien festlegen, dass Endbenutzergeräte die Google-Funktion „SafetyNet Attestation“ für Android-Geräte erfolgreich durchlaufen müssen. Eine neue Google Play-Dienstbestimmung wird in einem von Intune festgelegten Intervall an den IT-Administrator gesendet. Die Anzahl der Dienstaufrufe wird in Abhängigkeit von der Last gedrosselt; dieser Wert wird also intern verwaltet und kann nicht konfiguriert werden. Jede Aktion für die Einstellung von SafetyNet Attestation von Google, die von einem IT-Administrator konfiguriert wurde, wird auf Grundlage des zuletzt an Intune gemeldeten Ergebnisses zum Zeitpunkt des bedingten Starts ausgeführt. Wenn keine Daten vorhanden sind, wird der Zugriff abhängig davon gewährt, dass keine anderen Überprüfungen für den bedingten Start fehlschlagen, und der „Roundtrip“ des Google Play-Diensts zur Bestimmung der Nachweisergebnisse im Back-End startet. Wenn es beim Gerät zu Problemen kommt, wird der Benutzer asynchron benachrichtigt. Wenn die Daten veraltet sind, wird der Zugriff auf Grundlage des zuletzt gemeldeten Ergebnisses blockiert oder gewährt, und ein „Roundtrip“ des Google Play-Diensts zur Bestimmung der Nachweisergebnisse startet. Wenn es beim Gerät zu Problemen kommt, wird der Benutzer asynchron benachrichtigt.

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>Intune-App-Schutzrichtlinien und die Verify Apps-API von Google für Android-Geräte
Administratoren können in Intune-App-Schutzrichtlinien festlegen, dass Endbenutzergeräte Signale über die Verify Apps-API von Google für Android-Geräte senden müssen. Die dafür erforderlichen Schritte unterscheiden sich leicht je nach Gerät. Grundsätzlich müssen Sie dafür den Google Play Store besuchen, dort auf **My apps & games** (Meine Apps und Spiele) klicken und dann auf das Ergebnis der letzten App-Überprüfung klicken. Dadurch gelangen Sie zum Play Protect-Menü. Sorgen Sie dafür, dass die Option **Scan device for security threats** (Gerät auf Sicherheitsbedrohungen überprüfen) aktiviert ist.

### <a name="googles-safetynet-attestation-api"></a>SafetyNet Attestation-API von Google 
Für Intune werden die Google Play Protect SafetyNet-APIs verwendet, um die vorhandenen Überprüfungen auf Rootingerkennung für nicht registrierte Geräte zu ergänzen. Google hat diese APIs für Android-Apps entwickelt und verwaltet sie, wenn die Apps nicht auf gerooteten Geräten ausgeführt werden sollen. Sie kommen z. B. bei der Google Pay-App zum Einsatz. Google stellt zwar nicht alle Überprüfungen, die durchgeführt werden, um Rooting zu erkennen, öffentlich zur Verfügung; wir gehen jedoch davon aus, dass diese APIs Benutzer identifizieren können, die ihr Gerät gerootet haben. Diesen Benutzern kann der Zugriff dann verwehrt werden, oder ihre Unternehmenskonten können aus den Apps entfernt werden, für die Richtlinien aktiviert sind. Die Option **Check basic integrity** (Grundlegende Integrität überprüfen) informiert Sie über die allgemeine Integrität des Geräts. Für gerootete Geräte, Emulatoren, virtuelle Geräte und Geräte, die Anzeichen von Manipulationen aufweisen, schlägt die Überprüfung der grundlegenden Integrität fehl. Die Option **Check basic integrity & certified devices** (Grundlegende Integrität und zertifizierte Geräte überprüfen) informiert Sie über die Kompatibilität des Geräts mit Google-Diensten. Nur unveränderte Geräte, die von Google zertifiziert wurden, bestehen diese Überprüfung. Die folgenden Geräte bestehen die Überprüfung nicht:

- Geräte, für die die Überprüfung der Basisintegrität fehlschlägt
- Geräte mit entsperrtem Bootloader
- Geräte mit einem benutzerdefinierten Systemimage/ROM
- Geräte, für die der Hersteller entweder keine Google-Zertifizierung beantragt hat, oder für die diese nicht bestanden wurde
- Geräte mit einem Systemimage, das direkt aus den Quelldateien des Open Source-Programms für Android erstellt wurde
- Geräte mit einem Systemimage, das sich noch in der Betaversion oder in der Entwicklervorschau befindet

Technische Details finden Sie in der [Dokumentation von Google zu „SafetyNet Attestation“](https://developer.android.com/training/safetynet/attestation).

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>Einstellung für den SafetyNet-Gerätenachweis und die Einstellung „Geräte mit Jailbreak/entfernten Nutzungsbeschränkungen“
Die Überprüfungen im Rahmen der SafetyNet-API von Google Play Protect erfordern, dass der Endbenutzer online ist, zumindest während der Zeit, in der der „Roundtrip“ zur Bestimmung von Nachweisergebnissen ausgeführt wird. Wenn der Endbenutzer offline ist, kann der IT-Administrator immer noch davon ausgehen, dass ein Ergebnis der Einstellung **Geräte mit Jailbreak/entfernten Nutzungsbeschränkungen** erzwungen wird. Hierbei kommt der Wert **Offlinetoleranzperiode** ins Spiel, wenn der Endbenutzer zu lange offline war: Sobald dieser Wert erreicht ist, wird der Zugriff auf Geschäfts-, Schul- und Unidaten solange blockiert, bis wieder Netzwerkzugriff besteht. Durch Aktivieren beider Einstellungen können Sie die Integrität von Endbenutzergeräten auf mehreren Ebenen gewährleisten – ein wichtiger Aspekt, wenn Endbenutzer über Mobilgeräte auf Geschäfts-, Schul- und Unidaten zugreifen.

### <a name="google-play-protect-apis-and-google-play-services"></a>Google Play Protect-APIs und Google Play Services
Die App-Schutzrichtlinieneinstellungen, die Google Play Protect-APIs verwenden, erfordern funktionierende Google Play Services. Sowohl für **SafetyNet-Gerätenachweis** als auch für **Bedrohungsüberprüfung für Apps** muss die von Google bestimmte Version von Google Play Services ordnungsgemäß funktionieren. Da diese Einstellungen in den Sicherheitsbereich fallen, werden die Endbenutzer blockiert, für die diese Einstellungen gelten, wenn diese nicht die entsprechende Version von Google Play Services verwenden oder keinen Zugriff auf Google Play Services haben.

## <a name="next-steps"></a>Nächste Schritte

[Erstellen und Bereitstellen von App-Schutzrichtlinien mit Microsoft Intune](app-protection-policies.md)

[Verfügbare Einstellungen für Schutzrichtlinien für Android-Apps mit Microsoft Intune](app-protection-policy-settings-android.md)

[Verfügbare Einstellungen für Schutzrichtlinien für iOS-Apps mit Microsoft Intune](app-protection-policy-settings-ios.md)

## <a name="see-also"></a>Weitere Informationen:
Apps von Drittanbietern wie beispielsweise die mobile Salesforce-App arbeiten auf eine bestimmte Weise mit Intune zusammen, um die Unternehmensdaten zu schützen. Weitere Informationen zur speziellen Zusammenarbeit der Salesforce-App mit Intune (einschließlich Konfigurationseinstellungen für die MDM-App) finden Sie unter [Salesforce-App und Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
