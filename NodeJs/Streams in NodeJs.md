In Node.js, **Streams are abstract interfaces for working with streaming data**. They are objects that allow you to read data from a source or write data to a destination in chunks, rather than loading the entire data into memory at once.

Think of it like a pipeline: instead of pouring an entire bucket of water (all the data) into another bucket, you're using a hose to transfer the water bit by bit. This is especially efficient for large files or network data.

**Node.js provides four fundamental types of streams:**

1. **Readable Streams:** Abstract a source from which data can be read.
	- Examples: `fs.createReadStream()` for reading files, `http.IncomingMessage` for incoming HTTP requests, `process.stdin`.
	
2. **Writable Streams:** Abstract a destination to which data can be written.
	- Examples: `fs.createWriteStream()` for writing to files, `http.ServerResponse` for outgoing HTTP responses, `process.stdout`.

3. **Duplex Streams:** Are both Readable and Writable. They can be used for transforming data or for bidirectional communication.
	- Examples: `net.Socket` (TCP sockets), `zlib.Gzip` (for compression/decompression).

4. **Transform Streams:** A type of Duplex stream where the output is computed based on the input. Data written to the writable side is transformed and then read from the readable side.
	- Examples: `zlib.createGzip()` (to compress data), `crypto.createCipher()` (to encrypt data).


**All streams are instances of `EventEmitter`, which means they emit events (like `data`, `end`, `error`, `drain`) and allow you to listen for them.**

### Use Case

- Working with Large Files
- Handling Network I/O (HTTP Requests/Responses)
- Data Transformation and Manipulation
- Real-time Data Processing
- Performance Optimization
---
### Buffers and Streams

It's important to note the close relationship between Buffers and Streams:

- When you read data from a Readable Stream, the `data` event usually emits `Buffer` objects (or strings if an encoding is set).
- When you write data to a Writable Stream, you typically write `Buffer` objects (or strings, which are internally converted to Buffers based on the stream's encoding).

This synergy allows Node.js to efficiently handle large amounts of data by processing it in chunks (streams) of raw bytes (buffers), without needing to load everything into memory at once. This is a core concept that enables Node.js's high-performance I/O capabilities, which are essential for backend applications.

---
# Reference

[[Buffers in NodeJs]]

