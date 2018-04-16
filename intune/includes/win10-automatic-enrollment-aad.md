## <a name="enable-windows-10-automatic-enrollment"></a>Aktivieren der automatischen Registrierung von Windows 10

Durch die automatische Registrierung können Benutzer ihre Windows 10-Geräte in Intune registrieren. Benutzer müssen für die Registrierung ihr Geschäftskonto ihrem persönlichen Gerät hinzufügen oder firmeneigene Geräte mit Azure Active Directory verknüpfen. Im Hintergrund registriert sich das Gerät und tritt Azure Active Directory bei. Nach der Registrierung wird das Gerät mit Intune verwaltet.

**Voraussetzungen**
- Azure Active Directory Premium-Abonnement ([Testabonnement](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune-Abonnement


### <a name="configure-automatic-mdm-enrollment"></a>Konfigurieren der automatischen MDM-Registrierung

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an, und klicken Sie auf **Azure Active Directory**.

   ![Screenshot des Azure-Portals](../media/auto-enroll-azure-main.png)

2. Wählen Sie **Mobilität (MDM und MAM)** aus.

   ![Screenshot des Azure-Portals](../media/auto-enroll-mdm.png)

3. Wählen Sie **Microsoft Intune** aus.

   ![Screenshot des Azure-Portals](../media/auto-enroll-intune.png)

4. Konfigurieren Sie den **MDM-Benutzerbereich**. Geben Sie an, welche Geräte von Benutzern von Microsoft Intune verwaltet werden sollen. Diese Windows 10-Geräte können sich automatisch für die Verwaltung mit Microsoft Intune registrieren.

   - **Keine**: Automatische MDM-Registrierung ist deaktiviert.
   - **Einige**: Wählen Sie die **Gruppen** aus, die ihre Windows 10-Geräte automatisch registrieren können.
   - **Alle**: Alle Benutzer können ihre Windows 10-Geräte automatisch registrieren.

      > [!IMPORTANT]
      > Wenn der **MAM-Benutzerbereich** und die automatische MDM-Registrierung (**MDM-Benutzerbereich**) für eine Gruppe aktiviert sind, wird nur MAM aktiviert. Nur MAM wird für Benutzer in dieser Gruppe hinzugefügt, wenn ihr persönliches Gerät dem Arbeitsplatz beitritt. Geräte werden nicht automatisch in MDM registriert.

   ![Screenshot des Azure-Portals](../media/auto-enroll-scope.png)

5. Verwenden Sie die Standardwerte für die folgenden URLs:
    - **URL für MDM-Nutzungsbedingungen**
    - **URL für MDM-Ermittlung**
    - **MDM Compliance-URL**

6. Wählen Sie **Speichern** aus.

Standardmäßig ist die zweistufige Authentifizierung für den Dienst nicht aktiviert. Die zweistufige Authentifizierung wird jedoch empfohlen, wenn Sie ein Gerät registrieren. Für die zweistufige Authentifizierung müssen Sie einen Anbieter für die zweistufige Authentifizierung in Azure AD konfigurieren. Außerdem müssen Sie Ihre Benutzerkonten für die mehrstufige Authentifizierung konfigurieren. Weitere Informationen finden Sie unter [Erste Schritte mit Azure Multi-Factor Authentication-Server](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
