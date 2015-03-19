##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/DualBasis
##TITLE DifferentialGeometry[DualBasis]
##HALFLINE calculate the dual basis to a given basis of vectors or 1-forms
##CALLINGSEQUENCE
##- DualBasis('S', 'T')
##PARAMETERS
##- S : a list of independent vectors or 1-forms
##- T : (optional) a list of  independent 1-forms if 'S' is a list of vectors; a list of independent vectors if 'S' is a list of 1-forms
##DESCRIPTION
##- Let 'S = [X\_1, X\_2, ..., X\_n] 'be a list of vectors, defined on a manifold 'M', which define a basis for the tangent space at a point 'p'.  
## Then the dual basis for the cotangent space at 'p' is the list of 1-forms 'B = [alpha\_1, alpha\_2, ..., alpha\_n]' such that 'alpha\_i(X\_j) = delta\_ij = {0 if i <> j and 1 if i = j}'. 
## The command 'DualBasis(S)' will return the list of 1-forms 'B'.
##- Let 'S = [alpha\_1, alpha\_2, ..., alpha\_n]' be a list of 1-forms, defined on a manifold 'M', which define a basis for the cotangent space at a point 'p'.  
##  Then the dual basis for the tangent space at 'p' is the list of vectors 'B = [X\_1, X\_2, ..., X\_n]' such that 'alpha\_i(X\_j) = delta\_ij'. 
##  The command 'DualBasis(S)' will return the list of 1-forms 'B'.
##- More generally, let 'S = [X\_1, X\_2, ..., X\_k]' be a list of independent vectors defined on a manifold 'M' and let 
## 'T = [theta\_1, theta\_2, ..., theta\_k] 'be a list of independent 1-forms which are transverse to 'S' in the sense that 
## the 'k x k' matrix 'A\_ij = alpha\_i(X\_j)' is non-singular.  In this case 'DualBasis(S, T)' returns a list of 1-forms 'B = [alpha\_1, alpha\_2, ..., alpha\_k]' 
## such that 'span(B) = span(T)' and 'alpha\_i(X\_j)  = delta\_ij'.
##- This command is part of the DifferentialGeometry package, and so can be used in the form DualBasis(...) only after executing the command with(DifferentialGeometry).  
## It can always be used in the long form DifferentialGeometry:-DualBasis.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##- Initialize a 3-dimensional manifold 'M' with coordinates '[x, y, z]'.
##> DGsetup([x, y, z], M):
##-(nolead) 
##-(nolead) **Example 1.**
##> S1 := [D_x, D_y ,D_z];
##> B1 := DualBasis(S1);
##-(nolead)
##-(nolead) **Example 2.**
##> S2 := evalDG([D_x + D_y - D_z, D_y - D_z, D_x + D_y + 3*D_z]);
##> B2 := DualBasis(S2);
##-(nolead) We check the answer by computing the interior products of 'S2[i]' with 'B2[j]'.
##> Matrix(3, 3, (i, j) -> Hook(S2[i], B2[j]));
##-(nolead)
##-(nolead) **Example 3.**
##-(nolead) The dual basis for the forms 'B2' from Example 2 are the vectors 'S2'.
##> B3 := DualBasis(B2);
##-(nolead)
##-(nolead) **Example 4.**
##-(nolead) Calculate the dual basis to the vectors 'S3' relative to the subspace of 1-forms 'T3'.
##> S4 := evalDG([D_x + D_y + D_z, D_x - 2*D_y + D_z]);
##> T4 := evalDG([dx + dy + dz, dx - 2*dy + 3*dz]);
##> B4 := DualBasis(S4, T4);
##> Matrix(2, 2, (i, j) -> Hook(S4[i], B4[j]));

##SEEALSO
##- "DifferentialGeometry", "Annihilator", "ComplementaryBasis", "DGbasis", "CanonicalBasis"

##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Annihilator" : Help:DifferentialGeometry/Annihilator
##- "ComplementaryBasis" : Help:DifferentialGeometry/ComplementaryBasis
##- "DGbasis" : Help:DGbasis
##- "CanonicalBasis" : Help:DifferentialGeometry/Tools/CanonicalBasis
