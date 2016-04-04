# azure-logging #

Azure logging module


## reader(options) ##

```
var reader = require('azure-logging').reader;
```

Creates a log reader. Options are:

```js
{
    app: null,        // app filter
    format: 'text',    // output format (text | html | json)
    skip: 0, // number of lines to skip
    top: 10, // number of lines to fetch (limit)
    level: 'warn', // maximum level ('log' < 'info' < 'warn' < 'error')
    farm: null, // farm filter (e.g. 'anodejs')
    instance: null, // instance filter (e.g. 'anodejsrole_IN_0')
    since: null, // time query (find `top` entries since `since`. `null` means now).
    message: null, // regex query on message (very slow, will not work probably)
}
```

The log reader is an `EventEmitter` with the following events:

 * __'line'__ - `function(line, entry)` emitted on each log line.
 * __'error'__ - `function(err)` emitted if there was an error.
 * __'end'__ - `function()` emitted at the end of the log stream.
