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
with the cursor on a node), and how to unfocus a node (by pressing `g`).

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

Finally, you may be interested in reading README.md for an overview of
the directory structure of the code, including files and definitions
that the paper assumes to exist (e.g. `code/Datatypes/Vec.ced`).
However, understanding the directory structure and extra files is not
necessary to evaluate our artifact, and the instructions below are
sufficient. 

Section 4.1: Type of Dependent Identity Functions
-------------------------------------------------

The file `code/Base/Id.ced` contains the following dependent identity
function definitions: `IdDep`, `intrIdDep`, `elimIdDep`. It also
contains the following non-dependent counterparts: `Id`, `intrId`,
`elimId`.

Note that `elimIdDep` is defined in terms of the more general
`elimIdDep~` (not in the paper), which allows the eliminated `IdDep`
argument to be erased.


Part 3: Mandatory Revisions
===========================






