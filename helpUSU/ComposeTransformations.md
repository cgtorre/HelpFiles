##PROCEDURE(help) DifferentialGeometry/ComposeTransformations
##TITLE DifferentialGeometry[ComposeTransformations]
##HALFLINE compose a sequence of two or more transformations
##CALLINGSEQUENCE
##- ComposeTransformation('Phi1',' Phi2',' Phi3', ...)
##PARAMETERS
##- Phi1, Phi2, Phi3 : transformations
##DESCRIPTION
##- 'ComposeTransformation(Phi1, Phi2, Phi3, ...)' returns the composition of the transformations 'Phi1, Phi2, Phi3, ...', that is, 
## the transformation 'Psi = Phi1 o Phi2 o Phi3 ...'.  The domain frame of 'Phi1' must coincide with the range frame of 'Phi2', the domain frame of 'Phi2' must coincide 
## with the range of frame of 'Phi3', and so on.
##- This command is part of the DifferentialGeometry package, and so can be used in the form ComposeTransformations(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-ComposeTransformations.
##EXAMPLES
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##- 
##- **Example 1.**
##- Define some manifolds.
##> DGsetup([x, y], M): DGsetup([u, v], N): DGsetup([t], P): DGsetup([x1, x2, x3], Q):
##- 
##- Define transformations 'F: M -> N'; ' G: P -> M'; ' H: N -> Q'.
##> F := Transformation(M, N, [u = 3*x + 2*y, v = x - y]);
##> G := Transformation(P, M, [x = cos(t), y = sin(t)]);
##> H := Transformation(N, Q, [x1 = u, x2 = v, x3 = 1]);
##- 
##- Compute the compositions 'F o G', 'H o F' and 'H o F o G'.
##> ComposeTransformations(F, G);
##> ComposeTransformations(H, F);
##> ComposeTransformations(H, F, G);
##- 
##- **Example 2.**
##- We can express the transformation 'T: P -> P' as the composition of 3 transformations 'A', 'B', 'C'.
##> T := Transformation(P, P, [t = sqrt(sin(t) + 2)]);
##> A := Transformation(P, P, [t = sin(t)]);
##> B := Transformation(P, P, [t = t + 2]);
##> C := Transformation(P, P, [t = sqrt(t)]);
##> S := ComposeTransformations(C, B, A);
##> Tools:-DGequal(T, S);
##- 
##- **Example 3.**
##- We can check that the transformation 'K' is the inverse of the transformation 'F'.
##> K := Transformation(N, M, [x = 2/5*v + 1/5*u, y = 1/5*u - 3/5*v]);
##> ComposeTransformations(F, K);
##> ComposeTransformations(K, F);
##- 
##- **Example 4.**
##- If 'pi: E -> M' is a fiber bundle, then a section 's' of 'E' is a transformation 's: M -> E 'such that 'pi o s = identity on M'.
##- Check that the map 's' is a section for 'E'.
##> DGsetup([u, v, w], E): DGsetup([x, y], M):
##> pi := Transformation(E, M, [x = u*v + w^2, y = u^2 + w^2]);
##> s := Transformation(M, E, [u = sqrt(y), v = x/sqrt(y), w = 0]);
##> ComposeTransformations(pi, s);
##SEEALSO
##- "DifferentialGeometry", "Tools", "ApplyTransformation", "DGequal", "InverseTransformation", "Transformation"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "ApplyTransformation" : Help:DifferentialGeometry/ApplyTransformation
##- "InverseTransformation" : Help:DifferentialGeometry/InverseTransformation
##- "DGequal" : Help:DifferentialGeometry/Tools/DGequal
##- "Transformation" : Help:DifferentialGeometry/Transformation
