##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Flow
##TITLE DifferentialGeometry[Flow]
##HALFLINE calculate the one parameter group of differeomorphisms (flow) of a vector field
##CALLINGSEQUENCE
##-      Flow('X',' var',' options')
##PARAMETERS
##- X : a vector field
##- var :  an unassigned Maple name, the flow parameter
##- options : optional arguments to pass to the Maple command 'dsolve' for solving the ordinary differential equations for the flow
##DESCRIPTION
##- The flow of a vector field 'X' on a manifold 'M' is a one parameter group of transformations 'Phi\_t: M -> M 'such that for all 'p in' 'M',
## 'diff(Phi\_t(p), t) = X(Phi\_t(p))' and 'Phi\_0(p) = p'.
## For each fixed 't', 'Phi\_t 'is a local diffeomorphism of 'M' and 'Phi\_t o Phi\_s = Phi\_(t + s)'.
##- The flow of 'X' is calculated by solving a first order system of ordinary differential equations with the Maple "dsolve" command.  
##- If 'dsolve' fails to solve these odes, the 'Flow' command returns 'NULL'.
##- The command 'Flow' returns a transformation whose domain and range coincide with the manifold on which 'X 'is defined.
##- With the option 'ode = true', the system of odes (with initial conditions) defining the flow is returned.
##- With the option 'initialpoint = [x1 = a, x2 = b, ...]', the flow though the specific point '[a, b, ...]' is calculated.
##- With the option 'dsolvehints = [hints]', the list of optional arguments 'hints' is passed to 'dsolve'.
##- A customized ode solver can be used in place of 'dsolve' though the use of the "Preference" command.
##- This command is part of the DifferentialGeometry package, and so can be used in the form Flow(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-Flow.
##EXAMPLES     ##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##> DGsetup([x, y, z], M): 
##-(nolead)
##-(nolead) ** Example 1.**
##-(nolead) Calculate the flow 'Phi\_t' for the vector field 'X'.
##> X := evalDG(- y*D_x + x*D_y + 1/4*z*D_z);
##> Phi_t := Flow(X, t);
##SUBSECTION(collapsed = true) Flow plots
##-(nolead) Plot the flows for various initial conditions:
##> C:= map2(ApplyTransformation, Phi_t, {[1, 0, 0], [1, 0, 1/2], [0, 1, 1/2]});
##> plots[spacecurve](C, t = - Pi..Pi, axes = normal);
##ENDSUBSECTION
##-(nolead) We check that 'Phi\_s o Phi\_t' is 'Phi\_(t + s)'.
##> combine(ComposeTransformations(eval(Phi_t, t = s), Phi_t));
##> eval(Phi_t, t = t + s); 
##-(nolead) We check that the derivative of the flow with respect to 't' coincides with the vector field evaluated along the flow:
##> C1 := ApplyTransformation(Phi_t, [a, b, c]);
##-(nolead) Differentiate the components of this curve with respect to 't'.
##> Y1 := DGzip(diff(C1, t), [D_x, D_y, D_z], "plus");
##> C2 := ApplyTransformation(Phi_t, [x = a, y = b, z = c]);
##> Y2 := eval(X, C2); 
##> Y1 &minus Y2;
##-(nolead)
##-(nolead) **Example 2.**
##-(nolead) We find the flow of the vector 'X' through the point '(1, 0, 0)'.
##> Flow(X, t, initialpoint = [x = 1, y = 0, z = 0]);
##-(nolead)
##-(nolead) **Example 3.**
##- We obtain the ode defining the flow for 'X'.  The result consists of a sequence of 3 sets: the ode, the initial conditions, and the dependent variables.
##> Flow(X, t , ode = true);
##-(nolead) 
##-(nolead) **Example 4.**
##> Flow(X, t, dsolvehints = [method = laplace]);
##SEEALSO
##- "DifferentialGeometry", "ApplyTransformation", "ComposeTransformations", "InfinitesimalTransformation", "Preferences", "Transformation"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "ApplyTransformation" : Help:DifferentialGeometry/ApplyTransformation
##- "ComposeTransformation" : Help:DifferentialGeometry/ComposeTransformations
##- "InfinitesimalTransformation" : Help:DifferentialGeometry/InfinitesimalTransformation
##- "Preferences" : Help:DifferentialGeometry/Preferences
##- "Transformation" : Help:DifferentialGeometry/Transformation
