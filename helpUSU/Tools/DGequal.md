##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Tools/DGequal
##TITLE DifferentialGeometry:-Tools[DGequal]
##CALLINGSEQUENCE
##-      DGequal('S1', 'S2')
##PARAMETERS
##-    S1, S2 : two lists of vectors, differential forms, or tensors; two transformations; two Lie algebra data structures; or two representations
##DESCRIPTION
##- Let 'S1' and  'S2' be two lists of vectors, differential forms, or tensors. If every element of 'S1' is in the span of 'S2 'and every element of 'S1' is in the span of 'S2', then 'DGequal(S1, S2)' returns true and otherwise false.
##- If the two transformations 'Phi1' and 'Phi2' have the same domain frame, range frame, and the same coordinate expressions, 
## then 'DGequal(Phi1, Phi2)' returns true and otherwise false.  The command 'DGequal(Phi1, Phi2)' computes the differences between the Jacobian matrices and the coordinate equations for the two transformations 'Phi1 'and 'Phi2' and tests if these differences are zero.
##- This command is part of the DifferentialGeometry:-Tools package, and so can be used in the form DGequal(...) only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.  It can always be used in the long form DifferentialGeometry:-Tools:-DGequal.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tools): with(LieAlgebras):
##-(nolead) 
##- **Example 1.**
##-(nolead)  First initialize a 4-dimensional manifold 'M' with coordinates '[x, y, z, w]'.
##> DGsetup([x, y, z, w], M):
##-(nolead)  
##-(nolead)  Show that the vector subspaces spanned by the lists of vectors 'S1' and 'S2' are the same.
##> S1 := evalDG([D_x, D_y, D_x + D_y, D_x + D_y + D_z]);
##> S2 := evalDG([D_x, D_y, D_z]);
##> DGequal(S1, S2);
##- Show that the subspaces of differential forms spanned by the lists of 2-forms 'S3' and 'S4' are not the same.
##> S3 := evalDG([dx &w dy, dx &w dz]);
##> S4 := evalDG([dx &w dy, dy &w dz]);
##> DGequal(S3, S4);
##-(nolead)  
##-(nolead) **Example 2.**
##-(nolead)  First initialize manifolds 'M' and 'N' with coordinates '[x, y]' and '[u, v]'.
##> DGsetup([x, y], M): DGsetup([u, v], N):
##-(nolead) 
##- Show that the transformations 'Phi1' and 'Phi2' are the same.
##> Phi1 := Transformation(M, N, [u = 1/x + 1/y, v = x*y]);
##> Phi2 := Transformation(M, N, [u = (x + y)/(x*y), v = x*y]);
##> DGequal(Phi1, Phi2); 
##-(nolead)  Show that the transformations 'Phi3 'and 'Phi4' are not the same without assuming that 'x > 0'.
##> Phi3 := Transformation(M, N, [u = sqrt(x^2), v = 0]);
##> Phi4 := Transformation(M, N, [u = x, v = 0]);
##> DGequal(Phi3, Phi4);
##> DGequal(Phi3, Phi4) assuming x > 0;
##-(nolead)  
##-(nolead)  **Example 3.**
##-(nolead)  Define two Lie algebras data structures. Check that they are equal.
##> A := [Matrix([[1,0],[0,-1]]), Matrix([[0, 1], [0, 0]]), Matrix([[0,0], [1,0]])];
##> LD1 := LieAlgebraData(A, alg1);
##> LD2 := LieAlgebraData([[v1, v2] = 2*v2, [v1, v3] = -2*v3, [v2, v3] = v1], [v1, v2, v3], alg1);
##> DGequal(LD1, LD2);
##-(nolead) 
##-(nolead)  **Example 4.**
##-(nolead)  Define two representations of a Lie algebra and test for equality.
## First define the Lie algebra.
##> L := _DG([["LieAlgebra", A1, [3]], [[[2, 3, 1], 1], [[1, 3, 2], - 1], [[1, 2, 3], 1]]]);
##> DGsetup(L); 
##-(nolead)  Define the representation space V.
##> DGsetup([x1, x2, x3], V);
##> rho1 := Representation(A1, V, Adjoint(A1));
##> DGequal(rho1, rho1); 
##-(nolead)  Make a change of basis in the representation space.
##> rho2 := ChangeRepresentationBasis(rho1, [D_x1, D_x2, D_x3], V1); 
##-(nolead)  The representations 'rho1' and 'rho2' are equivalent but they are not equal.
##> DGequal(rho1, rho2);
##SEEALSO 
##- "DifferentialGeometry", "Tools", "LieAlgebras", "LieAlgebraData" "Representation", "Transformation"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "LieAlgebras" : Help:DifferentialGeometry/LieAlgebras
##- "LieAlgebraData" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData
##- "Representation" : Help:DiffeentialGeometry/LieAlgebras/Representation
##- "Transformation" : Help:DifferentialGeometry/Transformation
