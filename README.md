# `genre`

> A curated genre vocabulary as first-class on-chain objects. The shared primitive behind release and party genre tagging.

**Layer:** `lib` — a primitive, not core protocol and not an extension (it attaches to nothing miso-specific). A `Genre` is a derived object of a curator-held `GenreRegistry`, so its address is a pure function of `(registry, name)` and any consumer can derive it without a lookup table.

Genres are values other packages point at, never strings they copy: an extension stores a `Genre` id, and display names resolve through the object. That keeps naming consistent across every consumer and makes the vocabulary curatable in one place rather than re-litigated per extension.

Names are validated on creation — non-empty, length-bounded, and restricted to a canonical character range — so the vocabulary cannot accumulate near-duplicate spellings.

## Usage

```move
use genre::genre::Genre;

// Consumers hold the id and resolve the object when they need the name.
public fun tag(self: &mut MyObject, genre: &Genre) {
    self.genre_id = object::id(genre);
}
```

## License

Apache-2.0
