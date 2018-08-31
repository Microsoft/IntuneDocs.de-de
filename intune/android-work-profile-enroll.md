---
title: Registrieren von Android-Arbeitsprofilgeräten in Intune
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Android-Arbeitsprofilgeräte in Intune registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fc1943781dcf95209b575cdb6e36d5065275626f
ms.sourcegitcommit: 40b1d82df99f09a75a17065cdd0e84d8038f460a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "40255067"
---
# <a name="set-up-enrollment-of-android-work-profile-devices"></a>Einrichten der Registrieren von Android-Arbeitsprofilgeräten

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune unterstützt Sie bei der Bereitstellung von Apps und Einstellungen auf Android-Arbeitsprofilgeräten und stellt so sicher, dass geschäftliche und private Informationen immer getrennt bleiben. Ausführliche Informationen über Android Enterprise finden Sie in den [Voraussetzungen für Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Führen Sie die folgenden Schritte aus, um die Android-Arbeitsprofilerverwaltung einzurichten:

1. [Verknüpfen Sie Ihr Intune-Mandantenkonto mit Ihrem Android Enterprise-Konto](connect-intune-android-enterprise.md).
2. Geben Sie die Registrierungseinstellungen von Android-Arbeitsprofilen an. Android-Arbeitsprofile werden [nur auf bestimmten Android-Geräten unterstützt](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Jedes Gerät, das Android-Arbeitsprofile unterstützt, unterstützt auch die herkömmliche Android-Verwaltung. Mit Intune können Sie angeben, wie Geräte, die Android-Arbeitsprofile unterstützen, mithilfe von [Registrierungseinschränkungen](enrollment-restrictions-set.md) verwaltet werden sollen.
    - **Blockieren (Standardeinstellung):** Alle Android-Geräte, einschließlich der Geräte, die Android-Arbeitsprofile unterstützen, werden als herkömmliche Android-Geräte registriert.
    - **Zulassen:** Alle Geräte, die Android-Arbeitsprofile unterstützen, werden als Android-Arbeitsprofilgeräte registriert. Android-Geräte, die nicht Android-Arbeitsprofile unterstützen, werden als herkömmliche Android-Geräte registriert.
3. [Informieren Sie Ihre Benutzer darüber, wie sie ihre Geräte registrieren sollen.](/intune-user-help/enroll-your-device-in-intune-android)


Wenn Sie Geräte in Android-Arbeitsprofilen registrieren möchten, die bereits als reguläre Android-Geräte registriert wurden, müssen Sie die Registrierung der Geräte aufheben und die Geräte anschließend erneut registrieren.

Wenn Sie Android-Arbeitsprofilgeräte mithilfe eines [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md)-Kontos registrieren, besteht pro Konto ein Grenzwert von 10 registrierbaren Geräten.

Weitere Informationen finden Sie unter [Von Intune an Google gesendete Daten](data-intune-sends-to-google.md).

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Genehmigen der Unternehmensportal-App im verwalteten Google Play Store

Um sicherzustellen, dass Benutzer immer Zugriff auf die neueste Version der Unternehmensportal-App haben, müssen Sie die Unternehmensportal-App für Android im Managed Google Play Store genehmigen. Indem Sie sie genehmigen, stellen Sie sicher, dass jeder Benutzer automatische Updates erhält. Wenn Sie sie nicht genehmigen, wird das Unternehmensportal schließlich veraltet sein und möglicherweise keine wichtigen Fehlerbehebungen oder neuen Features erhalten, wenn Microsoft diese veröffentlicht.

Führen Sie die folgenden Schritte durch, um das Intune-Unternehmensportal zu genehmigen:

1.  Suchen Sie die Unternehmensportal-App im [verwalteten Google Play Store](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Melden Sie sich beim Managed Google Play Store mit dem gleichen Google-Konto an, mit dem Sie die Bindung für Android Enterprise konfiguriert haben.
3.  Klicken Sie auf **Genehmigen**. Daraufhin wird ein neues Dialogfeld geöffnet.
4.  Überprüfen Sie die Berechtigungen in diesem Dialogfeld, und klicken Sie dann auf **Genehmigen**. Sie müssen diese Berechtigungen zulassen, um der Unternehmensportal-App die Verwaltung des Arbeitsprofils auf dem Gerät zu ermöglichen.
5.  Wählen Sie **Genehmigt lassen, wenn Apps neue Berechtigungen anfordern** aus, und klicken Sie dann auf **Speichern**.

## <a name="next-steps-for-android-work-profiles"></a>Nächste Schritte für Android-Arbeitsprofile
- [Deploy Android work profile apps (Bereitstellen von Android-Arbeitsprofil-Apps)](store-apps-android.md)
- [Add Android work profile configuration policies (Hinzufügen von Konfigurationsrichtlinien für Android-Arbeitsprofile)](device-profiles.md)
