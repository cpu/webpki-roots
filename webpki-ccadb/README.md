# webpki-ccadb
This is a crate to fetch Mozilla's root certificates for use with
[webpki-roots](https://github.com/rustls/webpki-roots) crate.

This crate is inspired by [certifi.io](https://certifi.io/en/latest/) and
uses the data provided by the [Common CA Database (CCADB)](https://www.ccadb.org/).

Local exclusions in `src/lib.rs` apply to both generated root bundles. Add an
uppercase certificate SHA-256 fingerprint to `EXCLUDED_FINGERPRINTS` to exclude
one certificate, or a lowercase SPKI SHA-256 fingerprint to
`EXCLUDED_SPKI_FINGERPRINTS` to exclude every certificate using that key. SPKI
fingerprints hash the complete DER-encoded SubjectPublicKeyInfo, including the
outer SEQUENCE. These exclusions override CCADB trust bits during regeneration.

[![webpki-ccadb](https://github.com/rustls/webpki-roots/actions/workflows/build.yml/badge.svg?branch=main)](https://github.com/rustls/webpki-roots/actions/workflows/build.yml)
[![Crate](https://img.shields.io/crates/v/webpki-ccadb.svg)](https://crates.io/crates/webpki-ccadb)
