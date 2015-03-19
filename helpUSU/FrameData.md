##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/FrameData
##TITLE DifferentialGeometry[FrameData]
##HALFLINE calculate the structure equations for a generic (anholonomic) frame
##CALLINGSEQUENCE
##-      FrameData('Fr',' FrName')
##PARAMETERS
##- Fr : a list of vector fields or differential 1-forms on a manifold 'M'
##- FrName : an unassigned Maple name or  string,  the name to that will be assigned to the frame with the command 'DGsetup'
##DESCRIPTION
##- There are many situations in differential geometry where computations are tremendously simplified by using a frame or co-frame other than the standard coordinate frame or co-frame. 
## We refer to a general (local) frame or co-frame on a manifold as an anholomonic frame.  
## Important examples of anholomonic frames are: the orthogonal frames constructed from a metric on a manifold; the null frames used in general relativity; the left (or right) invariant vector fields on a Lie group; the moving frames adapted to a free group action on a manifold.  Cartan\'s method of equivalence provides an algorithmic approach to constructing adapted co-frames for Pfaffian systems.
##- All of the commands in the 'DifferentialGeometry' package and the 'Tensor' subpackage work with general anholonomic frames.  
## At present, the commands in the 'JetCalculus' package work only with the standard coordinate frame.
##- The structure equations of a frame 'Fr = [X\_1, X\_2, ...]' (the 'X\_i' are vector fields) are the Lie bracket relations
##-(nolead, alignment = "centred") '[X\_i, X\_j] = F\_{ij}^k X\_k    (sum on k)'.
##-(alignment = "left") The structure equations for a co-frame 'Omega = [omega^1,  omega^2, ...]' (the 'omega^k' are differential 1-forms) are the exterior derivative formulas
##-(nolead, alignment = "centred")  'd(omega^k) = G\_{ij}^k omega ^i &w omega ^j'.
##-(nolead) If the co-frame 'Omega 'is the dual co-frame to the frame 'Fr', then the structure functions are related by 'G\_{ij}^k = -1/2\*F\_{ij}^k').
##- To work in 'DifferentialGeometry' with anholomonic frames on a manifold 'M', first define an underlying coordinate system on 'M' and define the anholomonic frame or co-frame relative to this coordinate system. 
## Use the command 'FrameData' to generate the structure equations for this frame (along with other data).  Pass the results of the 'FrameData' procedure to the "DGsetup" procedure.
##- This command is part of the DifferentialGeometry package, and so can be used in the form FrameData(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-FrameData.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tensor):
##-(nolead) 
##-(nolead) **Example 1.**
##- Calculate the structure equations for the frame 'Fr'.  Create a manifold 'N' with local coordinate '(x, y)' and 'Fr' as the frame for the tangent bundle.
##> DGsetup([x,y], M):
##> Fr := evalDG([x*D_x + y*D_y, y^2*D_x + x^2*D_y]);
##> FD := FrameData(Fr, N);
##> DGsetup(FD, verbose);
##-(nolead) Calculate the exterior derivative of the function 'x\*y' in terms of the co-frame dual to 'Fr'.
##> ExteriorDerivative(x*y);
##-(nolead) 
##-(nolead) **Example 2.**
##-(nolead) Find an orthonormal co-frame for the metric 'g'.
## Use this co-frame to compute the curvature tensor and its first covariant derivative. 
##> DGsetup([x,y], M):
##> g := evalDG(dx &t dx + exp(2*x)*dy &t dy); 
##> Omega := evalDG([dx, exp(x)*dy]);
##> coFD := FrameData(Omega, N);
##> DGsetup(coFD, [E], [omega], verbose);
##> g := evalDG(omega1 &t omega1 + omega2 &t omega2); 
##> C := Christoffel(g);
##> R := CurvatureTensor(C);
##> R1 := CovariantDerivative(R, C);
##-(nolead) 
##-(nolead) **Example 3.**
##-(nolead) In this example we shall encode the Liouville equation 'u\_xy = exp(u)' as a exterior differential system on a 7 manifold 'N' with a co-frame adapted to the hyperbolic structure of the equation. The steps are:
##-(nolead) 1. Create a manifold 'M' with coordinates '(x, y, u, p, q, r, t)' -- here we are using the classical notation for derivatives 'p = u\_x, q = u\_y, r = u\_xx, t = u\_yy'.
##-(nolead) 2. Define a co-frame 'Omega' on 'M' by 'Omega = [du - p\*dx - q\*dy, dp - r\*dx - exp(u)\*dy, dq - exp(u)\*dx - t\*dy, dx, dr - p\*dp, dy, dt - q\*dq]'.
##-(nolead) 3. Compute the structure equations for the co-frame 'Omega' using the 'FrameData' command.
##-(nolead) 4. Initialize the manifold 'N' with the co-frame 'Omega'.  Label the first 3 elements of the co-frame on 'N' as 'theta1', 'theta2', 'theta3', and the last 4 elements as 'pi1', 'pi2', 'pi3', 'pi4'.
##-(nolead) 5. Compute the exterior derivatives of 'theta1', 'theta2', 'theta3'.
##> with(DifferentialGeometry):
##> DGsetup([x, y, u, p, q, r, t], M):
##> Omega := evalDG([du - p*dx - q*dy, dp - r*dx -exp(u)*dy, dq - exp(u)*dx - t*dy, dx, dr - p*dp, dy, dt - q*dq]);
##> coFD := FrameData(Omega, N);
##> DGsetup(coFD, [E], [theta1, theta2, theta3, pi1, pi2, pi3, pi4]);
##> ExteriorDerivative(theta1);
##> ExteriorDerivative(theta2);
##> ExteriorDerivative(theta3);
##SECTION See Also 
##- "DifferentialGeometry", "Tensor", "CovariantDerivative", "CurvatureTensor", "DGsetup", "DualBasis"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tensor" : Help:DifferentialGeometry/Tensor
##- "CovariantDerivative" : Help:DifferentialGeometry/Tensor/CovariantDerivative
##- "CurvatureTensor" : Help:DifferentialGeometry/Tensor/CurvatureTensor
##- "DGsetup" : Help:DifferentialGeometry/DGsetup
##- "DualBasis" : Help:DifferentialGeometry/DualBasis
