---
title: Verwalten von Betriebssystemversionen mit Microsoft Intune
description: Erfahren Sie, wie Sie Betriebssystemversionen plattformübergreifend mit Microsoft Intune verwalten können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 361ef17b-1ee0-4879-b7b1-d678b0787f5a
ms.openlocfilehash: 763cc61aae50de893461d1ed137025fa1e6b00b9
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231658"
---
# <a name="manage-operating-system-versions-with-intune"></a>Verwalten von Betriebssystemversionen mit Intune
Für aktuelle mobile Plattformen und Desktopplattformen werden ständig größere Updates, Patches und neue Versionen herausgegeben. Es gibt Steuerelemente, mit denen Sie Updates und Patches unter Windows vollständig verwalten können. Andere Plattformen wie iOS und Android verlangen, dass sich die Benutzer an dem Vorgang beteiligen.  Microsoft Intune verfügt über Funktionen, mit denen Sie Ihre Betriebssystemversionsverwaltung plattformübergreifend strukturieren können.

Intune kann Sie bei den folgenden häufig auftretenden Szenarios unterstützen: 
- Ermitteln, welche Betriebssystemversionen auf Ihren Benutzergeräten vorhanden sind
- Den Zugriff auf Unternehmensdaten auf Geräten steuern, während Sie eine neue Betriebssystemversion prüfen
- Benutzer ermutigen bzw. dazu verpflichten, auf die neuste Betriebssystemversion, die von Ihrer Organisation zugelassen wurde, zu aktualisieren
- Ein organisationsweites Rollout einer neuen Betriebssystemversion verwalten
  
## <a name="operating-system-version-control-using-intune-mobile-device-management-mdm-enrollment-restrictions"></a>Registrierungsbeschränkungen für die Versionskontrolle von Betriebssystemen mithilfe der mobilen Geräteverwaltung (MDM) von Intune
Mithilfe der Registrierungsbeschränkungen für die MDM von Intune können Sie die Clientgeräteanforderungen definieren, bevor Sie der Registrierung des Geräts zustimmen. Ziel ist es, Ihre Benutzer zu verpflichten, nur kompatible Geräte zu registrieren, bevor sie auf die Ressourcen der Organisation zugreifen können. Die Geräteanforderungen umfassen sowohl die Mindest- als auch die Maximalversionen von Betriebssystemen, die für unterstützte Plattformen genehmigt wurden.
 
![Seite mit Plattformkonfigurationsbeschränkungen](./media/os-version-platform-configurations.png) 
 
### <a name="in-practice"></a>In der Praxis
Organisationen verwenden Gerätetypbeschränkungen, um den Zugang zu Ressourcen der Organisation zu beschränken, indem sie folgende Einstellungen nutzen: 
1. Verwenden Sie eine Mindestversion des Betriebssystems, um Benutzer an aktuelle und unterstütze Plattformen innerhalb Ihrer Organisation zu binden. 
2. Bestimmen Sie entweder keine Maximalversion des Betriebssystems (keine Beschränkung), oder legen Sie die zuletzt in Ihrer Organisation geprüfte Version als Maximalversion fest, damit genügend Zeit für interne Tests neuer Betriebssystemversionen bleibt.

Weitere Informationen finden Sie unter [Set device type restrictions (Festlegen von Gerätetypbeschränkungen)](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions).
 
## <a name="operating-system-version-reporting-and-compliance-with-intune-mdm-device-compliance-policies"></a>Berichterstattung zu Betriebssystemversionen und Einhaltung der Gerätekompatibilitätsrichtlinien mit Intune MDM
Die Gerätekompatibilitätsrichtlinien für Intune MDM beinhalten Folgendes: 
- Näheres Bestimmen der Kompatibilitätsregeln
- Abrufen des Kompatibilitätsstatus anhand von Berichten
- Vorgehen gegen Kompatibilitätsverstöße, indem Geräte unter Quarantäne gestellt werden und der Zugriff beschränkt wird

Genauso wie Registrierungsbeschränkungen umfassen Gerätekompatibilitätsrichtlinien sowohl Mindest- als auch Maximalversionen von Betriebssystemen. Die Richtlinien verfügen außerdem über eine Kompatibilitätszeitachse, damit Ihren Benutzern eine Toleranzperiode eingeräumt wird, die sie nutzen sollen, um ihre Geräte entsprechend anzupassen. Gerätekompatibilitätsrichtlinien sorgen dafür, dass registrierte Benutzergeräte mit den Organisationsrichtlinien kompatibel sind.

![Gerätekompatibilität: Vorgehensweise bei nicht kompatiblen Geräten](./media/os-version-actions-noncompliance.png) 

### <a name="in-practice"></a>In der Praxis
Organisationen verwenden Gerätekompatibilitätsrichtlinien für dieselben Szenarios wie die Registrierungsbeschränkungen. Diese Richtlinien sorgen dafür, dass Benutzer in Ihrer Organisation aktuelle und geprüfte Betriebssystemversionen verwenden. Wenn Benutzergeräte nicht mit den Richtlinien kompatibel sind, kann der Zugriff auf Organisationsressourcen solange eingeschränkt werden, bis die Benutzer dem für Ihre Organisation unterstützten Betriebssystembereich entsprechen. Die Benutzer werden benachrichtigt, wenn sie gegen die Kompatibilitätsvorgaben verstoßen, und ihnen werden die nötigen Schritte genannt, um wieder Zugriff gewährt zu bekommen.   

Weitere Informationen finden Sie unter [Erste Schritte bei der Gerätekonformität](https://docs.microsoft.com/intune/device-compliance-get-started).
 
## <a name="operating-system-version-controls-using-intune-app-protection-policies"></a>Kontrollieren von Betriebssystemversionen mithilfe der Intune-App-Schutzrichtlinien    
Mithilfe von Intune-App-Schutzrichtlinien und Zugriffseinstellungen für die mobile Anwendungsverwaltung können Sie Mindestversionen von Betriebssystemen auf Anwendungsebene festlegen. Dadurch können Sie die Benutzer über Updates informieren und dazu ermutigen bzw. verpflichten, ihr Betriebssystem auf eine vorgegebene Mindestversion zu aktualisieren.
 
Dafür gibt es zwei Optionen: 

|Warnung  |Blockieren  |
|---------|---------|
|Warnungen informieren den Benutzer darüber, dass er ein Upgrade vornehmen sollte, wenn er eine Anwendung, für die Anwendungsschutzrichtlinien oder Zugriffseinstellungen für die mobile Anwendungsverwaltung gelten, auf einem Gerät öffnet, auf dem eine Betriebssystemversion installiert ist, die nicht der vorgegebenen Version entspricht. Der Zugriff auf die App und die Organisationsdaten wird nicht eingeschränkt.|Blockierungen informieren den Benutzer darüber, dass er ein Upgrade vornehmen muss, wenn er eine Anwendung, für die Anwendungsschutzrichtlinien oder Zugriffseinstellungen für die mobile Anwendungsverwaltung gelten, auf einem Gerät öffnet, auf dem eine Betriebssystemversion installiert ist, die nicht der vorgegebenen Version entspricht. Der Zugriff auf die App und die Organisationsdaten wird verwehrt.|
|![Dialogfeld: Warnung wegen erforderlichen Android-Updates](./media/os-version-update-warning.png)    |![Dialogfeld: Zugriff auf App blockiert](./media/os-version-access-blocked.png)          |

 
### <a name="in-practice"></a>In der Praxis
Heutzutage verwenden Organisationen Einstellungen für App-Schutzrichtlinien, wenn Apps geöffnet oder fortgesetzt werden, um Benutzer über die Notwendigkeit zu informieren, Apps aktuell zu halten. Eine mögliche Konfiguration wäre z.B., dass Benutzer des Vorgängers der aktuellen Version gewarnt werden und Benutzer, die eine frühere Version als den Vorgänger der aktuellen Version verwenden, blockiert werden.
 
Weitere Informationen finden Sie unter [Erstellen und Zuweisen von App-Schutzrichtlinien](https://docs.microsoft.com/intune/app-protection-policies).

## <a name="managing-a-new-operating-system-version-rollout"></a>Verwalten eines Rollout einer neuen Betriebssystemversion
Sie können die Funktionen von Intune, die in diesem Artikel beschrieben werden, nutzen, um die Geräte in Ihrer Organisation innerhalb der von Ihnen definierten Zeitachse auf eine neue Betriebssystemversion umzuziehen. Die folgenden Schritte stellen ein Beispiel für ein Bereitstellungsmodell dar, mit dem Sie die Benutzer innerhalb von sieben Tagen von einer Betriebssystemversion auf eine andere umziehen lassen können.
- **Schritt 1**: Verwenden Sie Registrierungsbeschränkungen, um die neue Betriebssystemversion als Mindestversion festzulegen, damit ein Gerät registriert werden kann. Damit wird gewährleistet, dass neue Benutzergeräte zum Zeitpunkt der Registrierung kompatibel sind.
- **Schritt 2a**: Verwenden Sie die Intune-App-Schutzrichtlinien, um Benutzer zu warnen, wenn eine App geöffnet oder fortgesetzt wird, für die eine neue Betriebssystemversion erforderlich ist.
- **Schritt 2b:** Verwenden Sie Gerätekompatibilitätsrichtlinien, um eine neue Betriebssystemversion als Mindestversion für ein Gerät festzulegen, damit es kompatibel ist. Verwenden Sie **Aktionen** bei Kompatibilitätsverstößen, um eine siebentägige Toleranzperiode einzuräumen und den Benutzer eine E-Mail-Benachrichtigung zukommen zu lassen, in der die Zeitachse und die Anforderungen angegeben werden.
  -  In diesen Richtlinien, die den Benutzern per E-Mail, im Intune-Unternehmensportal, und beim Öffnen einer App, für die die App-Schutzrichtlinie aktiviert ist, übermittelt werden, wird darüber informiert, dass vorhandene Geräte aktualisiert werden müssen.
  - Sie können einen Kompatibilitätsbericht ausführen, um Benutzer zu ermitteln, deren Geräte nicht kompatibel sind. 
- **Schritt 3a**: Verwenden Sie die Intune-App-Schutzrichtlinien, um Benutzer beim Öffnen oder Fortsetzen einer App zu blockieren, wenn das Gerät nicht unter der neusten Betriebssystemversion läuft.
- **Schritt 3b**: Verwenden Sie Gerätekompatibilitätsrichtlinien, um eine neu Betriebssystemversion als Mindestversion für ein Gerät festzulegen, damit es kompatibel ist.
  - In diesen Richtlinien wird festgelegt, dass Geräte aktualisiert werden müssen, damit sie weiterhin Zugriff auf Organisationsdaten haben. Geschützte Dienste werden blockiert, wenn Sie auf Geräten mit bedingtem Zugriff verwendet werden. Apps, für die eine App-Schutzrichtlinie aktiviert ist, werden beim Öffnen oder beim Zugreifen auf Organisationsdaten blockiert.

## <a name="next-steps"></a>Nächste Schritte
Verwenden Sie die folgenden Ressourcen, um Betriebssystemversionen in Ihrer Organisation zu verwalten: 

- [Festlegen von Gerätetypbeschränkungen](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions)
- [Erste Schritte bei der Gerätekonformität](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Erstellen und Zuweisen von App-Schutzrichtlinien](https://docs.microsoft.com/intune/app-protection-policies)
