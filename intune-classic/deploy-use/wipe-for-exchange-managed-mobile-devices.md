---
title: Zurücksetzen mobiler Geräte, die mit Exchange verwaltet werden
description: Mit Microsoft Intune können Sie mobile Geräte zurücksetzen, die mithilfe von Exchange ActiveSync (EAS) mit dem Intune Exchange Connector verwaltet werden.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e116b620-1e12-4b5c-9905-2f7acf2ae530
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 753e5e9dac7199dff18d110808524f05aa669036
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31016083"
---
# <a name="wipe-for-exchange-managed-mobile-devices"></a>Wipe for Exchange-managed mobile devices

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Mit Microsoft Intune können Sie mobile Geräte zurücksetzen, die mithilfe von Exchange ActiveSync (EAS) mit dem Intune Exchange Connector verwaltet werden. In der folgenden Tabelle werden die verfügbaren Funktionen zum Zurücksetzen über Exchange ActiveSync beschrieben:


|      Typ des Zurücksetzens       |              Windows 8.1 und Windows RT 8.1              |                            iOS                             |                          Android                          |
|-------------------------|----------------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|        Vollständiges Zurücksetzen        |          E-Mail-Konto und zwischengespeicherte E-Mails werden entfernt.           |                      Zurück auf XWerkseinstellungen.                       |                      Zurück auf Werkseinstellungen                       |
|  Selektives Zurücksetzen/E-Mail   |                  E-Mail-Konto wird entfernt                  |                       Nicht unterstützt.                       |                      Nicht unterstützt.                       |
| Selektives Zurücksetzen/Richtlinien | Die Durchsetzung von Richtlinien wird entfernt, es werden jedoch keine Einstellungen geändert. | Die Durchsetzung von XRichtlinien wird entfernt, es werden jedoch keine Einstellungen geändert. | Die Durchsetzung von Richtlinien wird entfernt, es werden jedoch keine Einstellungen geändert. |

