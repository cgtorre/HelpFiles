##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/DGbasis
##TITLE DifferentialGeometry[DGbasis]
##HALFLINE calculate the dual basis to a given basis of vectors or 1-forms
##CALLINGSEQUENCE
##-      DGbasis('S', 'option')
##PARAMETERS
##- S : a list of vectors, forms or tensors
##- option : the keyword argument method = \"real\"
##DESCRIPTION
##- Let 'S = [S\_1, S\_2, ..., S\_k]' be a list of  vectors, matrices, differential forms, or tensors. Then 'DGbasis(S)' returns a sublist 'B = [S\_i\_1, S\_i\_2, ..., S\_i\_r] 'of 'S 'such that the elements of 'B 'define a basis for the subspace spanned by the elements of 'S'.  Thus the elements of 'B' are linearly independent and 'span(S) = span(B)'.
##- With the  keyword argument method = \"real\", the set 'S' is viewed as a vector space of vectors, forms or tensors over the real numbers and the basis is calculated using real number coefficients instead of general expression (function) coefficients.
##- This command is part of the DifferentialGeometry package, and so can be used in the form DGbasis(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-DGbasis.
##EXAMPLES     ##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead)
##- Initialize a 4-dimensional manifold 'M' with coordinates '[x, y, z, w]'.
##> DGsetup([x, y, z, w], M):
##-(nolead) 
##-(nolead) **Example 1.**
##-(nolead) Find a basis 'B1' for the span of the vectors in 'S1'.
##> S1 := evalDG([D_x, D_x + D_y, D_y, 0 &mult D_x, D_y - D_z, D_z, D_x + D_y + D_w]);
##> B1 := DGbasis(S1);
##-(nolead) Use the "GetComponents" command to check that each vector in 'S' is a unique linear combination of the vectors in 'B'. ("GetComponents" returns the coefficients of the vectors in 'S' as linear combination of the vectors in 'B'.  If one of the vectors in 'S' is not a linear combination of the vectors in 'B', an empty list '[]' is returned).
##> GetComponents(S1, B1);
##-(nolead) The basis 'B1' is not the simplest basis for 'S1'.  Another choice of basis for 'S1' can be found using the command "CanonicalBasis".
##> Tools:-CanonicalBasis(B1, [D_x, D_y, D_z, D_w]);
##-(nolead) 
##-(nolead) **Example 2.**
##-(nolead) Find a basis for the span of the tensors in 'S2'.
##> S2 := evalDG([dx &t dx, dy &t dx, dx &t dx + dy &t dx, dy &t dy]);
##> DGbasis(S2); 
##-(nolead) **Example 3.**
##- 'DGbasis' also accepts a list of Matrices or Vectors.
##> S3 := [Matrix([[0, 1], [0, 0]]), Matrix([[1, 0], [0, 1]]), Matrix([[1, 1], [0, 1]]), Matrix([[1, 0], [0, - 1]])];
##-(nolead) 
##> DGbasis(S3); 
##-(nolead) **Example 4.**
##> S4 := evalDG([D_x, x*D_x,  (3*x -4)*D_x]);
##-(nolead) Here is the basis for 'S4' using function coefficients.
##> DGbasis(S4);
##-(nolead) Here is the basis for 'S4' using real number coefficients.
##> DGbasis(S4, method = "real");

##SEEALSO
##- "DifferentialGeometry", "CanonicalBasis", "GetComponents"

##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "CanonicalBasis" : Help:DifferentialGeometry/Tools/CanonicalBasis
##- "GetComponents" : Help:DifferentialGeometry/GetComponents
