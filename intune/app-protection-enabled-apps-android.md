---
title: Android-Apps mit App-Schutzrichtlinien
titlesuffix: Microsoft Intune
description: Erfahren Sie, was Sie von einer Android-App mit Schutzrichtlinien erwarten können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e8c606f9b304f91e02ba977c801bd8de18682612
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231694"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Erfahren Sie, was Sie von Android-Apps mit Schutzrichtlinien erwarten können. App-Schutzrichtlinien werden nur angewendet, wenn Apps im beruflichen Kontext verwendet werden. Zum Beispiel, wenn Sie über ein Geschäftskonto auf eine App zugreifen, oder wenn Sie auf Dateien am OneDrive-Speicherort Ihres Unternehmens zugreifen.
##  <a name="accessing-apps"></a>Zugreifen auf Apps

Die Unternehmensportal-App ist auf Android-Geräten für alle Apps erforderlich, die über App-Schutzrichtlinien verfügen.

Installieren Sie das Unternehmensportal auf allen Geräten, die bei Intune registriert sind. Benutzer müssen sich nicht bei der Unternehmensportal-App anmelden, um Apps mit App-Schutzrichtlinien verwenden zu können.
Die Unternehmensportal-App bietet Ihnen die Möglichkeit der Freigabe von Daten an einem sicheren Ort. Daher ist sie auch für nicht registrierte Geräte erforderlich.


##  <a name="using-apps-with-multi-identity-support"></a>Verwenden von Apps mit Multi-Identity Support (Unterstützung für mehrere Identitäten)

App-Schutzrichtlinien werden nur wirksam, wenn ein Benutzer versucht, auf geschäftliche Daten zuzugreifen.  Ihnen werden möglicherweise unterschiedliche Verhaltensweisen angezeigt, wenn der Benutzer für den persönlichen Gebrauch auf die App zugreift.

Einige Apps unterstützen mehrere Identitäten. In diesem Fall wendet Intune nur dann App-Schutzrichtlinien an, wenn ein Benutzer auf Arbeitsdaten zugreift.  So wird der Benutzer z.B. möglicherweise zur PIN-Eingabe aufgefordert.  In der **Outlook-App** tritt eine Eingabeaufforderung auf, wenn ein Benutzer die App startet. In der **OneDrive-App** tritt eine Aufforderung auf, wenn ein Benutzer eine Eingabe im Arbeitskonto macht.  In Microsoft **Word**, **PowerPoint** und **Excel** tritt eine Eingabeaufforderung auf, wenn ein Benutzer auf OneDrive-Dokumente des Unternehmens zugreift.
##  <a name="managing-user-accounts-on-the-device"></a>Verwalten von Benutzerkonten auf dem Gerät

Intune unterstützt die Bereitstellung von App-Schutzrichtlinien auf einem Benutzerkonto pro Gerät.

* Abhängig von der verwendeten App, ist der zweite Benutzer auf dem Gerät möglicherweise blockiert oder auch nicht. Unter allen Umständen wirken sich die App-Schutzrichtlinien nur auf den ersten Benutzer aus.

  * **Microsoft Word**, **Excel** und **PowerPoint** blockieren nicht den Zugriff auf ein zusätzliches Konto. Allerdings gelten die App-Schutzrichtlinien nicht für dieses Benutzerkonto.

  * Für **OneDrive- und Outlook-Apps** kann nur ein geschäftliches Konto verwendet werden.  Das Hinzufügen weiterer Geschäftskonten wird von diesen Apps blockiert.  Sie können jedoch einen Benutzer von einem Gerät entfernen und anschließend einen anderen Benutzer zum Gerät hinzufügen.


* Vor der Bereitstellung der App-Schutzrichtlinie sind auf einem Gerät möglicherweise mehrere Benutzerkonten vorhanden. In diesem Fall wird das erste Konto, für das die App-Schutzrichtlinien bereitgestellt werden, von Intune-App-Schutzrichtlinien verwaltet.


Lesen Sie das folgende Beispielszenario, um zu erfahren, wie Intune mit mehreren Benutzerkonten umgeht.

Benutzer A arbeitet für zwei Unternehmen: **Unternehmen X** und **Unternehmen Y**. Benutzer A verfügt für jedes Unternehmen über ein geschäftliches Konto, und beide verwenden Intune zum Bereitstellen von App-Schutzrichtlinien. **Unternehmen X** stellt App-Schutzrichtlinien **vor** **Unternehmen Y** bereit. Das dem **Unternehmen X** zugeordnete Konto erhält die App-Schutzrichtlinie, das dem Unternehmen Y zugeordnete Konto jedoch nicht. Damit das dem Unternehmen Y zugeordnete Konto durch die App-Schutzrichtlinien verwaltet wird, muss Benutzer A das dem Unternehmen X zugeordnete Benutzerkonto entfernen.
### <a name="adding-a-second-account"></a>Hinzufügen eines zweiten Kontos
####  <a name="android"></a>Android
Ihnen wird möglicherweise eine Aufforderung angezeigt, nach der Sie das vorhandene Konto entfernen und ein neues hinzufügen sollen.  Wechseln Sie zu **Einstellungen &gt;Allgemein &gt;Anwendungs-Manager &gt;Unternehmensportal, um das vorhandene Konto zu entfernen. Wählen Sie anschließend „Daten löschen“ aus.**

![Screenshot der Fehlermeldung und Anweisungen zum Entfernen des Kontos](./media/android-switch-user.png)

##  <a name="viewing-media-files-with-the-azure-information-protection-app-previously-known-as-rights-management-sharing-app"></a>Anzeigen von Mediendateien mit der Azure Information Protection-App (zuvor bekannt als Rights Management-Freigabeanwendung)
Verwenden Sie zum Anzeigen unternehmenseigener AV-, PDF- und Bilddateien auf Android-Geräten die [Azure Information Protection-App](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer).

Laden Sie diese App aus dem Google Play herunter.  

Die folgenden Dateitypen werden unterstützt:

* **Audio:** AAC LC, HE-AACv1 (AAC+), HE-AACv2 (erweitertes AAC+), AAC ELD (enhanced low delay ACC, erweitertes AAC mit geringer Verzögerung), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE.
* **Video:** H.263, H.264 AVC, MPEG-4 SP, VP8.
* **Bild:** JPG, PJPG, PNG, PPNG, BMP, PBMP, GIF, PGIF, JPEG, PJPEG.
* **Dokumente:** PDF, PPDF

------------

|                                                                                 <strong>pfile</strong>                                                                                 |                                                                      <strong>text</strong>                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Pfile ist ein generisches „Wrapper“-Format für geschützte Dateien. Es schließt den verschlüsselten Inhalt und die Azure Information Protection-Lizenzen ein. Es kann zum Schützen beliebiger Dateitypen verwendet werden. | Textdateien, einschließlich XML, CSV, etc. können zum Anzeigen in der App geöffnet werden, selbst wenn sie geschützt sind. Dateitypen: TXT, PTXT, CSV, PCSV, LOG, PLOG, XML, PXML. |

---------------
## <a name="next-steps"></a>Nächste Schritte
[Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>Siehe auch
[Erstellen und Bereitstellen von App-Schutzrichtlinien mit Microsoft Intune](app-protection-policies.md)
