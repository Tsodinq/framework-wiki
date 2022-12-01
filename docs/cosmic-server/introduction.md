# Cosmic

Cosmic is a self-hosted server for games on Framework. It is written in TypeScript and is built on the following technologies:

- [TypeScript](https://www.typescriptlang.org/) - A superset of JavaScript that adds static typing and other features.
- [Node.js](https://nodejs.org/) - A JavaScript runtime that allows you to run JavaScript outside of a browser.
- [Express](https://expressjs.com/) - A framework for building web applications in Node.js.
- [Socket.io](https://socket.io/) - A library for real-time, bidirectional, and event-based communication between the server and the client.

## Getting Started

### Prerequisites

You will need the following things installed on your computer:

- [Node.js](https://nodejs.org/)
- [Yarn](https://yarnpkg.com/)
- [Git](https://git-scm.com/)

### Installation

1. **Retrieve the source code from GitHub:**

```bash
git clone https://github.com/Tsodinq/cosmic.git
```

This'll create a new directory called `cosmic` in your current directory. You can change this by adding a path to the end of the command, like so:

```bash
git clone https://github.com/Tsodinq/cosmic.git my-project
```

2. **Install the dependencies:**

```bash
cd cosmic # or whatever you named the directory
yarn install # you will need to install yarn using npm if you don't have it already - use `npm install -g yarn`
```

3. **Configure the server:**

You'll need a Nucleus API key to enable the server to communicate with the Nucleus API. To get a key, you will need to create a Connection on Framework. You can do this [here](https://framework.soodam.rocks/game/2/edit?view=servers).

Once you've created a connection, head to **Invent -> Nucleus** and copy the corresponding API key for the connection you created ([quick link](https://framework.soodam.rocks/invent?view=nucleus)).

Now, create a file called `.env` in the root of the project and add the following line to it:

```env
NUCLEUS_KEY=your-api-key-here
```

Next, we're going to set up the database. Cosmic uses [Prisma](https://www.prisma.io/) as an ORM. Cosmic uses [PostgreSQL](https://www.postgresql.org/) as its database, so you'll need to install that as well.

Once you've installed PostgreSQL and retrieved your database credentials, paste this line into your `.env` and replace the values with your own:

```env
DATABASE_URL=postgresql://{username}:{password}@localhost:5432/cosmic
```

4. **Run the server:**

```bash
yarn build
yarn start
```

If everything went well, you should see this output:

[![terminal after running yarn start](https://cloud.soodam.rocks/index.php/s/TLJrJTJKiGXF6Km/download/Screenshot_20221130_192900.png)](https://cloud.soodam.rocks/index.php/s/TLJrJTJKiGXF6Km/download/Screenshot_20221130_192900.png)

Good job! You've successfully set up Cosmic. You should see your server listed as `Online` on your games server list.

## Tips

### Closing the server

To close the server, use the `exit` command in the integrated command prompt. This will close the server and run necessary exit tasks. If you close the server using `Ctrl+C`, problems may arise.

### Running the server in the background

You can use a tool like [PM2](https://pm2.keymetrics.io/) to run the server in the background. This is useful if you want to close your terminal and have the server continue running, and have a simple way to manage the server, such as restarting it, viewing logs, etc.

Set up Cosmic with `pm2` by running the following command:

```bash
pm2 start yarn --name "cosmic" --interpreter bash -- start
```

Cosmic should now be running in the background. You can view the logs by running `pm2 logs cosmic` and restart the server by running `pm2 restart cosmic`.
