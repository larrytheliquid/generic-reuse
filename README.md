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
* [Function Types (forgetful)](code/Datatypes/FogFun.ced)
* [Function Types (enriching)](code/Datatypes/EnrFun.ced)
* [Fixpoint Types (forgetful)](code/Datatypes/FogFix.ced)
* [Fixpoint Types (enriching)](code/Datatypes/EnrFix.ced)

[Datatypes](code/Datatypes)
---------------------------

This directory includes the algebraic list and vector datatypes,
and their schemes, defined using generic Mendler-style fixpoints:
* [List Scheme (ListF)](code/Datatypes/ListF.ced)
* [List](code/Datatypes/List.ced)
* [Vec Scheme (VecF)](code/Datatypes/VecF.ced)
* [Vec](code/Datatypes/Vec.ced)

[IndexedMendlerInduction](code/IndexedMendlerInduction)
-------------------------------------------------------

This directory imports the generic datatype development
(via efficient Mendler-style fixpoints) by
[Firsov et al.](https://arxiv.org/abs/1803.02473):
* [Non-Indexed Fixpoints (FixIndM)](code/IndexedMendlerInduction/FixIndM.ced)
* [Indexed Fixpoints (IFixIndM)](code/IndexedMendlerInduction/IFixIndM.ced)
* [Identity Mappings (IIdMapping)](code/IndexedMendlerInduction/IIdMapping.ced)

[Base](code/Base)
-----------------

This directory includes base or "prelude" definitions,
like the [Unit](code/Base/Unit.ced) and [Sigma](code/Base/Sigma.ced) types.
It also includes [IdDep](code/Base/Id.ced),
the type of dependent identity functions.

