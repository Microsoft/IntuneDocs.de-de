---
title: Testen und Überprüfen von Intune
titleSuffix: Microsoft Intune
description: Informationen zum Testen und Überprüfen in der Nur-Cloud-Lösung von Intune in Ihrer Umgebung
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 3/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2ce184a2dbd0ca4b66740f0687302d1ed007878
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505021"
---
# <a name="intune-testing-and-validation"></a>Testen und Überprüfen von Intune

Berücksichtigen Sie beim Testen der Implementierung von Microsoft Intune Funktions- und Anwendungsfallüberprüfungen. Bei der Funktionsüberprüfung werden die einzelnen Komponenten und die Konfiguration getestet, um deren ordnungsgemäße Funktionsweise zu überprüfen. Anwendungsfallüberprüfungen umfassen Tests, die sicherstellen, dass die Szenarios im Zusammenhang mit einer Reihe von Aufgaben wie erwartet funktionieren. 

Es wird empfohlen, Ihre IT-Support- und Helpdeskmitarbeiter in die Testphase einzubeziehen, damit sie eine Supportdokumentation erstellen und sich mit der Unterstützung des Produkts vertraut machen. Wenn eine Komponente oder ein Szenario auf der Grundlage der Anwendungsfälle nicht funktioniert, stellen Sie sicher, dass die notwendigen Änderungen dokumentiert werden. Geben Sie dabei den Grund für die Änderung an.

## <a name="before-you-begin"></a>Vorbereitung

Wir empfehlen, die folgenden Schritte zu dokumentieren:

- **Testkriterien:** Identifizieren Sie die Benchmarks, anhand derer die Messung erfolgt.

- **Entwurfskomponenten**: Müssen in mindestens einem Testkriterium vorhanden sein.

Wenn eine Entwurfskomponente nicht in mindestens einem auf eine Anforderung oder ein Szenario ausgerichteten Testkriterium vorhanden ist, überlegen Sie, ob die Entwurfskomponente erforderlich ist oder nicht. Stellen Sie darüber hinaus sicher, dass die folgenden Elemente vorhanden sind:

- **Konten**: Testkonten, die für EMS und Office 365 lizenziert sind, um alle Anwendungsszenarios testen zu können.

- **Geräte:** Testgeräte, die zurückgesetzt oder auf Werkseinstellungen zurückgesetzt werden können.

- **Integrationskomponenten**: Alle Integrationskomponenten (Zertifikatsconnectors und die lokalen Intune Exchange-Connectors) sollten installiert und bei Bedarf konfiguriert sein.

Sie benötigen möglicherweise Entwurfsänderungen, um unvorhergesehene Probleme zu berücksichtigen. Darüber hinaus müssen alle Entwurfsänderungen vollständig zusammen mit der jeweiligen Begründung dokumentiert werden. Hier sehen Sie ein Beispiel für die Veranschaulichung einer Änderung:

<blockquote>Sie stellen fest, dass Sie die Anforderungen des Registrierungsdiensts für Netzwerkgeräte (SCEP) nicht erfüllen. Zudem erfahren Sie, dass die VPN- und WLAN-Profile mit einer Stammzertifizierungsstelle konfiguriert werden können, die dieselben Anforderungen ohne eine SCEP-Implementierung erfüllt.</blockquote>

Möglicherweise gibt es Herausforderungen oder Probleme, die technische Hilfe oder eine spezielle Problembehandlung während des Test- und Überprüfungsprozesses erfordern. Es wird empfohlen, dass Sie sich an die Microsoft-Supportkanäle wenden.

- [Informationen zum Erhalten von Intune-Support](../get-support.md)

- [Kontaktieren des telefonischen Supports für Microsoft Intune](../get-support.md)

## <a name="functional-validation-testing"></a>Test zur Funktionsüberprüfung

Bei der Funktionsüberprüfung werden die einzelnen Komponenten und die Konfiguration getestet, um deren ordnungsgemäße Funktionsweise zu überprüfen. Ein Beispiel für einen Überprüfungstest ist in der folgenden Tabelle aufgeführt.

![Abschnitt 9 Tabelle 1](./media/planning-guide-test-validation/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>Test zur Anwendungsfallüberprüfung

Führen Sie Tests zur Anwendungsfallüberprüfung aus, um sicherzustellen, dass die Szenarios vollständig und funktionsfähig sind. Es gibt zwei Arten von Anwendungsszenarios: IT-Administrator und Endbenutzer.

### <a name="it-admin"></a>IT-Administrator

Führen Sie Überprüfungstests für IT-Administratoren aus, um sicherzustellen, dass administrative Aktionen für ein Gerät oder einen Benutzer ordnungsgemäß funktionieren. Es folgt ein Beispiel für ein umfassendes Überprüfungsszenario für IT-Administratoren.

![Abschnitt 9 Tabelle 2](./media/planning-guide-test-validation/section-9-image-2-table.PNG)

### <a name="end-user"></a>Endbenutzer

Führen Sie Überprüfungstests für Endbenutzer aus, um sicherzustellen, dass das Endbenutzererlebnis den Erwartungen entspricht und in der gesamten Benutzerkommunikation korrekt dargestellt wird. Es ist wichtig, zu überprüfen, dass die Endbenutzererfahrung richtig ist. Wenn Sie dies nicht überprüfen können, kann dies zu einer niedrigen Akzeptanz und höheren Volumen an Helpdesk-Aufrufen führen.

![Abschnitt 9 Tabelle 3](./media/planning-guide-test-validation/section-9-image-3-table.PNG)

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Ihre Intune-Funktionen und -Anwendungsszenarios getestet und überprüft haben, sind Sie für den [Intune-Rollout in die Produktion](../planning-guide-rollout-plan.md) bereit.

Weitere Planungsvorlagen und Informationen finden Sie in den [zusätzlichen Ressourcen](../planning-guide-resources.md).
