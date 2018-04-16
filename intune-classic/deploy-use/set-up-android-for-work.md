---
title: Einrichten von Android for Work
description: "Aktivieren Sie die Verwaltung mobiler Geräte (Mobile Device Management, MDM) für Android for Work-Geräte mit Microsoft Intune."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b2fdcea9-9ad7-4d73-88e2-854b7a774bb2
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: 366e2b281c05e1233c61f7f35a50700677ad4b79
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="enable-enrollment-of-android-for-work-devices"></a>Aktivieren der Registrierung von Android for Work-Geräten

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Für die Aktivierung der Verwaltung von Android for Work-Geräten müssen Sie eine Android for Work-Bindung zu Intune hinzufügen. Zur Registrierung von Geräten, die Android for Work unterstützen, aber zuvor als reguläre Android-Geräte registriert wurden, muss die Registrierung der Geräte aufgehoben werden. Anschließend muss die Registrierung erneuert werden.

## <a name="add-android-for-work-binding-for-intune"></a>Hinzufügen der Android for Work-Bindung für Intune

1. **Einrichten von Intune**<br>
Wenn nicht bereits geschehen, bereiten Sie die Verwaltung mobiler Geräte durch [Festlegen der Autorität für die Verwaltung mobiler Geräte](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-8#enable-device-enrollment) auf **Microsoft Intune** und Einrichten von MDM vor.

2. **Konfigurieren der Android for Work-Bindung**<br>
    Öffnen Sie als Intune-Administrator die [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), wechseln Sie zu **Verwaltung** &gt; **Verwaltung mobiler Geräte** &gt; **Android for Work**, und klicken Sie auf **Konfigurieren**, um die Google Play-Website für Android for Work zu öffnen. Diese wird in einer neuen Registerkarte im Browser geöffnet.

3. **Anmelden bei Google**<br>
   Geben Sie auf der Anmeldeseite von Google das Google-Konto an, das allen Android for Work-Verwaltungsaufgaben für diesen Mandanten zugeordnet sein wird. Dies ist das Google-Konto, das von den IT-Administratoren Ihrer Organisation gemeinsam verwendet wird, die Apps in der Play for Work-Konsole verwalten.

4. **Bereitstellen von Informationen zur Organisation**<br>
   Geben Sie den Namen Ihres Unternehmens für den **Organisationsnamen** ein. Für den **Enterprise Mobility Verwaltungsanbieter (EMM)** sollte *Microsoft Intune* angezeigt werden. Stimmen Sie der Android for Work-Vereinbarung zu, und klicken Sie auf **Bestätigen**. Ihre Anforderung wird verarbeitet.

## <a name="specify-android-for-work-enrollment-settings"></a>Angeben von Registrierungseinstellungen für Android for Work
   Android for Work wird nur auf bestimmten Android-Geräten unterstützt. Sehen Sie sich die [Voraussetzungen für Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") an.  Jedes Gerät, das Android for Work unterstützt, unterstützt auch die herkömmliche Android-Verwaltung.  Mit Intune können Sie angeben, dass Geräte, die Android for Work unterstützen, verwaltet werden sollen:

   - **Alle Geräte als Android verwalten**: Alle Android-Geräte, einschließlich Geräte, die Android for Work unterstützen, werden als herkömmliche Android-Geräte registriert.
   - **Unterstützte Geräte als Android for Work verwalten**: Alle Geräte,die Android for Work unterstützen, werden als Android for Work-Geräte registriert. Android-Geräte, die nicht Android for Work unterstützen, werden als herkömmliche Android-Geräte registriert.
   - **Unterstütze Geräte nur für Benutzer in den folgenden Benutzergruppen als Android for Work verwalten**: Sie können die Android for Work- Verwaltung auf eine begrenzte Anzahl von Benutzern ausrichten. Nur Geräte der Mitglieder der ausgewählten Gruppen, die ein Gerät registrieren, das Android for Work unterstützt, werden als Android for Work-Geräte registriert. Alle anderen werden als Android-Geräte registriert. Dies ist für Android for Work-Pilotprojekte nützlich.

## <a name="next-steps-for-android-for-work"></a>Nächste Schritte für Android for Work
Nach der Konfiguration der Bindung und der Einstellung für Android for Work können Sie Folgendes tun:
- [Bereitstellen von Android for Work-Apps](android-for-work-apps.md)
- [Hinzufügen von Android for Work-Konfigurationsrichtlinien](android-for-work-policy-settings-in-microsoft-intune.md)

## <a name="unbinding-your-android-for-work-administrative-account"></a>Aufheben der Bindung Ihres Android for Work-Administratorkontos

Sie können die Registrierung und die Verwaltung von Android for Work deaktivieren. Wenn Sie in der Intune-Verwaltungskonsole auf **Unbind** (Bindung aufheben) klicken, werden alle registrierten Android for Work-Geräte aus der Registrierung entfernt und die Beziehung zwischen dem Android for Work-Konto und Intune wird entfernt.

### <a name="how-to-unbind-an-android-for-work-account"></a>So heben Sie die Bindung für ein Android for Work-Konto auf

1. **Aufheben der Android for Work-Bindung**<br>
    Öffnen Sie als Administrator die [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), wechseln Sie zu **Verwaltung** &gt; **Verwaltung mobiler Geräte** &gt; **Android for Work**, und klicken Sie auf **Bindung aufheben**.

2. **Zustimmen zum Löschen der Android for Work-Bindung**<br>
  Klicken Sie auf **Ja**, um die Bindung zu löschen und die Registrierung von allen Android for Work-Geräten von Intune aufzuheben.
