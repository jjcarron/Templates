<%*
const fileTitle = await tp.system.prompt("Nom du projet ?");
if (!fileTitle) {
    new Notice("Le titre du projet est obligatoire !");
    throw new Error("Titre manquant");
}

// Définir la date actuelle et une date prévisionnelle
const startDate = tp.date.now("YYYY-MM-DD");
const dueDate = tp.date.now("YYYY-MM-DD", "+7d");

// Définir le répertoire du projet et les chemins de fichier
const projectDir = `Projects/${fileTitle}`;
const projectFile = `${projectDir}/projet_${fileTitle}.md`;
const kanbanFile = `${projectDir}/Kanban_${fileTitle}.md`;

// Vérifier si le dossier existe, sinon le créer
const folderExists = await app.vault.adapter.exists(projectDir);
if (!folderExists) {
    await app.vault.createFolder(projectDir);
}

// Renommer ou supprimer le fichier actuel (Untitled)
console.log(`${projectDir}/project_${fileTitle}`)
setTimeout(async () => {
    await tp.file.move(`${projectDir}/project_${fileTitle}`);
}, 0);

// Contenu pour le fichier Kanban
const kanbanContent = `---

kanban-plugin: basic
tags: 📋/kanban

---

# Kanban de ${fileTitle}

### ToDo

- [ ] Nouvelle tâche 1
- [ ] Nouvelle tâche 2

### In Progress

- [ ]

### Done

- [ ]
`;

// Écrire le fichier Kanban
await app.vault.create(kanbanFile, kanbanContent);
%>---

tags:
- 📁/projet
status: En cours
date_debut: <% startDate %>
date_fin_prevue: <% dueDate %>

---

# 🛠️ Projet <% fileTitle %>

## 🎯 Objectifs

- [ ] Décrire les objectifs du projet.

## 🗂️ Informations générales

- **Responsable** : [Nom]
- **Équipe** : [Équipe ou collaborateurs]
- **Délai estimé** : [Durée]

---

## 📋 Kanban des tâches

👉 [Kanban de <% fileTitle %>](Kanban_<% fileTitle %>.md)

---

## 📓 Notes supplémentaires

- Note ou détail 1
- Note ou détail 2



