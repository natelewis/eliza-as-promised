# eliza-as-promised

Adaptation of http://www.masswerk.at/elizabot/ to a promised based node.js module.

elizabot.js v.1.1 - ELIZA JS library (N.Landsteiner 2005) Eliza is a mock Rogerian psychotherapist. Original program by Joseph Weizenbaum in MAD-SLIP for "Project MAC" at MIT. cf: Weizenbaum, Joseph "ELIZA - A Computer Program For the Study of Natural Language Communication Between Man and Machine" in: Communications of the ACM; Volume 9 , Issue 1 (January 1966): p 36-45. JavaScript implementation by Norbert Landsteiner 2005; http://www.masserk.at

## Usage

```javascript
const Eliza = require('eliza-as-promised');

var eliza = new Eliza();

// start an Eliza conversation
console.log('>> ' + eliza.getInitial());

// tell Eliza something
let statement = 'I need some help';
console.log('<< ' + statement);

// let Eliza respond
// will respond with response.final if you're done
// will respond with response.reply if you still need more therapy
eliza.getResponse(statement)
  .then((response) => {
    if (response.reply) {
      console.log('>> ' + response.reply);
    }
    if (response.final) {
      console.log('>> ' + response.final);
      process.exit(0);
    }
  });

// repeat getResponse() over and over till response.final is defined
```
