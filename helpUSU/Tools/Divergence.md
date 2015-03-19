##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Tools/Divergence
##TITLE DifferentialGeometry:-Tools[Divergence]
##CALLINGSEQUENCE
##-      Divergence('X')
##PARAMETERS 
##-    X : a vector
##DESCRIPTION
##- The divergence of a vector, as defined by the usual formula in vector calculus, is not an intrinsic operator which can be defined in a 
## coordinate independent manner. 
## Still, for a number of purposes it is helpful to have this simple procedure.
##- The command Divergence is part of the DifferentialGeometry:-Tools package, and so can be used in the form Divergence(...) only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.  It can always be used in the long form DifferentialGeometry:-Tools:-Divergence.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tools):
##-(nolead)
##-(nolead) **Example 1.**
 ##-(nolead) First initialize a 3-dimensional manifold 'M' with coordinates '[x, y, z]'.
##> DGsetup([x, y, z], M): 
##> X := DGzip([a, b, c](x, y, z),[D_x, D_y, D_z], "plus");
##> Divergence(X);
##SEEALSO
##- "DifferentialGeometry", "Tools", "DGzip", "CovariantDerivative", "ExteriorDerivative"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "DGzip" : Help:DifferentialGeometry/DGzip
##- "CovariantDerivative" : Help:DifferentialGeometry/Tensor/CovariantDerivative
##- "ExteriorDerivative" : Help:DifferentialGeometry/ExteriorDerivative
