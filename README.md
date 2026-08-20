# alga2-derive

`#[derive(Alga)]` — one line brings a struct into the whole
[alga2](https://github.com/5-6-1/alga2-rs) algebraic tower.

```rust
use alga2::op::Additive;
use alga2::tower::Magma;
use alga2_derive::Alga;

#[derive(Alga)]
#[alga(level = "Field")]
struct Vec2 { x: f64, y: f64 }

let a = Vec2 { x: 1.0, y: 2.0 };
let b = Vec2 { x: 3.0, y: 4.0 };
assert_eq!(<Vec2 as Magma<Additive>>::combine(&a, &b).x, 4.0);
```

Generates the component-wise chain — additive `Magma → Monoid → Group →`
`AbelianGroup`, multiplicative `Magma → Monoid`, the two-operator
`Semiring → Ring → CommutativeRing → Field` chain, and
`Module`/`VectorSpace` — with the field types' bounds as the where clause.

Levels: `"Monoid"`, `"Group"`, `"Ring"` (default), `"Field"`.

Structs only (named, tuple, or generic, including where-clause
constraints). No tower imports are needed at the call site.

## License

MIT OR Apache-2.0, same as alga2.
