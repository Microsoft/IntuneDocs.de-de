---
title: iOS-Apps mit App-Schutzrichtlinien
titlesuffix: Microsoft Intune
description: Erfahren Sie, was Sie von einer iOS-App mit Schutzrichtlinien erwarten können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 66179c38edcc01104f9293ec292943e9faa200eb
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231413"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Erfahren Sie mehr über die Benutzererfahrung bei iOS-Apps mit App-Schutzrichtlinien. App-Schutzrichtlinien werden nur angewendet, wenn Apps im beruflichen Kontext verwendet werden. Zum Beispiel, wenn Sie über ein Geschäftskonto auf eine App zugreifen, oder wenn Sie auf Dateien am OneDrive-Speicherort Ihres Unternehmens zugreifen.
##  <a name="accessing-apps"></a>Zugreifen auf Apps

Wenn das Gerät **nicht bei Intune registriert** ist, wird der Benutzer bei der ersten Verwendung der App dazu aufgefordert, die App neu zu starten.  Ein Neustart ist erforderlich, damit App-Schutzrichtlinien auf die App angewendet werden können. Der folgende Screenshot stellt dies mithilfe der Skype-App dar:


![Screenshot des iOS-Geräts mit der PIN-Eingabeaufforderung](./media/ios-pin-prompt.png)

Bei Geräten, die **für die Verwaltung in Intune registriert** sind, wird dem Benutzer eine Meldung angezeigt, dass seine App nun verwaltet wird:

![Screenshot des iOS-Geräts mit der Meldung zur Verwaltung durch das Unternehmen und der Eingabeaufforderung](./media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>Verwenden von Apps mit Multi-Identity Support (Unterstützung für mehrere Identitäten)

App-Schutzrichtlinien werden nur wirksam, wenn ein Benutzer versucht, auf geschäftliche Daten zuzugreifen. Ihnen werden möglicherweise unterschiedliche Verhaltensweisen angezeigt, wenn der Benutzer versucht, für den persönlichen Gebrauch auf die App zuzugreifen. Die Richtlinie ist ebenfalls nicht für neuen Inhalt gültig, der noch nicht gespeichert wurde. Neue Inhalte werden erst dann als Unternehmensdaten angesehen, nachdem sie auf einem Unternehmensstandort gespeichert wurden, z.B. SharePoint oder OneDrive for Business.

Bei Apps, die mehrere Identitäten unterstützen, wendet Intune App-Schutzrichtlinien nur dann an, wenn ein Benutzer auf Arbeitsdaten zugreift.  So wird der Benutzer z.B. möglicherweise zur PIN-Eingabe aufgefordert.  In der **Outlook-App** tritt eine Eingabeaufforderung auf, wenn ein Benutzer die App startet. In der **OneDrive-App** tritt eine Aufforderung auf, wenn ein Benutzer eine Eingabe im Arbeitskonto macht.  In Microsoft **Word**, **PowerPoint** und **Excel** tritt eine Eingabeaufforderung auf, wenn ein Benutzer auf OneDrive-Dokumente des Unternehmens zugreift.
##  <a name="managing-user-accounts-on-the-device"></a>Verwalten von Benutzerkonten auf dem Gerät

Intune unterstützt nur die Bereitstellung von App-Schutzrichtlinien auf je einem Benutzerkonto pro Gerät.

* Abhängig von der verwendeten App, ist der zweite Benutzer auf dem Gerät möglicherweise blockiert oder auch nicht. Unter allen Umständen wirken sich die App-Schutzrichtlinien nur auf den ersten Benutzer aus.
  * **Microsoft Word**, **Excel** und **PowerPoint** blockieren nicht den Zugriff auf ein zusätzliches Konto. Allerdings gelten die App-Schutzrichtlinien nicht für dieses Benutzerkonto.

  * Für **OneDrive- und Outlook-Apps** kann nur ein geschäftliches Konto verwendet werden.  Das Hinzufügen weiterer Geschäftskonten wird von diesen Apps blockiert.  Sie können jedoch einen Benutzer von einem Gerät entfernen und anschließend einen anderen Benutzer zum Gerät hinzufügen.

* Vor der Bereitstellung der App-Schutzrichtlinien sind auf einem Gerät möglicherweise mehrere Benutzerkonten vorhanden. In diesem Fall wird das erste Konto, für das die App-Schutzrichtlinien bereitgestellt werden, von Intune-App-Schutzrichtlinien verwaltet.


Lesen Sie das folgende Beispielszenario, um zu erfahren, wie Intune mit mehreren Benutzerkonten umgeht.

Benutzer A arbeitet für zwei Unternehmen: **Unternehmen X** und **Unternehmen Y**. Benutzer A verfügt für jedes Unternehmen über ein geschäftliches Konto, und beide verwenden Intune zum Bereitstellen von App-Schutzrichtlinien. **Unternehmen X** stellt App-Schutzrichtlinien **vor** **Unternehmen Y** bereit. Das dem **Unternehmen X** zugeordnete Konto erhält die App-Schutzrichtlinie, das dem Unternehmen Y zugeordnete Konto jedoch nicht. Damit das dem Unternehmen Y zugeordnete Konto durch die App-Schutzrichtlinien verwaltet wird, muss Benutzer A das dem Unternehmen X zugeordnete Benutzerkonto entfernen.
### <a name="adding-a-second-account"></a>Hinzufügen eines zweiten Kontos

Wenn Sie ein iOS-Gerät verwenden und versuchen, auf demselben Gerät ein zweites Geschäftskonto einzurichten, wird möglicherweise eine Sperrnachricht angezeigt.  Die Konten werden angezeigt, und Sie können das Konto auswählen, das Sie entfernen möchten.

![Screenshot des Dialogfelds mit der Sperrnachricht und den Optionen „Ja“ und „Nein“](./media/ios-switch-user.PNG)

## <a name="next-steps"></a>Nächste Schritte
[Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](app-protection-enabled-apps-android.md)
### <a name="see-also"></a>Siehe auch
[Erstellen und Bereitstellen von App-Schutzrichtlinien mit Microsoft Intune](app-protection-policies.md)
