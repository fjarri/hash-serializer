[![crate][crate-image]][crate-link]
[![Docs][docs-image]][docs-link]
![License][license-image]
[![Coverage][coverage-image]][coverage-link]

An implementation of [`serde::Serializer`] serializing directly into a hash digest (anything implementing [`digest::Update`]).

```rust
use digest::Digest;
use k256::ecdsa::SigningKey;
use rand_core::OsRng;
use serde::Serialize;
use sha2::Sha256;

use hashing_serializer::HashSerializer;

let sk = SigningKey::random(&mut OsRng);
let vk = sk.verifying_key();

let mut digest = Sha256::new();
let serializer = HashingSerializer { digest: &mut digest };
vk.serialize(serializer).unwrap();
```

[crate-image]: https://img.shields.io/crates/v/hash-serializer.svg
[crate-link]: https://crates.io/crates/hash-serializer
[docs-image]: https://docs.rs/hash-serializer/badge.svg
[docs-link]: https://docs.rs/hash-serializer/
[license-image]: https://img.shields.io/crates/l/hash-serializer
[coverage-image]: https://codecov.io/gh/fjarri/hash-serializer/branch/master/graph/badge.svg
[coverage-link]: https://codecov.io/gh/fjarri/hash-serializer
