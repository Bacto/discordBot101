We will create a new command.

First, lets install a library we'll need to manipulate some dates.
In your Code-Hero terminal (in your bot directory), type this:
```javascript
yarn add date-fns
```


Here is a code that show the number of days between today and the next birtday celebration of somebody:
```javascript
// Import required methods from the 'date-fns' library
const {
  isAfter,
  differenceInMonths,
  differenceInDays,
  differenceInHours,
  differenceInMinutes,
  differenceInSeconds,
  addMonths,
  addDays,
  addHours,
  addMinutes
} = require('date-fns');


// Replace this with your birthday informations
const name = 'Adrien';
const birthdayDay = 20;
const birthdayMonth = 5;


const now = new Date();
const birthdayCelebrationThisYear = new Date(`${now.getFullYear()}-${birthdayMonth}-${birthdayDay}`);
const birthdayCelebrationNextYear = new Date(`${now.getFullYear() + 1}-${birthdayMonth}-${birthdayDay}`);
const birthdayCelebration = isAfter(birthdayCelebrationThisYear, now) ? birthdayCelebrationThisYear : birthdayCelebrationNextYear;


const months = differenceInMonths(birthdayCelebration, now);
const days = differenceInDays(birthdayCelebration, addMonths(now, months));
const hours = differenceInHours(birthdayCelebration, addDays(addMonths(now, months), days));
const minutes = differenceInMinutes(birthdayCelebration, addHours(addDays(addMonths(now, months), days), hours));
const seconds = differenceInSeconds(birthdayCelebration, addMinutes(addHours(addDays(addMonths(now, months), days), hours), minutes));

const sentence = `${name}'s birthday will be in ${months} months, ${days} days, ${hours} hours, ${minutes} minutes, and ${seconds} seconds.`;

// Display the sentence
console.log(sentence);
```

Create a file `example-birthday.js` on your `src` directory.
Run it with `node example-birthday.js` and see if it works.
Then update `name`, `birthdayDay` and `birthdayMonth` with your informations.
Re run it and check if it works with your informations.

FYI, this `example-birthday.js` file is just a test. This code is not related to your Discord bot, it's independant. Like a draft.


Let's transform this example in a real command.

Create a new command `/birthday`.
To do that, copy an existing command file (as a base) in `commands` directory and name it `birthday.js` (don't forget to require it in `index.js`).

Now, in the `callback` function, add the code from `example-birthday.js` to get something like that:

```javascript
// TODO: require the 'date-fns' methods here. Required modules should always be called at the top of the file.


module.exports = {
	name: '<COMMAND NAME>', // TODO: put your command name here

	description: '<DESCRIPTION TO ADD', // TODO: put your command description here

  // The "callback" is the function that will be called when the command is triggered by somebody
	callback: async interaction => {
    // TODO: add the code of `example-birthday.js` here (without the 'date-fns' require as you have defined it on top of the file)

    await interaction.reply('Pong!');
	}
};
```


Run your bot and check if it works.
Does it? No? If it replies "Pong!", that's normal.

You told it respond this with this line in the callback:
```javascript
await interaction.reply('Pong!');
```

Rather than responding "Pong!", you can tell the code to respond with a variable content.

Here is an example:

```javascript
const myVariable = 'This is my reply';
await interaction.reply(myVariable);
```

Now, your bot will reply with the content of `myVariable`, which is "This is my reply".


Did it worked? Yes? So now, your goal is to make your bot reply with the sentence defined by the birthday code.
It's your turn :)