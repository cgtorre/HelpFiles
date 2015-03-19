##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Tools/GenerateForms
##TITLE DifferentialGeometry:-Tools[GenerateForms]
##CALLINGSEQUENCE
##-      GenerateForms('Omega',' deg')
##PARAMETERS
##- Omega  : a list of lists of differential 1-forms
##- deg    : a list of positive integers
##DESCRIPTION
##- Let 'Omega = [Omega\_1, Omega\_2, Omega\_3, ...]' and let 'deg = [p\_1, p\_2, p\_3, ...]'.  Then 'GenerateForm(Omega, deg)' returns a list of differential forms of 
## degree 'p = p\_1 + p\_2 + p\_3 + ...', where each form 'omega' in the list is of the form 'omega = omega\_1 &w omega\_2 &w omega\_3 .... ' and 
## where 'omega\_i ' is a 'p\_i'-fold wedge product of forms in 'Omega\_i'.
##- The command GenerateForms is part of the DifferentialGeometry:-Tools package, and so can be used in the form GenerateForms(...) only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.  It can always be used in the long form DifferentialGeometry:-Tools:-GenerateForms.
##EXAMPLES     ##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tools):
##- 
##- Define a 6-dimensional manifold 'M' with coordinates '[x1, x2, y1, y2, y3, z1]'.  
## (This choice of coordinate names is simply to help understand the output of the commands that follow).
##> DGsetup([x1, x2, y1, y2, y3, z1], M);
##-(nolead)
##-(nolead) **Example 1.**
##-(nolead) Find all 2 -forms generated from '[dy1, dy2, dy3]'.
##> GenerateForms([[dy1, dy2, dy3]], [2]);
##-(nolead) 
##-(nolead) **Example 2.**
##-(nolead) Find all 2-forms obtained by choosing 1 from '[dx1, dx2]' and 1 from '[dy1, dy2, dy3]'.
##> GenerateForms([[dx1, dx2], [dy1, dy2, dy3]], [1, 1]);
##-(nolead)
##-(nolead) **Example 3.**
##-(nolead) Find all 5-forms obtained by choosing 2 from '[dx1, dx2]' and 3 from '[dy1, dy2, dy3]'.
##> GenerateForms([[dx1, dx2] , [dy1, dy2, dy3]], [2, 3]);
##-(nolead) **Example 4.** 
##-(nolead) Find all 3-forms obtained by choosing 1 from '[dx1, dx2]', 1 from '[dy1, dy2]', and 1 from '[dz1]'.
##> GenerateForms([[dx1, dx2], [dy1, dy2], [dz1]], [1, 1, 1]);
##SEEALSO
##- "DifferentialGeometry", "Tools", "JetCalculus", "GenerateSymmetricTensors"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "JetCalculus" : Help:DifferentialGeometry/JetCalculus
##- "GenerateSymmetricTensors" : Help:DifferentialGeometry/Tensor/GenerateSymmetricTensors
