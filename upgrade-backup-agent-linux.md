---

copyright:
  years: 1994, 2018
lastupdated: "2018-12-14"

---
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Upgrading backup software agent for Linux

The most recent backup agent can be downloaded from your {{site.data.keyword.backup_notm}} portal Dashboard quick links section.
{:tip}

Following the upgrade process ensures that you can upgrade your {{site.data.keyword.backup_notm}} agent without losing the registration

1. Log in to your host at root level.
2. Download the Latest version of the agent.
   ```
   wget -N downloads.service.softlayer.com/evault/Agent-Linux-x64-8.11.5251.tar.gz2.
   ```
   {:pre}

3. Extract the contents of the downloaded file.

   ```
   tar -xzvf Agent-Linux-x64-8.11.5251.tar.gz3.
   ```
4. Go to the recent installation directory.
   ```
   cd Agent-Linux-x64-8.11.5251/4.
   ```

5. Run installation script.
   ```
   ./install.sh
   ```
   {:pre}

6. Answer the prompts by selecting `N` for not registering the computer as a new host, selecting your language, and `A` to encrypt data using the Integrated encryption method.

7. If the installation is successful, it is recorded in `/opt/BUAgent/Install.log`.
