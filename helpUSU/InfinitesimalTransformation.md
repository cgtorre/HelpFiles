##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/InfinitesimalTransformation
##TITLE DifferentialGeometry[InfinitesimalTransformation]
##HALFLINE compute the Lie algebra of infinitesimal generators for an action of a Lie group on a manifold
##CALLINGSEQUENCE
##-      InfinitesimalTransformation('phi',' par',' initialpoint')
##PARAMETERS
##- phi : a transformation from a manifold 'M' to 'M', depending upon 1 or more parameters '[a, b, ...]'.
##- par : a list of the group parameters appearing in the transformation 'phi'
##- id : (optional) a list of equations 'initialpoint = [a = a0, b = b0, ... ]' specifying the values of the parameters 'a', 'b', ... which give the identity transformation on 'M'; the default value each parameter value is 0.
##DESCRIPTION
##- Let 'mu: G x M -> M 'define a (right) action of an 'r'-dimensional Lie group 'G 'on a manifold 'M'.  
##- Let 'R\_i',' i = 1 ... r 'denote a basis for the right invariant vector fields on 'G'.  
## Then the vector fields 'X\_i(x) = mu\_\*(e, x)(R\_i(e))' (where 'mu\_\*' is the Jacobian of 'mu',' e 'is the identity element of 'G', 
## and 'x' is a point of 'M') define a Lie algebra of vector fields on 'M 'whose structure constants coincide with 
## the structure constants of the Lie algebra of right invariant vector fields 'R\_i'. 
## The vector fields 'X\_i 'are called the *infinitesimal generators* for the action 'mu'.
##- For convenience, the command 'InfinitesimalTransformation' treats the action 'mu 'as a parameterized family of transformations 'phi: M -> M'.  
## The infinitesimal transformations are then computed by taking the derivatives of the components of 'phi 'with respect to the group parameters and 
## evaluating the result at the identity.  A list of vector fields is returned, one vector field for each group parameter in 'par'.
##- This command is part of the DifferentialGeometry package, and so can be used in the form InfinitesimalTransformation(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-InfinitesimalTransformation.
##EXAMPLES    
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(LieAlgebras):
##-(nolead)
##-(nolead) **Example 1.**
##-(nolead) The group of Euclidean motions in the plane, consisting of translations in the coordinate directions and rotations about the origin.
## We initialize the coordinates on the plane and define a 3-parameter transformation consisting of all the Euclidean motions.
##> DGsetup([x, y], M):
##> Phi1 := Transformation(M, M, [x = cos(theta)*x + sin(theta)*y + a, y = - sin(theta)*x + cos(theta)*y + b]);
##> Gamma1 := InfinitesimalTransformation(Phi1, [a, b, theta]); 
##-(nolead) To calculate the structure equations for this Lie algebra of vector fields, use the "LieAlgebraData" command from the "LieAlgebras" package.  
## Here '[e1, e2, e3]' denote the vectors in 'Gamma 'and only the non-trivial brackets are displayed.
##> LieAlgebraData(Gamma1);
##-(nolead) 
##-(nolead) **Example 2.**
##-(nolead) The group of fractional linear transformations on the line.
##> DGsetup([x], R):
##> Phi2 := Transformation(M, R, [x = (a*x + b)/(c*x + d)]);
##-(nolead) The identity transformation is given by 'a = 1', 'b = 0', 'c = 0', 'd = 1'.  Only the non-zero parameter values need to be specified.
##> Gamma2 := InfinitesimalTransformation(Phi2, [a, b, c, d], initialpoint = [a = 1, d = 1]); 
##-(nolead) Note that these vectors fields are not linearly independent over the real numbers ('Gamma2[1] = - Gamma2[4]').  
## This is because the parameter values '[a = t, b = 0, c = 0, d = 1]' and '[a = 1, b = 0, c = 0, d = 1/t]' 
## generate the same 1-parameter group of transformations, that is, the action is not effective.
##-(nolead) We can remove the linearly dependent elements of 'Gamma2' a with the "DGbasis" command.
##> Gamma2 := DGbasis(Gamma2, method = "real"); 
##-(nolead) Alternatively, we can make the action effective by normalizing the parameters to 'a\*b - c\*d = 1'.  
## (Now the group is 'SL2', the set of all 2 x 2 matrices with a determinant of 1.)
##> G := solve(a*d - b*c = 1, {d});
##> Phi3 := simplify(eval(Phi2, G));
##> Gamma3 := InfinitesimalTransformation(Phi3, [a, b, c], initialpoint = [a = 1]);
##-(nolead) 
##-(nolead) **Example 3.**
##-(nolead) The group of fractional linear transformations in the plane.
##> Phi4 := Transformation(M, M, [x = (a*x + b*y + c)/(r*x + s*y + t), y = (d*x + e*y + f)/(r*x + s*y + t)]);
##> Gamma4 := InfinitesimalTransformation(Phi4, [a, b, c, d, e, f, r, s, t], initialpoint = [a = 1, e = 1, t = 1]);
##-(nolead) Again we have to remove linearly dependent vectors:
##> Gamma5 := DGbasis(Gamma4, method = "real");
##> LieAlgebraData(Gamma5);
##SEEALSO
##- "DifferentialGeometry", "LieAlgebras", "DGbasis", "Flow", "GetComponents", "LieAlgebraData", "Transformation"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "LieAlgebras" : Help:DifferentialGeometry/LieAlgebras
##- "LieAlgebraData" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData
##- "DGbasis" : Help:DifferentialGeometry/DGbasis
##- "Flow" : Help:DifferentialGeometry/Flow
##- "GetComponents" : Help:DifferentialGeometry/GetComponents
##- "Transformation" : Help:DifferentialGeometry/Transformation
