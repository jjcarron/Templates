<%*
const fileTitle = await tp.system.prompt("Nom du logiciel ?");
if (!fileTitle) {
    new Notice("Le titre du logiciel est obligatoire !");
    throw new Error("Titre manquant");
}
const licenseType = await tp.system.prompt("Type de licence ? (e.g., Open Source, Commercial, etc.)") || "Non spécifié";
const licenseExpiry = await tp.system.prompt("Échéance de la licence ? (format: YYYY-MM-DD, ou 'illimité')") || "illimité";
const setupDate = tp.date.now("YYYY-MM-DD");
const status = await tp.system.prompt("État (Installé, En cours de test, Retiré)") || "Installé";
await tp.file.move(`IT/Software/${fileTitle}`);
%>---
tags:
- 🖥️/software
license_type: <% licenseType %>
license_expiry: <% licenseExpiry %>
setup_date: <% setupDate %>
status: <% status %>

---

# 📋 Fiche Logiciel : <% fileTitle %>

## 🔑 Licences

- **Type de licence** : <% licenseType %>
- **Échéance** : <% licenseExpiry %>
- **Clé de produit** : 

---

## ⚙️ Paramètres

- **Nom d'utilisateur** :
- **Mot de passe** :
- **Clé API** :
- **Serveur** :

---

## 🛠️ Configuration

- **Version** :
- **Chemin d'installation** :
- **Dépendances requises** :

---

## 🚀 Installation

*Instructions spéciales ou commentaires particuliers*

---

## 📑 Notes et Remarques

-

---

## 🔄 Historique

| Date       | Action            | Description                       |
|------------|-------------------|-----------------------------------|
| <% setupDate %> | Installation initiale | Logiciel configuré et prêt à l'emploi. |

---
