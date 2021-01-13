==================
Azul game notation
==================

Azul is an abstract strategy board game
designed by Michael Kiesling.

This is an effort of creating a notation
that can record a complete Azul game.

General
=======

The whole game is stored in a single text file.

All information is line-oriented
and there are no line continuations.

The players are denoted by letters ``A``, ``B``, ``C``, and ``D``.
In any game, A denotes the player playing first
and the rest of the letters denote players playing
in sequence.  Therefore, a two-player game
only uses ``A`` and ``B``.

The factories are denoted by numbers starting from ``1``.
A two-player game uses factories ``1`` to ``5``,
while a four-player game uses factories ``1`` to ``9``.
The center of the table, where unpicked tiles
from factories go, is denoted by number ``0``.

The tiles themselves are denoted
by a single lower-case letter.

+--------+----------------------+
| Letter | Tile                 |
+========+======================+
| ``l``  | blue (solid)         |
+--------+----------------------+
| ``o``  | orange (pattern)     |
+--------+----------------------+
| ``r``  | red (solid)          |
+--------+----------------------+
| ``k``  | black (pattern)      |
+--------+----------------------+
| ``u``  | light blue (pattern) |
+--------+----------------------+

A set of tiles are denoted by simply juxtaposing
all its contents.  The order is not significant.
For example, ``bbkr`` is a set of two blue tiles,
one black and one red.

The destination lines on the player board
are denoted by a single number, ``1`` to ``5``,
according to their length.
The floor line is denoted by ``-``.

Game record
===========

Signature
---------

The file starts with the string ``AZULGAME``
on the first line.

Number of players
-----------------

The first data line of the file should be
a single digit in the range ``2`` to ``4``,
denoting the number of players in the game.

Draws
-----

Draws of new tiles and placement on factories
are recorded on a single line.
The sets of tiles placed on each factory
are listed following the factory number.

For example, a random draw on a two-player game
(that uses five factories) can be like:

    1llrr 2orku 3luuk 4krul 5rrok

Movement
--------

Each player move is denoted by a single line.
The first character is the player symbol.
The second character is the origin.
Next is the set of tiles collected by the player,
which obviously must be of the same color.
Finally, the set of destinations are listed,
which have to be the same length as the collected tiles.

Spaces can occur anywhere in the line.

For example, the following line:

    A 2 rrr 22-

This records that the first player
picked from the second factory 
three red tiles,
placed two of them on the second line
and placed the third on the floor line.

Comments
--------

The data may be interspersed with comment lines.

A comment line starts with the character ``#``
as the first character of the line
and extends until the first newline.
The contents of the comment line
do not contain any crucial information
about the game and can be discarded.

Metadata
========

There are some special lines that can be used
to record game metadata.
These lines all start with the character ``:``
as the first character of the line.
As with comments, they can be interspersed
between data lines,
although it makes sense to have them as a block
at either the beginning or the end of the file.

Player names
------------

A metadata line with the player symbol immediately
after the initial ``:`` can be used to record
the name of the player.

The following example records that the first player
was John Doe:

    :A John Doe

Date of game
------------

A metadata line starting with ``:date``
can be used to denote the date a game took place.

The following example records that the game took place
on Christmas Day 2020:

    :date 2020-12-25

Commentary
----------

A single ``:`` followed by a space can be used
to record comments about the game.

