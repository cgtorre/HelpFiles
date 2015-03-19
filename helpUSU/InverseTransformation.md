##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/InverseTransformation
##TITLE DifferentialGeometry[InverseTransformation]
##HALFLINE find the inverse of a transformation
##CALLINGSEQUENCE
##-      InverseTransformation('Phi',' options')
##PARAMETERS
##- Phi :  a transformation mapping one manifold 'M' to another manifold 'N'
##- options : 'branch = \"all\"' or 'branch = [pt1, pt2]', where 'pt2' is a list of coordinates (Maple expressions) defining a point in 'M' and 'Phi(pt2) = pt1'
##DESCRIPTION
##- The 'InverseTransformation' command uses the Maple "solve" command to find a (local) inverse transformation 'Psi: N -> M', that is, 'Psi o Phi = identity' 
## on 'M' and 'Phi o Psi = identity' on 'N'.
##- Use the Maple environment variable '\_EnvExplicit = true' to obtain explicit formulas for the inverse.
##- In the case where there are multiple local inverses, the first one in the list returned by 'solve' is returned by 'InverseTransformation'.  
This may vary from one Maple session to another.
##- With 'branch = \"all\"', 'InverseTransformation' returns a list of all the inverse transformations.
##- With 'branch = [pt1, pt2]', 'InverseTransformation' returns the particular inverse transformation 'Psi' satisfying 'Psi(pt1) = pt2'.
##- This command is part of the DifferentialGeometry package, and so can be used in the form InverseTransformation(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-InverseTransformation.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): 
##-(nolead)
##-(nolead) Define a pair of 2-dimensional manifolds.
##> DGsetup([x, y], M): DGsetup([u, v], N):
##-(nolead) 
##-(nolead) **Example 1.**
##- Define a simple transformation 'Phi1: M -> N' with a unique global inverse.
##> Phi1 := Transformation(M, N, [u = 2*x - 3*y, v= - x + 2*y]);
##> Psi1 := InverseTransformation(Phi1); 
##-(nolead) Use "ComposeTransformations" to checks the result of 'InverseTransformation'.
##> ComposeTransformations(Psi1, Phi1);
##> ComposeTransformations(Phi1, Psi1);
##-(nolead) 
##-(nolead) **Example 2.**
##- Define a transformation  'Phi2: M -> N'  with multiple local inverses.
##> Phi2 := Transformation(M, N, [u = x^2, v = y^2]);
##> Psi2 := InverseTransformation(Phi2);
##-(nolead) To get explicit solutions:
##> _EnvExplicit := true;
##> Psi2 := InverseTransformation(Phi2);
##-(nolead) To get all possible inverses:
##> AllInverses := InverseTransformation(Phi2, branch = "all"); 
##- Since 'Phi2([- 1, - 1]) = [1, 1]', we can ask for that particular inverse which maps '[1, 1]' to '[- 1, - 1]'.  
## We can use either '[1, 1]' or '[u = 1, v = 1]' as arguments in the command 'InverseTransformation' to indicate the coordinates of the point.
##> InverseTransformation(Phi2, branch = [[1, 1], [- 1, - 1]]);
##> InverseTransformation(Phi2, branch = [[u = 1, v = 1], [x = - 1,y = - 1]]);
##SEEALSO
##- "DifferentialGeometry", "ComposeTransformations", "Transformation"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "ComposeTransformations" : Help:DifferentialGeometry/ComposeTransformations
##- "Solve" : Help:solve
##- "Transformation" : Help:DifferentialGeometry/Transformation
