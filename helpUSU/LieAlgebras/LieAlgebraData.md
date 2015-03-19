##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/LieAlgebras/LieAlgebraData
##TITLE LieAlgebras[LieAlgebraData]
##HALFLINE convert different realizations of a Lie algebra to a Lie algebra data structure
##CALLINGSEQUENCE
##-      LieAlgebraData('LieAlgebraPresentation')
##PARAMETERS
##- LieAlgebraPresentation : one of several different formats for defining a Lie algebra
##DESCRIPTION
##- In the 'LieAlgebras' package, the command 'DGsetup' is used to initialize a Lie algebra -- that is, to define the basis elements for the Lie algebra and its dual and to store the structure constants for the Lie algebra in memory.  The first argument for 'DGsetup' is a Lie algebra data structure which contains the structure constants in a standard format used by the 'LieAlgebras' package.
##- The purpose of the function 'LieAlgebraData' is to convert various different presentations of a Lie algebra, which are commonly used in differential geometry and Lie theory, into the standard Lie algebra data structure required by the 'DGsetup' command.
##- The types of Lie algebra presentations which can currently be converted to a Lie algebra data structure are:
##
##TABLE(width = 550, border = 0, alignment = center, colwidth = 12|10|10)
##ROW "FormStructureEquations" | "Grading" | "LieAlgebraName" 
##ROW "MatrixAlgebra" |"StructureConstants" | "Subalgebra"   
##ROW "VectorFields"  | "VectorStructureEquations" | `` 
##ENDTABLE
## 
##- The command 'LieAlgebraData' returns a Lie algebra data structure.  The structure equations defined by this data structure are displayed.                      
##- The command 'LieAlgebraData' is part of the DifferentialGeometry:-LieAlgebras package.  It can be used in the form LieAlgebraData(...) only after executing the commands with(DifferentialGeometry) and with(LieAlgebras), but can always be used by executing DifferentialGeometry:-LieAlgebras:-LieAlgebraData(...).
##EXAMPLES     ##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(LieAlgebras):
##- 
##- Example 1.  LieAlgebraData(StructureConstants)
##- In this example we create a 3 dimensional Array, 'C', of structure constants and use this Array to create a Lie algebra data structure for a Lie algebra called 'Ex1'.
##> C := Array(1..3, 1..3, 1..3, 0):
##> C[1, 3, 1] := 1: C[3, 1, 1] := -1: C[2, 3, 2] := 1: C[3, 2, 2] := -1:
##> L1 := LieAlgebraData(C, Ex1);
##- 
##- Example 2.  LieAlgebraData(VectorStructureEquations)
##- In this example we create a Lie algebra data structure for a Lie algebra called 'Ex2' from a list of structure equations for the Lie brackets.
##>(quote) VectStrEq := [[x1, x3] = x1, [x2, x3] = x1 + x2], [x1, x2, x3];
##> L2 := LieAlgebraData(VectStrEq, Ex2);
##- 
##- Example 3.  LieAlgebraData(FormStructureEquations)
##- In this example we create a Lie algebra data structure for a Lie algebra called 'Ex3' from a list of structure equations for the exterior derivatives of the dual 1-forms.
##>(quote) FormStrEq := [d(theta1) = -theta1 &w theta2, d(theta2) = - theta2 &w theta3, d(theta3) = 0], [theta1, theta2, theta3];
##> L3 := LieAlgebraData(FormStrEq, Ex3);
##- 
##- Example 4.  LieAlgebraData(MatrixAlgebra)
##- In this example we create a Lie algebra data structure for a Lie algebra called 'Ex4' from a list of matrices.
##> MatrixAlg := [Matrix([[0, 1], [0, 0]]), Matrix([[1, 0], [0, -1]]), Matrix([[0, 0], [1, 0]])];
##> L4 := LieAlgebraData(MatrixAlg, Ex4);
##- 
##- Example 5.  LieAlgebraData(LieAlgebraName)
##- In this example we create a Lie algebra data structure for a Lie algebra called 'Ex5' from a previously initialized Lie algebra.
##- First we initialize a Lie algebra 'Ex5'.
##> L5 := _DG([["LieAlgebra", Ex5, [3]], [[[1, 2, 1], 1]]]):
##> DGsetup(L5);
##- 
##- Applying 'LieAlgebraData' to 'Ex5' gives back the Lie algebra data structure we started from.
##> LieAlgebraData(Ex5, copyEx5);
##- 
##- Example 6.  LieAlgebraData(Subalgebra, \"LieAlgebraData\")
##- In this example we create a Lie algebra data structure from a subalgebra of a Lie algebra.
##- First we initialize a Lie algebra 'Alg5'.
##> L := _DG([["LieAlgebra", Alg5, [4]], [[[1, 4, 1], 2], [[2, 3, 1], 1], [[2, 4, 2], 1], [[3, 4, 3], 1]]]);
##>> DGsetup(L):
##- 
##- The vectors '[e1, e2, e3]' define a Lie subalgebra which we wish to initialize as a Lie algebra in its own right.
##> S1 := [e1, e2, e3]:
##> L6 := LieAlgebraData(S1, Ex6);
##SEEALSO
##- "DifferentialGeometry", "LieAlgebras", "Query"
##XREFMAP
##- "FormStructureEquations" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData/FormStructureEquations
##- "Grading" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData/Grading
##- "LieAlgebraName" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData/LieAlgebraName
##- "MatrixAlgebra" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData/MatrixAlgebra
##- "StructureConstants" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData/StructureConstants
##- "Subalgebra" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData/Subalgebra
##- "VectorFields" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData/VectorFields
##- "VectorStructureEquations" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData/VectorStructureEquations
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "LieAlgebras" : Help:DifferentialGeometry/LieAlgebras
##- "Query" : Help:DifferentialGeometry/LieAlgebras/Query
