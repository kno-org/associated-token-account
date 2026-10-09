# associated-token-account
The SPL Associated Token Account program and its clients

## SolK source build

The `solk-localnet-v8.0.0` branch is based on `program@v8.0.0` and uses the
Solana 3.0 modular SDK (`solana-cpi`, `solana-account-info`, etc.). It retains
upstream CPI handling and `#![forbid(unsafe_code)]`; no local ABI adapter is used.

Workspace patches resolve the ATA interface from this checkout, Token interface
2.0.0 from the sibling `kno-org/token` checkout at `token-interface`, and
Token-2022 interface 2.1.0 from the sibling `kno-org/token-2022` checkout.
The workspace Cargo.lock pins the complete dependency graph.

Build in the SolK project with `python3 scripts/build-forks.py --activate`.
Run `npm --prefix dashboard run verify:trace-ata` for canonical ATA creation,
prefunded PDA allocation/assignment, existing idempotent ATA, Token-2022 CPI,
account state and byte annotations, and finalization on four validators.
