##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Convert
##TITLE convert routines of the DifferentialGeometry package
##CALLINGSEQUENCE
##-      convert('A',' DGArray')
##-      convert('B',' DGvector')
##-      convert('C',' DGform')
##-      convert('C',' DGspinor')
##-      convert('E',' DGtensor')
##-      convert('F',' DGjet')
##-      convert('F',' DGdiff')
##-      convert('G',' DGbiform',' bidegree')
##PARAMETERS
##- A : a tensor
##- B : a Matrix, a tensor, or the infinitesimal symmetry generators for a system of differential equations, as calculated by PDEtools:-Infinitesimals
##- C : a differential form or a differential biform
##- E : an Arrary, a vector, a differential form, or a spinor-tensor
##- F : a Maple expression
##- G : a differential form 
##DESCRIPTION
##- "convert(A, DGArray)" will convert a rank 'r' tensor 'A' to an 'r'-dimensional array.  For example, if 'A= a \* dx1 &t dx2 &t dx3' and 'T = convert(A, DGArray)', then 'T[1, 2, 3] = a ' and all other entries of 'T' are 0.
##- If 'B' is a square matrix, then "convert(B, DGvector)" will return a linear vector field.
##- If 'B' is a a rank 1 contravariant tensor, then "convert(B, DGvector)" will return the corresponding vector field.
##- If 'B' is a list of infinitesimal symmetry generators for a system of differential equations, as calculated by "PDEtools:-Infinitesimals", then "convert(B, DGvector)" will return a list of vector fields.
##- If 'C' is a rank 1 covariant tensor, then "convert(B, DGform)" will return a differential 1-form.
##- If 'C' is a differential biform, that is, a form expressed in terms of the contact forms on a jet space, then "convert(C, DGform)" will return the differential form on jet space obtained by replacing the contact forms by their coordinate formulas.
##- If 'E' is a spin-tensor, then "convert(E, DGspinor, sigma, indexlist)" will convert tensorial indices of 'E' to pairs of spinorial indices.
##- If 'E' is an Array, then "convert(E, DGtensor, indextype)" will convert 'E' to an 'r'-dimensional array.
##- If 'E' is a vector field, then "convert(E, DGtensor)" will convert 'E' to a rank 1 contravariant tensor.
##- If 'E' is a differential 'p'-form, then "convert(E, DGtensor)" will convert 'E' to a rank 'p' contravariant tensor.
##- If 'E' is a spinor-tensor, "convert(E, DGtensor, sigma, indexlist)" will convert pairs of spinorial indices of 'E' to tensorial indices.
##- "convert(F, DGjet)" will convert a Maple expression 'F' involving the Maple command "diff", applied to functions 'u(x, y, z, ...)', 'v(x, y, z, ...)', ... to the standard indexed notation for derivatives, for example, 'diff(u(x, y, z), x) -> u[1]', 'diff(u(x, y, z), x, y, z, z) -> u[1, 2, 3, 3]' etc.
##- "convert(F, DGdiff)" performs the inverse to the conversion command 'convert/DGjet', it will convert expressions 'F' involving the indexed notation for derivatives to expressions containing the Maple  "diff" command.
##- "convert(G, DGbiform)" will convert a differential 'p'-form 'G', defined on a jet space 'J^k(M, N) ', into a list of '(p + 1)'-biforms, 'Theta = [theta\_0, theta\_1, theta\_2, .. theta\_p]', where 'theta\_k' has contact degree 'k', and 'G = theta\_0 + theta\_1 + theta\_2 + ... + theta\_p.'
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":

##SUBSECTION(collapsed = true, label = convertDGArray) convert/DGArray
##> with(DifferentialGeometry):
##-(nolead)
##-(nolead) **Example 1**.
##-(nolead) We define a manifold 'M' with coordinates '[x, y, z]'. On 'M' we define two tensors 'T1' and 'T2'.  We convert these tensors to a Maple "Array"
##> DGsetup([x,y,z], M):
##> T1 := evalDG(D_z &t D_x + D_x &t D_y);
##> T2 := evalDG(2*dx &t D_x &t dy + dz &t D_z &t dx); 
##> A1 := convert(T1, DGArray);
##> A2 := convert(T2, DGArray);
##> A2[1, 1, 2];
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = convertDGvector) convert/DGvector
##> with(DifferentialGeometry): with(Tensor):
##-(nolead)
##-(nolead) **Example 1.**
##-(nolead) We define a manifold 'M' with coordinates '[x, y, z]'.  We convert a matrix to a linear vector field.
##> DGsetup([x, y, z], M):
##> A := Matrix([[1, 0, 1], [0, 2, 0], [0, 3, 0]]);
##> convert(A, DGvector);
##-(nolead)
##-(nolead) **Example 2.**
##-(nolead)
## We define a manifold 'M' with coordinates '[x, y, z]'.  On 'M' we define two tensors 'T1' and 'T2' and contract the 1st and 3 indices of 'T1' against the 1st and second indices of 'T2'.  The result is a contravariant rank 1 tensor 'S' on 'M'.  We then convert 'S' to a vector field 'X'.
##> DGsetup([x, y, z], M):
##> T1 := evalDG(2*dx &t D_x &t dy + dz &t D_z &t dx);
##> T2 := evalDG(D_z &t D_x + D_x &t D_y);
##> S := ContractIndices(T1, T2, [[1, 1], [3, 2]]);
##> X := convert(S, DGvector);
####-(nolead) The tensor 'S' and vector 'X' both have the same external displays but are have different internal representations.  We can see this using 'DGinfo' or 'lprint'.
##> Tools:-DGinfo(S, "ObjectType"), Tools:-DGinfo(X, "ObjectType"); 
##> lprint(S), lprint(X);
##-(nolead)
##-(nolead) **Example 3.**
##-(nolead) We use the "PDEtools:-Infinitesimals" program to find the infinitesimals symmetries of a system of differential equations.  We convert the output of this program, which lists of the components of the infinitesimal symmetries, to a list of vector fields on the manifold of independent and dependent variables.
##> DE:=[diff(u(x, y), x, y) = v(x, y)^2, diff(v(x, y), x$2) = u(x, y)];
##> Sym := PDEtools:-Infinitesimals(DE, [u, v]);
##> DGsetup([x, y], [u, v], J, 2);
##> convert([Sym], DGvector);
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = convertDGform) convert/DGform
##> with(DifferentialGeometry): with(Tensor):
##-(nolead)
##-(nolead) **Example 1.**
##-(nolead) We define a manifold 'M' with coordinates '[x, y, z]'.  On 'M' we define a tensor 'T' and contract the 1st and 3rd indices of 'T'.  The result is a covariant rank 1 tensor 'S' on 'M'.  We then convert 'S' to a differential 1-form 'alpha'.
##> DGsetup([x, y, z], M):
##> T1 := evalDG(2*dx &t D_x &t dy + dz &t D_z &t dx);
##> S := ContractIndices(T1, [[1, 2]]);
##> X := convert(S, DGform);
##-(nolead) The  tensor 'S' and the 1 form 'alpha' both have the same external displays but are have different internal representations.  We can see this using 'DGinfo' or 'lprint'.
##> Tools:-DGinfo(S, "ObjectType"), Tools:-DGinfo(X, "ObjectType");
##> lprint(S), lprint(X);
##-(nolead)
##-(nolead) **Example 2.**
####-(nolead) We define the 2nd order jet space 'J^2(R^2, R)' for one function 'u' of two independent variables '[x, y]'.  We convert the standard contact forms on 'J^2(R^2, R)', which are represented as biforms of type '(0, 1)' to differential 1 forms.
##> DGsetup([x, y], [u], Jet, 2):
##> theta1, theta2, theta3 := Cu[], Cu[1], Cu[2];
##> convert(theta1, DGform);
##> convert(theta2, DGform);
##> convert(theta3, DGform);
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = convertDGspinor) convert/DGspinor
##-(nolead) The "solder form" 'sigma' is the fundamental spin-tensor in spinor algebra.  
## It provides for a 1-1 correspondence between vectors and rank 2 Hermitian spinors.
## The 'convert/DGspinor' uses a uer specified solder form to convert tensor indices of a given spinor-tensor to pairs of spinor indices. 
##> with(DifferentialGeometry): with(Tensor):
##-(nolead) To illustrate this convert procedure we first construct a solder form. 
## Define a vector bundle over 'M' with base coordinates '[x, y, z, t]' and fiber coordinates '[z1, z2, w1, w2]'.
##> DGsetup([t, x, y, z], [z1, z2, w1, w2], M); 
##-(nolead) Define a spacetime metric 'g' on 'M'. Our spinor conventions assume the metric has signature '[1, -1, -1, -1]'. 
##> g := evalDG(dt &t dt - dx &t dx - dy&t dy - dz &t dz);
##-(nolead) Define an orthonormal frame on 'M 'with respect to the metric 'g'. 
##>  F := [D_t, D_x, D_y, D_z];
##-(nolead) Calculate the solder form 'sigma' from the frame 'F'.  See "Spinor", "SolderForm".
##> sigma := SolderForm(F);
##-(nolead) **Example 1.**
##-(nolead) Define a vector 'X' and convert it to a contravariant rank 2 spinor 'psi'.  The 'convert/DGspinor 'command requires the solder form as a 3rd argument and a list of tensorial indices to be converted to spinorial indices as a 4th argument.
##> X := evalDG(a*D_t + b*D_y);
##> psi := convert(X, DGspinor, sigma, [1]);
##-(nolead) **Example 2.**
##-(nolead) Define a rank 3 tensor and convert the 1st and 3rd indices to pairs of spinor indices to obtain a rank 5 spin-tensor 'chi'. Note that the spinorial indices are moved to the right.
##> T := evalDG(D_x &t D_y &t dz);
##> chi := convert(T, DGspinor, sigma, [1,3]);
##-(nolead) **Example 3.**
##-(nolead) With the 'convert/DGspinor 'command, the spinor 'psi'. can be converted back to the vector 'X 'and the spin-tensor 'chi 'back to the tensor 'T'. 
##> convert(psi, DGtensor, sigma, [[1, 2]]);
##> convert(chi, DGtensor, sigma, [[2, 3], [4,5]]);
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = convertDGtensor) convert/DGtensor
##> with(DifferentialGeometry): with(Tensor):
##-(nolead)
##-(nolead) We define a manifold 'M' with coordinates '[x, y, z]'.
##> DGsetup([x, y, z], M):
##-(nolead)
##-(nolead) **Example 1.**
##-(nolead) We define a Matrix' A1' and convert it to a rank 2 tensor in 4 different ways:
##> A1:= Matrix([[1, 0, 2], [0, 2, 4], [1, 0, 0]]);
##> convert(A1, DGtensor, [["con_bas", "con_bas"], []]);
##> convert(A1, DGtensor, [["cov_bas", "con_bas"], []]);
##> convert(A1, DGtensor, [["con_bas", "cov_bas"], []]);
##> convert(A1, DGtensor, [["cov_bas", "cov_bas"], []]);
##-(nolead) **Example 2.**
##-(nolead) We define an 4 dimensional array and convert it to a rank 4 covariant tensor.
##> A2 := Array(1..3, 1..3, 1..3, 1..3):
##> A2[1, 2, 2, 3] := m;
##> A2[1, 3, 2, 1] := n;
##> convert(A2, DGtensor, [["con_bas", "cov_bas", "cov_bas", "cov_bas"], []]);
##-(nolead) **Example 3.**
##-(nolead) We define a vector field and convert it to a rank 1 contravariant tensor field.
##> X:= evalDG(x^2*D_y - y^2*D_z);
##> T := convert(X, DGtensor);
##-(nolead) The tensor 'T' and vector 'X' both have the same external displays but have different internal representations.  We can see this using 'DGinfo' or 'lprint'.
##> Tools:-DGinfo(X, "ObjectType"), Tools:-DGinfo(T, "ObjectType"); 
##> lprint(X), lprint(T);
##-(nolead)
##-(nolead) **Example 4.**
##-(nolead) We define a differential 2-form and convert it to a rank 2 covariant tensor field.
##> omega := evalDG(y*dx &w dy - z*dy &w dz); 
##> convert(omega, DGtensor);
##-(nolead) **Example 5.**
##-(nolead) A spinor or spinor-tensor can be converted to a tensor using a "solder form" 'sigma'. To work with spinors, define a vector bundle over 'M' with base coordinates '[x, y, z, t]' and fiber coordinates '[z1, z2, w1, w2]'.
##> DGsetup([t, x, y, z], [z1, z2, w1, w2], M);
##-(nolead) Define a spacetime metric 'g' on 'M'. Our spinor convention require that the metric has signature '[1, -1,-1,-1]'. 
##> g := evalDG(dt &t dt - dx &t dx - dy&t dy - dz &t dz);
##-(nolead) Define an orthonormal frame on 'M 'with respect to the metric 'g'.
##>  F := [D_t, D_x, D_y, D_z];
##-(nolead) Calculate the solder form 'sigma' from the frame 'F'.  See "Spinor", "SolderForm".
##> sigma := SolderForm(F);
##-(nolead) Define a contravariant rank 2 spinor 'psi 'and convert it to a rank 1 contravariant tensor 'X'.  In this situation, 'convert/DGtensor 'command requires the solder form as a 3rd argument and a list of pairs of spinorial indices to be converted to tensorial indices as a 4th argument.
##> psi := evalDG(-1/2*I*2^(1/2)*D_z1 &t D_w2+1/2*I*2^(1/2)*D_z2 &t D_w1);
##> X := convert(psi, DGtensor, sigma, [[1, 2]]);
##-(nolead) **Example 6.**
##-(nolead) Define a covariant rank 2 spinor 'psi  'and convert it to a rank 1 covariant tensor 'omega'. 
##> psi := evalDG(2^(1/2)*dz2 &t dw2);
##> omega := convert(psi, DGtensor, sigma, [[1, 2]]);
##-(nolead) **Example 7.**
##-(nolead) Define a covariant rank 4 spinor 'psi 'and convert it to a rank 2 covariant tensor 'G' .
##> psi := evalDG(dz1 &t dw1 &t dz2 &t dw2-dz1 &t dw2 &t dz2 &t dw1-dz2 &t dw1 &t dz1 &t dw2+dz2 &t dw2 &t dz1 &t dw1);
##> G :=convert(psi, DGtensor, sigma, [[1, 2], [3, 4]]); 
##-(nolead) **Example 8.**
##-(nolead) Define a mixed contravariant rank 5 spin-tensor 'psi 'and convert it to a rank 3 contravariant tensor in 2 different ways. (The tensors 'T1' and 'T2' are complex because 'psi 'is not Hermitian.)
##> psi := evalDG(-1/2*I*2^(1/2)*D_t &t D_z1 &t &t D_z1 &t D_w2+1/2*I*2^(1/2)*D_x &t D_z2 &t D_z2 &t D_w1);
##> T1 := convert(psi, DGtensor, sigma, [[2, 4]]);
##> T2 := convert(psi, DGtensor, sigma, [[3, 4]]);
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = convertDGjet) convert/DGjet, convert/DGdiff
##> with(DifferentialGeometry): with(Library):
##-(nolead)
##-(nolead) **Example 1.**
##-(nolead) We define the 2nd order jet space 'J^2(R^2, R)' for one function 'u' of two independent variables '[x, y]'.
##> DGsetup([x, y], [u], Jet, 2):
##-(nolead) We convert the Laplace of a function, defined using the Maple "diff" command into a standard index notation for coordinates on jet spaces.
##> L := diff(u(x, y), x, x) + diff(u(x, y), y, y);
##> convert(L, DGjet);
##-(nolead) **Example 2.**
##- We retrieve a 4th order ODE from Kamke and rewrite it in standard index notation for coordinates on jet spaces.
##> DGsetup([x], [y], J, 4);
##> ODE := Retrieve("Kamke", 1, [4, 8], variables = [x, y]);
##> convert(ODE, DGjet);
##-(nolead) **Example 3.**
##-(nolead) Define a 2-form on 'J^2(R^2, R)'.We convert the KdV equation, given in jet notation, to ordinary derivative notation.
##> DGsetup([t, x], [u], J, 3):
##> Delta := u[1] = u[2, 2, 2] + u[]*u[2];
##> convert(Delta, DGdiff);
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = convertDGbiform) convert/DGbiform
##> with(DifferentialGeometry):
##-(nolead) 
##-(nolead) Define a 2-form on 'J^2(R^2, R)'.We define the 2nd order jet space 'J^2(R^2, R)' for one function 'u' of two independent variables '[x, y]'.
##> DGsetup([x, y], [u], Jet, 2):
##-(nolead) Define a 2-form on 'J^2(R^2, R)'.
##> omega := evalDG(du[1] &w du[2]);
##-(nolead) Define a 2-form on 'J^2(R^2, R)'. To obtain the representation of omega in terms of the contact forms
## Cu[1] = du[1] - u[1, 1]\*dx - u[1, 2]\*dy and Cu[2] = du[2] - u[1, 2]\*dx - u[2, 2]\*dy   (\*)
## we solve the equations (\*) for du[1] and du[2], substitute for du[1] and du[2] into omega, and then  grade the terms according to their contact degree -- [2, 0] : not contact forms; [1,1] : linear in contact forms; [0, 2] : quadratic in contact forms.
##> convert(omega, DGbiform, [2, 0]);
##> convert(omega, DGbiform, [1, 1]);
##> convert(omega, DGbiform, [0, 2]);
##> convert(omega, DGbiform);
##ENDSUBSECTION

##SEEALSO
##- "DifferentialGeometry"

##XREFMAP
##- "convert(A, DGArray)" : Help:#convertDGArray
##- "convert(B, DGvector)" : Help:#convertDGvector
##- "PDEtools:-Infinitesimals" : Help:PDEtools/Infinitesimals
##- "convert(B, DGform)" : Help:#convertDGform
##- "convert(C, DGform)" : Help:#convertDGform
##- "convert(E, DGspinor, sigma, indexlist)" : Help:#convertDGspinor
##- "convert(E, DGtensor, indextype)" : Help:#convertDGtensor
##- "convert(E, DGtensor)" : Help:#convertDGtensor
##- "convert(E, DGtensor)" : Help:#convertDGtensor
##- "convert(E, DGtensor, sigma, indexlist)" : Help:#convertDGtensor
##- "convert(F, DGjet)" : Help:#convertDGjet
##- "convert(F, DGdiff)" : Help:#convertDGjet
##- "convert(G, DGbiform)" : Help:#convertDGbiform
##- "diff" : Help:diff
##- "Array" : Help:Array
##- "solder form" : Help:DifferentialGeometry/Tensor/SolderForm
##- "Spinor" : Help:DifferentialGeometry/Tensor/Spinor
##- "SolderForm" : Help:DifferentialGeometry/Tensor/SolderForm
##- "solder form" : Help:DifferentialGeometry/Tensor/SolderForm
##- "Spinor" : Help:DifferentialGeometry/Tensor/Spinor
##- "SolderForm" : Help:DifferentialGeometry/Tensor/SolderForm
##- "DifferentialGeometry" : Help:DifferentialGeometry
