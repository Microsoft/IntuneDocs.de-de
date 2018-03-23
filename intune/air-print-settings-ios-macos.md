---
title: Intune AirPrint-Einstellungen für iOS- und macOS-Geräte
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Microsoft Intune verwenden können, um iOS- und macOS-Geräte automatisch mit AirPrint-kompatiblen Druckern zu verbinden.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8402ff3631e18ec6169bc96ef1bb7669bdcfbdd8
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
---
# <a name="airprint-settings-for-ios-and-macos-devices"></a>AirPrint-Einstellungen für iOS- und macOS-Geräte

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Verwenden Sie diese Einstellungen, um iOS- oder macOS-Geräte für die automatische Verbindung mit AirPrint-kompatiblen Druckern im Netzwerk zu konfigurieren. Sie benötigen die IP-Adresse und den Ressourcenpfad der Drucker, um fortzufahren.

## <a name="find-airprint-printer-information"></a>Ermitteln von AirPrint-Druckerinformationen

Mit diesem Verfahren können Sie AirPrint-Informationen zur AirPrint-Nutzlast hinzufügen, sodass Benutzer von iOS-Geräten auf bekannten AirPrint-Druckern drucken können.

1. Öffnen Sie das Terminal auf einem Mac, der mit dem gleichen lokalen Netzwerk (Subnetz) verbunden ist wie die AirPrint-Drucker (über **/Anwendungen/Hilfsprogramme**).
2. Geben Sie im Terminal die Zeichenfolge **ippfind** ein, und drücken Sie die EINGABETASTE.
3. Notieren Sie sich die vom Befehl zurückgegebenen Druckerinformationen, z.B.: **ipp://myprinter.local.:631/ipp/port1**. Beim ersten Teil der Informationen handelt es sich um den Namen des Druckers, beim letzten Teil um den Ressourcenpfad.
4. Geben Sie im Terminal die Zeichenfolge **ping myprinter.local** ein, und drücken Sie die EINGABETASTE.
5. Notieren Sie sich die vom Befehl zurückgegebenen IP-Adressinformationen, z.B.: **PING myprinter.local (10.50.25.21)**.
6. Verwenden Sie die IP-Adresse und den Ressourcenpfad in den Einstellungen der AirPrint-Nutzlast. Eine IP-Adresse könnte beispielsweise **10.50.25.21** lauten, ein Ressourcenpfad **/ipp/port1**.

## <a name="configure-an-airprint-profile"></a>Konfigurieren eines AirPrint-Profils

1. Navigieren Sie von [Intune im Azure-Portal](https://portal.azure.com) zu [**Gerätefeatures** im Gerätekonfigurationsbereich](device-features-configure.md). 
1. Klicken Sie im Bereich **Gerätefeatures** auf die Option **AirPrint**.
2. Geben Sie im Bereich **AirPrint** die **IP-Adresse** und den **Ressourcenpfad** des Ziels ein, und klicken Sie auf **Hinzufügen**, um ein AirPrint-Ziel hinzuzufügen.
3. Fügen Sie so viele Ziele hinzu, wie Sie benötigen. Wenn Sie fertig sind, wählen Sie **OK** aus.

Sie können auch eine Liste mit Druckern aus einer Datei mit durch Trennzeichen getrennten Werten (CSV-Datei) importieren oder die Liste exportieren.


## <a name="next-steps"></a>Nächste Schritte

Sie können nun das Geräteprofil den von Ihnen ausgewählten Gruppen zuweisen. Weitere Informationen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).