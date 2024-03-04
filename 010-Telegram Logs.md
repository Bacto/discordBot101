# Telegram Logs

Lets integrate our previous code example in our `app.js`.

On top of `app.js`, load the Telegram library: `const TelegramBot = require('node-telegram-bot-api');`.


Just after `(async () => {`, create the Telegram bot:

```javascript
// Create a Telegram bot for logging purpose
const bot = new TelegramBot(process.env.TELEGRAM_BOT_TOKEN, { polling: true });

// Log messages received from the Telegram bot
bot.on(
  'message',
  msg => {
    const chatId = msg.chat.id;
    console.log(`Received Telegram message on chat "${chatId}": ${msg.text.toString()}`);
    bot.sendMessage(chatId, 'Received your message');
  }
);

const originalConsoleLog = console.log;
console.log = function() {
  const text = Array.from(arguments)
    .map(arg => typeof arg === 'object' ? JSON.stringify(arg) : arg)
    .join(' ');

  bot.sendMessage(process.env.TELEGRAM_CHAT_ID, text);
  originalConsoleLog(text);
};
```