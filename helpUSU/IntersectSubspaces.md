##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/IntersectSubspaces
##TITLE DifferentialGeometry[IntersectSubspaces]
##HALFLINE find the intersection of a list of vector subspaces of vectors, forms or tensors
##CALLINGSEQUENCE
##- IntersectSubspaces('S')
##PARAMETERS
##- S : a list '[A1, A2, ...]', where each 'Ai' is a list of vectors, forms or tensors
##DESCRIPTION
##- 'IntersectSubspaces(S)' computes the intersection of the subspaces spanned by the elements of the list.
##- This command is part of the DifferentialGeometry package, and so can be used in the form IntersectSubspaces(...) 
## only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-IntersectSubspaces.
##EXAMPLES    
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead) 
##-(nolead) Initialize a 4-dimensional manifold 'M' with coordinates '[x, y, z, w]'.
##> DGsetup([x, y, z, w], M):
##-(nolead) 
##-(nolead) **Example 1.**
##- Find the intersection of the three 3 dimensional subspaces spanned by 'A1', 'A2', 'A3'.
##> A1 := [D_x, D_y, D_z];
##> A2 := [D_x, D_y, D_w];
##> A3 := evalDG([D_y + D_z, D_z + D_w, D_w]);
##> IntersectSubspaces([A1, A2, A3]);
##-(nolead) 
##-(nolead) **Example 2.**
##-(nolead) Find the intersection of the subspaces of 2-forms spanned by 'B1' and 'B2'.  Check the result using the "GetComponents" command.
##> B1 := evalDG([dx &w dy + dy &w dz, dx &w dw - dy &w dz, dx &w dw + dy &w dw, dx &w dy + dx &w dz - dz &w dw]);
##> B2 := evalDG([dx &w dy - dy &w dz, dy &w dz + dz &w dw, dx &w dz + dz &w dw]);
##> C := IntersectSubspaces([B1, B2]);
##-(nolead) The command "GetComponents" returns the components of the 2-form in 'C' with respect to the 2-forms in 'B1' and 'B2'.  
## This proves that the 2-form in 'C' does indeed belong to the intersection of the spans of 'B1' and 'B2'.
##> GetComponents(C, B1);
##> GetComponents(C, B2);
##SEEALSO
##- "DifferentialGeometry", "DGbasis", "GetComponents"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "DGbasis" : Help:DifferentialGeometry/DGbasis
##- "GetComponents" : Help:DifferentialGeometry/GetComponents
