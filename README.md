# CosmWasm-Examples

### Collection of templates, reusable code and examples on Rust, for deploying CosmWasm smart contracts. 

cosmwasm is a library providing all modular code needed for building a contract. And cosmwasm-template contains a starter pack to quickly set up a minimal contract along with build system and unit tests, so you can start writing custom logic directly.


Compiling
To compile all the contracts, run the following in the repo root:

```
docker run --rm -v "$(pwd)":/code \
  --mount type=volume,source="$(basename "$(pwd)")_cache",target=/code/target \
  --mount type=volume,source=registry_cache,target=/usr/local/cargo/registry \
  cosmwasm/workspace-optimizer:0.12.13
This will compile all packages in the contracts directory and output the stripped and optimized wasm code under the artifacts directory as output, along with a checksums.txt file.
```

If you hit any issues there and want to debug, you can try to run the following in each contract dir: `RUSTFLAGS="-C link-arg=-s" cargo build --release --target=wasm32-unknown-unknown --locked`
