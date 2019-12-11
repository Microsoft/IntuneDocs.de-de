---
title: iOS-Apps mit App-Schutzrichtlinien
description: In diesem Thema erfahren Sie, was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
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
ms.openlocfilehash: a1a3dcd7068a004f94b97b5ec6c43c609662a76d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414560"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird

 Dieses Thema beschreibt das Benutzererlebnis beim Verwenden von Apps mit angewendeten App-Schutzrichtlinien. App-Schutzrichtlinien gelten nur, wenn Apps in einem geschäftlichen Kontext verwendet werden, z. B. wenn der Benutzer ein Geschäftskonto für den Zugriff auf Apps verwendet oder auf Dateien zugreift, die an einem OneDrive for Business-Speicherort im Unternehmen gespeichert sind.

## <a name="access-apps"></a>Zugriff auf Apps

Wenn das Gerät **nicht bei Intune registriert** ist, wird der Benutzer beim ersten Verwenden der App aufgefordert, die App neu zu starten. Ein Neustart ist erforderlich, damit App-Schutzrichtlinien auf die App angewendet werden können.

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

Bei Geräten, die **für die Verwaltung in Intune registriert** sind, wird dem Benutzer eine Meldung angezeigt, dass seine App nun verwaltet wird.

## <a name="use-apps-with-multi-identity-support"></a>Verwenden von Apps mit Unterstützung von mehreren Identitäten

Apps, die mehrere Identitäten unterstützen, bieten Ihnen die Möglichkeit, verschiedene Konten (Geschäfts- und persönliche Konten) für den Zugriff auf die gleichen Apps zu verwenden. Hierbei werden App-Schutzrichtlinien nur angewendet, wenn die Apps im Arbeitskontext verwendet werden.  

Beispielsweise erhalten Benutzer eine PIN-Eingabeaufforderung, wenn Sie auf Geschäftsdaten zugreifen. Bei der **Outlook-App** wird der Benutzer beim Starten der App zur Eingabe einer PIN aufgefordert. Bei der **OneDrive-App** wird der Benutzer zur Eingabe einer PIN aufgefordert, wenn er das Geschäftskonto eingibt.  Bei Microsoft **Word**, **PowerPoint** und **Excel** wird der Benutzer zur Eingabe einer PIN aufgefordert, wenn er auf Dokumente zugreift, die am OneDrive for Business-Speicherort des Unternehmens gespeichert sind.

- Erfahren Sie mehr über die Apps, die [App-Schutz und mehrere Identitäten](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) mit Intune unterstützen.

App-Schutzrichtlinien werden nur im geschäftlichen Kontext angewendet. Eine App kann sich daher unterschiedlich verhalten, je nachdem, ob sie im geschäftlichen oder privaten Kontext verwendet wird.

## <a name="manage-user-accounts-on-the-device"></a>Verwalten von Benutzerkonten auf dem Gerät

Mit Anwendungen, die mehrere Identitäten unterstützen, können Benutzer mehrere Konten hinzufügen.  Die Intune-App unterstützt nur ein verwaltetes Konto.  Sie schränkt die Anzahl nicht verwalteter Konten nicht ein.

Wenn in einer Anwendung ein verwaltetes Konto vorhanden ist, trifft Folgendes zu:

- Wenn ein Benutzer versucht, ein zweites verwaltetes Konto hinzuzufügen, wird er aufgefordert, das verwaltete Konto auszuwählen, das verwendet werden soll.  Das andere Konto wird entfernt.
- Wenn der IT-Administrator einem zweiten vorhandenen Konto eine Richtlinie hinzufügt, wird der Benutzer aufgefordert, das verwaltete Konto auszuwählen, das verwendet werden soll.  Das andere Konto wird entfernt.

Lesen Sie das folgende Beispielszenario, um genauer zu verstehen, wie mehrere Benutzerkonten behandelt werden.

Benutzer A arbeitet für zwei Unternehmen – **Unternehmen X** und **Unternehmen Y**. Benutzer A verfügt für jedes Unternehmen über ein geschäftliches Konto, und beide verwenden Intune zum Bereitstellen von App-Schutzrichtlinien. **Unternehmen X** stellt App-Schutzrichtlinien **vor** **Unternehmen Y** bereit. Das Konto, das **Unternehmen X** zugeordnet ist, erhält zuerst die App-Schutzrichtlinie. Wenn das dem Unternehmen Y zugeordnete Benutzerkonto durch die App-Schutzrichtlinien verwaltet werden soll, müssen Sie das dem Unternehmen X zugeordnete Benutzerkonto entfernen und das Benutzerkonto hinzufügen, das Unternehmen Y zugeordnet ist.

### <a name="add-a-second-account"></a>Hinzufügen eines zweiten Kontos

Wenn Sie ein iOS-Gerät verwenden und versuchen, auf diesem Gerät ein zweites Geschäftskonto einzurichten, wird möglicherweise eine Sperrnachricht angezeigt. Die Konten werden angezeigt, und Sie können das Konto auswählen, das Sie entfernen möchten.

## <a name="next-steps"></a>Nächste Schritte

[Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](end-user-mam-apps-android.md)
