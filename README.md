CBOR.js
=======

The Concise Binary Object Representation (CBOR) data format ([RFC 7049](http://tools.ietf.org/html/rfc7049)) implemented in pure JavaScript (ES Module).

API
---

The `CBOR`-object provides the following two functions:

CBOR.**decode**(*data*)
> Take the ArrayBuffer object *data* and return it decoded as a JavaScript object.

CBOR.**encode**(*data*)
> Take the JavaScript object *data* and return it encoded as a ArrayBuffer object.

Usage
-----

Include `CBOR.js` in your or HTML page:
```js
import { CBOR } from "https://code4fukui.github.io/CBOR/CBOR.js";

const initial = { Hello: "World" };
const encoded = CBOR.encode(initial);
const decoded = CBOR.decode(encoded);
```
After running this example `initial` and `decoded` represent the same value.

### Combination with WebSocket

The API was designed to play well with the `WebSocket` object in the browser:
```javascript
const websocket = new WebSocket(url);
websocket.binaryType = "arraybuffer";
...
websocket.onmessage = (event) => {
  const message = CBOR.decode(event.data);
};
...
websocket.send(CBOR.encode(message));
```
