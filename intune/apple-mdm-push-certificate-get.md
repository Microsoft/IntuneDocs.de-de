---
title: Abrufen eines Apple-MDM-Push-Zertifikats
titlesuffix: Microsoft Intune
description: "Lernen Sie die Schritte kennen, mit denen Sie ein Apple-MDM-Push-Zertifikat zum Verwalten von iOS-Geräten mit Intune abrufen."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/29/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ed6ae1812e49fa0ceda3079d25afd92ceeac01bd
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="get-an-apple-mdm-push-certificate"></a>Abrufen eines Apple-MDM-Push-Zertifikats

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune ermöglicht die Verwaltung mobiler Geräte (mobile device management, MDM) wie iPads, iPhones und Mac-Computer und ermöglicht Benutzern den Zugriff auf Unternehmens-E-Mails und -Apps. Für die Verwaltung von iOS- und Mac-Geräten ist ein MDM-Push-Zertifikat erforderlich. Wenn Sie das Zertifikat in Intune hinzugefügt haben, können Ihre Benutzer die Unternehmensportal-App installieren, um ihre Geräte zu registrieren. Sie können auch die Verwaltung firmeneigener iOS-Geräte mit dem Geräteregistrierungsprogramm von Apple einrichten oder Geräte beispielsweise mithilfe von Apple Configurator registrieren. Weitere Informationen zu Registrierungsoptionen finden Sie unter [Auswählen der Registrierungsmethode für iOS-Geräte](enrollment-method-choose-ios.md).

## <a name="steps-to-get-your-certificate"></a>Erforderliche Schritte, um Ihr Zertifikat abzurufen
Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Geräteregistrierung** > **Apple-Registrierung** > **Apple-MDM-Push-Zertifikat** aus, und führen Sie im [Azure-Portal](https://portal.azure.com) die folgenden Schritte aus.

**Schritt 1: Laden Sie die erforderliche Anforderung zur Signierung eines Intune-Zertifikats herunter, um ein Apple-MDM-Push-Zertifikat erstellen zu können.**<br>
Klicken Sie auf **CSR herunterladen**, um die Anforderungsdatei herunterzuladen und lokal zu speichern. Die Datei wird verwendet, um ein Vertrauensstellungszertifikat vom Apple Push Certificates-Portal anzufordern.

  ![Der Bildschirm „MDM-Push-Zertifikat konfigurieren“, auf dem MDM Push nicht eingerichtet ist.](./media/create-mdm-push-certificate.png)

**Schritt 2: Erstellen Sie ein Apple-MDM-Push-Zertifikat.**<br>
Wählen Sie **Eigenes MDM-Push-Zertifikat erstellen** aus, um zum Apple Push Certificates Portal zu gelangen. Melden Sie sich mit der Apple-ID Ihres Unternehmens an, und klicken Sie dann auf **Zertifikat erstellen**. Klicken Sie auf **Datei auswählen**, und suchen Sie die Anforderungsdatei für die Signierung des Zertifikats. Klicken Sie dann auf **Hochladen**. Klicken Sie auf der Bestätigungsseite auf **Herunterladen**, um die Zertifikatdatei (.pem) herunterzuladen, und speichern Sie die Datei lokal.

> [!NOTE]
> Das Zertifikat ist mit der Apple-ID verknüpft, die verwendet wurde, um es zu erstellen. Als bewährte Methode verwenden Sie eine Unternehmens-Apple-ID für Verwaltungsaufgaben. Verwenden Sie niemals eine persönliche Apple-ID.

**Schritt 3: Geben Sie die zum Erstellen Ihres Apple-MDM-Push-Zertifikats verwendete Apple-ID ein.**<br>
Notieren Sie sich diese ID, damit Sie sich daran erinnern, wenn Sie das Zertifikat erneuern müssen.

**Schritt 4: Navigieren Sie zu Ihrem hochzuladenden Apple-MDM-Push-Zertifikat.**<br>
Wechseln Sie zur Zertifikatsdatei (.pem), wählen Sie **Öffnen** aus, und wählen Sie dann **Hochladen**aus. Mit dem Push-Zertifikat kann Intune Apple-Geräte registrieren und verwalten.

## <a name="renew-apple-mdm-push-certificate"></a>Erneuern eines Apple-MDM-Push-Zertifikats
Das Apple-MDM-Push-Zertifikat ist für ein Jahr gültig und muss jährlich erneuert werden, um die Geräteverwaltung von iOS und macOS beizubehalten. Wenn Ihr Zertifikat abläuft können registrierte Apple-Geräte nicht kontaktiert werden.

Das Zertifikat ist mit der Apple-ID verknüpft, die verwendet wurde, um es zu erstellen. Erneuern Sie das MDM-Push-Zertifikat mit derselben Apple-ID, mit der es erstellt wurde.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Geräteregistrierung** > **Apple-Registrierung** und dann **Apple-MDM-Push-Zertifikat** aus.
2. Wählen Sie **CSR herunterladen** aus, um die CSR-Datei herunterzuladen und lokal zu speichern. Die Datei wird verwendet, um ein Vertrauensstellungszertifikat vom Apple Push Certificates-Portal anzufordern.
3. Wählen Sie **Eigenes MDM-Push-Zertifikat erstellen** aus, um zum Apple Push Certificates Portal zu gelangen. Suchen Sie das Zertifikat, das Sie erneuern möchten, und wählen Sie **Erneuern** aus.
4. Schreiben Sie auf dem Bildschirm **Push-Zertifikat erneuern** Notizen, die Ihnen zukünftig bei der Identifizierung des Zertifikats helfen. Klicken Sie auf **Datei auswählen**, um die neue Anforderungsdatei zu durchsuchen, die Sie heruntergeladen haben und dann auf **Hochladen**.
   > [!TIP]
   > Ein Zertifikat kann durch die Benutzer-ID identifiziert werden. Überprüfen Sie die **Antragsteller-ID** in den Zertifikatdetails, um den GUID-Teil der Benutzer-ID zu finden. Wenn Sie ein registriertes iOS-Gerät verwenden, klicken Sie auf **Einstellungen** > **Allgemein** > **Gerät** **Verwaltung** > **Verwaltungsprofil** > **Weitere Details** > **Verwaltungsprofil**. Das zweite Zeilenelement **Thema**, enthält die eindeutige GUID, die Sie mit dem Zertifikat im Apple Push Certificates-Portal vergleichen können.
 
6. Wählen Sie auf dem Bildschirm **Bestätigen** die Option **Herunterladen** aus, und speichern Sie die PEM-Datei lokal.
7. Wählen Sie im [Azure-Portal](https://portal.azure.com) das Symbol zum Durchsuchen des **Apple-MDM-Push-Zertifikats** aus, wählen Sie die PEM-Datei, die Sie von Apple heruntergeladen haben und anschließend **Hochladen** aus.

Ihr Apple MDM-Push-Zertifikat erscheint als **aktiv** und läuft in 365 Tagen ab.
