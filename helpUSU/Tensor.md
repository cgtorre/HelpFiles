##PROCEDURE(help) DifferentialGeometry[Tensor]
##TITLE  Overview of the Tensor package
##DESCRIPTION
## The 'DifferentialGeometry:-Tensor' package provides an extensive suite of commands for computations with tensors on the tangent bundle of any manifold 
## or with tensors on any vector bundle.  
##- The 'Tensor' package contains commands for the standard algebraic operations on tensors as well as commands for "covariant differentiation" and "curvature" calculations 
## (for metric connections, general affine connections, or connections on vector bundles).
##- The 'Tensor' package also includes a full implementation of the 2 component spinor and Newman-Penrose formalisms for space-time computations (pseudo-Riemannian manifolds with metric signature [+1, -1, -1, -1] ).  
## "Petrov" and "Segre" classifications of spacetimes can be calculated as well as complete sets of "curvature invariants". 
##- All tensor computations can be done in an arbitrary frame or co-frame on the manifold.  In particular, all curvature computations for a (pseudo-)Riemannian metric can be performed with respect to an "orthonormal frame".
##- The 'Tensor' package, working in conjunction with other "Differential Geometry" commands, provides great flexibility for mapping tensors between manifolds.  
## For example, if G is a Lie group acting on a manifold M, then the "PushPullTensor" command can be used to push forward the
## G invariant tensors on M to tensor fields on the quotient manifold M/G.
##- Commands are available for calculating the "Laplace-Beltrami" operator on differential forms and for the "Schouten" and "Frolicher-Nijenhuis" brackets of tensor fields.  
## These bracket operations are important in complex geometry and in Poisson geometry.
##- Infinitesimal transformation groups such as the "Killing vectors" of a metric can be calculated.
##- "Infinitesimal holonomy" of a metric or a connection can be calculated.
##- There are commands for computing special tensor fields such as "Killing-Yano tensors".  
##- The 'Tensor' package is fully integrated with the "LieAlgebras" and "LieAlgebraRepresentations" packages which allows for the computation of, for example, 
## the invariant tensors on a Lie algebra.
##- The  "Differential Geometry Lessons" (Lessons 9 and 10) provide a systematic introduction to the commands in the 'Tensor' package.
##- Each command in the 'Tensor' package can be accessed by using either the "long form" or the "short form" of the command name in the command calling sequence.
##
##SECTION  Commands for the algebraic manipulation of tensors
#["CanonicalTensors","ContractIndices","Convert/DGspinor","Convert/DGtensor", "FormInnerProduct", "DGGramSchmidt","GenerateSymmetricTensors","GenerateTensors","HodgeStar","InverseMetric","KroneckerDelta","MetricDensity","MultiVector","PermutationSymbol","PlebanskiTensor","PushPullTensor","RaiseLowerIndices", "QuadraticFormSignature", "RearrangeIndices","SymmetrizeIndices","TensorInnerProduct"] 
##TABLE(width = 500, border = 0, alignment = center, colwidth = 1|1|1)                                
##ROW  "CanonicalTensors" | "ContractIndices" | "Convert/DGspinor"
##ROW  "Convert/DGtensor" | "FormInnerProduct" | "DGGramSchmidt"
##ROW  "GenerateSymmetricTensors" | "GenerateTensors" | "HodgeStar"
##ROW  "InverseMetric" | "KroneckerDelta" | "MetricDensity"
##ROW  "MultiVector" | "PermutationSymbol" | "PlebanskiTensor"
##ROW  "PushPullTensor" | "QuadraticFormSignature" | "RaiseLowerIndices"
##ROW  "RearrangeIndices" | "SymmetrizeIndices" | "TensorInnerProduct"
##ENDTABLE
##
##- "CanonicalTensors": create various standard tensors.
##- "ContractIndices": contract the indices of a tensor.
##- "Convert/DGspinor": convert a tensor to a spinor.
##- "Convert/DGtensor": convert an array, vector, p-form, spinor ... to a  tensor. 
##- "DGGramSchmidt": construct an orthonormal basis of vector, forms, tensors with respect to a metric.
##- "FormInnerProduct": compute the inner product of two forms with respect to a given metric tensor.
##- "GenerateSymmetricTensors": generate a list of symmetric tensors from a list of tensors.
##- "GenerateTensors": generate a list of tensors from a list of lists of tensors.
##- "HodgeStar": apply the Hodge star operator to a differential form.
##- "InverseMetric": find the inverse of a metric tensor.
##- "KroneckerDelta": find the Kronecker delta tensor of rank r.
##- "MetricDensity": use a metric tensor to create a scalar density of a given weight.
##- "MultiVector": compute the alternating sum of the tensor product of a list of vector fields.
##- "PermutationSymbol": create a permutation symbol.
##- "PlebanskiTensor": calculate the Plebanski tensor from a trace-free rank 2 symmetric tensor.
##- "PushPullTensor": transform a tensor from one manifold or coordinate system to another.
##- "QuadraticFormSignature" : find the signature of a covariant, symmetric, rank 2 tensor.
##- "RaiseLowerIndices": raise or lower a list of indices of a tensor.
##- "RearrangeIndices": rearrange the argument/indices of a tensor.
##- "SymmetrizeIndices": symmetrize or skew-symmetrize a list of tensor indices.
##- "TensorInnerProduct": compute the inner product of two vectors, forms or tensors with respect to a given metric tensor.
#ENDSECTION
##
##SECTION Commands for tensor differentiation
#["Christoffel", "Connection","CovariantDerivative","DirectionalCovariantDerivative","GeodesicEquations","Laplacian","ParallelTransportEquations","TensorBrackets","TorsionTensor"]      
##TABLE(width = 425, border = 0, alignment = center, colwidth = 10|7|7)     
##ROW "Christoffel" | "Connection" | "CovariantDerivative"
##ROW "DirectionalCovariantDerivative" | "GeodesicEquations" | "Laplacian"
##ROW "ParallelTransportEquations" | "TensorBrackets" | "TorsionTensor"
##ENDTABLE
##- "Christoffel": find the Christoffel symbols of the first or second kind for a metric tensor.
##- "Connection": define a linear connection on the tangent bundle or on a vector bundle.
##- "CovariantDerivative": calculate the covariant derivative of a tensor field with respect to a connection.
##- "DirectionalCovariantDerivative": calculate the covariant derivative of a tensor field in the direction of a vector field and with respect to a given connection.
##- "GeodesicEquations": calculate the geodesic equations for a symmetric linear connection on the tangent bundle.
##- "Laplacian": find the Laplacian of a differential form with respect to a metric.
##- "ParallelTransportEquations": calculate the parallel transport equations for a linear connection on the tangent bundle or a linear connection on a vector bundle.
##- "TensorBrackets": calculate the Schouten bracket and Frolicher-Nijenhuis brackets of tensor fields.
##- "TorsionTensor": calculate the torsion tensor for a linear connection on the tangent bundle.
#ENDSUBSECTION
##
##SECTION Commands for calculating curvature tensors  
#["BachTensor", "CottonTensor","CurvatureTensor","EinsteinTensor", "ProjectiveCurvatureTensor", "RicciScalar", "RicciTensor","RiemannInvariants", "SchoutenTensor", "SectionalCurvature","TraceFreeRicciTensor","WeylTensor"]     
##TABLE(width = 450, border = 0, alignment = center, colwidth = 1|1|1)  
##ROW  "BachTensor" | "CottonTensor" | "CurvatureTensor"
##ROW  "EinsteinTensor" | "ProjectiveCurvatureTensor" | "RicciScalar"
##ROW  "RicciTensor" | "RiemannInvariants" | "SchoutenTensor"
##ROW  "SectionalCurvature" | "TraceFreeRicciTensor" | "WeylTensor"
##ENDTABLE
##- "BachTensor": calculate the Bach tensor of a metric.
##- "CottonTensor": calculate the Cotton tensor for a metric.
##- "CurvatureTensor": calculate the curvature tensor of a linear connection on the tangent bundle or on a vector bundle.
##- "EinsteinTensor": calculate the Einstein tensor for a metric.
##- "ProjectiveCurvatureTensor": calculate the Weyl projective curvature tensor of a connection on the tangent bundle.
##- "RicciScalar": calculate the Ricci scalar for a metric.
##- "RicciTensor": calculate the Ricci tensor of a linear connection on the tangent bundle.
##- "RiemannInvariants": calculate a complete set of scalar curvature invariants in 4 dimensions.
##- "SectionalCurvature": calculate the sectional curvature for a metric. 
##- "SchoutenTensor": calculate the Schouten tensor of a metric.  
##- "TraceFreeRicciTensor": calculate the trace-free Ricci tensor for a metric.   
##- "WeylTensor": calculate the Weyl curvature tensor of a metric.
#ENDSUBSECTION
##
##SECTION Infinitesimal transformation groups
# "ConformalKillingVectors", "HomthetyVectors", "KillingVectors"
##TABLE(width = 400, border = 0, alignment = center, colwidth = 12|10|10)  
##ROW  "ConformalKillingVectors" | "HomothetyVectors" | "KillingVectors"
##ENDTABLE
##- "ConformalKillingVectors": calculate the conformal Killing vectors for a given metric.
##- "HomothetyVectors": calculate the homothety vectors for a given metric.
##- "KillingVectors": calculate the Killing vectors or infinitesimal isometries for a given metric.
#SUBSECION
## 
##SECTION Commands for calculating holonomy
# [InfinitesimalHolonomy, InvariantTensorsAtAPoint]
##TABLE(width = 425, border = 0, alignment = center, colwidth = 10|12|10)  
##ROW "InfinitesimalHolonomy" | "InvariantTensorsAtAPoint" | ``
##ENDTABLE
##
##- "InfinitesimalHolonomy": find the matrix Lie algebra giving the infinitesimal holonomy of a metric or a connection on the tangent bundle or on a general vector bundle.
##- "InvariantTensorsAtAPoint": find tensors or differential forms which are invariant under the infinitesimal action of a set of matrices.
#ENDSUBSECTION
##
##SECTION Commands for calculating special tensor fields
#["CovariantlyConstantTensors", "KillingSpinors","KillingTensors","KillingYanoTensors", "RecurrentTensors"]
##
##TABLE(width = 425, border = 0, alignment = center, colwidth = 10|8|8)
##ROW "CovariantlyConstantTensors" | "KillingSpinors" | "KillingTensors"
##ROW "KillingYanoTensors" | "RecurrentTensors" | ``
##ENDTABLE
##
##- "CovariantlyConstantTensors": calculate the covariantly constant tensors with respect to a given metric or connection.
##- "KillingSpinors": calculate the Killing spinors for a given spacetime.
##- "KillingYanoTensors":  calculate the Killing tensors of a specified rank for a given metric or connection.
##- "KillingTensors": calculate the Killing-Yano tensors for a given connection or a given metric.
##- "RecurrentTensors": calculate the recurrent tensors with respect to a given metric or connection.
#SUBSECTION
##SECTION Commands for working with Killing tensors
#["CheckKillingTensor", "IndependentKillingTensors",  "KillingBracket", "SymmetricProductsOfKillingTensors"]
##
##TABLE(width = 550, border = 0, alignment = center, colwidth = 10|8|6)
##ROW "CheckKillingTensor" | "IndependentKillingTensors" | "KillingBracket"
##ROW "SymmetricProductsOfKillingTensors" | `` | ``
##ENDTABLE
##
##- "CheckKillingTensor": check that a tensor is the Killing tensor for a metric.
##- "IndependentKillingTensors": create a list of linearly independent Killing tensors.
##- "KillingBracket": a covariant form of the Schouten bracket for symmetric tensors.
##- "SymmetricProductsOfKillingTensors": form all possible symmetric tensors of a given rank.
#ENDSUBSECTION
##
##SECTION Commands for the 2-component spinor formalism
#["AdaptedSpinorDyad","BivectorSolderForm","ConjugateSpinor","EpsilonSpinor","FactorWeylSpinor","KroneckerDeltaSpinor","RaiseLowerSpinorIndices","RicciSpinor","SolderForm","SpinConnection","SpinorInnerProduct","WeylSpinor"         
##TABLE(width = 450, border = 0, alignment = center, colwidth = 10|8|8)
##ROW "AdaptedSpinorDyad" | "BivectorSolderForm" | "ConjugateSpinor"
##ROW "EpsilonSpinor" | "FactorWeylSpinor" | "KroneckerDeltaSpinor"
##ROW "RaiseLowerSpinorIndices" | "RicciSpinor" | "SolderForm"
##ROW "SpinConnection" | "SpinorInnerProduct" | "WeylSpinor"
##ENDTABLE
##- "AdaptedSpinorDyad": find a spinor dyad which transforms the Weyl spinor to normal form.
##- "BivectorSolderForm": calculate the rank 4 spin-tensor which maps bivectors to symmetric rank 2 spinors.
##- "ConjugateSpinor": calculate the complex conjugate of a spinor.
##- "EpsilonSpinor": calculate the epsilon spinor in the 2 component spinor formalism.
##- "FactorWeylSpinor": factorize a rank 4 symmetric spinor.
##- "KroneckerDeltaSpinor": calculate the Kronecker delta spinor in the 2 component spinor formalism.
##- "RaiseLowerSpinorIndices": raise/lower the indices of a spinor or spin-tensor using the epsilon spinors.
##- "RicciSpinor": calculate the rank 4 Ricci spinor corresponding to the trace-free Ricci tensor.
##- "SolderForm": calculate the solder form (or Infeld-van der Waerden symbols) from an orthonormal tetrad.
##- "SpinConnection": calculate the unique spin connection defined by a solder form.
##- "SpinorInnerProduct":  contract all spinor indices of a pair of 2-component spin-tensors using the epsilon spinors.
##- "WeylSpinor": calculate the rank 4 Weyl spinor corresponding to the Weyl tensor.
#ENDSUBSECTION
##
##SECTION Commands for the Newman-Penrose formalism
#["AdaptedNullTetrad","GRQuery","NPBianchiIdentities","NPCurvatureScalars","NPDirectionalDerivatives","NPRicciIdentities","NPSpinCoefficients","NullTetrad","NullTetradTransformation","NullVecetor","OrthonormalTetrad","PrincipalNullDirections",  "SpacetimeConventions"]         
##TABLE(width = 500, border = 0, alignment = center, colwidth = 8|10|8)
##ROW "AdaptedNullTetrad" | "GRQuery" | "NPBianchiIdentities"
##ROW "NPCurvatureScalars" | "NPDirectionalDerivatives" | "NPRicciIdentities"
##ROW "NPSpinCoefficients" | "NullTetrad" | "NullTetradTransformation"
##ROW "NullVector" | "OrthonormalTetrad" | "PrincipalNullDirections"
# ROW "SpacetimeConventions" | `` | ``
##ENDTABLE
##- "AdaptedNullTetrad": find a null tetrad which transforms the Newman-Penrose Weyl scalars to a standard form.
##- "GRQuery": verify various properties of spacetimes.
##- "NPBianchiIdentities": calculate the Bianchi identities in the Newman-Penrose formalism.
##- "NPCurvatureScalars": calculate the Ricci scalars and the Weyl scalars in the Newman-Penrose formalism.
##- "NPDirectionalDerivatives": define the directional derivative operators used in the Newman-Penrose formalism.
##- "NPRicciIdentities": calculate the Ricci identities in the Newman-Penrose formalism.
##- "NPSpinCoefficients": calculate the Newman-Penrose spin coefficients.
##- "NullTetrad": calculate a null tetrad from an orthonormal tetrad.
##- "NullTetradTransformation": apply a Lorentz transformation to a null tetrad.
##- "NullVector": construct a null vector from a solder form and a rank 1 spinor.
##- "OrthonormalTetrad": calculate an orthonormal tetrad from a null tetrad.
##- "PrincipalNullDirections": find the principal null directions of a 4-dimensional spacetime.  
# - "SpacetimeConventions": a description of the tensor and spinor conventions used by the DifferentialGeometry package.
#ENDSUBSECTION
##
##SECTION Commands for the algebraic classification of spacetimes 
#["IsotropyType","PetrovType","SubspaceType","SegreType"]   
##TABLE(width = 425, border = 0, alignment = center, colwidth = 1|1|1)
##ROW "CongruenceProperties" | "IsotropyType" | "PetrovType" 
##ROW "SubspaceType" | "SegreType" | ``
##ENDTABLE
##- "CongruenceProperties": calculate the geometry properties of a line congruence.
##- "IsotropyType": determine the isotropy type of the isotropy subalgebra of infinitesimal isometries.
##- "PetrovType": determine the Petrov type of a spacetime from the Weyl tensor.
##- "SegreType": determine the Plebanski-Petrov type and the Segre type of a trace-free, rank 2 symmetric tensor.
SubspaceType": determine the signature of the metric restricted to a subspace.
#ENDSECTION
##
##SECTION Commands for field theory
#["BelRobinson","DivergenceIdentities","EnergyMomentumTensor","MatterFieldEquations"]   
##TABLE(width = 500, border = 0, alignment = center, colwidth = 1|1|1)
##ROW "BelRobinson" | "DivergenceIdentities" | "EnergyMomentumTensor"
##ROW "MatterFieldEquations" | "RainichConditions" | "RainichElectromagneticField"
##ENDTABLE
##- "BelRobinson": calculate the rank 4 Bel-Robinson tensor for a metric. 
##- "DivergenceIdentities": check the divergence identity for various energy-momentum tensors.
##- "EnergyMomentumTensor": calculate the energy-momentum tensor for various fields (scalar, electromagnetic, dust, ...).
##- "MatterFieldEquations": calculate the field equations for various field theories (scalar, electromagnetic, dust, ...).
##- "RainichConditions": check that a metric tensor satisfies the Rainich conditions.
##- "RainichElectromagneticField" : from a given metric satisfying the Rainich conditions, calculate an electromagnetic field which solves the Einstein-Maxwell equations. 
#ENDSUBSECTION
##
#["AdaptedNullTetrad", "AdaptedSpinorDyad", "BachTensor", "BelRobinson", "BivectorSolderForm", "CanonicalTensors", "CheckKillingTensor", "Christoffel", "ConformalKillingVectors", "CongruenceProperties", "ConjugateSpinor", 
#"Connection", "ContractIndices", "CottonTensor", "CovariantDerivative", "CovariantlyConstantTensors", "CurvatureTensor", "DGGramSchmidt", "DirectionalCovariantDerivative", "DivergenceIdentities", "EinsteinTensor", 
#"EnergyMomentumTensor", "EpsilonSpinor", "FactorWeylSpinor", "FormInnerProduct", "GRQuery", "GenerateSymmetricTensors", "GenerateTensors", "GeodesicEquations", "HodgeStar", "HomothetyVectors", "IndependentKillingTensors", 
#"InfinitesimalHolonomy", "InvariantTensorsAtAPoint", "InverseMetric", "IsotropyType", "KillingBracket", "KillingSpinors", "KillingTensors", "KillingVectors", "KillingYanoTensors", "KroneckerDelta", "KroneckerDeltaSpinor", 
#"Laplacian", "MatterFieldEquations", "MetricDensity", "MultiVector", "NPBianchiIdentities", "NPCurvatureScalars", "NPDirectionalDerivatives", "NPRicciIdentities", "NPSpinCoefficients", "NullTetrad", "NullTetradTransformation", 
#"NullVector", "OrthonormalTetrad", "ParallelTransportEquations", "PermutationSymbol", "PetrovType", "PlebanskiTensor", "PrincipalNullDirections", "ProjectiveCurvatureTensor", "PushPullTensor", "QuadraticFormSignature", 
#"RainichConditions", "RainichElectromagneticField", "RaiseLowerIndices", "RaiseLowerSpinorIndices", "RearrangeIndices", "RecurrentTensors", "RicciScalar", "RicciSpinor", "RicciTensor", "RiemannInvariants", "SchoutenTensor", 
#"SectionalCurvature", "SegreType", "SolderForm", "SpinConnection", "SpinorInnerProduct", "SubspaceType", "SymmetricProductsOfKillingTensors", "SymmetrizeIndices", "TensorBrackets", "TensorInnerProduct", "TorsionTensor", 
#"TraceFreeRicciTensor", "WeylSpinor", "WeylTensor"]
##SECTION Alphabetical listing of all Tensor commands
##TABLE(width = 600, border = 0, alignment = center, colwidth = 1|1|1)                                     
##ROW "AdaptedNullTetrad" | "AdaptedSpinorDyad" | "BachTensor"
##ROW "BelRobinson" | "BivectorSolderForm" | "CanonicalTensors"
##ROW "CheckKillingTensor" | "Christoffel" | "ConformalKillingVectors"
##ROW "CongruenceProperties" | "ConjugateSpinor" | "Connection"
##ROW "ContractIndices" | "CottonTensor" | "CovariantDerivative"
##ROW "CovariantlyConstantTensors" | "CurvatureTensor" | "DGGramSchmidt"
##ROW "DirectionalCovariantDerivative" | "DivergenceIdentities" | "EinsteinTensor"
##ROW "EnergyMomentumTensor" | "EpsilonSpinor" | "FactorWeylSpinor"
##ROW "FormInnerProduct" | "GRQuery" | "GenerateSymmetricTensors"
##ROW "GenerateTensors" | "GeodesicEquations" | "HodgeStar"
##ROW "HomothetyVectors" | "IndependentKillingTensors" | "InfinitesimalHolonomy"
##ROW "InvariantTensorsAtAPoint" | "InverseMetric" | "IsotropyType"
##ROW "KillingBracket" | "KillingSpinors" | "KillingTensors"
##ROW "KillingVectors" | "KillingYanoTensors" | "KroneckerDelta"
##ROW "KroneckerDeltaSpinor" | "Laplacian" | "MatterFieldEquations"
##ROW "MetricDensity" | "MultiVector" | "NPBianchiIdentities"
##ROW "NPCurvatureScalars" | "NPDirectionalDerivatives" | "NPRicciIdentities"
##ROW "NPSpinCoefficients" | "NullTetrad" | "NullTetradTransformation"
##ROW "NullVector" | "OrthonormalTetrad" | "ParallelTransportEquations"
##ROW "PermutationSymbol" | "PetrovType" | "PlebanskiTensor"
##ROW "PrincipalNullDirections" | "ProjectiveCurvatureTensor" | "PushPullTensor"
##ROW "QuadraticFormSignature" | "RainichConditions" | "RainichElectromagneticField"
##ROW "RaiseLowerIndices" | "RaiseLowerSpinorIndices" | "RearrangeIndices"
##ROW "RecurrentTensors" | "RicciScalar" | "RicciSpinor"
##ROW "RicciTensor" | "RiemannInvariants" | "SchoutenTensor"
##ROW "SectionalCurvature" | "SegreType" | "SolderForm"
##ROW "SpinConnection" | "SpinorInnerProduct" | "SubspaceType"
##ROW "SymmetricProductsOfKillingTensors" | "SymmetrizeIndices" | "TensorBrackets"
##ROW "TensorInnerProduct" | "TorsionTensor" | "TraceFreeRicciTensor"
##ROW "WeylSpinor" | "WeylTensor" | `` 
##ENDTABLE
#ENDSUBSECTION
##
##SEEALSO
##- "DifferentialGeometry", "GroupActions", "JetCalculus", "Library", "LieAlgebras", "Tools"
##- "Physics[D_]"
##- "Physics[d_]"
##- "Physics[Einstein]"
##- "Physics[g_]"
##- "Physics[LeviCivita]"
##- "Physics[Ricci]"
##- "Physics[Riemann]"
##- "Physics[Weyl]"
## 
##XREFMAP
##
##
##- "covariant differentiation" : Help:DifferentialGeometry[Tensor][CovariantDerivative]
##- "curvature" : Help:DifferentialGeometry[Tensor][CurvatureTensor]
##- "Infinitesimal holonomy" : Help:DifferentialGeometry[Tensor][InfinitesimalHolonomy]
##- "Petrov" : Help:DifferentialGeometry[Tensor][PetrovType]
##- "Segre" : Help:DifferentialGeometry[Tensor][SegreType]
##- "curvature invariants" : Help:DifferentialGeometry[Tensor][RiemannInvariants]
##- "orthonormal frame" : Help:DifferentialGeometry[Tensor][DGGramSchmidt]
##- "Killing vectors" : Help:DifferentialGeometry[Tensor][KillingVectors]
##- "Killing-Yano tensors" : Help:DifferentialGeometry[Tensor][KillingYanoTensors]
##- "Laplace-Beltrami" : Help:DifferentialGeometry[Tensor][Laplacian]
##- "Schouten" : Help:DifferentialGeometry[Tensor][TensorBrackets]
##- "Frolicher-Nijenhuis" : Help:DifferentialGeometry[Tensor][TensorBrackets]
##- "Differential Geometry Lessons" : Help:DifferentialGeometry[LessonsAndTutorials][LessonsOverview]
##- "long form" : Help:UsingPackages#longform
##- "short form" : Help:UsingPackages#shortform
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "GroupActions" : Help:DifferentialGeometry[GroupActions]
##- "JetCalculus" : Help:DifferentialGeometry[JetCalculus]
##- "LieAlgebras" : Help:DifferentialGeometry[LieAlgebras]
##- "Library" : Help:DifferentialGeometry[Library]
##- "Tools" :  Help:DifferentialGeometry[Tools]
##- "LieAlgebraRepresentations" : Help:DifferentialGeometry[LieAlgebras][Representation]
##- "AdaptedNullTetrad" : Help:DifferentialGeometry[Tensor][AdaptedNullTetrad]
##- "AdaptedSpinorDyad" : Help:DifferentialGeometry[Tensor][AdaptedSpinorDyad]
##- "BachTensor" : Help:DifferentialGeometry[Tensor][BachTensor] 
##- "BelRobinson" : Help:DifferentialGeometry[Tensor][BelRobinson]
##- "BivectorSolderForm" : Help:DifferentialGeometry[Tensor][BivectorSolderForm]
##- "CanonicalTensors" : Help:DifferentialGeometry[Tensor][CanonicalTensors]
##- "CheckKillingTensor" : Help:DifferentialGeometry[Tensor][CheckKillingTensor]
##- "Christoffel" : Help:DifferentialGeometry[Tensor][Christoffel]
##- "ConformalKillingVectors" : Help:DifferentialGeometry[Tensor][ConformalKillingVectors]
##- "ConjugateSpinor" : Help:DifferentialGeometry[Tensor][ConjugateSpinor]
##- "Connection" : Help:DifferentialGeometry[Tensor][Connection]
##- "CongruenceProperties" : Help:DifferentialGeometry[Tensor][CongruenceProperties]
##- "ContractIndices" : Help:DifferentialGeometry[Tensor][ContractIndices]
##- "Convert/DGspinor" : Help:DifferentialGeometry[Convert]
##- "Convert/DGtensor" : Help:DifferentialGeometry[Convert]
##- "CottonTensor" : Help:DifferentialGeometry[Tensor][CottonTensor]
##- "CovariantDerivative" : Help:DifferentialGeometry[Tensor][CovariantDerivative]
##- "CovariantlyConstantTensors" : Help:DifferentialGeometry[Tensor][CovariantlyConstantTensors]
##- "CurvatureTensor" : Help:DifferentialGeometry[Tensor][CurvatureTensor]
##- "DGGramSchmidt" : Help:DifferentialGeometry[Tensor][DGGramSchmidt]
##- "DirectionalCovariantDerivative" : Help:DifferentialGeometry[Tensor][DirectionalCovariantDerivative]
##- "DivergenceIdentities" : Help:DifferentialGeometry[Tensor][EnergyMomentumTensor]
##- "EinsteinTensor" : Help:DifferentialGeometry[Tensor][EinsteinTensor]
##- "EnergyMomentumTensor" : Help:DifferentialGeometry[Tensor][EnergyMomentumTensor]
##- "EpsilonSpinor" : Help:DifferentialGeometry[Tensor][EpsilonSpinor]
##- "FactorWeylSpinor" : Help:DifferentialGeometry[Tensor][FactorWeylSpinor]
##- "FormInnerProduct" : Help:DifferentialGeometry[Tensor][FormInnerProduct]
##- "GRQuery" : Help:DifferentialGeometry[Tensor][GRQuery]
##- "GenerateSymmetricTensors" : Help:DifferentialGeometry[Tensor][GenerateSymmetricTensors]
##- "GenerateTensors" : Help:DifferentialGeometry[Tensor][GenerateTensors]
##- "GeodesicEquations" : Help:DifferentialGeometry[Tensor][GeodesicEquations]
##- "HodgeStar" : Help:DifferentialGeometry[Tensor][HodgeStar]
##- "HomothetyVectors" : Help:DifferentialGeometry[Tensor][HomothetyVectors]
##- "InfinitesimalHolonomy" : Help:DifferentialGeometry[Tensor][InfinitesimalHolonomy]
##- "InvariantTensorsAtAPoint" : Help:DifferentialGeometry[Tensor][InvariantTensorsAtAPoint]
##- "IndependentKillingTensors" : Help:DifferentialGeometry[Tensor][IndependentKillingTensors]
##- "InverseMetric" : Help:DifferentialGeometry[Tensor][InverseMetric]
##- "IsotropyType" : Help:DifferentialGeometry[Tensor][IsotropyType]
##- "KillingBracket" : Help:DifferentialGeometry[Tensor][KillingBracket]
##- "KillingSpinors" : Help:DifferentialGeometry[Tensor][KillingSpinors]
##- "KillingTensors" : Help:DifferentialGeometry[Tensor][KillingTensors]
##- "KillingVectors" : Help:DifferentialGeometry[Tensor][KillingVectors]
##- "KillingYanoTensors" : Help:DifferentialGeometry[Tensor][KillingYanoTensors]
##- "KroneckerDelta" : Help:DifferentialGeometry[Tensor][KroneckerDelta]
##- "KroneckerDeltaSpinor" : Help:DifferentialGeometry[Tensor][KroneckerDeltaSpinor]
##- "Laplacian" : Help:DifferentialGeometry[Tensor][Laplacian]
##- "MatterFieldEquations" : Help:DifferentialGeometry[Tensor][EnergyMomentumTensor]
##- "MetricDensity" : Help:DifferentialGeometry[Tensor][MetricDensity]
##- "MultiVector" : Help:DifferentialGeometry[Tensor][MultiVector]
##- "NPBianchiIdentities" : Help:DifferentialGeometry[Tensor][NPBianchiIdentities]
##- "NPCurvatureScalars" : Help:DifferentialGeometry[Tensor][NPCurvatureScalars]
##- "NPDirectionalDerivatives" : Help:DifferentialGeometry[Tensor][NPDirectionalDerivatives]
##- "NPRicciIdentities" : Help:DifferentialGeometry[Tensor][NPRicciIdentities]
##- "NPSpinCoefficients" : Help:DifferentialGeometry[Tensor][NPSpinCoefficients]
##- "NullTetrad" : Help:DifferentialGeometry[Tensor][NullTetrad]
##- "NullTetradTransformation" : Help:DifferentialGeometry[Tensor][NullTetradTransformation]
##- "NullVector" : Help:DifferentialGeometry[Tensor][NullVector]
##- "OrthonormalTetrad" : Help:DifferentialGeometry[Tensor][NullTetrad]
##- "ParallelTransportEquations" : Help:DifferentialGeometry[Tensor][ParallelTransportEquations]
##- "PermutationSymbol" : Help:DifferentialGeometry[Tensor][PermutationSymbol]
##- "PetrovType" : Help:DifferentialGeometry[Tensor][PetrovType]
##- "PlebanskiTensor" : Help:DifferentialGeometry[Tensor][PlebanskiTensor]
##- "PrincipalNullDirections" : Help:DifferentialGeometry[Tensor][PrincipalNullDirections]
##- "ProjectiveCurvatureTensor" : Help:DifferentialGeometry[Tensor][ProjectiveCurvatureTensor]
##- "PushPullTensor" : Help:DifferentialGeometry[Tensor][PushPullTensor]
##- "QuadraticFormSignature" : Help:DifferentialGeometry[Tensor][QuadraticFormSignature]
##- "RainichConditions" : Help:DifferentialGeometry[Tensor][RainichConditions]
##- "RainichElectromagneticField" : Help:DifferentialGeometry[Tensor][RainichElectromagneticField]
##- "RaiseLowerIndices" : Help:DifferentialGeometry[Tensor][RaiseLowerIndices]
##- "RaiseLowerSpinorIndices" : Help:DifferentialGeometry[Tensor][RaiseLowerSpinorIndices]
##- "RearrangeIndices" : Help:DifferentialGeometry[Tensor][RearrangeIndices]
##- "RecurrentTensors" : Help:DifferentialGeometry[Tensor][RecurrentTensors]
##- "RicciScalar" : Help:DifferentialGeometry[Tensor][RicciScalar]
##- "RicciSpinor" : Help:DifferentialGeometry[Tensor][RicciSpinor]
##- "RicciTensor" : Help:DifferentialGeometry[Tensor][RicciTensor]
##- "RiemannInvariants" : Help:DifferentialGeometry[Tensor][RiemannInvariants]
##- "SchoutenTensor" : Help:DifferentialGeometry[Tensor][SchoutenTensor]
##- "SectionalCurvature" : Help:DifferentialGeometry[Tensor][SectionalCurvature]
##- "SegreType" : Help:DifferentialGeometry[Tensor][SegreType]
##- "SolderForm" : Help:DifferentialGeometry[Tensor][SolderForm]
##- "SpinConnection" : Help:DifferentialGeometry[Tensor][SpinConnection]
##- "SpinorInnerProduct" : Help:DifferentialGeometry[Tensor][SpinorInnerProduct]
##- "SubspaceType" : Help:DifferentialGeometry[Tensor][SubspaceType]
##- "SymmetricProductsOfKillingTensors" : Help:DifferentialGeometry[Tensor][SymmetricProductsOfKillingTensors]
##- "SymmetrizeIndices" : Help:DifferentialGeometry[Tensor][SymmetrizeIndices]
##- "TensorBrackets" : Help:DifferentialGeometry[Tensor][TensorBrackets]
##- "TensorInnerProduct" : Help:DifferentialGeometry[Tensor][TensorInnerProduct]
##- "TorsionTensor" : Help:DifferentialGeometry[Tensor][TorsionTensor]
##- "TraceFreeRicciTensor" : Help:DifferentialGeometry[Tensor][TraceFreeRicciTensor]
##- "WeylSpinor" : Help:DifferentialGeometry[Tensor][WeylSpinor]
##- "WeylTensor" : Help:DifferentialGeometry[Tensor][WeylTensor]


