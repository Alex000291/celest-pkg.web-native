# web-native

Native HTTP server adapter connecting `web-core` applications to Celest's standard HTTP runtime.

```text
cpm install web-native@1.0.0
```

```celest
import "web-native" as native;
native.serve(app, "127.0.0.1", 8080, 1048576);
```

`listen(app, host, port, maximumBodyBytes)` creates a native listener and returns its lifecycle object. `serve` runs the blocking accept loop. Requests are parsed from real TCP connections and responses preserve ordered duplicate headers and trailers supplied by `web-core`.

Binding, accept, parsing, body-limit, write, and shutdown failures throw native-backed errors. The listener owns its socket state and must be closed by the lifecycle contract when the caller does not use the blocking convenience entry. This package targets the native Windows and Linux runtimes; it is not available in a browser sandbox.
