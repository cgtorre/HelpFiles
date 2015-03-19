##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Tools/DGsimplify
##TITLE DifferentialGeometry:-Tools[DGsimplify]
##CALLINGSEQUENCE
##- DGsimplify('X')
##PARAMETERS
##- X :  a vector field, differential form or tensor
##DESCRIPTION
##- This command is typically used to simplify a vector field, differential form or tensor, defined on a manifold 'M', after a substitution or evaluation of its coefficients at point on 'M'.
##- This command is part of the DifferentialGeometry:-Tools package, and so can be used in the form DGsimplify(...) only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.  It can always be used in the long form DifferentialGeometry:-Tools:-DGsimplify.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tools):
##-(nolead)
##-(nolead) **Example 1.**  
##- Define a manifold 'M' with coordinates '[x, y, z]'.
##> DGsetup([x, y, z], M):
##-(nolead)
##- Define a tensor on 'M' and evaluate it at the point '[x = 0, y = 2, z = 3]'.
##> T := evalDG(x^2*D_x &t dx + x*y*D_y &t dz + z &t D_z &t dy);
##> S := eval(T, [x = 0, y = 2, z = 3]); 
##-(nolead) The terms '0\*D\_x' and '0\*D\_y' can be eliminated with a call to 'DGsimplify'.
##> DGsimplify(S);
##SECTION See Also 
##- "DifferentialGeometry", "Tools"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
