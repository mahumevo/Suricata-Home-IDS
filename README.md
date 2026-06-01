# Project: Suricata Home IDS Network Analysis

## 🛠️ Phase 1 : Préparation de l'architecture réseau
* **Mode d'accès réseau :** Passage de la machine virtuelle d'un mode NAT isolé à un mode **Accès par pont (Bridged)** afin d'intégrer la VM au réseau domestique local.
* **Mode Promiscuité (Promiscuous Mode) :** Activation du mode promiscuité sur VirtualBox (Tout autoriser) et configuration sur l'interface Ubuntu via la commande :
  `sudo ip link set enp0s3 promisc on`
* **Résultat :** L'interface réseau `enp0s3` a obtenu l'IP locale `192.168.1.70` et écoute désormais l'ensemble du trafic du réseau local.

## ⚙️ Phase 2 : Installation et Configuration de Suricata
* **Version installée :** Suricata v8.0.5 RELEASE (via le dépôt officiel OISF).
* **Fichier de configuration (`suricata.yaml`) :**
  * Définition de la variable `HOME_NET` sur la plage d'adresses locale : `"[192.168.1.0/24]"`.
  * Liaison de l'analyse réseau sur l'interface active : `enp0s3`.
* **Règles de sécurité :** Téléchargement et intégration du catalogue de signatures de menaces officielles via `suricata-update`.
* **Validation :** Test de syntaxe validé avec succès (`suricata -T`).## 🛠️ Phase 1: Network Architecture & Preparation
* **Network Access Mode:** Switched the virtual machine from an isolated NAT mode to **Bridged Adapter** mode to integrate the VM directly into the local home network.
* **Promiscuous Mode:** Enabled promiscuous mode in VirtualBox ("Allow All") and configured the Ubuntu interface using the following command:
  `sudo ip link set enp0s3 promisc on`
* **Result:** The network interface `enp0s3` successfully acquired the local IP address `192.168.1.70` and is now capturing all broadcast traffic on the local network.

## ⚙️ Phase 2: Suricata Installation & Configuration
* **Installed Version:** Suricata v8.0.5 RELEASE (via the official OISF repository).
* **Configuration File (`suricata.yaml`):**
  * Defined the `HOME_NET` variable to target the local subnet: `"[192.168.1.0/24]"`.
  * Bound the network analysis engine to the active interface: `enp0s3`.
* **Security Rules:** Downloaded and integrated the official Emerging Threats signature database using `suricata-update`.
* **Validation:** Configuration syntax test successfully passed and verified (`suricata -T`).# Projet Suricata Home IDS
## 🧪 Phase 3 : Simulation d'attaques et Analyse des Logs / Attack Simulation & Log Analysis

### Version Française :
* **Simulation :** Utilisation de l'outil `curl` pour déclencher une alerte de test standardisée via l'adresse `http://testmyids.com`.
* **Analyse du fichier de log (`fast.log`) :** Interception réussie du trafic par Suricata et génération immédiate de l'alerte de sécurité.
* **Résultat obtenu :**
  `[GPL ATTACK_RESPONSE id check returned root]` -> Preuve que l'IDS détecte efficacement les signatures de comportements suspects sur le réseau local.

### English Version:
* **Simulation:** Used the `curl` tool to trigger a standardized test alert via `http://testmyids.com`.
* **Log Analysis (`fast.log`):** Traffic was successfully intercepted by Suricata, instantly generating a security alert.
* **Triggered Alert:**
  `[GPL ATTACK_RESPONSE id check returned root]` -> Proof that the IDS is effectively detecting suspicious behavior signatures on the local network.
