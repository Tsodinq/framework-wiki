# Cosmic

Cosmic est un serveur auto-hébergé pour les jeux sur Framework. Il est écrit en TypeScript et est construit avec les technologies suivantes :

- [TypeScript](https://www.typescriptlang.org/) - Un sur-ensemble de JavaScript qui ajoute des types statiques et d'autres fonctionnalités.
- [Node.js](https://nodejs.org/) - Un runtime JavaScript qui vous permet d'exécuter du JavaScript en dehors d'un navigateur.
- [Express](https://expressjs.com/) - Un cadre pour construire des applications web dans Node.js.
- [Socket.io](https://socket.io/) - Une bibliothèque pour la communication bidirectionnelle et basée sur des événements en temps réel entre le serveur et le client.

## Démarrage

### Prérequis

Vous aurez besoin des choses suivantes installées sur votre ordinateur :

- [Node.js](https://nodejs.org/)
- [Yarn](https://yarnpkg.com/)
- [Git](https://git-scm.com/)

### Installation

1. **Récupérez le code source de GitHub :**

```bash
git clone https://github.com/Tsodinq/cosmic.git
```

Cela créera un nouveau répertoire appelé `cosmic` dans votre répertoire actuel. Vous pouvez modifier cela en ajoutant un chemin à la fin de la commande, comme suit :

```bash
git clone https://github.com/Tsodinq/cosmic.git my-project
```

2. **Installez les dépendances :**

```bash
cd cosmic # ou ce que vous avez nommé le répertoire
yarn install # vous devrez installer yarn à l'aide de npm si vous ne l'avez pas déjà - utilisez `npm install -g yarn`
```

3. **Configurez le serveur :**

Vous aurez besoin d'une clé API Nucleus pour permettre au serveur de communiquer avec l'API Nucleus. Pour obtenir une clé, vous devrez créer une connexion sur Framework. Vous pouvez le faire [ici](https://framework.soodam.rocks/game/2/edit?view=servers).

Une fois que vous avez créé une connexion, accédez à **Invent -> Nucleus** et copiez la clé API correspondante pour la connexion que vous avez créée ([lien rapide](https://framework.soodam.rocks/invent?view=nucleus)).

Maintenant, créez un fichier appelé .env à la racine du projet et ajoutez la ligne suivante à celui-ci:

```env
NUCLEUS_KEY=your-api-key-here
```

Ensuite, nous allons configurer la base de données. Cosmic utilise [Prisma](https://www.prisma.io/) en tant que ORM. Cosmic utilise [PostgreSQL](https://www.postgresql.org/) en tant que base de données, vous devrez donc également l'installer.

Une fois que vous avez installé PostgreSQL et récupéré vos informations de connexion de base de données, collez cette ligne dans votre .env et remplacez les valeurs par les vôtres:

```env
DATABASE_URL=postgresql://{username}:{password}@localhost:5432/cosmic
```

4. **Exécuter le serveur:**

```bash
yarn build
yarn start
```

Si tout s'est bien déroulé, vous devriez voir cette sortie:

[![terminal after running yarn start](https://cloud.soodam.rocks/index.php/s/TLJrJTJKiGXF6Km/download/Screenshot_20221130_192900.png)](https://cloud.soodam.rocks/index.php/s/TLJrJTJKiGXF6Km/download/Screenshot_20221130_192900.png)

Bon travail ! Vous avez correctement configuré Cosmic. Vous devriez voir votre serveur figurant en tant que "En ligne" dans votre liste de serveurs de jeux.

## Conseils

### Fermeture du serveur

Pour fermer le serveur, utilisez la commande `exit` dans la invite de commandes intégrée. Cela fermera le serveur et exécutera les tâches de sortie nécessaires. Si vous fermez le serveur en utilisant `Ctrl+C`, des problèmes peuvent survenir.

### Exécution du serveur en arrière-plan

Vous pouvez utiliser un outil tel que [PM2](https://pm2.keymetrics.io/) pour exécuter le serveur en arrière-plan. Cela est utile si vous souhaitez fermer votre terminal et laisser le serveur en cours d'exécution, et avoir une manière simple de gérer le serveur, telle que le redémarrer, afficher les journaux, etc.

Configurez Cosmic avec `pm2` en exécutant la commande suivante:

```bash
pm2 start yarn --name "cosmic" --interpreter bash -- start
```

Cosmic devrait maintenant être en cours d'exécution en arrière-plan. Vous pouvez afficher les journaux en exécutant `pm2 logs cosmic` et redémarrer le serveur en exécutant `pm2 restart cosmic`.
