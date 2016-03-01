# simple-cli

*--In Progress--*

The idea is to provide a more declarative approach to defining CLI applications in Node.js (as opposed to something like [Commander](https://github.com/tj/commander.js/) or [Vorpal](https://github.com/dthree/vorpal)). This library assumes you want Git-style sub-commands and is loosely inspired by [Ember's router](https://guides.emberjs.com/v1.10.0/routing/defining-your-routes/).

Features:
- Full ES6/7 Support
- Declarative API
- Command Auto Complete
- Auto-generated Abbreviated Commands
- Default and Auto-generated Help Command

## Installation

*TODO*

`npm install simple-cli`

## Usage

*TODO*

```javascript
import { Application } from 'simple-cli'
import Status from './commands/status'
import Create from './commands/Create'

// `defaultHelp` means running `outbox` on it's own will display the help dialog
const application = new Application('sonos', { defaultHelp: true })

// basic
application.command('status', Status)

// `--port` expects a value whereas `--stream` is assumed to be a boolean
application.command('data --port <port> --stream', Status)

application.command('create', { someOption: true }, function() {
  // `[name]` represents a literal that will be passed to the sub-program
  this.command('playlist [name]', Create.playlist, function() {
    // Alias `sonos mixtapes` to `sonos playlists`
    this.alias('mixtapes')
    
    // A custom help command
    this.command('help', Create.playlist.help)
  })
})

export default application

```

## API
*TODO*

### Application
*TODO*

### command
*TODO*

### alias
*TODO*

### run
*TODO*

## Contributing

*TODO*

