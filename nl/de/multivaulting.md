---

copyright:
  years: 1994, 2018
lastupdated: "2018-12-14"

---
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Verwendung mehrerer Vaults (Multi-Vaulting)

Bei der Verwendung mehrerer Vaults (Multi-Vaulting) kann ein Client/Server eine Verbindung zu mehreren Vaultpositionen herstellen. Eine solche Umgebung bietet Redundanz und die Gewissheit, dass Ihre Sicherungen selbst dann noch verfügbar sind, wenn einer Ihrer Standorte ausfällt.

**Wesentliche Punkte**

1. Mehrere Vaults können über dieselbe WebCC verwaltet werden und werden auf dieselbe Weise behandelt. Der einzige Unterschied besteht darin, dass andere Auswahlmöglichkeiten für die Vault verfügbar sind.
2. Die Plug-in-Lizenzierung erfolgt auf Vaultbasis. Wenn Sie beispielsweise das Plug-in für MS SQL für eine Vaultinstanz in Washington DC erworben haben, kann diese Lizenz in der Vault 'Seattle' nicht verwendet werden.
3. Die neue Vault muss nach jedem Kauf manuell zu WebCC hinzugefügt werden.

**Positionen von {{site.data.keyword.backup_notm}} Vault Director**

Multi-Vaulting steht über alle Rechenzentren hinweg zur Verfügung und es gibt keine geografische Einschränkung bei der Auswahl eines fernen Vaults. Wenn Vaults anhand der Schritte in diesem Dokument konfiguriert werden, werden alle konfigurierten Vaults in den Vaulteinstellungen angezeigt.

Die Sicherung auf fernen Positionen von Rechenzentren kann mehr Zeit in Anspruch nehmen, als die Sicherung in demselben Rechenzentrum, in dem sich auch ihr Server befindet.
{:note}

## Ferne Vault zu einem Konto hinzufügen

Sie müssen den neuen fernen {{site.data.keyword.backup_notm}}-Vault zum Konto hinzufügen, bevor eine neue Sicherungsposition in WebCC hinzugefügt werden kann.

1. Melden Sie sich an der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/catalog/){:new_window} an und klicken Sie oben links auf das Symbol **Menü**. Wählen Sie **Klassische Infrastruktur** aus.

   Alternativ können Sie sich beim [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} anmelden.
2. Klicken Sie auf **Geräte**.
3. Suchen Sie den Link für den betreffenden Server und klicken Sie auf den Link.
4. Klicken Sie unter **Gerätedetails** auf **Speicher**.
5. Blättern Sie nach dem Öffnen des Abschnitts 'Speicher' bis zu **{{site.data.keyword.backup_notm}}** und klicken Sie dann auf **Hinzufügen**.
6. Wählen Sie im Fenster **{{site.data.keyword.backup_notm}} bestellen** die ferne Vaultposition aus, indem Sie in der Pulldown-Liste auf den zugehörigen Eintrag klicken.
7. Wählen Sie die Größe des Speichervolumens aus und klicken Sie auf **Weiter**.
8. Wählen Sie das Kontrollkästchen **Rahmenvereinbarung gelesen...** aus und klicken Sie auf **Bestellung aufgeben**.

Die neu bestellte Vault wird automatisch zum Konto hinzugefügt. Sollte dies nicht der Fall sein, bitten Sie den Vertrieb um Hilfe.

Nachdem Sie den Bestellprozess abgeschlossen haben, navigieren Sie zu **Speicher** > **Sicherung**, um die aufgelistete neue Vault anzuzeigen.

## Zusätzliche Vault zu WebCC hinzufügen

1. Melden Sie sich an der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/catalog/){:new_window} an und klicken Sie oben links auf das Symbol **Menü**. Wählen Sie **Klassische Infrastruktur** aus.

   Alternativ können Sie sich beim [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} anmelden.
2. Klicken Sie auf **Speicher** > **Sicherung**, um die Server mit Backup-Service anzuzeigen.
3. Wählen Sie den Server aus, für den Sicherungen mit mehreren Vaults möglich sein sollen. Klicken Sie auf den nach rechts zeigenden Pfeil, um den Link zu WebCC sichtbar zu machen.
4. Klicken Sie auf den Link **WebCC-Anmeldung**, um den WebCC-Client in Ihrem Browser zu starten.

   Auf WebCC kann nur über {{site.data.keyword.BluVPN}} zugegriffen werden.
   {:tip}
5. Klicken Sie im linken Navigationsbereich auf **Alle Agenten**.
6. Klicken Sie in der rechten oberen Ecke auf **Bearbeiten** und wählen Sie **Vaulteinstellungen** aus.
7. Klicken Sie im Fenster **Vaulteinstellungen** auf **Hinzufügen**.
8. Führen Sie im Fenster **Neue Vault** folgende Schritte aus.
  1. Wählen Sie im Menü 'Vaultprofil' die Option **Vaulteinstellungen eingeben** aus, um einen neuen Eintrag zu erstellen. Aktualisieren Sie den vorhandenen Eintrag nicht.
  2. Der Vaultname darf nicht mit dem Namen des anderen Vaults identisch sein. Es empfiehlt sich, die Kennzeichnung '-2' am Ende des Namens hinzuzufügen. <br/>

     Das Feld hat eine Begrenzung von 15 Zeichen.
     {:important}
  3. Tragen Sie in das Feld 'IP-Adresse' die Position von {{site.data.keyword.backup_notm}} Director ein. Beispiel: `ev-director301.service.softlayer.com` hat die IP-Adresse 10.1.114.46 und befindet sich in WDC.
  4. Geben Sie im Feld 'Berechtigungsnachweise' die Konto-ID, den {{site.data.keyword.backup_notm}}-Benutzernamen und das zugehörige Kennwort für den ausgewählten Vault ein.
  5. Klicken Sie auf **Änderungen speichern**.

Nach einigen Sekunden ist die neue Vault verwendbar. Falls Sie einen Verbindungsfehler empfangen, überprüfen Sie Ihre Einstellungen und wiederholen Sie die Aktion. Bedenken Sie, dass Sie beim Hinzufügen einer zusätzlichen Vault lediglich die Möglichkeit erhalten, ein zusätzliches Ziel für einen Job auszuwählen. Es werden nicht automatisch Jobs für beide Vaults ausgeführt. Sie müssen entsprechende Jobs konfigurieren, um die zusätzliche Vault nutzen zu können. Weitere Informationen finden Sie im [Lernprogramm 'Einführung'](index.html).
