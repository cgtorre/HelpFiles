##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Pullback
##TITLE DifferentialGeometry[Pullback]
##HALFLINE pullback a differential p-form by the Jacobian of a transformation
##CALLINGSEQUENCE
##-      Pullback('Phi',' omega')
##PARAMETERS
##-  Phi : a transformation from a manifold 'M 'to a manifold 'N'
##-  omega : a differential 'r'-form on the manifold 'N', where 'r 'is not greater than the dimension of 'M'
##DESCRIPTION
##- The pullback of 'omega' with respect to a transformation 'Phi: M -> N'is an 'r'-form 'theta' on the manifold 'M 'and is denoted by 'theta = Phi^\*(omega)'.  
## If 'p 'is a point of 'M' and 'X\_1', 'X\_2', '...', 'X\_r' are vectors in 'T\_pM', then:
##-(nolead, alignment = "centred") 'theta(p)(X\_1, X\_2, ..., X\_r) = omega(Phi\_\*(X\_1), Phi\_\*(X\_2), ..., Phi\_\*(X\_r))'  (\*)
##-(nolead) The pullback of a '0'-form, that is, a real-valued function 'g' on 'N', is the real-valued function 'f = g o Phi 'on 'M'.
##- In components, let 'J' be the Jacobian matrix of 'Phi' computed with respect to a system of coordinates 'x^i 'on 'M' and 'y^j 'on 'N' and evaluated at 'p'.  
## Let 'a' be the row vector whose entries are the components of a 1-form 'omega' at 'q = Phi(p)', computed with respect to the coordinate basis on 'N'. 
## Then the matrix vector product 'b = a.J 'gives the components of 'theta = Phi^\*(omega)' with respect to the coordinate basis on 'M'.
##- From the definition (\*), it follows that 'Phi^\* 'is a homomorphism from the ring of all differential forms on 'N' to the ring of differential forms on 'M', that is, 
## 'Phi^\*(omega1 + omega2) = Phi^\*(omega1) + Phi^\*(omega2)' and 'Phi^\*(omega1 &w omega2) = Phi^\*(omega1) &w Phi^\*(omega2)' (\*\*)
## for all forms 'omega1' and 'omega2' on 'N'.  'Pullback' uses property (\*), applied to '1'-forms, together with (\*\*) to calculate the pullback of an 'r'-form.
##- The 'Pullback' command can be applied to a list of differential forms.
##- This command is part of the DifferentialGeometry package, and so can be used in the form Pullback(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-Pullback.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead) 
##-(nolead) **Example 1.**
##-(nolead) Calculate the pullback of the differential form 'omega1' with respect to the transformation 'Phi1' at the point 'p1 = [x = 1, y = 2]'.
## Check this result using the Jacobian of 'Phi1'.
##> DGsetup([x, y], M): DGsetup([u, v, w], N):
##> p1 := [x = 1, y = 2];
##> Phi1 := Transformation(M, N, [u = x + 2*y, v = 3*x + 4*y, w = 5*x + 6*y]);
##> omega1 := v*du + w*dv + u*dw;
##> theta1 := Pullback(Phi1, omega1);
##> theta1_at_p1 := eval(theta1, p1);
##-(nolead) We check this last result against a direct computation using the Jacobian of 'Phi1'.
## First calculate the coordinates of 'q1 = Phi1(p1)' and evaluate 'omega1' at this point.
##> q1 := ApplyTransformation(Phi1, p1);
##> omega1_at_q1 := eval(omega1, q1);
##> a := Vector[row]([11, 17, 5]);
##> J := Tools:-DGinfo(Phi1, "JacobianMatrix");
##> b := a.J; 
##-(nolead) The entries of 'b' coincide with the components of 'theta1\_at\_p1'.
##-(nolead) 
##-(nolead) **Example 2.**
##-(nolead) The Pullback command can be applied to a list of differential forms.
##> Pullback(Phi1, [du, dv]); 
##-(nolead) 
##-(nolead) **Example 3.**
##-(nolead) Express the function 'f' and the 2-form 'omega2' in spherical coordinates.
##> DGsetup([x, y, z] ,E3): DGsetup([rho, theta, phi], Sp):
##> f2 := x^2 + y^2 + z^2;
##> omega2 := evalDG(z*dx &w dy - y*dx &w dz + x *dy &w dz);
##> Phi2 := Transformation(Sp, E3, [x = rho*cos(theta)*sin(phi), y = rho*sin(theta)*sin(phi), z = rho*cos(phi)]);
##> simplify(Pullback(Phi2, f2));
##> simplify(Pullback(Phi2, omega2));
##SEEALSO
##- "DifferentialGeometry", "Pushforward", "PushPullTensor", "Transformation"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Pushforward" : Help:DifferentialGeometry/Pushforward
##- "PushPullTensor" : Help:DifferentialGeometry/Tensor/PushPullTensor
##- "Transformation" : Help:DifferentialGeometry/Transformation
