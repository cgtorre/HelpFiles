##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Tools/IdentityTransformation
##TITLE DifferentialGeometry:-Tools[IdentityTransformation]
##CALLINGSEQUENCE
##-      IdentityTransformation('M')
##PARAMETERS
##- M : a Maple name or string, the name of an initialized frame
##DESCRIPTION
##- This procedure returns the transformation 'Phi : M -> M' with 'Phi(p) = p 'for all 'p' in 'M'.
##- This command is part of the DifferentialGeometry:-Tools package, and so can be used in the form IdentityTransformation(...) only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.  It can always be used in the long form DifferentialGeometry:-Tools:-IdentityTransformation.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tools):
##-(nolead)
##-(nolead) **Example 1.** 
##-(nolead) First initialize a 3-dimensional manifold 'M' with coordinates '[x, y, z]'.  Then define the identity transformation on 'M'.
##> DGsetup([x, y, z], M):
##> Phi := IdentityTransformation();
##> ApplyTransformation(Phi, [a, b, c]);
##SECTION See Also 
##- "DifferentialGeometry", "Tools", "ApplyTransformation", "Transformation", "InverseTransformation"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "ApplyTransformation" : Help:DifferentialGeometry/ApplyTransformation
##- "Transformation" : Help:DifferentialGeometry/Transformation
##- "InverseTransformation" : Help:DifferentialGeometry/InverseTransformation
