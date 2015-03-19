##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/PullbackVector
##TITLE DifferentialGeometry[PullbackVector]
##HALFLINE find (if possible) a vector field whose pushforward by the Jacobian of a given transformation is a given vector field
##CALLINGSEQUENCE
##-      PullbackVector('Phi', 'Y', 'S', 'freevar')
##PARAMETERS
##- Phi : a transformation from a manifold 'M 'to a manifold 'N'
##- Y : a vector field on 'N'
##- S : (optional) a list of independent vector fields on 'M'; the default is the standard local frame for the tangent bundle of 'M'
##- freevar : (optional) ' freevariable = k', where 'k' is an unassigned Maple name
##DESCRIPTION
##- This procedures finds all vector fields 'X' in the span of 'S 'such that 'Phi\_\*(X) = Y', where 'Phi\_\* 'is the Jacobian of 'Phi'.
## If 'Phi 'is a local immersion, then 'Phi\_\* 'is injective and the vector 'X', if it exists, is unique.  
## If ' Phi 'is not a local immersion, then the optional argument 'freevariable = k' can be used to specify the name of the indexed variable that will be used to parameterize the possiblities for 'X'.
##- The kernel of ' Phi\_\*' can be computed by taking 'Y' to be the zero vector.
##- If no vector field 'X' exists such that 'Phi\_\*(X) = Y', then 'NULL' is returned.
##- This command is part of the DifferentialGeometry package, and so can be used in the form PullbackVector(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-PullbackVector.
##EXAMPLES    
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead) 
##-(nolead) **Example 1.**
##- Suppose 'Phi: M -> N' is an imbedding and 'Y' is a vector field on 'N' which is tangent to the image of 'M'.  
## Then there exists a unique vector field 'X' on 'M' such that 'Phi\_\*(X) = Y'; and 'X' can be found using the 'PullbackVector' command.
## For example, the vectors 'Y1' and 'Y2'  defined below are both tangent to the unit 3-sphere 'x^2 + y^2 + z^2 + w^2 = 1' and therefore can be pulled-back by 
## the stereographic projection map 'Phi1' to the 3-dimensional Euclidean space 'E3' with coordinates '[r, s, t]'.
##> DGsetup([x, y, z, w], E4): DGsetup([r, s, t], E3):
##> Phi1 := Transformation(E3, E4, [x = 2*r/(1 + r^2 + s^2 + t^2), y = 2*s/(1 + r^2 + s^2 + t^2), z = 2*t/(1 + r^2 + s^2 + t^2), w = (1 - (r^2 + s^2 + t^2))/(1 + r^2 + s^2 + t^2)]);
##> Y1 := evalDG(- y*D_x + x*D_y + w*D_z - z*D_w);
##> Y2 := evalDG(- z*D_x - w*D_y + x*D_z + y*D_w); 
##> X1 := PullbackVector(Phi1, Y1);
##> X2 := PullbackVector(Phi1, Y2); 
##-(nolead) We remark that since the vector fields 'X1' and 'X2' are uniquely determined, the Lie bracket relations are preserved.
##> Y3 := LieBracket(Y1, Y2);
##> X3 := PullbackVector(Phi1, Y3);
##> X3 &minus LieBracket(X1, X2);
##-(nolead)  
##-(nolead)  **Example 2.**
##- In the following example the map 'Phi2' is not a local immersion.
## We can use the 'freevariable' option to specify the name of the indexed variable that will be used to parameterize the vectors 'X2' such that 'Phi2\_\*(X2) = Y2'.
##> DGsetup([x, y, z, w], E4): DGsetup([t, u, v], E2):
##> Phi2 := Transformation(E4, E2, [u = x, v = z, t = 1]);
##> Y4 := D_u;
##> X4 := PullbackVector(Phi2, Y4, freevariable = 's');
##> X5 := PullbackVector(Phi2, D_t, freevariable = 's');  
##-(nolead)
##-(nolead) We can use the optional third argument to force the vector to belong to a given subspace.
##> X6 := PullbackVector(Phi2, Y4, [D_x, D_y], freevariable = 's');
##> X7 := PullbackVector(Phi2, Y4, [D_x], freevariable = 's');
##SEEALSO
##- "DifferentialGeometry", "Pushforward", "Transformation"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Pushforward" : Help:DifferentialGeometry/Pushforward
##- "Transformation" : Help:DifferentialGeometry/Transformation
