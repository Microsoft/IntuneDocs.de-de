---
title: Registrieren von Android Enterprise-Arbeitsprofilgeräten in Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Android Enterprise-Arbeitsprofilgeräte in Intune registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66574fe66f90b73d8ebf5835c5b16e93276579e4
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568218"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Einrichten der Registrierung von Android Enterprise-Arbeitsprofilgeräten

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune unterstützt Sie bei der Bereitstellung von Apps und Einstellungen auf Android Enterprise-Arbeitsprofilgeräten und stellt so sicher, dass geschäftliche und private Informationen immer getrennt bleiben. Ausführliche Informationen über Android Enterprise finden Sie in den [Voraussetzungen für Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Führen Sie die folgenden Schritte aus, um die Android Enterprise-Arbeitsprofilverwaltung einzurichten:

1. [Verknüpfen Sie Ihr Intune-Mandantenkonto mit Ihrem Android Enterprise-Konto](connect-intune-android-enterprise.md).
2. Geben Sie die Registrierungseinstellungen für Android Enterprise-Arbeitsprofilen an. Android Enterprise-Arbeitsprofile werden [nur auf bestimmten Android-Geräten unterstützt](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Jedes Gerät, das Android Enterprise-Arbeitsprofile unterstützt, unterstützt auch die herkömmliche Android-Verwaltung. Mit Intune können Sie angeben, wie Geräte, die Android Enterprise-Arbeitsprofile unterstützen, mithilfe von [Registrierungseinschränkungen](enrollment-restrictions-set.md) verwaltet werden sollen.
    - **Blockieren (Standardeinstellung)** :  Alle Android-Geräte, einschließlich der Geräte, die Android Enterprise-Arbeitsprofile unterstützen, werden als herkömmliche Android-Geräte registriert.
    - **Zulassen:** Alle Geräte, die Android Enterprise-Arbeitsprofile unterstützen, werden als Android Enterprise-Arbeitsprofilgeräte registriert. Android-Geräte, die Android Enterprise-Arbeitsprofile nicht unterstützen, werden als herkömmliche Android-Geräte registriert.
3. [Informieren Sie Ihre Benutzer darüber, wie sie ihre Geräte registrieren sollen.](/intune-user-help/enroll-your-device-in-intune-android)


Wenn Sie Geräte mit Android Enterprise-Arbeitsprofilen registrieren möchten, die bereits als reguläre Android-Geräte registriert wurden, müssen Sie die Registrierung der Geräte aufheben und die Geräte anschließend erneut registrieren.

Wenn Sie Android Enterprise-Arbeitsprofilgeräte über das Konto eines [Geräteregistrierungs-Managers](device-enrollment-manager-enroll.md) registrieren, besteht pro Konto ein Grenzwert von 10 registrierbaren Geräten.

Weitere Informationen finden Sie unter [Von Intune an Google gesendete Daten](data-intune-sends-to-google.md).

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Genehmigen der Unternehmensportal-App im verwalteten Google Play Store

Sie müssen die Unternehmensportal-App für Android im verwalteten Google Play Store genehmigen, um sicherzustellen, dass Benutzer immer Zugriff auf die neueste Version der Unternehmensportal-App haben. Indem Sie sie genehmigen, stellen Sie sicher, dass jeder Benutzer automatische Updates erhält. Wenn Sie sie nicht genehmigen, wird das Unternehmensportal schließlich veraltet sein und möglicherweise keine wichtigen Fehlerbehebungen oder neuen Features erhalten, wenn Microsoft diese veröffentlicht.

Führen Sie die folgenden Schritte durch, um das Intune-Unternehmensportal zu genehmigen:

1.  Suchen Sie die Unternehmensportal-App im [verwalteten Google Play Store](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Melden Sie sich beim verwalteten Google Play Store mit dem gleichen Google-Konto an, mit dem Sie die Bindung für Android Enterprise konfiguriert haben.
3.  Klicken Sie auf **Genehmigen**. Daraufhin wird ein neues Dialogfeld geöffnet.
4.  Überprüfen Sie die Berechtigungen in diesem Dialogfeld, und klicken Sie dann auf **Genehmigen**. Sie müssen diese Berechtigungen zulassen, um der Unternehmensportal-App die Verwaltung des Arbeitsprofils auf dem Gerät zu ermöglichen.
5.  Wählen Sie **Genehmigt lassen, wenn Apps neue Berechtigungen anfordern** aus, und klicken Sie dann auf **Speichern**.

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Weiterführende Schritte für Android Enterprise-Arbeitsprofile
- [Hinzufügen von verwalteten Google Play-Apps für Android Enterprise-Geräte mit Intune](apps-add-android-for-work.md)
- [Apply features and settings on your devices using device profiles in Microsoft Intune (Anwenden von Features und Einstellungen für Ihre Geräte mithilfe von Geräteprofilen in Microsoft Intune)](device-profiles.md)
