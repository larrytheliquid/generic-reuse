Part 0: Installation
====================

Our artifact is a VirtualBox
(https://www.virtualbox.org/wiki/Downloads) image, which has Ubuntu
installed on it. The username and password on Ubuntu are both "icfp".

We now assume you are reading this
(`/home/icfp/generic-reuse/ArtifactOverview.md`, also available from
https://github.com/larrytheliquid/generic-reuse/blob/artifact/ArtifactOverview.md)
in Emacs on our provided VirtualBox image, hence all the software
installation has already been performed, and you can skip Part 0. If
you would like to manually setup the software on your personal
machine, see `/home/icfp/generic-reuse/Installation.md`, also
available from
https://github.com/larrytheliquid/generic-reuse/blob/artifact/Installation.md.

Part 1: Getting Started Guide
=============================

Our artifact is a formalization of the code presented in our paper in
the depedently typed Cedille proof assistant. The primary means of
interacting with Cedille is through an Emacs mode. To type check a
file in Cedille, open a file in Emacs whose extension is `.ced`.  The
code should be colored black, and the mode displayed at the bottom of
the buffer should be `(cedille)`.

Pressing `M-s` (the meta key, e.g. the alt key, and the character 's')
checks the file, which adds syntax highlighting and adds navigation
mode (navi) to the bottom of the buffer, which should now display
`(cedille navi)`. The file passed type checking if pressing `r`
results in the message "No errors." at the bottom in the Emacs mini
buffer.  Note that navi mode is a navigation-only mode. To edit the
file, (for example, to manually insert a syntax or type error), press
`q` to quit navi mode. After editing, press `M-s` to re-check the
file, and then `r` to ensure there are no errors, or to jump to the
first error location if there is one.  For example, you can try
checking the file `code/Everything.ced`, which imports all parts of
our development.

This is all that is required to have Cedille type check files
contained in our artifact.  If you feel more adventurous, feel free to
press `h` to enter Cedille's help mode, then click `cedille mode
commands` to learn how to navigate the code's AST, and display the
context (`c`) and goal (`i`) once focusing on a particular node (by
pressing `p` with the cursor on a node), and how to unfocus a node (by
pressing `g`). It is also possible to jump (by pressing `j`) to the
definition of a focused node, and jump back (by pressing `,`).


Part 2: Step-by-Step Evaluation Instructions
============================================

To evaluate our artifact, open each Cedille (.ced) file described below
(which we map to the appropriate section in our paper), then press
`M-s` to check it, and press `r` to verify that the "No errors."
message is displayed. We also indicate which section of the paper each
definition comes from.

Note that the paper's code is much more terse, as it omits types and
terms inferrable by a sufficiently advanced unification algorithm,
which is not currently implemented by Cedille. Hence, the Cedille code
is more verbose, but we did our best to use type synonyms where
possible to maintain the readability of our code. Futher details about
Cedille syntax can be found in Section 2.1 and Figure 2 of the paper.

Cedille's syntax distinguishes type application from
term application, where type application uses a center dot. For
example, in the paper we would see `Id AppV AppL`, whereas in the
formalization we see `Id · AppV · AppL`. Erased term (rather than
type) arguments (mostly omitted/inferred in the paper) are given via a
dash. For example, `v2l! xs` in the paper becomes `v2l! · A -n xs` in
the formalization.

In Cedille and in our development, it is important to know what a term
normalizes to after erasure (especially if complex terms, like the
zero-cost conversion `v2l!`, erase to the identity function). To
practice this on a definition (after type checking, i.e., in navi
mode), place your cursor on its identifier, then press `p` to focus on
the definition, then press `C-i n` to erase and normalize it. For
example, focusing on the identitier `id` and erasing/normalizing it in
the definition: `id ◂ ∀ X : ★. X ➔ X = Λ X. λ x. x.`, produces `λ
x. x.`. Notice that the capital lambda (`Λ X.`), which binds types,
has been erased (Figure 1 contains the erasure rules).

Finally, you may be interested in reading `README.md` for an overview of
the directory structure of the code, including files and definitions
that the paper assumes to exist (e.g. `code/Datatypes/Vec.ced`).
However, understanding the directory structure and extra files is not
necessary to evaluate our artifact, and the instructions below are
sufficient.

Everything
----------

As a sanity check, `code/Everything.ced` imports all of the files
mentioned below, so if it passes type checking then everything type
checks.

Type of Dependent Identity Functions
------------------------------------

The file `code/Base/Id.ced` contains the following dependent identity
function definitions (Section 4.1): `IdDep`, `intrIdDep`,
`elimIdDep`. It also contains the following non-dependent
counterparts: `Id`, `intrId`, `elimId`.

Note that `elimIdDep` is defined in terms of the more general
`elimIdDep~` (not in the paper), which allows the eliminated `IdDep`
argument to be erased.

Identity Mappings
-----------------

File `code/IndexedMendlerInduction/IIdMapping.ced` contains the
non-indexed and indexed types of identity mappings (Section 5.1),
`IdMapping` and `IIdMapping`, respectively.

Files `code/Datatypes/ListF.ced` and `code/Datatypes/VecF.ced` contain
the list and vector schemes (Figure 3) and identity mappings (Section 5.2),
`ListF` & `imapL` and `VecF` & `imapV`, respectively.

Forgetful Program & Proof Reuse Combinators
-------------------------------------------

File `code/GenericReuse/FogFun.ced` contains the forgetful program
(non-dependent function) reuse combinator `allArr2arr` (Section 4.2.1)
and the forgetful proof (dependent function) reuse combinator
`allPi2pi` (Section 4.2.3). Note that these are defined in terms of
more general versions of the combinators, whose names are suffixed by
the prime symbol: `allArr2arr'` and `allPi2pi'`. However, inlining the
prime definitions results in the definitions of the paper.

Enriching Program & Proof Reuse Combinators
-------------------------------------------

File `code/GenericReuse/EnrFun.ced` contains the
enriching program (non-dependent function) reuse combinator
`arr2allArrP` (Section 4.3.1) and the enriching proof (dependent
function) reuse combinator `pi2allPiP` (Section 4.3.3).

Forgetful Data Reuse Combinator
-------------------------------

File `code/GenericReuse/FogFix.ced` contains the forgetful data
(fixpoint) reuse combinator `ifix2fix` (Section 5.3.1).

Enriching Data Reuse Combinator
-------------------------------

File `code/GenericReuse/EnrFix.ced` contains the enriching data
(fixpoint) reuse combinator `fix2ifix` (Section 5.5.1).

Program Reuse Examples
----------------------

File `code/Examples/AppendReuse.ced` contains examples of reusing
append functions and associativity proofs:
1. Forgetful program reuse `appV2appL` (Section 4.2.2).
2. Forgetful proof reuse `assocV2assocL` (Section 4.2.4).
3. Enriching program reuse `appL2appV` (Section 4.3.2).
4. Enriching proof reuse `assocL2assocV` (discussed in Section 4.3.3,
   but omitted in the paper).

Note that these examples make extensive use of type synonyms to split
a type into the various pieces that would be inferred by a more
sophisticated implementation of Cedille, e.g. AppV1 through AppV3,
AssocV1 through AssocV4, etc.

The crucial point of our paper is that the bang versions of these
definitions erase and normalize to the identity function. For example,
you can focus on `assocV2assocL!` by pressing `p` over its definition
identifier, then pressing `C-i n` to verify the identity function is
produced.

Data Reuse Examples
-------------------

File `code/Examples/ListVecReuse.ced` contains examples of reusing
lists and vectors:
1. Forgetful reuse of vectors as lists `v2l` & `vf2lf` (Section 5.3.2)
2. Enriching reuse of lists as vectors `l2v` & `lf2vf` (Section 5.5.2)

Again, you can verify that bang versions of these definitions, like
`v2l!`, erase to the identity function.

Auxiliary Combinators
---------------------

File `code/GenericReuse/Aux.ced` contains the auxiliary combinators
from Figure 2 in the paper: `id`, `copyType`, `copyTypeP`, and `subst`
(as well as others not in the paper).


Part 3: Mandatory Revisions
===========================

For completeness, we have also included code addressing the mandatory
revisions of our paper. Because the text describing the revisions has
not yet been written, we do not expect you to verify this part, but we
include it below in case you are interested.

Enriching Data Reuse Combinator with a Premise
----------------------------------------------

As mentioned in Part 2, file `code/GenericReuse/EnrFix.ced` contains
`fix2ifix`, which enriches data by providing an algebra (representing
a total function). Thus, lists can be enriched to vectors by
calculating the index via the length algebra. Some indexed types
(e.g. typed STLC terms) cannot have their indices be computed by a
total function from their untyped counterparts. Hence, the file also
contains the combinator `fix2ifixP`, which allows data to be enriched
if it satisfies a premise (e.g. the typing relation of an untyped STLC
term).

Data Reuse Examples
-------------------

Data reuse is between typed (the positive result of type checking)
STLC `Term`s (code/Datatypes/Term.ced) and untyped (prior to type
checking) `Raw` terms (code/Datatypes/Raw.ced).

File `code/Examples/RawTermReuse.ced` contains examples of reusing
raw and typed terms:
1. Forgetful reuse of typed terms as raw terms `t2r` & `tf2rf`
2. Forgetful reuse of list membership proofs as natural numbers `i2n` & `if2nf`
3. Enriching reuse of raw terms as typed terms `r2tP` & `rf2tfP`
4. Enriching reuse of natural numbers as list membership proofs `n2iP` & `nf2ifP`

The list membership proofs are used to ensure that a type appears in
the context, as an argument to the well-typed variable constructor of
`Term`. The `Raw` term variable constructor simply has a natural
number as its argument, representing the de Bruijn index.

Raw terms are enrichable if they satisfy a typing relation (`Typed`),
given abstractly as a module parameter. Any implementation of `Typed`
works, as long as it is possible to satisfy the required inversion
lemmas (e.g. `invLamEq`), which also appear as module parameters.

Similarly, a natural number is enrichable to a membership proof if it
satisfies an abstract `Lookup` relation saying that an element appears
in the list at a particular natural number position. `Lookup` can also
be implemented many different ways, and is specified by its required
inversion lemmas.

Program Reuse Examples
----------------------

For program reuse, we show how to enrich a one-step
(beta) reduction function on raw terms to a
type-preserving version on typed terms.

File `code/Examples/StepReuse.ced` contains an example of enriching
program reuse of a step function as the term `stepR2stepT`.  The
premise to `stepR2stepT` is that the step function for raw terms must
preserve types, as specified by `TpPres`.






