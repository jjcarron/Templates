<%*
const taskTitle = await tp.system.prompt("Nom de la tâche ?");
if (!taskTitle) {
    new Notice("Le titre de la tâche est obligatoire !");
    throw new Error("Titre manquant");
}
const periodicity = await tp.system.prompt("Périodicité (e.g., Quotidienne, Hebdomadaire, Mensuelle) ?") || "Non spécifié";
const dueDate = await tp.system.prompt("Échéance (format: YYYY-MM-DD) ?") || "Sans échéance";
await tp.file.move(`Tasks/${taskTitle}`);
%>---
tags:
- 📝/tasks
periodicity: <% periodicity %>
due_date: <% dueDate %>

---

# 📋 Tâche : <% taskTitle %>

## 📝 Description

- [ ] Décrivez brièvement la tâche ici.

---

## 🛠️ Instructions

1. Étape 1
2. Étape 2
3. Étape 3

---

## 📑 Notes et Remarques

-
---

