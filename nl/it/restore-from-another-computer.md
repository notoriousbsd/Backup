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

# Creazione di un backup e di un ripristino dei dati da una VSI a un'altra all'interno dello stesso data center

A volte potresti voler ripristinare i dati in un server diverso all'interno dello stesso data center. Questa procedura si applica solo ai ripristini a livello di file per i file non di sistema. Per ripristinare un'immagine del sistema, segui le istruzioni di [Windows BMR](restore-bmr-system-volume-image.html).

Il processo include la ri-registrazione dell'agent Backup sul secondo server per accedere all'ubicazione dell'archivio del primo server e il completamento di un **ripristino da un altro computer**.

**Prerequisiti**

- Server1 e Server2 devono avere lo stesso sistema operativo. I ripristini multipiattaforma non sono supportati.
- Server1 e Server2 devono avere gli agent Backup che erano stati configurati in precedenza. Per ulteriori informazioni sulla configurazione degli agent Backup, vedi [Configurazione dell'agent Backup in WebCC](index.html#configuring-the-backup-agent-in-webcc).
- Un lavoro di backup per Server1 che ha prodotto un backup nell'ubicazione dell'archivio del Server1.

Disabilita tutte le attività di pianificazione su entrambi i server per evitare conflitti.
{:important}

## Avvio di WebCC del Server2

Ricordati di avviare la tua connessione {{site.data.keyword.BluVPN}} per ottenere l'accesso alla rete privata {{site.data.keyword.BluSoftlayer_full}}, altrimenti il collegamento WebCC non funziona.
{:tip}

1. Accedi alla [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/catalog/){:new_window} e fai clic sull'icona **Menu** nella parte superiore sinistra. Seleziona **Infrastruttura classica**.

   In alternativa, puoi eseguire l'accesso al [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
2. Fai clic su **Storage** > **Backup** per visualizzare i server con un servizio di backup.
3. Seleziona Server2. Fai clic sulla freccia di espansione rivolta verso destra per visualizzare il collegamento WebCC.
4. Fai clic su **WebCC Login** per avviare il client WebCC nel tuo browser.

## Ri-registrazione dell'archivio

1. Fai clic su **All Agents** e apri l'agent specifico che desideri modificare.
2. Fai clic su **Edit** e seleziona **Vault Settings**.
3. Fai clic su **Reregister** per connettere Server1 a Server2.
4. Nella schermata **Re-register Vault** per la voce **Use a Vault Profile**, seleziona **Enter Vault Settings**.
5. Immetti il nome archivio (Vault Name), che è uguale al nome archivio di Server1.
6. Immetti le credenziali per Server1 per accedere all'archivio per Server1.
7. Fai clic su **Load Computers**; questa azione mostra i server collegati all'ubicazione dell'archivio.
8. Fai clic su **Save Changes**.
9. Quando ti viene richiesto, fai clic su **Yes** per confermare la ri-registrazione dell'archivio.

## Esecuzione del lavoro di backup da Server1 come lavoro di ripristino su Server2

1. Fai clic su **All Agents**.

   Potresti dover aggiornare la pagina per visualizzare i lavori definiti su Server1 come accessibili/sincronizzati nella scheda **Jobs** di Server2.
   {:tip}
2. Passa con il mouse su **Advanced** e seleziona **Restore from another Computer**.
3. Nella schermata **Restore From Another Computer**, effettua le seguenti selezioni.
  - Vault - questa voce viene impostata come valore predefinito sull'archivio di Server1
  - Computer - Seleziona Server1 come computer di backup da cui ripristinare.
  - Job - Seleziona il lavoro di backup da Server1.
4. Fai clic su **Next**
5. Conferma le informazioni relative all'origine
  - **Safeset location** è l'ubicazione dell'archivio per Server1.
  - Nella sezione **Select a Backup Version**, specifica il tuo backup da Server1 come la versione di backup.
  - La password di crittografia è la password utilizzata quando hai creato il backup di Server1.
6. Fai clic su **Next**
7. Seleziona i file che devono essere ripristinati dal backup di Server1. Seleziona le caselle accanto ai file e alle directory che vuoi ripristinare, quindi fai clic su **Include** per salvare le tue scelte.
8. Fai clic su **Next** per passare alle opzioni di ripristino.
9. In Options
  - Destination - Seleziona **Restore to original location**
  - File Overwrite - Seleziona **Overwrite existing files**
10. Fai clic su **Run Restore**.
11. La schermata Process Detail visualizza lo stato del lavoro di ripristino.


## Verifica del ripristino

1. Collegati alla root di Server2 tramite SSH.
2. Elenca i file e tutte le voci di directory in un formato esteso.
  ```
  ls -la
  ```
  {: pre}

3. Confronta l'output.

## Ripresa della normale pianificazione di Backup.

1. Al termine del ripristino, rimuovi le informazioni di registrazione del server1 da cui sono stati ripristinati i dati.
2. Immetti la registrazione del server2 corrente e abilita le attività di pianificazione.
