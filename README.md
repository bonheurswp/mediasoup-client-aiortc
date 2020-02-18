# mediasoup-client-aiortc

[mediasoup-client](https://github.com/versatica/mediasoup-client/) handler for [aiortc](https://github.com/aiortc/aiortc/). Suitable for building Node.js applications that connect using *WebRTC* to a mediasoup server and exchange real audio, video and DataChannel messages with it in both directions.


## Requirements

This module uses **aiortc** Python library, which needs Python 3 and these [requirements](https://github.com/aiortc/aiortc#requirements) to be installed in your system.


## Installation

Once the requirements above are satisfied, install **mediasoup-client-aiortc** within your Node.js application:

```bash
$ npm install --save mediasoup-client-aiortc
```

The "postinstall" script in the `package.json` file will install the Python libraries (including **aiortc**) by using `pip3` command. If such a command is not in the `PATH` or has a different name in your system, you can override its location by setting the `PIP3` environment variable:

```bash
$ PIP3=/home/me/bin/pip npm install --save mediasoup-client-aiortc
```


## API

```javascript
// ES6 style.
import {
  createFactory,
  WorkerLogLevel
} from 'mediasoup-client-aiortc';

// CommonJS style.
const {
  createFactory,
  WorkerLogLevel
} = require('mediasoup-client-aiortc');
```

#### `createFactory(logLevel: WorkerLogLevel = 'none'): HandlerFactory`

A function that creates a mediasoup-client handler factory, suitable as [handlerFactory](https://mediasoup.org/documentation/v3/mediasoup-client/api/#Device-dictionaries) argument when instantiating a mediasoup-client [Device](https://mediasoup.org/documentation/v3/mediasoup-client/api/#mediasoupClient-Device).

```typescript
const device = new mediasoupClient.Device({
  handlerFactory : createFactory('warn')
});
```

Once you run your Node.js application, **mediasoup-client-aiortc** will spawn Python processes and communicate with them. This module assumes that there is a `python3` executable in your `PATH`. If not, you can override its location by setting the `PYTHON3` environment variable:

```bash
$ PYTHON3=/home/me/bin/python-3.7 node my_app.js
```

#### `WorkerLogLevel`

A TypeScript `type` to determine the logging verbosity of the Python component of the module.

```typescript
type WorkerLogLevel = 'debug' | 'warn' | 'error' | 'none';
```

Logs generated by both, Node.js component and Python component of this module, are printed using the mediasoup-client [debugging](https://mediasoup.org/documentation/v3/mediasoup-client/debugging/) system.


## Authors

* José Luis Millán [[github](https://github.com/jmillan/)]
* Iñaki Baz Castillo [[website](https://inakibaz.me)|[github](https://github.com/ibc/)]


## License

[ISC](./LICENSE)