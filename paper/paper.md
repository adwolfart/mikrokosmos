---
title: 'Mikrokosmos: an educational lambda calculus interpreter'
tags:
- lambda calculus
- functional programming
- intuitionistic logic
- computability
authors:
- name: Mario Román
  orcid: 0000-0003-3158-1226
  affiliation: 1
affiliations:
- name: University of Granada
  index: 1
date: 5 August 2018
bibliography: paper.bib
---

# Description

Mikrokosmos is an educational untyped and simply typed lambda-calculus
interpreter.  For students, it is a tool to learn lambda-calculus and
intuitionistic logic by coding.  For educators, it is a didactic resource,
grounded in the theoretical implementation of a functional programming language,
so that they can integrate it with other learning materials.  Mikrokosmos can be
used on three different environments: (1) as a *command line executable*,
implementing a read-eval-print loop interpreter; (2) as a *Jupyter kernel*,
executing code blocks from a Jupyter notebook [@jupyter]; and (3)
as a *Javascript web application*, that can be used in conjunction
with web text editors such as Codemirror[^codemirror] to create an
online programming environment.

[^codemirror]: http://codemirror.net/

Mikrokosmos provides a minimalist and unified syntax for both simply
typed and untyped lambda-calculus.  The same expressions can be used
to define untyped and typed terms.  This helps highlighting the
differences between them, and avoids the added complexity of two
different syntaxes.  Moreover, the syntax is heavily inspired by
Haskell so that it facilitates transferring ideas to a fully-fledged
functional programming language.  Mikrokosmos comes also bundled with
a self-documenting standard library of common lambda-calculus
combinators and data structures which can be consulted directly from
the interpreter and ease the learning process, while demonstrating how
to write basic programs on lambda-calculus.

The interpreter focuses on being portable, close to the theory and
suited for learning and experimentation.  For the untyped
lambda-calculus, Mikrokosmos works as a Turing-complete programming
language. Following @barendregt84, it implements the *leftmost
evaluation strategy*, which finds a normal form whenever it exists,
allowing infinite data structures and fixed point definitions.  The
evaluation can be visualized step-by-step, showing how the internal
representation of a lambda term using De Bruijn indexes works
[@de1972lambda].  Optional coloring of the output facilitates this
purpose.  With regards to combinatorial logic, a translation between
lambda terms and SKI combinators is available. It follows a standard
algorithm from @hindley2008lambda that allows the user to input and
visualize results in both formats.  On the typed side, Mikrokosmos
facilitates the study of the Curry-Howard isomorphism; see
@sorensen2006lectures for a description of this correspondence.  To
this end, it implements implicit typing à la Curry: the most general
possible type is automatically inferred for any term, providing a
limited form of polymorphism.  Given any typed lambda expression,
Mikrokosmos can visualize the logical derivation tree it codifies in
the style of Gentzen, sharing the notation of introductory articles
and textbooks such as those by @wadler2015propositions or
@girard1989proofs.

![](fig1.png)
*Figure 1. An example Gentzen diagram of a proof on intuitionistic logic.*

The latest release of the interpreter can be installed via `stack` or
`cabal` from Hackage[^hackage] and the documentation can be found in
https://mroman42.github.io/mikrokosmos/, where installation and usage
instructions for the Jupyter kernel and the Javascript web application
are also provided.

[^hackage]: https://hackage.haskell.org/package/mikrokosmos

# Statement of need

When teaching the logical structure of lambda-calculus, it is
common to ask the students to evaluate lambda terms by hand. This
approach seems necessary on the first stages of the learning
process, but turns out to be very tedious while dealing with complex terms.  
Just as one would never teach C programming language by making students
execute large programs by hand, it makes sense to provide an interpreter
and a programming environment allowing the students to explore lambda-calculus 
without having to worry about the details and focusing on the
big picture. Because of this, there is a need for a lambda-calculus
interpreter.  Untyped lambda-calculus interpreters are common, but
they are usually developed as programming exercises, and only provide
ascetic interpreters lacking any didactic features. Mikrokosmos
addresses the need for an educational interpreter with multiple ways
of visualizing the results, a clean and coherent syntax, libraries,
and the possibility of integration in web pages and Jupyter notebooks.

The Curry-Howard isomorphism between simply-typed lambda calculus and
propositional intuitionistic logic as described by
@wadler2015propositions is sometimes illustrated using the Haskell
programming language or other similar functional languages. This
approach, however, is theoretically questionable. On the one hand,
Haskell implements a polymorphic lambda calculus corresponding to
second-order intuitionistic logic, as depicted by @wadler2007girard;
but it is not total and makes every type inhabited, which is a fatal
flaw for our purpose.  On the other hand, it fails to represent a
cartesian closed category due to its support for strict evaluation,
partial functions and undefined values; as justified by
@danielsson2006fast. Even if these deviations from the theory are
justified by the needs of a real-world programming language, a student
faced with Haskell as an example of the "Propositions as Types"
paradigm may find it difficult to determine exactly what parts of the
language should be ignored in order to retain a sound interpretation.
Mikrokosmos, on the contrary, simply implements the internal language
of a bicartesian closed category, following, for instance,
@lambek1988introduction, and avoiding any spurious additions.

Simply-typed lambda calculus interpreters of this kind are rare; the
existing software usually implements some particular primitive types,
input-output, and tends not to use Curry typing. It is not designed to
allow the study of the Curry-Howard correspondence.

Mikrokosmos has already been tested on the classroom and its web
application can be easily deployed to create interactive tutorials
suited for the needs of each specific course.  In particular,
Mikrokosmos and its interactive tutorial have already been used as a
module for the course "Lógica y Programación" (Logic and Programming)
taught by Pedro A. García-Sánchez at the University of Granada. The
students were able to complete the exercises of the tutorial and to
use the interpreter as an aid while completing other problem sets of
the course.

# Acknowledgments

This development was partially supported by the "Beca de Colaboración
de Estudiantes en Departamentos Universitarios para el curso académico
2017-2018" from the Spanish Ministerio de Educación, Cultura y Deporte
at the Departamento de Álgebra of the Universidad de Granada. The
author would like to thank his advisor for this grant program,
professor Pedro A. García-Sánchez, for his patient supervision, advice
and encouragement.

# References




