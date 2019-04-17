# Frameworks

## Web

[TODO] Rationale report

### Rust

- tide
- tower-web

**Others**: actix-web (actor model), warp

#### Websockets

- https://github.com/snapview/tungstenite-rs

### TypeScript

Avoid nodejs unless absolutely needed, and use `Deno` instead. 
(https://deno.land)

- https://github.com/zhmushan/abc

#### Websockets

- https://github.com/denoland/deno_std/tree/master/ws

## Parsing

Speech to text, and then text context and NLP requires heavy use of parser combinator frameworks.

[TODO] Rationale report.

### Use
- nom
- LALRPOP

### Others

#### Parser Combinators
- nom 
- https://github.com/Marwes/combine
- pest.rs

#### Others
- https://github.com/lalrpop/lalrpop [LR]
