---
title: Umbenennen eines Geräts mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Benennen Sie ein Gerät mithilfe von Microsoft Intune um.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 11b339a3e94e60db43e8237d9f3d2c729b48a57d
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413608"
---
# <a name="rename-a-device-in-intune"></a>Umbenennen eines Geräts in Intune

Mithilfe der Aktion **Gerät umbenennen** können Sie ein Gerät umbenennen, das bei Intune registriert ist. Der Name des Geräts wird sowohl in Intune als auch auf dem Gerät geändert.

Sie können die folgenden Gerätetypen umbenennen:
- Unternehmenseigene Windows-Geräte 
- iOS-/iPadOS-Modus wird überwacht
- Unternehmenseigene macOS 10-Geräte

Dieses Feature unterstützt derzeit nicht das Umbenennen von Windows-Geräten mit Azure AD Hybrid.

## <a name="rename-a-device"></a>Umbenennen eines Geräts

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
3. Klicken Sie auf **Geräte** > **Alle Geräte**, und wählen Sie ein Gerät aus. Klicken Sie dann auf **Mehr** > **Gerät umbenennen**.
4. Geben Sie auf dem Blatt **Gerät umbenennen** den neuen Namen in das Textfeld ein. Sie können Buchstaben, Zahlen und Bindestriche verwenden. Der Name muss mindestens einen Buchstaben oder Bindestrich enthalten.
5. Wenn Sie das Gerät nach dem Umbenennen neu starten möchten, wählen Sie neben **Restart after rename** (Nach Umbenennung neu starten) die Option **Ja** aus.
6. Klicken Sie auf **Umbenennen**.

## <a name="windows-device-rename-rules"></a>Umbenennungsregeln für Windows-Geräte
Wird ein Windows-Gerät umbenannt, müssen beim neuen Namen folgende Regeln eingehalten werden:
- Der Name sollte aus 15 oder weniger Zeichen (d. h. weniger als oder gleich 63 Byte ohne nachstehender NULL) bestehen.
- Der Name sollte nicht NULL sein oder aus einer leeren Zeichenfolge bestehen.
- Zulässiger ASCII-Code: Buchstaben (a-z, A-Z), Zahlen (0-9) und Bindestriche
- Zulässige Unicode-Zeichen: Zeichen >= 0x80, muss eine gültige UTF-8-Codierung und die IDN-Zuordnung (RtlIdnToNameprepUnicode erfolgreich, weitere Informationen finden Sie im RFC 3492) aufweisen
- Namen dürfen nicht nur aus Zahlen bestehen.
- Es dürfen keine Leerzeichen im Namen enthalten sein.
- Unzulässige Zeichen: { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)


## <a name="next-steps"></a>Nächste Schritte

Der Status der Aktion **Umbenennen** des Geräts wird auf dessen **Übersichtsseite** angezeigt.
