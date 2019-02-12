---
title: Grundlegendes zur Benutzerfreundlichkeit der Registrierung von iOS-Geräten
titlesuffix: Microsoft Intune
description: Lernen Sie die den Registrierungsprozess umfassend kennen, indem Sie ein iOS-Gerät registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 487ad607bc34d5fc2137f1b3903b0711e793658d
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55840540"
---
# <a name="understand-the-users-experience-enrolling-an-ios-device"></a>Grundlegendes zur Benutzerfreundlichkeit der Registrierung von iOS-Geräten

Mit Microsoft Intune können Sie Ihre Belegschaft mit mobilen Geräten ausstatten, ohne dass Ihre Unternehmensdaten gefährdet werden. Da Ihre Endbenutzer mit Intune eher auf ihren Geräten als in der Verwaltungskonsole interagieren, sollten Sie mit der Registrierung vertraut sein. Auf diese Weise können Sie ausgezeichnete Kompatibilitätsrichtlinien zusammen mit Ihrer Erfahrung nutzen, um sich in die Lage Ihrer Benutzer hineinzuversetzen. Dies ist besonders wichtig, da Ihre Benutzer genau wissen werden, welche Informationen Sie als Administrator sehen können:

| Was für die IT nicht einsehbar ist | Was für die IT einsehbar ist |
|---|---|
| Ihren Anrufs- und Browserverlauf | Modell |
| Standort | Seriennummer |
| Ihren persönlichen E-Mail-Account | Betriebssystemversion |
| SMS | App-Namen |
| Kontakte | Besitzer |
| Die Kennwörter für Ihre persönlichen Accounts | Gerätename |
| Ihre Termine | Der Hersteller (gilt nur für Geräte, die nicht von Apple hergestellt wurden) |
| Ihre Bilder, einschließlich dem, was sich in der Fotos- und Kamera-App befindet | Telefonnummer (Bei Arbeitsgeräten die vollständige Nummer). Bei persönlichen Geräten nur die letzten vier Ziffern.) |

## <a name="how-do-i-enroll-a-device"></a>Wie registriere ich ein Gerät?

Das Registrieren eines Geräts ist für viele Endbenutzer beim Zugriff auf Unternehmensressourcen die erste Erfahrung. [Vertrautheit mit dieser Erfahrung](end-user-educate.md) kann ein möglicherweise unangenehmes Erlebnis in ein besseres verwandeln.

1. Öffnen Sie den **App Store**, und suchen Sie nach **Intune-Unternehmensportal**.
2. Laden Sie die App **Microsoft Intune-Unternehmensportal** herunter.
3. Öffnen Sie die **Unternehmensportal-App**, geben Sie die E-Mail-Adresse und das Kennwort Ihres Testbenutzers ein, und tippen Sie dann auf **Anmelden**.
4. Ersetzen Sie das temporäre Kennwort durch ein neues.
5. Tippen Sie auf der Seite **Unternehmenszugriff einrichten** auf **Geräteregistrierung**.
6. Lesen Sie auf der Seite **Gründe für das Registrieren Ihres Geräts**, welche Möglichkeiten ein Benutzer bei der Geräteregistrierung hat, und tippen Sie dann auf **Weiter**.
7. Sehen Sie sich in einer Liste an, welchen Zugriff ein Benutzer bei der Registrierung erhält, und tippen Sie dann auf **Weiter**.
8. Sehen Sie sich an, was IT-Administratoren auf einem Gerät sehen können und was nicht, und tippen Sie dann auf **Weiter**.
9. Lesen Sie auf der Seite **Was ist der nächste Schritt?**, was während der Registrierung passiert, und tippen Sie dann auf **Registrieren**.
10. Tippen Sie auf der Seite **Profil installieren** auf **Installieren**, und geben Sie dann bei Aufforderung die Gerätekennung ein.
11. Tippen Sie auf **Installieren**.
12. Tippen Sie erneut auf **Installieren**, um anzugeben, dass Sie die Warnung gelesen haben.
13. Tippen Sie im Popupfenster **Warnung** auf **Vertrauen**.
14. Wenn auf dem Bildschirm angezeigt wird, dass die Installation des Profils abgeschlossen ist, tippen Sie auf **Fertig**.
15. Auf dem Bildschirm wird die Meldung „Gerät wird registriert“ angezeigt und im Anschluss gemeldet, dass das Gerät erfolgreich registriert wurde. Es öffnet sich ein Popupfenster mit der Aufforderung, die Seite im Unternehmensportal zu öffnen. Tippen Sie auf **Öffnen**.
16. Sie kehren zur Seite **Unternehmenszugriff einrichten** zurück. Wenn Sie keine Testrichtlinien eingerichtet haben, sollte das Gerät als kompatibel angezeigt werden. Wenn Testrichtlinien vorhanden sind, tippen Sie auf **Gerätekompatibilität** und es wird angezeigt, dass Schritte durchgeführt werden müssen, um das Gerät sicherer zu machen.

## <a name="next-steps"></a>Nächste Schritte

[Erste Schritte beim Hinzufügen von Apps:](get-started-apps.md) Suchen Sie Apps, und fügen Sie sie auf Geräten hinzu, um Ihren Mitarbeitern die Arbeit zu erleichtern.

## <a name="learn-more"></a>Erfahren Sie mehr

* [Registrierungsoptionen für Intune](enrollment-options.md)
* [Aktivieren von BYOD mit Intune](byod-enable.md)
* [So informieren sie Ihre Benutzer über Microsoft Intune](end-user-educate.md)
