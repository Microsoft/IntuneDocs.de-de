---
title: Was ist Microsoft Intune?
description: Erfahren Sie mehr zu Intune, der Komponente der „Enterprise Mobility + Security“-Lösung für die Verwaltung mobiler Geräte (MDM) und die Verwaltung mobiler Apps (MAM), und wie Intune Sie beim Schutz von Unternehmensdaten unterstützt.
keywords: Was ist Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/01/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
ms.custom: ''
ms.openlocfilehash: 25bb5ec1610eb3d3cac02244a43ead6e63d441e5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="what-is-intune"></a>Was ist Intune?

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Intune ist ein cloudbasierter Dienst für den Bereich Enterprise Mobility, der die Produktivität Ihrer Mitarbeiter unterstützt und gleichzeitig Ihre Unternehmensdaten schützt. Mit Intune können Sie folgende Aktionen ausführen:
* Die mobilen Geräte verwalten, die Ihre Mitarbeiter verwenden, um auf Unternehmensdaten zuzugreifen
* Die mobilen Apps verwalten, die Ihre Mitarbeiter verwenden
* Ihre Unternehmensinformationen schützen, indem Sie steuern, wie Ihre Mitarbeiter darauf zugreifen und diese freigeben
* Sicherstellen, dass Geräte und Apps kompatibel mit den Sicherheitsanforderungen des Unternehmens sind

## <a name="common-business-problems-that-intune-helps-solve"></a>Häufig auftretende geschäftliche Probleme, die mithilfe von Intune gelöst werden können

* [Sichern Ihrer lokalen E-Mails und Daten für den sicheren Zugriff über mobile Geräte](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Sichern von Office 365-E-Mails und -Daten für den sicheren Zugriff über mobile Geräte](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Ausgeben firmeneigener Smartphones für Information-Worker](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [Anbieten eines BYOD-Programms (Bring Your Own Device) für alle Mitarbeiter](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Ermöglichen des sicheren Zugriffs für Mitarbeiter auf Office 365 von einem nicht verwalteten, öffentlichen Kiosk aus](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Ausgeben gemeinsam genutzter Tablets mit eingeschränkter Verwendung an Ihre Taskworker](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)


## <a name="how-does-intune-work"></a>Funktionsweise von Intune
Intune ist die Komponente von Enterprise Mobility + Security (EMS), mit der mobile Geräte und Apps verwaltet werden. Die Lösung lässt sich eng in andere EMS-Komponenten wie Azure Active Directory (Azure AD) integrieren und bietet Identitäts- und Zugriffsteuerungsfunktionen sowie Azure Information Protection für den Datenschutz. Wenn Sie EMS zusammen mit Office 365 bereitstellen, können Ihre Mitarbeiter auf allen ihren Geräten produktiv arbeiten, während die Informationen Ihres Unternehmens geschützt bleiben.

![Abbild der Intune-Architektur](./media/intunearch_sm.png)

Hier können Sie sich eine [größere Version](./media/intunearchitecture.svg) des Intune-Architekturschaubilds ansehen.

Wie Sie die Geräte- und App-Verwaltungsfunktionen von Intune und EMS nutzen, hängt der Datenschutz von dem [Geschäftsproblem ab, das Sie lösen möchten](#common-business-problems-that-intune-helps-solve). Beispiel:
* Sie werden die Geräteverwaltung umfassend einsetzen, wenn Sie einen Pool mit Geräten erstellen, die nur eine bestimmte Funktion bereitstellen und von Benutzern, die in einem Ladengeschäft zu unterschiedlichen Zeiten arbeiten, gemeinsam verwendet werden sollen.
* Sie brauchen die App-Verwaltung und Datenschutz, wenn Sie Ihren Mitarbeitern erlauben, ihre persönlichen Geräte für den Zugriff auf Unternehmensdaten zu nutzen (BYOD).  
* Wenn Sie Firmentelefone an Information-Worker ausgeben, werden Sie sich auf alle Technologien verlassen.

## <a name="intune-device-management-explained"></a>Erläuterung: Intune-Geräteverwaltung
Die Geräteverwaltung von Intune funktioniert mithilfe der Protokolle oder APIs, die in den mobilen Betriebssystemen verfügbar sind. Es umfasst Aufgaben wie:
* Registrieren von Geräten in der Verwaltung, damit Ihre IT-Abteilung eine Bestandsaufnahme der Geräte hat, die auf Unternehmensdienste zugreifen
* Konfigurieren von Geräten, um sicherzustellen, dass diese die Sicherheits- und -Integritätsstandards des Unternehmens erfüllen
* Bereitstellen von Zertifikaten und WLAN/VPN-Profilen für den Zugriff auf Unternehmensdienste
* Messen der Gerätekompatibilität nach Standards des Unternehmens, inklusive Berichterstellung
* Entfernen von Unternehmensdaten von verwalteten Geräten  

In manchen Fällen kann der Eindruck entstehen, die **Steuerung des Zugriffs auf Unternehmensdaten** sei eine Geräteverwaltungsfunktion. Dies ist nicht der Fall, da die Funktion nicht vom mobilen Betriebssystem bereitgestellt wird. Vielmehr ist es etwas, das der Identitätsanbieter bereitstellt. In unserem Fall ist der Identitätsanbieter Azure Active Directory (Azure AD), das Identitäts- und Zugriffsverwaltungssystem von Microsoft.  

Intune ist mit Azure AD integriert, um eine breite Palette von Szenarios für die Zugriffssteuerung zu aktivieren. Sie können z.B. fordern, dass ein mobiles Gerät konform mit den von Ihnen in Intune definierten Unternehmensstandards ist, bevor das Gerät auf einen Unternehmensdienst wie Exchange zugreifen kann. Ebenso können Sie den Unternehmensdienst auf einen bestimmten Satz mobiler Apps begrenzen. Sie können den Zugriff auf Exchange Online beispielsweise nur auf Outlook und Outlook Mobile begrenzen.

## <a name="intune-app-management-explained"></a>Erläuterung: Intune-App-Verwaltung
Wenn wir über die App-Verwaltung sprechen, sprechen wir über Folgendes:
* Zuweisen mobiler Apps an Mitarbeiter
* Konfigurieren von Apps mit Standardeinstellungen, die bei der Ausführung der App verwendet werden
* Steuern, wie Unternehmensdaten in mobilen Apps verwendet und freigegeben werden
* Entfernen von Unternehmensdaten aus mobilen Apps   
* Aktualisieren von Apps
* Berichte über das mobile App-Inventar
* Nachverfolgen der Nutzung mobiler Apps

Mit dem Begriff „Mobile App-Verwaltung“ können diese Punkte einzeln oder in bestimmten Kombinationen gemeint sein. Insbesondere wird das Konzept der App-Konfiguration mit dem Konzept zum Schutz von Unternehmensdaten in mobilen Apps verbunden, weil einige mobile Apps Einstellungen verfügbar machen, mit denen ihre Datensicherheitsfeatures konfiguriert werden können.

Wenn wir über App-Konfiguration und Intune sprechen, meinen wir genau solche Technologien wie die [verwaltete App-Konfiguration unter iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html).

Wenn Sie Intune mit den anderen Diensten in EMS verwenden, können Sie für die mobilen Anwendungen Ihres Unternehmens Sicherheit jenseits dessen bereitstellen, was das mobile Betriebssystem und die mobilen Apps über die App-Konfiguration bereitstellen. Eine App, die mit EMS verwaltet wird, hat Zugriff auf eine größere Auswahl von Schutzfunktionen für mobile Apps und Daten, einschließlich:

* [Einmaliges Anmelden](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [Multi-Factor Authentication](https://docs.microsoft.com/multi-factor-authentication/multi-factor-authentication)
* [bedingter App-Zugriff: Zugriff zulassen, wenn die mobile App Unternehmensdaten enthält](app-based-conditional-access-intune.md)
* [Trennen von Unternehmensdaten und persönlichen Daten in der gleichen App](app-protection-policy.md)
* [App-Schutzrichtlinie (PIN, Verschlüsselung, Speichern unter, Zwischenablage usw.)](app-protection-policies.md)
* [Zurücksetzen von Unternehmensdaten in einer mobilen App](apps-selective-wipe.md)
* [Unterstützung der Rechteverwaltung](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![Stufen der Datensicherheit bei der App-Verwaltung](./media/managing-mobile-apps.png)

### <a name="intune-app-security"></a>Intune-App-Sicherheit
App-Sicherheit ist ein Bestandteil der App-Verwaltung. Wenn wir in Intune von der Sicherheit für mobile Apps sprechen, meinen wir:
* Ein Bewusstsein dafür, persönliche Informationen getrennt von Unternehmens-IT zu halten
* Eine Beschränkung der Aktionen, die Benutzer mit Unternehmensinformationen durchführen können, z.B. Kopieren, Ausschneiden und Einfügen, Speichern und Anzeigen
* Entfernen von Unternehmensdaten aus mobilen Apps, auch bekannt als selektives Zurücksetzen oder Zurücksetzen von Unternehmensdaten

Intune stellt Sicherheit für mobile Apps z.B. über das Feature **App-Schutzrichtlinie** bereit. Die App-Schutzrichtlinie verwendet die Azure AD-Identität, um Unternehmensdaten von persönlichen Daten zu trennen. Daten, auf die mithilfe von Unternehmensanmeldeinformationen zugegriffen wird, erhalten zusätzliche Unternehmensschutzmaßnahmen.

Wenn ein Benutzer sich z.B. auf seinem Gerät mit seinen Unternehmensanmeldeinformationen anmeldet, ermöglicht seine Unternehmensidentität den Zugriff auf Daten, auf die er mit seiner persönlichen Identität nicht zugreifen kann. Während der Verwendung von Unternehmensdaten steuern App-Schutzrichtlinien, wie die Daten gespeichert und freigegeben werden. Die gleichen Schutzmaßnahmen werden nicht auf Daten angewendet, auf die der Benutzer mit seinem Gerät nach Anmeldung mit seiner persönlichen Identität zugreift. Auf diese Weise hat die IT-Abteilung die Kontrolle über Unternehmensdaten, während der Endbenutzer Zugriff und Schutz seiner persönlichen Daten verwaltet.

## <a name="emm-with-and-without-device-enrollment"></a>EMM mit und ohne Geräteregistrierung
Die meisten Enterprise Mobility Management-Lösungen unterstützen grundlegende Technologien für mobile Geräte und mobile Apps. Diese sind normalerweise an das Gerät gebunden, das in der MDM-Lösung Ihrer Organisation registriert ist. Intune unterstützt diese Szenarios und darüber hinaus viele Szenarios ohne Registrierung.  

Unternehmen unterscheiden sich, inwieweit sie Szenarios ohne Registrierung übernehmen. Einige Unternehmen machen dieses Szenario zu Ihrem Standard. Einige ermöglichen es bloß für Begleitgeräte wie z.B. ein persönliches Tablet. Andere unterstützen es überhaupt nicht. Auch im letzten Fall, in dem eine Organisation von allen Mitarbeitern fordert, ihre Geräte in MDM zu registrieren, unterstützen sie in der Regel Szenarios ohne Registrierung für Auftragnehmer, Lieferanten und für andere Geräte, die über eine bestimmte Freistellung verfügen.

Sie können die Intune-Technologie für die Geräteverwendung ohne Registrierung sogar auf registrierten Geräten verwenden. Beispielsweise kann vom mobilen Betriebssystem für ein Gerät, das in MDM registriert ist, die Schutzfunktion „Öffnen In“ bereitgestellt werden. (Es handelt sich hierbei um ein iOS-Feature, das Sie daran hindert, ein Dokument aus einer App, z.B. Outlook, in einer anderen App, z.B. Word, zu öffnen – es sei denn, beide Apps werden vom MDM-Anbieter verwaltet.) Darüber hinaus kann die IT die App-Schutzrichtlinie auf EMS-verwaltete mobile Apps anwenden, um die Option „Speichern als“ zu steuern oder eine mehrstufige Authentifizierung bereitzustellen.

Intune verfügt als Teil von EMS über Tools, mit denen Sie Ihre Produktivität steigern und gleichzeitig Ihre Unternehmensdaten schützen können – unabhängig von der Position Ihrer Organisation zu registrierten und nicht registrierten mobilen Geräten und Apps.



### <a name="next-steps"></a>Nächste Schritte
* Erfahren Sie mehr über einige der [gängigsten Arten der Verwendung von Intune](common-scenarios.md).
* Machen Sie sich [mit einer 30-Tage-Testversion von Intune](free-trial-sign-up.md) mit dem Produkt vertraut.
* Lernen Sie die [technischen Anforderungen und Funktionen](supported-devices-browsers.md) von Intune detailliert kennen.
