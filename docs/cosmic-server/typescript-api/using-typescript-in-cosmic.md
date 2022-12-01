# Using TypeScript in Cosmic

Cosmic is written in TypeScript and we encourage you to use TypeScript in your Cosmic projects. This guide will help you get started.

## Getting Started

If you were able to get your Cosmic server up and running, you should already have everything you need to build your game in TypeScript. All game scripts are stored in the `src/scripts` directory.

Cosmic, by default recursively iterates through directories and files in the `src/scripts` directory and loads them as game scripts. This means that you can organize your scripts however you'd like.

## Learning TypeScript

[TypeScript](https://www.typescriptlang.org/) is a superset of JavaScript that adds static typing and other useful features. If you're new to TypeScript, we recommend reading the [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html) to learn the basics.

If you're already familiar with JavaScript, learning TypeScript will be a breeze. The TypeScript Handbook is a great resource for learning the differences between JavaScript and TypeScript.

## Writing Scripts

We recommend using [Visual Studio Code](https://code.visualstudio.com/) for programming in TypeScript as it has great support for the TypeScript/JavaScript ecosystem. VSCode also comes with many useful extensions and built-in features that will make your life easier, such as:

- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) - Linting
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) - Code formatting
- [Intellisense](https://code.visualstudio.com/docs/editor/intellisense) - Code completion
- ...and on and on

### Example Script

Let's start by creating a simple script that will log a message to the console when a player connects to the server.

```typescript title="src/scripts/events.ts"
Game.on("playerConnected", async (player: Types.Player) => {
  // (1)
  console.log(`Player ${player.username} connected!`); // (2)
});
```

1. The `Game.on` method is used to register an event handler. The first argument is the name of the event, and the second argument is the event handler function. Event names are typed, so you can use the `Game.on` method to discover all available events.
2. The `console.log` method is used to log a message to the console. The `console` object is a global object that is available in all scripts. Here, we print the name of the player that connected.

### Linting

Cosmic's source code is linted using [ESLint](https://eslint.org/). You can extend our configuration in the `.eslintrc.json` file in the root of your Cosmic server directory. Learn more about [configuring ESLint](https://eslint.org/docs/user-guide/configuring).
