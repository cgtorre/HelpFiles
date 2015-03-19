##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/IntegrateForm
##TITLE DifferentialGeometry[IntegrateForm]
##HALFLINE evaluate a p-fold iterated integral of a differential p-form
##CALLINGSEQUENCE
##- IntegrateForm('omega', 'integrationlimits')
##PARAMETERS
##- omega : a differential 'p'-form on a 'p'-dimensional manifold 'N'
##- integrationlimits : a 'p'-term sequence 't1 = a1  .. b1,  t2  =  a1(t1)  ..  b1(t1),  t3  =  a3(t1,  t2) .. b3(t1, t2), ...', 
## where 't1, t2, t3, ...' are coordinates on 'N', defining a 'p'-dimensional region in 'N'
##DESCRIPTION
##- With respect to the coordinates 't1, t2, t3, ...' on 'N', the 'p'-form 'omega 'can be written as 
## 'omega = f(t1, t2, t3, ...) dt1 &w dt2 &w dt3 ...'.  The command 'IntegrateForm' integrates the function 'f(t1, t2, t3, ...)' over the 'p'-dimensional region 
## defined by 't1 = a1 .. b1, t2 = a1(t1) ... b1(t1), t3 = a3(t1, t2) ... b3(t1, t2), ...'.
##- In many cases one is interested in integrating a 'p'-form 'omega 'on a manifold 'M' over an imbedding submanifold 'phi : N -> M'.  
## This is done in the 'DifferentialGeometry' package by first computing the pullback  'theta = Phi^\*(omega)' with the "Pullback" 
## command and then integrating the resulting 'p'-form 'theta' over 'N 'with the 'IntegrateForm' command.
##- In many cases a more efficient alternative to the 'IntegrateForm' command is provided by the "VectorCalculus[int]" command.
##- This command is part of the DifferentialGeometry package, and so can be used in the form IntegrateForm(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-IntegrateForm.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead) 
##-(nolead)  **Example 1.**
##-(nolead)  Integrate the 2-form '(x^2 + 3\*x\*y)\*dx &w dy' over the triangle 'T' with vertices '(0, 0)', '(1, 0)', and '(0, 1)'.
##> DGsetup([x, y], M):
##> omega := evalDG((x^2 + 3*x*y)*dx &w dy);
##-(nolead)  To evaluate the double integral over 'T' we note that for a point '(x, y)' in 'T' the variable 'x' ranges from '0' to '1' and, 
## for a given 'x' value, 'y' ranges from '0' to '1 - x'.
##> IntegrateForm(omega, x = 0..1, y = 0..1 - x);
##-(nolead)  
##-(nolead)  **Example 2.**
##-(nolead)  Compute the line integral of the 1-form 'omega = y^2\*dx + z^2\*dy + x\*y\*z\*dz' along the curve 'x = sin(t)\*cos(t), y = sin(t)\*cos(t), z = exp(t)' from 't = 0 'to 't = Pi'.
##> DGsetup([t], N): DGsetup([x, y, z], E3):
##> omega := evalDG(y^2*dx + z^2*dy +  x*y*z*dz);
##> Phi := Transformation(N, E3, [x = sin(t)*cos(t), y = sin(t)*cos(t), z = exp(t)]);
##> IntegrateForm(Pullback(Phi, omega), t = 0 .. Pi);
##-(nolead)  
##-(nolead)  **Example 3.**
##-(nolead)  Compute the surface integral of the 1-form 'omega = y^2\*z^2\*dx &w dy + x^2\*y^2\*dy &w dz + x^2\*z^2\*dx &w dz' 
## over the surface of the ellipsoid 'x^2 + y^2/4 + z^2/9 = 1'.
##-(nolead)  We shall parameterize the surface of the ellipsoid with coordinates '(theta, phi)' 
## and map 'x = cos(theta)\*sin(phi), y = 2\*sin(theta)\*sin(phi), z = 3\*cos(phi)'.
##> DGsetup([theta, phi], N): DGsetup([x, y, z], E3):
##> omega := evalDG(-3*y^2*z*dx &w dy + x*z^2*dy &w dz - x^2*y*dx &w dz);
##> Phi := Transformation(N, E3, [x = cos(theta)*sin(phi), y = 2*sin(theta)*sin(phi),  z = 3*cos(phi)]);
##> IntegrateForm(Pullback(Phi, omega), theta = 0 .. 2*Pi, phi = 0 .. Pi);
##SEEALSO
##- "DifferentialGeometry", "Pullback", "Transformation", "VectorCalculus[int]"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Pullback" : Help:DifferentialGeometry/Pullback
##- "Transformation" : Help:DifferentialGeometry/Transformation
##- "VectorCalculus[int]" : Help:VectorCalculus/int
