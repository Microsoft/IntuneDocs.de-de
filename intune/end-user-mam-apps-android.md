---
title: Android-Apps mit App-Schutzrichtlinien
description: In diesem Thema erfahren Sie, was Sie erwartet, wenn Ihre App von App-Schutzrichtlinien verwaltet wird.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 06115170300909d1683f44e565161d189f345ab8
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188033"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Dieser Artikel beschreibt die Benutzung von Apps mit App-Schutzrichtlinien. App-Schutzrichtlinien gelten nur, wenn Apps in einem geschäftlichen Kontext verwendet werden, z.B. wenn der Benutzer ein Geschäftskonto für den Zugriff auf Apps verwendet oder auf Dateien zugreift, die an einem OneDrive for Business-Speicherort gespeichert sind.

##  <a name="access-apps"></a>Zugriff auf Apps

Die Unternehmensportal-App ist auf Android-Geräten für alle Apps erforderlich, die App-Schutzrichtlinien zugeordnet sind.

Bei Geräten, die nicht bei Intune registriert sind, muss die Unternehmensportal-App auf dem Gerät installiert sein. Jedoch muss der Benutzer die Unternehmensportal-App nicht starten bzw. sich darin anmelden, bevor er Apps verwenden kann, die von App-Schutzrichtlinien verwaltet werden.

Die Unternehmensportal-App ist in Intune eine Möglichkeit der Freigabe von Daten an einem sicheren Ort. Daher ist die Unternehmensportal-App eine Voraussetzung für alle Apps, denen App-Schutzrichtlinien zugeordnet sind, auch wenn das Gerät nicht in Intune registriert ist.


##  <a name="use-apps-with-multi-identity-support"></a>Verwenden von Apps mit Unterstützung von mehreren Identitäten

App-Schutzrichtlinien werden nur im geschäftlichen Kontext angewendet. Eine App kann sich daher unterschiedlich verhalten, je nachdem, ob sie im geschäftlichen oder privaten Kontext verwendet wird.

Beispielsweise erhalten Benutzer eine PIN-Eingabeaufforderung, wenn Sie auf Geschäftsdaten zugreifen. Bei der **Outlook-App** wird der Benutzer beim Starten der App zur Eingabe einer PIN aufgefordert. Bei der **OneDrive-App** wird der Benutzer zur Eingabe der PIN aufgefordert, wenn er das Geschäftskonto eingibt. Bei Microsoft **Word**, **PowerPoint** und **Excel** wird der Benutzer zur Eingabe der PIN aufgefordert, wenn er auf Dokumente zugreift, die am OneDrive for Business-Speicherort des Unternehmens gespeichert sind.

##  <a name="manage-user-accounts-on-the-device"></a>Verwalten von Benutzerkonten auf dem Gerät

Mit Anwendungen, die mehrere Identitäten unterstützen, können Benutzer mehrere Konten hinzufügen.  Die Intune-App unterstützt nur ein verwaltetes Konto.  Sie schränkt die Anzahl nicht verwalteter Konten nicht ein.

Wenn in einer Anwendung ein verwaltetes Konto vorhanden ist, trifft Folgendes zu:
*   Wenn ein Benutzer versucht, ein zweites verwaltetes Konto hinzuzufügen, wird er aufgefordert, das verwaltete Konto auszuwählen, das verwendet werden soll.  Das andere Konto wird entfernt.
*   Wenn der IT-Administrator einem zweiten vorhandenen Konto eine Richtlinie hinzufügt, wird der Benutzer aufgefordert, das verwaltete Konto auszuwählen, das verwendet werden soll.  Das andere Konto wird entfernt.

Lesen Sie das folgende Beispielszenario, um genauer zu verstehen, wie mehrere Benutzerkonten behandelt werden.

Benutzer A arbeitet für zwei Unternehmen – **Unternehmen X** und **Unternehmen Y**. Benutzer A verfügt für jedes Unternehmen über ein geschäftliches Konto, und beide verwenden Intune zum Bereitstellen von App-Schutzrichtlinien. **Unternehmen X** stellt App-Schutzrichtlinien **vor** **Unternehmen Y** bereit. Das dem **Unternehmen X** zugeordnete Konto erhält die App-Schutzrichtlinie, nicht jedoch das dem Unternehmen Y zugeordnete Konto. Wenn das dem Unternehmen Y zugeordnete Konto durch die App-Schutzrichtlinien verwaltet werden soll, müssen Sie das dem Unternehmen X zugeordnete Benutzerkonto entfernen und das Konto hinzufügen, das Unternehmen Y zugeordnet ist.
### <a name="add-a-second-account"></a>Hinzufügen eines zweiten Kontos
####  <a name="android"></a>Android
Wenn Sie ein Android-Gerät verwenden, wird möglicherweise eine Sperrnachricht mit Anweisungen angezeigt, wie Sie das vorhandene Konto entfernen und ein neues Konto hinzufügen können.  Um das vorhandene Konto zu entfernen, wechseln Sie zu **Einstellungen &gt; Allgemein &gt; Anwendungs-Manager &gt; Unternehmensportal**. Wählen Sie dann **Daten löschen** aus.

![Screenshot der Fehlermeldung und Anweisungen zum Entfernen des Kontos](./media/Android_SwitchUser.png)

##  <a name="view-media-files-with-the-azure-information-protection-app"></a>Anzeigen von Mediendateien mit der Azure Information Protection-App
Verwenden Sie zum Anzeigen unternehmenseigener AV-, PDF- und Bilddateien auf Android-Geräten die [Azure Information Protection-App](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) (ehemals Rights Management-Freigabe-App).

Laden Sie diese App aus dem Google Play Store herunter.  

Die folgenden Dateitypen werden unterstützt:

* **Audio:** AAC LC, HE-AACv1 (AAC+), HE-AACv2 (erweitertes AAC+), AAC ELD (erweitertes AAC mit geringer Verzögerung), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE
* **Video:** H.263, H.264 AVC, MPEG-4 SP, VP8
* **Bild:** JPG, PJPG, PNG, PPNG, BMP, PBMP, GIF, PGIF, JPEG, PJPEG
* **Dokumente:** PDF, PPDF


|**pfile**|
|----|
|Pfile ist ein generisches „Wrapper“-Format für geschützte Dateien, das den verschlüsselten Inhalt sowie die Azure Information Protection-Lizenzen kapselt. Es kann zum Schützen beliebiger Dateitypen verwendet werden.|

## <a name="next-steps"></a>Nächste Schritte
[Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](end-user-mam-apps-ios.md)
