##PROCEDURE(help) DifferentialGeometry[GroupActions]
##TITLE  Overview of the GroupActions package
##DESCRIPTION
##- The `DifferentialGeometry:-GroupActions` package provides basic symbolic capabilities for working with Lie groups, transformation groups and infinitesimal transformation groups.
##- For a given Lie algebra of vector fields (that is, an infinitesimal transformation group) on a manifold, important geometric information is provided by 
## the (infinitesimal) isotropy subalgebras, their representations on the tangent space and the "isotropy filtration". 
## This information can be calculated with the `GroupActions` package.
##- The "infinitesimal isometries" of any metric tensor can be calculated and conversely, all metric tensors invariant with respect to a given infinitesimal transformation group can be found.  
## More generally, the "infinitesimal symmetries" of any collection of vector fields, differential forms, tensor fields or connections can be found.
##- A global "Lie group" can be calculated for any solvable Lie algebra.  
## The "r-parameter transformation group" for a given r-dimensional solvable infinitesimal transformation group can be determined.
##- Invariants and differential invariants for group actions can also be determined by the method of "moving frames".
##- The `GroupActions` package is a subpackage of the DifferentialGeometry package. 
## Each command in the GroupActions package can be accessed by using either the "long form" or the "short form" of the command name in the command calling sequence.
##
##
##SECTION List of the GroupAction commands and subpackages
##-(nolead) The following is a list of available commands and subpackages. 
##TABLE(width = 500, border = 0, alignment = center, colwidth = 1|1)
##ROW "Action" | "InfinitesimalPseudoGroupNormalizer"
##ROW "InfinitesimalSymmetriesOfGeometricObjectFields" | "InvariantGeometricObjectFields"
##ROW "InvariantVectorsAndForms" | "IsotropyFiltration"
##ROW "IsotropySubalgebra" | "LieGroup"
##ROW "LiesThirdTheorem" |   "MatrixGroup"
##ROW "MovingFrames" |
##ENDTABLE
##
##
##-(nolead) A brief description of the package's commands is as follows.
##- "Action": find the action of a solvable Lie group on a manifold from its infinitesimal generators.
##- "InfinitesimalPseudoGroupNormalizer": find the normalizer of a finite dimensional Lie algebra of vector fields in an (infinite-dimensional) pseudo-Lie algebra of vector fields
##- "InfinitesimalSymmetriesOfGeometricObjectFields": find the infinitesimal symmetries (vector fields) for a collection of vector fields, differential forms or tensors.
##- "InvariantGeometricObjectFields": find the vector fields, differential forms, or tensors which are invariant with respect to a Lie algebra of vector fields.
##- "InvariantVectorsAndForms": calculate a basis of left and right invariant vector fields and differential 1-forms on a Lie group.
##- "IsotropyFiltration": find the infinitesimal isotropy filtration for a Lie algebra of vector fields.
##- "IsotropySubalgebra": find the infinitesimal isotropy subalgebra of a Lie algebra of vector fields and infinitesimal isotropy representation.
##- "LieGroup": create a module defining a Lie group.
##- "LiesThirdTheorem": find a Lie algebra of pointwise independent vector fields with prescribed structure equations (solvable algebras only).
##- "MatrixGroup": find the matrix group defined by a matrix algebra or by a matrix of 1-forms 
##- "MovingFrames": a small package for the method of moving frames.
##
##SEEALSO
##- "DifferentialGeometry", "JetCalculus", "Library", "LieAlgebras", "Tensor", "Tools"
##
##
##XREFMAP
##- "long form" : Help:UsingPackages#longform
##- "short form" : Help:UsingPackages#shortform
##- "isotropy filtration" : Help:DifferentialGeometry[GroupActions][IsotropyFiltration]
##- "infinitesimal isometries" : Help:DifferentialGeometry[GroupActions][InfinitesimalSymmetriesOfGeometricObjectFields]
##- "infinitesimal symmetries" : Help:DifferentialGeometry[GroupActions][InfinitesimalSymmetriesOfGeometricObjectFields]
##- "Lie group" : Help:DifferentialGeometry[GroupActions][LieGroup]
##- "r-parameter transformation group" : Help:DifferentialGeometry[GroupActions][Action]
##- "moving frames" :  Help:DifferentialGeometry[GroupActions][MovingFrames]
##- "Action" : Help:DifferentialGeometry[GroupActions][Action]
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "InfinitesimalSymmetriesOfGeometricObjectFields" : Help:DifferentialGeometry[GroupActions][InfinitesimalSymmetriesOfGeometricObjectFields]
##- "InvariantGeometricObjectFields" : Help:DifferentialGeometry[GroupActions][InvariantGeometricObjectFields]
##- "InvariantVectorsAndForms" : Help:DifferentialGeometry[GroupActions][InvariantVectorsAndForms]
##- "IsotropyFiltration" : Help:DifferentialGeometry[GroupActions][IsotropyFiltration]
##- "IsotropySubalgebra" : Help:DifferentialGeometry[GroupActions][IsotropySubalgebra]
##- "JetCalculus" : Help:DifferentialGeometry[JetCalculus]
##- "Library" : Help:DifferentialGeometry[Library]
##- "LieGroup" : Help:DifferentialGeometry[GroupActions][LieGroup]
##- "LiesThirdTheorem" : Help:DifferentialGeometry[GroupActions][LiesThirdTheorem]
##- "MatrixGroup" : Help:DifferentialGeometry[GroupActions][MatrixGroup]
##- "MovingFrames" : Help:DifferentialGeometry[GroupActions][MovingFrames]
##- "Tensor" : Help:DifferentialGeometry[Tensor]
##- "Tools" :  Help:DifferentialGeometry[Tools]
