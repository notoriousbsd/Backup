---

copyright:
  years: 1994, 2018
lastupdated: "2018-12-14"

---
{:pre: .pre}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Plug-in für Oracle installieren

Beim Plug-in für Oracle handelt es sich um ein Add-on, das mit dem Windows-Agenten oder dem Linux-Agenten auf dem Oracle-Datenbankhost installiert wird. Mit dem WebCC-Portal können Sie Jobs konfigurieren, Oracle-Datenbanken in einer sicheren, fernen Vault sichern und Oracle-Datenbanken wiederherstellen. Das Plug-in für Oracle wird in die vorhandene Architektur integriert.

**Bereitgestelltes Leistungsspektrum**

- Unterstützung für die Sicherung und Wiederherstellung von Oracle-Datenbanken.
- Das Plug-in für Oracle stellt auf ARCHIVELOG basierende Sicherungen ohne Recovery Manager (RMAN) von vollständigen Online-Datenbankinstanzen bereit. Alle nicht temporären Tabellenbereiche und Instanzparameterdateien werden automatisch gesichert. Die Oracle Corporation empfiehlt, Sicherungen in Zeiten mit geringer Datenbankaktivität auszuführen.
- Datenbanken werden mit den üblichen vom Benutzer verwalteten Oracle-Wiederherstellungsmechanismen ganz und teilweise wiederhergestellt.

**Einschränkungen**
- Es werden nur einzelne Instanzen von lokalen, datenträgerbasierten Datenbanken gesichert.
- Datenbankcluster werden nicht gesichert.
- Roheinheiten werden nicht gesichert.
- Ferne Datenbanken werden nicht gesichert.
- Die Datenbank muss sich im Modus ARCHIVELOG befinden und der Benutzer, unter dem die Sicherung konfiguriert ist, muss die Berechtigung SYSDBA besitzen.
- Datenbankkennwörter werden zur verstärkten Sicherheit über scriptbasierte Methoden verschlüsselt.

## Plug-in bestellen

1. Melden Sie sich an der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/catalog/){:new_window} an und klicken Sie oben links auf das Symbol **Menü**. Wählen Sie **Klassische Infrastruktur** aus.

   Alternativ können Sie sich beim [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} anmelden.
2. Klicken Sie auf **Speicher** > **Sicherung**, um die Server mit Backup-Service anzuzeigen.
3. Wählen Sie Ihr Konto aus und klicken Sie auf **Plug-ins bestellen**.
4. Wählen Sie **{{site.data.keyword.backup_notm}}-Plug-in - Oracle** aus und klicken Sie auf **Weiter**.
5. Geben Sie einen gegebenenfalls verfügbaren Werbeaktionscode ein und klicken Sie auf **Neu berechnen**.
6. Die aktualisierten Gebühren werden angezeigt. Prüfen Sie Ihre Bestellung.
7. Aktivieren Sie das Kontrollkästchen, um anzugeben, dass Sie die Servicevereinbarung eines anderen Anbieters gelesen haben und akzeptieren.
8. Klicken Sie auf **Bestellung aufgeben**.

## Oracle-Plug-in für Windows installieren

Das Oracle-Plug-in für Windows wird mit dem 32-Bit- oder 64-Bit-Windows-Agenten installiert. Zur Installation des Oracle-Plug-ins für Windows führen Sie das Agenteninstallationskit aus. Das Oracle-Plug-in wird auf der Seite **Angepasste Installation** als Option angezeigt.

Bevor Sie das Plug-in für Ihren Microsoft Windows-Server installieren, stoppen Sie beide {{site.data.keyword.backup_notm}}-Services in `services.msc`.
{:tip}

1. Navigieren Sie zum Ordner `c:\installs\evault` und führen Sie die Datei '.exe' mit der höchsten Überarbeitungsnummer aus.
2. Klicken Sie in der Anzeige für die Sprache auf **OK**.
3. Klicken Sie in der Eingangsanzeige auf **Weiter**.
4. Wählen Sie die Option **Installation ändern** aus und klicken Sie auf **Weiter**.
5. Wählen Sie die Option **Unverändert beibehalten** aus und klicken Sie auf **Weiter**.
6. Wählen Sie in der Anzeige für die angepasste Installation jedes von Ihnen erworbene Plug-in und dann die Option **Feature wird installiert auf ...** aus. Klicken Sie anschließend auf **Weiter**.
7. Wählen Sie **Aktuelle Registrierung beibehalten** aus und klicken Sie auf **Weiter**.
8. Klicken Sie auf **Installieren**.
9. Stellen Sie nach Abschluss der Installation sicher, dass beide Services aktiviert und in Betrieb sind.
10. Falls WebCC in der Lage ist, auf die Datenbank zuzugreifen bzw. die Datenbank anzuzeigen, war die Installation erfolgreich.

## Oracle-Plug-in für UNIX installieren

Beim Plug-in für Oracle handelt es sich um ein Add-on für den Linux-Agenten, das mit dem Agenten auf dem Datenbankhost installiert wird. Die Linux-Agentenanwendung muss vor der Installation des Oracle-Plug-ins installiert werden. Der Linux-Agent ist als 32-Bit-Anwendung und als 64-Bit-Anwendung verfügbar. Weitere Informationen zur Installation des Linux-Agenten finden Sie unter [{{site.data.keyword.backup_notm}}-Client unter Linux installieren](install-backup-client-linux.html).

Das Installationskit für das Oracle-Plug-in steht in einer 'tar.gz'-Datei zur Verfügung.

1. Laden Sie auf dem Host das Installationspaket herunter.
   ```
   http://downloads.softlayer.com/evault/Oracle-Plugin-Linux-x64-8.10.5249.tar.gz
   ```
   {: pre}

2. Extrahieren Sie die Dateien aus dem Paket.
   ```
   # cd /tmp
   # tar xvf Oracle-Plugin-Linux-x64-8.10.5249.tar
   ```
   {: pre}

3. Rufen Sie den Ordner auf.
   ```
   # cd Oracle-Plugin-Linux-x64-8.10.5249.xxxx
   ```
   {: pre}

4. Führen Sie das Installationsscript aus.
   ```
   # ./install.sh
   ```
   {: pre}

5. Gehen Sie den angezeigten Anweisungen entsprechend vor.

Das Oracle-Plug-in führt eine "inkonsistente" Datenbankgesamtsicherung durch, die es erforderlich macht, dass die Datenbank im Modus ARCHIVELOG ausgeführt wird. Der Datenbankadministrator muss sicherstellen, dass sich die Datenbank im Modus ARCHIVELOG befindet, bevor die Sicherungen gestartet werden. Weitere Informationen finden Sie im Benutzerhandbuch.
{:important}


## Benutzerhandbuch herunterladen

Stellen Sie mit {{site.data.keyword.BluVPN}} eine Verbindung zum {{site.data.keyword.BluSoftlayer_full}}-Netz her, damit Sie die Benutzerhandbücher über [Für den Download verfügbare {{site.data.keyword.backup_notm}}-Dokumentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://downloads.service.softlayer.com/evault/Documentation/){:new_window} herunterladen können.
