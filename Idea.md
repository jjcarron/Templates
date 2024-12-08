<%*
const ideaTitle = await tp.system.prompt("Titre de l'idée ?");
if (!ideaTitle) {
    new Notice("Le titre est obligatoire !");
    throw new Error("Titre manquant");
}

const ideaContext = await tp.system.prompt("Contexte de l'idée ?") || "Non spécifié";
const ideaType = await tp.system.prompt("Type (HW, SW, Projet mécanique, etc.) ?") || "Non spécifié";
const initialTimeEstimate = await tp.system.prompt("Estimation initiale du temps nécessaire ? (e.g., 2 heures, 1 semaine)") || "Non estimé";

await tp.file.move(`Ideas/${ideaTitle}`);
%>---
tags:
- 💡/ideas
context: <% ideaContext %>
type: <% ideaType %>
time_estimate: <% initialTimeEstimate %>

---

# 💡 Idée : <% ideaTitle %>

## 🔍 Contexte
<% ideaContext %>

---

## 🛠️ Type
<% ideaType %>

---

## 🧰 Matériel nécessaire
- Élément 1
- Élément 2
- Élément 3

---

## ⏳ Estimation du temps
<% initialTimeEstimate %>

---

## 🚀 Description et notes
- Note ou détail 1
- Note ou détail 2

---

## 🔄 Étapes pour la réalisation
1. Étape 1
2. Étape 2
3. Étape 3

---

## 📋 Historique
| Date       | Action              | Description                      |
|------------|---------------------|----------------------------------|
| <% tp.date.now("YYYY-MM-DD") %> | Création initiale | Idée capturée. |

---
