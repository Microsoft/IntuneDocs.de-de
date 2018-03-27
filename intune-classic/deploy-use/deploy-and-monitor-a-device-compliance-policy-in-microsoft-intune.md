---
title: Bereitstellen und Überwachen einer Konformitätsrichtlinie
description: Befolgen Sie die schrittweisen Anweisungen in diesem Thema zum Bereitstellen und Überwachen einer Konformitätsrichtlinie für Geräte.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d8f246d4-0d86-4c8b-a1bf-9977985506d8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e24c969206d3e1f34bfee0af46c4398c9d2739a8
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune"></a>Bereitstellen und Überwachen einer in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="deploy-a-compliance-policy"></a>Bereitstellen einer Konformitätsrichtlinie
Stellen Sie die von Ihnen [erstellte](create-a-device-compliance-policy-in-microsoft-intune.md) Kompatibilitätsrichtlinie für eine oder mehrere Gruppen von Benutzern in Ihrer Organisation bereit. Wenn Sie eine Kompatibilitätsrichtlinie für einen Benutzer bereitstellen, wird die Kompatibilität der Geräte des Benutzers überprüft.

1.  Wählen Sie im Arbeitsbereich **Richtlinie** die Richtlinie aus, die Sie bereitstellen möchten, und wählen Sie anschließend **Bereitstellung verwalten** aus.
![Screenshot der Seite „Kompatibilitätsrichtlinie“ mit der Menüoption „Bereitstellung verwalten“ ganz oben](./media/intune-sa-3c-deploy-compliance-policy2.png)

2.  Wählen Sie im Dialogfeld **Bereitstellung verwalten** mindestens eine Gruppe aus, für die die Richtlinie bereitgestellt werden soll, und wählen Sie dann **Hinzufügen** > **OK** aus.
![Screenshot des Dialogfelds „Bereitstellung verwalten“](./media/intune-sa-3d-deploy-compliance-policy3-Manage.png) Verwenden Sie bereits erstellte und mit Intune synchronisierte Active Directory-Gruppen aus, oder erstellen Sie diese Gruppen manuell in der Intune-Konsole. Weitere Informationen zum Bereitstellen von Richtlinien finden Sie unter [Bereitstellen einer Konfigurationsrichtlinie](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Verwenden Sie die Statuszusammenfassung und Warnungen auf der Seite **Übersicht** des Arbeitsbereichs **Richtlinie**, um Probleme mit der Richtlinie zu identifizieren, die Ihre Aufmerksamkeit erfordern. Darüber hinaus wird eine Statusübersicht im Arbeitsbereich **Dashboard** angezeigt.

> [!IMPORTANT]
> Wenn Sie keine Kompatibilitätsrichtlinie bereitgestellt haben und dann die Exchange-Richtlinie für bedingten Zugriff aktivieren, erhalten alle betreffenden Geräte Zugriff.

## <a name="monitor-the-compliance-policy"></a>Überwachen der Konformitätsrichtlinie

#### <a name="to-view-devices-that-do-not-conform-to-a-compliance-policy"></a>So zeigen Sie Geräte an, die keiner Konformitätsrichtlinie entsprechen

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) **Gruppen** > **Alle Geräte** aus.

2.  Doppelklicken Sie in der Geräteliste auf den Namen eines Geräts.

3.  Wählen Sie die Registerkarte **Richtlinie** aus, um eine Liste der Richtlinien für das Gerät anzuzeigen.

4.  Wählen Sie in der Dropdownliste **Filter** die Option **Entspricht nicht der Kompatibilitätsrichtlinie** aus.
![Screenshot mit der Liste der Optionen in der Filterliste](./media/intune-sa-3e-view-device-noncompliance.png)

#### <a name="to-view-the-health-attestation-reports"></a>So zeigen Sie die Integritätsnachweisberichte an

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Option **Berichte** aus.

2.  Auf der Seite **Integritätsnachweisbericht - Neuen Bericht erstellen** können Sie einen Bericht mit allen von Intune erfassten Windows 10-Integritätsnachweisdaten anzeigen. Sie können mithilfe von Filtern auch einen Bericht für eine Teilmenge der Daten erstellen. Die Filter können auf dem Gerätetyp, Betriebssystem oder auf einer Teilmenge der Datenpunkte basieren.

## <a name="how-intune-resolves-policy-conflicts"></a>Wie Intune-Richtlinienkonflikte löst
Richtlinienkonflikte können auftreten, wenn mehrere Intune-Richtlinien auf ein Gerät angewendet werden. Wenn sich Richtlinieneinstellungen überschneiden, löst Intune Konflikte nach den folgenden Regeln:

-   Wenn die in Konflikt stehenden Einstellungen zu einer Intune-Konfigurationsrichtlinie und einer Kompatibilitätsrichtlinie gehören, haben die Einstellungen in der Kompatibilitätsrichtlinie Vorrang vor den Einstellungen in der Konfigurationsrichtlinie. Dies geschieht auch, wenn die Einstellungen in der Konfigurationsrichtlinie sicherer sind.

-   Wenn Sie mehrere Kompatibilitätsrichtlinien bereitgestellt haben, verwendet Intune die sichersten dieser Richtlinien.

## <a name="next-steps"></a>Nächste Schritte
Wie Sie die Kompatibilitätsrichtlinie zusammen mit Richtlinien für bedingten Zugriff verwenden können, um den Zugriff auf Dienste in Ihrer Organisation zu steuern, erfahren Sie unter [Beschränken des Zugriffs auf E-Mail- und Office 365-Dienste](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).


### <a name="see-also"></a>Siehe auch
[Einführung in Richtlinien zur Gerätekompatibilität in Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md)
