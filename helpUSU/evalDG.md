##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/evalDG
##TITLE DifferentialGeometry[evalDG]
##HALFLINE evaluate a DifferentialGeometry expression
##CALLINGSEQUENCE
##-      evalDG('T')
##PARAMETERS
## T : a linear combination of vectors, differential forms or tensors defining using '+', '-', '\*' for scalar multiplication, '&w' for wedge product, '&t' for tensor product, and '&s' for the symmetric tensor product
##DESCRIPTION
##- The command 'evalDG' provides a simple and efficient way for creating vector files, differential forms and tensors for subsequent calculations with the 'DifferentialGeometry' package.
##- Note that Maple may perform simplifications before passing the arguments to 'evalDG,' and these simplifications may result in an incorrect parsing of the input to 'evalDG'.  In particular, if, 
## for example, 'X' is a vector field, then 'evalDG(0\*X)' will return the scalar 0 and not the zero vector.  To define a zero object, use '0 &mult evalDG(X)' or the 'Tools' command "DGzero".
##- This command is part of the DifferentialGeometry package, and so can be used in the form evalDG(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-evalDG.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead) 
##-(nolead)  Define a 4 dimensional manifold 'M' with coordinates '[x, y, z, t]'.
##> DGsetup([x, y, z, w], M):
##-(nolead) 
##-(nolead) **Example 1.**
##-(nolead)  Create some vectors.
##> evalDG(2*D_x - y*D_z + x^2*D_w);
##> evalDG(1/2*D_x - 1/y*D_z + 1/x^2*D_w);
##-(nolead) 
##-(nolead) **Example 2.** 
##-(nolead)  Create a differential form.
##> evalDG(dx &w dy + (x^2+y^2)*dz &w dw);
##-(nolead) 
##-(nolead) **Example 3.**
##-(nolead)  Create some tensors.
##> evalDG(dx &t dy + (x^2+y^2)*dz &t dw);
##> evalDG(dx &s dy + dz &t dw);
##-(nolead) 
##-(nolead) **Example 4.**
##-(nolead)  Note the difference between the following two calls to 'evalDG'.
##> evalDG(0*D_x);
##> eval(evalDG(a*D_x), a=0);
##> Tools:-DGzero("vector");
##SECTION See Also 
##- "DifferentialGeometry", "Tools", "&plus", "DGzero", "DGzip"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "&plus" : Help:DifferentialGeometry/AlgebraicOperations
##- "DGzero" : Help:DifferentialGeometry/Tools/DGzero
##- "DGzip" : Help:DifferentialGeometry/DGzip
