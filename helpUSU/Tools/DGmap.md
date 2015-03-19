##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Tools/DGmap
##TITLE DifferentialGeometry:-Tools[DGmap]
##CALLINGSEQUENCE
##- DGmap('n',' f',' X',' arg1',' arg2',' '...,' argN')
##PARAMETERS
##- n : a positive integer
##- f : a Maple procedure
##- X : any 'DifferentialGeometry' object
##- argN : (optional) arguments for the procedure 'f'
##DESCRIPTION
##- The command 'DGmap' is similar to the command "map".  'DGmap' will apply the procedure 'f' to the coefficients of the object 'X'.  
## The integer 'n' indicates the position of the coefficients of 'X' in the argument list of  'f'.  
## Thus 'DGmap(1, f, X, arg1, arg2, ..., argN)' will replace the coefficient 'C' of 'X' with  'f(C, arg1, arg2, ..., argN)'; 
## 'DGmap(2, f, X, arg1, arg2, ..., argN)' will replace the coefficient 'C' of 'X 'with 'f(arg1, C, arg2, ..., argN)'; and so on.
##- This command is part of the DifferentialGeometry:-Tools package, and so can be used in the form DGmap(...) only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.  It can always be used in the long form DifferentialGeometry:-Tools:-DGmap.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) Define a manifold 'M' with local coordinates '[x, y]'.
##> DGsetup([x, y], M);
##-(nolead)
##-(nolead) **Example 1.** 
##-(nolead) Define a vector field 'X' depending on parameters 'C1' and 'C2'. Differentiate the coefficients of 'X' with respect to 'C1' and 'C2'.
##> X := evalDG((C1*x + C2)*D_x + C1*y*D_y);
##> DGmap(1, diff, X, C1);
##> DGmap(1, diff, X, C2);
##-(nolead)
##-(nolead) **Example 2.** 
##-(nolead) Define a differential 1-form 'omega' depending on a parameter 't'.  Integrate the coefficients of 'omega' with respect to 't' from 't = 0 .. 1'
##> omega := evalDG(t^2*x^2*dx - t^3*x*y^2*dy);
##> DGmap(1, int, omega, t = 0..1);
##-(nolead)
##-(nolead) **Example 3.** 
##-(nolead) Evaluate the tensor 'T' at 'x = 0' by taking the limit of the coefficients as 'x -> 0'.
##> T := evalDG((exp(x) - 1)/x*dx &t dx + sin(2*x)/x*dy &t dy);
##> DGmap(1, limit, T, x = 0);
##-(nolead)
##-(nolead) **Example 4.** 
##-(nolead) Substitute 's = 1' into the transformation 'Phi':
##> Phi := Transformation(M, M, [x = s*x + (s-1)*y, y = s*y]);
##> DGmap(2, subs, Phi, {s = 1});
##SEEALSO
##- "DifferentialGeometry", "Tools", "Transformation"
##XREFMAP
##- "map" : Help:map
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "Transformation" : Help:DifferentialGeometry/Transformation
