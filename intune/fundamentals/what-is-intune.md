---
title: Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erfahren Sie mehr zu Microsoft Intune, der Komponente der „Enterprise Mobility + Security“-Lösung für die Verwaltung mobiler Geräte (MDM) und die Verwaltung mobiler Apps (MAM), und wie Intune Sie beim Schutz von Unternehmensdaten unterstützt.
keywords: Was ist Intune
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/14/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 56c76663330cae5cb771358542fd22ff09398118
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314731"
---
# <a name="microsoft-intune-is-an-mdm-and-mam-provider-for-your-devices"></a>Microsoft Intune ist ein MDM- und MAM-Anbieter für Ihre Geräte

Microsoft Intune ist ein cloudbasierter Dienst, der sich auf die Verwaltung mobiler Geräte (MDM, Mobile Device Management) und mobiler Anwendungen (MAM, Mobile Application Management) konzentriert. Intune ist in der [EMS-Suite (Enterprise Mobility + Security)](https://www.microsoft.com/microsoft-365/enterprise-mobility-security) von Microsoft enthalten und ermöglicht Ihren Benutzern, produktiv zu sein, während die Daten ihrer Organisation geschützt bleiben. Sie wird in andere Dienste einschließlich Microsoft 365 und Azure Active Directory (Azure AD) integriert, um zu steuern, wer worauf Zugriff hat, und in Azure Information Protection für den Datenschutz. Wenn Sie EMS zusammen mit Microsoft 365 bereitstellen, können Ihre Mitarbeiter auf allen ihren Geräten produktiv arbeiten, während die Informationen Ihres Unternehmens geschützt bleiben.

![Abbild der Intune-Architektur](./media/what-is-intune/intunearch_sm.png)

Hier können Sie sich eine [größere Version](./media/what-is-intune/intunearchitecture.svg) des Intune-Architekturschaubilds ansehen.

Mit Intune können Sie folgende Aktionen ausführen:

- Sie können zu 100 % mit Intune in der Cloud arbeiten oder die [Co-Verwaltung](https://docs.microsoft.com/sccm/comanage/overview) mit Configuration Manager und Intune wählen.
- Legen Sie Regeln fest, und konfigurieren Sie Einstellungen für private und organisationseigene Geräte für den Zugriff auf Daten und Netzwerke.
- Stellen Sie Apps auf lokalen und mobilen Geräten bereit, und authentifizieren Sie sie.
- Schützen Sie Ihre Unternehmensinformationen, indem Sie steuern, wie Benutzer auf Informationen zugreifen und diese freigeben können.
- Stellen Sie sicher, dass Geräte und Apps mit Ihren Sicherheitsanforderungen konform sind.

## <a name="manage-devices"></a>Verwalten von Geräten

In Intune verwalten Sie Geräte mithilfe eines Ansatzes, der für Sie geeignet ist. Für organisationseigene Geräte benötigen Sie möglicherweise Vollzugriff auf Einstellungen, Features und Sicherheit. Bei diesem Ansatz werden die Geräte und die Benutzer dieser Geräte in Intune registriert. Nach der Registrierung erhalten sie Ihre Regeln und Einstellungen über Richtlinien, die in Intune konfiguriert sind. Beispielsweise können Sie Kennwort- und PIN-Anforderungen festlegen, eine VPN-Verbindung erstellen, den Bedrohungsschutz einrichten und vieles mehr.

Bei persönlichen Geräten oder BYOD-Geräten (Bring Your Own Devices) möchten die Benutzer möglicherweise nicht, dass die Administratoren ihrer Organisation über Vollzugriff verfügen. Weisen Sie den Benutzern bei diesem Ansatz Optionen zu. Beispielsweise [registrieren](../enrollment/device-enrollment.md) Benutzer ihre Geräte, wenn sie Vollzugriff auf die Ressourcen Ihrer Organisation wünschen. Wenn diese Benutzer nur auf E-Mail oder Microsoft Teams zugreifen möchten, verwenden Sie App-Schutzrichtlinien, die mehrstufige Authentifizierung (Multi-Factor Authentication, MFA) erfordern, um diese Apps zu verwenden.

Wenn Geräte in Intune registriert und verwaltet werden, können Administratoren folgende Aktionen ausführen:

- Registrierte Geräte anzeigen und eine Bestandsaufnahme der Geräte erhalten, die auf Ressourcen der Organisation zugreifen.
- Geräte konfigurieren, sodass sie den Sicherheits- und Integritätsstandards entsprechen. Beispielsweise möchten Sie wahrscheinlich Geräte mit Jailbreaks blockieren.
- Zertifikate per Push an Geräte übermitteln, damit Benutzer problemlos auf Ihr WLAN zugreifen oder über ein VPN eine Verbindung mit Ihrem Netzwerk herstellen können.
- Berichte zu Benutzern und Geräten anzeigen, die kompatibel und nicht kompatibel sind.
- Organisationsdaten entfernen, wenn ein Gerät verloren geht, gestohlen wurde oder nicht mehr verwendet wird.

**Onlineressourcen**:

- [Was ist die Geräteregistrierung?](../enrollment/device-enrollment.md)

- [Anwenden von Einstellungen und Funktionen auf Ihren Geräten mit Geräteprofilen](../configuration/device-profiles.md)

- [Schützen von Geräten mit Microsoft Intune](../protect/device-protect.md)

## <a name="manage-apps"></a>Verwalten von Apps

Die Verwaltung mobiler Anwendungen (Mobile Application Management, MAM) in Intune dient zum Schutz von Organisationsdaten auf Anwendungsebene, einschließlich benutzerdefinierter Apps und Store-Apps. Die App-Verwaltung kann auf unternehmenseigenen Geräten und persönlichen Geräten verwendet werden.

Wenn Apps in Intune verwaltet werden, können Administratoren folgende Aktionen ausführen:

- Mobile Apps Benutzergruppen und Geräten hinzufügen und zuweisen, einschließlich Benutzern in bestimmten Gruppen, Geräten in bestimmten Gruppen usw.
- Apps so konfigurieren, dass sie mit bestimmten Einstellungen gestartet oder ausgeführt werden, und bereits auf dem Gerät vorhandene Apps aktualisieren.
- Berichte darüber anzeigen, welche Apps verwendet werden, und deren Nutzung nachverfolgen.
- Selektive Löschungen ausführen, indem sie nur Organisationsdaten aus Apps entfernen.

Intune stellt Sicherheit für mobile Apps z. B. über **[App-Schutzrichtlinien](../apps/app-protection-policy.md)** bereit. App-Schutzrichtlinien:

- Verwenden die Azure AD-Identität, um Organisationsdaten von persönlichen Daten zu isolieren. So sind persönliche Daten für die IT-Abteilung der Organisation nicht sichtbar. Daten, auf die mithilfe von Anmeldeinformationen der Organisation zugegriffen wird, erhalten zusätzlichen Sicherheitsschutz.
- Sichern den Zugriff auf persönliche Geräte, indem sie Aktionen einschränken, die Benutzer ausführen können, z. B. Kopieren und Einfügen, Speichern und Anzeigen.
- Können auf Geräten erstellt und bereitgestellt werden, die bei Intune, einem anderen MDM-Dienst oder keinem MDM-Dienst registriert sind. Auf registrierten Geräten können App-Schutzrichtlinien eine zusätzliche Schutzebene hinzufügen.

Ein Benutzer meldet sich z. B. mit den Anmeldeinformationen seines Unternehmens bei einem Gerät an. Seine Organisationsidentität ermöglicht ihm den Zugriff auf Daten, die seiner persönlichen Identität verweigert werden. Während der Verwendung von Organisationsdaten steuern App-Schutzrichtlinien, wie die Daten gespeichert und freigegeben werden. Wenn sich Benutzer mit Ihrer persönlichen Identität anmelden, werden nicht die gleichen Schutzmaßnahmen angewendet. Auf diese Weise hat die IT-Abteilung die Kontrolle über Organisationsdaten, während der Endbenutzer Zugriff und Schutz seiner persönlichen Daten verwaltet.

Außerdem können Sie Intune mit den anderen Diensten in EMS verwenden. Diese Funktion bietet Ihrer Organisation eine höhere Sicherheit mobiler Apps als die im Betriebssystem und in Apps enthaltenen Sicherheitsfunktionen. Mit EMS verwaltete Apps haben Zugriff auf eine größere Auswahl von Schutzfunktionen für mobile Apps und Daten.

![Stufen der Datensicherheit bei der App-Verwaltung](./media/what-is-intune/managing-mobile-apps.png)

## <a name="compliance-and-conditional-access"></a>Konformität und bedingter Zugriff

Intune ist mit Azure AD integriert, um eine breite Palette von Szenarios für die Zugriffssteuerung zu aktivieren. Fordern Sie beispielsweise, dass mobile Geräte mit den in Intune definierten Organisationsstandards kompatibel sind, bevor sie auf Netzwerkressourcen wie E-Mail oder SharePoint zugreifen können. Ebenso können Sie Dienste sperren, sodass sie nur für einen bestimmten Satz mobiler Apps verfügbar sind. Sie können den Zugriff auf Exchange Online beispielsweise nur auf Outlook oder Outlook Mobile begrenzen.

**Onlineressourcen**:

- [Legen Sie Regeln auf Geräten fest, um Zugriff auf die Ressourcen Ihrer Organisation zu gewähren](../protect/device-compliance-get-started.md)

- [Gängige Möglichkeiten für die Verwendung des bedingten Zugriffs mit Intune](../protect/conditional-access-intune-common-ways-use.md)

## <a name="how-to-get-intune"></a>Informationen zum Erhalten von Intune

Intune ist verfügbar:

- Als eigenständiger [Azure-Dienst](https://go.microsoft.com/fwlink/?linkid=2090973)
- Enthalten in [Microsoft 365 ](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune) und [Microsoft 365 Government](https://www.microsoft.com/microsoft-365/government)
- Als [Mobile Geräteverwaltung in Office 365](https://support.office.com/article/choose-between-mdm-for-office-365-and-microsoft-intune-c93d9ab9-efb2-4349-9b93-30c30562ee22), die aus einigen eingeschränkten Intune-Features besteht

Intune wird in vielen Sektoren verwendet, einschließlich [Behörden](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description), [Ausbildung](https://www.microsoft.com/en-us/education/intune), [Kiosk- oder dedizierten Geräten](../configuration/kiosk-settings.md) für Produktion, Einzelhandel und Sonstiges.

## <a name="next-steps"></a>Nächste Schritte

- Beispielsweise können die folgenden [gängigen Geschäftsprobleme mithilfe von Intune gelöst werden](https://docs.microsoft.com/intune/common-scenarios).
- Starten Sie mit einer [30-Tage-Testversion von Intune](free-trial-sign-up.md).
- Planen Sie Ihre [Migration zu Intune](migration-guide.md).
- Mithilfe Ihrer kostenlosen Testversion oder Ihres Abonnements können Sie schrittweise den [Schnellstart: Erstellen eines E-Mail-Geräteprofils für iOS](../configuration/quickstart-email-profile.md) ausführen.
