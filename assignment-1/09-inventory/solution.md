# Solution notes: Inventory

## Approach

For the `restock` function, I used a `HashMap<String, u32>` to merge the two inventories. Since the function takes ownership of both input vectors, I iterated through each inventory and inserted every `(name, quantity)` pair into the hash map. If an item name already existed, I added its quantity to the existing value using the `entry()` API. After processing both inventories, I converted the hash map back into a `Vec<(String, u32)>`.

For the `summary` function, I borrowed the inventory instead of taking ownership. I used `inventory.len()` to determine the number of distinct items and iterated through the inventory to compute the total number of units. Finally, I formatted the result as a string in the required format.

## Edge cases handled

* Both inventories empty
* One inventory empty
* Duplicate item names across inventories
* Inventories with completely different item names
* Empty inventory summary
* Borrowing the inventory before consuming it

## Anything special

This exercise demonstrates the difference between ownership and borrowing in Rust. The `summary` function borrows the inventory using a slice (`&[(String, u32)]`), allowing the caller to continue using the inventory afterward. In contrast, the `restock` function takes ownership of both vectors, consuming them while building the merged inventory. The `HashMap::entry()` API with `or_insert()` provides an efficient and idiomatic way to combine quantities for duplicate item names. The overall time complexity of `restock` is **O(n + m)**, where `n` and `m` are the sizes of the two inventories, while `summary` runs in **O(n)** time.
