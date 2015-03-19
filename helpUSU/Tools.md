##PROCEDURE(help) DifferentialGeometry[Tools]
##TITLE  Overview of the Tools package
##DESCRIPTION
##- The `DifferentialGeometry:-Tools` sub-package contains a number of utility procedures which are used primarily in the development of new DifferentialGeometry applications.
##- Each of the commands in the DifferentialGeometry:-Tools package can only be accessed by first executing with(DifferentialGeometry) and with(Tools), 
## in that order or by using the long form of the command DifferentialGeometry:-Tools:-Command(...).
##
##
##SECTION List of the Tools commands
##-(nolead) The following is a list of available commands.
##TABLE(width = 500, border = 0, alignment = center, colwidth = 1|1|1)
##ROW "&MatrixMinus" | "&MatrixMult" | "&MatrixPlus"            
##ROW "&MatrixWedge" | "CalculationHistory" | "CanonicalBasis"         
##ROW "DGbiform" | "DGform" | "DGinfo"                 
##ROW "DGmain" | "DGmap" | "DGscalar"               
##ROW "DGsimplify" | "DGtensor" | "DGvector"               
##ROW "DGvolume" | "DGzero" | "Divergence"             
##ROW "DGequal" | "GenerateForms" | "IdentityTransformation"
##ENDTABLE
##
##-(nolead) A brief description of the package's commands is as follows.
##- "&MatrixMinus": subtract two Matrices or Vectors of vector fields, differential forms, or tensors.
##- "&MatrixMult": multiply a Matrix of vectors, differential forms or tensors by a scalar or by a Matrix of scalars.
##- "&MatrixPlus": add two Matrices or Vectors of vector fields, differential forms, or tensors.
##- "&MatrixWedge": calculate the Matrix wedge product of two Matrices/Vectors of differential forms.
##- "CalculationHistory": a module to store and retrieve important intermediate computations.
##- "CanonicalBasis": calculate a standard basis for a subspace of vectors, forms, or tensors.
##- "DGbiform": create a monomial bi-form.
##- "DGform": create a monomial form.
##- "DGinfo": obtain information about a DifferentialGeometry object.
##- "DGmain": a module containing fast versions of some DifferentialGeometry procedures.
##- "DGmap": apply a procedure to the coefficients of a vector, differential form or tensor.
##- "DGscalar": create a degree 0 differential form or a rank 0 tensor.
##- "DGsimplify": simplify a vector, differential form, or tensor.
##- "DGtensor": create a monomial tensor.
##- "DGvector": create a monomial vector.
##- "DGvolume": create a top degree differential form.
##- "DGzero": create a zero vector, differential form, or tensor.
##- "Divergence": calculate the divergence of a vector field.
##- "DGequal": test if two DifferentialGeometry objects are equal.
##- "GenerateForms": create a list of differential forms.
##- "IdentityTransformation": define the identity transformation on a manifold.
##
##SEEALSO
##- "DifferentialGeometry", "GroupActions", "JetCalculus", "Library", "LieAlgebras", "Tensor"
##
##XREFMAP
##- "long form" : Help:UsingPackages#longform
##- "short form" : Help:UsingPackages#shortform  
##- "&MatrixMinus" : Help:DifferentialGeometry[Tools][MatrixOperations]
##- "&MatrixMult" : Help:DifferentialGeometry[Tools][MatrixOperations]
##- "&MatrixPlus" : Help:DifferentialGeometry[Tools][MatrixOperations]
##- "&MatrixWedge" : Help:DifferentialGeometry[Tools][MatrixOperations]
##- "CalculationHistory" : Help:DifferentialGeometry[Tools][CalculationHistory]
##- "CanonicalBasis" : Help:DifferentialGeometry[Tools][CanonicalBasis]
##- "DGbiform" : Help:DifferentialGeometry[Tools][DGbiform]
##- "DGform" : Help:DifferentialGeometry[Tools][DGform]
##- "DGinfo" : Help:DifferentialGeometry[Tools][DGinfo]
##- "DGmain" : Help:DifferentialGeometry[Tools][DGmain]
##- "DGmap" : Help:DifferentialGeometry[Tools][DGmap]
##- "DGscalar" : Help:DifferentialGeometry[Tools][DGscalar]
##- "DGsimplify" : Help:DifferentialGeometry[Tools][DGsimplify]
##- "DGtensor" : Help:DifferentialGeometry[Tools][DGtensor]
##- "DGvector" : Help:DifferentialGeometry[Tools][DGvector]
##- "DGvolume" : Help:DifferentialGeometry[Tools][DGvolume]
##- "DGzero" :  Help:DifferentialGeometry[Tools][DGzero]
##- "Divergence" : Help:DifferentialGeometry[Tools][Divergence]
##- "DGequal" : Help:DifferentialGeometry[Tools][DGequal] 
##- "GenerateForm" : Help:DifferentialGeometry[Tools][GenerateForms]
##- "GroupActions" : Help:DifferentialGeometry[GroupActions]
##- "IdentityTransformation" : Help:DifferentialGeometry[Tools][IdentityTransformation]
##- "JetCalculus" : Help:DifferentialGeometry[JetCalculus]
##- "Library" : Help:DifferentialGeometry[Library]
##- "LieAlgebras" : Help:DifferentialGeometry[LieAlgebras]
##- "Tensor" : Help:DifferentialGeometry[Tensor]
##- "Tools" : Help:DifferentialGeometry[Tools]

