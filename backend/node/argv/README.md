# `process.argv`

See: [How to parse command line arguments](https://nodejs.org/en/knowledge/command-line/how-to-parse-command-line-arguments/)

**Sample Code**: [Language preference](argv-example.js)

### Activity: Greetings from the command line
1. Copy this [starter code](starter/greet.js) into a new project folder.
2. Using `process.argv`, refactor the `greet` function to return the proper command line greeting based on the supplied language preference shown in the [Language preference](argv-example.js) script above. For example: typing `node greet.js es` into your terminal (assuming you're in the right directory) should return "Hola!":
    1. Navigate to the `starter` directory fromt he command line.
    2. Use `process.argv` to import a `lang` argument from the command line.
    3. Based on the `lang` value, `console.log()` the greeting in the correct language.
