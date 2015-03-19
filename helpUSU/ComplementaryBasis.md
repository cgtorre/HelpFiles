##PROCEDURE(help, nospec, postprocess="helpmw_execute") DifferentialGeometry/ComplementaryBasis
##TITLE DifferentialGeometry[ComplementaryBasis]
##HALFLINE extend a basis for a subspace to a basis for a larger subspace
##CALLINGSEQUENCE
##- ComplementaryBasis('S', 'T')
##PARAMETERS
##- S, T : lists of vectors, differential p-forms, or tensors (of the same type)
##DESCRIPTION
## The procedure 'ComplementaryBasis(S, T)' returns a list 'C' of vectors, differential p-forms or tensors such that the span of '[S, C]' 
## equals the span of the vectors, differential p-forms or tensors  defined by 'T'.
##- This command is part of the DifferentialGeometry package, and so can be used in the form ComplementaryBasis(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-ComplementaryBasis.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":    
##> with(DifferentialGeometry):
##- Initialize a 5-dimensional manifold 'M' with coordinates '[x, y, z, u, v]'.
##> DGsetup([x, y, z, u, v], M):
##- 
##- **Example 1.**
##> S1 := [D_x, D_y];
##> T1 := [D_x, D_y, D_z];  
##> C1 := ComplementaryBasis(S1, T1);
##- 
##- **Example 2.**
##- Note that a basis for 'S2' is '[D\_x, D\_y]' and a basis for 'T2' is '[D\_x, D\_y, D\_x + D\_z, D\_u]'.
##> S2 := [D_x, D_y, D_x + D_y];
##> T2 := evalDG([D_x, D_y, D_x + D_z, D_x - D_y, D_z, D_u]);  
##> C2 := ComplementaryBasis(S2, T2);
##- 
##- **Example 3.**
##- In most applications the subspace spanned by the first argument 'S' will be a subspace of the span of the second argument 'T'.  However, the procedure works in the more general context described above.
##> S3 := [D_x, D_y];
##> T3 := [D_x, D_u, D_v];
##> C3 := ComplementaryBasis(S3, T3);
##- 
##- **Example 4.**
##- The command 'ComplementaryBasis' works with differential forms.
##> S4 := evalDG([dx &w dy, dx &w dz]);
##> T4 := evalDG([dx &w dy, dx &w dz, dx &w du, dy &w dv]);
##> C4 :=  ComplementaryBasis(S4, T4);
##- 
##- **Example 5.**
##- The command 'ComplementaryBasis' works with tensors.
##> S5 := evalDG([dx &t D_y, dx &t D_z]);
##> T5 := evalDG([dx &t D_y, dx &t D_z, dx &t D_u, dy &t D_v]);
##> C5 :=  ComplementaryBasis(S5, T5);
##SEEALSO
##- "DifferentialGeometry", "Tools", "CanonicalBasis", "DGbasis", "DualBasis"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "CanonicalBasis" : Help:DifferentialGeometry/Tools/CanonicalBasis
##- "DGbasis" : Help:DifferentialGeometry/DGbasis
##- "DualBasis" : Help:DifferentialGeometry/DualBasis
