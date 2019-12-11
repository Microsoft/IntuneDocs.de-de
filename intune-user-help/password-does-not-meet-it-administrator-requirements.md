---
title: Kenn Wort Anforderungen für Geräte in InTune-Unternehmensportal | Microsoft-Dokumentation
description: In diesem Artikel werden allgemeine Kenn Wort Anforderungen beschrieben, die Ihre Organisation möglicherweise erzwingt.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/05/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: efb3c261-1f6c-4d39-bfa4-18661f8c59c7
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9181510dad2640fcc8ea84ce2db2856bd02cbaf5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502179"
---
# <a name="device-password-requirements-for-enrolled-devices"></a>Geräte Kennwort-Anforderungen für registrierte Geräte

In Ihrer Organisation kann es erforderlich sein, ein sicheres Kennwort zu erstellen, bevor Sie Zugriff auf Geschäfts-, Schul-oder uniressourcen haben. In diesem Artikel werden allgemeine Kenn Wort Anforderungen für Windows 10-, Ios-, macOS-und Android-Geräte beschrieben. Ihre Organisation erzwingt möglicherweise nicht alle diese Anforderungen.  


Wenn ein Kennwort oder eine Kennung nicht mehr die Anforderung erfüllt, erhalten Sie eine Meldung von Unternehmensportal. Dabei werden die Änderungen beschrieben, die Sie vornehmen müssen. Wenn in der Nachricht keine Details bereitgestellt werden, verwenden Sie diesen Artikel als Referenz für den Vergleich mit Ihrem aktuellen Kennwort.  

> [!IMPORTANT]
> Wenn Sie Ihr Kennwort geändert haben, um die Anforderungen zu erfüllen, aber weiterhin Benachrichtigungen erhalten, starten Sie das Gerät neu.  

Wenden Sie sich an Ihren IT-Support, um zusätzliche Hilfe zu erhalten oder um die spezifischen Anforderungen Ihrer Organisation zu ermitteln. Auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980) finden Sie Kontaktinformationen.  

## <a name="windows-10-password-requirements"></a>Kenn Wort Anforderungen für Windows 10

| Nachricht | Beheben |
|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Das Kennwort ist erforderlich. | Legen Sie ein Kennwort fest. Ihre Organisation erfordert, dass Sie ein Kennwort eingeben, um das Gerät zu entsperren. |
| Das Kennwort ist zu einfach. |  Stellen Sie sicher, dass Ihr Kennwort keine sequenziellen oder sich wiederholenden Zahlen wie 1234 oder 1111 enthält. |
| Das Kennwort ist zu kurz.| Aktualisieren oder legen Sie ein Kennwort mit mehr Zeichen fest. Ihre Organisation erfordert, dass Ihr Kennwort eine bestimmte Länge hat. Was Sie tatsächlich auswählen, ist unterschiedlich, aber die erforderliche Mindestlänge beträgt 4 Zeichen, und der Höchstwert beträgt 16. |
| Das Kennwort darf nur Zahlen enthalten. | Legen Sie ein Kennwort fest, das nur Zahlen enthält.|
| Das Kennwort darf nur alphanumerische Zeichen enthalten. | Legen Sie ein Kennwort fest, das eine Mischung aus Zahlen und Buchstaben enthält.|
| Das Kennwort muss komplexe Zeichen enthalten. | Fügen Sie komplexe Zeichen hinzu, wie z. b. Zahlen, Großbuchstaben und Symbole wie `$`, `%`und `#`. Ihre Organisation erfordert eine Mischung aus Buchstaben, Zahlen und nicht alphanumerischen Zeichen, damit andere Benutzer das Kennwort nicht erraten können.|  
| Das Kennwort ist abgelaufen. | Legen Sie ein neues Kennwort fest. Ihre Organisation verlangt, dass Sie Ihr Kennwort nach einer bestimmten Anzahl von Tagen ändern. |
| Das Kennwort wurde erst kürzlich verwendet. | Wählen Sie ein Kennwort aus, das Sie zuvor noch nicht verwendet haben. Ihre Organisation erfordert, dass eine bestimmte Zeitspanne verstrichen ist, bevor Sie ein Kennwort wieder verwenden. |

## <a name="ios-passcode-requirements"></a>IOS-Kennungs Anforderungen

| Nachricht | Beheben |
|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Die Kennung ist erforderlich.| Legen Sie einen Passcode fest. Ihre Organisation erfordert, dass Sie eine Kennung eingeben, um das Gerät zu entsperren. |
| Die Kennung ist zu einfach. |  Stellen Sie sicher, dass Ihre Kennung keine sequenziellen oder sich wiederholenden Zahlen enthält, wie z. b. 1234 oder 1111. |
| Die Kennung ist zu kurz. | Aktualisieren Sie eine Kennung, oder legen Sie eine Kennung mit mehr Zeichen fest. Ihre Organisation erfordert, dass Ihre Kennung eine bestimmte Länge hat. Was Sie tatsächlich auswählen, ist unterschiedlich, aber die erforderliche Mindestlänge beträgt 4 Zeichen, und der Höchstwert beträgt 14. Wenn Sie Ihre Kennung ändern, wird möglicherweise eine Eingabeaufforderung von Apple angezeigt, die Sie darüber informiert, dass Sie 6 oder mehr Zeichen eingeben müssen. Diese Meldung ist eine Apple-System Empfehlung. Wenn für Ihre Organisation nur eine Kennung von 4 oder 5 Zeichen erforderlich ist, müssen Sie keine 6-stellige Kennung eingeben.|  
| Die Kennung darf nur Zahlen enthalten. | Legen Sie eine Kennung fest, die nur Zahlen enthält.|
| Die Kennung darf nur alphanumerische Zeichen enthalten.| Legen Sie eine Kennung fest, die eine Mischung aus Zahlen und Buchstaben enthält.|
| Die Kennung muss nicht alphanumerische Zeichen enthalten. | Fügen Sie Sonderzeichen hinzu, z. b. `&`, `!`, `$`, `%`und `#`. Ihre Organisation erfordert eine Mischung aus Buchstaben, Zahlen und nicht alphanumerischen Zeichen, damit andere Benutzer die Kennung nicht erraten können.|
| Der Passcode ist abgelaufen. | Legen Sie ein neues Kennwort fest. Ihre Organisation verlangt, dass Sie Ihr Kennwort nach einer bestimmten Anzahl von Tagen ändern. |
| Ihre Kennung wurde zu kurzem verwendet.| Wählen Sie einen Passcode aus, den Sie zuvor noch nicht verwendet haben. Ihre Organisation erfordert, dass eine bestimmte Zeitspanne verstrichen ist, bevor Sie eine Kennung wieder verwenden. |
|Fingereingabe-ID oder Gesichts-ID-Authentifizierung erforderlich. | Einrichten der Fingereingabe-ID oder der Gesichts-ID. Ihre Organisation erfordert, dass Sie sich mit einer dieser Methoden authentifizieren, bevor Sie Auto Ausfüllen für Kenn Wörter oder Kreditkarteninformationen verwenden. | 

## <a name="macos-password-requirements"></a>Kennwortanforderungen unter macOS
| Nachricht | Beheben |
|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Das Kennwort ist erforderlich. | Legen Sie ein Kennwort fest. Ihre Organisation erfordert, dass Sie ein Kennwort eingeben, um das Gerät zu entsperren. |
| Das Kennwort ist zu einfach.|  Stellen Sie sicher, dass Ihr Kennwort keine sequenziellen oder sich wiederholenden Zahlen wie 1234 oder 1111 enthält. |
| Das Kennwort ist zu kurz. | Aktualisieren oder legen Sie ein Kennwort mit mehr Zeichen fest. Ihre Organisation erfordert, dass Ihr Kennwort eine bestimmte Länge hat.|
| Das Kennwort darf nur Zahlen enthalten. | Legen Sie ein Kennwort fest, das nur Zahlen enthält.|
| Das Kennwort darf nur alphanumerische Zeichen enthalten. | Legen Sie ein Kennwort fest, das eine Mischung aus Zahlen und Buchstaben enthält.|
| Das Kennwort muss nicht alphanumerische Zeichen enthalten. | Fügen Sie Sonderzeichen hinzu, z. b. `&`, `!`, `$`, `%`und `#`. Ihre Organisation erfordert eine Mischung aus Buchstaben, Zahlen und nicht alphanumerischen Zeichen, damit andere Benutzer das Kennwort nicht erraten können.|
| Das Kennwort ist abgelaufen. | Legen Sie ein neues Kennwort fest. Ihre Organisation verlangt, dass Sie Ihr Kennwort nach einer bestimmten Anzahl von Tagen ändern. |
| Das Kennwort wurde erst kürzlich verwendet. | Wählen Sie ein Kennwort aus, das Sie zuvor noch nicht verwendet haben. Ihre Organisation erfordert, dass eine bestimmte Zeitspanne verstrichen ist, bevor Sie ein Kennwort wieder verwenden. |

## <a name="android-password-requirements"></a>Android-Kenn Wort Anforderungen
| Nachricht | Beheben |
|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Das Kennwort ist erforderlich. | Legen Sie ein Kennwort oder eine PIN fest. Ihre Organisation erfordert, dass Sie ein Kennwort eingeben, um das Gerät zu entsperren. |
| Das Kennwort ist zu einfach. |  Stellen Sie sicher, dass Ihr Kennwort oder Ihre PIN keine sequenziellen oder sich wiederholenden Zahlen enthält, wie etwa 1234 oder 1111. |
| Das Kennwort ist zu kurz. | Aktualisieren oder legen Sie ein Kennwort mit mehr Zeichen fest. Ihre Organisation erfordert, dass Ihr Kennwort eine bestimmte Länge hat.|
| Das Kennwort muss Ziffern enthalten. | Legen Sie ein Kennwort oder eine PIN fest, das Zahlen enthält.|
| Das Kennwort muss Buchstaben enthalten. | Legen Sie ein Kennwort fest, das Buchstaben aus dem Alphabet enthält.|
| Das Kennwort muss alphanumerische Zeichen enthalten. | Legen Sie ein Kennwort fest, das eine Mischung aus Zahlen und Buchstaben enthält.|
| Das Kennwort muss alphanumerische Zeichen und Symbole enthalten. | Legen Sie ein Kennwort fest, das eine Kombination aus Buchstaben, Ziffern und Sonderzeichen enthält, wie z. b. `&`, `!`, `$`, `%`und `#`. |
| Für das Kennwort muss biometrische Technologie verwendet werden.| Richten Sie Ihr Gerät für die Verwendung der biometrischen Authentifizierung ein, z. b. Fingerabdruck oder Gesichtserkennung.
| Das Kennwort ist abgelaufen. | Legen Sie ein neues Kennwort fest. Ihre Organisation verlangt, dass Sie Ihr Kennwort nach einer bestimmten Anzahl von Tagen ändern. |
| Das Kennwort wurde erst kürzlich verwendet. | Wählen Sie ein Kennwort aus, das Sie zuvor noch nicht verwendet haben. Ihre Organisation erfordert, dass eine bestimmte Zeitspanne verstrichen ist, bevor Sie ein Kennwort wieder verwenden. |

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Artikeln finden Sie Informationen zum Erstellen oder Ändern des Kennworts, der Kennung oder der PIN für das Gerät.  

- [Festlegen des Windows 10-Geräte Kennworts](set-or-change-your-password-windows.md)  
- [Festlegen der Passcodes für IOS-Geräte](set-or-change-your-passcode-ios.md)  
- [Festlegen der PIN oder des Kennworts für ein Android-Gerät](set-your-pin-or-password-android.md)  

Benötigen Sie weitere Unterstützung? Wenden Sie sich an den Support. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  


