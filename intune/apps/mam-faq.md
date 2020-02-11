---
title: Häufig gestellte Fragen zu MAM und App-Schutz
description: Dieser Artikel beantwortet einige häufig gestellte Fragen zur mobilen Anwendungsverwaltung (Mobile Application Management, MAM) und zum App-Schutz in Intune.
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
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: erikre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6a92863dc504d295d77029082b57090e55d7f743
ms.sourcegitcommit: 5178aec0244e023e73546f3d10f1a76eaf1f4a3e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2020
ms.locfileid: "76971849"
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Häufig gestellte Fragen zu MAM und App-Schutz

Dieser Artikel beantwortet einige häufig gestellte Fragen zur mobilen Anwendungsverwaltung (Mobile Application Management, MAM) und zum App-Schutz in Intune.

## <a name="mam-basics"></a>Grundlagen zu MAM

**Was ist MAM?**<br></br>
Die [mobile Anwendungsverwaltung (Mobile Application Management, MAM) von Intune](app-lifecycle.md) bezeichnet die Intune-Verwaltungsfunktionen, mit denen Sie mobile Apps für Ihre Benutzer veröffentlichen, per Push bereitstellen, konfigurieren, schützen, überwachen und aktualisieren.

**Welche Vorteile bietet der App-Schutz von MAM?**<br></br>
MAM schützt die Daten einer Organisation innerhalb einer Anwendung. Mit MAM ohne Geräteregistrierung (MAM-WE) kann eine Geschäfts-, Schul- oder Uni-App, die vertrauliche Daten enthält, auf nahezu jedem Gerät verwaltet werden, auch auf persönlichen Geräten in BYOD-Szenarien (Bring Your Own Device). Viele Produktivitäts-Apps, wie z. B. die Microsoft Office-Apps, können über Intune MAM verwaltet werden. Weitere Informationen finden Sie in der Liste von in [Intune verwalteten Apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps), die für die Öffentlichkeit verfügbar sind.

**Welche Gerätekonfigurationen unterstützt MAM?**<br></br>
Intune MAM unterstützt zwei Konfigurationen:
- **Intune MDM und MAM**: IT-Administratoren können Apps mithilfe von MAM und App-Schutzrichtlinien nur auf Geräten verwalten, die bei der Intune-Verwaltung mobiler Geräte (Mobile Device Management, MDM) registriert sind. Um Apps mithilfe von MDM und MAM zu verwalten, sollten Kunden die Intune-Konsole im Azure-Portal unter https://portal.azure.com verwenden.

- **MAM ohne Geräteregistrierung**: Mit MAM ohne Geräteregistrierung (MAM without enrollment, MAM-WE) können IT-Administratoren Apps mithilfe von MAM und App-Schutzrichtlinien auf Geräten verwalten, die nicht bei Intune MDM registriert sind. Dies bedeutet, dass Apps über Intune auf Geräten verwaltet werden können, die bei EMM-Drittanbietern registriert sind. Um Apps mithilfe von MAM-WE zu verwalten, sollten Kunden unter [https://portal.azure.com](https://portal.azure.com) die Intune-Konsole im Azure-Portal verwenden. Darüber hinaus können Apps auf Geräten, die entweder bei EMM-Drittanbietern (Enterprise Mobility Management, EMM) oder überhaupt nicht bei einer MDM registriert sind, von Intune verwaltet werden.


## <a name="app-protection-policies"></a>App-Schutzrichtlinien

**Was sind App-Schutzrichtlinien?**<br></br>
App-Schutzrichtlinien sind Regeln, die sicherstellen, dass die Daten einer Organisation in einer verwalteten App jederzeit sicher sind und dort verbleiben. Eine Richtlinie kann eine Regel sein, die erzwungen wird, wenn ein Benutzer versucht, auf „unternehmenseigene“ Daten zuzugreifen oder diese zu verschieben. Es kann sich auch um eine Reihe von Aktionen handeln, die nicht zulässig sind oder überwacht werden, wenn sich ein Benutzer in der App befindet.

**Was sind Beispiele für App-Schutzrichtlinien?**<br></br>
Ausführliche Informationen zu den einzelnen Einstellungen für App-Schutzrichtlinien finden Sie unter [Android-Verwaltungsrichtlinieneinstellungen für mobile Apps in Microsoft Intune](app-protection-policy-settings-android.md) und [iOS-Richtlinieneinstellungen für die Verwaltung mobiler Apps](app-protection-policy-settings-ios.md).

**Ist es möglich, sowohl MDM- als auch MAM-Richtlinien gleichzeitig auf denselben Benutzer, aber für verschiedene Geräte angewendet zu haben? Wenn ein Benutzer beispielsweise von seinem eigenen MAM-fähigen Computer aus auf seine Arbeitsressourcen zugreifen könnte, aber auch zur Arbeit kommen und dort ein mit Intune MDM verwaltetes Gerät verwenden könnte. Gibt es Vorbehalte gegenüber dieser Idee?**<br></br>
Wenn Sie eine MAM-Richtlinie auf den Benutzer anwenden, ohne den Gerätezustand festzulegen, erhält der Benutzer die MAM-Richtlinie sowohl auf dem BYOD-Gerät als auch auf dem mit Intune verwalteten Gerät. Sie können eine MAM-Richtlinie auch basierend auf dem verwalteten Zustand anwenden. Wenn Sie also eine App-Schutzrichtlinie erstellen, würden Sie neben „Ziel“ für alle App-Typen „Nein“ auswählen. Gehen Sie dann auf eine der folgenden Arten vor:
- Wenden Sie eine weniger strenge MAM-Richtlinie auf mit Intune verwaltete Geräte an, und wenden Sie eine restriktivere MAM-Richtlinie auf nicht bei MDM registrierte Geräte an.
- Wenden Sie eine MAM-Richtlinie nur auf nicht registrierte Geräte an.

Weitere Informationen finden Sie unter [Überwachen von App-Schutzrichtlinien](app-protection-policies-monitor.md).

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Apps, die mit App-Schutzrichtlinien verwaltet werden können

**Welche Apps können mithilfe von App-Schutzrichtlinien verwaltet werden?**<br></br>
Jede App, die in das [Intune App SDK](../developer/app-sdk.md) integriert oder vom [Intune App Wrapping Tool](../developer/apps-prepare-mobile-application-management.md) umschlossen wurde, kann mithilfe von Intune-App-Schutzrichtlinien verwaltet werden. Weitere Informationen finden Sie in der Liste von in [Intune verwalteten Apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps), die für die Öffentlichkeit verfügbar sind.

**Welche grundlegenden Anforderungen bestehen für die Verwendung von App-Schutzrichtlinien in einer mit Intune verwalteten App?**

- Der Endbenutzer muss über ein Azure Active Directory-Konto (AAD) verfügen. Informationen dazu, wie Sie Intune-Benutzer in Azure Active Directory erstellen, finden Sie unter [Hinzufügen von Benutzern und Gewähren von Administratorrechten für Intune](../fundamentals/users-add.md).

- Dem AAD-Konto des Endbenutzers muss eine Lizenz für Microsoft Intune zugewiesen sein. Informationen zum Zuweisen von Intune-Lizenzen zu Endbenutzern finden Sie unter [Verwalten von Intune-Lizenzen](../fundamentals/licenses-assign.md).

- Der Endbenutzer muss zu einer Sicherheitsgruppe gehören, für die eine App-Schutzrichtlinie gilt. Die gleiche App-Schutzrichtlinie muss für die verwendete App gelten. App-Schutzrichtlinien können in der Intune-Konsole im [Azure-Portal](https://portal.azure.com) erstellt und bereitgestellt werden. Sicherheitsgruppen können zurzeit im [Microsoft 365 Admin Center](https://admin.microsoft.com) erstellt werden.

- Der Endbenutzer muss sich mit seinem AAD-Konto bei der App anmelden.

**Was geschieht, wenn ich eine App mit Intune-App-Schutz aktivieren möchte, diese aber keine unterstützte App-Entwicklungsplattform verwendet?**

Das Intune SDK-Entwicklungsteam testet und unterstützt aktiv Apps, die mit dem nativen Android-, iOS- (Obj-C, Swift), Xamarin-, Xamarin.Forms- und Cordova-Plattformen erstellt wurden. Während einige Kunden das Intune SDK erfolgreich in andere Plattformen wie React Native und NativeScript integrieren konnten, bieten wir keine expliziten Anleitungen oder Plug-Ins für App-Entwickler, die andere als unsere unterstützten Plattformen verwenden.

**Unterstützt das Intune App SDK die Microsoft Authentication Library (MSAL) oder soziale Konten?**<br></br>
Das Intune App SDK verwendet erweiterte ADAL-Funktionen für die Erstanbieter- und Drittanbieterversionen des SDK. Deshalb ist die MSAL für viele Hauptszenarios wie die Authentifizierung beim Intune-App-Schutz-Dienst und der bedingte Start nicht gut geeignet. Da der allgemeine Leitfaden des Identity-Teams von Microsoft darin besteht, für alle Microsoft Office-Apps auf MSAL umzusteigen, wird das Intune SDK es letztlich unterstützen müssen, aber derzeit ist keine Unterstützung geplant.

**Welche zusätzlichen Anforderungen gelten für die Verwendung der [mobilen Outlook-App](https://products.office.com/outlook)?**

- Die mobile Outlook-App muss auf dem Gerät des Endbenutzers installiert sein.

- Das [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online)-Postfach und die zugehörige Lizenz des Endbenutzers müssen mit dem AAD-Konto des Endbenutzers verknüpft sein.

  >[!NOTE]
  > Die mobile Outlook-App unterstützt derzeit nur den Intune-App-Schutz für Microsoft Exchange Online und [Exchange Server mit moderner hybrider Authentifizierung](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx), nicht jedoch lokales Exchange oder Exchange in Office 365.

**Welche zusätzlichen Anforderungen gelten für die Verwendung der [Word-, Excel- und PowerPoint](https://products.office.com/business/office)-Apps?**

- Mit dem AAD-Konto des Endbenutzers muss eine Lizenz für [Office 365 Business oder Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) verknüpft sein. Das Abonnement muss die Office-Apps auf mobilen Geräten enthalten und kann ein Cloudspeicherkonto mit [OneDrive for Business](https://onedrive.live.com/about/business/) umfassen. Office 365-Lizenzen können im [Microsoft 365 Admin Center](https://admin.microsoft.com) zugewiesen werden. Befolgen Sie dazu diese [Anweisungen](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- Der Benutzer muss über einen verwalteten Speicherort verfügen, der mithilfe der Funktion „Speichern unter“ im Rahmen der Einstellung für die Anwendungsschutzrichtlinie „Kopien von Organisationsdaten speichern“ konfiguriert wird. Wenn beispielsweise der verwaltete Speicherort OneDrive ist, muss die [OneDrive](https://onedrive.live.com/about/)-App in der Word-, Excel- oder PowerPoint-App des Endbenutzer konfiguriert werden.

- Wenn der verwaltete Speicherort OneDrive ist, muss die App unter die App-Schutzrichtlinie fallen, die für den Endbenutzer angegeben ist.

  >[!NOTE]
  > Die mobilen Office-Apps unterstützen zurzeit nur SharePoint Online, nicht jedoch SharePoint lokal.

**Warum wird ein verwalteter Speicherort (z. B. OneDrive) für Office benötigt?**<br></br>
Intune kennzeichnet alle Daten in der App entweder als „unternehmenseigen“ oder „persönlich“. Daten werden als „unternehmenseigen“ betrachtet, wenn sie von einem Speicherort des Unternehmens stammen. Bei den Office-Apps betrachtet Intune Folgendes als Unternehmensspeicher: E-Mail-Speicher (Exchange) oder Cloudspeicher (OneDrive-App mit einem OneDrive for Business-Konto).

**Welche zusätzlichen Anforderungen gelten für die Verwendung von Skype for Business?**<br></br>
Informationen hierzu finden Sie in den Lizenzanforderungen für [Skype for Business](https://products.office.com/skype-for-business/it-pros). Informationen zu Skype for Business (SfB)-Hybrid- und lokalen Konfigurationen finden Sie Informationen unter [Moderne Hybridauthentifizierung für SfB und Exchange wird allgemein verfügbar](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) bzw. [Moderne Authentifizierung für SfB OnPrem mit AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910).

## <a name="app-protection-features"></a>App-Schutzfunktionen

**Was ist die Unterstützung mehrerer Identitäten?**<br></br>
Die Unterstützung mehrerer Identitäten ist die Fähigkeit des Intune App SDK, App-Schutzrichtlinien nur anzuwenden, wenn ein Geschäfts-, Schul- oder Unikonto bei der App angemeldet ist. Wenn ein persönliches Konto bei der App angemeldet ist, kann nicht auf die Daten zugegriffen werden.

**Zu welchem Zweck dient die Unterstützung mehrerer Identitäten?**<br></br>
Dank der Unterstützung mehrerer Identitäten können Apps, die sowohl geschäftlich als auch privat genutzt werden (z. B. die Office-Apps), öffentlich freigegeben werden. Auf die „unternehmenseigenen“ Konten werden die Intune-App-Schutzfunktionen angewendet.

**Funktionieren mehrere Identitäten in Outlook?**<br></br>
Da in Outlook persönliche und „unternehmenseigene“ E-Mails in einer gemeinsamen Ansicht angezeigt werden, fordert die Outlook-App beim Start zur Eingabe der Intune-PIN auf.

**Was ist die Intune-App-PIN?**<br></br>
Die PIN (Personal Identification Number) ist eine Kennung, mit der sichergestellt wird, dass der richtige Benutzer in einer Anwendung auf die Daten der Organisation zugreift.

- **Wann wird ein Benutzer zur Eingabe der PIN aufgefordert?**<br></br> Intune fordert den Benutzer zur Eingabe seiner App-PIN auf, wenn dieser versucht, auf „unternehmenseigene“ Daten zuzugreifen. In Apps mit Unterstützung mehrerer Identitäten wie z. B. Word, Excel oder PowerPoint wird der Benutzer zur PIN-Eingabe aufgefordert, wenn er versucht, ein „unternehmenseigenes“ Dokument oder eine „unternehmenseigene“ Datei zu öffnen. In Apps mit nur einer Identität wie z. B. Branchen-Apps, die über das Intune App Wrapping Tool verwaltet werden, wird der Benutzer beim Start der App zur Eingabe der PIN aufgefordert, da dem Intune App SDK bekannt ist, dass die Verwendung der App immer „unternehmenseigen“ ist.

- **Wie häufig wird ein Benutzer zur Eingabe der Intune-PIN aufgefordert?**<br></br> Der IT-Administrator kann in der Intune-Verwaltungskonsole die Einstellung „Zugriffsanforderungen nach (Minuten) erneut überprüfen“ für die Intune-App-Schutzrichtlinie definieren. Diese Einstellung gibt die Zeitspanne an, nach der die Zugriffsanforderungen auf dem Gerät überprüft werden und der Bildschirm zur Eingabe der PIN erneut angezeigt wird. Folgende Faktoren beeinflussen, wie häufig ein Benutzer zur PIN-Eingabe aufgefordert wird: 

  - **Eine PIN wird für alle Apps des gleichen Herausgebers genutzt, um die Benutzerfreundlichkeit zu erhöhen**: In iOS wird eine gemeinsame App-PIN für alle Apps **des gleichen App-Herausgebers** genutzt. Unter Android wird eine App-PIN für alle Apps genutzt.
  - **Das Verhalten für „Zugriffsanforderungen erneut überprüfen nach (Minuten)“ nach einem Geräteneustart**: Ein „PIN-Timer“ zählt die Anzahl von Minuten der Inaktivität, die angeben, wann die Intune-App-PIN das nächste Mal angezeigt werden soll. Unter iOS hat ein Neustart des Geräts keine Auswirkung auf den PIN-Timer. Das bedeutet, dass ein Neustart des Geräts keine Auswirkung auf die Anzahl der inaktiven Minuten des Benutzers einer iOS-App mit der Intune-PIN-Richtlinie hat. Unter Android wird der PIN-Timer beim Neustart des Geräts zurückgesetzt. Deshalb fordern Android-Apps mit der Intune-PIN-Richtlinie den Benutzer wahrscheinlich unabhängig vom Wert der Einstellung „Zugriffsanforderungen erneut überprüfen nach (Minuten)“ nach dem **Neustart des Geräts** zur Eingabe einer PIN für die App auf.  
  - **Das Wiederholungsverhalten des Timers für die PIN**: Wenn für den Zugriff auf eine App (App A) eine PIN eingegeben wurde und diese App auf dem Gerät nicht mehr im Vordergrund (Haupteingabefokus) ausgeführt wird, wird der PIN-Zeitgeber für diese PIN zurückgesetzt. Eine andere App (App B), für die die gleiche PIN gilt, fordert den Benutzer nicht zur PIN-Eingabe auf, weil der Zeitgeber zurückgesetzt wurde. Die Aufforderung wird wieder angezeigt, wenn der Wert für „Zugriffsanforderungen nach (Minuten) erneut überprüfen“ erneut erreicht wurde.

Selbst wenn die PIN auf iOS-Geräten unter Apps von verschiedenen Herausgebern freigegeben wird, wird die Eingabeaufforderung erneut angezeigt, wenn der Wert für **Zugriffsanforderungen nach (Minuten) erneut überprüfen** erneut für die App erreicht wird, die nicht über den Eingabefokus verfügt. Beispiel: Der Benutzer verfügt über die App _A_ von Herausgeber _X_ und über die App _B_ von Herausgeber _Y_, und für diese Apps wird die gleiche PIN verwendet. Der Benutzer verwendet App _A_ (im Vordergrund), und die App _B_ ist minimiert. Wenn der Wert für **Zugriffsanforderungen nach (Minuten) erneut überprüfen** erreicht wurde und der Benutzer zur App _B_ wechselt, ist eine PIN erforderlich.

  >[!NOTE] 
  > Um die Zugriffsanforderungen des Benutzers (besonders bei häufig verwendeten Apps) öfter zu überprüfen (z. B. die PIN-Eingabeaufforderung), empfiehlt es sich, den Wert für die Einstellung „Zugriffsanforderungen nach (Minuten) erneut überprüfen“ zu senken. 
      
- **Wie funktioniert die Intune-PIN mit integrierten App-PINs für Outlook und OneDrive?**<br></br>
Die Funktionsweise der Intune-PIN basiert auf einem auf Inaktivität basierten Timer (d. h. der Wert von „Zugriffsanforderungen erneut überprüfen nach (Minuten)“). Deshalb werden Aufforderungen zur Eingabe der Intune-PIN unabhängig von Aufforderungen zur Eingabe der integrierten App-PIN für Outlook und OneDrive, die standardmäßig beim Start der App angezeigt werden, angezeigt. Wenn der Benutzer gleichzeitig zur Eingabe beider PINs aufgefordert wird, sollte die Intune-PIN Vorrang haben. 

- **Ist die PIN sicher?**<br></br> Mit der PIN wird sichergestellt, dass nur der richtige Benutzer in der App auf Daten der Organisation zugreifen kann. Ein Endbenutzer muss sich daher mit seinem Geschäfts-, Uni- oder Schulkonto anmelden, bevor er seine Intune-App-PIN festlegen oder zurücksetzen kann. Diese Authentifizierung wird von Azure Active Directory über einen Austausch sicherer Token durchgeführt und ist für das Intune App SDK nicht transparent. Hinsichtlich der Sicherheit ist die beste Möglichkeit, ein Geschäfts-, Uni- oder Schulkonto zu schützen, das Konto zu verschlüsseln. Die Verschlüsselung steht nicht in Zusammenhang mit der App-PIN, sondern stellt eine eigene App-Schutzrichtlinie dar.

- **Wie schützt Intune die PIN vor Brute-Force-Angriffen?**<br></br> Im Rahmen der App-PIN-Richtlinie kann der IT-Administrator festlegen, wie oft ein Benutzer versuchen kann, die PIN zu authentifizieren, bevor die App gesperrt wird. Nachdem die maximale Anzahl von Versuchen erreicht wurde, kann das Intune App SDK die „unternehmenseigenen“ Daten aus der App zurücksetzen.
  
- **Warum muss ich bei Apps desselben Herausgebers zweimal eine PIN festlegen?**<br></br> MAM (für iOS) erlaubt derzeit eine PIN auf Anwendungsebene mit alphanumerischen Zeichen und Sonderzeichen (als „Kennung“ bezeichnet), was die Beteiligung von Anwendungen (z. B. WXP, Outlook, Managed Browser, Yammer) erfordert, damit das Intune App SDK für iOS integriert werden kann. Ohne das SDK werden die Kennungseinstellungen nicht ordnungsgemäß für die Zielanwendungen erzwungen. Hierbei handelte es sich um ein Feature, das im Intune SDK für iOS Version 7.1.12 veröffentlicht wurde. <br><br> Um dieses Feature zu unterstützen und die Abwärtskompatibilität mit früheren Versionen des Intune SDK für iOS zu gewährleisten, werden alle numerischen PINs oder Kennungen in Version 7.1.12 oder höher getrennt von der numerischen PIN in früheren Versionen des SDK verarbeitet. Wenn also ein Gerät Anwendungen mit Intune SDK für iOS-Versionen zwischen 7.1.12 UND 7.1.12 vom selben Hersteller aufweist, müssen sie zwei PINs einrichten. <br><br> Allerdings sind die beiden PINs (für jede App) in keiner Weise miteinander verknüpft, d. h., sie muss die jeweilige für die App geltende App-Schutzrichtlinie einhalten. Daher kann der Benutzer eine PIN *nur* dann zweimal einrichten, wenn für App A und B die gleichen Richtlinien (in Bezug auf die PIN) gelten. <br><br> Dieses Verhalten gilt speziell für die PIN für iOS-Anwendungen, die mit der Intune-Verwaltung mobiler Apps aktiviert sind. Wenn Anwendungen im Laufe der Zeit höhere Intune SDK-Versionen für iOS annehmen, ist das zweimalige Festlegen einer PIN für Apps desselben Herausgebers weniger entscheidend. Beachten Sie den Hinweis unterhalb eines Beispiels.

  >[!NOTE]
  > Beispiel: Wenn App A mit einer niedrigeren Version als 7.1.12 und App B mit einer höheren oder gleichen Version wie 7.1.12 vom selben Herausgeber erstellt wurde, muss der Endbenutzer die PINs für A und B separat einrichten, sofern beide auf einem iOS-Gerät installiert sind. <br><br> Wenn App C mit SDK Version 7.1.9 auf dem Gerät installiert ist, verwendet diese dieselbe PIN wie bei App A. <br><br> App D, die mit 7.1.14 erstellt wurde, verwendet dieselbe PIN wie App B. <br><br> Wenn auf einem Gerät nur App A und C installiert sind, muss eine PIN festgelegt werden. Dasselbe gilt, wenn auf einem Gerät nur App B und D installiert sind.

**Wie funktioniert die Verschlüsselung?**<br></br>
IT-Administratoren können eine App-Schutzrichtlinie bereitstellen, die erzwingt, dass App-Daten verschlüsselt werden. Im Rahmen einer solchen Richtlinie kann ein IT-Administrator auch angeben, wann die Inhalte verschlüsselt werden.

- **Wie verschlüsselt Intune Daten?**<br></br> Ausführliche Informationen zur Verschlüsselungseinstellung im Rahmen von App-Schutzrichtlinien finden Sie unter [Android-Verwaltungsrichtlinieneinstellungen für mobile Apps in Microsoft Intune](app-protection-policy-settings-android.md) und [iOS-Richtlinieneinstellungen für die Verwaltung mobiler Apps](app-protection-policy-settings-ios.md).

- **Was wird verschlüsselt?**<br></br> Nur Daten, die als „unternehmenseigen“ markiert sind, werden gemäß der vom IT-Administrator eingerichteten App-Schutzrichtlinie verschlüsselt. Daten werden als „unternehmenseigen“ betrachtet, wenn sie von einem Speicherort des Unternehmens stammen. Bei den Office-Apps betrachtet Intune Folgendes als Unternehmensspeicher: E-Mail-Speicher (Exchange) oder Cloudspeicher (OneDrive-App mit einem OneDrive for Business-Konto). Bei Branchen-Apps, die vom Intune App Wrapping Tools verwaltet werden, werden alle App-Daten als „unternehmenseigen“ betrachtet.

**Wie setzt Intune Daten remote zurück?**<br></br>
Intune kann App-Daten auf drei Arten zurücksetzen: vollständiges Zurücksetzen des Geräts, selektives Zurücksetzen für MDM und selektives Zurücksetzen für MAM. Weitere Informationen zur Remotezurücksetzung der MDM finden Sie unter [Entfernen von Geräten durch Zurücksetzen oder Abkoppeln](../remote-actions/devices-wipe.md). Weitere Informationen zum selektiven Zurücksetzen mit MAM finden Sie unter [the Retire action (Die Aktion „Abkoppeln“)](../remote-actions/devices-wipe.md#retire) und [Zurücksetzen von Unternehmensdaten in Apps](apps-selective-wipe.md).

- **Was ist Zurücksetzen?**<br></br> Beim [Zurücksetzen](../remote-actions/devices-wipe.md) werden alle Benutzerdaten und -einstellungen vom **Gerät** entfernt, indem die werkseitigen Standardeinstellungen auf dem Gerät wiederhergestellt werden. Das Gerät wird aus Intune entfernt.
  >[!NOTE]
  > Die Zurücksetzung kann nur auf Geräten ausgeführt werden, die mit Intune-MDM registriert sind.

- **Was ist selektives Zurücksetzen für MDM?**<br></br> Informationen zum Entfernen von Unternehmensdaten finden Sie unter [Remove devices - retire (Entfernen von Geräten: Abkoppeln)](../remote-actions/devices-wipe.md#retire).

- **Was ist selektives Zurücksetzen für MAM?**<br></br> Durch selektives Zurücksetzen für MAM können Unternehmensanwendungsdaten von einer App entfernt werden. Die Anforderung wird mithilfe des Azure-Portals für Intune initiiert. Informationen zum Initiieren einer Zurücksetzungsanforderung finden Sie unter [So setzen Sie nur die Unternehmensdaten in einer App zurück](apps-selective-wipe.md).

- **Wie schnell wird das selektive Zurücksetzen für MAM ausgeführt?**<br></br> Wenn das selektive Zurücksetzen initiiert wird, während ein Benutzer die App verwendet, überprüft das Intune App SDK alle 30 Minuten, ob eine Anforderung zum selektiven Zurücksetzen vom Intune MAM-Dienst vorhanden ist. Das SDK überprüft auch, ob eine Anforderung zum selektiven Zurücksetzen vorhanden ist, wenn ein Benutzer eine App zum ersten Mal startet und sich mit einem Geschäfts-, Uni- oder Schulkonto anmeldet.

**Warum funktionieren lokale Dienste nicht mit von Intune geschützten Apps?**<br></br>
Der Intune-App-Schutz basiert darauf, dass die Identität des Benutzers in der App und im Intune App SDK konsistent ist. Die einzige Möglichkeit, dies zu garantieren, ist eine moderne Authentifizierung. Es gibt Szenarien, in denen Apps möglicherweise mit einer lokalen Konfiguration funktionieren. Dies ist aber weder konsistent noch garantiert.

**Gibt es eine sichere Möglichkeit, Weblinks in verwalteten Apps zu öffnen?**<br></br>
Ja! Ein IT-Administrator kann eine App-Schutzrichtlinie für die [Intune Managed Browser-App](../apps/app-configuration-managed-browser.md) einrichten und bereitstellen, ein von Microsoft Intune entwickelter Webbrowser, der problemlos mit Intune verwaltet werden kann. Der IT-Administrator kann festlegen, dass alle Weblinks in über Intune verwaltete Apps mit der Managed Browser-App geöffnet werden müssen.

## <a name="app-experience-on-android"></a>Apps unter Android

**Warum ist die Unternehmensportal-App erforderlich, damit der Intune-App-Schutz auf Android-Geräten funktioniert?**<br></br>
Ein Großteil der App-Schutzfunktionen ist in die Unternehmensportal-App integriert. Eine Registrierung der Geräte ist _nicht erforderlich_, allerdings wird immer die Unternehmensportal-App benötigt. Bei MAM-WE muss lediglich die Unternehmensportal-App auf dem Gerät des Endbenutzers installiert sein.

**Wie funktionieren die verschiedenen Zugriffseinstellungen für den Intune-App-Schutz unter Android, die für mehrere Apps und Benutzer konfiguriert sind?**<br></br>
Zugriffsrichtlinien für den Intune-App-Schutz werden in einer bestimmten Reihenfolge auf den Geräten von Endbenutzern angewendet, wenn diese versuchen, über ihr Unternehmenskonto auf eine App zuzugreifen. In der Regel haben Blöcke Vorrang vor verwerfbaren Warnungen. Es wird z. B. eine Einstellung der mindestens erforderlichen Android-Patch-Version, die den Benutzer auffordert, ein Patchupgrade auszuführen, im Anschluss an die Einstellung angewendet, die dem Benutzer den Zugriff verweigert (wenn dies auf den Benutzer/die App zutrifft). In diesem Szenario konfiguriert der IT-Administrator die Einstellung für die mindestens erforderliche Version des Android-Patch auf den 1.3.2018 und die für die mindestens erforderliche Version des Android-Patch, die nur für Warnungen gilt, auf den 1.2.2018. Gleichzeitig versucht das Gerät, das noch die Patch-Version vom 1.1.2018 verwendet, auf die App zuzugreifen. In Folge dessen wird der Endbenutzer basierend auf restriktiveren Einstellungen für die mindestens erforderliche Version des Android-Patch blockiert und erhält keinen Zugriff. 

Wenn verschiedene Arten von Einstellungen verarbeitet werden müssen, haben die Anforderungen hinsichtlich bestimmter App-Versionen Vorrang. Erst danach werden Anforderungen berücksichtigt, die eine Version des Android-Betriebssystems und Android-Patch-Versionen betreffen. Anschließend werden in derselben Reihenfolge mögliche Warnungen für sämtliche Einstellungstypen überprüft.

**In Intune-App-Schutzrichtlinien können Administratoren festlegen, dass Endbenutzergeräte SafetyNet Attestation von Google für Android-Geräte übergeben müssen. Wie oft wird ein neues SafetyNet Attestation-Ergebnis an den Dienst gesendet?** <br><br> Eine neue Google Play-Dienstbestimmung wird in einem von Intune festgelegten Intervall an den IT-Administrator gesendet. Die Anzahl der Dienstaufrufe wird in Abhängigkeit von der Last gedrosselt; dieser Wert wird also intern verwaltet und kann nicht konfiguriert werden. Jede Aktion für die Einstellung von SafetyNet Attestation von Google, die von einem IT-Administrator konfiguriert wurde, wird auf Grundlage des zuletzt an Intune gemeldeten Ergebnisses zum Zeitpunkt des bedingten Starts ausgeführt. Wenn keine Daten vorhanden sind, wird der Zugriff abhängig davon gewährt, dass keine anderen Überprüfungen für den bedingten Start fehlschlagen, und der „Roundtrip“ des Google Play-Diensts zur Bestimmung der Nachweisergebnisse im Back-End startet. Wenn es beim Gerät zu Problemen kommt, wird der Benutzer asynchron benachrichtigt. Wenn die Daten veraltet sind, wird der Zugriff auf Grundlage des zuletzt gemeldeten Ergebnisses blockiert oder gewährt, und ein „Roundtrip“ des Google Play-Diensts zur Bestimmung der Nachweisergebnisse startet. Wenn es beim Gerät zu Problemen kommt, wird der Benutzer asynchron benachrichtigt.

**In Intune-App-Schutz-Richtlinien können Administratoren festlegen, dass Endbenutzergeräte Signale über die Verify Apps-API von Google für Android-Geräte (API von Google für die Überprüfung von Apps für Android-Geräte) senden müssen. Wie können Endbenutzer die Überprüfung der App aktivieren, sodass der Zugriff für sie aufgrund einer solchen Richtlinie nicht blockiert wird?**<br><br> Die dafür erforderlichen Schritte unterscheiden sich leicht je nach Gerät. Grundsätzlich müssen Sie dafür den Google Play Store besuchen, dort auf **My apps & games** (Meine Apps und Spiele) klicken und dann auf das Ergebnis der letzten App-Überprüfung klicken. Dadurch gelangen Sie zum Play Protect-Menü. Sorgen Sie dafür, dass die Option **Scan device for security threats** (Gerät auf Sicherheitsbedrohungen überprüfen) aktiviert ist.

**Was genau überprüft die SafetyNet Attestation-API von Google auf Android-Geräten eigentlich? Worin besteht der Unterschied zwischen den konfigurierbaren Werten von „Check basic integrity“ (Basisintegrität überprüfen) und „Check basic integrity & certified devices“ (Basisintegrität und zertifizierte Geräte überprüfen)?** <br><br>
Für Intune werden die Google Play Protect SafetyNet-APIs verwendet, um die vorhandenen Überprüfungen auf Rootingerkennung für nicht registrierte Geräte zu ergänzen. Google hat diese APIs für Android-Apps entwickelt und verwaltet sie, wenn die Apps nicht auf gerooteten Geräten ausgeführt werden sollen. Sie kommen z. B. bei der Google Pay-App zum Einsatz. Google stellt zwar nicht alle Überprüfungen, die durchgeführt werden, um Rooting zu erkennen, öffentlich zur Verfügung; wir gehen jedoch davon aus, dass diese APIs Benutzer identifizieren können, die ihr Gerät gerootet haben. Diesen Benutzern kann der Zugriff dann verwehrt werden, oder ihre Unternehmenskonten können aus den Apps entfernt werden, für die Richtlinien aktiviert sind. Die Option „Check basic integrity“ (Basisintegrität überprüfen) informiert Sie über die allgemeine Integrität des Geräts. Für gerootete Geräte, Emulatoren, virtuelle Geräte und Geräte, die Anzeichen von Manipulationen aufweisen, schlägt die Überprüfung der grundlegenden Integrität fehl. Die Option „Check basic integrity & certified devices“ (Basisintegrität und zertifizierte Geräte überprüfen) informiert Sie über die Kompatibilität des Geräts mit Google-Diensten. Nur unveränderte Geräte, die von Google zertifiziert wurden, bestehen diese Überprüfung. Die folgenden Geräte bestehen die Überprüfung nicht:

- Geräte, für die die Überprüfung der Basisintegrität fehlschlägt
- Geräte mit entsperrtem Bootloader
- Geräte mit einem benutzerdefinierten Systemimage/ROM
- Geräte, für die der Hersteller entweder keine Google-Zertifizierung beantragt hat, oder für die diese nicht bestanden wurde 
- Geräte mit einem Systemimage, das direkt aus den Quelldateien des Open Source-Programms für Android erstellt wurde
- Geräte mit einem Systemimage, das sich noch in der Betaversion oder in der Entwicklervorschau befindet

Technische Details finden Sie in der [Dokumentation von Google zu „SafetyNet Attestation“](https://developer.android.com/training/safetynet/attestation).

**Beim Erstellen einer Intune-App-Schutzrichtlinie für Android-Geräte gibt es im Bereich „Conditional Launch“ (Bedingter Start) zwei ähnliche Überprüfungen. Sollte als Anforderung die Einstellung „SafetyNet device attestation“ (SafetyNet-Gerätenachweis) oder die Einstellung „jailbroken/rooted devices“ (Mit Jailbreak oder Rooting manipulierte Geräte) verwendet werden?** <br><br>
Die Überprüfungen im Rahmen der SafetyNet-API von Google Play Protect erfordern, dass der Endbenutzer online ist, zumindest während der Zeit, in der der „Roundtrip“ zur Bestimmung von Nachweisergebnissen ausgeführt wird. Wenn der Endbenutzer offline ist, kann der IT-Administrator immer noch davon ausgehen, dass ein Ergebnis der Einstellung „jailbroken/rooted devices“ (Mit Jailbreak oder Rooting manipulierte Geräte) erzwungen wird. Vor diesem Hintergrund kommt der Wert „Offline grace period“ (Offlinetoleranzperiode) ins Spiel, wenn der Endbenutzer zu lange offline war, und sobald der Zeitwert erreicht wird, wird der Zugriff auf Unternehmens- oder Schuldaten solange blockiert, bis wieder Netzwerkzugriff besteht. Wenn beide Einstellungen aktiviert werden, steht Ihnen ein mehrstufiger Ansatz zur Verfügung, um die Integrität von Endbenutzergeräten zu gewährleisten, was wichtig ist, wenn Endbenutzer über Mobilgeräte auf Unternehmens- und Schuldaten zugreifen. 

**Für die Schutzrichtlinieneinstellungen für Apps, die APIs von Google Play Protect verwenden, muss Google Play Services funktionieren. Was ist, wenn Google Play Services am Standort des Endbenutzers nicht zulässig sind?**<br><br>
Für die beiden Einstellungen „SafetyNet device attestation“ (SafetyNet-Gerätenachweis) und „Threat scan on apps“ (Apps auf Bedrohungen überprüfen) muss die von Google bestimmte Version von Google Play Services ordnungsgemäß funktionieren. Da diese Einstellungen in den Sicherheitsbereich fallen, werden die Endbenutzer blockiert, für die diese Einstellungen gelten, wenn diese nicht die entsprechende Version von Google Play Services verwenden oder keinen Zugriff auf Google Play Services haben. 

## <a name="app-experience-on-ios"></a>Apps unter iOS
**Was geschieht, wenn ich einen Fingerabdruck oder ein Gesicht auf meinem Gerät hinzufüge oder entferne?**<br></br>
Die Richtlinien für den Intune-App-Schutz ermöglichen es Ihnen, den App-Zugriff nur auf Benutzer mit Intune-Lizenz zu beschränken. Eine der Möglichkeiten, den Zugriff auf die App zu steuern, besteht darin, Apple Touch ID oder Face ID auf unterstützten Geräten zu erfordern. Intune implementiert ein Verhalten, bei dem Intune den Benutzer bei Änderungen an der biometrischen Datenbank des Geräts zur PIN-Eingabe auffordert, wenn der nächste Wert des Inaktivitätstimeouts erfüllt ist. Zu Änderungen an biometrischen Daten zählen das Hinzufügen oder Entfernen von Fingerabdrücken oder Gesichtern. Wenn der Intune-Benutzer keine PIN festgelegt hat, wird er zu einem Fenster für die Einrichtung einer Intune-PIN weitergeleitet.

Durch diese Maßnahmen sollen die Daten Ihrer Organisation innerhalb der App und auf App-Ebene geschützt werden. Dieses Feature ist nur für iOS verfügbar und erfordert, dass das Intune App SDK für iOS, Version 9.0.1 oder höher in betreffende Anwendungen integriert wird. Die Integration des SDK ist erforderlich, damit das Verhalten für die Zielanwendungen erzwungen werden kann. Diese Integration erfolgt kontinuierlich und ist abhängig von den jeweiligen Anwendungsteams. Zu den betreffenden Apps zählen z. B. WXP, Outlook, Managed Browser und Yammer.
  
**Ich kann die iOS-Freigabeerweiterung verwenden, um Geschäfts-, Uni- oder Schuldaten in nicht verwalteten Apps zu öffnen, auch wenn die Datenübertragungsrichtlinie auf „nur verwaltete Apps“ oder „keine Apps“ festgelegt ist. Führt das nicht zu Datenlecks?**<br></br>
Die Intune-App-Schutzrichtlinie kann die iOS-Freigabeerweiterung nicht steuern, ohne das Gerät zu verwalten. Daher _**verschlüsselt Intune „unternehmenseigene“ Daten, bevor diese außerhalb der App freigegeben werden**_ . Sie können dies überprüfen, indem Sie versuchen, die „unternehmenseigene“ Datei außerhalb der verwalteten App zu öffnen. Die Datei sollte verschlüsselt sein und außerhalb der verwalteten App nicht geöffnet werden können.

**Wie funktionieren die verschiedenen Zugriffseinstellungen für den Intune-App-Schutz unter iOS, die für dieselben Apps und Benutzer konfiguriert sind?**<br></br>
Zugriffsrichtlinien für den Intune-App-Schutz werden in einer bestimmten Reihenfolge auf den Geräten von Endbenutzern angewendet, wenn diese versuchen, über ihr Unternehmenskonto auf eine App zuzugreifen. In der Regel hat ein Zurücksetzungsvorgang Vorrang vor einem Block. Verwerfbare Warnungen werden erst als letztes berücksichtigt. Es wird z. B. eine Einstellung der mindestens erforderlichen iOS-Version, die den Benutzer auffordert, ein Update des Betriebssystems auszuführen, im Anschluss an die Einstellung angewendet, die dem Benutzer den Zugriff verweigert (wenn dies auf den Benutzer/die App zutrifft). In diesem Szenario konfiguriert der IT-Administrator die Einstellung für die mindestens erforderliche iOS-Version auf Version 11.0.0.0 und die mindestens erforderliche iOS-Version, die nur für Warnungen gilt, auf 11.1.0.0. Gleichzeitig versucht das Gerät, auf dem noch die iOS-Version 10 installiert ist, auf die App zuzugreifen. In Folge dessen wird der Endbenutzer basierend auf restriktiveren Einstellungen für die mindestens erforderliche iOS-Version blockiert und erhält keinen Zugriff.

Wenn verschiedene Arten von Einstellungen verarbeitet werden müssen, haben die Anforderungen hinsichtlich bestimmter Versionen des Intune App SDK Vorrang. Erst danach werden Anforderungen berücksichtigt, die eine Version einer App oder eines iOS-Betriebssystems betreffen. Anschließend werden in derselben Reihenfolge mögliche Warnungen für sämtliche Einstellungstypen überprüft. Es wird empfohlen, die Anforderung, die die Intune App SDK-Version betrifft, nur unter Anleitung des Intune-Produktteams für grundlegende Blockierungsszenarios zu konfigurieren.


## <a name="see-also"></a>Weitere Informationen:
- [Implementieren Ihres Intune-Plans](../fundamentals/planning-guide-onboarding.md)
- [Testen und Überprüfen von Intune](../fundamentals/planning-guide-test-validation.md)
- [Android-Richtlinieneinstellungen für die Verwaltung mobiler Apps in Microsoft Intune](../apps/app-protection-policy-settings-android.md)
- [iOS-Richtlinieneinstellungen für die Verwaltung mobiler Apps](../apps/app-protection-policy-settings-ios.md)
- [App protection policies policy refresh (Zustellung von App-Schutzrichtlinien)](../apps/app-protection-policy-delivery.md)
- [Überprüfen Ihrer App-Schutzrichtlinien](../apps/app-protection-policy-delivery.md)
- [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Apps ohne Geräteregistrierung](../apps/app-configuration-policies-managed-app.md)
- [Anfordern von Support für Microsoft Intune](../fundamentals/get-support.md)
