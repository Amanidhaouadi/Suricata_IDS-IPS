# Suricata IDS/IPS 

   Ce projet présente la mise en place et l'exploitation de **Suricata**, un système de détection et de prévention d'intrusions (IDS/IPS), dans un environnement CentOS 8.


# Suricata IDS – Partie 1 : Installation, Configuration et Tests

##  Objectifs
- Installer et configurer Suricata en mode IDS.
- Tester la détection de trafic malveillant via des règles personnalisées et existantes.
- Analyser un fichier PCAP pour identifier des attaques de phishing.

## Étapes principales

### 1. Installation et configuration de Suricata
- Ajout des dépôts OISF et installation des dépendances.
- Configuration des variables réseau (`HOME_NET`, `EXTERNAL_NET`).
- Désactivation de l'offloading (LRO/GRO) pour une capture fiable.
- Mise à jour des règles avec `suricata-update`.

### 2. Test des règles existantes
- Vérification du chargement des règles (plus de 61 000 règles).
- Génération d'alerte via un User-Agent suspect (`BlackSun`).
- Détection d'une attaque SYN Flood avec `hping3`.

### 3. Création de règles personnalisées
- Ajout d'une règle pour détecter les pings ICMP.
- Création d'une règle pour identifier les tentatives de phishing PayPal via DNS.

### 4. Analyse de PCAP et rejeu de trafic
- Téléchargement et analyse d'un fichier `phishingattack.pcap` avec Wireshark.
- Rejeu du trafic avec `tcpreplay` et validation des alertes Suricata.

## Commandes clés
```bash
sudo suricata -c /etc/suricata/suricata.yaml -v -i enp0s3
sudo suricata-update
sudo tail -f /var/log/suricata/fast.log
```

## Fichiers de configuration modifiés
- `/etc/suricata/suricata.yaml`
- `/etc/sysconfig/suricata`
- `/var/lib/suricata/rules/custom.rules`

## Résultats
- Suricata fonctionne en mode IDS avec des règles personnalisées et tierces.
- Détection réussie d'attaques : User-Agent suspect, SYN Flood, phishing DNS, et ICMP.


-------------------------------------------------------------------------------------------------------------------



# Suricata IPS – Partie 2 : Installation, Configuration et Tests












