- Ensure you are in the "projects" directory. If you need to go to the parent directory (for example if you are in `projects/helloWorld`), you can use `cd ..`

- Create a directory named with your bot name. Here it is `myBot`:
  ```bash
  mkdir myBot
  cd myBot
  ```

- Initiate the project and add dependencies (`discord.js` and `dotenv`):
  ```bash
  yarn init
  yarn add discord.js dotenv
  ```

- Create the project on GitHub (with the same name as your bot name) and copy/paste the git commands to initiate the Git repository

- Add some files to the Git ignore list, to avoid to push them to GitHub:
  ```bash
  echo ".env" >> .gitignore
  echo "node_modules" >> .gitignore
  ```


- Create the bot on Discord at https://discord.com/developers/applications
Once created, click on "Bot", then "Reset Token" and copy the new token generated.

- Store the token: open the `.env` file and add the token like this:
  ```
  DISCORD_TOKEN=<YOUR_TOKEN>
  ```

- Create the first code example:
  ```bash
  mkdir src
  code src/app.js
  ```

- Add this code:
  ```javacript
  // Load the ".env" file and put its content to "process.env".
  // To access "DISCORD_TOKEN", you'll have to use "process.env.DISCORD_TOKEN".
  require('dotenv').config()

  // Load "discord.js" library
  const { Client, Events, GatewayIntentBits } = require('discord.js');


  // Create a new client
  const client = new Client({ intents: [GatewayIntentBits.Guilds] });

  client.once(Events.ClientReady, readyClient => {
    console.log(`Ready! Logged in as ${readyClient.user.tag}`);
  });

  // Log in to Discord with your client's token
  client.login(process.env.DISCORD_TOKEN);
  ```

- Finally, start the bot: `node src/app.js`

Congrats, you have your first bot running! 🥳