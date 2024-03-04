For now your bot runs on your local machine (kind of, in fact it runs on a server from Stackhero but it is like it runs on your development platform).

It is great to develop but you should also have a "production" platform where your final bot runs.


## Create a production server and configure it

1. Start a Node.js service on Stackhero
1. Once started, click on the "Configure" button
1. You should put your SSH public key in the "SSH public keys"/"Key" field.
  1. Get your SSH public key by executing this command in Code-Hero terminal: `cat ~/.ssh/id_rsa.pub `
  1. Copy the SSH public key
  1. Paste in on Stackhero dashboard
  1. Click on "Validate" button
1. On you Node.js service first page, there is a field "Git remote command" (something like "git remote add stackhero ssh://..."). Copy its value and paste it in your Code-Hero terminal **while you are in your bot project directory**.


## Prepare your bots

You'll have 2 bots. One for development and one for production.

Your current bot is now officially the development one.
1. Rename it to show that this is a development one. Something like "[DEV] Bodja" of "Bodja - dev". It's your choice but we should see clearly that this a development bot.
1. In your bot Discord configuration, there is an option to make it public or not. Uncheck it, so a stranger will not be able to speak with it.
1. Create a new bot called "Bodja". This is your production bot.
1. Copy the token from your production bot and the "Client ID".
1. Set the token and client ID on your Node.js service, in Stackhero
  1. Select your Node.js service, click on "Configure", go to "Environment variables"
  1. Click on "Add a variable"
  1. In "Name", set "DISCORD_TOKEN". In value, set the token
  1. Click on "Add a variable"
  1. In "Name", set "DISCORD_CLIENT_ID". In value, set the client id
  1. Validate the configuration
1. Invite your production bot to Adrien's server


## Deploy your bot to production

You know have 2 bots, one called "Bodja" for production and one called "[DEV] Bodja".
Both are present on Adrien's server.

On your develoment platform (Code-Hero), you have a `.env` file containing the token and client ID of your development bot.

On Stackhero, you have a Node.js service for your production bot.
In its configuration, there is the token and client ID of your production bot.


Now, you have to deploy your code from your development platform (Code-Hero) to your production platform (service Node.js on Stackhero).


To do that, in Code-Hero, push your code to GitHub if you haven't did it yet.
Then, in the terminal, type this to deploy to production: `git push stackhero main`.
You should see your code being deployed to the production server.

Once done, send a command on Discord to your production bot.

TADA, you now have a development platform, a production platform, 2 bots and a clean way to deploy from development to production!

> Remember, each time you want to deploy your code to production, you have to first push to GitHub and then execute `git push stackhero main`.