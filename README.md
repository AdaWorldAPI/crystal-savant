# Crystal Savant

**Multi-pass Codebook: Concept CAM with Hamming Meta-Resonance**

Massive semantic compression through learned resonance surfaces.

## Key Insight

**Pass 1** (expensive, one-time): Collect concepts from rich corpus
- Books, NARS patterns, qualia mappings, SPO relations
- Jina embed → 10Kbit fingerprint → cluster into CAM slots

**Pass 2** (cheap, runtime): Hamming meta-resonance lookup
- New text → hash fingerprint (NO API CALL)
- XOR scan against CAM slots
- ~6µs per lookup, 176K lookups/sec
- 157KB memory (fits L2 cache)

```
The CAM IS the learned semantic space.
Once trained, it's a pure resonance surface.
All lookups are binary operations—no embedding calls.
```

## Compression Architectures

| Architecture | Compression | Use Case |
|--------------|-------------|----------|
| Dictionary Crystal | 300x @ 1M chunks | Codebook + sparse index |
| Hierarchical 8×1024 | 3400x | Clustering + projection |
| SPO Resonance | 1000x on addresses | Cell-based navigation |

## Performance

```
10K lookups in 56.73ms
Throughput: 176,274 lookups/sec
Memory: 157 KB (128 slots × 10Kbit)
```

## Files

- `src/multipass.rs` - Core Concept CAM with NARS/SPO/Qualia archetypes
- `src/dictionary_crystal.rs` - Codebook-indexed compression
- `src/hierarchical.rs` - 8×1024 clustering + projection
- `ARCHITECTURE.md` - Full system documentation

## Build

```bash
cargo build --release
./target/release/crystal-savant
```

## Related

- [spo-crystal](https://github.com/AdaWorldAPI/spo-crystal) - Core 3D crystal + Jina cache
- [crystal-memory](https://github.com/AdaWorldAPI/crystal-memory) - VSA benchmarks

## License

MIT
