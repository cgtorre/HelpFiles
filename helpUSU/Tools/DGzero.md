##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Tools/DGzero
##TITLE DifferentialGeometry:-Tools[DGscalar,  DGvolume,  DGzero]
##CALLINGSEQUENCE
##- 	 DGzero('keyword1',' options')
##-      DGvolume('keyword2',' options')
##-      DGscalar('keyword3',' options')
##PARAMETERS
##- keyword1 : a string, one of: '\"biform\"', '\"form\"', '\"vector\"', '\"tensor\"'
##- keyword2 : a string, one of: '\"biform\"', '\"form\"'
##- keyword3 : a string, one of: '\"biform\"', '\"form\"', '\"tensor\"'
##- options  : each command admits a defined frame name as an optional last argument
##DESCRIPTION
##- The command 'DGzero' creates a zero biform, form, vector or tensor.  The degree of the form or the index type of the tensor is 
## specified as a second argument.  This command is useful when, for example, a tensor 'T 'is to be computed recursively as sum of  tensors.
##- The command 'DGvolume' creates the standard top-dimensional form on a manifold 'M 'or a biform of top degree horizontal on the jet 
## space 'J^k(E)',  where 'E' is a fiber bundle over a base manifold 'M'. It is convenient to use this command 
## whenever a Lagrangian for some variational problem is to be defined as a biform of  top horizontal degree on the jet space.  
## The command 'DGvolume' accepts as a second optional argument a Maple expression 'k', where 'DGvolume(keyword2,  k) = k  &mult DGvolume(keyword2)'.
##- The command 'DGscalar' constructs a degree '0' form, a rank '0' tensor, or a biform of degree '[0, 0]'.  
##- The command 'DGscalar' accepts as a second optional argument a Maple expression 'k', where 'DGscalar(keyword3, k) = k &mult DGscalar(keyword3)'.
##- The command DGzero is part of the DifferentialGeometry:-Tools package, and so can be used in the form DGzero(...) only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.  It can always be used in the long form DifferentialGeometry:-Tools:-DGzero.  The commands DGvolume and DGscalar work the same way.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) Define some manifolds.
##> DGsetup([x, y], M): DGsetup([p, q], [u], E, 1):
##-(nolead)
##-(nolead) **Example 1.**
##-(nolead) Create the zero vector for the current frame.
##> DGinfo("CurrentFrame");
##> DGzero("vector");
##-(nolead)
##-(nolead) **Example 2.** 
##-(nolead) Create the zero vector on the manifold 'M'.
##> DGzero("vector", M);
##-(nolead) 
##-(nolead) **Example 3.**
##-(nolead) Create the zero 2-form for the current frame.
##> DGzero("form", 2);
##-(nolead)
##-(nolead) **Example 4.** 
##-(nolead) Create the zero type (1, 2) tensor on the manifold 'M'.
##> DGzero("tensor", [["con_bas", "cov_bas", "cov_bas"], []]);
##-(nolead) 
##-(nolead) **Example 5.**
##-(nolead) Create the zero type (1, 2) tensor on the manifold 'E'.
##> DGzero("tensor", [["con_bas", "cov_bas", "cov_bas"], []], E);
##-(nolead) 
##-(nolead) **Example 6.**
##- Create the zero type (2, 2) biform on the jet space of 'E'.
##> DGzero("biform", [2, 2], E);
##-(nolead) 
##-(nolead) **Example 7.**
##- Create the top degree form on 'M' with coefficient 'exp(- x^2 - y^2)'.
##> DGvolume("form", exp(- x^2 - y^2), M);
##-(nolead) 
##-(nolead) **Example 8.**
##-(nolead) Represent the  Maple expression 'ln(x)' as a degree '0' form on 'M'.
##> f := DGscalar("form", ln(x));
##> lprint(f);
##SEEALSO
##- "DifferentialGeometry", "Tools", "DGform"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "DGform" : Help:DifferentialGeometry/Tools/DGform
