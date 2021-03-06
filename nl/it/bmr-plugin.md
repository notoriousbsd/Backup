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

# Installazione del plug-in Bare Metal Restore

BMR è una soluzione di ripristino di emergenza per Microsoft Windows. Puoi utilizzare BMR per ripristinare il server da uno stato bare metal quando si verifica un'emergenza, ad esempio quando si verifica un malfunzionamento del sistema operativo o hardware. Con BMR, puoi ripristinare rapidamente l'immagine del sistema da un'ubicazione sicura e protetta gestita da {{site.data.keyword.BluSoftlayer_full}}.

BMR è un prodotto solo per Microsoft Windows sui server fisici. Non è disponibile per i server virtuali. I ripristini bare metal per le distribuzioni Linux non sono supportati. BMR è supportato solo da agent Backup 8.30 o versioni precedenti. (30 giungo 2018).
{:important}

**Capacità fornite**

- Ripristina il tuo sistema in un momento specifico.
- Ripristina il tuo sistema da backup di immagini o file.
- Ripristina il tuo sistema dai backup che sono archiviati in IBM Cloud Backup.
- Una transazione di ripristino avviabile che puoi utilizzare per ripristinare i tuoi dati senza un sistema di avvio.
.
## Ordine del plugin

1. Accedi alla [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/catalog/){:new_window} e fai clic sull'icona **Menu** nella parte superiore sinistra. Seleziona **Infrastruttura classica**.

   In alternativa, puoi eseguire l'accesso al [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
2. Fai clic su **Storage** > **Backup** per visualizzare i server con un servizio di backup.
3. Seleziona il tuo account e fai clic su **Order plug-ins**.
4. Seleziona **{{site.data.keyword.backup_notm}} plug-in - BMR (Bare Metal Restore)** e fai clic su **Continue**.
5. Se ne hai uno, immetti il tuo codice promozionale e fai clic su **Recalculate**.
6. Vengono visualizzati i costi aggiornati. Riesamina l'ordine.
7. Seleziona la casella per indicare che hai letto e accettato gli accordi di servizio di terze parti.
8. Fai clic su **Place Order**.

## Download della guida utente

Connettiti alla rete {{site.data.keyword.BluSoftlayer_full}} con {{site.data.keyword.BluVPN}} in modo da poter accedere alla guida utente e scaricarla da [Downloadable {{site.data.keyword.backup_notm}} Documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://downloads.service.softlayer.com/evault/Documentation/){:new_window}.

## Domande Frequenti (FAQ)

**Posso passare da un singolo disco a un array RAID?**

Sì, funziona. Tuttavia, devi selezionare un dispositivo di grande capacità a causa della diminuzione delle dimensioni causata dall'array RAID.

**osa succede se l'immagine viene ripristinata su un disco più grande del volume originale?**

Se ripristini l'immagine su un disco più grande del volume originale, lo spazio restante viene deallocato. Quindi, se hai un'unità da 500-GB e ripristini i suoi dati su un disco da 1-TB, ci saranno 500 GB di spazio su disco deallocato. Con Windows 2008, puoi utilizzare il programma di utilità del disco integrato per aumentare la partizione primaria. Tuttavia, non esiste alcuna funzionalità integrata simile in Windows 2003, per cui devi assegnare lo spazio in un altro modo.

**È possibile utilizzare BMR per un backup regolare?**

Il backup BMR non è un'immagine del disco, ma un sistema di backup dell'immagine del volume di sistema. Il sistema non è destinato a essere utilizzato per backup regolari, ma insieme a essi.  

**È possibile utilizzare BMR per i backup del database?**

I backup del database devono essere eseguiti separatamente con i normali metodi di IBM Cloud Backup. BMR non sostituisce la necessità di plug-in SQL o Oracle. Sebbene BMR utilizzi la tecnologia VSS per eseguire il backup di file aperti, non può sempre garantire che i file di backup siano coerenti con le transazioni. Il consiglio per questi tipi di applicazioni specializzate è la creazione di due lavori di backup: uno per il backup del sistema operativo e dei file binari dell'applicazione e un altro per i dati dell'applicazione. È disponibile una nota al riguardo alla fine della guida utente BMR.

**Che tipo di lavori di ripristino è possibile eseguire con BMR?**

Puoi eseguire un ripristino dell'intero sistema oppure selezionare singoli file dal backup da ripristinare. Il lavoro di backup BMR può sostituire il lavoro di backup dei file corrente. Il processo di ripristino viene eseguito all'interno del sistema operativo, proprio come un lavoro di backup tradizionale.

**BMR ha capacità di backup dei file aperti?**

BMR ha capacità di backup dei file aperti. Tuttavia, BMR non sostituisce la necessità di plug-in SQL o Oracle. Per ulteriori informazioni sul plug-in MSSQL, vedi [qui](mssql-plugin.html).

**Quanto spazio su disco e tempo sono necessari per un ripristino BMR?**

Un backup effettuato da un'installazione predefinita utilizza circa 6 GB. Tale ripristino richiede circa 15 minuti su una porta da 1-GB. Questo processo è influenzato anche dalla velocità della porta privata. Se hai bisogno di backup e ripristini più veloci, potrebbe essere necessario un aumento della velocità della porta.
