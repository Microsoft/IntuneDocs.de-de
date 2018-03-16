---
title: "Registrieren von Geräten mithilfe des Windows AutoPilot Deployment-Programms"
titleSuffix: Microsoft Intune
description: "Erfahren Sie, wie Sie Windows 10-Geräte mithilfe des Windows AutoPilot Deployment-Programms registrieren."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: dfdc712f3cf1b9ce928574ee9e9078c80bd696bb
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="enroll-windows-devices-by-using-the-windows-autopilot-deployment-program"></a>Registrieren von Windows-Geräten mithilfe des Windows AutoPilot Deployment-Programms
Das Windows AutoPilot Deployment-Programm vereinfacht die Bereitstellung von Geräten. Das Erstellen und Warten von benutzerdefinierten Images des Betriebssystems ist ein langwieriger Prozess. Es kann ebenfalls Zeit in Anspruch nehmen, diese benutzerdefinierten Images von Betriebssystemen auf neue Geräte anzuwenden, um diese für die Verwendung vorzubereiten, bevor Sie sie Ihren Benutzern zur Verfügung stellen. Mit Microsoft Intune und AutoPilot können Sie Ihren Benutzern neue Geräte geben, ohne die benutzerdefinierten Images des Betriebssystems auf den Geräten erstellen, verwalten und auf diese anwenden zu müssen. Wenn Sie Intune zum Verwalten von AutoPilot-Geräten verwenden, können Sie z.B. Richtlinien, Profile und Apps auf den Geräten verwalten, nachdem diese registriert sind. Eine Übersicht über die Vorteile, Szenarios und Voraussetzungen finden Sie unter [Overview of Windows AutoPilot (Übersicht über Windows AutoPilot)](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

## <a name="prerequisites"></a>Voraussetzungen
- [Die Geräte müssen für Ihre Organisation registriert sein](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot#device-registration-and-oobe-customization).
- [Die automatische Windows-Registrierung muss aktiviert sein](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment).
- [Azure Active Directory Premium-Abonnement](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="synchronize-devices"></a>Synchronisieren von Geräten
Synchronisieren Sie Ihre registrierten Geräte in Intune, sodass Sie diese konfigurieren können.

1. Melden Sie sich bei [Azure](https://portal.azure.com/) an.
2. Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3. Wählen Sie auf dem Blatt **Intune** die Option **Geräteregistrierung** aus.
4. Klicken Sie auf dem Blatt **Windows-Registrierung** im Abschnitt **Windows AutoPilot Deployment-Programm** auf **Geräte**.
5. Klicken Sie auf **Sync** (Synchronisieren), um Ihre registrierten Geräte zu importieren. Eine Meldung zeigt an, dass die Synchronisierung ausgeführt wird.
6. Aktualisieren Sie die Ansicht, um neue Geräte anzuzeigen. Der Prozess kann ein paar Minuten in Anspruch nehmen, je nachdem, wie viele Geräte synchronisiert werden.  

## <a name="create-an-autopilot-deployment-profile"></a>Erstellen eines AutoPilot-Bereitstellungsprofils
AutoPilot-Bereitstellungsprofile werden verwendet, um die AutoPilot-Geräte zu konfigurieren.
1. Melden Sie sich bei [Azure](https://portal.azure.com/) an. 
2. Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3. Wählen Sie auf dem Blatt **Intune** die Option **Geräteregistrierung** aus.
4. Klicken Sie unter **Windows-Registrierung** im Abschnitt **Windows AutoPilot Deployment-Programm** auf **Geräte**.
5. Klicken Sie auf **Profil erstellen**, und wählen Sie einen Namen und optional eine Beschreibung. 
6. Wählen Sie **In Azure AD eingebunden** für **Join type** (Jointyp) aus.
7. Konfigurieren Sie für die **Out-of-Box-Experience (OOBE)** folgende Optionen, und klicken Sie dann auf **OK**: 
   - **Datenschutzeinstellungen**: Wählen Sie aus, ob die Datenschutzeinstellungen den Benutzern angezeigt werden. 
   - **Lizenzbedingungen**: Wählen Sie, ob die Lizenzbedingungen den Benutzern angezeigt werden sollen.
   - **Benutzerkontotyp**: Wählen Sie, ob der Kontotyp des Benutzers **Administrator** oder **Standardbenutzer** sein soll.

     > [!Note]    
     > Diese Einstellung gilt nicht für Konten von globalen Administratoren oder Unternehmensadministratoren. Diese Konten gelten nicht als Konten von Standardbenutzern, da Sie Zugriff auf sämtliche Verwaltungsfunktionen in Azure AD haben.
8. Klicken Sie auf **Erstellen**, um das Profil zu erstellen. Das AutoPilot-Bereitstellungsprofil ist nun verfügbar und kann Geräten zugewiesen werden.
     
> [!Note]    
> Folgende Einstellungen werden für alle AutoPilot-Bereitstellungsprofile konfiguriert:
> - Skip Cortana, OneDrive und OEM-Setupseiten für die Registrierung
> - Automatisches Einrichten für die Arbeit oder Schule
> - Anmelden mit einer Unternehmens- oder Schulmarke    

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Warnungen für nicht zugewiesene Windows AutoPilot-Geräte <!-- 163236 -->
Sie können eine Warnung für nicht zugewiesene Windows AutoPilot-Geräte anzeigen, um zu sehen, wie vielen Geräten aus dem AutoPilot-Programm keine AutoPilot-Bereitstellungsprofile zugewiesen sind. Verwenden Sie die Informationen aus der Warnung, um Profile zu erstellen und sie den nicht zugeordneten Geräten zuzuweisen. Wenn Sie auf die Warnung klicken, sehen Sie die vollständige Liste der Windows AutoPilot-Geräte zusammen mit detaillierten Informationen. 
1. Melden Sie sich bei [Azure](https://portal.azure.com/) an. 
2. Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3. Wählen Sie auf dem Blatt **Intune** die Option **Geräteregistrierung** aus.
4. Um die Warnung anzuzeigen, wählen Sie **Übersicht** aus. Klicken Sie auf die Warnung, um eine Liste der AutoPilot-Geräte anzuzeigen.  

## <a name="assign-an-autopilot-deployment-profile"></a>Zuweisen eines AutoPilot-Bereitstellungsprofils
Nachdem Sie AutoPilot-Bereitstellungsprofile erstellt haben, können Sie diese ausgewählten Diensten zuweisen.

1. Melden Sie sich bei [Azure](https://portal.azure.com/) an. 
2. Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3. Wählen Sie auf dem Blatt **Intune** die Option **Geräteregistrierung** aus.
4. Klicken Sie auf dem Blatt **Windows-Registrierung** im Abschnitt **Windows AutoPilot Deployment-Programm** auf **Geräte**.
5. Wählen Sie die Geräte aus, denen Sie das Bereitstellungsprofil zuweisen möchten. Sie können diese in der Spalte **Status** filtern, um Geräte ohne zugewiesenes Profil einfach zu finden. 
6. Klicken Sie auf **Profil zuweisen**, wählen Sie das AutoPilot-Bereitstellungsprofil aus, und klicken Sie dann auf **Zuweisen**. Eine Meldung zeigt an, dass die Zuweisung ausgeführt wird.
7. Aktualisieren Sie die Ansicht, um festzustellen, ob das Profil den Geräten zugewiesen wurde. Der Prozess kann ein paar Minuten in Anspruch nehmen, je nachdem, wie viele Geräte Sie ausgewählt haben. 

> [!Note]
> Das neue Profil wird dem Gerät zugewiesen. Nachdem das Gerät zurückgesetzt und erneut registriert wurde, wird das Profil wird auf Geräte, die bereits in Intune registriert wurden, angewendet.

### <a name="assign-a-different-autopilot-deployment-profile"></a>Zuweisen eines anderen AutoPilot-Bereitstellungsprofils
Wenn Sie einem Gerät ein AutoPilot-Bereitstellungsprofil zugewiesen haben und ein anderes Profil zuweisen möchten, weisen Sie dem Gerät das neue Profil zu.  

## <a name="edit-an-autopilot-deployment-profile"></a>Bearbeiten eines AutoPilot-Bereitstellungsprofils 
Nachdem Sie ein AutoPilot-Bereitstellungsprofil erstellt haben, können Sie bestimmte Teile des Bereitstellungsprofils bearbeiten.   
1. Melden Sie sich bei [Azure](https://portal.azure.com/) an. 
2. Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3. Wählen Sie auf dem Blatt **Intune** die Option **Geräteregistrierung** aus.
4. Klicken Sie unter **Windows-Registrierung** im Abschnitt **Windows AutoPilot Deployment-Programm** auf **Geräte**. 
5. Wählen Sie das Profil aus, das Sie bearbeiten möchten. 
6. Klicken Sie auf der linken Seite auf **Eigenschaften**, um den Namen oder die Beschreibung des Bereitstellungsprofils zu ändern. Klicken Sie auf **Speichern**, wenn Sie Änderungen vorgenommen haben. 
7. Klicken Sie auf **Einstellungen**, um Änderungen an den OOBE-Einstellungen vorzunehmen. Klicken Sie auf **Speichern**, wenn Sie Änderungen vorgenommen haben. 

> [!NOTE]
> Das aktualisierte Profil ist dem Gerät zugewiesen. Das aktualisierte Profil wird jedoch nicht auf ein Gerät angewendet, das bereits bei Intune registriert ist, bis das Gerät zurückgesetzt und erneut registriert wurde. 

## <a name="using-autopilot-in-other-portals"></a>Verwenden von AutoPilot in anderen Portalen
Wenn die mobile Geräteverwaltung für Sie nicht von Interesse ist, können Sie AutoPilot beispielsweise in Microsoft Store für Unternehmen verwenden. Die Verwendung von anderen Portalen ist ebenfalls möglich, es wird jedoch empfohlen, ausschließlich Intune zum Verwalten Ihrer AutoPilot-Bereitstellungen zu verwenden. Wenn Sie Intune und ein anderes Portal verwenden, kann Intune folgende Funktionen nicht verwenden:
- Anzeigen von Änderungen an Profilen, die in Intune erstellt, aber in einem anderen Portal bearbeitet wurden
- Synchronisieren von Profilen, die in einem anderen Portal erstellt wurden
- Anzeigen von Profilzuweisungen, die in einem anderen Portal vorgenommen wurden
- Synchronisieren von Profilzuweisungen, die in einem anderen Portal vorgenommen wurden
- Anzeigen von Änderungen an der Geräteliste, die in einem anderen Portal vorgenommen wurden

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie Windows AutoPilot für registrierte Windows 10-Geräte konfiguriert haben, erfahren Sie mehr über die Verwaltung dieser Geräte. Weitere Informationen finden Sie unter [Was ist die Microsoft Intune-Geräteverwaltung?](https://docs.microsoft.com/intune/device-management).