# 1. Introduction and General Overview

[Take Me Home](README.md)
<br>

## Introduction

Databases need data structures to store data and implement access methods for efficient access of
a data item.

Traditionally, B+-trees are used for this data structure for its efficient handling of read and
write operations. However, log-structured merge trees are recently a widely adopted alternative
due to its efficiency in handling write-intensive workloads.

### B+-trees

- Traditional approach.
- Built for when read and write operations are more balanced.

### Log-structured merge trees (LSM-trees)

- Newer approach.
- Built for write-intensive workloads.
- Widely adopted by newer database systems.

<br>

## General Overview

<div align=center>
    <h3>What Makes an LSM-tree?</h3>
    <img src="pictures/lsm_overview.svg" alt="LSM Overview" width="700">
</div>

<br>

An LSM-tree consists of an in-memory memtable that can either use a skip list or balanced tree as
its data structure.

It also has on-disk storage that uses multiple SSTables to store data on-disk.

[Next: Main Components of an LSM-tree](02_main_components.md)

<br>
