##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/LieDerivative
##TITLE DifferentialGeometry[LieDerivative]
##HALFLINE calculate the Lie derivative of a vector field, differential form, tensor, or connection with respect to a vector field 
##CALLINGSEQUENCE
##- LieDerivative('X', 'T')
##PARAMETERS
##- X : a vector field on a manifold 'M' or a vector in a Lie algebra 'A'
##- T : a vector field, a Maple expression, a differential form or a tensor field on the manifold 'M' or the Lie algebra 'A'
##DESCRIPTION
##- If 'T 'is a Maple expression, then 'LieDerivative(X, T) 'is the directional derivative 'X(T) 'of 'T 'in the direction of the vector field 'X'.
##- If 'T' is a vector field, then 'LieDerivative(X, T) 'coincides with the Lie bracket '[X, T] = LieBracket(X, T)'.
##- If 'T 'is a differential 1-form, then 'alpha = LieDerivative(X, T) 'is the 1-form defined by 'alpha(Y) = X(alpha(Y)) - alpha([X,Y])', where 'Y' is any vector field on 'M'.
##- The Lie derivative operator acts as a derivation with respect to both the wedge and tensor products.  If 'alpha' and 'beta 'are differential forms and 'T' and 'S' are tensors, then 'LieDerivative(X, alpha &w beta) = LieDerivative(X, alpha) &w beta + alpha &w LieDerivative(X, beta), 'and 'LieDerivative(X, S &t T) = LieDerivative(X, S) &t T + S &w LieDerivative(X, T).'
##- The Lie derivative of a differential form can also be calculated from the Cartan formula, 'LieDerivative(X, alpha) = ExteriorDerivative(Hook(X, alpha)) + Hook(X, ExteriorDerivative(alpha))'
##- The Lie derivative of a connection 'nabla\_Y(Z) 'is the type '(1, 2)' tensor field 'S = LieDerivative(X, nabla)', defined (when viewed as mapping from pairs of vector fields to vector fields) by 'S(Y, Z) = LieDerivative(X, nabla\_Y(Z)) - nabla\_{LieDerivative(X, Y)}(Z) - nabla\_X(LieDerivative(Y, Z)).'
##- For the definition of the Lie derivative of these geometric objects in terms of the flow of the vector field 'X' see, for example, Spivak page 207-208.
##- The Lie derivative of a tensor defined on a Lie algebra can also be computed. 
##- The first argument also be a list of vectors. The second argument can be a list of a vectors, Maple  expressions, a differential forms or tensors. 
##- This command is part of the DifferentialGeometry package, and so can be used in the form LieDerivative(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-LieDerivative.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(LieAlgebras):
##-(noload)
##-(noload) First initialize a manifold 'M' with local coordinates '[x, y, z]'.
##> DGsetup([x, y, z], M):
##-(noload) 
##-(noload) **Example 1.**
##-(noload) First we calculate the Lie derivative of a function 'f' and note that it agrees with the directional derivative 'f'.
##> X := evalDG(a *D_x + b*D_y + c*D_z);
##> LieDerivative(X, f(x, y, z));
##-(noload) 
##-(noload) **Example 2.**
##-(noload) First we calculate the Lie derivative of a vector field and check that it coincides with the Lie bracket.
##> X := evalDG(x*D_y - y^2*z*D_z);
##> Y := evalDG(y*D_x + z^2*D_y);
##> LieDerivative(X, Y);
##> LieBracket(X, Y);
##-(noload) 
##-(noload) **Example 3.**
##-(noload) First we calculate the Lie derivative of a differential form and check the result against Cartan\'s formula.
##> X := evalDG(z^2*D_x - y*D_z);
##> omega := evalDG(y*dx &w dz);
##> LieDerivative(X, omega);
##> Hook(X, ExteriorDerivative(omega)) &plus ExteriorDerivative(Hook(X, omega));
##-(noload) 
##-(noload) **Example 4.**
##-(noload) We calculate the Lie derivative of a tensor field.
##> X := evalDG(z^2*D_x - y*D_z);
##> T := evalDG(z*D_x &t dy &t dz);
##> LieDerivative(X,T);
##-(noload) 
##-(noload) **Example 5.**
##-(noload) We calculate the Lie derivative of the zero connection.
##> X := evalDG(z^2*D_x - y^2*D_z);
##> T := Tensor:-Connection(0 &mult (D_x &tensor dx &tensor dx));
##> LieDerivative(X, T);
##-(noload) 
##-(noload) **Example 6.** 
##-(noload) The Lie derivative with respect to a list of vectors can be calculated simultaneously.
##> LieDerivative( [D_x, D_y, D_z],  x*y*z*Dz);
##-(noload) The Lie derivative of a list of tensors can be calculated simultaneously.
##> LieDerivative(D_x,  [D_x &t D_x, x*D_x &t Dy, x^2*D_x &t Dz]);
##-(noload) Both arguments to 'LieDerivative' can be lists.
##> LieDerivative( [D_x, D_y],  [D_x, x*D_x, y*D_x, x*y*Dz]);
##-(noload) The Lie derivative of a Matrix of differential 2-forms can be calculated simultaneously.
##> T := map(evalDG,Matrix([[y^2*dx &w dy, x^2*dy &w dz], [x*y*dx &w dz,  z^2*dx &w dy]])); 
##> LieDerivative(x*D_x +y*D_y +z*D_z, T);   
##-(noload)
##-(noload) **Example 7.** 
##-(noload) The Lie derivative can be calculated in anholonomic frames. Use "FrameData" to find the structure equations for an anholonomic frame and initialize with "DGsetup".
##> FD := FrameData([y*dx,  dx + z*dy, dz], P);
##> DGsetup(FD, [U], [sigma]);
##> LieDerivative(U1, sigma1 &w sigma3);
##> LieDerivative(x*U1, U1 &t sigma3);
##-(noload) 
##-(noload) **Example 8.** 
##-(noload) The Lie derivative can be calculated for abstract forms. 
##> DGsetup([[omega1, omega2, omega3], beta1 = dgform(2)], [d(omega1) = omega2 &w omega3, d(omega2) = beta1], N);  
##> LieDerivative(D_omega2, omega1); 
##> LieDerivative(D_omega2, beta1);   
##-(noload) 
##-(noload) **Example 9.** 
##-(noload) The Lie derivative can be calculated for tensors on a Lie algebra. Use "LieAlgebraData" and "DGsetup" to initialize a Lie algebra.  
##> LD := LieAlgebraData([[x1, x2] = x3, [x3, x1] = 2*x1, [x3, x2] = -2*x2], [x1, x2, x3], alg);
##> DGsetup(LD);
##> MultiplicationTable("LieTable");
##-(noload) Calculate the "Killing form" for the Lie algebra and show that its Lie derivative is zero for all vectors in the Lie algebra.
##> K := KillingForm();
##> LieDerivative([e1, e2, e3], K);
##SEEALSO
##- "DifferentialGeometry", "Tensor", "Connection", "ExteriorDerivative", "Hook", "LieBracket"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "LieAlgebras" :  Help:DifferentialGeometry/LieAlgebras
##- "Tensor" : Help:DifferentialGeometry/Tensor
##- "Connection" : Help:DifferentialGeometry/Tensor/Connection
##- "DGsetup" : Help:DifferentialGeometry/DGsetup
##- "ExteriorDerivative" : Help:DifferentialGeometry/ExteriorDerivative
##- "FrameData" : Help:DifferentialGeometry/FrameData
##- "Hook" : Help:DifferentialGeometry/Hook
##- "LieAlgebraData" :  Help:DifferentialGeometry/LieAlgebras/LieAlgebraData
##- "LieBracket" : Help:DifferentialGeometry/LieBracket
##- "Killing form" : Help:DifferentialGeometry/LieAlgebras/KillingForm

