# BlockNet

Minecraft: Bedrock Edition Protocol and Networking Library in Rust.

This library provides an API and framework for creating proxies, servers, or clients compatible with Mojang's Bedrock Edition protocol. Built on tokio for async networking.

## Crates

### binary

Binary encoding/decoding utilities:

- `Encode` / `Decode` traits for serialization
- `Reader` / `Writer` types for byte manipulation
- Variable-length integer support (VarInt)
- Enum encoding with configurable variant types
- Zero-copy reading with byte slices

```rust
use binary::{Encode, Decode, Writer, Reader};

impl Encode for MyPacket {
    fn encode(&self, w: &mut Writer) {
        self.id.encode(w);
        self.data.encode(w);
    }
}
```

### derive

Procedural macros for automatic packet implementation:

- `#[derive(Encode)]` - Auto-generate encoding
- `#[derive(Decode)]` - Auto-generate decoding
- `#[packet]` attribute for packet ID binding

### protocol

Complete Bedrock Edition protocol implementation:

- **Packets**: All game packets (login, play, world, etc.)
- **NBT**: Network NBT encoding/decoding
- **Types**: Game-specific data types
- **Registry**: Packet ID registration

Includes packets for:
- Login and handshake
- Player movement and actions
- World and chunk data
- Inventory and items
- Entities and actors
- Commands and chat
- And many more...

### raknet

RakNet UDP protocol layer providing TCP-like reliability:

- Connection handshake and session management
- Reliable and ordered packet delivery
- Fragmentation and reassembly
- ACK/NACK acknowledgment system

## Installation

Add to your `Cargo.toml`:

```toml
[dependencies]
binary = { path = "binary" }
derive = { path = "derive" }
protocol = { path = "protocol" }
raknet = { path = "raknet" }
```

## Building

```bash
cargo build --release
```

## Testing

```bash
cargo test
```

## License

MIT
