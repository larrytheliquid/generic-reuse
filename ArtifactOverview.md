Part 1: Getting Started Guide
=============================

Our artifact is a formalization of the code presented in our paper in
the depedently typed Cedille proof assistant. The primary means of
interacting with Cedille is through an Emacs mode. To type check a
file in Cedille, open a file in Emacs whose extension is `.ced`.
The code should be black and white, and the mode displayed at the
bottom of the buffer should be "(cedille)".

Pressing `M-s` (the meta key, e.g. alt, and `s`) checks the file,
which adds syntax highlighting and adds navigation mode (navi) to the
bottom of the buffer "(cedille navi)". The file passed type checking
if pressing `r` results in the message "No errors." at the bottom of
the file buffer.

This is all that is required to evaluate our artifact, for each file
described in Part 2. If you feel more adventurous, feel free to press
`h` to enter Cedille's help mode, then click "cedille mode commands"
to learn how to navigate the code's AST, and display the context (`c`)
and goal (`i`) once focusing on a particular node (by pressing `p`
with the cursor on a node), and how to unfocus a node (by pressing
`g`). It is also possible to jump (by pressing `j`) to the definition
of a focused node, and jump back (by pressing `,`).

Part 2: Step-by-Step Evaluation Instructions
============================================

To evaluate our artifact, open each Cedille (.ced) file described below
(which we map to the appropriate section in our paper), then press
`M-s` to check it, and press `r` to verify that the "No errors."
message is displayed. Also, verify that the definitions described
below appear in the Cedille file and the paper section.

Note that the paper's code is much more terse, as it omits types
inferrable via a sufficiently advanced unification algorithm not
currently implemented by Cedille. Hence, the Cedille code is more
verbose, but we did our best to use type synonyms where possible to
maintain the readability of our code.

Cedille's syntax distinguishes type application from
term application, where type application uses a center dot. For
example, in the paper we would see `Id AppV AppL`, whereas in the
formalization we see `Id · AppV · AppL`. Erased term (rather than
type) arguments (mostly omitted/inferred in the paper) are given via a
dash. For example, `v2l! xs` in the paper becomes `v2l! · A -n xs` in
the formalization.

Finally, you may be interested in reading README.md for an overview of
the directory structure of the code, including files and definitions
that the paper assumes to exist (e.g. `code/Datatypes/Vec.ced`).
However, understanding the directory structure and extra files is not
necessary to evaluate our artifact, and the instructions below are
sufficient. 

Type of Dependent Identity Functions
------------------------------------

The file `code/Base/Id.ced` contains the following dependent identity
function (Section 4.1) definitions: `IdDep`, `intrIdDep`,
`elimIdDep`. It also contains the following non-dependent
counterparts: `Id`, `intrId`, `elimId`.

Note that `elimIdDep` is defined in terms of the more general
`elimIdDep~` (not in the paper), which allows the eliminated `IdDep`
argument to be erased.

Forgetful Program & Proof Reuse Combinators
-------------------------------------------

File `code/GenericReuse/FogFun.ced` contains the
forgetful program (non-dependent function) reuse combinator
`allArr2arr` (Section 4.2.1) and the forgetful proof
(dependent function) reuse combinator `allPi2pi` (Section 4.2.3). Note
that these are defined in terms of more general "prime" versions of
the  combinators: ``allArr2arr'` and `allPi2pi'`. However, inlining
the prime definitions results in the definitions of the paper.

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
4. Enriching proof reuse `assocL2assocV` (Section 4.3.3).

Note that these examples make extensive use of type synonyms to break
apart a type into the various pieces that would be inferred by a more
advantaged implementation of Cedille, e.g. AppV1 through AppV3,
AssocV1 through AssocV4, etc.

Data Reuse Examples
-------------------

File `code/Examples/ListVecReuse.ced` contains examples of reusing
lists and vectors:
1. Forgetful reuse of vectors as lists `v2l` & `vf2lf` (Section 5.3.2)
2. Enriching reuse of lists as vectors `l2v` & `lf2vf` (Section 5.5.2)

Identity Mappings
-----------------

File `code/IndexedMendlerInduction/IIdMapping.ced` contains the
non-indexed and indexed types of identity mappings (Section 5.1),
`IdMapping` and `IIdMapping`, respectively.

Files `code/Datatypes/ListF.ced` and `code/Datatypes/VecF.ced` contain
the list and vector schemes (Figure 3) and identity mappings (Section 5.2),
`ListF` & `imapL` and `VecF` & `imapV`, respectively.

Auxiliary Combinators
---------------------

File `code/GenericReuse/Aux.ced` contains the auxiliary combinators
from Figure 2 in the paper: `id`, `copyType`, `copyTypeP`, and `subst`
(as well as others not in the paper).

Part 3: Mandatory Revisions
===========================






