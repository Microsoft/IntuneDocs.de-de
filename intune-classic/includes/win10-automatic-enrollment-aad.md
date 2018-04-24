## <a name="enable-windows-10-automatic-enrollment"></a>Aktivieren der automatischen Registrierung von Windows 10

Mit der Funktion der automatischen Registrierung können Benutzer ihre Windows 10-Geräte bei Intune registrieren, wenn sie ihr Arbeitskonto auf Geräten hinzufügen, die ihnen privat gehören, oder wenn sie ihre unternehmenseigenen Geräte in Ihr Azure Active Directory einbinden. Im Hintergrund registriert sich das Gerät des Benutzers und tritt Azure Active Directory bei. Nach der Registrierung wird das Gerät mit Intune verwaltet.

**Voraussetzungen**
- Azure Active Directory Premium-Abonnement ([Testabonnement](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune-Abonnement


### <a name="configure-automatic-mdm-enrollment"></a>Konfigurieren der automatischen MDM-Registrierung

1. Melden Sie sich beim [Azure-Verwaltungsportal ](https://portal.azure.com) an (https://manage.windowsazure.com)), und klicken Sie auf **Azure Active Directory**.

   ![Screenshot des Azure-Portals](../media/auto-enroll-azure-main.png)

2. Wählen Sie **Mobilität (MDM und MAM)** aus.

   ![Screenshot des Azure-Portals](../media/auto-enroll-mdm.png)

3. Wählen Sie **Microsoft Intune** aus.

   ![Screenshot des Azure-Portals](../media/auto-enroll-intune.png)

4. Konfigurieren Sie den **MDM-Benutzerbereich**. Geben Sie an, welche Geräte von Benutzern von Microsoft Intune verwaltet werden sollen. Die Windows 10-Geräte dieser Benutzer werden automatisch für die Verwaltung mit Microsoft Intune registriert.

   - **Keine**
   - **Einige**
   - **Alle**

   ![Screenshot des Azure-Portals](../media/auto-enroll-scope.png)

5. Verwenden Sie die Standardwerte für die folgenden URLs:
   - **URL für MDM-Nutzungsbedingungen**
   - **URL für MDM-Ermittlung**
   - **MDM Compliance-URL**

6. Wählen Sie **Speichern** aus.

Standardmäßig ist die zweistufige Authentifizierung für den Dienst nicht aktiviert. Die zweistufige Authentifizierung wird jedoch empfohlen, wenn Sie ein Gerät registrieren. Bevor die zweistufige Authentifizierung für diesen Dienst erforderlich ist, müssen Sie einen Anbieter für die zweistufige Authentifizierung in Azure Active Directory und Ihre Benutzerkonten konfigurieren. Weitere Informationen finden Sie unter [Erste Schritte mit Azure Multi-Factor Authentication-Server](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
