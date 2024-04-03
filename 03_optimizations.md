# 3. Main Optimizations for an LSM-tree

<br>

## Compaction

- With compaction, storage and read performance are improved by merging smaller SSTables and eliminating obsolete data.

- Compaction policies, such as leveling and tiering, are arguably the most important optimization for LSM-trees.

    - Leveling: When a level/layer gets full, smaller SSTables are merged into a larger one on the next level.

    - Tiering: Data is separated into tiers based on size, age, or access frequency. Custom compaction policies for each tier help optimize compaction.

<br>

## Bloom Filters

- Bloom filters improve read performance by reducing unnecessary access to places in storage that don’t have the desired key.

- When data is written to a data structure with a Bloom filter, the data is hashed three times to become a random index of a bit array. The three indexes in the bit array are turned into a 1.

- When looking up data, it’s ran through the hashes again, and if any of the indexes map to a 0, the data is not contained in the data structure.

- False positives can occur when every index maps to a 1, but the data is not in the data structure. This gives reads an average time complexity of constant time, but a worst-case scenario time complexity of O(n).

- In LSM-trees, Bloom filters are commonly applied to SSTables, but can also be applied to the layers that hold SSTables.

<br>

## Other Optimizations?

It’s important to note that there are more optimizations that LSM-trees can utilize. How LSM-trees are implemented and what optimizations they choose to implement depends on the use case of the LSM-tree.