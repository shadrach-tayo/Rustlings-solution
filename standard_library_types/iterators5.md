```rust
fn count_iterator(map: &HashMap<String, Progress>, value: Progress) -> usize {
    // map is a hashmap with String keys and Progress values.
    // map = { "variables1": Complete, "from_str": None, ... }
    map.values()
        .into_iter()
        .filter(|m| *m.clone() == value)
        .count()
}

fn count_collection_iterator(collection: &[HashMap<String, Progress>], value: Progress) -> usize {
    // collection is a slice of hashmaps.
    // collection = [{ "variables1": Complete, "from_str": None, ... },
    //     { "variables2": Complete, ... }, ... ]
    collection
        .into_iter()
        .map(|hash| {
            hash.values()
                .into_iter()
                .filter(|m| *m.clone() == value)
                .count()
        })
        .sum()
}
```