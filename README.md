# Projet de Gestion de Pages et de Blocs

Ce projet est une application full-stack permettant de gérer des pages et des blocs associés via une API backend construite avec NestJS et un frontend construit avec Next.js.

---

## **Prérequis**

Avant de commencer, assurez-vous d'avoir les outils suivants installés sur votre machine :

- [Node.js](https://nodejs.org/) (version 18 ou supérieure)
- [npm](https://www.npmjs.com/) (installé avec Node.js)
- [PostgreSQL](https://www.postgresql.org/) (version 12 ou supérieure)
- [Docker](https://www.docker.com/) (optionnel, pour exécuter PostgreSQL dans un conteneur)

---

## **Installation et Configuration**

### **1. Clonez le dépôt**

```bash
git clone <url_du_repos_git>
cd <nom_du_repertoire>
```

### **2. Backend**

1. **Accédez au dossier backend** :
   ```bash
   cd backend
   ```

2. **Installez les dépendances** :
   ```bash
   npm install
   ```

3. **Configurez les variables d'environnement** :
   Créez un fichier `.env` à la racine du dossier `backend` et ajoutez les variables suivantes :
   ```env
   DATABASE_HOST=localhost
   DATABASE_PORT=5432
   DATABASE_USERNAME=postgres
   DATABASE_PASSWORD=postgres
   DATABASE_NAME=pages_blocks_db
   BACKEND_PORT=4400
   ```

4. **Lancez la base de données PostgreSQL** :
   - Avec Docker :
     ```bash
     docker run --name postgres-db -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres -e POSTGRES_DB=pages_blocks_db -p 5432:5432 -d postgres
     ```
   - Ou configurez PostgreSQL manuellement.

5. **Exécutez les migrations (si utilisées)** :
   ```bash
   npm run typeorm migration:run
   ```

6. **Démarrez le backend** :
   ```bash
   npm run start:dev
   ```

7. **Accédez à l'API backend** :
   - L'API est accessible par défaut sur : `http://localhost:4400`
   - Les endpoints principaux :
     - `GET /blocks` : Liste des blocs
     - `POST /blocks` : Créer un bloc
     - `GET /pages` : Liste des pages
     - `POST /pages` : Créer une page

### **3. Frontend**

1. **Accédez au dossier frontend** :
   ```bash
   cd ../frontend
   ```

2. **Installez les dépendances** :
   ```bash
   npm install
   ```

3. **Configurez les variables d'environnement** :
   Créez un fichier `.env.local` à la racine du dossier `frontend` :
   ```env
   NEXT_PUBLIC_BACKEND_URL=http://localhost:4400
   ```

4. **Démarrez le frontend** :
   ```bash
   npm run dev
   ```

5. **Accédez à l'application frontend** :
   - L'application est accessible sur : `http://localhost:3000`

---

## **Fonctionnalités Principales**

### **Backend**
- CRUD complet pour les blocs (`/blocks`)
- CRUD complet pour les pages (`/pages`)
- Relations entre les blocs et les pages
- Gestion des erreurs et validation des données

### **Frontend**
- Création et modification des pages avec sélection de blocs associés
- Création et modification des blocs
- Liste des pages avec affichage des blocs associés

---

## **Tester le Projet**

### **Tests du Backend**
1. Ajoutez des données de test via le seeder (optionnel) :
   ```bash
   npm run seed
   ```

2. **Tester via Postman ou Insomnia** :
   - Importez le fichier Postman inclus dans le projet (s'il existe).

3. **Tester avec Jest** (si les tests unitaires sont configurés) :
   ```bash
   npm run test
   ```

### **Tester le Frontend**
1. **Effectuez des tests manuels** :
   - Accédez aux différentes pages et vérifiez les fonctionnalités.
   - Testez les workflows : création, modification et suppression.

2. **Tests automatiques** (si configurés) :
   ```bash
   npm run test
   ```

---

## **Bonnes pratiques et conventions**

- **Linting** : Utilisez ESLint et Prettier pour maintenir un code propre.
  ```bash
  npm run lint
  ```

- **Types** : Le projet utilise TypeScript pour un typage strict.
- **CORS** : Assurez-vous que le backend est configuré pour autoriser les appels provenant du frontend (`http://localhost:3000`).

---

## **Dépendances Clés**

### **Backend**
- [NestJS](https://nestjs.com/) : Framework backend
- [TypeORM](https://typeorm.io/) : ORM pour la gestion de la base de données
- [PostgreSQL](https://www.postgresql.org/) : Base de données relationnelle

### **Frontend**
- [Next.js](https://nextjs.org/) : Framework React
- [Axios](https://axios-http.com/) : Gestion des appels API

---

## **Auteurs et Contributions**

- Auteur : [Votre nom ou équipe]
- Contributions : Les contributions sont les bienvenues. Ouvrez une pull request ou un ticket pour discuter des améliorations possibles.

---

## **Licence**

Ce projet est sous licence [MIT](LICENSE).
