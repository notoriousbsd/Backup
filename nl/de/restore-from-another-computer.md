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
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Sicherung erstellen und Daten von einer virtuellen Serverinstanz auf einer anderen virtuellen Serverinstanz in demselben Rechenzentrum wiederherstellen

Es kann mitunter vorkommen, dass Sie Daten auf einem anderen Server desselben Rechenzentrums wiederherstellen wollen. Die beschriebene Prozedur gilt nur für Wiederherstellungen auf Dateiebene für Dateien, die keine Betriebssystemdateien sind. Anweisungen zum Wiederherstellen eines Systemimages enthält der Abschnitt zu [Windows BMR](restore-bmr-system-volume-image.html).

Der Prozess umfasst das erneute Registrieren des Sicherungsagenten auf dem zweiten Server, um auf die Vaultposition des ersten Servers zuzugreifen, sowie das Durchführen der Aktion **Aus anderem Computer wiederherstellen**.

**Vorbedingungen**

- Server 1 und Server 2 müssen über dasselbe Betriebssystem verfügen. Plattformübergreifende Wiederherstellungen werden nicht unterstützt.
- Für Server 1 und Server 2 müssen Sicherungsagenten vorhanden sein, die zuvor konfiguriert wurden. Weitere Informationen zum Konfigurieren der Sicherungsagenten finden Sie im Abschnitt [Sicherungsagent in WebCC konfigurieren](index.html#configuring-the-backup-agent-in-webcc).
- Ein Sicherungsjob für Server 1, der eine Sicherung an der Vaultposition von Server 1 erstellt hat.

Inaktivieren Sie auf beiden Servern alle Zeitplanungstasks, um Konflikte zu vermeiden.
{:important}

## WebCC auf Server 2 starten

Denken Sie daran, Ihre {{site.data.keyword.BluVPN}}-Verbindung zu starten, damit Sie Zugang zum privaten {{site.data.keyword.BluSoftlayer_full}}-Netz erhalten, da der Link zu WebCC andernfalls nicht funktioniert.
{:tip}

1. Melden Sie sich an der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}/catalog/){:new_window} an und klicken Sie oben links auf das Symbol **Menü**. Wählen Sie **Klassische Infrastruktur** aus.

   Alternativ können Sie sich beim [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} anmelden.
2. Klicken Sie auf **Speicher** > **Sicherung**, um die Server mit Backup-Service anzuzeigen.
3. Wählen Sie Server 2 aus. Klicken Sie auf den nach rechts zeigenden Erweiterungspfeil, um den Link zu WebCC sichtbar zu machen.
4. Klicken Sie auf **WebCC-Anmeldung**, um den WebCC-Client in Ihrem Browser zu starten.

## Vault erneut registrieren

1. Klicken Sie auf **Alle Agenten** und öffnen Sie den Agenten, den Sie ändern wollen.
2. Klicken Sie auf **Bearbeiten** und wählen Sie **Vaulteinstellungen** aus.
3. Klicken Sie auf **Erneut registrieren**, um Server 1 mit Server 2 zu verbinden.
4. Wählen Sie in der Anzeige **Vault erneut registrieren** für den Eintrag **Vaultprofil verwenden** die Option **Vaulteinstellungen eingeben** aus.
5. Geben Sie den Vaultnamen ein; dieser ist mit dem Vaultnamen von Server 1 identisch.
6. Geben Sie die Berechtigungsnachweise für Server 1 ein, um sich bei der Vaultinstanz für Server 1 anzumelden.
7. Klicken Sie auf **Computer laden**. Daraufhin werden die Server angezeigt, die der Vaultposition zugeordnet sind.
8. Klicken Sie auf **Änderungen speichern**.
9. Klicken Sie bei der entsprechenden Eingabeaufforderung auf **Ja**, um die erneute Registrierung der Vaultinstanz zu bestätigen.

## Sicherungsjob aus Server 1 als Wiederherstellungsjob auf Server 2 ausführen

1. Klicken Sie auf **Alle Agenten**.

   Möglicherweise müssen Sie die Seite aktualisieren, damit die auf Server 1 definierten Jobs auf der Registerkarte **Jobs** für Server 2 als zugänglich/synchronisiert angezeigt werden.
{:tip}
2. Bewegen Sie den Mauscursor auf **Erweitert** und wählen Sie die Option **Aus anderem Computer wiederherstellen** aus.
3. Wählen Sie in der Anzeige **Aus anderem Computer wiederherstellen** die folgenden Einstellungen aus.
  - Vault - Für diesen Eintrag wird standardmäßig die Vaultinstanz von Server 1 verwendet.
  - Computer - Wählen Sie Server 1 als Sicherungscomputer für die Wiederherstellung aus.
  - Job - Wählen Sie den Sicherungsjob aus Server 1 aus.
4. Klicken Sie auf **Weiter**.
5. Bestätigen Sie die Quelleninformationen:
  - **Position der Sicherungsgruppe** ist die Vaultposition für Server 1.
  - Geben Sie im Abschnitt **Sicherungsversion auswählen** Ihre Sicherung aus Server 1 als Sicherungsversion an.
  - Das Verschlüsselungskennwort ist das Kennwort, das Sie beim Erstellen der Sicherung von Server 1 verwendet haben.
6. Klicken Sie auf **Weiter**.
7. Wählen Sie aus, welche Dateien aus der Sicherung von Server 1 wiederhergestellt werden müssen. Wählen Sie die Kontrollkästchen neben den Dateien und Verzeichnissen aus, die wiederhergestellt werden sollen, und klicken Sie anschließend auf **Einschließen**, um Ihre Auswahl zu speichern.
8. Klicken Sie auf **Weiter**, um zu den Optionen für die Wiederherstellung zu wechseln.
9. Führen Sie unter den Optionen die folgenden Schritte aus:
  - Ziel - Wählen Sie **An ursprünglicher Position wiederherstellen** aus.
  - Datei überschreiben - Wählen Sie **Vorhandene Dateien überschreiben** aus.
10. Klicken Sie auf **Wiederherstellung durchführen**.
11. In der Anzeige 'Prozessdetails' wird jetzt der Status des Wiederherstellungsjobs angezeigt.


## Wiederherstellung prüfen

1. Stellen Sie über SSH eine Verbindung zum Stammverzeichnis von Server 2 her.
2. Listen Sie die Dateien und alle Verzeichniseinträge in einem Langformat auf.
  ```
  ls -la
  ```
  {: pre}

3. Vergleichen Sie die Ausgabe.

## Normalen Sicherungszeitplan wiederaufnehmen

1. Entfernen Sie nach Abschluss der Wiederherstellung die Registrierungsinformationen von Server 1, aus dem die Daten wiederhergestellt wurden.
2. Geben Sie die aktuelle Registrierung von Server 2 ein und aktivieren Sie die Zeitplanungstasks.
