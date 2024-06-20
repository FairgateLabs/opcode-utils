# Bitcoin Opcode Utilities

This module provides utilities for working with Bitcoin opcodes. It includes functions for identifying push opcodes and a macro for generating opcode conversion from string representations.

## Functions

### `is_push_bytes(op: Opcode) -> bool`

Determines if the given `Opcode` is a push bytes opcode.

- **Parameters**: 
  - `op`: The `Opcode` to check.
- **Returns**: `True` if the opcode is of the `PushBytes` class, `False` otherwise.

### `is_push_data(op: Opcode) -> bool`

Determines if the given `Opcode` is one of the `OP_PUSHDATA` opcodes.

- **Parameters**:
  - `op`: The `Opcode` to check.
- **Returns**: `True` if the opcode is `OP_PUSHDATA1`, `OP_PUSHDATA2`, or `OP_PUSHDATA4`, `False` otherwise.

## Macros

### `opcode_from_str!`

Macro to generate a function for converting string representations of opcodes to their respective `Opcode` values.

#### Example Usage

```rust
let opcode = from_str("OP_0").unwrap();
assert_eq!(opcode, OP_0);
```

## Usage Notes

- The utility functions use a workaround to determine the class of an opcode due to the lack of direct access to the internal code value from the `Opcode` struct.
- The `opcode_from_str!` macro simplifies the conversion from string literals to `Opcode` instances, accommodating common opcode aliases such as `TRUE` and `FALSE`.

This module is designed to extend the handling and manipulation of Bitcoin script opcodes provided by [Rust Bitcoin - BitVM branch](https://github.com/rust-bitcoin/rust-bitcoin/tree/bitvm) within Rust applications without the need of modifying the original Rust Bitcoin project.