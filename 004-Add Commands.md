- In `src/app.js`, update the line where the `discord.js` library is loaded (via the `require` function. Add `REST` and `Routes` to it (in addition to `Client`, `Events` and `GatewayIntentBits`)

- Before the `client.login` command, add this code:

```javascript
	// Define the commands
	const commands = [
		{
			// Command name (for "/<NAME>")
			name: 'ping',

			// Command description that will be show when the user type "/"
			description: 'Replies with Pong!',

			// Command callback that will be executed
			callback: async interaction => {
				await interaction.reply('Pong!');
			}
		}
	];



	// Register commands to Discord
	const rest = new REST({ version: '10' }).setToken(process.env.DISCORD_TOKEN);
	console.log('Registering commands');
	await rest.put(
		Routes.applicationCommands(process.env.DISCORD_CLIENT_ID),
		{ body: commands.map(({ name, description }) => ({ name, description })) }
	);
	console.log('Commands registered');



	// Receive interactions
	client.on('interactionCreate', async interaction => {

		// Return (ignore) if it is not a command
		if (!interaction.isChatInputCommand()) return;

		// Try to fhind the command in "commands" array
		const command = commands.find(command => command.name === interaction.commandName);

		// If we haven't found the command, log, reply with an error and return
		if (!command) {
			console.log(`Unknown command received: ${interaction.commandName}`);
			await interaction.reply('Unknown command :(');
			return;
		}

		// Log the command
		console.log(`Command received by ${interaction.user.username}: ${interaction.commandName}`);

		// Execute the "callback" function corresponding to the command, and pass the "interaction" object to it
		await command.callback(interaction);
	});
```

- Restart your bot. You should see that the commands have been registered. You can then try the "/ping" command.

> It can take a few tens of seconds for the command to be available in Discord.
> Reloading the Discord page seems to update commands faster.