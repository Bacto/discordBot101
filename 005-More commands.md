The code to add commands is the following. It's an "array" (because of the `[` and `]`) named `commands`:

```javascript
const commands = [];
```

In this `commands` array, we can add "objects" (because of the `{` and `}`):
```javascript
{
	name: 'ping',
	description: 'Replies with Pong!',
	callback: async interaction => {
		await interaction.reply('Pong!');
	}
}
```

This object has 3 keys: `name`, `description` and `callback`.
`name` and `description` are strings (text).
`callback` is a function that will be executed when a user use the command.

In this example, the `callback` function will run `interaction.reply('Pong!');` which means that we will reply with the text `Pong!`.

The whole code that define commands if the following: a `commands` array, containing one object:

```javascript
const commands = [
	{
		name: 'ping',
		description: 'Replies with Pong!',
		callback: async interaction => {
			await interaction.reply('Pong!');
		}
	}
];
```


To add a second command, we just need to add a second object.
This object can be the following:

```javascript
{
	name: 'pong',
	description: 'Replies with Ping!',
	callback: async interaction => {
		await interaction.reply('Ping!');
	}
}
```

Here is how to add multiple objects to an array:
```javascript
const myArray = [
	// Object 1
	{
		// Content of object 1
	},

	// Object 2
	{
		// Content of object 2
	}
];
```

Now it's your turn: add the second object representing the command `pong` to your code :)