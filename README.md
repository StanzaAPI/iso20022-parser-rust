# ISO 20022 Financial Message Parser & Validator — Rust Client Crate

[![Crates.io](https://img.shields.io/crates/v/stanzaapi-iso20022-parser.svg)](https://crates.io/crates/stanzaapi-iso20022-parser)
[![Documentation](https://docs.rs/stanzaapi-iso20022-parser/badge.svg)](https://docs.rs/stanzaapi-iso20022-parser)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> SWIFT ISO 20022 XML-to-JSON parser and compliance engine for pacs.008, camt.053, and pain.001 with sub-5ms edge latency.

Official high-performance, asynchronous Rust client library for **ISO 20022 Financial Message Parser & Validator**, built on the [Stanza Micro-API Network](https://stanzaapi.com). Uses pure Rustls TLS (zero C/OpenSSL dependencies) and Tokio for maximum concurrency and safety.

* 🌐 **Online Interactive Sandbox:** [Test your inputs live](https://stanzaapi.com/tools/iso20022-parser)
* 📚 **API Reference & Schemas:** [View documentation on Stanza](https://stanzaapi.com/tools/iso20022-parser)
* ⚡ **Platform Overview:** [Explore the Stanza Developer Network](https://stanzaapi.com)

---

## 📦 Installation

Add to your `Cargo.toml`:

```toml
[dependencies]
stanzaapi-iso20022-parser = "1.0.0"
tokio = { version = "1.0", features = ["full"] }
```

Or use `cargo add`:

```bash
cargo add stanzaapi-iso20022-parser
```

---

## 🚀 Quickstart

```rust
use stanzaapi_iso20022_parser::Iso20022ParserClient;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    // Reads STANZA_API_KEY from environment automatically
    // Public edge default: https://api.stanzaapi.com/iso20022-parser
    let client = Iso20022ParserClient::new(None, None);

    let response = client.validate("<Document xmlns=\"urn:iso:std:iso:20022:tech:xsd:pacs.008.001.08\">...</Document>").await?;

    if response.success {
        println!("Verification Success: {:?}", response.data);
    } else {
        eprintln!("Validation Error: {:?}", response.error);
    }

    Ok(())
}
```

---

## 📄 Example Response

```json
{
  "success": true,
  "data": {
    "message_type": "pacs.008.001.08",
    "settlement_amount": 150000,
    "currency": "EUR",
    "instruction_id": "INSTR-2026-0982"
  }
}
```

---

## 🔗 Useful Links

* [ISO 20022 Financial Message Parser & Validator Interactive Sandbox](https://stanzaapi.com/tools/iso20022-parser)
* [Stanza Developer Directory](https://stanzaapi.com)
* [Source Code & Issue Tracker](https://github.com/StanzaAPI/iso20022-parser-rust)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).
