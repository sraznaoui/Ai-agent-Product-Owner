# Ai-agent-Product-Owner

🤖 Assistant IA pour Product Owner

🧭 Présentation Générale

Ce projet a été réalisé dans le cadre d’un test technique visant à créer un assistant intelligent pour les Product Owners d’une plateforme SaaS de gestion de projet. L’agent IA automatise plusieurs tâches clés :

✍️ Rédaction de User Stories, Critères d’acceptation, et estimation de la Complexité

🚦 Priorisation des éléments du backlog selon les méthodes MoSCoW et RICE

📬 Analyse automatique des feedbacks et catégorisation des mails reçus

Le tout est orchestré via des scénarios n8n, avec une interface 100 % pilotée via Airtable.

🛠️ Architecture

🧩 Outils Utilisés

n8n – Moteur d’automatisation

Airtable – Interface utilisateur & base de données

OpenAI API – Génération & interprétation de texte (LLM agent)

Gmail – Entrée via trigger de boîte mail

🔗 Interfaces Airtable

Onglet Brief – Lance la génération des user stories à partir du brief client

Onglet Projet – Lance la priorisation des fonctionnalités du backlog

Table Feedback – Centralise les feedbacks analysés par l’agent IA

Formulaire externe – Permet aux utilisateurs de soumettre des demandes manuellement

⚙️ Workflows

1. ✍️ Agent IA – Rédaction Assistée

Déclencheur : Script manuel depuis l’onglet “Brief” d’Airtable

Fonctionnalités :

Génère des User Stories avec Titre, Description, Critères d’acceptation

Fournit une estimation de complexité (T-Shirt Sizing : XS à XL)

Lie automatiquement chaque user story à son projet dans Airtable

Génère une Vision Produit concise et mobilisatrice

📌 Lien Airtable à insérer ici → [Lien vers Airtable - Vue Brief]

📸 [INSÉRER IMAGE : capture du workflow et du rendu Airtable]

2. 🚦 Agent IA – Priorisation

Déclencheur : Action manuelle depuis l’onglet “Projet”

Fonctionnement :

Récupère les éléments du backlog liés à un projet

Applique MoSCoW + estimation partielle RICE (Reach et Impact seulement)

Laisse Confidence et Effort au soin du PO ou de l’équipe technique

Explique la logique de priorisation et met à jour Airtable

📌 Lien Airtable à insérer ici → [Lien vers Airtable - Vue Priorisation]

📸 [INSÉRER IMAGE : logiques de priorisation ou sortie]

3. 📬 Agent IA – Feedback

Déclencheur : Boîte Gmail + formulaire Airtable optionnel

Fonctionnalités :

Analyse automatique des mails toutes les heures

Détecte si le message est un Bug, une Feature Request, ou un Feedback

Extrait les informations importantes : nom, prénom, projet, email, explication

Filtre les spams et contenus hors-sujet grâce à un prompt strict

Alimente la table "Feedbacks" dans Airtable

📌 Lien Airtable à insérer ici → [Lien vers Airtable - Feedback]

📸 [INSÉRER IMAGE : feedback analysé dans Airtable]

🧪 Comment Tester l’Agent

🧾 Créer un brief projet dans Airtable > lancer le workflow de rédaction

📊 Accéder au projet correspondant > lancer la priorisation

📩 Envoyer un mail à la boîte Gmail liée et vérifier le traitement

🧠 (Optionnel) Soumettre une demande via le formulaire Airtable

📚 Notes Techniques

Le modèle RICE est partiellement automatisé (R + I uniquement)

La Vision Produit est générée selon un template inspiré des meilleures pratiques produit (ex. Marty Cagan)

Le lien projet/story est assuré par un identifiant de projet (recordId)

📎 Améliorations Possibles



📩 Auteur

Réalisé par Saad – Ingénieur orienté produit, passionné de No-Code et d’IA 🧠⚡️

🚀 N'hésitez pas à cloner, améliorer ou me contacter sur LinkedIn !

