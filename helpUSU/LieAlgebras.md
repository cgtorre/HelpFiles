##PROCEDURE(help) DifferentialGeometry[LieAlgebras]
##TITLE  Overview of the LieAlgebras package
##DESCRIPTION
##- Lie groups and Lie algebras play an essential part in differential geometry and its applications. 
## For this reason the "DifferentialGeometry package provides Maple users with the `LieAlgebra` package.
##- The `LieAlgebra` package contains a large number of commands for defining Lie algebras from a variety of sources and 
## for creating new Lie algebras from existing Lie algebras.  These include "DirectSum", "Extension", "LieAlgebraData", "MatrixAlgebras", 
## "QuotientAlgebra", "SimpleLieAlgebraData", "SemiDirectSum". Especially noteworthy is the use of the "LieAlgebraData" command to 
## convert a Lie algebra of vector fields on a manifold to an abstract Lie algebra.
##- The general structure of the Lie algebra can be investigated with the "Decompose", "Query", "Series", "Nilradical", and "Radical" commands.
##- The structure of a semi-simple Lie algebra can be explored with the commands "CartanDecomposition", "CartanSubalgebra", "CartanMatrix", "CompactRoots", "PositiveRoots",  "RootSpaceDecomposition", "RestrictedRootSpaceDecomposition", "SimpleLieAlgebraProperties", "SimpleRoots".
##- Homomorphisms between Lie algebras can be constructed using the DifferentialGeometry command "Transformation".  
##- The matrix exponential of any "derivation" of a Lie algebra will define an automorphism of that Lie algebra.
##- Structure equations for general more general algebras such as the quaternions, octonions, Jordan algebras and Clifford algebras are available.  See "AlgebraData" and "AlgebraLibraryData".
##- Cohomology of Lie algebras can be computed with the commands "Cohomology", "CohomologyDecomposition", "KostantCodifferential", "KostantLaplacian".
##- Deformations of Lie algebras can be studied with the commands "Deformation" amd "MasseyProduct".  
##- Lie algebras can be prolonged with "TanakaProlongation". 
##- Properties of Lie subalgebras can also be investigated with the "Query" command.
##- The `LieAlgebra` "Lessons" provide a systematic introduction to the commands in the LieAlgebra  package.
##- The `LieAlgebra` package is a subpackage of the "DifferentialGeometry" package. 
## Each command in the LieAlgebras package can be accessed by using either the "long form" or the "short form" of the command name in the command calling sequence.
##
##SECTION Commands for creating Lie algegbras
#["Complexify", "DirectSum", "Extension",  "LieAlgebraData", "LieAlgebraWithCoefficientsData",  "QuotientAlgebra", "SemiDirectSum",   "SimpleLieAlgebraData", "SymbolAlgebra"]
##TABLE(width = 550, border = 0, alignment = center, colwidth = 1|1|1) 
##ROW "Complexify" | "DirectSum" | "Extension"
##ROW "LieAlgebraData" | "LieAlgebraWithCoefficientsData" | "QuotientAlgebra"
##ROW "SemiDirectSum" | "SimpleLieAlgebraData" | "SymbolAlgebra"
##ENDTABLE
##
##- "Complexify": find the complexification of a Lie algebra.
##- "DirectSum": create the direct sum of a list of Lie algebras.
##- "Extension": calculate a right or a central extension of a Lie algebra.
##- "LieAlgebraData": convert different realizations of a Lie algebra to a Lie algebra data structure.
##- "LieAlgebraWithCoefficientsData": calculate the structure equations for a Lie algebra with coefficients in a representation.
##- "QuotientAlgebra": create the Lie algebra data structure for a quotient algebra of a Lie algebra by an ideal.
##- "SemiDirectSum": create the semi-direct product of two Lie algebras.
##- "SimpleLieAlgebraData": obtain the structure equations for a classical matrix Lie algebra.
##- "SymbolAlgebra": find the symbol algebra for a distribution.
##
##SECTION Commands for finding subalgebras
##TABLE(width = 550, border = 0, alignment = center, colwidth = 1|1|1) 
##ROW "Center" | "Centralizer" | "DerivedAlgebra" 
##ROW "GeneralizedCenter" | "HomomorphismSubalgebras" | "MinimalIdeal" 
##ROW "MinimalSubalgebra" | "Nilradical" | "ParabolicSubalgebra" 
##ROW "ParabolicSubalgebraRoots" | "Radical" | "Series"
##ROW "SubalgebraNormalizer"  | `` | ``
##ENDTABLE
##
##- "Center": find the center of a Lie algebra.
##- "Centralizer": find the centralizer of a list of vectors.
##- "DerivedAlgebra": find the derived algebra of a Lie algebra.
##- "HomomorphismSubalgebras": find the kernel or image of a Lie algebra homomorphism.
##- "GeneralizedCenter": calculate the generalized center of an ideal in a Lie algebra.
##- "Nilradical": find the nilradical of a Lie algebra.
##- "ParabolicSubalgebra": find the parabolic subalgebra defined by a set of simple roots or a set of restricted simple roots.
##- "ParabolicSubalgebraRoots": find the simple roots which generate a parabolic subalgebra
##- "Radical": find the radical of a Lie algebra.
##- "Series": find the derived series, lower central series, upper central series of a Lie algebra or a Lie subalgebra.
##- "SubalgebraNormalizer": find the normalizer of a subalgebra.
##
##
##SECTION Commands for working with mappings of Lie algebras
##TABLE(width = 550, border = 0, alignment = center, colwidth = 1|1|1) 
##ROW "Adjoint" | "AdjointExp" | "ApplyHomomorphism"  
##ROW "Derivations" | ``  | ``
##ENDTABLE
##
##- "Adjoint": find the Adjoint Matrix for a vector in a Lie algebra.
##- "AdjointExp": find the Exponential of the Adjoint Matrix for a vector in a Lie algebra.
##- "ApplyHomomorphism": apply a Lie algebra homomorphism to a vector, form or tensor.
##- "Derivations": find the inner and/or outer derivations of a Lie algebra.
##
##
##SECTION Utilities
##TABLE(width = 550, border = 0, alignment = center, colwidth = 1|1|1) 
##ROW "BracketOfSubspaces" | "ChangeLieAlgebraTo" | "InfinitesimalCoadjointAction" 
##ROW "Killing" | "KillingForm" | "MultiplicationTable"     
##ROW "Query" | `` | `` 
##ENDTABLE
##
##- "BracketOfSubspaces": find the subspace generated by the bracketing of two subspaces.
##- "ChangeLieAlgebraTo": change the current frame to the frame for a Lie algebra.
##- "InfinitesimalCoadjointAction": find the vector fields defining the infinitesimal co-adjoint action of a Lie group on its Lie algebra.
##- "Killing": find the Killing form of a Lie algebra.
##- "KillingForm": find the Killing form, defined as a tensor, of a Lie algebra.
##- "MultiplicationTable": display the multiplication table of a Lie algebra.
##- "Query": check various properties of a Lie algebra, subalgebra, or transformation.
##
##
##SECTION Commands for general structure theory of Lie algebras
##TABLE(width = 550, border = 0, alignment = center, colwidth = 1|1|1) 
##ROW "Decompose"  | "LeviDecomposition" | ``
##ENDTABLE
##- "Decompose": decompose a Lie algebra into a direct sum of indecomposable Lie algebras.
##- "LeviDecomposition": compute the Levi decomposition of a Lie algebra.
##
##
##SECTION Commands for studying semi-simple Lie algebras
#["CartanDecomposition", "CartanInvolution",  "CartanMatrix", "CartanMatrixToStandardForm", "CartanSubalgebra", "ChevalleyBasis", "CompactRoots", "CoRoot", "GradeSemiSimpleLieAlgebra", "LieAlgebraRoots", "PositiveRoots", "RestrictedRootSpaceDecomposition", 
# "RootSpace", "RootSpaceDecomposition", "RootString",  "RootToCartanSubalgebraElementH", "SatakeAssociate", "SatakeDiagram", "SplitAndCompactForms"]
##TABLE(width = 625, border = 0, alignment = center, colwidth = 1|1|1) 
##ROW "CartanDecomposition" | "CartanInvolution" | "CartanMatrix"
##ROW "CartanMatrixToStandardForm" | "CartanSubalgebra" | "ChevalleyBasis"
##ROW "CompactRoots" | "CoRoot" | "GradeSemiSimpleLieAlgebra"
##ROW "LieAlgebraRoots" | "PositiveRoots" | "RestrictedRootSpaceDecomposition"
##ROW "RootSpace" | "RootSpaceDecomposition" | "RootString"
##ROW "RootToCartanSubalgebraElementH" | "SatakeAssociate" | "SatakeDiagram"
##ROW "SplitAndCompactForms" | `` | ``
##ENDTABLE 
##- "CartanDecomposition": find the Cartan decomposition defined by a Cartan involution, find the Cartan decomposition of a semi-simple matrix algebra.
##- "CartanInvolution": find the Cartan involution defined by a Cartan decomposition of a non-compact, semi-simple, real Lie algebra.
##- "CartanMatrix": find the Cartan matrix for a simple Lie algebra from a root space decomposition, display the Cartan matrix for a given root type.
##- "CartanMatrixToStandardForm": transform a Cartan matrix to standard form.
##- "CartanSubalgebra": find a Cartan subalgebra of a Lie algebra.
##- "ChevalleyBasis": find the Chevalley basis for a real, split semi-simple Lie algebra.
##- "CompactRoots": find the compact roots in a root system for a non-compact semi-simple real Lie algebra.
##- "CoRoot": find the coroot of a root vector for a semi-simple Lie algebra.
##- "GradeSemiSimpleLieAlgebra": find the grading of a semi-simple Lie algebra defined by a set of simple roots or restricted simple roots.
##- "LieAlgebraRoots": find a root or the roots for a semi-simple Lie algebra from a root space and a Cartan subalgebra; or from a root space decomposition.
##- "PositiveRoots": find the positive roots from a set of roots or a root space decomposition, list the positive roots for a given root type.
##- "RestrictedRootSpaceDecomposition": find the real root space decomposition of a non-compact semi-simple Lie algebra with respect to an Abelian subalgebra.
##- "RootSpaceDecomposition": find the root space decomposition for a semi-simple Lie algebra from a Cartan subalgebra. 
##- "RootString": find the sequence of roots through a given root of a semi-simple Lie algebra.
##- "RootToCartanSubalgebraElementH" : associate to each positive root of a simple Lie algebra a vector in the Cartan subalgebra.
##- "SatakeAssociate" : find the non-compact simple root associated to a given non-compact root in the Satake diagram.	
##- "SatakeDiagram": display the Satake diagram for a non-compact, real,  simple matrix algbra.
##- "SimpleLieAlgebraProperties": provide a table of properties for any real simple Lie algebra.
##- "SimpleRoots": find the simple roots for a set of  positive roots.
##- "SplitAndCompactForms": find the real split and real compact forms of a real semi-simple Lie algebra.
##
##
##SECTION Commands for calculating Lie algebra cohomology
#["Codifferential", "Cohomology", "CohomologyDecomposition", "KostantCodifferential", "KostantLaplacian", "RelativeChains"]
##TABLE(width = 500, border = 0, alignment = center, colwidth = 1|1|1) 
##ROW "Codifferential" | "Cohomology" | "CohomologyDecomposition"
##ROW "KostantCodifferential" | "KostantLaplacian" | "RelativeChains"
##ENDTABLE
#
##- "Codifferential": calculate the codifferential of a multi-vector defined on a Lie algebra with coefficients in a representation.
##- "Cohomology": find the cohomology of a Lie algebra.
##- "CohomologyDecomposition": decompose a closed form into the sum of an exact form and a form defining a coholomogy class.
##- "KostantCodifferential": calculate the Kostant co-differential of a p-form or a list of p-forms defined on a nilpotent Lie algebra with coefficients in a representation.
##- "KostantLaplacian": calculate the Kostant Laplacian of a form defined on a nilpotent Lie algebra with coefficients in a representation.
##- "PositiveDefiniteMetricOnRepresentationSpace":  find a positive-definite inner product on a representation space which is compatible with a Cartan involution.
##- "RelativeChains": find the vector space of forms on a Lie algebra relative to a given subalgebra.
##
##
##SECTION Commands for calculating deformations of Lie algebras
##TABLE(width = 450, border = 0, alignment = center, colwidth = 1|1|1) 
##ROW "Deformation" | "MasseyProduct" | ``
##ENDTABLE
##- "Deformation": find the deformation of a Lie algebra defined by a list of 2-forms.
##- "MasseyProduct": calculate the Massey product of a pair of forms.
##
##	
##SECTION Commands for working with matrix algebras
##TABLE(width = 550, border = 0, alignment = center, colwidth = 1|1|1) 
##ROW "JacobsonRadical" | "MatrixAlgebras" | "MatrixCentralizer"
##ROW "MatrixNormalizer" | "MatrixSubalgebra" | ``
##ENDTABLE
##- "JacobsonRadical": find the Jacobson radical for a matrix Lie algebra.
##- "MatrixAlgebras": create a Lie algebra data structure for a matrix Lie algebra.
##- "MatrixCentralizer": find the matrix centralizer of a list of matrices.
##- "MatrixNormalizer": find the matrix normalizer of a list of matrices.
##- "MatrixSubalgebra": find the subalgebra of a Lie algebra which preserves a collection of tensors or subspaces of tensors.
##- "MinimalIdeal": find the smallest ideal containing a given set of vectors.
##- "MinimalSubalgebra": find the smallest subalgebra containing a given set of vectors.
##
##
##SECTION Commands for working with general algebras algebras
#[AlgebraData, AlgebraLibraryData, AlgebraNorm, AlgebraInverse, JordanMatrices, JordanProduct]
##TABLE(width = 450, border = 0, alignment = center, colwidth = 1|1|1) 
##ROW  "AlgebraData" | "AlgebraLibraryData" | "AlgebraNorm"
##ROW  "AlgebraInverse" | "JordanMatrices" | "JordanProduct"
##ENDTABLE
##- "AlgebraData": find the structure equations for a real algebra defined by a list of matrices and a multiplication procedure.
##- "AlgebraLibraryData": retrieve the structure equations for various classical algebras (quaternions, octonions, Clifford algebras, and low dimensional Jordan algebras).
##- "AlgebraNorm":  find the norm of a quaternion or octonion.
##- "AlgebraInverse": find the multiplicative inverse of a quaternion or octonion.	
##- "JordanMatrices": find a basis for a Jordan algebra of matrices.
##- "JordanProduct": find the Jordan product of two Jordan matrices.	
##
##
##SECTION Commands for working with representations of Lie algebras
#["ApplyRepresentation", "AscendingIdealsBasis", "ChangeRepresentationBasis", "DirectSumOfRepresentations", "Invariants", "QuotientRepresentation", "Representation",  "RepresentationEigenvector",  "RestrictedRepresentation", "SolvableRepresentation", "StandardRepresentation", "SubRepresentation", "TensorProductOfRepresentations"
##TABLE(width = 575, border = 0, alignment = center, colwidth = 1|1|1) 
##ROW  "ApplyRepresentation" | "AscendingIdealsBasis" | "ChangeRepresentationBasis"
##ROW  "DirectSumOfRepresentations" | "Invariants" | "QuotientRepresentation"
##ROW  "Representation" | "RepresentationEigenvector" | "RestrictedRepresentation"
##ROW  "SolvableRepresentation" | "StandardRepresentation" | "SubRepresentation"
##ROW  "TensorProductOfRepresentations" | `` | ``
##ENDTABLE
##- "ApplyRepresentation": apply a Lie algebra representation to a vector in a Lie algebra.
##- "AscendingIdealsBasis":  find a basis for a solvable Lie algebra which defines an ascending chain of ideals.
##- "ChangeBasis": change the basis for a representation, either in the Lie algebra or in the representation space.
##- "Invariants": calculate the invariant vectors and tensors for a representation of a Lie algebra
##- "Representation": define a representation of a Lie algebra.
##- "RepresentationEigenvector": find a simultaneous eigenvector for the representation of a solvable Lie algebra.
##- "RestrictedRepresentation" : find the restriction of a representation of a subalgebra.
##- "SolvableRepresentation": given a representation of a solvable algebra, find a basis for the representation space in which the representation matrices are Upper triangular matrices. 
##- "StandardRepresentation": find the standard matrix representation or linear vector field representation of a classical matrix algebra.
##- "SubRepresentation": find the induced representation on an invariant subspace.
##- "TensorProduct": form a tensor product representation from a list of representations. 
##
##
##SECTION Commands for working with prolongations of Lie algebras
##TABLE(width = 475, border = 0, alignment = center, colwidth = 10|10|12) 
##ROW "ChangeGradedComponent" | "Rank1Element" | "TanakaProlongation"
##ENDTABLE
##- "ChangeGradedComponent" :  change one or more components of a graded Lie algebra.
##- "Rank1Elements" : calculate the rank 1 matrices in the span of a given list of matrices.
##- "TanakaProlongation" : calculate the Tanaka prolongation, to a specified order, of a graded nilpotent Lie algebra.	
##
##SECTION Alphabetical listing of all LieAlgebra commands 
##TABLE(width = 675, border = 0, alignment = center, colwidth = 10|10|12) 
##ROW "Adjoint" | "AdjointExp" | "AlgebraData"
##ROW "AlgebraInverse" | "AlgebraLibraryData" | "AlgebraNorm"
##ROW "ApplyHomomorphism" | "ApplyRepresentation" | "AscendingIdealsBasis"
##ROW "BracketOfSubspaces" | "CartanDecomposition" | "CartanInvolution"
##ROW "CartanMatrix" | "CartanMatrixToStandardForm" | "CartanSubalgebra"
##ROW "Center" | "Centralizer" | "ChangeGradedComponent"
##ROW "ChangeLieAlgebraTo" | "ChangeRepresentationBasis" | "ChevalleyBasis"
##ROW "CoRoot" | "Codifferential" | "Cohomology"
##ROW "CohomologyDecomposition" | "CompactRoots" | "Complexify"
##ROW "Decompose" | "Deformation" | "Derivations"
##ROW "DerivedAlgebra" | "DirectSum" | "DirectSumOfRepresentations"
##ROW "DynkinDiagram" | "Extension" | "GeneralizedCenter"
##ROW "GradeSemiSimpleLieAlgebra" | "HomomorphismSubalgebras" | "InfinitesimalCoadjointAction"
##ROW "Invariants" | "JacobsonRadical" | "JordanMatrices"
##ROW "JordanProduct" | "Killing" | "KillingForm"
##ROW "KostantCodifferential" | "KostantLaplacian" | "LeviDecomposition"
##ROW "LieAlgebraData" | "LieAlgebraRoots" | "LieAlgebraWithCoefficientsData"
##ROW "MasseyProduct" | "MatrixAlgebras" | "MatrixCentralizer"
##ROW "MatrixNormalizer" | "MatrixSubalgebra" | "MinimalIdeal"
##ROW "MinimalSubalgebra" | "MultiplicationTable" | "Nilradical"
##ROW "ParabolicSubalgebra" | "ParabolicSubalgebraRoots" | "PositiveDefiniteMetricOnRepresentationSpace"
##ROW "PositiveRoots" | "Query" | "QuotientAlgebra"
##ROW "QuotientRepresentation" | "Radical" | "Rank1Elements"
##ROW "RelativeChains" | "Representation" | "RepresentationEigenvector"
##ROW "RestrictedRepresentation" | "RestrictedRootSpaceDecomposition" | "RootSpace"
##ROW "RootSpaceDecomposition" | "RootString" | "RootToCartanSubalgebraElementH"
##ROW "SatakeAssociate" | "SatakeDiagram" | "SemiDirectSum"
##ROW "Series" | "SimpleLieAlgebraData" | "SimpleLieAlgebraProperties"
##ROW "SimpleRoots" | "SolvableRepresentation" | "SplitAndCompactForms"
##ROW "StandardRepresentation" | "SubRepresentation" | "SubalgebraNormalizer"
##ROW "SymbolAlgebra" | "TanakaProlongation" | "TensorProductOfRepresentations"
##ENDTABLE
##
##
##SEEALSO
##- "DifferentialGeometry", "GroupActions", "JetCalculus", "Library", "Tensor", "Tools"
##
##	
##XREFMAP 
##- "long form" : Help:UsingPackages#longform
##- "short form" : Help:UsingPackages#shortform
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Lessons" : Help:DifferentialGeometry[LessonsAndTutorials][LessonsOverview] 
##- "Transformation" : Help:DifferentialGeometry[Transformation]
##- "Tensor" : Help:DifferentialGeometry[Tensor] 
##- "derivation" : Help:DifferentialGeometry[LieAlgebras][Derivations]
##- "GroupActions" : Help:DifferentialGeometry[GroupActions]
##- "JetCalculus" : Help:DifferentialGeometry[JetCalculus]
##- "Library" : Help:DifferentialGeometry[Library]
##- "Tensor" : Help:DifferentialGeometry[Tensor]
##- "Tools" : Help:DifferentialGeometry[Tools]
##- "Adjoint" : Help:DifferentialGeometry[LieAlgebras][Adjoint]
##- "AdjointExp" : Help:DifferentialGeometry[LieAlgebras][Adjoint]
##- "AlgebraData" : Help:DifferentialGeometry[LieAlgebras][AlgebraData]
##- "AlgebraLibraryData" : Help:DifferentialGeometry[LieAlgebras][AlgebraLibraryData]
##- "AlgebraNorm" : Help:DifferentialGeometry[LieAlgebras][AlgebraNorm]
##- "AlgebraInverse" : Help:DifferentialGeometry[LieAlgebras][AlgebraNorm]
##- "ApplyHomomorphism" : Help:DifferentialGeometry[LieAlgebras][ApplyHomomorphism]
##- "ApplyRepresentation" : Help:DifferentialGeometry[LieAlgebras][Representation]
##- "AscendingIdealsBasis" : Help:DifferentialGeometry[LieAlgebras][AscendingIdealsBasis]
##- "BracketOfSubspaces" : Help:DifferentialGeometry[LieAlgebras][BracketOfSubspaces]
##- "CartanDecomposition" : Help:DifferentialGeometry[LieAlgebras][CartanDecomposition]
##- "CartanInvolution" : Help:DifferentialGeometry[LieAlgebras][CartanInvolution]
##- "CartanMatrix" : Help:DifferentialGeometry[LieAlgebras][CartanMatrix]
##- "CartanMatrixToStandardForm" : Help:DifferentialGeometry[LieAlgebras][CartanMatrixToStandardForm]
##- "CartanSubalgebra" : Help:DifferentialGeometry[LieAlgebras][CartanSubalgebra]
##- "ChevalleyBasis" : Help:DifferentialGeometry[LieAlgebras][ChevalleyBasis]
##- "Center" : Help:DifferentialGeometry[LieAlgebras][Center]
##- "Centralizer" : Help:DifferentialGeometry[LieAlgebras][Centralizer]
##- "ChangeGradedComponent" : Help:DifferentialGeometry[LieAlgebras][ChangeGradedComponent]
##- "ChangeRepresentationBasis" : Help:DifferentialGeometry[LieAlgebras][ChangeRepresentationBasis]
##- "ChangeLieAlgebraTo" : Help:DifferentialGeometry[LieAlgebras][ChangeLieAlgebraTo]
##- "Codifferential" : Help:DifferentialGeometry[LieAlgebras][Codifferential]
##- "CoRoot" : Help:DifferentialGeometry[LieAlgebras][CoRoot]
##- "Cohomology" : Help:DifferentialGeometry[LieAlgebras][Cohomology]
##- "CohomologyDecomposition" : Help:DifferentialGeometry[LieAlgebras][Cohomology]
##- "CompactRoots" : Help:DifferentialGeometry[LieAlgebras][CompactRoots]
##- "Complexify" : Help:DifferentialGeometry[LieAlgebras][Complexify]
##- "Decompose" : Help:DifferentialGeometry[LieAlgebras][Decompose]
##- "Deformation" : Help:DifferentialGeometry[LieAlgebras][Deformation]
##- "Derivations" : Help:DifferentialGeometry[LieAlgebras][Derivations]
##- "DerivedAlgebra" : Help:DifferentialGeometry[LieAlgebras][DerivedAlgebra]
##- "DirectSum" : Help:DifferentialGeometry[LieAlgebras][DirectSum]
##- "DirectSumOfRepresentations" : Help:DifferentialGeometry[LieAlgebras][DirectSumOfRepresentations]
##- "Extension" : Help:DifferentialGeometry[LieAlgebras][Extension]
##- "GeneralizedCenter" : Help:DifferentialGeometry[LieAlgebras][GeneralizedCenter]
##- "GroupActions" : Help:DifferentialGeometry[GroupActions]
##- "HomomorphismSubalgebras" : Help:DifferentialGeometry[LieAlgebras][HomomorphismSubalgebras]
##- "InfinitesimalCoadjointAction" : Help:DifferentialGeometry[LieAlgebras][InfinitesimalCoadjointAction]
##- "Invariants" : Help:DifferentialGeometry[LieAlgebras][Invariants]
##- "JacobsonRadical" : Help:DifferentialGeometry[LieAlgebras][JacobsonRadical]
##- "JetCalculus" : Help:DifferentialGeometry[JetCalculus]
##- "JordanMatrices" : Help:DifferentialGeometry[LieAlgebras][JordanMatrices]
##- "JordanProduct" : Help:DifferentialGeometry[LieAlgebras][JordanMatrices]
##- "KostantCodifferential" : Help:DifferentialGeometry[LieAlgebras][KostantCodifferential]
##- "KostantLaplacian" : Help:DifferentialGeometry[LieAlgebras][KostantCodifferential]
##- "Library" : Help:DifferentialGeometry[Library]
##- "Killing" : Help:DifferentialGeometry[LieAlgebras][Killing]
##- "KillingForm" : Help:DifferentiaGeometry[LieAlgebras][KillingForm]
##- "LeviDecomposition" : Help:DifferentialGeometry[LieAlgebras][LeviDecomposition]
##- "LieAlgebraCohomology" : Help:DifferentialGeometry[LieAlgebras][LieAlgebraCohomology]
##- "LieAlgebraData" : Help:DifferentialGeometry[LieAlgebras][LieAlgebraData]
##- "LieAlgebraRepresentations" : Help:DifferentialGeometry[LieAlgebras][LieAlgebraRepresentations]
##- "LieAlgebraRoots" : Help:DifferentialGeometry[LieAlgebras][LieAlgebraRoots]
##- "MatrixAlgebras" : Help:DifferentialGeometry[LieAlgebras][MatrixAlgebras]
##- "LieAlgebraWithCoefficientsData" : Help:DifferentialGeometry[LieAlgebras][LieAlgebraWithCoefficientsData]
##- "MasseyProduct" : Help:DifferentialGeometry[LieAlgebras][LieAlgebraWithCoefficientsData]
##- "MatrixCentralizer" : Help:DifferentialGeometry[LieAlgebras][MatrixCentralizer]
##- "MatrixNormalizer" : Help:DifferentialGeometry[LieAlgebras][MatrixNormalizer]
##- "MinimalIdeal" : Help:DifferentialGeometry[LieAlgebras][MinimalIdeal]
##- "MinimalSubalgebra" : Help:DifferentialGeometry[LieAlgebras][MinimalSubalgebra]
##- "MultiplicationTable" : Help:DifferentialGeometry[LieAlgebras][MultiplicationTable]
##- "Nilradical" : Help:DifferentialGeometry[LieAlgebras][Nilradical]
##- "ParabolicSubalgebra" : Help:DifferentialGeometry[LieAlgebras][ParabolicSubalgebra]
##- "ParabolicSubalebraRoots" : Help:DifferentialGeometry[LieAlgebras][ParabolicSubalgebraRoots]
##- "PositiveDefiniteMetricOnRepresentationSpace" : Help:DifferentialGeometry[LieAlgebras][PositiveDefiniteMetricOnRepresentationSpace]
##- "PositiveRoots" : Help:DifferentialGeometry[LieAlgebras][PositiveRoots]
##- "Query" : Help:DifferentialGeometry[LieAlgebras][Query]
##- "QuotientAlgebra" : Help:DifferentialGeometry[LieAlgebras][QuotientAlgebra]
##- "QuotientRepresentation" : Help:DifferentialGeometry[LieAlgebras][QuotientRepresentation]
##- "Radical" : Help:DifferentialGeometry[LieAlgebras][Radical]
##- "Rank1Elements" : Help:DifferentialGeometry[LieAlgebras][Rank1Elements]
##- "RelativeChains" : Help:DifferentialGeometry[LieAlgebras][Cohomology] 
##- "Representation" : Help:DifferentialGeometry[LieAlgebras][Representation] 
##- "RepresentationEigenvector" : Help:DifferentialGeometry[LieAlgebras][RepresentationEigenvector] 
##- "RestrictedRepresentation" : Help:DifferentialGeometry[LieAlgebras][RestrictedRepresentation] 
##- "RestrictedRootSpaceDecomposition" : Help:DifferentialGeometry[LieAlgebras][RestrictedRootSpaceDecomposition]
##- "RootSpaceDecomposition" : Help:DifferentialGeometry[LieAlgebras][RootSpaceDecomposition]
##- "RootSpace" : Help:DifferentialGeometry[LieAlgebras][RootSpace]
##- "RootToCartanSubalgebraElementH" : Help:DifferentialGeometry[LieAlgebras][RootToCartanSubalgebraElementH]
##- "RootString" : Help:DifferentialGeometry[LieAlgebras][RootString]
##- "SatakeDiagram" : Help:DifferentialGeometry[LieAlgebras][SatakeDiagram]
##- "SemiDirectSum" : Help:DifferentialGeometry[LieAlgebras][SemiDirectSum]
##- "Series" : Help:DifferentialGeometry[LieAlgebras][Series]
##- "SimpleLieAlgebraData" : Help:DifferentialGeometry[LieAlgebras][SimpleLieAlgebraData]
##- "SimpleLieAlgebraProperties" : Help:DifferentialGeometry[LieAlgebras][SimpleLieAlgebraProperties]
##- "SimpleRoots" : Help:DifferentialGeometry[LieAlgebras][SimpleRoots]
##- "SplitAndCompactForms" : Help:DifferentialGeometry[LieAlgebras][SplitAndCompactForms]
##- "SolvableRepresentation" : Help:DifferentialGeometry[LieAlgebras][SolvableRepresentation]
##- "SubalgebraNormalizer" : Help:DifferentialGeometry[LieAlgebras][SubalgebraNormalizer]
##- "SymbolAlgebra" : Help:DifferentialGeometry[LieAlgebras][SymbolAlgebra]
##- "StandardRepresentation" : Help:DifferentialGeometry[LieAlgebras][StandardRepresentation]
##- "SubRepresentation" : Help:DifferentialGeometry[LieAlgebras][SubRepresentation] 
##- "TanakaProlongation" :  Help:DifferentialGeometry[LieAlgebras][TanakaProlongation]
##- "TensorProductOfRepresentations" : Help:DifferentialGeometry[LieAlgebras][TensorProductOfRepresentations]

	
