---
title: Registrieren von Android-Geräten in Intune
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Android-Geräte in Intune registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2b2b3ba5443cd95cd81bdca6d386ab95a2c831eb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190114"
---
# <a name="enroll-android-devices"></a>Registrieren von Android-Geräten

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Als Intune-Administrator können Sie die folgenden Android-Geräte verwalten:
- Android-Geräte, einschließlich Samsung Knox Standard-Geräte
- Android Enterprise-Geräte, einschließlich [Android-Arbeitsprofilgeräte](#enable-enrollment-of-android-for-work-devices) und Android-Kioskgeräte

Geräte, die mit Samsung Knox-Standard ausgeführt werden, werden für die Mehrbenutzerverwaltung von Intune unterstützt. Dies bedeutet, dass Benutzer sich bei einem Gerät mit ihren Azure AD-Anmeldeinformationen an- und abmelden können. Das Gerät wird zentral verwaltet, ganz gleich, ob es verwendet oder nicht. Wenn sich Benutzer anmelden, verfügen sie über Zugriff auf Apps und erhalten zusätzlich alle Richtlinien, die ihnen zugewiesen sind. Wenn sich Benutzer abmelden, werden alle App-Daten gelöscht.

## <a name="prerequisite"></a>Voraussetzung

Um auf die Verwaltung von mobilen Geräten vorzubereiten, müssen Sie die MDM-Autorität (Mobile Device Management, Verwaltung mobiler Geräte) auf **Microsoft Intune** festlegen. Anweisungen finden Sie unter [Festlegen der MDM-Autorität](mdm-authority-set.md). Sie legen dieses Element nur einmal fest, wenn Sie die Ersteinrichtung von Intune für die Verwaltung mobiler Geräte durchführen.

## <a name="set-up-android-enrollment"></a>Einrichten der Android-Registrierung

Standardmäßig erlaubt Intune die Registrierung von Android- und Samsung KNOX Standard-Geräten. Nachdem die Voraussetzung erfüllt wurde, müssen Administratoren [ihren Benutzern lediglich erklären, wie sie ihre Geräte registrieren](/intune-user-help/enroll-your-device-in-intune-android).

Nachdem ein Benutzer sich registriert hat, können Sie damit anfangen, die Geräte in Intune zu verwalten, dies umfasst das [Zuweisen von Gerätekonformitätsrichtlinien](compliance-policy-create-android.md), das [Verwalten von Apps](app-management.md) und mehr.

Informationen zu anderen Benutzeraufgaben finden Sie in den folgenden Artikeln:

- [Ressourcen zu Endbenutzerszenarios in Microsoft Intune](end-user-educate.md)
- [Verwenden Ihres Android-Geräts mit Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Um Android-Geräte oder nur die Registrierung von persönlichen Android-Geräten zu blockieren, gehen Sie unter [Festlegen von Gerätetypbeschränkungen](enrollment-restrictions-set.md).

## <a name="set-up-android-enterprise-enrollment"></a>Einrichten der Android Enterprise-Registrierung

Android Enterprise umfasst eine Reihe von Android-Gerätefeatures und -Diensten, die Ihre privaten Apps und Daten von Ihrem Arbeitsprofil trennt, das Geschäfts-Apps und -daten enthält. Android Enterprise-Geräte umfassen Arbeitsprofilgeräte und Kioskgeräte. 

Sie müssen zunächst [Android Enterprise mit Intune verknüpfen](connect-intune-android-enterprise.md), um die Registrierung für Android Enterprise-Geräte einzurichten. Nachdem Sie diesen Schritt ausgeführt haben, können Sie folgende Aktionen ausführen:

[Set up Android work profile enrollments (Einrichten von Android-Arbeitsprofilregistrierungen)](android-work-profile-enroll.md)
[Set up Android kiosk enrollments (Einrichten von Android-Kioskregistrierungen)](android-kiosk-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Endbenutzererfahrung bei der Registrierung eines Samsung KNOX-Geräts
Im Folgenden finden Sie einige Überlegungen bei der Registrierung von Samsung KNOX-Geräten:
-   Auch wenn keine Richtlinien eine PIN erfordern, muss das Gerät zumindest eine vierstellige PIN für die Registrierung besitzen. Wenn das Gerät über keine PIN verfügt, werden Benutzer aufgefordert, eine zu erstellen.
-   Für Arbeitsbereichverknüpfungszertifikate (Workplace Join Certificates, WPJ) gibt es keine Benutzerinteraktion.
-   Der Benutzer erhält Informationen zur Dienstregistrierung und zu den Funktionen der App.
-   Der Benutzer erhält Informationen zur KNOX-Registrierung und zu den Funktionen von KNOX.
-   Wenn eine Verschlüsselungsrichtlinie erzwungen wird, müssen Benutzer ein komplexes Kennwort, das aus sechs Zeichen besteht, für die Gerätekennung festlegen.
-   Es gibt keine zusätzlichen Aufforderungen an den Benutzer, Zertifikate zu installieren, die per Push von einem Dienst für den Zugriff auf Unternehmensressourcen gesendet werden.
- Benutzer werden von einigen älteren KNOX-Geräten aufgefordert, zusätzliche Zertifikate für den Zugriff auf Unternehmensressourcen bereitzustellen.
- Wenn ein Samsung Mini-Gerät die Arbeitsbereichverknüpfung nicht installieren kann, wird entweder der Fehler **Certificate Not Found** (Das Zertifikat wurde nicht gefunden.) oder **Unable to Register Device** (Das Gerät konnte nicht registriert werden.) ausgegeben. Installieren Sie dann die neuesten Samsung-Firmwareupdates.
