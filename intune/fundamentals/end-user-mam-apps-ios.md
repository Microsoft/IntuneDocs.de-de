---
title: iOS-/iPadOS-Apps mit App-Schutzrichtlinien
description: In diesem Thema erfahren Sie, was Sie erwartet, wenn Ihre iOS-/iPadOS-App von App-Schutzrichtlinien verwaltet wird.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c854811a9deb938613af872f3cf86244ab9121b3
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514658"
---
# <a name="what-to-expect-when-your-iosipados-app-is-managed-by-app-protection-policies"></a>Was Sie erwartet, wenn Ihre iOS-/iPadOS-App von App-Schutzrichtlinien verwaltet wird

Intune-App-Schutzrichtlinien werden auf Geschäfts-, Schul- und Uni-Apps angewendet. Deshalb bemerken Mitarbeiter und Schüler/Studenten möglicherweise keine Unterschiede bei der Benutzeroberfläche, wenn sie ihre Apps in einem persönlichen Kontext nutzen. Im Geschäfts-, Schul- oder Uni-Kontext erhalten sie jedoch möglicherweise Aufforderungen, Kontoentscheidungen zu treffen, ihre Einstellungen zu aktualisieren oder Sie um Hilfe zu bitten. In diesem Artikel erfahren Sie, welche Erfahrungen Ihre Benutzer machen, wenn sie versuchen, auf Intune-geschützte Anwendungen zuzugreifen und diese zu verwenden.  

## <a name="access-apps"></a>Zugriff auf Apps

Wenn das Gerät **nicht bei Intune registriert** ist, wird der Benutzer beim ersten Verwenden der App aufgefordert, die App neu zu starten. Es ist ein Neustart erforderlich, damit App-Schutzrichtlinien auf die App angewendet werden können.

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS/iPadOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

Bei Geräten, die **für die Verwaltung in Intune registriert** sind, wird dem Benutzer eine Meldung angezeigt, dass seine App nun verwaltet wird.

## <a name="use-apps-with-multi-identity-support"></a>Verwenden von Apps mit Unterstützung von mehreren Identitäten

Mit Apps, die mehrere Identitäten unterstützen, können Sie unterschiedliche Geschäfts- und persönliche Konten verwenden, um auf die gleichen Apps zuzugreifen. App-Schutzrichtlinien – wie z. B. die Aufforderung zur Eingabe einer Geräte-PIN – werden aktiviert, wenn Benutzer in einem Geschäfts-, Schul- oder Unikontext auf diese Apps zugreifen.   

Je nachdem, wie Sie die Richtlinien konfigurieren, erfolgt die PIN-Eingabeaufforderung für die Benutzer möglicherweise in all ihren Apps auf unterschiedliche Weise.  Angenommen, Sie konfigurieren Ihre Richtlinien wie folgt:       
* Microsoft Outlook fordert den Benutzer beim Starten der App zur Eingabe einer PIN auf. 
* OneDrive fordert die Benutzer zur Eingabe einer PIN auf, wenn sie sich bei ihrem Geschäftskonto anmelden.  
* Microsoft Word, PowerPoint und Excel fordern die Benutzer zur Eingabe einer PIN auf, wenn sie auf Dokumente zugreifen, die im OneDrive for Business-Speicherort des Unternehmens gespeichert sind.  

- Erfahren Sie mehr über die Apps, die [App-Schutz und mehrere Identitäten](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) mit Intune unterstützen.  

## <a name="manage-user-accounts-on-the-device"></a>Verwalten von Benutzerkonten auf dem Gerät  

Intune App-Schutzrichtlinien beschränken die Benutzer auf ein verwaltetes Geschäfts-, Schul- oder Uni-Konto pro App. App-Schutzrichtlinien beschränken nicht die Anzahl verwalteter Konten, die ein Benutzer hinzufügen kann.   

- Wenn ein Benutzer versucht, ein zweites verwaltetes Konto hinzuzufügen, wird er aufgefordert, das verwaltete Konto auszuwählen, das verwendet werden soll. Wenn der Benutzer das zweite Konto hinzufügt, wird das erste Konto entfernt.
- Wenn Sie Schutzrichtlinien zu einem anderen Konto Ihres Benutzers hinzufügen, wird der Benutzer aufgefordert, das zu verwendende verwaltete Konto auszuwählen. Das andere Konto wird entfernt. 

Einige Benutzer erhalten nicht die Möglichkeit, zwischen verwalteten Konten zu wechseln oder auszuwählen. Die Option ist nicht für Geräte verfügbar, auf die Folgendes zutrifft:
* Gerät wird von Intune verwaltet  
* Gerät wird über eine Drittanbieterlösung für die Enterprise Mobility-Verwaltung verwaltet und mit der IntuneMAMUPN-Einstellung konfiguriert 

Das folgende Beispielszenario beschreibt, wie mehrere Benutzerkonten behandelt werden:  

Benutzer A arbeitet für zwei Unternehmen – **Unternehmen X** und **Unternehmen Y**. Benutzer A verfügt für jedes Unternehmen über ein geschäftliches Konto, und beide verwenden Intune zum Bereitstellen von App-Schutzrichtlinien. **Unternehmen X** stellt App-Schutzrichtlinien **vor** **Unternehmen Y** bereit. Das Konto, das **Unternehmen X** zugeordnet ist, erhält zuerst die App-Schutzrichtlinie. Wenn das dem Unternehmen Y zugeordnete Benutzerkonto durch die App-Schutzrichtlinien verwaltet werden soll, müssen Sie das dem Unternehmen X zugeordnete Benutzerkonto entfernen und das Benutzerkonto hinzufügen, das Unternehmen Y zugeordnet ist.  

## <a name="next-steps"></a>Nächste Schritte

[Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](end-user-mam-apps-android.md)
