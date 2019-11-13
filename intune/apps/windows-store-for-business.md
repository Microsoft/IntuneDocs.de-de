---
title: Verwalten von VPP-Apps aus Microsoft Store für Unternehmen
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Apps aus Microsoft Store für Unternehmen in Intune synchronisieren können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04bc1fac8d3362a173c4777cdf5228fed6b6349d
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712537"
---
# <a name="how-to-manage-volume-purchased-apps-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Verwalten von VPP-Apps (Apple Volume Purchase Program) aus Microsoft Store für Unternehmen mit Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Im [Microsoft Store für Unternehmen](https://www.microsoft.com/business-store) können Sie Apps für Ihre Organisation suchen und einzeln oder im Rahmen eines Volumenprogramms erwerben. Indem Sie den Store mit Microsoft Intune verbinden, können Sie im Rahmen von per Volumenlizenz erworbenen Apps über das Azure-Portal verwalten. Beispiel:
* Sie können die Liste der Apps, die Sie im Speicher erworben haben (oder die kostenlos sind), mit Intune synchronisieren.
* Synchronisierte Apps werden in der Intune-Verwaltungskonsole angezeigt und können wie alle anderen Apps zugewiesen werden.
* Sowohl online als auch offline lizenzierte App-Versionen werden mit Intune synchronisiert. App-Namen wird im Portal entweder die Bezeichnung „Online“ oder „Offline“ angefügt.
* Sie können in der Intune-Verwaltungskonsole die Anzahl der verfügbaren und der verwendeten Lizenzen nachverfolgen.
* Intune blockiert die Zuweisung und Installation von Apps, wenn nicht genügend Lizenzen vorhanden sind.
* Anwendungen, die von Microsoft Store für Unternehmen verwaltet werden, entziehen Lizenzen automatisch, wenn ein Benutzer das Unternehmen verlässt oder der Administrator den Benutzer und dessen Geräte entfernt.

## <a name="before-you-start"></a>Vorbereitung

Überprüfen Sie die folgenden Informationen, bevor Sie beginnen, Apps aus dem Microsoft Store für Unternehmen zu synchronisieren und zuzuweisen:

- Konfigurieren Sie Intune als Autorität zur Verwaltung mobiler Geräte für Ihre Organisation.
- Sie müssen im Microsoft Store für Unternehmen über ein registriertes Konto verfügen.
- Sobald ein Konto für den Microsoft Store für Unternehmen Intune zugeordnet wurde, können Sie dieses zugeordnete Konto nicht mehr ändern.
- Apps, die im Store erworben wurden, können Intune nicht manuell hinzugefügt oder daraus gelöscht werden. Sie können nur mit dem Microsoft Store für Unternehmen synchronisiert werden.
- Sowohl online als auch offline lizenzierte Apps, die Sie aus dem Microsoft Store für Unternehmen erworben haben, werden mit dem Intune-Portal synchronisiert. Sie können diese Apps dann für Geräte- oder Benutzergruppen bereitstellen. 
- Die Installation von Online-Apps wird über den Store verwaltet.
- Kostenlose Offline-Apps können ebenfalls mit Intune synchronisiert werden. Diese Apps werden durch Intune und nicht durch den Store installiert.
- Geräte müssen mit Active Directory Domain Services oder einem Arbeitsbereich verknüpft sein, damit diese Funktion verwendet werden kann.
- Registrierte Geräte müssen die Version 1511 oder höher von Windows 10 verwenden.

Ferner werden zugehörige Lizenzen und offline lizenzierte Apps aus dem Microsoft Store für Unternehmen ab sofort in der Benutzeroberfläche in einem App-Eintrag zusammengefasst. Bereitstellungsdetails aus den einzelnen Paketen werden in den jeweiligen Eintrag migriert. Wenn Sie verwandte Lizenzen im Azure-Portal abrufen möchten, wählen Sie auf der Seite **Client-Apps** die Option **App-Lizenzen** aus.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Verknüpfen Ihres Kontos für den Microsoft Store für Unternehmen mit Intune
Bevor Sie die Synchronisierung in der Intune-Konsole aktivieren, müssen Sie Ihr Konto für den Windows Store für Unternehmen so konfigurieren, dass Intune als Verwaltungstool verwendet wird:
1. Stellen Sie sicher, dass Sie sich beim [Microsoft Store für Unternehmen](https://www.microsoft.com/business-store) und bei Intune mit demselben Mandantenkonto anmelden.
2. Wählen Sie im Store für Unternehmen die Registerkarte **Verwalten**, **Einstellungen** und die Registerkarte **Verteilen** aus.
3. Wenn Sie nicht ausdrücklich **Microsoft Intune** als Verwaltungstool für mobile Geräte angegeben haben, wählen Sie **Verwaltungstool hinzufügen** aus, um **Microsoft Intune** hinzuzufügen. Wenn Sie nicht **Microsoft Intune** als Ihr Verwaltungstool für mobile Geräte aktiviert haben, klicken Sie neben **Microsoft Intune** auf **Aktivieren**. Beachten Sie, dass Sie **Microsoft Intune** statt **Microsoft Intune-Registrierung** aktivieren sollten.

> [!NOTE]
> Zuvor konnten Sie nur ein Verwaltungstool zum Zuweisen von Apps mit Microsoft Store für Unternehmen zuweisen. Nun können Sie mehrere Verwaltungstools dem Store zuordnen, z.B. Intune und Configuration Manager. 

Sie können nun fortfahren und die Synchronisierung in der Intune-Konsole einrichten.

## <a name="configure-synchronization"></a>Konfigurieren der Synchronisierung

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** die Option **Client-Apps** aus.
1. Wählen Sie im Bereich **Client-Apps** die Option **Setup** > **Microsoft Store für Unternehmen** aus.
2. Klicken Sie auf **Aktivieren**.
3. Klicken Sie auf den Link zur Registrierung für den Microsoft Store für Unternehmen, falls Sie dies noch nicht getan haben, und weisen Sie Ihr Konto wie oben beschrieben zu.
5. Wählen Sie in der Dropdownliste **Sprache** die Sprache aus, in der Apps aus dem Microsoft Store für Unternehmen im Azure-Portal angezeigt werden sollen. Die Installation der Apps erfolgt unabhängig von der Anzeigesprache in der Sprache des Endbenutzers, sofern verfügbar.
6. Klicken Sie auf **Synchronisieren**, um die im Microsoft Store erworbenen Apps in Intune abzurufen.

## <a name="synchronize-apps"></a>Synchronisieren von Apps

1. Wählen Sie in der Workload **Client-Apps** die Option **Setup** > **Microsoft Store für Unternehmen** aus.
2. Klicken Sie auf **Synchronisieren**, um die im Microsoft Store erworbenen Apps in Intune abzurufen.

> [!NOTE]
> Apps mit verschlüsselten App-Paketen werden derzeit nicht unterstützt und nicht mit Intune synchronisiert.

## <a name="assign-apps"></a>Zuweisen von Apps

Sie weisen Apps aus dem Store auf die gleiche Weise wie andere Intune-Apps zu. Weitere Informationen finden Sie unter [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md). 

Offline-Apps können Benutzergruppen, Gerätegruppen oder Gruppen mit Benutzern und Geräten als Ziel haben.
Offline-Apps können für einen bestimmten Benutzer auf einem Gerät oder für alle Benutzer auf einem Gerät installiert werden. 


Wenn Sie eine App aus dem Microsoft Store für Unternehmen zuweisen, wird von jedem Benutzer, der die App installiert, eine Lizenz verwendet. Wenn alle verfügbaren Lizenzen für eine zugewiesene App verwendet werden, können Sie keine weiteren Kopien zuweisen. Unternehmen Sie eine der folgenden Aktionen aus:
* Deinstallieren Sie die App auf einigen Geräten.
* Beschränken Sie die aktuelle Zuweisung auf die Anzahl von Benutzern, für die Sie über Lizenzen verfügen.
* Erwerben Sie zusätzliche Kopien der App im Microsoft Store für Unternehmen.

## <a name="remove-apps"></a>Entfernen von Apps

Sie müssen sich beim Microsoft Store für Unternehmen anmelden und die App kündigen, um eine App zu entfernen, die über den Microsoft Store für Unternehmen synchronisiert wird. Der Prozess ist identisch, ob die App kostenlos ist oder nicht. Für eine kostenlose App werden im Store 0US-Dollar rückerstattet. Das folgende Beispiel zeigt eine Rückerstattung für eine kostenlose App. 

![Screenshot vom Entfernen der App](./media/windows-store-for-business/microsoft-store-for-business-01.png)

> [!NOTE]
> Durch Entfernen der Sichtbarkeit einer App im privaten Store wird die Synchronisierung der App durch Intune nicht beendet. Sie müssen eine Rückerstattung für die App leisten, um die App vollständig zu entfernen.

## <a name="next-steps"></a>Nächste Schritte

- [Verwalten von per Volumenlizenz erworbenen Apps und Büchern mit Microsoft Intune](../vpp-apps.md)
