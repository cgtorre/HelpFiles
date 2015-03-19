##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/ExteriorDerivative
##TITLE DifferentialGeometry[ExteriorDerivative]
##HALFLINE take the exterior derivative of a differential form
##CALLINGSEQUENCE
##-      ExteriorDerivative('omega')
##PARAMETERS
##- omega : a Maple expression or a differential form
##DESCRIPTION
##- The exterior derivative of a differential 'p'-form 'omega' is a differential form 'd(omega) 'of degree 'p + 1'.  There are two standard ways to intrinsically define the exterior derivative 'd'.
##- The exterior derivative can be defined directly in terms of the Lie bracket.  For a 1-form 'alpha' and a 2-form 'beta' this definition is: 
##--(nolead, alignment = "centred") 'd(alpha)(X, Y) = X(alpha(Y)) - Y(alpha(X)) - alpha([X, Y])', 
##-(nolead, alignment = "centred") 'd(beta)(X, Y, Z) = X(beta(Y, Z)) - Y(beta(X, Z)) + Z(beta(X, Y)) - X(beta([Y, Z])) + Y(beta([X, Z ])) - Z(beta([X, Y])),'
##-(nolead alignment = "left") where 'X', 'Y', 'Z' are vector fields.  Most of the references listed on the 'DifferentialGeometry' "References" page contain 
## the general formula for the exterior derivative of a 'p'-form.
##- Alternatively, 'd' can be defined uniquely as that linear operator acting on differential forms such that: 
##-(nolead) `      `**[i]**` ` for functions 'f', 'd(f)(X) = X(f)',  where 'X'  is any vector field;
##-(nolead) `      `**[ii]**` ` 'd(alpha &w beta) = d(alpha) &w beta + (- 1)^p alpha &w d(beta)', where 'alpha' and 'beta' are differential forms and 'p' is the degree of 'alpha'; and 
##-(nolead) `      `**[iii]** 'd(d(alpha)) = 0'.
##-(nolead) The explicit coordinate formulas for the exterior derivatives of a function, a 1-form and a 2-form in 3 dimensions are given in **Example 1.**
##- The 'ExteriorDerivative' command can also be applied to a list of differential forms.
##- This command is part of the DifferentialGeometry package, and so can be used in the form ExteriorDerivative(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-ExteriorDerivative.
##EXAMPLES     ##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(LieAlgebras): 
##-(nolead)
##-(nolead)  **Example 1.**
##-(nolead)  We initialize a 3-dimensional manifold with coordinates '[x, y, z]'.
##-(nolead)  We use the 'declare' command in ' PDEtools' to display the partial derivatives of the functions 'a(x, y, z)', 'b(x, y, z)' and 'c(x, y, z)' in compact form.
##> DGsetup([x, y, z], M):
##> PDEtools[declare](a(x, y, z), b(x, y, z), c(x, y, z)); 
##-(nolead)  The exterior derivative of a function:
##> ExteriorDerivative(a(x, y, z)); 
##-(nolead)  The exterior derivative of a 1-form:
##> omega1 := evalDG(a(x, y, z)*dx + b(x, y, z)*dy + c(x, y, z)*dz);
##> ExteriorDerivative(omega1); 
##-(nolead)  The exterior derivative of a 2-form:
##> omega2 :=  evalDG(c(x, y, z)*dx &w dy - b(x, y, z)*dx &w dz + a(x, y, z)*dy &w dz);
##> ExteriorDerivative(omega2);
##-(nolead)  
##-(nolead)  **Example 2.**
##- By way of an example, we illustrate the fact that 'd^2 = 0'.
##> omega3 := evalDG(exp(y)*cos(z)*dx + ln(x)*sin(y)*dz);
##> omega4 := ExteriorDerivative(omega3);
##> ExteriorDerivative(omega4);
##-(nolead)  
##-(nolead)  **Example 3.**
##- The 'ExteriorDerivative' command can also be applied to a list of forms or a matrix of forms.
##> ExteriorDerivative([y*dx, z*dx &w dy]);
##> A := Matrix([[y &mult dx, z &mult dy], [0 &mult dx, dz]]); 
##> ExteriorDerivative(A);
##-(nolead)  
##-(nolead)  **Example 4.**
##-(nolead)  The 'ExteriorDerivative' command can also be used with adapted frames.  First we define an adapted coframe for 'M'.
##> Fr:= evalDG([x*dx + y*dy + z*dz, x*dy + y*dz, x*dz]);
##> FrData := FrameData(Fr, P);
##> DGsetup(FrData);
##> ExteriorDerivative(z);
##> ExteriorDerivative(x*Theta1 + y^2*Theta2);
##-(nolead)   
##-(nolead) **Example 5.**
##-(nolead) The 'ExteriorDerivative' command can be used with Lie algebras.
##> LD := LieAlgebraData([[x1, x3] = x1, [x1, x4] = -x2, [x2, x3] = x2, [x2, x4] = x1], [x1, x2, x3, x4], Alg1);
##> DGsetup(LD);
##> ExteriorDerivative(theta1); 
##-(nolead)   
##-(nolead)  **Example 6.** 
##-(nolead) The 'ExteriorDerivative' command can also be used with abstract differential forms.    
##> DGsetup([f = dgform(0), alpha = dgform(1), beta = dgform(2)], [d(alpha) = f*beta], M11);  
##> ExteriorDerivative(alpha); 
##> ExteriorDerivative(alpha &w beta &w beta);    
##SEEALSO
##- "DifferentialGeometry", "LieBracket", "DeRhamHomotopy", "PDEtools[declare]"
##XREFMAP
##- "References" : Help:DifferentialGeometry/References
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "LieBracket" : Help:DifferentialGeometry/LieBracket
##- "DeRhamHomotopy" : Help:DifferentialGeometry/DeRhamHomotopy
##- "PDEtools[declare]" : Help:PDEtools, declare
