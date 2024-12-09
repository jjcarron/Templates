<%*
const fileTitle = await tp.system.prompt("Nom de l'élément réseau ?");
if (!fileTitle) {
    new Notice("Le titre de l'élément réseau est obligatoire !");
    throw new Error("Titre manquant");
}

const deviceType = await tp.system.prompt("Type de dispositif réseau (e.g., Switch, Router, Firewall) ?") || "Non spécifié";
const ipAddress = await tp.system.prompt("Adresse IP (e.g., 192.168.1.1) ?") || "Non spécifiée";
const location = await tp.system.prompt("Lieu (e.g., Salle serveur, Datacenter) ?") || "Non spécifié";
const setupDate = tp.date.now("YYYY-MM-DD");
const status = await tp.system.prompt("État (e.g., Actif, En maintenance, Retiré) ?") || "Actif";

await tp.file.move(`IT/Network/${fileTitle}`);
%>---
tags:
- 🌐/network
type: <% deviceType %>
ip_address: <% ipAddress %>
location: <% location %>
setup_date: <% setupDate %>
status: <% status %>

---

# 🌐 Équipement Réseau : <% fileTitle %>

## 🛠️ Informations Générales

- **Type** : <% deviceType %>
- **Adresse IP** : <% ipAddress %>
- **Lieu** : <% location %>
- **Date de mise en service** : <% setupDate %>
- **État** : <% status %>

---

## 🔌 Configuration Réseau

- **Adresse MAC** : 
- **Passerelle** : 
- **Masque de sous-réseau** : 
- **Ports ouverts** :
  - Port 1 : 
  - Port 2 : 
- **Protocole** : 

---

## ⚙️ Paramètres Avancés

- **VLAN** : 
- **QoS (Quality of Service)** : 
- **Paramètres de sécurité** : 
  - **Firewall** : Activé/Désactivé
  - **Règles spécifiques** :

---

## 📑 Notes et Remarques

- 

---

## 🔄 Historique et Maintenance

| Date       | Action                     | Description                        |
|------------|----------------------------|------------------------------------|
| <% setupDate %> | Mise en service            | Équipement installé et configuré. |

---
