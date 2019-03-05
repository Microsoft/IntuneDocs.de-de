---
title: Windows Information Protection-Einstellungen in Microsoft Intune | Microsoft Intune
description: Erfahren Sie mehr über die Microsoft Intune-Einstellungen, die Sie für die Verwaltung von Windows Information Protection verwenden können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6a5dea2075def1d7a30fdebc5722c4117a1579f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229631"
---
# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>Konfigurieren von Windows Information Protection in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Immer mehr Mitarbeiter möchten mit ihren eigenen Geräten im Unternehmen arbeiten. Dadurch steigt das Risiko versehentlicher Datenlecks durch Apps und Dienste wie E-Mail, soziale Medien und die öffentliche Cloud, die sich außerhalb der Kontrolle des Unternehmens befinden. Einige Beispiele: Ein Mitarbeiter sendet Fotos der neuesten technischen Entwicklung von einem persönlichen E-Mail-Konto, kopiert Produktinformationen in einen Tweet oder speichert einen laufenden Vertriebsbericht in öffentlichem Cloudspeicher.

**Windows Information Protection** unterstützt Sie dabei, das Unternehmen vor solchen potenziellen Datenlecks zu schützen, ohne gleichzeitig die Benutzerfreundlichkeit für die Mitarbeiter einzuschränken. Die Lösung schützt auch Unternehmens-Apps und -Daten vor versehentlichen Datenlecks auf unternehmenseigenen sowie auf persönlichen Geräten, die die Mitarbeiter zur Arbeit mitbringen – ohne dass Sie Ihre Umgebung oder andere Apps ändern müssen.

Die Intune-Richtlinie verwaltet die Liste der von Windows Information Protection geschützten Apps sowie die zugehörigen Speicherorte im Unternehmensnetzwerk, die Schutzebene und Verschlüsselungseinstellungen.

>[!NOTE]
> Um die Windows 10-Unternehmensportal-App mit Windows Information Protection verwenden zu können, müssen Sie die Unternehmensportal-App unter dem Windows Information Protection-Modus **Ausnahme** hinzufügen. 

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen finden Sie in folgenden Quellen:
-  [Schützen von Unternehmensdaten mit Windows Information Protection](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)
- [Erstellen einer Windows Information Protection-Richtlinie (WIP) mithilfe der klassischen Konsole für Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune)
- [Erstellen einer Windows Information Protection-Richtlinie (WIP) mit MDM mithilfe des Azure-Portals für Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune-azure)
- [Erstellen einer Windows Information Protection-Richtlinie (WIP) mit MAM mithilfe des Azure-Portals für Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure)
