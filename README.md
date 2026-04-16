# 📅 Planning équipe ARTE

Planning d'équipe collaboratif avec synchronisation en temps réel via Firebase.

---

## 🚀 Mise en place (15 minutes)

### Étape 1 — Créer un projet Firebase (gratuit)

1. Allez sur **[console.firebase.google.com](https://console.firebase.google.com)**
2. Cliquez **Créer un projet**
3. Donnez-lui un nom (ex : `arte-planning`)
4. Désactivez Google Analytics (pas nécessaire) → **Créer le projet**

### Étape 2 — Activer la base de données Realtime Database

1. Dans le menu gauche : **Générer** → **Realtime Database**
2. Cliquez **Créer une base de données**
3. Choisissez la région **europe-west1 (Belgique)**
4. Sélectionnez **Démarrer en mode test** → **Activer**

> ⚠️ Le mode test expire après 30 jours. Pour le prolonger, allez dans
> **Realtime Database → Règles** et remplacez la date d'expiration par une date éloignée,
> ou utilisez ces règles permanentes :
> ```json
> {
>   "rules": {
>     ".read": true,
>     ".write": true
>   }
> }
> ```

### Étape 3 — Récupérer la configuration Firebase

1. Dans **Paramètres du projet ⚙️** (icône en haut à gauche) → onglet **Général**
2. Faites défiler jusqu'à **Vos applications**
3. Cliquez l'icône Web **`</>`** → nommez l'app (ex : `planning`) → **Enregistrer**
4. Copiez l'objet `firebaseConfig` affiché (les 7 lignes entre accolades)

### Étape 4 — Déployer sur GitHub Pages

1. Créez un compte sur **[github.com](https://github.com)** si vous n'en avez pas
2. Cliquez **New repository**
   - Nom : `arte-planning` (ou autre)
   - Visibilité : **Public** (requis pour GitHub Pages gratuit)
   - Cliquez **Create repository**
3. Sur la page du dépôt, cliquez **Add file → Upload files**
4. Glissez le fichier `index.html` et validez (**Commit changes**)
5. Allez dans **Settings → Pages** (menu gauche)
   - Source : **Deploy from a branch**
   - Branch : **main** → dossier **/ (root)**
   - Cliquez **Save**
6. Après 1-2 minutes, votre URL apparaît :
   `https://votre-pseudo.github.io/arte-planning/`

### Étape 5 — Première connexion

1. Ouvrez l'URL et collez votre configuration Firebase dans le formulaire
2. Cette configuration est mémorisée dans le navigateur — chaque collaborateur doit le faire une seule fois
3. Entrez votre prénom, choisissez votre couleur → vous êtes prêt !

---

## 👥 Utilisation

| Action | Comment |
|--------|---------|
| Ajouter une mission | Cliquer n'importe où sur la grille horaire du jour souhaité |
| Modifier une mission | Cliquer sur le bloc de la mission |
| Supprimer une mission | Ouvrir la mission → bouton **Supprimer** (uniquement vos missions) |
| Changer de semaine | Boutons `‹` `›` ou **Aujourd'hui** en haut |
| Changer de profil | Cliquer sur votre nom en haut à droite |

**Synchronisation** : toute modification est visible en temps réel sur tous les appareils connectés, sans rechargement de page.

**Couleurs** : chaque collaborateur choisit une couleur unique à sa première connexion. Les couleurs déjà prises apparaissent grisées avec l'initiale de la personne.

---

## 📱 Partager avec l'équipe

Envoyez simplement l'URL GitHub Pages à vos collègues.
Chaque personne configure Firebase une fois (coller la config), puis entre son prénom et choisit sa couleur.

---

## 🛠️ Structure technique

- **Un seul fichier HTML** — aucune dépendance à installer
- **Firebase Realtime Database** — synchronisation WebSocket en temps réel
- **localStorage** — mémorise le profil et la config Firebase sur chaque appareil
- **Mode sombre** — s'adapte automatiquement aux préférences système
