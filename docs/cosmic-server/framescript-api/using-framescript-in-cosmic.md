# Using Framescript in Cosmic

Framescript is a human-readable, high-level interpreted scripting language that is used to create game logic in Cosmic. Since Framescript is specifically designed for Cosmic/Framework, it may require some getting used to.

## Why Framescript?

We made Framescript because we wanted to make it easier for people to create games on Framework without having go through the long and tedious process of learning and adopting a new programming language. Framescript was designed to be easy to learn and use, but also powerful enough to create complex games.

Here's an example of what you can do with Framescript, with it's TypeScript equivalent:

=== "Framescript"
    ```
    // Broadcast a server message when a player connects
    when game.playerConnected do
      send message to list(game.players) with "A player connected!"
    end
    ```
=== "TypeScript"
    ```typescript
    // Broadcast a server message when a player connects
    Game.on("playerConnected", (player: Types.Player) => {
      game.players.forEach((player: Types.Player) => {
        player.send("A player connected!");
      });
    });
    ```

## Getting Started

Cosmic ships with a Framescript interpreter built-in, so you don't need to install anything extra to get started. All you need to do is create a Framescript (.fs) file in the `src/scripts` directory and start programming!

!!! note "Very early stage"

    Framescript is still in very early stages of development, so expect things to change, break, and be generally unstable.
    Framescript lacks many features in its current state, and we are working hard to add them as quickly as possible. We
    will be adding more documentation as we add more features.