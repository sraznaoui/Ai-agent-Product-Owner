# 🤖 AI-Agent Product Owner

## 🧭 Présentation Générale

Ce projet est un **agent intelligent** conçu pour assister les Product Owners d’une plateforme SaaS de gestion de projet.  
🎯 Objectif : décharger le PO des tâches répétitives et lui offrir une **supervision augmentée** de son backlog.

### Fonctions principales :
- ✍️ **Génération de User Stories** (titre, description, critères d’acceptation, complexité)
- 🚦 **Priorisation du backlog** via **MoSCoW** et **RICE**
- 📬 **Analyse automatique des feedbacks** et classification en `Bug`, `Feature Request`, ou `Feedback`

🧠 Propulsé par **n8n**, **OpenAI API**, et **Airtable** en guise d’interface utilisateur.

---

## 🛠️ Architecture & Stack

### 🧩 Stack Technique

- `n8n` : moteur d’orchestration no-code
- `Airtable` : interface de saisie + base de données collaborative  
  🔗 [Accès à la base (lecture seule)](https://airtable.com/appdbdWixyLMElhAH/shrX1YU7wWhg9DkuJ)
- `OpenAI API` : génération de texte & analyse sémantique
- `Gmail` : source de feedbacks clients (mail scraping)

> ⚠️ **Note** : en raison des limitations Airtable, un accès complet nécessite une invitation au workspace. Me contacter pour y accéder.

---

## ⚙️ Workflows IA

### 1. ✍️ Génération assistée de User Stories

📍 Déclenchement : depuis l’onglet **Brief** dans Airtable  
📌 [Accès lecture seule](https://airtable.com/appdbdWixyLMElhAH/shr61nuyOpT0LW8ZC?Bm7FO=recC7u336r20vEihL)

**Fonctionnalités :**
- Génération automatique (titre, description, critères)
- Complexité estimée (XS → XL)
- Liée automatiquement au projet concerné
- Formulation d’une **vision produit** claire et mobilisatrice

📸 Exemple de processus :

![Assisted Writing Trigger](https://github.com/user-attachments/assets/fd6a2fe1-d05b-4008-bf6e-9d75818330ce)

![Script Airtable](https://github.com/user-attachments/assets/4f085b61-994a-4968-804e-c2c53bdc1340)

![n8n Workflow](https://github.com/user-attachments/assets/75fa5f9f-c864-49ff-ad5c-37e658506ac0)

📬 À la fin du process, le PO reçoit une confirmation par mail :  
![Mail Confirmation](https://github.com/user-attachments/assets/6522dc03-4008-4202-b76b-cb618d3aef0d)

🧾 Résultat en base Airtable :  
![Résultat 1](https://github.com/user-attachments/assets/c3ab484f-f372-4e3b-9554-4d5027464b3e)  
![Résultat 2](https://github.com/user-attachments/assets/7b9f9659-1aa6-4ec5-93f0-fbb9bbcf85ad)

> 💡 Astuce UX : un champ "🧠 IA" + un champ "✅ Validé PO" permettent de distinguer ce qui a été généré automatiquement de ce qui a été revu.

---

### 2. 🚦 Priorisation intelligente du backlog

📍 Déclenchement : clic dans l’onglet **Projet**  
📌 [Interface Airtable](https://airtable.com/appdbdWixyLMElhAH/shrruPyt9kQdQP9rm)

**Fonctionnalités :**
- Lecture automatique du backlog
- Application stricte de la méthode **MoSCoW**
- Calcul du **Reach** & **Impact** pour RICE  
- Attribution de priorité justifiée et expliquée

> ⚠️ Seules les valeurs **C** (Confiance) & **E** (Effort) de RICE restent à compléter manuellement par le PO

📸 Aperçus :

![Déclenchement Projet](https://github.com/user-attachments/assets/fa9f90ae-773a-456f-bbe2-0565b75145ab)  
![Script Airtable](https://github.com/user-attachments/assets/3ba90254-8f43-498f-a358-8ca8610d4deb)  
![Workflow n8n](https://github.com/user-attachments/assets/801aa64f-9906-46e0-a507-6f3d3106b8a0)

---

### 3. 📬 Analyse automatisée des feedbacks

📍 Déclencheurs :
- Emails reçus via Gmail
- Formulaire client
- Saisie manuelle par le PO

📌 Trois méthodes de collecte :
1. **Formulaire client**  
   ![Formulaire client](https://github.com/user-attachments/assets/15172bb9-c7e5-4da8-8327-6311052db3a9)  
   ![Interface](https://github.com/user-attachments/assets/75447c5a-53b3-4501-a75b-c82f29ea2abb)

2. **Feedback direct par PO**

3. **Scraping d'emails entrants via Gmail + IA**  
   ![Email Parsing](https://github.com/user-attachments/assets/215949c4-ea52-46ff-a454-91ba213f36e8)

**Fonctionnalités :**
- Classification sémantique : `Bug`, `Feature Request`, `Feedback`, `Hors Sujet`
- Extraction automatique des infos clés (contact, projet, contenu)
- Ajout dans la table Feedbacks

---

## 🧪 Guide de Test

1. 🧾 Ajouter un **brief client** dans Airtable  
2. ✍️ Lancer le **processus de génération** dans l’onglet Brief  
3. 🚦 Lancer la **priorisation** dans l’onglet Projet  
4. 📩 Envoyer un email ou remplir un formulaire pour tester l’analyse feedback  
5. 🌐 (Optionnel) Tester le **formulaire client public**

---

## 📚 Détails Techniques

- 🔢 RICE : `Reach` et `Impact` sont automatisés. `Confidence` & `Effort` sont manuels.
- 🧭 Vision Produit :  
  > *Notre produit [type de solution] aide [utilisateur] à [transformation], en leur fournissant [valeurs clés]. Contrairement à [alternative], notre produit permet [bénéfice différenciant].*
- 🔒 Gestion sécurisée via `recordId` pour relier les entités
- 🔐 Accès restreint à Airtable : me contacter avec votre email pour une invitation

---

## 🧠 Pistes d’Amélioration

- [ ] Refonte UI/UX pour un parcours plus fluide
- [ ] Déplacement des déclencheurs IA hors d’Airtable (limites UI)
- [ ] Réponse automatique par mail post-priorisation
- [ ] Système de log d’historique IA par projet
- [ ] Utiliser LangChain & Langrahp pour exploiter les agents swarms & Base de données vectorielles.

---

## 👤 Auteur

Développé par **Saad**  
Ingénieur efficacité énergétique & Product Builder IA / No-Code 🚀

📬 Envie de contribuer, forker ou juste discuter ?  
N’hésite pas à me ping !

---

> *"Build once. Scale endlessly."*
