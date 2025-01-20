# Rust Raw Pointer Vector Modification Bug

This repository demonstrates a common error in Rust: modifying a vector through a raw pointer after the vector's capacity has been exceeded. This can lead to undefined behavior, such as data corruption or crashes.

The `bug.rs` file contains the buggy code. The `bugSolution.rs` file offers a corrected version that avoids undefined behavior.

## Problem

When a vector needs to grow beyond its initial capacity, Rust may reallocate its memory.  If you have a raw pointer to the vector's data, this pointer becomes invalid after reallocation. Modifying the data through this invalid pointer results in undefined behavior.

## Solution

Avoid using raw pointers to modify vectors unless you absolutely need to work at this low level.  If using raw pointers, ensure the pointer remains valid throughout its use by carefully managing the vector's lifetime and capacity.