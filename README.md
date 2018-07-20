Generic Zero-Cost Reuse for Dependent Types
===========================================

Cedille code accompanying the paper draft
([available on arXiv](https://arxiv.org/abs/1803.08150)) 
authored by Larry Diehl, Denis Firsov, and Aaron Stump.

This is the generic version of our
previous [manual reuse](https://github.com/larrytheliquid/zero-cost-coercions)
work, where identity functions are defined via definitional equality, 
rather than propositional equality.

We describe the directories containing our code below. As in the paper,
program reuse corresponds to non-dependent function type reuse,
proof reuse corresponds to dependent function type reuse,
and data reuse corresponds to fixpoint type reuse.

[GenericReuse](code/GenericReuse)
---------------------------------

This directory includes our primary contributions,
the generic zero-cost reuse combinators for the following types:
* [Functions (forgetful `allArr2arr` & `allPi2pi`)](code/GenericReuse/FogFun.ced)
* [Functions (enriching `arr2allArrP` & `pi2allPiP`)](code/GenericReuse/EnrFun.ced)
* [Fixpoints (forgetful `ifix2fix`)](code/GenericReuse/FogFix.ced)
* [Fixpoints (enriching `fix2ifix` & `fix2ifixP`)](code/GenericReuse/EnrFix.ced)

The [auxiliary combinators](code/GenericReuse/Aux.ced) also appear here.

[Examples](code/Examples)
---------------------------------

This directory includes reuse examples via our combinators:
* [Program Reuse of append and Proof Reuse of associativity](code/Examples/AppendReuse.ced)
  * forgetful `appV2appL` & enriching `appL2appV`
  * forgetful `assocV2assocL` & enriching `assocL2assocV`
* Data Reuse of vectors and lists
  * [Forgetful `v2l`](code/Examples/VecListReuse.ced)
  * [Enriching `l2v`](code/Examples/ListVecReuse.ced)
* Data Reuse of unchecked/raw and checked/typed STLC terms
  * [Forgetful `t2r`](code/Examples/TermRawReuse.ced)
  * [Enriching `r2tP`](code/Examples/RawTermReuse.ced)
* [Program Reuse of STLC step function (enriching `stepR2stepT`)](code/Examples/StepReuse.ced)
* [Program Reuse of STLC substitution function (enriching `subR2subT`)](code/Examples/SubReuse.ced)

[Datatypes](code/Datatypes)
---------------------------

This directory includes the algebraic list and vector datatypes,
and their schemes, defined using generic Mendler-style fixpoints:
* [Lists Scheme (`ListF`)](code/Datatypes/ListF.ced)
* [Lists (`List`)](code/Datatypes/List.ced)
* [Vectors Scheme (`VecF`)](code/Datatypes/VecF.ced)
* [Vectors (`Vec`)](code/Datatypes/Vec.ced)
* [Raw Terms Scheme (`RawF`)](code/Datatypes/RawF.ced)
* [Raw Terms (`Raw`)](code/Datatypes/Raw.ced)
* [Typed Terms Scheme (`TermF`)](code/Datatypes/TermF.ced)
* [Typed Terms (`Term`)](code/Datatypes/Term.ced)

The derived definition of [`Nat`](code/Datatypes/Nat.ced)
(in terms of the scheme [`NatF`](code/Datatypes/NatF.ced))
also appears here, as well the types [`Tp`](code/Datatypes/Tp.ced)
of STLC (and their scheme [`TpF`](code/Datatypes/TpF.ced)).

[IndexedMendlerInduction](code/IndexedMendlerInduction)
-------------------------------------------------------

This directory imports the generic datatype development
(via efficient Mendler-style fixpoints) by
[Firsov et al.](https://arxiv.org/abs/1803.02473):
* [Non-Indexed Fixpoints (`FixIndM`)](code/IndexedMendlerInduction/FixIndM.ced)
* [Indexed Fixpoints (`IFixIndM`)](code/IndexedMendlerInduction/IFixIndM.ced)
* [Identity Mappings (`IIdMapping`)](code/IndexedMendlerInduction/IIdMapping.ced)

It also includes the generic derivation of [induction (`iindFixIndM`)](code/IndexedMendlerInduction/IInductionM.ced),
as well as other technical devices.

[Base](code/Base)
-----------------

This directory includes base or "prelude" definitions,
like the [`Unit`](code/Base/Unit.ced) and [`Sigma`](code/Base/Sigma.ced) types.
It also includes [`IdDep`](code/Base/Id.ced),
the type of dependent identity functions.

