##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/LieBracket
##TITLE DifferentialGeometry[LieBracket]
##HALFLINE calculate the Lie bracket of two vector fields or 2 vectors in a Lie algebra
##CALLINGSEQUENCE
##- LieBracket('X',' Y')
##PARAMETERS
##- X, Y : vector fields, defined on the same manifold or Lie algebra
##DESCRIPTION
##- If 'X' is a vector field on a manifold 'M' and 'f 'is a real-valued function on 'M', then 'X' may be applied to 'f' to give a new real valued function.  
## In coordinates, 'X(f)' is the directional derivative of 'f' with respect to 'X'.  
## The Lie bracket of two vector fields 'X',' Y ', defined on a manifold 'M', is the vector field 'Z 'defined by the commutator rule 'Z(f) = X(Y(f)) - Y(X(f))'.  
## The standard notation for the Lie bracket is 'Z = [X, Y]'.
##- The 'LieBracket' command is also used to calculate brackets in an abstract Lie algebra.
##- This command is part of the DifferentialGeometry package, and so can be used in the form LieBracket(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-LieBracket.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(LieAlgebras):
##-(nolead) 
##-(nolead)  Define a 2-dimensional manifold 'M'..
##> DGsetup([x, y], M):
##-(nolead)
##-(nolead) **Example 1.**
##-(nolead) Define a pair of vector fields 'X1' and 'Y1'.
##> X1 := evalDG(y^2*D_x + x^2*D_y);
##> Y1:= evalDG(x*D_x);
##-(nolead)  Calculate the Lie bracket of 'X1' and 'Y1'.
##> Z := LieBracket(X1, Y1);
##- Let\'s check this result against the commutator definition of the Lie bracket acting on functions.  To apply a vector field to a function we use the 'LieDerivative' command.
##> LHSofDefinition := LieDerivative(Z, F(x, y));
##> RHSofDefinition := LieDerivative(X1, LieDerivative(Y1, F(x, y))) - LieDerivative(Y1, LieDerivative(X1, F(x, y)));
##> simplify(RHSofDefinition);
##-(nolead) 
##-(nolead) **Example 2.**  
##- Here is the general coordinate formula for the Lie bracket of two vector fields defined on a 2-dimensional manifold.
##> X2 := evalDG(a(x, y)*D_x + b(x, y)*D_y);
##> Y2 := evalDG(c(x, y)*D_x + d(x, y)*D_y);
##> LieBracket(X2, Y2);
##-(nolead) 
##-(nolead) **Example 3.**  
##-(nolead) Two vector fields are said to commute if their Lie bracket is 0.  For example:
##> X3 := evalDG(x*D_x + y*D_y);
##> Y3 := evalDG((- y*x^2/(x^2 + y^2))*D_x + (x^3/(x^2 + y^2))*D_y);
##> LieBracket(X3, Y3);
##-(nolead) 
##-(nolead) **Example 4.**  
##-(nolead) The Lie bracket satisfies the Jacobi identity '[[X, Y], Z] + [[Z, X], Y] + [[Y, Z], X] = 0'.  For example:
##> X := evalDG(sin(x)*D_x + ln(x)*y*D_y);
##> Y := evalDG(cos(y)*D_x + exp(x)*D_y);
##> Z := evalDG(x*y^3*D_x - y*x^3*D_y);
##> LieBracket(LieBracket(X, Y), Z) &plus LieBracket(LieBracket(Z, X), Y) &plus LieBracket(LieBracket(Y, Z), X);
##-(nolead) 
##-(nolead) **Example 5.**  
##-(nolead) Use "LieAlgebraData" and "DGsetup" to initialize a Lie algebra.  
##> LD := LieAlgebraData([[x1, x2] = x3, [x3, x1] = 2*x1, [x3, x2] = -2*x2], [x1, x2, x3], alg);  
##> DGsetup(LD);
##> MultiplicationTable("LieTable");
##-(nolead) Calculate the Lie bracket of 2 vectors in this Lie algebra.
##> LieBracket(e1 + e2, e2 + e3); 
##SEEALSO
##- "DifferentialGeometry", "ExteriorDerivative", "LieDerivative"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "LieAlgebras" : Help:DifferentialGeometry/LieAlgebras
##- "DGsetup" : Help:DifferentialGeometry/DGsetup
##- "ExteriorDerivative" : Help:DifferentialGeometry/ExteriorDerivative
##- "LieAlgebraData" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData
##- "LieDerivative" : Help:DifferentialGeometry/LieDerivative
