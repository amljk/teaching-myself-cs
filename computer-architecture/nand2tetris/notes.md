# Build a Modern Computer from First Principles: From Nand to Tetris

## Resources
- [Course](https://www.coursera.org/learn/build-a-computer)
- [Simulator](https://www.nand2tetris.org/software)
  - [Setup Guide](https://drive.google.com/file/d/1QDYIvriWBS_ARntfmZ5E856OEPpE4j1F/view)

## Intro
- A programming language is an **abstraction**, so that you don't have to worry about the implementation (how the pixels show up on the screen, how the language interacts with the computer to give it instructions, etc.) 

# Module 1: Boolean Functions and Gate Logic
## 1.1 Boolean Logic
- Computers internally only have 0s and 1s (can also be considered No/Yes, False/True)

### Boolean Operations
**AND operation:** `(x AND y) x^y`
| x | y | AND|
|:-:|:-:|:--:|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

**OR operation:** `(x OR y) x∨y`
| x | y | OR|
|:-:|:-:|:--:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

**NOT operation:** `(NOT x) ¬x`
| x |NOT|
|:-:|:-:|
| 0 | 1 |
| 1 | 0 |

### Boolean Functions
`f(x,y,z) = (x AND y) OR (NOT(x) AND z)`
| x | y | z| f|
|:-:|:-:|:--:|:--:|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |

### Boolean Identities
- Commutative Laws
  - `(x AND y) = (y AND x)`
  - `(x OR y) = (y OR x)`
- Associative Laws
  - `(x AND (y AND z)) = ((x AND y) AND z)`
  - `(x OR (y OR z)) = ((x OR y) OR z)`
- Distributive Laws
  - `(x AND (y OR z)) = (x AND y) OR (x AND z)`
  - `(x OR (y AND z)) = (x OR y) AND (x OR z)`
- De Morgan Laws
  - `NOT(x AND y) = NOT(x) OR NOT(y)`
  - `NOT(x OR y) = NOT(x) AND NOT(y)`

### Boolean Algebra
To simplify `NOT(NOT(x) AND NOT(x OR y))`:
  - Using De Morgan Law: `NOT(NOT(x) AND (NOT(x) AND NOT(y)))`
  - Then, using Associative Law: `NOT((NOT(x) AND NOT(x)) AND NOT(y)))`
  - Then, simplified with Idempotence Law: `NOT(NOT(x) AND NOT(y))`
  - Then, using De Morgan Law: `NOT(NOT(x)) OR NOT(NOT(y))`
  - Then, simplified using Double Negation Law: `x OR y`
  - Can also derive this using truth table

## 1.2 Boolean Function Synthesis
- If only given a truth table, can you derive the Boolean function?
  
| x | y | z| f|
|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 1 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 0 |

- From the first line, we get `(NOT(x) AND NOT(y) AND NOT(z))`
- From the third line, we get `(NOT(x) AND y AND NOT(z))`
- From the fifth line, we get `(x AND NOT(y) AND NOT(z))`
- Combining all three, we get `(NOT(x) AND NOT(y) AND NOT(z)) OR (NOT(x) AND y AND NOT(z)) OR (x AND NOT(y) AND NOT(z))`
  - From the first two statements, we can remove the y, so we get `(NOT(x) AND NOT(z)) OR (x AND NOT(y) AND NOT(z))`

### Nand
- Any Boolean function can be represented using an expression containing AND and NOT operations (because we know that OR equals NOT AND using De Morgan Law)
- However, the NAND function can simplify this: `NAND(x,y) = NOT(x AND y)`
- **Any Boolean function can be repsented using an expression containing only NAND operations**
  - `NOT(x) = (x NAND x)`
  - `(x AND y) = NOT(x NAND y)`

## 1.3 Logic Gates
- Gate logic: a technique for implementing Boolean functions using logic gates
  - **Elementary logic gate:** a standalone chip which is designed to deliver a well-defined functionality (NAND, AND, OR, NOT functionality)
  - **Composite:** A logic made up from elementary logic gates and other composite logic gates, more complex than elementary (multiplexer, adder)

### Elementary Logic Gates
