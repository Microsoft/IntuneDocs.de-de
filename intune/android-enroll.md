---
title: "Registrieren von Android-Geräten in Intune"
titlesuffix: Microsoft Intune
description: "Erfahren Sie, wie Sie Android-Geräte in Intune registrieren."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a72199c9e38f4f4d9d7317469eea2e6254efee7
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="enroll-android-devices"></a>Registrieren von Android-Geräten

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Als Intune-Administrator können Sie Android-Geräte verwalten, einschließlich Geräte nach dem Samsung Knox-Standard. Sie können außerdem das Arbeitsprofil [Android for Work-Geräte](#enable-enrollment-of-android-for-work-devices) verwalten.

Geräte, die mit Samsung Knox-Standard ausgeführt werden, werden für die Mehrbenutzerverwaltung von Intune unterstützt. Dies bedeutet, dass Benutzer sich bei einem Gerät mit ihren Azure AD-Anmeldeinformationen an- und abmelden können. Das Gerät wird zentral verwaltet, ganz gleich, ob es verwendet oder nicht. Wenn sich Benutzer anmelden, verfügen sie über Zugriff auf Apps und erhalten zusätzlich alle Richtlinien, die ihnen zugewiesen sind. Wenn sich Benutzer abmelden, werden alle App-Daten gelöscht.

## <a name="prerequisite"></a>Voraussetzung

Um auf die Verwaltung von mobilen Geräten vorzubereiten, müssen Sie die MDM-Autorität (Mobile Device Management, Verwaltung mobiler Geräte) auf **Microsoft Intune** festlegen. Anweisungen finden Sie unter [Festlegen der MDM-Autorität](mdm-authority-set.md). Sie legen dieses Element nur einmal fest, wenn Sie die Ersteinrichtung von Intune für die Verwaltung mobiler Geräte durchführen.

## <a name="set-up-android-enrollment"></a>Einrichten der Android-Registrierung

Standardmäßig erlaubt Intune die Registrierung von Android- und Samsung KNOX Standard-Geräten.

Um Android-Geräte oder nur die Registrierung von persönlichen Android-Geräten zu blockieren, gehen Sie unter [Festlegen von Gerätetypbeschränkungen](enrollment-restrictions-set.md).

Um die Geräteverwaltung zu aktivieren, müssen die Benutzer ihre Geräte durch Herunterladen der Intune-Unternehmensportal-App (bei Google Play verfügbar) registrieren und anschließend die App öffnen und den Anweisungen folgen. Sobald Android-Geräte verwaltet werden, können Sie [Konformitätsrichtlinien zuweisen](compliance-policy-create-android.md), [Apps verwalten](app-management.md) und mehr.

## <a name="enable-enrollment-of-android-for-work-devices"></a>Aktivieren der Registrierung von Android for Work-Geräten

Für die Aktivierung der Verwaltung von Arbeitsprofilen auf Geräten, die [Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) unterstützen, müssen Sie eine Android for Work-Bindung zu Intune hinzufügen. Wenn Sie Geräte in Android for Work registrieren möchten, die bereits als reguläre Android-Geräte registriert wurden, müssen Sie die Registrierung der Geräte aufheben und die Geräte anschließend erneut registrieren.

Wenn Sie Android for Work-Geräte mithilfe eines [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md)-Kontos registrieren, besteht pro Konto ein Grenzwert von 10 registrierbaren Geräten.

## <a name="add-android-for-work-binding-for-intune"></a>Hinzufügen der Android for Work-Bindung für Intune

> [!NOTE]
> Aufgrund der Interaktion zwischen den Domänen „Google“ und „Microsoft“ müssen Sie möglicherweise Ihre Browsereinstellungen anpassen, um diesen Schritt erfolgreich abzuschließen.  Stellen Sie sicher, dass „portal.azure.com“ und „play.google.com“ sich in der gleichen Sicherheitszone Ihres Browsers befinden.

1. **Einrichten von Intune MDM**<br>
Wenn nicht bereits geschehen, bereiten Sie die Verwaltung mobiler Geräte durch [Festlegen der Autorität für die Verwaltung mobiler Geräte](mdm-authority-set.md) auf **Microsoft Intune** vor.
2. **Konfigurieren der Android for Work-Bindung**<br>
    Wählen Sie als Intune-Administrator im Azure-Portal **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.

   ein. Wählen Sie auf dem Blatt **Intune** die Option **Geräteregistrierung**  > **Android for Work-Registrierung** und dann **Konfigurieren** aus, um die Android for Work-Website von Google Play zu öffnen. Die Website wird auf einer neuen Registerkarte im Browser geöffnet.
   ![Android for Work-Registrierungsbildschirm](./media/android-work-bind.png)

   b. **Anmelden bei Google**<br>
   Geben Sie auf der Anmeldeseite von Google das Google-Konto an, das allen Android for Work-Verwaltungsaufgaben für diesen Mandanten zugeordnet sein wird. Dies ist das Google-Konto, das von den IT-Administratoren Ihres Unternehmens gemeinsam zum Verwalten und Veröffentlichen von Apps in der Play for Work-Konsole verwendet wird. Sie können ein vorhandenes Google-Konto verwenden oder ein neues Konto erstellen.  Das von Ihnen ausgewählte Konto sollte einer G-Suite-Domäne zugeordnet sein.

   c. **Bereitstellen von Informationen zur Organisation**<br>
   Geben Sie den Namen Ihres Unternehmens als **Organisationsnamen** ein. Für den **Enterprise Mobility Verwaltungsanbieter (EMM)** sollte **Microsoft Intune** angezeigt werden. Stimmen Sie der Android for Work-Vereinbarung zu, und wählen Sie dann **Bestätigen** aus. Ihre Anforderung wird verarbeitet.

## <a name="specify-android-for-work-enrollment-settings"></a>Angeben von Registrierungseinstellungen für Android for Work
Android for Work wird nur auf bestimmten Android-Geräten unterstützt. Sehen Sie sich die [Voraussetzungen für Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22) an. Jedes Gerät, das Android for Work unterstützt, unterstützt auch die herkömmliche Android-Verwaltung. Mit Intune können Sie angeben, wie Geräte, die Android for Work unterstützen, mithilfe von [Registrierungseinschränkungen](enrollment-restrictions-set.md) verwaltet werden sollen.

- **Blockieren (Standardeinstellung)**: Alle Android-Geräte, einschließlich der Geräte, die Android for Work unterstützen, werden als herkömmliche Android-Geräte registriert.
- **Zulassen**: Alle Geräte, die Android for Work unterstützen, werden als Android for Work-Geräte registriert. Android-Geräte, die nicht Android for Work unterstützen, werden als herkömmliche Android-Geräte registriert.

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Genehmigen der Unternehmensportal-App im verwalteten Google Play Store
Sie müssen die Unternehmensportal-App für Android im verwalteten Google Play Store genehmigen, um sicherzustellen, dass diese automatische App-Updates erhält. Wenn Sie sie nicht genehmigen, wird das Unternehmensportal schließlich veraltet sein und möglicherweise keine wichtigen Fehlerbehebungen oder neuen Features erhalten, wenn Microsoft diese veröffentlicht.

Führen Sie die folgenden Schritte durch, um das Intune-Unternehmensportal zu genehmigen:

1.  Suchen Sie die Unternehmensportal-App im [verwalteten Google Play Store](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Melden Sie sich beim verwalteten Google Play Store mit dem gleichen Google-Konto an, mit dem Sie die Bindung für Android for Work konfiguriert haben.
3.  Klicken Sie auf **Genehmigen**. Daraufhin wird ein neues Dialogfeld geöffnet.
4.  Überprüfen Sie die Berechtigungen in diesem Dialogfeld, und klicken Sie dann auf **Genehmigen**. Sie müssen diese Berechtigungen zulassen, um der Unternehmensportal-App die Verwaltung des Arbeitsprofils auf dem Gerät zu ermöglichen.
5.  Wählen Sie **Genehmigt lassen, wenn Apps neue Berechtigungen anfordern** aus, und klicken Sie dann auf **Speichern**.

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Kommunizieren der Geräteregistrierung für den Zugriff auf Unternehmensressourcen an die Benutzer

Informieren Sie Ihre Benutzer, dass sie die Intune-Unternehmensportal-App von Google Play herunterladen, sie dann öffnen und den Aufforderungen folgen müssen, um ihr Gerät zu registrieren. Im Laufe des von der App geführten Registrierungsprozesses werden Benutzer darüber informiert, was sie erwarten können und was IT-Administratoren auf ihren Geräten sehen können und was nicht.

Sie können auch einen Link für Online-Registrierungsschritte senden: [Registrieren Ihres Android-Geräts bei Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android).

Informationen zu anderen Benutzeraufgaben finden Sie in den folgenden Artikeln:

- [Ressourcen zu Endbenutzerszenarios in Microsoft Intune](end-user-educate.md)
- [Verwenden Ihres Android-Geräts mit Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbind-your-android-for-work-administrative-account"></a>Aufheben der Bindung Ihres Android for Work-Administratorkontos

Sie können die Registrierung und die Verwaltung von Android for Work deaktivieren. Durch Auswählen von **Bindung aufheben** in der Intune-Verwaltungskonsole wird die Registrierung aller registrierten Android for Work-Geräte aufgehoben. Außerdem wird die Beziehung zwischen dem Android for Work-Konto und Intune entfernt.

### <a name="to-unbind-an-android-for-work-account"></a>Aufheben der Bindung für ein Android for Work-Konto

1. **Aufheben der Android for Work-Bindung**<br>
    Wählen Sie als Intune-Administrator im Azure-Portal **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.  Wählen Sie auf dem Blatt **Intune** die Option **Geräteregistrierung** > **Android for Work-Registrierung** und dann **Bindung aufheben** aus.

2. **Zustimmen zum Löschen der Android for Work-Bindung**<br>
  Wählen Sie **Ja** aus, um die Bindung zu löschen und die Registrierung von allen Android for Work-Geräten in Intune aufzuheben.
