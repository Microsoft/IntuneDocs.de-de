---
title: Exchange-Zugriffsregeln für mobile Geräte
description: Exchange ActiveSync-Zugriffsregeln, die Geräteverbindungen mit EAS zulassen oder blockieren
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 208b9f45-02d9-413a-b86a-8bad9b5008fa
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 93dece592ce5280b1650303484bd24169814465c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31018735"
---
# <a name="exchange-access-rules-for-mobile-devices"></a>Exchange-Zugriffsregeln für mobile Geräte

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Die Exchange-Zugriffsregeln für mobile Geräte bestimmen die Ebene des Zugriffs, den diese Geräte auf Exchange ActiveSync erhalten. Diese Einstellungen betreffen alle mobilen Geräte, einschließlich der Geräte, die nicht in Microsoft Intune registriert sind. Sie können zunächst eine **Standardregel** definieren, die für alle mobilen Geräte gilt, auf welche keine benutzerdefinierten Regeln angewendet werden.

Die folgende Tabelle enthält die Zugriffsebenen, die von Exchange ActiveSync verwaltet werden:

|Zugriffsebene|Beschreibung|
|----------------|---------------|
|**Zugriff auf Exchange für Geräte zulassen**|Mit dem Status *Zugriff zulassen* können mobile Geräte mithilfe von Exchange ActiveSync synchronisieren und eine Verbindung mit dem Exchange-Server herstellen, um E-Mails abzurufen und Kalender, Kontakte, Aufgaben und Notizen zu verwalten. Dies wird so lange fortgeführt, wie das Gerät der von Ihnen in Exchange konfigurierten Richtlinie für das Exchange ActiveSync-Postfach entspricht, es sei denn, der Benutzer oder das jeweilige mobile Gerät wurde vom Exchange-Administrator blockiert.|
|**Zugriff auf Exchange für Geräte blockieren**|Im Status *Zugriff blockieren* sind mobile Geräte blockiert, und das Herstellen von Verbindungen mit dem Exchange-Server wird nicht zugelassen. Die Geräte empfangen einen Fehler „HTTP 403 Forbidden“. Der Benutzer erhält eine E-Mail-Nachricht vom Exchange-Server, in der er darüber informiert wird, dass das mobile Gerät nicht mehr auf sein Postfach zugreifen kann. Diese Nachricht kann nicht mit dem gesperrten mobilen Gerät empfangen werden. Mithilfe der Aufgabe **Nachricht an Benutzer festlegen** können Sie dieser Nachricht angepassten Text hinzufügen, um Anweisungen für Benutzer bereitzustellen, deren Geräte blockiert wurden. |
|**Geräte unter Quarantäne stellen, sodass Sie sie später zulassen oder blockieren können**|Wenn ein mobiles Gerät unter Quarantäne gestellt wird, kann es weiterhin eine Verbindung zum Exchange-Server herstellen. Ihm wird jedoch nur ein beschränkter Zugriff auf die Daten gewährt. Der Benutzer des Geräts kann seinen eigenen Ordnern mit dem Kalender, Kontakten, Aufgaben und Notizen Inhalt hinzufügen, aber das Gerät kann keine Inhalte aus dem Postfach des Benutzers abrufen. Der Benutzer empfängt eine einzelne E-Mail-Nachricht, die besagt, dass das mobile Gerät unter Quarantäne gestellt wurde. Diese Nachricht wird an das Gerät und den Posteingang des Benutzers gesendet. Mithilfe der Aufgabe **Nachricht an Benutzer festlegen** können Sie dieser Nachricht angepassten Text hinzufügen, um Anweisungen für Benutzer bereitzustellen, deren Geräte unter Quarantäne gestellt wurden.|

Eine Zugriffsstrategie enthält eine **Standardregel** und **Plattformausnahmen** und gilt für alle mobilen Geräte, die mit Exchange verbunden sind. Die folgende Tabelle enthält einige Beispiele für Zugriffsmethoden.


|    Zugriffsmethode    |                                                                                                                                                                                                                                                                                       Beschreibung                                                                                                                                                                                                                                                                                        |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Liste „Zulassen“       |                                                                                  Mit der <em>Liste „Zulassen“</em> können Sie einer Liste bekannter Geräte Zugriff gewähren und den Zugriff für alle anderen Geräte blockieren. Hierzu müssen Sie benutzerdefinierte Regeln für Geräteplattformen erstellen, die auf das Postfach eines Benutzers zugreifen können. Nachdem Sie eine solche Regel erstellt haben, müssen Sie in der Standardzugriffsregel festlegen, dass alle anderen Geräte blockiert oder unter Quarantäne gestellt werden. Zum Hinzufügen eines neuen Geräts zur Liste „Zulassen“ müssen Sie eine neue benutzerdefinierte Regel erstellen.                                                                                  |
|      Liste „Blockieren“       |                              Mit der <em>Liste „Blockieren“</em> können Sie allen Geräten standardmäßig Zugriff gewähren, aber eine Gruppe von Geräten blockieren, die keinen Zugriff auf Ihr Unternehmen haben sollen. Erstellen Sie die Liste „Blockieren“ mithilfe benutzerdefinierter Regeln, um die Geräteplattformen zu blockieren, die nicht mit den Postfächern Ihres Unternehmens synchronisiert werden sollen. Es empfiehlt sich, die Standardzugriffsregel so festzulegen, dass sie den Zugriff auf alle Geräte gewährt, die durch die bestehenden Regeln nicht explizit blockiert werden. Zum Hinzufügen eines neuen Geräts oder einer Gerätegruppe zur Liste „Blockieren“ müssen Sie eine neue benutzerdefinierte Regel erstellen.                               |
| Gemischtes Zulassen und Blockieren | Sie können nicht nur die Listen „Zulassen“ und „Blockieren“ erstellen, sondern auch neue mobile Geräte unter Quarantäne stellen, wenn sie ganz neu in das Unternehmen eingeführt und noch geprüft werden. Wenn Sie z. B. eine Liste „Blockieren“ für mobile Geräte erstellt haben, die nicht in Ihrem Unternehmen zugelassen sind, und eine Liste „Zulassen“ für mobile Geräte, die im Unternehmen zugelassen sind, können Sie in der Standardregel festlegen, dass Geräte unter Quarantäne gestellt werden sollen. Alle anderen Geräte werden automatisch unter Quarantäne gestellt. Dadurch können Sie neue Geräte erkennen, wenn sie in die Organisation eingeführt werden, und entscheiden, ob sie der Liste „Zulassen“ oder der Liste „Blockieren“ hinzugefügt werden sollen. |

Im folgenden Verfahren wird das Erstellen einer benutzerdefinierten Regel beschrieben.

## <a name="create-a-default-access-rule"></a>Erstellen einer Standardzugriffsregel

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Richtlinie**&gt; **Exchange ActiveSync**.

2.  Wählen Sie in der Liste **Standardregel** die Zugriffsregel aus, die Sie auf alle mobilen Geräte anwenden möchten, die nicht durch eine Regel oder persönliche Ausnahme abgedeckt werden. Wählen Sie **Speichern** aus.

Im folgenden Verfahren wird das Erstellen einer benutzerdefinierten Regel beschrieben:

## <a name="create-a-custom-access-rule"></a>Erstellen einer benutzerdefinierten Zugriffsregel

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Richtlinie**&gt; **Exchange ActiveSync**.

2.  Wählen Sie in der Liste **Plattformausnahmen** die Option **Regel hinzufügen** aus, und erstellen Sie dann eine benutzerdefinierte Regel. Wählen Sie **Speichern** aus.
