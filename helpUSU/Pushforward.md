##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Pushforward
##TITLE DifferentialGeometry[Pushforward]
##HALFLINE pushforward a vector or a vector field by the Jacobian of a transformation
##CALLINGSEQUENCE
##- Pushforward('Phi',' X',' pt')
##- Pushforward('Phi',' X')
##- Pushforward('Phi',' Psi',' X')
##PARAMETERS
##- Phi : a transformation from a manifold 'M 'to a manifold 'N'
##- X : a vector defined at a point 'pt 'of 'M'; or a vector field on 'M'
##- pt : a list specifying the coordinates of a point on 'M'
##- Psi : a transformation from the manifold 'N 'to a manifold 'M', typically the inverse of the map 'Phi'
##DESCRIPTION
##- In differential geometry, the Jacobian of a transformation 'Phi: M -> N 'is considered to be a linear transformation between 
## tangent spaces 'Phi\_\*: T\_pM -> T\_qN', where 'p 'is a point of 'M' and 'q = Phi(p)'.  
## Let 'X' be a tangent vector in 'T\_pM'.' ' Then 'Y = Phi\_\*(X) 'may be defined in one of two ways.  
## If 'X' is viewed as a derivation on the smooth functions defined in a neighborhood of 'p' in 'M', then 'Y = Phi\_\*(X)' is the 
## derivation on the smooth functions 'g' defined in a neighborhood 'q' of 'N' by 'Y(g) = X(Phi o g)'.  
## If 'X' is viewed as the tangent vector to a curve 'alpha(t) 'at 't = 0', then 'Y' is the tangent vector to the curve 'beta = (Phi o alpha)(t) 'at 't = 0'.
##- The vector 'Y = Phi\_\*(X)' is called the pushforward of 'X 'by 'Phi'.  The vector 'Y' is computed by 'Pushforward(Phi, X, pt)', where 'pt = [a1, a2, a3, ...]' or 
## 'pt = [x1 = a1, x2 = a2, x3 = a3, ...] 'are the coordinates of the point 'p'.
##- In components, let 'J 'be the Jacobian matrix of 'Phi 'computed with respect to a system of coordinates 'x^i 'on 'M' and 'y^j 'on 'N', and evaluated at 'p'.  
## Let 'a' be the column vector whose entries are the components of 'X 'computed with respect to the coordinate basis on 'M'. Then the matrix vector product 'b = J.a 'gives the components of 'Y = Phi\_\*(X) 'with respect to the coordinate basis on 'N'.
##- The command 'Pushforward(Phi, X) 'returns a vector on 'N' whose coefficients are functions of the coordinates on 'M'.  
## The result defines the pushforward of the vector field 'X' at an arbitrary point of 'M'.
##- If 'Phi' is an invertible transformation with inverse 'Psi', then a vector field  'Y' on 'N 'can be constructed from a vector field 'X' on 'M' 
## by setting 'Y(q) = Phi\_\*(X(p))', where 'q 'is an arbitrary point of 'N' and 'p = Psi(q)'.  The command 'Pushforward(Phi,  Psi, X)' returns the vector field 'Y'.
##- The 'Pushforward' command can be applied to a list of vectors.
##- This command is part of the DifferentialGeometry package, and so can be used in the form Pushforward(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-Pushforward.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead)
##-(nolead) **Example 1.**
##-(nolead) Compute the pushforward of the vector 'X1', defined at the point '[x = 1, y = 3]' by the transformation 'Phi'.
## Check this answer against the component calculation of the pushforward using the Jacobian matrix.
##> DGsetup([x, y], M): DGsetup([u, v], N):
##> Phi1 := Transformation(M, N, [u = ln(x^2 + y^2), v = x/y]);
##> X1 := evalDG(a*D_x + b*D_y);
##> Y1 := Pushforward(Phi1, X1, [x = 1, y = 3]);
##> J := Tools:-DGinfo(Phi1, "JacobianMatrix");
##> J1 := eval(J, [x = 1, y = 3]);
##> C := J1.Vector([a, b]);
##-(nolead) 
##-(nolead) The entries of the vector 'C' agree with the components of the vector 'Y1'.
##-(nolead)
##- **Example 2.** 
##- Show that the points 'p1 = [1, 1]' and 'p2 = [- 1, - 1]', in 'M', map under the transformation 'Phi' to the same point in 'N' but that the pushforward of the vector field 'D\_x' by 'Phi' at these two points are different.
##> Phi2 := Transformation(M, N, [u = ln(x^2 + y^2), v = x/y]); 
##> p1 := [x = 1, y = 1];
##> p2 := [x = -1, y = -1];
##> ApplyTransformation(Phi2, p1), ApplyTransformation(Phi2, p2);
##> Pushforward(Phi2, D_x, p1), Pushforward(Phi2, D_x, p2);
##-(nolead) 
##-(nolead) **Example 3.**
##-(nolead) Compute the pushforward of the vector field 'X3' by the transformation 'Phi3' at an arbitrary point.
## Here we use the second calling sequence for 'Pushforward'.
##> Phi3 := Transformation(M, N, [u = ln(x^2 + y^2), v = x/y]);
##> X3 := evalDG(x^2*D_x + x^2*D_y);
##> Pushforward(Phi3, X3);
##-(nolead) 
##-(nolead) **Example 4.**
##-(nolead) Express the vector field 'X4' in polar coordinates.
## First set up the polar coordinate system and define the transformation 'Phi4' from polar to Cartesian coordinates.  
## Calculate the inverse transformation.  Use the third calling sequence for 'Pushforward'.
##> DGsetup([r, theta], P):
##> X4 := evalDG(y/x*D_x - 2*D_y);
##> Phi4 := Transformation(P, M, [x = r*cos(theta), y = r*sin(theta)]);
##> _EnvExplicit := true:
##> invPhi4 := InverseTransformation(Phi4);
##> Pushforward(invPhi4, Phi4, X4) assuming r > 0;
##-(nolead) 
##-(nolead) **Example 5.**
##- Find the tangent vector to the curve 't -> [x = t^2, y = t^3, z = t^3]'.
##> DGsetup([t], R): DGsetup([x, y, z], E3):
##> C := Transformation(R, E3, [x = t^2, y = t^3, z = t^3]);
##> Pushforward(C, D_t);
##-(nolead) 
##-(nolead) **Example 6.**
##-(nolead) Find a basis for the tangent plane to the surface 'z = x^3 - 3\*x\*y^2' at each point '[x, y, z]'.
##> DGsetup([x, y], E2): DGsetup([x, y, z], E3):
##> S := Transformation(E2, E3, [x = x, y = y, z = x^3 - 3*x*y^2]);
##> Pushforward(S, [D_x, D_y]);
##-(nolead)
##-(nolead) **Example 7.**
##- Find the projection of the vector field 'X5' under the map 'Phi5'.
##> DGsetup([u, v], E2): DGsetup([x, y, z], E3):
##> Phi5 := Transformation(E3, N, [u = x/z, v = y/z]);
##> X5 := evalDG(1/(x^2 + y^2 + z^2)*(x^2*y*D_x + y*z^2*D_y - x*y*z*D_z));
##> Pushforward(Phi5, X5);
##-(nolead)
##-(nolead) The goal now is to rewrite the coefficients of this vector field in terms of the variables 'u' and 'v'.  The map 'Phi5' is not invertible but it does admit a right inverse 'Sigma'.
##> Sigma := Transformation(N, E3, [x = u, y = v, z = 1]);
##> ComposeTransformations(Phi5, Sigma);
##-(nolead)
##-(nolead) We use this map as the second argument in the third calling sequence for 'Pushforward'.
##> Pushforward(Phi5, Sigma, X5);
##-(nolead) 
##-(nolead) **Example 8.**
##- The 'Pushforward' command can also be applied to a list of  vectors.
##> ChangeFrame(M);
##> Pushforward(Phi1, [D_x, D_y], [x = 1, y = 3]);
##SEEALSO
##- "DifferentialGeometry", "ComposeTransformations", "DGinfo", "PullbackVector", "Pullback", "Transformation"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "ComposeTransformations" : Help:DifferentialGeometry/ComposeTransformations
##- "DGinfo" : Help:DifferentialGeometry/Tools/DGinfo
##- "PullbackVector" : Help:DifferentialGeometry/PullbackVector
##- "Pullback" : Help:DifferentialGeometry/Pullback
##- "Transformation" : Help:DifferentialGeometry/Transformation
