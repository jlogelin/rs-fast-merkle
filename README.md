# rs-fast-merkle

Rust Implementation of Streaming Merkle Root, Proof, and Verify (single leaf) from Luke Champine's paper: **Streaming Merkle Proofs within Binary Numeral Trees** @ https://eprint.iacr.org/2021/038.pdf

## Usage

```rust
use std::time::Instant;
use rs_fast_merkle::{merkle_root};

fn main() {
    let iterations = 33554432;
    let mut blkstream = Vec::with_capacity(iterations);
    for _i in 0..iterations {
        blkstream.push(Vec::from("42"));
    }

    let start = Instant::now();
    let root = merkle_root(&blkstream);
    let elapsed = start.elapsed();
    println!("Merkle root: {:?}", root);
    println!("Elapsed time: {:?}", elapsed);
}
```
