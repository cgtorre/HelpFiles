##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/GetComponents
##TITLE DifferentialGeometry[GetComponents]
##HALFLINE find the coefficients of a vector, differential form or tensor with respect to a list of vectors, differential forms or tensors
##CALLINGSEQUENCE
##-      GetComponents('T',' S',' options')
##PARAMETERS
##- T : a vector, differential form or tensor on a manifold 'M' or a list of such
##- S : a list of vectors, differential form or tensors
## options :  'method = \"real\"', 'trueorfalse = \"on\"/\"off\"', 'initialpointlist = [pt1, pt2, ...]'
##DESCRIPTION
##- If 'T' is a vector, differential form, or tensor and 'S = [S1, S2, S3, ...]' is a list of like objects, then the 
## procedure 'GetComponents(T, S) 'will return a list of Maple expressions 'C = [c1, c2, c3, ...]' such that 'T = c1\*S1 + c2\*S2 + c3\*S3 + ...' .  
## The expressions 'C 'are called the coefficients of 'T' with respect to the elements of 'S'.  
## If the elements of 'S' are linearly independent, then the coefficients 'C', if they exist, are unique. 
## If the coefficients 'C' cannot be found, that is, if 'T 'is linearly independent from the elements of 'S', then 'GetComponents(T, S)' will return '[]'.
##- If 'T = [T1, T2, T3, ...]' is a list of vectors, differential form or tensors, then 'GetComponents(T, S)' will return a list of lists 'C = [C1, C2, C3, ...]', 
## where the 'Ci 'are the coefficients of 'T' with respect to the elements of 'S'.
##- If 'method = \"real\"', then 'GetComponents(T, S) 'will determine if 'T 'is a linear combination of the elements of 'S' with real numbers (i.e. constants) as coefficients.
##- If 'trueorfalse = \"on\"' then 'GetComponents' will simply return 'true' if 'T 'is a linear combination of 'S' and false otherwise.
##- Here are the details of how the 'GetComponents' procedure works with the option 'method = \"real\"'.  
## Let us just consider the question of when a function 'g(x, y)' is a constant linear combination of the functions 'f1(x, y)', 'f2(x, y)', 'f3(x, y)', ' ...', that is, 'g(x, y) = c1\*f1(x, y) + c2\*f2(x, y) + c3\*f3(x, y) + ... (\*)'.
## The first approach is to use the Maple random number generator to pick many numerical values '[xi, yi]' for the coordinates '[x, y]', substitute these values into '(\*)' 
## to obtain a large overdetermined system, and use 'LinearAlgebra:-LinearSolve' to find the 'c1, c2, c3, ...'.  
## This works well when the 'fi(x, y)' are rational functions (except for the remote possibility that a value of '[x, y]' is chosen to be a singular point for one of the functions).  
## The second method is to take repeated derivatives of '(\*) 'with respect to all the variables and evaluate the results at a few select user specified points 'pt1, pt2'.  
## This too will generate a large overdetermined system which can then be solved for the 'c1, c2, c3, ...'.  If the 'GetComponents' command is called with the 'initialpointlist = [pt1, pt2 , ..]' where 'pti = [ xi, yi]', 
## then the second method is used.  The second approach works better in cases where the functions are transcendental.
##- This command is part of the DifferentialGeometry package, and so can be used in the form GetComponents(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-GetComponents.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead) 
##-(nolead) Create a 3-dimensional manifold 'M' with coordinates '[x, y, z, w]'.
##> DGsetup([x, y, z, w], M):
##-(nolead) 
##-(nolead) **Example 1.**
##- Express the vector 'X' as a linear combination of the vectors 'S1'.  Check the result using 'DGzip'.
##> X1 := evalDG(x^2*D_x - y*z*D_y + z^3*D_w);
##> S1 := evalDG([D_x, D_y, D_z, D_w]);
##> C := GetComponents(X1, S1);
##> Y1 := DGzip(C, S1, "plus");
##> Y1 &minus X1;
##-(nolead) 
##-(nolead) **Example 2.**
##- Show that the 2-form 'omega2' is linearly independent of the 2-forms in 'S2'.
##> omega2 := evalDG(dx &w dy + dy &w dw);
##> S2 := evalDG([dx &w dz + dy &w dw,dx &w dz + dx &w dw, dy &w dz + dx &w dw, dx &w dz + dz &w dw]);
##> GetComponents(omega2, S2);
##> GetComponents(omega2, S2, trueorfalse = "on");
##-(nolead) 
##-(nolead) **Example 3.**
##-(nolead) Express the 1-forms in 'Omega' as linear combinations of the 1-forms in 'S3'.
##> Omega := evalDG([dx + dy, dy + dz, dz + dw, dx + dy + dz + dw]);
##> S3 := evalDG([dx, dy, dz, dw]);
##> GetComponents(Omega, S3);
##-(nolead) 
##-(nolead) **Example 4.**
##-(nolead) Show that the vector 'X' is a real linear combination of the vectors in 'S4' but not a real linear combination of the first 3 vectors in 'S4'
##> X4 := evalDG((x + 3)*D_x - (y + x + 1)*D_y);
##> S4 := evalDG([D_x, D_y, x*D_x, y*D_x, x*D_y, y*D_y]);
##> GetComponents(X4, S4, method = "real");
##> GetComponents(X4, S4[1..3], method = "real");
##-(nolead)
##-(nolead) **Example 5.**
##-(nolead) Show that the 1-form 'omega' is a real linear combination of the 1-forms in 'S5'.
##> with(DifferentialGeometry):
##> DGsetup([x, y, z, w], M);
##> omega := evalDG(sin(x)*dx + cos(y)*dy);
##> S5 := evalDG([sin(x)*dx, cos(x)*dx, sin(y)*dx, cos(y)*dx, sin(x)*dy, cos(x)*dy, sin(y)*dy, cos(y)*dy]);
##> GetComponents(omega, S5, method = "real", initialpointlist = [[x =0, y = 0],[x = 0, y = Pi]]);
##SEEALSO
##- "DifferentialGeometry", "DGbasis", "DGzip"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "DGbasis" : Help:DifferentialGeometry/DGbasis
##- "DGzip" : Help:DifferentialGeometry/DGzip
