---
title: Erstellen von Geräteprofilen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Fügen Sie ein Gerätekonfigurationsprofil in Microsoft Intune hinzu, oder konfigurieren Sie eines. Wählen Sie den Plattformtyp aus, konfigurieren Sie die Einstellungen, und fügen Sie eine Bereichsmarkierung hinzu.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6dff94a9bfeb21f09b8a8c629e10ba562d7e642b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511424"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Erstellen eines Geräteprofils in Microsoft Intune

Mit Geräteprofilen können Sie Einstellungen hinzufügen und konfigurieren und diese anschließend mithilfe von Push an Geräte in Ihrer Organisation übertragen. Im Artikel [Apply features and settings on your devices using device profiles (Anwenden von Funktionen und Einstellungen auf Ihren Geräten mithilfe von Geräteprofilen in Microsoft Intune)](device-profiles.md) ist dies ausführlicher beschrieben. Sie erfahren dort u. a. mehr über die Möglichkeiten, die Sie dabei haben.

Inhalt dieses Artikels

- Schritte zum Erstellen eines Profils
- Hinzufügen einer Bereichsmarkierung zum „Filtern“ im Profil
- Beschreibung von Anwendbarkeitsregeln auf Windows 10-Geräten und Erläuterung, wie eine Regel erstellt wird
- Check-In-Aktualisierungszykluszeiten, wenn Geräte Profile und Profilupdates erhalten

## <a name="create-the-profile"></a>Erstellen des Profils

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konfigurationsprofile** aus. Hierzu stehen Ihnen folgende Optionen zur Verfügung:

    - **Übersicht:** Hier werden die Status Ihrer Profile sowie weitere Details zu den Profilen angezeigt, die Sie Benutzern und Geräten zugewiesen haben.
    - **Verwalten:** Erstellen Sie Geräteprofile, und laden Sie benutzerdefinierte [PowerShell-Skripts](../apps/intune-management-extension.md) zur Ausführung im Profil hoch. Fügen Sie mit [eSIM](esim-device-configuration.md) Datenpläne zu Geräten hinzu.
    - **Überwachen:** Prüfen Sie den Status eines Profils, und zeigen Sie Protokolle zu Ihren Profilen an.
    - **Setup:** Fügen Sie eine Zertifizierungsstelle (SCEP oder PFX) hinzu, oder aktivieren Sie [Telecom Expense Management](telecom-expenses-monitor.md) für das Profil.

3. Wählen Sie **Profil erstellen** aus. Geben Sie die folgenden Eigenschaften ein:

   - **Name:** Geben Sie einen aussagekräftigen Namen für das Profil ein. Benennen Sie Ihre Profile, damit Sie diese später leicht wiedererkennen. Ein angemessener Profilname ist beispielsweise **WP email profile for entire company** (WP-E-Mail-Profil für das gesamte Unternehmen).
   - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
   - **Plattform**: Wählen Sie die Plattform Ihrer Geräte aus. Folgende Optionen sind verfügbar:  

       - **Android**
       - **Android Enterprise**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 und höher**
       - **Windows 10 und höher**

   - **Profiltyp**: Wählen Sie den Typ der Einstellungen aus, den Sie erstellen möchten. Die angezeigte Liste variiert je nach ausgewählter **Plattform**.
   - **Einstellungen**: Die folgenden Artikel beschreiben die Einstellungen für die einzelnen Profiltypen:

       - [Administrative Vorlagen](administrative-templates-windows.md)
       - [Benutzerdefiniert](../custom-settings-configure.md)
       - [Übermittlungsoptimierung](../delivery-optimization-windows.md)
       - [Gerätefeatures](../device-features-configure.md)
       - [Geräteeinschränkungen](device-restrictions-configure.md)
       - [Editionsupgrade und Moduswechsel](edition-upgrade-configure-windows-10.md)
       - [Bildungswesen](education-settings-configure.md)
       - [E-Mail](email-settings-configure.md)
       - [Endpoint Protection](../protect/endpoint-protection-configure.md)
       - [Identity Protection](../protect/identity-protection-configure.md)  
       - [Kiosk](kiosk-settings.md)
       - [PKCS-Zertifikat](../protect/certficates-pfx-configure.md)
       - [Importiertes PKCS-Zertifikat](../protect/certificates-imported-pfx-configure.md)
       - [Einstellungsdatei](preference-file-settings-macos.md)
       - [SCEP-Zertifikat](../protect/certificates-scep-configure.md)
       - [ Vertrauenswürdiges Zertifikat](../protect/certificates-configure.md)
       - [Updaterichtlinien](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [WLAN](wi-fi-settings-configure.md)
       - [Microsoft Defender ATP](../protect/advanced-threat-protection.md)
       - [Windows Information Protection](../protect/windows-information-protection-configure.md)

     Wenn Sie beispielsweise **iOS/iPadOS** für die Plattform auswählen, werden Ihnen Profiltypoptionen ähnlich den folgenden angezeigt:

     ![Erstellen eines iOS/iPadOS-Profils in Intune](./media/device-profile-create/create-device-profile.png)

4. Wählen Sie anschließend **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern. Das Profil wird erstellt und in der Liste angezeigt.

## <a name="scope-tags"></a>Festlegen von Tags

Nachdem Sie die Einstellungen hinzugefügt haben, können Sie dem Profil ebenfalls eine Bereichsmarkierung hinzufügen. Bereichsmarkierungen filtern Profile für bestimmte IT-Gruppen, z. B. `US-NC IT Team` oder `JohnGlenn_ITDepartment`.

Weitere Informationen zu Bereichsmarkierungen und Ihren Möglichkeiten finden Sie unter [Use role-based access control (RBAC) and scope tags for distributed IT (Verwenden der rollenbasierten Zugriffssteuerung sowie Bereichsmarkierungen für verteilte IT)](../fundamentals/scope-tags.md).

### <a name="add-a-scope-tag"></a>Hinzufügen einer Bereichsmarkierung

1. Wählen Sie **Scope (Tags)** (Bereich (Markierungen)) aus.
2. Klicken Sie auf **Hinzufügen**, um eine neue Bereichsmarkierung zu erstellen. Wählen Sie alternativ eine Bereichsmarkierung aus der Liste aus.
3. Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="applicability-rules"></a>Anwendbarkeitsregeln

Gilt für:

- Windows 10 und höher

Anwendbarkeitsregeln ermöglichen es Administratoren, Geräte in einer Gruppe als Ziel zu verwenden, die bestimmte Kriterien erfüllt. Sie können z. B. ein Geräteinschränkungsprofil erstellen, das auf die Gruppe **Alle Windows 10-Geräte** angewendet wird. Zusätzlich soll dieses Profil nur Geräten zugewiesen werden, auf denen Windows 10 Enterprise ausgeführt wird.

Hierfür erstellen Sie eine **Anwendbarkeitsregel**. Diese Regeln eignen sich hervorragend für folgende Szenarien:

- Sie verwenden Windows 10 Education (EDU). Für das Bellows College möchten Sie alle Windows 10 EDU-Geräte zwischen RS3 und RS4 einbeziehen.
- Sie möchten alle Benutzer in der Personalabteilung bei Contoso als Zielgruppe einbeziehen, aber nur Geräte unter Windows 10 Professional oder Enterprise berücksichtigen.

Gehen Sie für diese Szenarien folgendermaßen vor:

- Erstellen Sie eine Gerätegruppe, die alle Geräte im Bellows College enthält. Fügen Sie im Profil eine Anwendbarkeitsregel hinzu, die angewendet wird, wenn die Mindestversion des Betriebssystems `16299` und die Höchstversion `17134` lautet. Weisen Sie dieses Profil der Gerätegruppe im Bellows College zu.

  Nach der Zuweisung wird dieses Profil auf Geräte angewendet, deren Betriebssystemversion zwischen der von Ihnen angegebenen Mindest- und Höchstversion liegt. Bei Geräten, deren Betriebssystemversion zwischen der von Ihnen angegebenen Mindest- und Höchstversion liegt, wird der Status **Nicht zutreffend** angezeigt.

- Erstellen Sie eine Benutzergruppe, die alle Benutzer in der Personalabteilung bei Contoso umfasst. Fügen Sie im Profil eine Anwendbarkeitsregel hin, die auf Geräte unter Windows 10 Professional oder Enterprise angewendet wird. Weisen Sie dieses Profil der Benutzergruppe in der Personalabteilung zu.

  Wenn dieses Profil zugewiesen ist, wird es auf Geräte unter Windows 10 Professional oder Enterprise angewendet. Bei Geräten, auf denen diese Editionen nicht ausgeführt werden, wird der Status **Nicht zutreffend** angezeigt.

- Wenn zwei Profile mit exakt den gleichen Einstellungen vorhanden sind, wird das Profil angewendet, das keine Anwendbarkeitsregel enthält. 

  Ein Beispiel: Profil A gilt für die Windows 10-Gerätegruppe, aktiviert BitLocker und enthält keine Anwendbarkeitsregel. Profil B gilt für die gleiche Windows 10-Gerätegruppe, aktiviert BitLocker und enthält eine Anwendbarkeitsregel, mit der das Profil nur auf Geräte unter Windows 10 Enterprise angewendet wird.

  Wenn beide Profile zugewiesen sind, wird Profil A angewendet, weil es keine Anwendbarkeitsregel enthält. 

Beim Zuweisen von Profilen zu Gruppen fungieren die Anwendbarkeitsregeln als Filter, sodass nur die Geräte einbezogen werden, die Ihre Kriterien erfüllen.

### <a name="add-a-rule"></a>Hinzufügen einer Regel

1. Wählen Sie **Anwendbarkeitsregeln** aus. Sie können die **Regel**, die **Eigenschaft** und die **Betriebssystemedition** auswählen:

    ![Hinzufügen einer Anwendbarkeitsregel zu einem Gerätekonfigurationsprofil in Microsoft Intune](./media/device-profile-create/applicability-rules.png)

2. Wählen Sie unter **Regel** aus, ob Sie Benutzer oder Gruppen einschließen oder ausschließen möchten. Folgende Optionen sind verfügbar:

    - **Profil in folgenden Fällen zuweisen**: Schließt Benutzer oder Gruppen ein, die die von Ihnen angegebenen Kriterien erfüllen.
    - **Profil in folgenden Fällen nicht zuweisen**: Schließt Benutzer oder Gruppen aus, die die von Ihnen angegebenen Kriterien erfüllen.

3. Wählen Sie unter **Eigenschaft** den gewünschten Filter aus. Folgende Optionen sind verfügbar: 

    - **Betriebssystemedition**: Markieren Sie in der Liste die Windows 10-Editionen, die Sie in Ihrer Regel einschließen (bzw. ausschließen) möchten.
    - **Betriebssystemversion**: Geben Sie die **Mindestversion** und die **Höchste zulässige Version** von Windows 10 ein, die Sie in Ihrer Regel einschließen (bzw. ausschließen) möchten. Beide Werte sind erforderlich.

      Sie können z. B. `10.0.16299.0` (RS3 oder 1709) als Mindestversion und `10.0.17134.0` (RS4 oder 1803) als höchste zulässige Version eingeben. Sie können die Werte auch genauer definieren und `10.0.16299.001` als Mindestversion und `10.0.17134.319` als höchste zulässige Version eingeben.

4. Klicken Sie auf **Hinzufügen**, um die Änderungen zu speichern.

## <a name="refresh-cycle-times"></a>Aktualisierungszykluszeit

Intune verwendet verschiedene Aktualisierungszyklen zur Suche nach Updates für Konfigurationsprofile. Wenn ein Gerät vor Kurzem registriert wurde, wird der Check-In häufiger durchgeführt. Unter [Richtlinien- und Profilaktualisierungszyklen](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) werden die geschätzten Aktualisierungszeiten aufgeführt.

Benutzer können jederzeit die Unternehmensportal-App öffnen und das Gerät synchronisieren, um sofort zu prüfen, ob neue Profilupdates verfügbar sind.

## <a name="recommendations"></a>Empfehlungen

Erstellen Sie Profile unter Berücksichtigung folgender Empfehlungen:

- Benennen Sie Ihre Richtlinien, damit Sie wissen, wofür diese vorgesehen sind. Alle [Konformitätsrichtlinien](../protect/create-compliance-policy.md) und [Konfigurationsprofile](../configuration/device-profile-create.md) verfügen über eine optionale Eigenschaft namens **Beschreibung**. Sie sollten in der **Beschreibung** spezifisch sein und Informationen angeben, damit andere Benutzer wissen, wofür die Richtlinie vorgesehen ist.

  Einige Beispiele für Konfigurationsprofile sind:

  **Profilname**: Administratorvorlage – OneDrive-Konfigurationsprofil für alle Windows 10-Benutzer  
  **Profilbeschreibung**: OneDrive-Profil der Administratorvorlage, das die Mindest- und Basiseinstellungen für alle Windows 10-Benutzer enthält. Dieses wurde von user@contoso.com erstellt, um zu verhindern, dass Benutzer Organisationsdaten für persönliche Konten freigeben.

  **Profilname**: VPN-Profil für alle iOS/iPadOS-Benutzer  
  **Profilbeschreibung**: VPN-Profil, das die Mindest- und Basiseinstellungen für alle iOS/iPadOS-Benutzer enthält, um eine Verbindung mit Contoso-VPN zu erstellen. Dieses wurde von user@contoso.com erstellt, sodass Benutzer sich automatisch bei VPN authentifizieren, anstatt dass der Benutzernamen und das Kennwort der Benutzer angefordert wird.

- Erstellen Sie Ihr Profil anhand der Aufgabe, z. B. dem Konfigurieren von Microsoft Edge-Einstellungen, dem Aktivieren von Microsoft Defender-Antivireneinstellungen oder dem Blockieren von iOS/iPadOS-Geräten mit Jailbreak.

- Erstellen Sie Profile, die für bestimmte Gruppen wie Marketing, Vertrieb, IT oder Administratoren gelten, oder nach Standort oder Schulsystem.

- Trennen Sie Benutzerrichtlinien von Geräterichtlinien.

  Beispielsweise haben [Administrative Vorlagen in Intune](administrative-templates-windows.md) Hunderte von ADMX-Einstellungen. Diese Vorlagen zeigen, ob eine Einstellung für Benutzer oder Geräte gilt. Weisen Sie bei der Erstellung von Administratorvorlagen Ihre Benutzereinstellungen einer Benutzergruppe und Ihre Geräteeinstellungen einer Gerätegruppe zu.

  Die folgende Abbildung zeigt ein Beispiel einer Einstellung, die für Benutzer und/oder Geräte gelten kann:

  ![Intune-Administratorvorlage, die für Benutzer und Geräte gilt](./media/device-profile-create/setting-applies-to-user-and-device.png)

- Jedes Mal, wenn Sie eine einschränkende Richtlinie erstellen, sollten Sie diese Änderung Ihren Benutzern mitteilen. Wenn Sie z. B. die Kennungsanforderung von vier auf sechs Zeichen ändern, informieren Sie Ihre Benutzer, bevor Sie die Richtlinie zuweisen.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](../device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
