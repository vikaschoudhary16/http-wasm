# http-wasm-abi

[http-wasm][1] is HTTP server middleware implemented in [WebAssembly][1]. This
repository contains the Abstract Binary Interface (ABI), that defines how
hosts and guests can communicate compatability.

## Application Binary Interface (ABI)

The HTTP middleware ABI is currently being defined. Follow this repository for
updates.

### Common notes

- Parameters of type `string` expand to two parameters of type `i32`, the
  first being the pointer to the contents of the string and the second being 
  the number of bytes. *Note* that for unicode strings, the number of bytes is
  larger than the number of characters.

### Host ABI

The [host ABI](./http-host.md) defines the functions that the host makes
available to middleware. Frameworks adding support for http-wasm middleware
must export the functions defined in the ABI to guest Wasm binaries for them
to function.

### Guest ABI

The guest must to minimally export its memory as "memory".

[1]: https://github.com/http-wasm
[2]: https://webassembly.org/
