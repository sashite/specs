# Forsyth–Edwards Expanded Notation

Largely inspired by [FEN](https://en.wikipedia.org/wiki/Forsyth%E2%80%93Edwards_Notation), **FEEN** is "_Forsyth–Edwards Expanded Notation_"; it is a flexible and minimalist format for describing chess variant positions.

## Overview

The FEEN format is intended to be flexible enough to represent the positions of most chess variants, even on more than two dimensions, while remaining minimalist by ignoring specific features of chess variants.

For example,

- there is no field for _Castling availability_ in FEEN because it would be too specific to the Western Chess variant (whose positions are already fully described by the FEN format);
- there is no field for _Pieces in hand_ in FEEN because it would be too specific to the Japanese Chess variant (whose positions are already fully described by the [FEN for Shogi](http://hgm.nubati.net/usi.html) format).

## Data fields

A FEEN description has two fields:

1. Piece placement
2. Side to move

Each field is composed only of non-blank printing ASCII characters.
Adjacent fields are separated by a single ASCII space character.

### Piece placement

Pieces should be symbolized by one character. However, it is possible to use several characters if there is no ambiguity to distinguish them.

Examples:

- "`+p`"
- "`♔`"
- "`C:P`"
- "`卒`"
- "`foobar`"

Blank squares are noted using digits `1` through `n` (where `n` is the number of continuous blank squares on the last dimension).
An empty string (i.e., "") is used to separate pieces, and between each dimension, solidus characters "`/`" are used.

Empty board examples:

- 6 size: "`6`"
- 4x8 size: "`8/8/8/8`"
- 7x7 size: "`7/7/7/7/7/7/7`"
- 5x5x5 size: "`5/5/5/5/5//5/5/5/5/5//5/5/5/5/5//5/5/5/5/5//5/5/5/5/5`"

Starting board examples:

- Chess: "`♜♞♝♛♚♝♞♜/♟♟♟♟♟♟♟♟/8/8/8/8/♙♙♙♙♙♙♙♙/♖♘♗♕♔♗♘♖`"
- Four-Player Chess: "`3yRyNyByKyQyByNyR3/3yPyPyPyPyPyPyPyP3/14/bRbP10gPgR/bNbP10gPgN/bBbP10gPgB/bKbP10gPgQ/bQbP10gPgK/bBbP10gPgB/bNbP10gPgN/bRbP10gPgR/14/3rPrPrPrPrPrPrPrP3/3rRrNrBrQrKrBrNrR3`"
- Shogi: "`lnsgkgsnl/1r5b1/ppppppppp/9/9/9/PPPPPPPPP/1B5R1/LNSGKGSNL`"
- Xiangqi: "`車馬象士將士象馬車/9/1砲5砲1/卒1卒1卒1卒1卒/9/9/兵1兵1兵1兵1兵/1炮5炮1/9/俥傌相仕帥仕相傌俥`"

Another example:

- A tsume Shogi: "`3sks3/9/4+P4/9/7+B1/9/9/9/9`"

### Side to move

Players can be identified by a number according to the order in which they traditionally play from the starting position, or a letter.

Examples:

- Chess: _White_ is `0` (or `w`) and _Black_ is `1` (or `b`);
- Four-Player Chess: _Red_ is `0` (or `r`), _Blue_ is `1` (or `b`), _Yellow_ is `2` (or `y`) and _Green_ is `3` (or `g`).
- Shogi: _Sente_ is `0` (or `s`) and _Gote_ is `1` (or `g`);
- Xiangqi: _Red_ is `0` (or `r`) and _Black_ is `1` (or `b`);

Therefore, in a game of Chess, if _Black_ have to play the next move, the identifier can be `1` (or `b`).

## Example

Starting position examples:

- Chess: "`rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR 0`"
- Four-Player Chess: "`3yRyNyByKyQyByNyR3/3yPyPyPyPyPyPyPyP3/14/bRbP10gPgR/bNbP10gPgN/bBbP10gPgB/bKbP10gPgQ/bQbP10gPgK/bBbP10gPgB/bNbP10gPgN/bRbP10gPgR/14/3rPrPrPrPrPrPrPrP3/3rRrNrBrQrKrBrNrR3 0`"
- Janggi: "`rmes1semr/4g4/1p5p1/j1j1j1j1j/9/9/J1J1J1J1J/1P5P1/4G4/RMES1SEMR 0`"
- Makruk: "`rnbqkbnr/8/pppppppp/8/8/PPPPPPPP/8/RNBKQBNR 0`"
- Shogi: "`lnsgkgsnl/1r5b1/ppppppppp/9/9/9/PPPPPPPPP/1B5R1/LNSGKGSNL 0`"
- Xiangqi: "`rheagaehr/9/1c5c1/s1s1s1s1s/9/9/S1S1S1S1S/1C5C1/9/RHEAGAEHR 0`"

Another example:

- A tsume Shogi: "`3sks3/9/4+P4/9/7+B1/9/9/9/9 0`"

### Scenario

Given the following position between two Chess players:

```
♜♞♝♛♚♝♞♜/♟♟♟♟♟♟♟♟/8/8/8/8/♙♙♙♙♙♙♙♙/♖♘♗♕♔♗♘♖ 0
```

When e2e4 move is applied, then the position becomes:

```
♜♞♝♛♚♝♞♜/♟♟♟♟♟♟♟♟/8/8/4♙3/8/♙♙♙♙1♙♙♙/♖♘♗♕♔♗♘♖ 1
```
