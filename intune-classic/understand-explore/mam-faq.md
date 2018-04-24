---
title: Häufig gestellte Fragen zu MAM und App-Schutz
description: Dieser Artikel beantwortet einige häufig gestellte Fragen zur mobilen Anwendungsverwaltung (Mobile Application Management, MAM) und zum App-Schutz in Intune.
keywords: ''
author: oydang
ms.author: oydang
manager: dougeby
ms.date: 01/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 816a235136d91f2691e6be442036515544c004b2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Häufig gestellte Fragen zu MAM und App-Schutz

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Dieser Artikel beantwortet einige häufig gestellte Fragen zur mobilen Anwendungsverwaltung (Mobile Application Management, MAM) und zum App-Schutz in Intune.

## <a name="mam-basics"></a>Grundlagen zu MAM


**Was ist MAM?** Die [mobile Anwendungsverwaltung (Mobile Application Management, MAM) von Intune](/intune/app-lifecycle) bezeichnet die Intune-Verwaltungsfunktionen, mit denen Sie mobile Apps für Ihre Benutzer veröffentlichen, per Push bereitstellen, konfigurieren, schützen, überwachen und aktualisieren.

**Welche Vorteile bietet der App-Schutz von MAM?** MAM schützt die Daten einer Organisation innerhalb einer Anwendung. Mit MAM-WE kann eine Geschäfts-, Schul- oder Uni-App, die vertrauliche Daten enthält, auf nahezu jedem Gerät verwaltet werden, auch auf persönlichen Geräten in BYOD-Szenarien (Bring Your Own Device). Viele Produktivitäts-Apps, wie z.B. die Microsoft Office-Apps, können über Intune MAM verwaltet werden. Weitere Informationen finden Sie in der Liste von in [Intune verwalteten Apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps), die für die Öffentlichkeit verfügbar sind.

**Welche Gerätekonfigurationen unterstützt MAM?** Intune MAM unterstützt zwei Konfigurationen:
  1. **Intune MDM und MAM**: Dies ist die erste Konfiguration, die bei der ersten Einführung von MAM unterstützt wurde. IT-Administratoren können Apps mithilfe von MAM und App-Schutzrichtlinien nur auf Geräten verwalten, die bei der Intune-Verwaltung mobiler Geräte (Mobile Device Management, MDM) registriert sind. Um Apps über MDM und MAM zu verwalten, sollten Kunden die eigenständige Intune-Konsole unter https://manage.microsoft.com verwenden.

  2. **MAM ohne Geräteregistrierung**: Mit MAM ohne Geräteregistrierung (MAM without enrollment, MAM-WE) können IT-Administratoren Apps mithilfe von MAM und App-Schutzrichtlinien auf Geräten verwalten, die nicht bei Intune MDM registriert sind. Dies bedeutet, dass Apps über Intune auf Geräten verwaltet werden können, die bei EMM-Drittanbietern registriert sind. Um Apps mithilfe von MAM-WE zu verwalten, sollten Kunden unter http://portal.azure.com die Intune-Konsole im Azure-Portal verwenden.


## <a name="app-protection-policies"></a>App-Schutzrichtlinien

**Was sind App-Schutzrichtlinien?** App-Schutzrichtlinien sind Regeln, die sicherstellen, dass die Daten einer Organisation in einer verwalteten App jederzeit sicher sind und dort verbleiben. Eine Richtlinie kann eine Regel sein, die erzwungen wird, wenn ein Benutzer versucht, auf „unternehmenseigene“ Daten zuzugreifen oder diese zu verschieben. Es kann sich auch um eine Reihe von Aktionen handeln, die nicht zulässig sind oder überwacht werden, wenn sich ein Benutzer in der App befindet.

**Was sind Beispiele für App-Schutzrichtlinien?** Ausführliche Informationen zu den einzelnen Einstellungen für App-Schutzrichtlinien finden Sie unter [Android-Verwaltungsrichtlinieneinstellungen für mobile Apps in Microsoft Intune](../deploy-use/android-mam-policy-settings.md) und [iOS-Richtlinieneinstellungen für die Verwaltung mobiler Apps](../deploy-use/ios-mam-policy-settings.md).

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Apps, die mit App-Schutzrichtlinien verwaltet werden können

**Welche Apps können mithilfe von App-Schutzrichtlinien verwaltet werden?** Jede App, die über das [Intune App SDK](/intune/app-sdk) aktiviert oder vom [Intune App Wrapping Tool](/intune/apps-prepare-mobile-application-management) gepackt wurde, kann mithilfe von Intune-App-Schutzrichtlinien verwaltet werden. Weitere Informationen finden Sie in der Liste von in [Intune verwalteten Apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps), die für die Öffentlichkeit verfügbar sind.

**Welche grundlegenden Anforderungen bestehen für die Verwendung von App-Schutzrichtlinien in einer mit Intune verwalteten App?**
  1. Der Endbenutzer muss über ein Azure Active Directory-Konto (AAD) verfügen. Informationen dazu, wie Sie Intune-Benutzer in Azure Active Directory erstellen, finden Sie unter [Hinzufügen von Benutzern und Gewähren von Administratorrechten für Intune](/intune/users-permissions-add).

  2. Dem AAD-Konto des Endbenutzers muss eine Lizenz für Microsoft Intune zugewiesen sein. Informationen zum Zuweisen von Intune-Lizenzen zu Endbenutzern finden Sie unter [Verwalten von Intune-Lizenzen](/intune/licenses-assign).

  3. Der Endbenutzer muss zu einer Sicherheitsgruppe gehören, für die eine App-Schutzrichtlinie gilt. Die gleiche App-Schutzrichtlinie muss für die verwendete App gelten. App-Schutzrichtlinien können in der Intune-Konsole im [Azure-Portal](http://portal.azure.com) erstellt und bereitgestellt werden. Sicherheitsgruppen können zurzeit im [Office-Portal](http://portal.office.com) erstellt werden.

  4. Der Endbenutzer muss sich mit seinem AAD-Konto bei der App anmelden.

**Welche zusätzlichen Anforderungen gelten für die Verwendung der [mobilen Outlook-App](https://www.microsoft.com/outlook-com/mobile/)?**

1. Die mobile Outlook-App muss auf dem Gerät des Endbenutzers installiert sein.

2. Das [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online)-Postfach und die zugehörige Lizenz des Endbenutzers müssen mit dem AAD-Konto des Endbenutzers verknüpft sein.

   >[!NOTE]
   > Die mobile Outlook-App unterstützt derzeit nur Microsoft Exchange Online, nicht jedoch lokales Exchange oder Exchange in Office 365 dediziert.

**Welche zusätzlichen Anforderungen gelten für die Verwendung der [Word-, Excel- und PowerPoint](https://products.office.com/business/office)-Apps?**

1. Mit dem AAD-Konto des Endbenutzers muss eine Lizenz für [Office 365 Business oder Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) verknüpft sein. Das Abonnement muss die Office-Apps auf mobilen Geräten enthalten und kann ein Cloudspeicherkonto mit [OneDrive for Business](https://onedrive.live.com/about/business/) umfassen. Office 365-Lizenzen können im [Office-Portal](http://portal.office.com) zugewiesen werden. Befolgen Sie diese [Anweisungen](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

2. Der Benutzer muss über einen verwalteten konfigurierten Speicherort verfügen. Dieser wird mithilfe der Funktion „Speichern unter“ unter der Einstellung für die Anwendungsschutzrichtlinie zum Verhindern von „Speichern unter“ konfiguriert. Wenn beispielsweise der verwaltete Speicherort OneDrive ist, muss die [OneDrive](https://onedrive.live.com/about/)-App in der Word-, Excel- oder PowerPoint-App des Benutzer konfiguriert werden.

3. Wenn der verwaltete Speicherort OneDrive ist, muss die App unter die App-Schutzrichtlinie fallen, die für den Benutzer angegeben ist.

   >[!NOTE]
   > Die mobilen Office-Apps unterstützen zurzeit nur SharePoint Online, nicht jedoch SharePoint lokal.

**Warum wird ein verwalteter Speicherort (z.B. OneDrive) für Office benötigt?** Intune kennzeichnet alle Daten in der App entweder als „unternehmenseigen“ oder „persönlich“. Daten werden als „unternehmenseigen“ betrachtet, wenn sie von einem Speicherort des Unternehmens stammen. Bei den Office-Apps betrachtet Intune Folgendes als Unternehmensspeicher: E-Mail-Speicher (Exchange) oder Cloudspeicher (OneDrive-App mit einem OneDrive for Business-Konto).

**Welche zusätzlichen Anforderungen gelten für die Verwendung von Skype for Business?** Informationen hierzu finden Sie in den Lizenzanforderungen für [Skype for Business](https://products.office.com/skype-for-business/it-pros).
  >[!NOTE]
  > Die mobile Skype for Business-App unterstützt zurzeit nur Skype for Business Online.

## <a name="app-protection-features"></a>App-Schutzfunktionen

**Was ist die Unterstützung mehrerer Identitäten?** Die Unterstützung mehrerer Identitäten ist die Fähigkeit des Intune App SDK, App-Schutzrichtlinien nur anzuwenden, wenn ein Geschäfts-, Schul- oder Unikonto bei der App angemeldet ist. Wenn ein persönliches Konto bei der App angemeldet ist, kann nicht auf die Daten zugegriffen werden.

**Zu welchem Zweck dient die Unterstützung mehrerer Identitäten?** Dank der Unterstützung mehrerer Identitäten können Apps, die sowohl geschäftlich als auch privat genutzt werden (z.B. die Office-Apps), öffentlich freigegeben werden. Auf die „unternehmenseigenen“ Konten werden die Intune-App-Schutzfunktionen angewendet.

**Funktionieren mehrere Identitäten in Outlook?** Da in Outlook persönliche und „unternehmenseigene“ E-Mails in einer gemeinsamen Ansicht angezeigt werden, fordert die Outlook-App beim Start zur Eingabe der Intune-PIN auf.

**Was ist die Intune-App-PIN?** Die PIN (Personal Identification Number) ist eine Kennung, mit der sichergestellt wird, dass der richtige Benutzer in einer Anwendung auf die Daten der Organisation zugreift.

  1. **Wann wird ein Benutzer zur Eingabe der PIN aufgefordert?** Intune fordert nur dann zur Eingabe der PIN auf, wenn ein Benutzer versucht, auf „unternehmenseigene“ Daten zuzugreifen. In Apps mit Unterstützung mehrerer Identitäten wie z.B. Word, Excel oder PowerPoint wird der Benutzer zur PIN-Eingabe aufgefordert, wenn er versucht, ein „unternehmenseigenes“ Dokument oder eine „unternehmenseigene“ Datei zu öffnen. In Apps mit nur einer Identität wie z.B. Branchen-Apps, die über das Intune App Wrapping Tool aktiviert wurden, wird der Benutzer beim Start der App zur Eingabe der PIN aufgefordert, da dem Intune App SDK bekannt ist, dass die Verwendung der App immer „unternehmenseigen“ ist.

2. **Wie häufig wird ein Benutzer zur Eingabe der Intune-PIN aufgefordert?**
Der IT-Administrator kann in der Intune-Verwaltungskonsole die Einstellung „Zugriffsanforderungen nach (Minuten) erneut überprüfen“ für die Intune-App-Schutzrichtlinie definieren. Diese Einstellung gibt die Zeitspanne an, nach der die Zugriffsanforderungen auf dem Gerät überprüft werden und der Bildschirm zur Eingabe der PIN erneut angezeigt wird. Folgende Faktoren beeinflussen, wie häufig ein Benutzer zur PIN-Eingabe aufgefordert wird: 

* **Die PIN gilt für mehrere Apps des gleichen Herausgebers, um die Benutzerfreundlichkeit zu verbessern:** Unter iOS wird eine App-PIN für alle Apps **des gleichen Herausgebers** genutzt. Unter Android wird eine App-PIN für alle Apps genutzt.
* **Die Natur des Zeitgebers, der mit der PIN verknüpft ist:** Wenn für den Zugriff auf eine App (App A) eine PIN eingegeben wurde und diese App nicht mehr im Vordergrund (Haupteingabefokus) ausgeführt wird, wird der PIN-Zeitgeber für diese PIN zurückgesetzt. Eine andere App (App B), für die die gleiche PIN gilt, fordert den Benutzer nicht zur PIN-Eingabe auf, weil der Zeitgeber zurückgesetzt wurde. Die Aufforderung wird wieder angezeigt, wenn der Wert für „Zugriffsanforderungen nach (Minuten) erneut überprüfen“ erneut erreicht wurde. 

>[!NOTE] 
> Um die Zugriffsanforderungen für einen Benutzer häufiger zu überprüfen (also die PIN-Eingabe anzufordern), empfiehlt es sich insbesondere bei häufig genutzten Apps, den Wert für die Einstellung „Zugriffsanforderungen nach (Minuten) erneut überprüfen“ zu senken. 

  3. **Ist die PIN sicher?** Mit der PIN wird sichergestellt, dass nur der richtige Benutzer in der App auf Daten der Organisation zugreifen kann. Ein Endbenutzer muss sich daher mit seinem Geschäfts-, Uni- oder Schulkonto anmelden, bevor er seine Intune-App-PIN festlegen oder zurücksetzen kann. Diese Authentifizierung wird von Azure Active Directory über einen Austausch sicherer Token durchgeführt und ist für das Intune App SDK nicht transparent. Hinsichtlich der Sicherheit ist die beste Möglichkeit, ein Geschäfts-, Uni- oder Schulkonto zu schützen, das Konto zu verschlüsseln. Die Verschlüsselung steht nicht in Zusammenhang mit der App-PIN, sondern stellt eine eigene App-Schutzrichtlinie dar.

  4. **Wie schützt Intune die PIN vor Brute-Force-Angriffen?** Im Rahmen der App-PIN-Richtlinie kann der IT-Administrator festlegen, wie oft ein Benutzer versuchen kann, die PIN zu authentifizieren, bevor die App gesperrt wird. Nachdem die maximale Anzahl von Versuchen erreicht wurde, kann das Intune App SDK die „unternehmenseigenen“ Daten aus der App zurücksetzen.
  
  5. **Warum muss ich bei Apps desselben Herausgebers zweimal eine PIN festlegen?**
MAM (für iOS) erlaubt derzeit eine PIN auf Anwendungsebene mit alphanumerischen Zeichen und Sonderzeichen (als „Kennung“ bezeichnet), was die Teilnahme von Anwendungen (z.B. WXP, Outlook, Managed Browser, Yammer) erfordert, damit das Intune App SDK für iOS integriert werden kann. Ohne das SDK werden die Kennungseinstellungen nicht ordnungsgemäß für die Zielanwendungen erzwungen. Hierbei handelte es sich um ein Feature, das im Intune SDK für iOS Version 7.1.12 veröffentlicht wurde. <br> Um dieses Feature zu unterstützen und die Abwärtskompatibilität mit früheren Versionen des Intune SDK für iOS zu gewährleisten, werden alle numerischen PINs oder Kennungen in Version 7.1.12 oder höher getrennt von der numerischen PIN in früheren Versionen des SDK verarbeitet. Wenn also ein Gerät Anwendungen mit Intune SDK für iOS-Versionen zwischen 7.1.12 UND 7.1.12 vom selben Hersteller aufweist, müssen sie zwei PINs einrichten. <br><br> Allerdings sind die beiden PINs (für jede App) in keiner Weise miteinander verknüpft, d.h., sie muss die jeweilige für die App geltende App-Schutzrichtlinie einhalten. Daher kann der Benutzer eine PIN *nur* dann zweimal einrichten, wenn für App A und B die gleichen Richtlinien (in Bezug auf die PIN) gelten. <br><br> Dieses Verhalten gilt speziell für die PIN für iOS-Anwendungen, die mit der Verwaltung mobiler Apps von Intune aktiviert sind. Wenn Anwendungen im Laufe der Zeit höhere Intune SDK-Versionen für iOS annehmen, ist das zweimalige Festlegen einer PIN für Apps desselben Herausgebers weniger entscheidend. Beachten Sie den Hinweis unterhalb eines Beispiels.

>[!NOTE]
> Beispiel: Wenn App A mit einer niedrigeren Version als 7.1.12 und App B mit einer höheren oder gleichen Version wie 7.1.12 vom selben Herausgeber erstellt wurde, muss der Endbenutzer die PINs für A und B separat einrichten, sofern beide auf einem iOS-Gerät installiert sind. <br> Wenn App C mit SDK Version 7.1.9 auf dem Gerät installiert ist, verwendet diese dieselbe PIN wie bei App A. <br> App D, die mit 7.1.14 erstellt wurde, verwendet dieselbe PIN wie App B. <br> Wenn auf einem Gerät nur App A und C installiert sind, muss eine PIN festgelegt werden. Dasselbe gilt, wenn auf einem Gerät nur App B und D installiert sind.

**Wie funktioniert die Verschlüsselung?** IT-Administratoren können eine App-Schutzrichtlinie bereitstellen, die erzwingt, dass App-Daten verschlüsselt werden. Im Rahmen einer solchen Richtlinie kann ein IT-Administrator auch angeben, wann die Inhalte verschlüsselt werden.

  1. **Wie verschlüsselt Intune Daten?** Ausführliche Informationen zur Verschlüsselungseinstellung im Rahmen von App-Schutzrichtlinien finden Sie unter [Android-Verwaltungsrichtlinieneinstellungen für mobile Apps in Microsoft Intune](../deploy-use/android-mam-policy-settings.md) und [iOS-Richtlinieneinstellungen für die Verwaltung mobiler Apps](../deploy-use/ios-mam-policy-settings.md).

  2. **Was wird verschlüsselt?** Nur Daten, die als „unternehmenseigen“ markiert sind, werden gemäß der vom IT-Administrator eingerichteten App-Schutzrichtlinie verschlüsselt. Daten werden als „unternehmenseigen“ betrachtet, wenn sie von einem Speicherort des Unternehmens stammen. Bei den Office-Apps betrachtet Intune Folgendes als Unternehmensspeicher: E-Mail-Speicher (Exchange) oder Cloudspeicher (OneDrive-App mit einem OneDrive for Business-Konto). Bei Branchen-Apps, die mithilfe des Intune App Wrapping Tools aktiviert wurden, werden alle App-Daten als „unternehmenseigen“ betrachtet.

**Wie setzt Intune Daten remote zurück?** Intune kann App-Daten auf drei Arten zurücksetzen: vollständiges Zurücksetzen des Geräts, selektives Zurücksetzen für MDM und selektives Zurücksetzen für MAM. Weitere Informationen zur Remotezurücksetzung für MDM finden Sie unter [Schützen von Daten durch vollständiges oder selektives Zurücksetzen mit Microsoft Intune](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md). Weitere Informationen zum selektiven Zurücksetzen unter Verwendung von MAM finden Sie unter [Zurücksetzen von verwalteten Unternehmensanwendungsdaten mit Microsoft Intune](../deploy-use/wipe-managed-company-app-data-with-microsoft-intune.md)

1. **Was ist vollständiges Zurücksetzen?** Beim [vollständigen Zurücksetzen](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe) werden alle Benutzerdaten und -einstellungen vom **Gerät** entfernt, indem das Gerät auf die werkseitigen Standardeinstellungen zurückgesetzt wird. Das Gerät wird aus Intune entfernt.
   >[!NOTE]
   > Ein vollständiges Zurücksetzen kann nur auf Geräten erreicht werden, die bei der mobilen Intune-Geräteverwaltung registriert sind.

2. **Was ist selektives Zurücksetzen für MDM?** Informationen zum selektiven Zurücksetzen finden Sie unter [Schützen von Daten durch vollständiges oder selektives Zurücksetzen mit Microsoft Intune](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe).

3. **Was ist selektives Zurücksetzen für MAM?** Durch selektives Zurücksetzen für MAM können Unternehmensanwendungsdaten von einer App entfernt werden. Die Anforderung wird mithilfe des Azure-Portals für Intune initiiert. Weitere Informationen zum Initiieren einer Zurücksetzungsanforderung erhalten Sie unter [Zurücksetzen von verwalteten Unternehmensanwendungsdaten mit Microsoft Intune](../deploy-use/wipe-managed-company-app-data-with-microsoft-intune.md).

4. **Wie schnell wird das selektive Zurücksetzen für MAM ausgeführt?** Wenn das selektive Zurücksetzen initiiert wird, während ein Benutzer die App verwendet, überprüft das Intune App SDK alle 30 Minuten, ob eine Anforderung zum selektiven Zurücksetzen vom Intune MAM-Dienst vorhanden ist. Das SDK überprüft auch, ob eine Anforderung zum selektiven Zurücksetzen vorhanden ist, wenn ein Benutzer eine App zum ersten Mal startet und sich mit einem Geschäfts-, Uni- oder Schulkonto anmeldet.

**Warum funktionieren lokale Dienste nicht mit von Intune geschützten Apps?** Der Intune-App-Schutz basiert darauf, dass die Identität des Benutzers in der App und im Intune App SDK konsistent ist. Die einzige Möglichkeit, dies zu garantieren, ist eine moderne Authentifizierung. Es gibt Szenarien, in denen Apps möglicherweise mit einer lokalen Konfiguration funktionieren. Dies ist aber weder konsistent noch garantiert.

**Gibt es eine sichere Möglichkeit, Weblinks in verwalteten Apps zu öffnen?** Ja! Ein IT-Administrator kann eine App-Schutzrichtlinie für die [Intune Managed Browser-App](../deploy-use/manage-internet-access-using-managed-browser-policies.md) einrichten und bereitstellen, ein von Microsoft Intune entwickelter Webbrowser, der problemlos mit Intune verwaltet werden kann. Der IT-Administrator kann festlegen, dass alle Weblinks in über Intune verwaltete Apps mit der Managed Browser-App geöffnet werden müssen.


## <a name="app-experience-on-android"></a>Apps unter Android

**Warum ist die Unternehmensportal-App erforderlich, damit der Intune-App-Schutz auf Android-Geräten funktioniert?** Ein Großteil der App-Schutzfunktionen ist in die Unternehmensportal-App integriert. Eine Registrierung der Geräte ist _nicht erforderlich_, allerdings wird immer die Unternehmensportal-App benötigt. Bei MAM-WE muss lediglich die Unternehmensportal-App auf dem Gerät des Endbenutzers installiert sein.

## <a name="app-experience-on-ios"></a>Apps unter iOS

**Ich kann die iOS-Freigabeerweiterung verwenden, um Geschäfts-, Uni- oder Schuldaten in nicht verwalteten Apps zu öffnen, auch wenn die Datenübertragungsrichtlinie auf „nur verwaltete Apps“ oder „keine Apps“ festgelegt ist. Führt das nicht zu Datenlecks?** Die Intune-App-Schutzrichtlinie kann die iOS-Freigabeerweiterung nicht steuern, ohne das Gerät zu verwalten. Daher _**verschlüsselt Intune „unternehmenseigene“ Daten, bevor diese außerhalb der App freigegeben werden**_. Sie können dies überprüfen, indem Sie versuchen, die „unternehmenseigene“ Datei außerhalb der verwalteten App zu öffnen. Die Datei sollte verschlüsselt sein und außerhalb der verwalteten App nicht geöffnet werden können.

### <a name="see-also"></a>Siehe auch
- [Android-Richtlinieneinstellungen für die Verwaltung mobiler Apps in Microsoft Intune](../deploy-use/android-mam-policy-settings.md)
- [iOS-Richtlinieneinstellungen für die Verwaltung mobiler Apps](../deploy-use/ios-mam-policy-settings.md)
- [Überprüfen des Setups für die Verwaltung Ihrer mobilen Anwendungen](../deploy-use/validate-mobile-application-management.md)
- [Vorbereiten der Konfiguration von Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
- [Anfordern von Support für Microsoft Intune](../troubleshoot/how-to-get-support-for-microsoft-intune.md)
