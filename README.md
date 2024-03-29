# demo-rust-sqlite

https://github.com/diesel-rs/diesel

https://diesel.rs/guides/getting-started

## DIESEL

A safe, extensible ORM and Query Builder for Rust, supported databases:

- PostgreSQL
- MySQL
- SQLite

https://github.com/gluesql/gluesql

https://github.com/gluesql/gluesql-js

https://github.com/spacejam/sled

https://github.com/sqlparser-rs/sqlparser-rs

## sqlparser-rs example

To parse a simple `SELECT` statement:

```rust
use sqlparser::dialect::GenericDialect;
use sqlparser::parser::Parser;

let sql = "SELECT a, b, 123, myfunc(b) \
           FROM table_1 \
           WHERE a > b AND b < 100 \
           ORDER BY a DESC, b";

let dialect = GenericDialect {}; // or AnsiDialect, or your own dialect ...

let ast = Parser::parse_sql(&dialect, sql).unwrap();

println!("AST: {:?}", ast);
```

This outputs

```rust
AST: [Query(Query { ctes: [], body: Select(Select { distinct: false, projection: [UnnamedExpr(Identifier("a")), UnnamedExpr(Identifier("b")), UnnamedExpr(Value(Long(123))), UnnamedExpr(Function(Function { name: ObjectName(["myfunc"]), args: [Identifier("b")], over: None, distinct: false }))], from: [TableWithJoins { relation: Table { name: ObjectName(["table_1"]), alias: None, args: [], with_hints: [] }, joins: [] }], selection: Some(BinaryOp { left: BinaryOp { left: Identifier("a"), op: Gt, right: Identifier("b") }, op: And, right: BinaryOp { left: Identifier("b"), op: Lt, right: Value(Long(100)) } }), group_by: [], having: None }), order_by: [OrderByExpr { expr: Identifier("a"), asc: Some(false) }, OrderByExpr { expr: Identifier("b"), asc: None }], limit: None, offset: None, fetch: None })]
```

## wapm sqlite

https://www.sqlite.org/download.html 可以下载类似 sqlite-wasm-3420000.zip 

https://www.youtube.com/watch?v=KIpyg7uBz1Q

https://webassembly.sh/?run-command=sqlite

https://wapm.io/sqlite/sqlite

https://github.com/wapm-packages/sqlite

https://github.com/wasienv/wasienv

https://docs.wasmer.io/ecosystem/wasienv/compile-c-c++-to-wasm-wasi

https://www.sqlitetutorial.net/sqlite-commands

wasmer --version

export http_proxy=http://127.0.0.1:1087;export https_proxy=http://127.0.0.1:1087;

wasmer self-update

wapm install sqlite

wapm run sqlite

wapm run sqlite r7MJVvcf.db3

- .help
- .quit .exit
- .open
- .database
- .tables
- .table '%es'
- .schema table_name

常见问题：r7MJVvcf.db3 本地文件，无法打开（r7MJVvcf.db3 提前用rust程序创建好，并添加了表、插入了记录数据）

解决方案：wapm run sqlite --dir .  （记得将本地目录映射到runtime中）

.open r7MJVvcf.db3

SELECT id, name, data FROM person;





