# Hardened Rust WASM GraphQL gRPC API

GraphQL API written in Rust that implements [`apollo-rs`](https://www.apollographql.com/blog/announcement/tooling/apollo-rs-graphql-tools-in-rust/), [`argon2`](https://crates.io/crates/argon2) (_Argon2id_), [`aes-keywrap-rs`](https://crates.io/crates/aes-keywrap-rs) (_RFC-5649_), and [`mongodb`](https://crates.io/crates/mongodb) over gRPC. Secured using TLS 1.3.

## Overview

This is a future-forward green fields project whose purpose is to serve as a proof of concept for a headless client-side GraphQL API that communicates with Go-based microservices over gRPC.

Languages and related technologies are being evaluated and selected based on the following criteria:

- Speed of iteration.
- Memory safety.
- Type safety.
- Concurrency.
- Economic footprint for deployments.

## 01/04/2022: Project Outline

1. Client-side
   | Technology | Implementation |
   | :-- | :-- |
   | Compiled Language | [`rust`](https://www.rust-lang.org/learn) |
   | GraphQL API | [`apollo-rs`](https://www.apollographql.com/blog/announcement/tooling/apollo-rs-graphql-tools-in-rust/) |
   | gRPC Client | [`tonic`](https://github.com/hyperium/tonic) |
   | Compile Target | [`wasm`](https://rustwasm.github.io/docs/book/) |
   | Frontend Language | [`typescript`](https://www.typescriptlang.org) |
   | Frontend Framework | [`svelte`](https://svelte.dev) |
2. Miscroservices
   | Technology | Implementation |
   | :-- | :-- |
   | Compiled Language | [`go`](https://go.dev) |
   | gRPC Server | [`grpc`](https://pkg.go.dev/google.golang.org/grpc) |
   | Password Protection | [`argon2`](https://pkg.go.dev/golang.org/x/crypto/argon2) |
   | Encryption at Rest | [`kwp`](https://pkg.go.dev/github.com/google/tink/go/subtle/kwp) |
   | Persisted Database | [`mongo`](https://pkg.go.dev/go.mongodb.org/mongo-driver/mongo) |
   | In-Memory Database | [`redis`](https://pkg.go.dev/github.com/go-redis/redis/v8) |
   | Session ID | [`uuid`](https://pkg.go.dev/github.com/google/uuid) |
   | Cookies | [`securecookie`](https://pkg.go.dev/github.com/gorilla/securecookie) |
3. Considerations

Writing the project in `C#` as a Blazor WebAssembly client-side app is appealing because of the support for cross-platform deployment beyond strictly web use cases. **Currently, development of the project will focus on the stack listed above.** However, planning and execution of the features in this project will include careful consideration of best practices with regard to implementation of `Rust` code from within `.NET 6` in the future.

### TODO List (To Be Expanded)

- Write API as implementation of `apollo-rs` in `Rust`.
- Populate resolvers with implementations of `tonic` as client.
- Build API with `wasm` as compilation target.
- Load and bind `wasm` module to `TypeScript`.
- Compile `TypeScript` deployment in `Svelte`.
- Configure `SSR` using `Sapper`.
