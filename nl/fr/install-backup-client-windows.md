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

# Installation du client de sauvegarde dans Windows

L'installation du client {{site.data.keyword.backup_full}} sous Windows est réalisée via une série d'interactions sur le serveur désigné pour le service {{site.data.keyword.backup_notm}}.

Pour plus d'informations sur les sauvegardes pour les serveurs Windows 2016, voir [Configuration d'{{site.data.keyword.backup_notm}} sur Windows 2016](install-backup-client-windows2016.html).
{:tip}

## Connexion au serveur de l'unité cible

1. Connectez-vous à la [console {{site.data.keyword.cloud_notm}}](https://{DomainName}/catalog/){:new_window} et cliquez sur l'icône **Menu** dans l'angle supérieur gauche. Sélectionnez **Infrastructure classique**.

   Sinon, vous pouvez vous connecter au portail [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
2. Sélectionnez **Unités** > **Liste des unités** dans le menu principal pour afficher la liste des serveurs disponibles.
3. Recherchez l'unité pour laquelle vous avez fait l'acquisition du service {{site.data.keyword.backup_notm}} et notez son adresse IP publique.
4. Cliquez sur la flèche pointant vers la droite pour développer l'arborescence et afficher plus d'informations sur l'unité, notamment le nom d'utilisateur et le mot de passe. Si le mot de passe n'est pas affiché, cliquez sur **Afficher mot de passe** pour l'afficher.
5. Connectez-vous à l'unité cible à l'aide d'une connexion de bureau à distance.

## Téléchargement du client de sauvegarde

1. Sur le serveur cible, ouvrez une session de navigateur et entrez l'URL suivante pour télécharger le fichier exécutable du client {{site.data.keyword.backup_notm}}. <br/>
  ```
  http://downloads.service.softlayer.com/evault/
  ```
  {:pre}

2. Cliquez deux fois sur le fichier téléchargé.
3. Cliquez sur **Exécuter**.


## Installation et enregistrement de l'agent de sauvegarde

1. Entrez l'adresse réseau : <br />
  ```
  ev-webcc01.service.softlayer.com
  ```
  {: pre}

2. Entrez le nom de l'utilisateur dans la zone **Nom d'utilisateur**.
3. Entrez le mot de passe dans la zone **Mot de passe**.
6. Cliquez sur **Suivant**.
7. Cliquez sur **Installer** pour terminer l'installation.

## Configuration d'agents de sauvegarde

Connectez-vous à WebCC pour configurer et gérer vos agents de sauvegarde. Pour plus d'informations, voir le [Tutoriel d'initiation](index.html#configuring-the-backup-agent-in-webcc).
