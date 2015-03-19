##PROCEDURE(help) DifferentialGeometry[LieAlgebras][Query]
##TITLE(halfline="check various properties of a Lie algebra, subalgebra, or transformation") LieAlgebras[Query]
##
##CALLINGSEQUENCE
##- Query(arg1, arg2, ..., keyword)
##
##PARAMETERS
##- 'arg1, arg2, ...' : (optional) other arguments
##- 'keyword' : keyword string
##
##DESCRIPTION
##- The `Query` function can be used in one of two ways to check various properties of a Lie algebra, subalgebra, or transformation.  
## In the first way the function simply returns true if the property defined by the keyword holds and false otherwise. 
## In the second way, a set of parameters is specified and the function returns the following sequence - `TF`, `Eq`, `Soln`, `A`. 
## Here `TF` is true if there is a choice of the parameters which makes the keyword property true; `Eq` is the list of equations which the parameters 
## must satisfy for the property defined by the keyword to be be true; `Soln` is the list of all solutions to the equations as found by the Maple solve command; 
## and `A` is the list of all algebraic structures defined by the previously listed solutions.
##- The argument keyword must be one of the following, entered as a string (in quotes "  "):
##TABLE(width = 575, border = 0, alignment = center, colwidth = 10|12|10)
##ROW " Abelian" | "AbsolutelyIndecomposable"  | "Derivation"  
##ROW "CartanDecomposition" |"CartanInvolution" | "CartanSubalgebra"
##ROW "ClosedUnderConjugation" | "ClosedUnderHermitianTransposition" | "ClosedUnderTransposition" 
##ROW "Derivation" | "DirectSumDecomposition" | "Filtration" 
##ROW "Gradation" | "Homomorphism" | "Ideal"
##ROW "Indecomposable" | "InvariantSubspace" | "Jacobi"
##ROW "Keywords" | "LeviDecomposition" | "MatrixAlgebra"
##ROW "NaturallyReductivePair" | "NilRepresentation" | "Nilpotent" 
##ROW "Parabolic" | "ReductivePair" |"RegularElement"
##ROW "Representation" | "RootSpaceDecomposition" | "Semisimple" 
##ROW "Solvable" | "SolvableRepresentation" | "Subalgebra"
##ROW "SymmetricPair" | `` | ``
##ENDTABLE
##- Further information is available under ?Query[keyword], where keyword is from the above list.
##- A user can add new functionality to `Query` with the command `Query:-addCheck(keyword, procedure)`.
##- The command `Query` is part of the `DifferentialGeometry:-LieAlgebras` package.  
## It can be used in the form Query(...) only after executing the commands with(DifferentialGeometry) and with(LieAlgebras), 
## but can always be used by executing DifferentialGeometry:-LieAlgebras:-Query(...).  
##
##EXAMPLES
##
##> with(DifferentialGeometry): with(LieAlgebras):
##-(lead=indent) Define two Lie algebras.
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[1, 3, 1], 1], [[2, 3, 2], 1]]]):
##> L2 := _DG([["LieAlgebra", Alg2, [3]], [[[2, 3, 1], 1]]]):
##> DGsetup(L1): DGsetup(L2, [f], [alpha]):
##
##-(lead=indent) **Example 1.**
##> Query(Alg1, "Nilpotent");
##< false
##> Query(Alg2, "Nilpotent");
##< true
##> Query([e1, e2], "Ideal");
##< true
##> Query([e1, e2+a*e4], {a}, "Ideal");
##<(quote) true, {0, -a}, [{a = 0}], [[e1, e2]]
##
##-(lead=indent) **Example 2.**
##-(lead=indent) In this example we find all the homomorphisms from Alg1 to Alg2 of the form defined by the Matrix A.
##> A := Matrix([[a6, 0, 0, a1], [0, a5, 0, a2], [0, 0, a4, a3]]); 
##<(verification="(x, y) -> LinearAlgebra:-Equal(x, y)") Matrix(3, 4, {(1, 1) = a6, (1, 2) = 0, (1, 3) = 0, (1, 4) = a1, (2, 1) = 0, (2, 2) = a5, (2, 3) = 0, (2, 4) = a2, (3, 1) = 0, (3, 2) = 0, (3, 3) = a4, (3, 4) = a3})
##> TF, Eq, Soln, B := Query(Alg1, Alg2, A, {a1, a2, a3, a4, a5, a6}, "Homomorphism");
##<(verification="proc(x,y) local n, i; if not x::list(Matrix) then if x <>y then return(false) fi;  else n := nops(x); for i from 1 to n do if not LinearAlgebra:-Equal(x[i], y[i]) then return false fi;od fi; true; end") op([true, {0, a5, a6, a4*a2, a5*a3, a5*a4, -a5, -a6, -a4*a2, -a5*a3, -a5*a4}, [{a1 = a1, a2 = a2, a3 = a3, a4 = 0, a5 = 0, a6 = 0}, {a1 = a1, a2 = 0, a3 = a3, a4 = a4, a5 = 0, a6 = 0}], [Matrix(3, 4, [[0,0,0,a1],[0,0,0,a2],[0,0,0,a3]]), Matrix(3, 4, [[0,0,0,a1],[0,0,0,0],[0,0,a4,a3]])]])
##-(lead=indent) **Example 3.**
##-(lead=indent) In this example we add functionality to `Query`. Recall that a Lie algebra is said to be a two-step nilpotent Lie algebra if the second term in the 
## lower central series vanishes. We create a procedure that returns `true` if the given Lie algebra is two-step nilpotent and `false` otherwise.
##>> f := proc() local C, k;
##>> if nargs = 1 then ChangeLieAlgebraTo(args[1]) end if;
##>> C := LieAlgebraSeries("Lower");
##>> k := nops(C[3]);
##>> if k = 0 then true else false end if;
##>> end:
##-(lead=indent) Add this procedure to the `Query` command.
##> Query:-addCheck("two-step", f);
##< f
##> Query(Alg1, "two-step");
##< false  
##> Query(Alg2, "two-step");
##< false
##-(lead=indent) Note that `"two-step"` has now been added to the keywords list for `Query`.
##> Query("Keywords");
##< ["Abelian", "AbsolutelyIndecomposable", "AscendingIdealsBasis", "Associative", "CartanDecomposition", "CartanInvolution", "CartanSubalgebra", "ChevalleyBasis", "ClosedUnderConjugation", "ClosedUnderHermitianTransposition", "ClosedUnderTransposition", "Commutative", "CompactForm", "Derivation", "DirectSumDecomposition", "Filtration", "Gradation", "Homomorphism", "Ideal", "Indecomposable", "IntegerStructureConstants", "InvariantSubspace", "Jacobi", "Keywords", "LeviDecomposition", "MatrixAlgebra", "NaturallyReductivePair", "NilRepresentation", "Nilpotent", "Normalizer", "Parabolic", "ReductivePair", "RegularElement", "Representation", "RootSpaceDecomposition", "Semisimple", "SkewCommutative", "Solvable", "SolvableRepresentation", "SplitForm", "Subalgebra", "SymmetricPair", "two-step"]
##
##SEEALSO
##- "DifferentialGeometry", "LieAlgebras"
##
##XREFMAP
##- "long form" : Help:UsingPackages#longform
##- "short form" : Help:UsingPackages#shortform
##- "Abelian" : Help:DifferentialGeometry[LieAlgebras][Query][Abelian]
##- "Indecomposible" : Help:DifferentialGeometry[LieAlgebras][Query][Indecomposable]
##- "Derivation" : Help:DifferentialGeometry[LieAlgebras][Query][Derivation]
##- "DirectSumDecomposition" : Help:DifferentialGeometry/LieAlgebras/Query/DirectSumDecomposition
##- "Flitration" : Help:DifferentialGeometry[LieAlgebras][Query][Filtration]
##- "Gradation" : Help:DifferentialGeometry[LieAlgebras][Query][[Gradation]
##- "Homomorphism" : Help:DifferentialGeometry[LieAlgebras][Query][Homomorphism]
##- "Ideal" : Help:DifferentialGeometry[LieAlgebras][Query][Ideal]
##- "Indecomposable" : Help:DifferentialGeometry[LieAlgebras][Query][Indecomposable] 
##- "Jacobi" : Help:DifferentialGeometry[LieAlgebras][Query][Jacobi]
##- "Keywords" : Help:DifferentialGeometry[LieAlgebras][Query][Keywords] 
##- "LeviDecomposition" : Help:DifferentialGeometry[LieAlgebras][Query][LeviDecomposition]
##- "NaturallyReductivePair" : Help:DifferentialGeometry[LieAlgebras][Query][NaturallyReductivePair]
##- "Nilpotent" : Help:DifferentialGeometry[LieAlgebras][Query][Nilpotent]
##- "ReductivePair" : Help:DifferentialGeometry[LieAlgebras][Query][ReductivePair]
##- "Semisimple" : Help:DifferentialGeometry[LieAlgebras][Query][Semisimple]
##- "Solvable" : Help:DifferentialGeometry[LieAlgebras][Query][Solvable]
##- "Subalgebra" : DifferentialGeometry[LieAlgebras][Query][Subalgebra]
##- "SymmetryPair" : DifferentialGeometry[LieAlgebras][Query][SymmetricPair]
##- "DifferentialGeometry" : Help : DifferentialGeometry
##- "DifferentialGeometry" : Help : DifferentialGeometry[LieAlgebras]
