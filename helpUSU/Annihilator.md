##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Annihilator
##TITLE(halfline="find the subspace of vectors (or 1-forms) whose interior product with a given list of 1-forms (or vectors) vanishes") DifferentialGeometry[Annihilator]
##CALLINGSEQUENCE
##-      Annihilator('S', 'T')
##PARAMETERS
##- 'S' : a list of vectors or a list of 1-forms
##- 'T' : (optional) a list of 1-forms if 'S' is a list of vectors or a list of vectors if 'S' is a list of 1-forms
##DESCRIPTION
##- Let 'S 'be a list of 1-forms and 'T' a list of vectors.  Then 'Annihilator(S, T)' calculates the subspace of vectors 'X' in the span of 'T' such that 'alpha(X) = 0' for all 'alpha in S'.
##- Let 'S' be a list of vectors and 'T' a list of 1-forms.  Then 'Annihilator(S, T)' calculates the subspace of 1-forms 'alpha' in the span of 'T' such that 'alpha(X) = 0' for all 'X in S'.
##- If the optional argument 'T' is not given, then 'T' is taken to be the standard basis for the tangent space or cotangent space for the manifold 'M' on which the elements of 'S' are defined.
##- This command is part of the DifferentialGeometry package, and so can be used in the form Annihilator(...) only after executing the command with(DifferentialGeometry).  
## It can always be used in the long form DifferentialGeometry:-Annihilator.
##EXAMPLES
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##> DGsetup([x, y, z, w], M):
##-(nolead)
##-(nolead) **Example 1.**
##-(nolead) Calculate the annihilator of the set of 1-forms 'S1' relative to subspaces 'T1', 'T2', and the full tangent space.
##> S1 := [dx, dy];
##> T1 := [D_x, D_y, D_z];
##> T2 := [D_x, D_y];
##> Annihilator(S1, T1);
##> Annihilator(S1, T2);
##> Annihilator(S1);
##-(nolead)  
##- **Example 2.**
##- Calculate the annihilator of the set of vectors 'S2' and 'S3'.
##> S2 := [D_y];
##> Annihilator(S2);
##> S3 := evalDG([D_x - 2*D_y + D_z, D_y + 3*D_z - D_w]);
##> A3 := Annihilator(S3);
##- Let us check this result.
##> Matrix(2, 2, (i, j) -> Hook(S3[i], A3[j]));
##SEEALSO
##- "DifferentialGeometry", "DualBasis", "Hook"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "DualBasis" : Help:DifferentialGeometry/DualBasis
##- "Hook" : Help:DifferentialGeometry/Hook
