##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Hook
##TITLE DifferentialGeometry[Hook]
##CALLINGSEQUENCE
##-      Hook('X',' omega')
##-      Hook('Y, T, indexlist')
##HALFLINE form the interior product of a vector or a list of vectors with a differential form
##PARAMETERS
##- X : a vector or a list of vectors
##- omega : a differential 'p'-form
##- Y : a list of vectors or differential 1-forms
##- T : a tensor
##- indexlist : (optional) a list of positive integers labeling various arguments of the tensor 'T'   
##DESCRIPTION
##- If ' X' is a vector and 'omega' a differential 'p'-form, then the interior product or hook of ' X' and 'omega' is the 
## differential '(p - 1)'-form 'theta = Hook(X, omega)' defined by 'theta(Y1, Y2, ..., Yq) = omega(X, Y1, Y2, ..., Yq)', where 'q = p - 1 'and 'Y1',' Y2', '...',  'Yq'
## are arbitrary vectors.
##- More generally, given a list of vectors '[X1, X2, ... , Xr]' and a differential 'p'-form 'omega' then 'theta = Hook([X1, X2, ..., Xr], omega)' 
## is the differential form of degree 'p - r' defined by 'theta(Y1, Y2, ..., Yq) = omega(X1, X2, ..., Xr, Y1, Y2, ..., Yq)', where 'q = p - r' and 
## 'Y1',' Y2', ...,'Yq' are arbitrary vectors.
##- If ' Y = [X1, X2, alpha1, ..., Xr]' is a list of  vectors or differential 1-forms and 'T' is a tensor of total rank 's = r',
##  then the second calling sequence evaluates the scalar 'T(X1, X2, alpha1, ... , Xr)'.  
## If 's > r' and  'indexlist = [i\_1, i\_2, ..., i\_r]', then 'Hook(Y, T, indexlist)' calculates the rank 's - r' tensor obtained by evaluating the 
## 'i\_k-th 'argument of the tensor 'T 'on the 'k-th' element of the list 'Y', for 'k = 1, 2, ... r'.
##- This command is part of the DifferentialGeometry package, and so can be used in the form Hook(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-Hook.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##> DGsetup([x, y, z], M):
##-(nolead) 
##-(nolead) **Example 1.**
##-(nolead) Define vectors 'X1', 'X2', 'X3'.
##> X1 := evalDG(a*D_x + b*D_y + c*D_z);
##> X2 := evalDG(2*D_y - D_z);
##> X3 := evalDG(D_x + D_z);
##-(nolead) Define a 1-form 'alpha', a 2-form 'beta' and a 3-form 'omega'.
##> alpha := evalDG(3*dx + 4*dy - 7*dz);
##> beta := evalDG(dx &w dy - 3*dx &w dz);
##> omega := evalDG(dx &w dy &w dz); 
##-(nolead) Compute various interior products.  Note that 'Hook(Y, Hook(X, omega) = Hook([X, Y], omega)'.
##> f := Hook(X1, alpha);
##> theta := Hook(X1, beta);
##> Hook(X2, theta);
##> Hook([X1, X2], beta);
##> Hook([X2, X1], beta);
##> Hook([X1, X2, X3], omega);
##-(nolead) 
##-(nolead) **Example 2.**
##-(nolead) Evaluate a  type (1,3) tensor T on various vectors and differential forms.
##> T := evalDG(2*dx &t dy &t dz &t D_y - 3*dy &t dx &t dz &t D_z);
##> Hook([D_x, D_y, D_z, dy], T);
##> Hook([X1, X3], T);
##> Hook([X1, X2, X3, alpha], T);
##> Hook([D_y, dz], T, [1,4]);
##> Hook([X1, X2], T, [1,3]);
##-(nolead)  
##-(nolead) **Example 3.** 
##- The interior product can be calculated for abstract forms. 
##> DGsetup([[omega1, omega2, omega3], beta1 = dgform(2)], [d(omega1) = omega2 &w omega3, d(omega2) = beta1], M3);  
##> Hook(D_omega1 ,omega1); Hook(D_omega1, beta1);   
##-(nolead) Structure equations for interior products can be specified. 
##> DGsetup(M3, [], [hook(D_omega1, beta1) = omega3]); 
##> Hook(D_omega1, beta1); 
##SEEALSO
##- "DifferentialGeometry", "ContractIndices"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "ContractIndices" : Help:DifferentialGeometry/Tensor/ContractIndices
