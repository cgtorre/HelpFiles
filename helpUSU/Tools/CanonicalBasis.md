##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Tools/CanonicalBasis
##TITLE DifferentialGeometry:-Tools[CanonicalBasis]
##CALLINGSEQUENCE
##-      CanonicalBasis('S',' T')
##PARAMETERS
##- S : a list of vectors, forms, or tensors
##- T : a list of vectors, forms, or tensors, the span of 'S' must be contained in the span of 'T'.
##DESCRIPTION
##- The command 'CanonicalBasis(S, T)' will return a list 'W'  of vectors, forms or tensors such that [i] 'span(S) = span(W)' 
## and [ii] the matrix whose rows are the coefficients of the elements of 'W 'with respect to 'T 'is in reduced row echelon form.
##- In the typical use of this command, 'S' is a list of vectors or 1-forms on a manifold 'M 'and 'T' is the standard basis for the tangent space or cotangent space of 'M'.
##- The use of this command can dramatically simplify subsequent computations with the subspace spanned by 'S'.
##- This command is part of the DifferentialGeometry:-Tools package, and so can be used in the form CanonicalBasis(...) only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.  It can always be used in the long form DifferentialGeometry:-Tools:-CanonicalBasis.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) Define a manifold M with local coordinates [x, y, z, w].
##> DGsetup([x, y, z, w], M):
##-(nolead) 
##-(nolead) **Example 1.**
##- Define a 3-dimensional subspace of vectors by the span of 'S' and compute a simpler base for this subspace relative to the coordinate basis 'T' for the tangent space of 'M'.
##> S1 := evalDG([D_x - D_y, D_x + D_y, D_x + D_y + D_w]);
##> T1 := [D_x, D_y, D_z, D_w];
##> W1 := CanonicalBasis(S1, T1); 
##-(nolead) We use the command 'DGEqual' to check that the span of 'S' and 'W' agree.
##> DGequal(S1, W1);
##-(nolead) **Example 2.**
##- We use the same vectors 'S' as in Example 1 but reverse the ordering of the vectors in the basis 'S'.
##> S2 := evalDG([D_x - D_y, D_x + D_y, D_x + D_y + D_w]);
##> T2 := [D_w, D_z, D_y, D_x];
##> W2 := CanonicalBasis(S2, T2); 
##-(nolead) We note that the matrix of coefficients of 'W' with respect to 'T' is in reduced row echelon form.
##> A := Matrix(GetComponents(W2, T2));
##-(nolead) 
##-(nolead) **Example 3.**
##-(nolead) Find a canonical basis for the space of 2-forms spanned by 'S3'.
##> S3 := evalDG([dx &w dy + dy &w dz - dy &w dw, dx &w dy + dy &w dy + dy &w dz, dy &w dz + dy &w dw]);
##> T3 := GenerateForms([[dx, dy, dz, dw]], [2]);
##> W3 := CanonicalBasis(S3, T3);
##> DGequal(S3, W3);
##SECTION See Also 
##- "DifferentialGeometry", "Tensor", "Tools", "DGequal", "GenerateForms", "GenerateTensors", "GetComponents"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tensor" : Help:DifferentialGeometry/Tensor
##- "Tools" : Help:DifferentialGeometry/Tools
##- "DGequal" : Help:DifferentialGeometry/Tools/DGequal
##- "GenerateForms" : Help:DifferentialGeometry/Tools/GenerateForms
##- "GenerateTensors" : Help:DifferentialGeometry/Tensor/GenerateTensors
##- "GetComponents" : Help:DifferentialGeometry/GetComponents
