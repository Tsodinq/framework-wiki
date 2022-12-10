# Utiliser TypeScript dans Cosmic

Cosmic est écrit en TypeScript et nous vous encourageons à utiliser TypeScript dans vos projets Cosmic. Ce guide vous aidera à vous lancer.

## Commencer

Si vous avez réussi à mettre en marche votre serveur Cosmic, vous devriez déjà avoir tout ce dont vous avez besoin pour construire votre jeu en TypeScript. Tous les scripts de jeu sont stockés dans le répertoire `src/scripts`.

Cosmic, par défaut, parcourt récursivement les répertoires et les fichiers dans le répertoire `src/scripts` et les charge en tant que scripts de jeu. Cela signifie que vous pouvez organiser vos scripts comme vous le souhaitez.

## Apprendre TypeScript

[TypeScript](https://www.typescriptlang.org/) est un sur-ensemble de JavaScript qui ajoute un typage statique et d'autres fonctionnalités utiles. Si vous êtes nouveau sur TypeScript, nous vous recommandons de lire le [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html) pour en apprendre les bases.

Si vous êtes déjà familier avec JavaScript, apprendre TypeScript sera un jeu d'enfant. Le TypeScript Handbook est une excellente ressource pour apprendre les différences entre JavaScript et TypeScript.

## Écrire des scripts

Nous vous recommandons d'utiliser [Visual Studio Code](https://code.visualstudio.com/) pour programmer en TypeScript car il offre un excellent support pour l'écosystème TypeScript/JavaScript. VSCode dispose également de nombreuses extensions utiles et de fonctionnalités intégrées qui faciliteront votre vie, telles que :

- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) - Linting
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) - Formatage de code
- [Intellisense](https://code.visualstudio.com/docs/editor/intellisense) - Complétion de code
- ...et ainsi de suite

### Exemple de script

Commençons par créer un script simple qui affichera un message dans la console lorsqu'un joueur se connecte au serveur.

```typescript title="src/scripts/events.ts"
Game.on("playerConnected", async (player: Types.Player) => {
  // (1)
  console.log(`Player ${player.username} connected!`); // (2)
});
```

1. La méthode Game.on est utilisée pour enregistrer un gestionnaire d'événements. Le premier
2. La méthode `console.log` est utilisée pour afficher un message dans la console. L'objet `console` est un objet global qui est disponible dans tous les scripts. Ici, nous imprimons le nom du joueur qui s'est connecté.

### Linting

Le code source de Cosmic est linté en utilisant [ESLint](https://eslint.org/). Vous pouvez étendre notre configuration dans le fichier `.eslintrc.json` à la racine de votre répertoire de serveur Cosmic. Apprenez-en plus sur la [configuration de ESLint](https://eslint.org/docs/user-guide/configuring).
