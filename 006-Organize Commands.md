Having 2 commands is great. But a real bot will probably have dozen of commands and more code for each command.

If we store all of them in the `app.js` file, it will be difficult to read and maintain.

To improve that, a good solution is to store each command definition and code in an individual file.
For example, having a file `ping.js` to define the command `/ping`, and a file `pong.js` to define the command `/pong`.


## Export your first command

First, we will create a `ping` command.
In `src`, create a `commands` directory and a file `ping.js` in it.

```
src/
├── commands/
|   ├── ping.js
└── app.js
```

Put the object that handles the ping command into it and prefix it with `module.exports = ` so you'll have this:
```javascript
module.exports = {
	name: 'ping',

	description: 'Replies with Pong!',

	callback: async interaction => {
		await interaction.reply('Pong!');
	}
};
```

In your `app.js`, remove the object handling the `/ping` command and replace it with `require('./commands/ping.js')`.

Tada: you have exported your commands from `app.js` to a dedicated file (`commands/ping.js`);


## Export your second command

Now, do the same with the second command, `/pong`.


## One more thing

To improve a little bit this, we will create an intermediate `index.js` file in `commands`.

This file will require all the command files like this:
```javascript
module.exports = [
  require('./ping.js'),
  require('./pong.js')
];
```

Then, in your `app.js`, simply require the `commands` directory and Node.js will find the `index.js` file automatically:

```javascript
const commands = require('./commands');
```