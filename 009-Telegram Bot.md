# Telegram Bot

1. Connect to your Telegram account and find the user "BotFather". Talk to him and ask him to create a bot named "[DEV] Bodja". Retrieve the token.
1. In `.env`, create a new entry "TELEGRAM_BOT_TOKEN" and give it the value of the token.
1. Install the Telegram bot module: `yarn add node-telegram-bot-api`
1. Create a file `src/example-telegram.js` and put this code into it:
```javascript
require('dotenv').config();
const TelegramBot = require('node-telegram-bot-api');

// Create a bot
const bot = new TelegramBot(process.env.TELEGRAM_BOT_TOKEN, { polling: true });

bot.on(
  'message',
  msg => {
    const chatId = msg.chat.id;

    console.log(`Received Telegram message on chat "${chatId}": ${msg.text.toString()}`);

    bot.sendMessage(chatId, 'Received your message');
  }
);
```
1. Start your bot example with `node src/example-telegram.js`
1. Send a message to your Telegram bot
1. You'll see in your terminal a message like "Received Telegram message on chat XXXX". Retrieve the chat ID ("XXXX") and put it in you `.env` in `TELEGRAM_CHAT_ID`.


Congrats, you have create your first Telegram bot!

Now, speak with BotFather to create a new Telegram bot named "Bodja" and store its token to the Node.js service on Stackhero, using the environment variable "TELEGRAM_BOT_TOKEN".

Deploy you bot in production and speak with your Telegram bot. In Stackhero's console, you'll see the chat ID. Copy it and in your Node.js configuration add an environment key `TELEGRAM_CHAT_ID` with its value.

> It's not clear? I know. Ask me and I'll help you :)

Congrats, you now have 2 Telegram bots. One for the development platform and one for the production!

You can now delete the file `src/example-telegram.js`. It was just and example.