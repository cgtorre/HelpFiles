##PROCEDURE(help) DifferentialGeometry
##TITLE  Overview of the DifferentialGeometry Package
##DESCRIPTION
##- The `DifferentialGeometry` package is a comprehensive suite of commands and subpackages featuring a collection of tightly integrated tools for computations in the 
## areas of: calculus on manifolds (vector fields, differential forms and transformations); "tensor analysis"; "calculus on jet spaces"; "Lie algebras" and "Lie 
## and transformation groups". 
##- The software includes a variety of homotopy operators for the deRham and variational bicomplexes; extensive capabilities for computing with the Newman-Penrose and spinor formalisms 
## in "general relativity"; programs for analyzing the structure of general and semi-simple Lie algebras; programs for finding symmetries of tensor fields and other geometric structures;
##  and programs for construction of a solvable Lie group from its Lie algebra. 
##- Computations may be performed in user specified frames. One can also compute with "abstract differential forms", that is, with differential forms and their structure equations defined without reference to 
## any underlying system of coordinates.
##- Also included are extensive tables of Lie algebras, Lie algebras of vectors, differential equations, and space-time metrics taken from the mathematics and mathematical physics literature.
##- The 'DifferentialGeometry' package includes a comprehensive collection of "Lessons" and "Tutorials".  The lessons worksheets provide a systematic approach to 
## learning the commands in the DifferentialGeometry, Tensor, LieAlgebras and JetCalculus sub-packages.  Each lesson contains a set of exercises which range in difficult from simple 
## computational exercises to programming exercises.  Solutions are given. The tutorials present specialized applications of the DifferentialGeometry package.
##- The 'DiffferentialGeometry' package is based upon the Vessiot package developed by I. M. Anderson, Florin Catrina, Sydney Chamberlain, Cinnamon Hillyard, Jeff Humphries, Jamie Jorgensen, 
## Charles Miller, and Charles Torre at Utah State University. The redesign and expansion of Vessiot to 'DifferentialGeometry' for 
## Maple 11 was done by I. M. Anderson and E. S. Cheb-Terrab.
##- Each command in the 'DifferentialGeometry' package can be accessed by using either the "long form" or the "short form" of the command name in the command calling sequence. 
##
##SECTION List of the DifferentialGeometry commands and sub-packages
##-(nolead) The following is a list of available commands and sub-packages. 
##TABLE(width = 500, border = 0, alignment = center, colwidth = 1|1|1)
##ROW  "&algmult" | "&minus" | "&mult"
##ROW  "&plus" | "&tensor" | "&wedge"
##ROW  "Annihilator" | "ApplyTransformation" | "ChangeFrame"
##ROW  "ComplementaryBasis" | "ComposeTransformations" | "Convert" 
##ROW  "DGIm" | "DGImageSpace" | "DGNullSpace"
##ROW  "DGRe" | "DGbasis" | "DGconjugate"
##ROW  "DGsetup" | "DGsolve" | "DGzip"
##ROW  "DeRhamHomotopy" | "DualBasis" | "ExteriorDerivative"
##ROW  "ExteriorDifferentialSystems" | "Flow" | "FrameData"
##ROW  "GetComponents" | "GroupActions" | "Hook"
##ROW  "InfinitesimalTransformation" | "IntegrateForm" | "IntersectSubspaces"
##ROW  "InverseTransformation" | "JetCalculus" | "Library"
##ROW  "LieAlgebras" | "LieBracket" | "LieDerivative"
##ROW  "Preferences" | "Pullback" | "PullbackVector"
##ROW  "Pushforward" | "RemoveFrame" | "Tensor"
##ROW  "Tools" | "Transformation" | "evalDG"
##ENDTABLE
##
##-(nolead) A brief description of the package's commands is as follows.
##- To display the help page for a particular DifferentialGeometry command, see "Getting Help with a Command in a Package".
##- "&minus": find the difference between two vectors, differential forms or tensors.
##- "&mult": multiply a vector, differential form or tensor by a Maple expression.
##- "&plus": add two vectors, differential forms or tensors.
##- "&tensor": calculate the tensor product of two tensors.
##- "&wedge": calculate the exterior product of two differential forms.
##- "Annihilator": find the subspace of vectors (or 1-forms) whose interior product with a given list of 1-forms (or vectors) vanish.
##- "ApplyTransformation": evaluate a transformation at a point.
##- "ChangeFrame": change the current or active frame.
##- "ComplementaryBasis": extend a basis for subspace to a basis for larger subspace.
##- "ComposeTransformations": compose a sequence of two or more transformations.
##- "Convert": change the presentations or internal representations of various geometric objects.
##- "DGIm": find the the imaginary part of a vector, a tensor or differential form; find the imaginary part of a quaternion or octonion
##- "DGImageSpace": find the image space of a linear transformation acting on a vector space of vectors, differential forms, tensors
##- "DGNullSpace": find the null space of a linear transformation acting on a vector space of vectors, differential forms, tensors
##- "DGRe": find the the real part of a vector, tensor or differential form; find the real part of a quaternion or octonion
##- "DGbasis": select a maximal linearly independent list of elements from a list of vectors, forms or tensors.
##- "DGconjugate": find the the complex conjugate of a vector, tensor or differential form; find the conjugate of a quaternion or octonion
##- "DGsetup": initialize a coordinate system, frame, or Lie algebra.
##- "DGsolve": solve a list of tensor equations for an unknown list of tensors
##- "DGzip": form a linear combination, wedge product or tensor product of a list of vectors, forms or tensors.
##- "DeRhamHomotopy": the homotopy operator for the exterior derivative operator (the de Rham complex).
##- "DualBasis": calculate the dual basis to a given basis of vectors or 1-forms.
##- "evalDG": evaluate a 'DifferentialGeometry' expression.
##- "ExteriorDerivative": take the exterior derivative of a differential form.
##- "Flow": calculate the 1-parameter group of diffeomorphisms (the flow) of a vector field.
##- "FrameData": calculate the structure equations for a generic (anholonomic) frame.
##- "GroupActions": a package for Lie groups and group actions on manifolds.
##- "Hook": the interior product of a vector or a list of vectors with a differential form.
##- "InfinitesimalTransformation": compute the Lie algebra of infinitesimal generators for an action of a Lie group on a manifold.
##- "IntegrateForm": evaluate a p-fold iterated integral of a differential p-form.
##- "IntersectSubspaces": find the intersection of a list of vector subspaces of vectors, forms or tensors.
##- "InverseTransformation": find the inverse of a transformation.
##- "JetCalculus": a package for the variational calculus on jet spaces.
##- "Library": a package of databases of Lie algebras, vector field systems, differential equations, and exact solutions in general relativity.
##- "LieAlgebras": a package for the symbolic analysis of Lie algebras.
##- "LieBracket": calculate the Lie bracket of two vector fields.
##- "LieDerivative": calculate the Lie derivative of a vector field, differential form or tensor with respect to a vector field.
##- "GetComponents": find the coefficients of a vector, differential form or tensor with respect to a list of vectors, differential forms or tensors.
##- "Preferences": set worksheet preferences for the 'DifferentialGeometry' package.
##- "Pullback": pullback a differential p-form by the Jacobian of a transformation.
##- "PullbackVector": find (if possible) a vector field whose pushforward by the Jacobian of a given transformation is a given vector field.
##- "Pushforward": pushforward a vector or a vector field by the Jacobian of a transformation.
##- "RemoveFrame": remove a frame from a Maple session.
##- "Tensor": a package for tensor analysis within the DifferentialGeometry environment.
##- "Tools": a small utility package for DifferentialGeometry.
##- "Transformation": create a transformation or mapping from one manifold to another.
##
##
##SEEALSO
##- "DifferentialGeometry", "JetCalculus", "Library", "LieAlgebras", "Tensor", "Tools"
##
##
##XREFMAP
##- "long form" : Help:UsingPackages#longform
##- "short form" : Help:UsingPackages#shortform
##- "tensor analysis" :  Help:DifferentialGeometry[Tensor]
##- "calculus on jet spaces" : Help:DifferentialGeometry[JetCalculus]
##- "Lie algebras" : Help:DifferentialGeometry[LieAlgebras]
##- "Lie and transformation groups" : Help:DifferentialGeometry[GroupActions]
##- "abstract differential forms" : Help:DifferentialGeometry/WorkingWithAbstractForms
##- "general relativity" : Help:DifferentialGeometry/OverviewOfGeneralRelativity
##- "semi-simple Lie algebras" : Help:DifferentialGeometry/AnalyzingASimpleLieAlgebra
##- "Getting Help with a Command in a Package" : Help:getting_help#gethelp
##- "&algmult" : Help:DifferentialGeometry[AlgebraicOperations]
##- "&minus" : Help:DifferentialGeometry[AlgebraicOperations]
##- "&mult" : Help:DifferentialGeometry[AlgebraicOperations]
##- "&plus" : Help:DifferentialGeometry[AlgebraicOperations]
##- "&tensor" : Help:DifferentialGeometry[AlgebraicOperations]
##- "&wedge" : Help:DifferentialGeometry[AlgebraicOperations]
##- "Annihilator" : Help:DifferentialGeometry[Annihilator]
##- "ApplyTransformation" : Help:DifferentialGeometry[ApplyTransformation]
##- "ChangeFrame" : Help:DifferentialGeometry[ChangeFrame]
##- "ComplementaryBasis" : Help:DifferentialGeometry[ComplementaryBasis]
##- "ComposeTransformations" : Help:DifferentialGeometry[ComposeTransformations]
##- "Convert" : Help:DifferentialGeometry[Convert]
##- "DeRhamHomotopy" : Help:DifferentialGeometry[DeRhamHomotopy]
##- "DGbasis" : Help:DifferentialGeometry[DGbasis]
##- "DGcongjugate" : Help:DifferentialGeometry[DGconjugate] 
##- "DGIm" : Help:DifferentialGeometry[DGconjugate] 
##- "DGImageSpace" : Help:DifferentialGeometry[DGNullSpace] 
##- "DGNullspace" : Help:DifferentialGeometry[DGNullSpace] 
##- "DGRe" : Help:DifferentialGeometry[DGconjugate] 
##- "DGsolve" : Help:DifferentialGeometry[DGsolve] 
##- "DGsetup" : Help:DifferentialGeometry[DGsetup]
##- "DGzip" : Help:DifferentialGeometry[DGzip]
##- "DualBasis" : Help:DifferentialGeometry[DualBasis]
##- "ExteriorDerivative" : Help:DifferentialGeometry[ExteriorDerivative]
##- "Flow" :  Help:DifferentialGeometry[Flow]
##- "FrameData" : Help:DifferentialGeometry[FrameData]
##- "GetComponents" : Help:DifferentialGeometry[GetComponents]
##- "GroupActions" : Help:DifferentialGeometry[GroupActions]
##- "Hook" : Help:DifferentialGeometry[Hook]
##- "InfinitesimalTransformation" : Help:DifferentialGeometry[InfinitesimalTransformation]
##- "IntegrateForm" : Help:DifferentialGeometry[IntegrateForm]
##- "IntersectSubspaces" : Help:DifferentialGeometry[IntersectSubspaces]
##- "InverseTransformation" : Help:DifferentialGeometry[InverseTransformation]
##- "JetCalculus" : Help:DifferentialGeometry[JetCalculus]
##- "Lessons " : Help:DifferentialGeometry[LessonsAndTutorials][LessonsOverview]
##- "Library" : Help:DifferentialGeometry[Library]
##- "LieAlgebras" : Help:DifferentialGeometry[LieAlgebras]
##- "LieBracket" : Help:DifferentialGeometry[LieBracket]
##- "LieDerivative" : Help:DifferentialGeometry[LieDerivative]
##- "Preferences" : Help:DifferentialGeometry[Preferences]
##- "Pullback" : Help:DifferentialGeometry[Pullback]
##- "PullbackVector" : Help:DifferentialGeometry[PullbackVector]
##- "Pushforward" : Help:DifferentialGeometry[Pushforward]
##- "RemoveFrame" : Help:DifferentialGeometry[RemoveFrame]
##- "Tensor" : Help:DifferentialGeometry[Tensor]
##- "Tools" : Help:DifferentialGeometry[Tools]
##- "Transformation" : Help:DifferentialGeometry[Transformation]
##- "Tutorials " : Help:DifferentialGeometry[LessonsAndTutorials][TutorialsOverview]
##- "evalDG" : Help:DifferentialGeometry[evalDG]

