<%*
const fileTitle = await tp.system.prompt("Nom de l'élément (titre du fichier) ?");
if (!fileTitle) {
    new Notice("Le titre du fichier est obligatoire !");
    throw new Error("Titre manquant");
}
const type = await tp.system.prompt("Type d'élément (PC, Router, Switch, Raspberry, phone etc.) ?") || "Non spécifié";
const location = await tp.system.prompt("Lieu d'installation (e.g., Bureau, Salon, Data Center)") || "Non spécifié";
const setupDate = tp.date.now("YYYY-MM-DD");
const status = await tp.system.prompt("État (Actif, En maintenance, Retiré)") || "Actif";

%>---
tags:
  - 🖥️/infrastructure
type: <% type %>
location: <% location %>
setup_date: <% setupDate %>
status: <% status %>
---

# 📋 Fiche Matériel : <% fileTitle %>

## 🛠️ Informations Générales
- **Type** : <% type %>
- **Lieu** : <% location %>
- **Date de mise en service** : <% setupDate %>
- **État** : <% status %>

---

## 📦 Spécifications Techniques
- **Fabricant** : 
- **Modèle** : 
- **Numéro de série** : 
- **Adresse MAC** : 
- **Adresse IP** :

---

## 🗓️ Historique et Maintenance
| Date       | Action                     | Description                        |
|------------|----------------------------|------------------------------------|
| <% setupDate %> | Installation               | Mise en service initiale.        |

---

## 📑 Notes et Remarques
- 

---

<%*
// Renommer le fichier avec le titre saisi 
// après un temps d'attente en raison des latence du réseau (125 ms semblent suffisantes)
// attedre 250 ms donne une marge raisonable 
setTimeout(async () => {tp.file.rename(fileTitle); }, 250); 
%>