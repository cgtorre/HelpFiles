##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Transformation
##TITLE DifferentialGeometry[Transformation]
##HALFLINE create a transformation or mapping from one manifold to another
##CALLINGSEQUENCE
##- Transformation('M',' N',' Eq')
##- Transformation('M',' N',' A')
##PARAMETERS
##- M : an unassigned Maple name or string, the domain for the transformation
##- N : an unassigned Maple name or string, the range for the transformation
##- Eq : a list of equations specifying each range variable as a function of the domain variables
##- A : a Matrix
##DESCRIPTION
##- The 'Transformation' command creates an internal data structure for a mapping between two frames.  
## This internal data structure contains information regarding the transformation (domain, range, prolongation order, transformation type (projectable, point, contact, differential substitution etc.), 
## and the Jacobian of the transformation).  Once a mapping between frames has been encoded using the 'Transformation' command, the mapping can then be using to transform vectors, differential forms 
## and tensors using the "Pushforward", "Pullback", and "PushPullTensor" commands in the 'DifferentialGeometry' package and in the 'Tensor' subpackage.
##- If 'M' and 'N' are the names of initialized Lie algebras, then the second calling sequence can be used to define a linear transformation from 'M' to 'N' with matrix representation 'A'.
##- This command is part of the DifferentialGeometry package, and so can be used in the form Transformation(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-Transformation.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead) 
##-(nolead)  Define 4 different manifolds:
##> DGsetup([t], R): DGsetup([x, y], M): DGsetup([u, v], N): DGsetup([r, theta], P): DGsetup([x, y, z], Q):
##-(nolead)  
##-(nolead)  **Example 1.**
##-(nolead)  Define a transformation from 'R' to 'Q', that is, the parametric representation of a space-curve.
##> T1 := Transformation(R, Q, [x = 2*t*sin(t), y = 3*t*cos(t), z = t/(t + 1)]);
##-(nolead)  
##-(nolead)  **Example 2.**
##-(nolead)  Define a transformation presenting the mapping in the complex plane 'z -> w = z^3'.
##> w := evalc((x + I*y)^3);
##-(nolead)  We use the real and imaginary parts of 'w' to define the components of the transformation.  We can set up the transformation as a map from 'M' to 'N' or as a map from 'M' to itself.
##> T2 := Transformation(M, N, [u = evalc(Re(w)), v = evalc(Im(w))]);
##> T3 := Transformation(M, M, [x = evalc(Re(w)), y = evalc(Im(w))]);
##-(nolead)  
##-(nolead)  **Example 3.**
##-(nolead)  Define a transformation encoding the change from polar to Cartesian coordinates.
##> T4 := Transformation(P, M, [x = r*cos(theta), y = r*sin(theta)]);
##-(nolead)  
##-(nolead)  **Example 4.**
##-(nolead)  Define a transformation from 'P' to 'Q' which parameterizes the hyperboloid of revolution 'z^2 = 1 + x^2 + y^2'.
##> T5 := Transformation(P, Q, [x = r*cos(theta), y = r*(theta), z = sqrt(1 + x^2)]);
##-(nolead)  
##-(nolead)  **Example 5.**
##- Define the canonical projection map '[x, y, z] -> [x, y]' from 'Q' to 'M'.
##> T6 := Transformation(Q, M, [x = x, y = y]);
##-(nolead)  
##-(nolead)  **Example 6.**
##-(nolead)  The command "DGinfo" can be used to access various attributes of a transformation.
##> T2;
##> Tools:-DGinfo(T2, "DomainFrame");
##> Tools:-DGinfo(T2, "RangeFrame");
##> Tools:-DGinfo(T2, "JacobianMatrix");
##-(nolead)  
##-(nolead)  **Example 7.**
##-(nolead)  Where an adapted frame is used, the Jacobian is computed relative to that frame. Here is a simple example:
##> ChangeFrame(M);
##> Fr := [D_x + y*D_y, D_y];
##> FrData := FrameData(Fr, M1);
##> DGsetup(FrData, verbose);
##> T7 := Transformation(M, M, [x = 2*x + y, y = - x + 3*y]);
##> J7 := Tools:-DGinfo(T7, "JacobianMatrix");
##> T8 :=  Transformation(M, M1, [x = 2*x + y, y = - x + 3*y]);
##> J8 := Tools:-DGinfo(T8, "JacobianMatrix");
##-(nolead)
##-(nolead) **Example 8.**
##-(nolead)  Here we use the second calling sequence to define a Lie algebra homomorphism between two Lie algebras. See the "LieAlgebraData" help page for information on creating Lie algebras with Maple.
##> with(LieAlgebras):
##-(nolead)  
##-(nolead)  Initialize a Lie algebra 'Alg1' which will serve as the domain for the Lie algebra homomorphism.
##> L1 := LieAlgebraData( [[x1, x4] = x1, [x2, x4] = x1 + x2, [x3, x4] = x2 + x3], [x1, x2, x3, x4], Alg1);
##> DGsetup(L1); 
##-(nolead)  Initialize a Lie algebra 'Alg2' which will serve as the range for the Lie algebra homomorphism.
##> L2 := LieAlgebraData([[x1, x2] = -x2-x3, [x1, x3] = -x3],[x1, x2, x3], Alg2);
##> DGsetup(L2, [f], [theta]); 
##- Define a matrix which will determine the linear transformation from 'Alg1' to 'Alg2'.
##> A := Matrix([[0, 0, 0, 1], [0, 0, 1, 0], [0, 1, 0, -1]]);
##> phi := Transformation(Alg1, Alg2, A);
##-(nolead)  The output indicates that 'phi' sends 'e1 'to '0f1, e2' to 'f3', 'e3' to 'f2', and 'e4' to 'f1 - f3'.  The LieAlgebras "Query" command allows us to check that 'phi' is a Lie algebra homomorphism.
##> Query(Alg1, Alg2,A, "Homomorphism");
##SEEALSO
##- "DifferentialGeometry", "Tools", "ApplyTransformation", "ComposeTransformations", "DGinfo", "InverseTransformation", "Pullback", "Pushforward", "PushPullTensor"
##XREFMAP
##- "LieAlgebraData" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData
##- "Query" : Help:DifferentialGeometry/LieAlgebras/Query
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "ApplyTransformation" : Help:DifferentialGeometry/ApplyTransformation
##- "ComposeTransformations" : Help:DifferentialGeometry/ComposeTransformations
##- "DGinfo" : Help:DifferentialGeometry/Tools/DGinfo
##- "InverseTransformation" : Help:DifferentialGeometry/InverseTransformation
##- "Pullback" : Help:DifferentialGeometry/Pullback
##- "Pushforward" : Help:DifferentialGeometry/Pushforward
##- "PushPullTensor" : Help:DifferentialGeometry/Tensor/PushPullTensor
