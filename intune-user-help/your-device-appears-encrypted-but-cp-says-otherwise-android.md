---
title: Ihr Android-Gerät ist offenbar verschlüsselt | Microsoft-Dokumentation
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55935b2f69f9573d8df5ea5ca32fb4587c652b26
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57389462"
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>Es sieht so aus, als sei Ihr Gerät verschlüsselt, aber das Unternehmensportal sagt etwas anderes

Beim Verschlüsseln eines Geräts werden die darauf enthaltenen Informationen mit einem geheimen Schlüssel verschlüsselt, der nur Ihnen bekannt ist. So wird verhindert, dass unautorisierte Personen darauf zugreifen können. Bei vielen Unternehmen müssen die Benutzer ihre Android-Geräte verschlüsseln, bevor sie auf Unternehmensdateien, E-Mails oder Daten zugreifen können.

## <a name="common-issues"></a>Häufige Probleme

Neuere Versionen von Android, insbesondere ab Version 7.0, fordern eine Startkennung an, um sicherzustellen, dass Ihr Gerät vollständig verschlüsselt ist. Verschiedene Gerätehersteller weisen unterschiedliche Beschreibungen und Stellen für die Startkennung auf. Zumeist wird diese Einstellung als „Sicherer Start“ bezeichnet. 

## <a name="solutions"></a>Lösungen

### <a name="add-a-startup-pin"></a>Hinzufügen einer Start-PIN

Bei bestimmten Android-Geräten müssen Sie eine Start-PIN erstellen, um die Sicherheit Ihres Geräts zu gewährleisten. Es gibt viele Versionen von Android von vielen Herstellern. Sie können versuchen, dieses Problem in den Griff zu bekommen, indem Sie in Ihrem Menüpunkt „Einstellungen“ die Stelle zum Aktivieren dieser Option finden. Auf dem Samsung Galaxy S7 aktivieren Sie beispielsweise „Sicherer Start“ über **Einstellungen** > **Sperrbildschirm und Sicherheit** > **Sicherer Start**.  

### <a name="encrypt-the-entire-device"></a>Verschlüsseln Sie das gesamte Gerät

Bei einigen Geräten haben Sie die Wahl: Sie können entweder das gesamte Gerät verschlüsseln oder nur den tatsächlich belegten Speicherplatz. Wählen Sie die Option zum Verschlüsseln des gesamten Geräts und nicht die Option „only used space“ (nur belegter Speicherplatz). Wenn Sie bereits nur den belegten Speicherplatz verschlüsselt haben:

1. [Entfernen Sie dieses Geräts aus dem Unternehmensportal](unenroll-your-device-from-intune-android.md).
2. Entschlüsseln Sie den belegten Speicherplatz.
3. Verschlüsseln Sie das gesamte Gerät
4. Registrieren Sie das Gerät erneut.

### <a name="downgrade-your-version-of-android"></a>Herabstufen Ihrer Android-Version

Falls Ihr Gerät Ihnen die Option gibt, auf Android 6.0+ downzugraden, machen Sie dies. Falls Sie versuchen, Ihr Gerät downzugraden, besteht die Gefahr, dass Daten verloren gehen. Wenden Sie sich andernfalls an die Supportabteilung Ihres Unternehmens, um dieses Problem zu beheben. Entsprechende Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).

## <a name="specific-manufacturer-issues"></a>Spezifische Herstellerprobleme

Einige Android-Geräte mit Version 7.0+ verschlüsseln Daten so, dass sie mit gewissen Android-Plattformstandards nicht kompatibel sind. Diese Geräte werden möglicherweise verschlüsselt angezeigt, selbst wenn sie neu sind. Intune erkennt, dass die Informationen des Geräts durch die Verschlüsselungsmethoden dieser Geräte gefährdet werden. Dieses Risiko entsteht ist in erster Linie durch böswillige Benutzer, die physikalischen Zugriff auf das Gerät haben.

> [!Note]
> Microsoft arbeitet mit Herstellern zusammen, um Probleme zu beheben, die wir beim Testen finden oder die Benutzer uns melden. Dieser Artikel wird aktualisiert, sobald neue Informationen verfügbar sind. 

## <a name="known-devices"></a>Bekannte Geräte

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>Bekannte Geräte, die aktualisiert werden können, um dieses Problem zu beheben

Wenn Sie Ihr Gerät auf die neueste Version von Android aktualisiert haben, rufen Sie Ihres Geräts **Einstellungen** app, und wählen **Update**. Diese Geräte möglicherweise als nicht konform angezeigt, bis Sie aktualisieren:  

- Huawei Honor 8
- Huawei P9

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>Bekannte Geräte, die derzeit nicht aktualisiert werden können, um dieses Problem zu beheben
Die folgenden Geräte werden immer verschlüsselte angezeigt und können nicht verwendet werden, um den Zugriff auf Unternehmensressourcen. Um auf Unternehmensressourcen zuzugreifen, müssen Sie ein anderes Gerät verwenden.  

- Huawei Mate 8
- OPPO-Geräte
- Vivo-Geräte
- Xiaomi Mi-Smartphones
