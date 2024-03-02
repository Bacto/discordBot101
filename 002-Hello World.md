- Open a terminal in Code-Hero

- Update Node.js:
```bash
asdf nodejs update-nodebuild
asdf install nodejs `asdf nodejs resolve lts --latest-available`
asdf global nodejs `asdf nodejs resolve lts --latest-available`
```

- Create the first project:
```bash
# Create the directory "helloWorld"
mkdir helloWorld

# Enter the directory "helloWorld"
cd helloWorld

# Note: you'll see this directory on the left pane in Code-Hero :)
```

- Initiate the project:
```bash
yarn init
```

- Create the first file:
```bash
# Create the "src" directory ("src" for "sources", where the source files will be added)
mkdir src

# Tell Code-Hero to open (and create as it doesn't exist yet) the file "app.js" in the directory "src"
code src/app.js
```

- Add this code:
```javascript
console.log('Hello World!');
```

- Run your code:
```bash
node src/app.js
```


Congrats! You have run your first Node.js (JavaScript) code! 🥳