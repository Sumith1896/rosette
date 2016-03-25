The Rosette Language
====================

[![Build Status](https://travis-ci.org/emina/rosette.svg?branch=master)](https://travis-ci.org/emina/rosette)

This repository includes the source code for the Rosette solver-aided host language, as well as several example
solver-aided DSLs.

## Installing Rosette

To install Rosette from source:

* Download and install Racket 6.4 from http://racket-lang.org

* Clone the rosette repository:

  `$ git clone https://github.com/emina/rosette.git`
  
* Use Racket's `raco` tool to install Rosette as one of your Racket collections:

  `$ cd rosette`  
  `$ raco pkg install ./rosette`  
  
## Executing Rosette programs

* Open the target program in DrRacket (e.g., [`rosette/sdsl/fsm/demo.rkt`](https://github.com/emina/rosette/blob/master/sdsl/fsm/demo.rkt))
  and hit run!

* DrRacket is the preferred way to execute Rosette programs.  If you
  need to use the command line, make sure to first compile the program:

  `$ raco make <your program>`  
  `$ racket <your program>`  

## Available languages

* Rosette ships with two languages: `#lang rosette/safe` and  `#lang rosette`.

* The `rosette/safe` language includes only constructs that are safe to
  use with symbolic values.  This (for now) excludes some nice Racket
  features, such as iteration constructs.  The semantics of these
  constructs can be expressed in the core language, however, so no
  expressiveness is lost (just convenience).  It is recommended for
  new users of Rosette to start with the `rosette/safe` language.  To
  see the list of syntactic forms and procedures provided by
  `rosette/safe`, type the following into the Rosette REPL:
  
  `> (rosette)`  
  `'(define assert let let* ...)`

* The `rosette` language includes all of Racket.  This places the burden
  on the programmer to decide whether a given Racket construct (which
  is not overriden by Rosette) is safe to use in a given context.
  Rosette provides no guarantees or checks for programs that use
  unsafe constructs.  In the best case, such a program will fail with
  an exception if a symbolic value flows to a construct that does not
  support it.  In the worst case, it will continue executing with
  incorrect semantics or cause more serious problems (e.g., data loss if 
  it writes to a file).

* For more on using Rosette, see [_The Rosette Guide_][1].  Rosette's internals are described in [PLDI'14][2].
  
[1]: http://emina.github.io/rosette/doc/rosette-guide/index.html
[2]: http://dl.acm.org/citation.cfm?id=2594340


  
  