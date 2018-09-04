---
title: Entfernen Ihres Geräts aus der Verwaltung bei Ablehnung der Nutzungsbedingungen | Microsoft-Dokumentation
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 24aa876b7100f0f802ab3723cedf92a32bc7e9d7
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "43149706"
---
# <a name="remove-your-device-from-management-if-you-declined-terms-of-use"></a>Entfernen Ihres Geräts aus der Verwaltung bei Ablehnung der Nutzungsbedingungen

Wenn Sie beim Versuch, sich bei der Unternehmensportal-App anzumelden, die Nutzungsbedingungen abgelehnt haben, können Sie sich bei späteren Versuchen nicht mehr bei der Unternehmensportal-App anmelden, d.h. Sie müssen diese Anweisungen zur Problemumgehung verwenden, um das Gerät aus Intune zu entfernen.

Wenn Sie die Unternehmensportal-App deinstallieren, wird auch Ihr Geräts aus Intune entfernt. Ihr Gerät wird nicht mehr auf Unternehmensressourcen zugreifen können. Weitere Informationen dazu, was beim Entfernen Ihres Geräts aus der Verwaltung geschieht, finden Sie unter [Was geschieht, wenn Sie die Registrierung Ihres Geräts bei Intune aufheben?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Vor der Deinstallation der Unternehmensportal-App müssen Sie zur Einstellung **Geräteadministratoren** wechseln und **Unternehmensportal** deaktivieren. Je nach Android-Gerät können sich diese Schritte geringfügig unterscheiden.

## <a name="removing-the-device-from-the-company-portal-app"></a>Entfernen Ihres Geräts über die Unternehmensportal-App

So können Sie Ihr Gerät aus Intune entfernen und die Unternehmensportal-App deinstallieren:

1.  Wechseln Sie zu **Einstellungen**&gt;**Sicherheit&amp; Sperrbildschirm** &gt; **Geräteadministratoren**.

    Durch das Ausführen dieses Schritts wird die Registrierung Ihres Geräts sofort aufgehoben.

2.  Deaktivieren Sie das Kontrollkästchen neben **Unternehmensportal**, oder schalten Sie das Unternehmensportal aus.

    Sie können die Unternehmensportal-App jetzt deinstallieren.

## <a name="removing-data-collected-by-the-company-portal-app"></a>Entfernen von Daten, die von der Unternehmensportal-App gesammelt wurden

So entfernen Sie alle Daten, die die Unternehmensportal-App für Android auf Ihrem Gerät gespeichert hat:

  - Klicken Sie zum Löschen von App-Daten auf die entsprechende App und anschließend auf die Schaltfläche „Daten löschen“.
  - Löschen Sie den Ordner „\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal“.


Benötigen Sie weitere Unterstützung? Wenden Sie sich an den Support Ihres Unternehmens (suchen Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980) nach Kontaktinformationen) oder an das <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having unenrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-Team</a>.
