##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/ApplyTransformation
##TITLE(halfline="evaluate a transformation at a point") DifferentialGeometry[ApplyTransformation]
##CALLINGSEQUENCE
##- ApplyTransformation('Phi', 'pt')
##PARAMETERS
##- Phi : transformation from a manifold 'M' to another manifold 'N'
##- pt : a list of coordinates or a list of equations defining a point in the domain manifold 'M'
##DESCRIPTION
##- 'ApplyTransformation(Phi, pt)' returns the coordinates of the point 'Phi(pt)' in 'N'.
##- The second argument is of the form '[a1, a2, ...]' or '[x1 = a1, x2 = a2, ...]', where 'x1', 'x2', ... are the coordinates on 'M'.
##- This command is part of the DifferentialGeometry package, and so can be used in the form ApplyTransformation(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-ApplyTransformation.
##EXAMPLES
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead)
##- **Example 1.** 
##- Define coordinate systems 'M' and 'N'.
##> DGsetup([x, y, z], M): DGsetup([u, v], N):
##-(nolead) 
##- Define a transformation 'Phi' from 'M' to 'N'.
##> Phi :=Transformation(M, N, [u = x^2 + y^2 + z^2, v = x*y + y*z + x*z]);
##-(nolead) 
##- Apply the transformation 'Phi' to the points 'p1', 'p2'.
##> p1 := [1, 2, 3];
##> ApplyTransformation(Phi, p1);
##> p2 := [x = 5, y = 0, z = 1];
##> ApplyTransformation(Phi, p2);
##SEEALSO
##- "DifferentialGeometry", "Transformation"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Transformation" : Help:DifferentialGeometry/Transformation
