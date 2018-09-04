---
title: Was geschieht, wenn Sie die Registrierung für Ihr Windows-Gerät aufheben? | Microsoft-Dokumentation
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 92cd7969dafb133cf044e2bf5fd2c6d0f829f6ff
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "43150377"
---
# <a name="what-happens-if-you-unenroll-your-windows-device-from-intune"></a>Was geschieht, wenn Sie die Registrierung Ihres Windows-Geräts bei Intune aufheben?

Informationen zum verwendeten Gerätetyp finden Sie über die Links rechts auf dieser Seite unter **Inhalt dieses Artikels**.


## <a name="windows-10-windows-81-windows-8-windows-7-windows-vista"></a>Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista

-   Ihr Gerät wird nicht mehr im Unternehmensportal angezeigt, und Sie können über das Unternehmensportal keine Apps mehr installieren.

-   Wenn die Intune-Clientsoftware installiert ist, wird diese von Ihrem Computer entfernt.

-   Die Intune Endpoint Protection-Software wird von Ihrem Computer entfernt. Wenn auf dem Computer eine andere Virenschutzsoftware installiert ist und diese deaktiviert wurde, kann sie nach dem Entfernen von Intune Endpoint Protection wieder aktiviert werden. Überprüfen Sie Ihren Computer nach dem Entfernen aus dem Unternehmensportal.

    > [!IMPORTANT]
    > Wenn die andere Virenschutzsoftware nicht wieder aktiviert wird oder keine andere Virenschutzsoftware installiert ist, bleibt der Computer unter Umständen anfällig für Viren und Schadsoftware.

-   Alle Einstellungen, die beim Hinzufügen des Geräts auf diesem geändert wurden (z.B. das Deaktivieren der Kamera), werden unwirksam.

-   Automatische Softwareupdates und Updates der Antivirensoftware vom Intune-Dienst werden nicht mehr auf dem Computer empfangen. Der Computer könnte jedoch je nach Einrichtung weiterhin Updates von Windows Server Update Services, Windows Update oder Microsoft Update empfangen.

Zusätzlich für Windows 8.1:

-   Sie können keine Unternehmens-Apps und Unternehmensdaten mehr auf dem Gerät verwenden.

-   In einigen E-Mail-Apps wie Windows Mail kann nicht mehr auf Unternehmens-E-Mails zugegriffen werden, die auf dem Gerät gespeichert sind.

-   Möglicherweise können Sie keine Verbindung mit dem Unternehmensnetzwerk über WLAN oder ein virtuelles privates Netzwerk herstellen.

-   Unter Umständen haben Sie auf dem Gerät keinen Zugriff mehr auf einige Unternehmensressourcen wie Dateifreigaben oder interne Websites.

## <a name="windows-10-mobile-and-windows-phone-81"></a>Windows 10 Mobile und Windows Phone 8.1

-   Die Unternehmensportal-App wird auf Ihrem Gerät deinstalliert. Ihr Gerät wird nicht mehr im Unternehmensportal angezeigt, und Sie können über die Unternehmensportal-App bzw. die Unternehmensportal-Website keine Apps installieren.

-   Sie können keine Unternehmens-Apps und Unternehmensdaten mehr auf dem Gerät verwenden.

-   Alle Einstellungen, die beim Hinzufügen des Geräts auf diesem geändert wurden, z.B. das Deaktivieren der Kamera oder die Anforderung einer bestimmten Kennwortlänge, werden unwirksam.

    > [!IMPORTANT]
    > Die einzige Ausnahme sind die Verschlüsselungsrichtlinien, die weiterhin wirksam sind. Wenn in Ihrer Unternehmensrichtlinie vorgeschrieben war, dass Sie Ihr Windows Phone verschlüsseln, können Sie Ihr Telefon nur noch entschlüsseln, indem Sie es über das Menü **Einstellungen** zurücksetzen.

## <a name="windows-rt-running-windows-81"></a>Windows RT, das Windows 8.1 ausführt

-   Die Unternehmensportal-App wird auf Ihrem Gerät deinstalliert. Das bedeutet, dass Ihr Gerät nicht mehr im Unternehmensportal angezeigt wird, und Sie über das Unternehmensportal keine Apps installieren können.

-   Sie können keine Unternehmens-Apps und Unternehmensdaten mehr auf dem Gerät verwenden.

-   Alle Einstellungen, die beim Hinzufügen des Geräts auf diesem geändert wurden, z.B. das Deaktivieren der Kamera oder die Anforderung einer bestimmten Kennwortlänge, werden unwirksam.

-   Möglicherweise können Sie mit dem Unternehmensnetzwerk keine Verbindung mehr über WLAN oder ein virtuelles privates Netzwerk (VPN) herstellen.

-   Unter Umständen haben Sie auf dem Gerät keinen Zugriff mehr auf einige Unternehmensressourcen wie Dateifreigaben oder interne Websites.

-   In einigen E-Mail-Apps wie Windows Mail kann nicht mehr auf Unternehmens-E-Mails zugegriffen werden, die auf dem Gerät gespeichert sind.

Wenn Sie Ihr Windows RT-Gerät entfernen, geschieht Folgendes:

-   Die Unternehmensportal-App wird auf Ihrem Gerät deinstalliert. Das bedeutet, dass Ihr Gerät nicht mehr im Unternehmensportal angezeigt wird, und Sie über das Unternehmensportal keine Apps installieren können.

-   Sie können keine Unternehmens-Apps und Unternehmensdaten mehr auf dem Gerät verwenden.

-   Alle Einstellungen, die beim Hinzufügen des Geräts auf diesem geändert wurden, z.B. das Deaktivieren der Kamera oder die Anforderung einer bestimmten Kennwortlänge, werden unwirksam.

Wenn Sie Fragen haben, wenden Sie sich an den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).
