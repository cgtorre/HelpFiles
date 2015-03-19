##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Tools/MatrixOperations
##TITLE DifferentialGeometry:-Tools[&MatrixMinus, &MatrixMult, &MatrixPlus, &MatrixWedge]
##CALLINGSEQUENCE
##- 'A' &MatrixMinus 'B' - subtract two Matrices/Vectors of vectors, differential forms or tensors
##- 'A' &MatrixMult 'C' - multiply a Matrix/Vector 'A' of vectors, differential forms or tensors by a scalar 'C' or a Matrix/Vector 'C' of scalars
##- 'C' &MatrixMult 'A' - multiply a Matrix 'A 'of vectors, differential forms or tensors by a scalar 'C' or a Matrix/Vector 'C' of scalars
##- 'A' &MatrixPlus 'B' - add two Matrices/Vectors of vectors, differential forms or tensors
##- 'E' &MatrixWedge 'F' - calculate the Matrix wedge product of two Matrices/Vectors of differential forms.
##PARAMETERS
##-    A, B : two Matrices/Vectors of vectors, differential forms or tensors
##-    C    : a scalar or a Matrix/Vector of scalars
##-    E, F : two Matrices/Vectors of differential forms
##DESCRIPTION
##- These commands provide, within the 'DifferentialGeometry' environment, the basic arithmetical operations for Matrices or Vectors of: vectors, differential forms, or tensors.  They are particularly useful for curvature calculations for connections on principle bundles of matrix groups.
##- These commands are part of the DifferentialGeometry:-Tools package, and so can be used in the form described above only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##- Define a 3-dimensional manifold 'M' with coordinates '[x, y, z]'.
##> DGsetup([x, y, z], M):
##-(nolead) 
##-(nolead) **Example 1** 
##-(nolead) Define two column Vectors of 1 forms 'A', 'B'; a 2x2 matrix 'C' of scalars; a row Vector of 1 forms 'E' and a 2x2 Matrix of 1 forms 'F'.
##> A := Vector(evalDG([dx - dy, dy + dx]));
##> B := Vector(evalDG([dx + 2*dy, dx + 3*dy]));
##> C := Matrix([[1, 2], [3, 4]]);
##> E := LinearAlgebra:-Transpose(A);
##> F := Matrix(evalDG([[dx - dz, dy ], [dz, dx + dy + 3*dz]]));
##-(nolead) Perform various arithmetic operations with the quantities 'A', 'B', 'C', 'E', 'F'.
##> A &MatrixPlus B;
##> A &MatrixMinus B;
##> a &MatrixMult A;
##> C &MatrixMult A;
##> E &MatrixMult C;
##> E &MatrixWedge B;
##> C &MatrixMult F;
##> F &MatrixWedge A;
##> F &MatrixWedge F;
##SEEALSO
##- "DifferentialGeometry", "LinearAlgebra", "AlgebraicOperations", "evalDG", "DGzip", "Matrix", "Vector"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "LinearAlgebra" : Help:LinearAlgebra
##- "AlgebraicOperations" : Help:DifferentialGeometry/AlgebraicOperations
##- "evalDG" : Help:DifferentialGeometry/evalDG
##- "DGzip" : Help:DifferentialGeometry/DGzip
##- "Matrix" : Help:Matrix
##- "Vector" : Help:Vector
