##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Tools/DGform
##TITLE DifferentialGeometry:-Tools[DGbifom, DGform, DGtensor, DGvector]
##CALLINGSEQUENCE
##-      DGbiform('x',' M')
##-      DGform('x',' M')
##-      DGtensor('x',' indexType',' M')
##-      DGvector('y',' M')
##PARAMETERS
##-    x : a positive integer, a list of positive integers, a coordinate variable, or a list of coordinate variables
##-    M : (optional) the name of defined frame
##-    indexType : specifying the index type of the tensor
##-    y : a positive integer or a coordinate variable
##DESCRIPTION
##- The command 'DGform' will create a single term differential form.  Let 'Theta = [theta\_1, theta\_2, theta\_3, ...]' denote the coframe for 
## the current frame or, if the optional argument 'M' is given, the frame 'M'.  
## The list 'Theta' can be obtained from the command "DGinfo" with the keyword '\"frameBaseForms\"' or '\"frameJetForms\"'.  Let 'V = [x\_1, x\_2, x\_3, ...]' 
## denote the local coordinates for the current frame or, if the optional argument 'M' is given, the frame 'M'.  
## The list 'V 'can be obtained from the command 'DGinfo' with the keyword '\"frameIndependentVariables\"' or '\"frameJetVariables\"'. 
## If the integer 'i' or coordinate 'x\_i' is given, the command returns the corresponding 1-form 'theta\_i'.  If a list of 'p' integers ['i, j, k, ...]' or 
## coordinates [x\_'i, x\_j, x\_k, ...] 'is given, the command returns the 'p'-form  'theta\_i &w theta\_j &w theta\_k...'
##- The commands 'DGbiform', 'DGtensor', and 'DGvector' work in a similar fashion.
##- The command DGform is part of the DifferentialGeometry:-Tools package and so can be used in the form DGform(...) only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.  It can always be used in the long form DifferentialGeometry:-Tools:-DGform.  DGbiform, DGtensor, and DGvector work in the same way.
##EXAMPLES     ##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tools):
##-(nolead) **Example 1. **
##-(nolead) Define a manifold 'M' with coordinates '[x, y, z, w]'.
##> DGsetup([x, y, z, w], M):
##> DGvector(x);
##> DGvector(3);
##> DGform(y);
##> DGform(4);
##> DGform([x, y]);
##> DGform([1, 2, 3, 4]);
##> DGtensor(x, "con_bas");
##> DGtensor(2, "cov_bas");
##> DGtensor([1, 1, 1], [["cov_bas", "con_bas", "cov_bas"], []]);
##-(nolead)
##-(nolead) **Example 2. **
##- Define a rank 3 vector bundle 'E' with coordinates '[x, y, u, v, w]' over a two dimensional base with coordinates '[x, y]'.
##> DGsetup([x,y,u, v, w], E);
##> DGtensor([x,v,v], [["con_bas", "cov_bas", "con_bas"], []]);
##-(nolead)
##-(nolead) **Example 2. **
##-(nolead) Define the jet space 'J^2(R^2, R^2)' for two functions 'u' and 'v' of 2 independent variables 'x' and 'y'.
##> DGsetup([x,y], [u,v], J, 2):
##> omega := DGbiform(u[1, 1]);
##> convert(omega, DGform);
##SEEALSO
##- "DifferentialGeometry", "Tools", "evalDG", "DGinfo", "DGzip"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "evalDG" : Help:DifferentialGeometry/evalDG
##- "DGinfo" : Help:DifferentialGeometry/Tools/DGinfo
##- "DGzip" : Help:DifferentialGeometry/DGzip

