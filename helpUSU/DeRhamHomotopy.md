##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/DeRhamHomotopy
##TITLE DifferentialGeometry[DeRhamHomotopy]
##HALFLINE apply the homotopy operator for the de Rham complex on R^n to a differential form
##CALLINGSEQUENCE
##-      DeRhamHomotopy('omega',' options')
##PARAMETERS
##- omega : a differential form
##- options : equations of the form 'integrationlimits = list',' initialpoint = list', 'path=\"straightline\"',' path=\"zigzag\"', 'variableorder = list', 'cylinderconstruction = var'
##DESCRIPTION
##- Let 'Omega^p(R^n)' denote the space of differential p-forms defined on the Euclidean space 'R^n'.  A homotopy operator for the de Rham complex on 'R^n' 
## is a map 'H: Omega^p(R^n) -> Omega^(p-1)(R^n)' such that 'omega = H(d(omega)) + d(H(omega) )' for any  'omega in Omega^p(R^n)'.
##- Most differential geometry texts give a standard formula for a homotopy operator which involves an integration of the coefficients of the differential from 'omega' along the 
## straight line '[tx, ty, tz, ...]' from the origin ('t = 0)' to the general point ['x, y, z, ...]'.  
## The optional arguments to "DeRhamHomotopy' allows the user to modify the standard homotopy operator by changing the path of integration.
##- The option 'initialpoint = [x = a, y = b, z = c, ...]' changes the path of integration to the straight line starting at the point with coordinates '[a, b, c, ...]'. 
## This option is useful when the differential form 'omega' is singular at the origin.
##- The option 'integrationlimits = [infinity, 1]' integrates the coefficients of the differential form from a point at infinity to the general point ['x, y, z, ...]'. 
## This option may be used for differential forms which vanish at infinity.  More precisely, if 'A(x^1, x^2, x^3, ...)' is any coefficient of the differential form 'omega', 
## then the function 'a(t) = t\*A(tx^1, tx^2, tx^3, ...)' must have a finite integral over the interval 't = 1 .. infinity'.
##- In many situations, the 'DeRhamHomotopy' command will return a simpler answer by using the 'path=\"zigzag\"' option.  
## In this case the \'radial\' integration from the origin to the point ['x, y, z, ...]' is replaced by a sequence of straight line integrations along the coordinate lines, 
## first from ['0, 0, 0, ...]' to '[x, 0, 0, ...]', then from '[x, 0, 0, ...]' to' '[x, y, 0, ...] 'and so on.  
## The option 'variableorder = list 'specifies the order in which the integrations along the different coordinate lines are performed.
##- The option 'cylinderconstruction = var' implements the more general homotopy operator described in the books by "Boothby", page 277 and "Flanders", page 27.  
## We consider a manifold 'M' and set 'N = I x M', where 'I' is an interval with coordinate (say) 't'.  Let 'omega 'be a  'p'-form on 'N'. 
## Then 'eta = DeRhamHomotopy(omega, cylinderconstruction = t)' returns a '(p-1)'-form on 'M'.  
## If 'omega = A(t, x) dx &w dy ... (no dt differentials)' then 'eta = 0'.  
## If 'omega = A(t, x) dt &w dx &w dy ...', then 'eta = int(A(t, x) t = 0..1) dx &w dy.'  
## With the 'cylinderconstruction 'option it is a simple matter for the Maple user to create customized homotopy operators for the de Rham complex.
##- This command is part of the DifferentialGeometry package, and so can be used in the form DeRhamHomotopy(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-DeRhamHomotopy.
##EXAMPLES     ##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##- 
##-(nolead) **Example 1.**
##- First define a manifold 'M' with coordinates '[x, y, z, w]'.
##> DGsetup([x, y, z, w], M);
##-(nolead) 
##-(nolead)  Define a differential 3-form 'omega1' and check that it is closed, that is, that the exterior derivative of 'omega1' is 0.
##> omega1 := evalDG(y*dx &w dz &w dw + x*dy &w dz &w dw);
##> ExteriorDerivative(omega1);
##-(nolead)  To write omega1 as the exterior derivative of a 1-form, we apply the 'DeRhamHomotopy' to 'omega1'.
##> eta1 := DeRhamHomotopy(omega1); 
##-(nolead)  Check this result.
##> ExteriorDerivative(eta1) &minus omega1;
##-(nolead)  
##-(nolead) ** Example 2.**
##- Here are a few simple examples which illustrate the use of the options to control the values returned by the 'DeRhamHomotopy' command.
##> omega2 := evalDG(x *dx &w dy);
##> eta2a := DeRhamHomotopy(omega2); 
##-(nolead)  Change the starting point for the straight line defining the integration path.
##> eta2b := DeRhamHomotopy(omega2, initialpoint = [x=1, y=2]); 
##-(nolead)  Use a sequence of coordinate lines starting from the origin.  Integrate along the x-axis, y-axis, z-axis, and w-axis.
##> eta2c := DeRhamHomotopy(omega2, path = "zigzag"); 
##-(nolead)  Use a sequence of coordinate lines starting from the origin.  Integrate along the y-axis, x-axis, w-axis, and z-axis.
##> eta2d := DeRhamHomotopy(omega2, path = "zigzag", variableorder = [y, x, w, z]); 
##-(nolead)  Use a sequence of coordinate lines starting from the point '[x=1, y=2, z=0, w=0]'.  Integrate along the y-axis, x-axis, z-axis, and w-axis.
##> eta2e := DeRhamHomotopy(omega2, path = "zigzag", variableorder = [y, x, z, w], initialpoint = [x = 1, y = 2]);
##-(nolead)  The exterior derivative of each the forms 'eta2a ... eta2e' returns the correct result, namely 'omega2'.
##> ExteriorDerivative([eta2a, eta2b, eta2c, eta2d, eta2e]);
##-(nolead)  
##-(nolead) ** Example 3.**
##- Here are a few examples which illustrate the use of 'DeRhamHomotopy' operator for forms with singularities.
##> omega3 := evalDG(1/x^3*dx &w dy);
##> eta3 := DeRhamHomotopy(omega3, integrationlimits = [1, infinity]);
##> omega4 := evalDG(1/x*dx &w dy);
##> eta4a := DeRhamHomotopy(omega4, path = "zigzag");
##> eta4b := DeRhamHomotopy(omega4, path = "zigzag", initialpoint = [x=1], variableorder = [y, x, w, z]);
##-(nolead)  
##-(nolead) **Example 4.**
##- Here is a simple example of the cylinder construction.
##> DGsetup([x, y, t], P);
##> omega := evalDG(f(x, y, t)*dx &w dt + g(x, y, t)*dx &w dy);
##> DeRhamHomotopy(omega, cylinderconstruction = t);
##SEEALSO
##- "DifferentialGeometry", "ExteriorDerivative"
##XREFMAP
##- "Boothby" : Help:DifferentialGeometry/References
##- "Flanders" : Help:DifferentialGeometry/References
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "ExteriorDerivative" : Help:DifferentialGeometry/ExteriorDerivative
