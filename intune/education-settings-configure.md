---
title: Konfigurieren der Intune-Einstellungen für Bildungseinrichtungen für Windows 10
titleSuffix: Microsoft Intune
description: In diesem Artikel erfahren Sie, wie Sie mit Intune Einstellungen für Windows 10 Education auf Geräten konfigurieren, die Sie verwalten.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 413ad0bab32353fc6f5b401f9a7b910b6c5cb390
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>Konfigurieren von Einstellungen für Bildungseinrichtungen für Windows 10 in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mit Education-Profilen können Sie Details für die Konfiguration der Windows Take a Test-App einschließlich Kontodetails und die Test-URL angeben. Wenn Sie diese Konfiguration vornehmen, öffnet sich die Take a Test-App mit dem angegebenen Test, und auf dem Gerät können keine anderen Apps ausgeführt werden, bevor der Test abgeschlossen ist.

Informationen zur „Take a Test“-App finden Sie unter [Durchführen von Prüfungen in Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).

## <a name="create-a-device-profile-containing-education-profile-settings"></a>Erstellen eines Geräteprofils mit Education-Profileinstellungen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Gerätekonfiguration**.
2. Klicken Sie im Bereich **Gerätekonfiguration** im Abschnitt **Verwalten** auf **Profile**.
3. Klicken Sie im Bereich „Profile“ auf **Profil erstellen**.
4. Geben Sie im Bereich **Profil erstellen** einen **Namen** und eine **Beschreibung** für das Geräteeinschränkungsprofil ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Option **Windows 10 und höher** aus.
6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Education-Profil** aus. 
7. Klicken Sie auf **Einstellungen > Konfigurieren**, und konfigurieren Sie im Bereich **Take a Test** (Prüfung) Folgendes:
    - **Kontotyp:** Wählen Sie aus dem Dropdownfeld einen Kontotypen aus.
    - **Kontobenutzername** – Geben Sie den Benutzernamen des Kontos ein, das mit Take a Test verwendet wird. Dies kann ein Domänenkonto, ein Azure Active Directory (AAD)-Konto oder ein lokales Computerkonto sein.
    - **Bewertungs-URL** – Geben Sie die URL des Tests an, den Benutzer ausführen sollen. Weitere Informationen finden Sie in der Take a Test-Dokumentation.
    - **Bildschirmaufnahme** – Geben Sie an, ob sie die Bildschirmaktivität aufnehmen möchten, während Benutzer einen Test ausführen.
    - **Textvorschlag** – Lassen Sie Textvorschläge zu oder blockieren sie diese, während Benutzer einen Test ausführen.
8. Wechseln Sie anschließend wieder zum Bereich **Profil erstellen**, und klicken Sie auf **Erstellen**.

Das Profil wird erstellt und im Bereich „Profilliste“ angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie fortfahren und dieses Profil Gruppen zuweisen möchten, lesen Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md) nach.



