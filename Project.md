<%*
const fileTitle = await tp.system.prompt("Nom du projet ?");
if (!fileTitle) {
    new Notice("Le titre du projet est obligatoire !");
    throw new Error("Titre manquant");
}

// Normaliser le titre
const normalizedTitle = fileTitle.replace(/[\s']/g, "_");

// Définir la date actuelle et une date prévisionnelle
const startDate = tp.date.now("YYYY-MM-DD");
const dueDate = tp.date.now("YYYY-MM-DD", "+7d");

// Définir le répertoire du projet et les chemins de fichier
const projectDir = `Projects/${normalizedTitle}`;
const assetsDir = `Projects/${normalizedTitle}/Assets`;
const filesDir = `Projects/${normalizedTitle}/Files`;
const projectFile = `${projectDir}/projet_${normalizedTitle}.md`;
const kanbanFile = `${projectDir}/Kanban_${normalizedTitle}.md`;

// Vérifier si le dossier existe, sinon le créer
const folderExists = await app.vault.adapter.exists(projectDir);
if (!folderExists) {
    await app.vault.createFolder(projectDir);
    await app.vault.createFolder(assetsDir);
    await app.vault.createFolder(filesDir);
}

// Renommer ou supprimer le fichier actuel (Untitled)
setTimeout(async () => {
    await tp.file.move(`${projectDir}/project_${normalizedTitle}`);
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

👉 [Kanban de <% fileTitle %>](Kanban_<% normalizedTitle %>.md)

---

## 📓 Notes supplémentaires

- Note ou détail 1
- Note ou détail 2



