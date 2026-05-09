# Tin Architecture v0.1 Draft
A clean, emulator-first 64-bit instruction set designed for readability, OS development, and virtual hardware experimentation.

## 1. Design goals

The architecture prioritizes:

* Human-readable assembly syntax
* Simple, consistent instruction semantics
* Easy emulator implementation
* OS-friendly design (syscalls, interrupts, memory mapping)
* No legacy baggage (unlike x86 / ARM / 6502)

## 2. Core properties
* 64-bit architecture
* Byte-addressable memory
* Little-endian (recommended for simplicity)
* Flat memory model (no segmentation in v0.1)
* Fixed general-purpose registers

## 3. Registers

| Name    | Purpose                                                |
| ------- | ------------------------------------------------------ |
| `a`     | primary accumulator                                    |
| `b`     | general purpose                                        |
| `c`     | general purpose                                        |
| `d`     | general purpose                                        |
| `sp`    | stack pointer                                          |
| `bp`    | base/frame pointer                                     |
| `pc`    | program counter (not directly writable in normal code) |
| `flags` | status register                                        |


### Flags (basic set)
* `Z` zero
* `N` negative
* `C` carry
* `O` overflow

## 4. Memory model
* Full 64-bit address space (virtualized in emulator)
* Memory-mapped I/O allowed
* No segmentation in base version

Example device map (emulator-defined):
```
0xFFFF0000 - LED display
0xFFFF0008 - button A
0xFFFF0009 - button B
```

