Generic Zero-Cost Reuse for Dependent Types
===========================================

Cedille code accompanying the paper draft
([available on arXiv](https://arxiv.org/abs/1803.08150)) 
authored by Larry Diehl, Denis Firsov, and Aaron Stump.

This is the generic version of our
previous [manual reuse](https://github.com/larrytheliquid/zero-cost-coercions)
work, where identity functions are defined via definitional equality, 
rather than propositional equality.

[GenericReuse](code/GenericReuse)
---------------------------------

This directory includes our primary contributions,
the generic zero-cost reuse combinators for the following types:
* [Functions (forgetful `allArr2arr` & `allPi2pi`)](code/GenericReuse/FogFun.ced)
* [Functions (enriching `arr2allArrP` & `pi2allPiP`)](code/GenericReuse/EnrFun.ced)
* [Fixpoints (forgetful `ifix2fix`)](code/GenericReuse/FogFix.ced)
* [Fixpoints (enriching `fix2ifix`)](code/GenericReuse/EnrFix.ced)

[Datatypes](code/Datatypes)
---------------------------

This directory includes the algebraic list and vector datatypes,
and their schemes, defined using generic Mendler-style fixpoints:
* [Lists Scheme (`ListF`)](code/Datatypes/ListF.ced)
* [Lists (`List`)](code/Datatypes/List.ced)
* [Vectors Scheme (`VecF`)](code/Datatypes/VecF.ced)
* [Vectors (`Vec`)](code/Datatypes/Vec.ced)

[IndexedMendlerInduction](code/IndexedMendlerInduction)
-------------------------------------------------------

This directory imports the generic datatype development
(via efficient Mendler-style fixpoints) by
[Firsov et al.](https://arxiv.org/abs/1803.02473):
* [Non-Indexed Fixpoints (`FixIndM`)](code/IndexedMendlerInduction/FixIndM.ced)
* [Indexed Fixpoints (`IFixIndM`)](code/IndexedMendlerInduction/IFixIndM.ced)
* [Identity Mappings (`IIdMapping`)](code/IndexedMendlerInduction/IIdMapping.ced)

[Base](code/Base)
-----------------

This directory includes base or "prelude" definitions,
like the [`Unit`](code/Base/Unit.ced) and [`Sigma`](code/Base/Sigma.ced) types.
It also includes [`IdDep`](code/Base/Id.ced),
the type of dependent identity functions.

