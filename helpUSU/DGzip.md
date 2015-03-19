##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/DGzip
##TITLE DifferentialGeometry[DGzip]
##HALFLINE form a linear combination, wedge product or tensor product of a list of vectors, forms or tensors
##CALLINGSEQUENCE
##-      DGzip('C', 'T', 'operand')
##PARAMETERS
##- C : a list of Maple expressions
##- T : a list of vectors, differential 'p'-forms, or tensors (of the same type); the number of elements in 'C' and 'T' must be equal
##- operand : a string, one of '\"plus\"', '\"wedge\"', or '\"tensor\"'
##DESCRIPTION
##- 'DGzip(C, T, \"plus\")' returns the additive linear combination of the objects in 'T' with coefficients taken from the list 'C'.
##- 'DGzip(T, \"wedge\") 'returns the wedge product of the forms in 'T'.
##- 'DGzip(T, \"tensor\")' returns the tensor product of the tensors in the list 'T'.
##- This command is part of the DifferentialGeometry package, and so can be used in the form DGzip(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-DGzip.
##EXAMPLES     ##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead) 
##- Initialize a 4-dimensional manifold 'M' with coordinates '[x, y, z, w]'.
##> DGsetup([x, y, z, w], M):
##-(nolead)
##-(nolead) **Example 1.**
##- Form a vector on 'M' with arbitrary coefficients.
##> C1 := [a, b, c, d];
##> T1 := [D_x, D_y, D_z, D_w];
##> X := DGzip(C1, T1, "plus");
##-(nolead)
##-(nolead) **Example 2.**
##- Generate a list of 6 coefficients using the "seq" command, generate a basis for the 2-forms on 'M' using the "GenerateForms" command, and use 'DGzip' to make a general 2-form on 'M'.
##> C2 := [seq(a||i, i = 1 ..6)];
##> T2 := Tools:-GenerateForms([dx, dy, dz, dw], 2);
##> omega := DGzip(C2, T2, "plus");
##-(nolead)
##-(nolead) **Example 3.**
##-(nolead) Define the standard volume form on 'M'.
##> T3 := [dx, dy, dz, dw];  
##> nu := DGzip(T3, "wedge");
##-(nolead)
##-(nolead) **Example 4.**
##-(nolead) Create the tensor product of a list of tensors.
##> T4 := evalDG([dx, D_x, dy, D_y, dz, D_z, dw, D_w]);
##> T := DGzip(T4, "tensor");

##SEEALSO
##- "DifferentialGeometry", "&plus", "&minus", "&mult", "&wedge", "&tensor", "evalDG", "GetComponents"

##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "&plus" : Help:DifferentialGeometry/AlgebraicOperations
##- "&minus" : Help:DifferentialGeometry/AlgebraicOperations
##- "&mult" : Help:DifferentialGeometry/AlgebraicOperations
##- "&wedge" : Help:DifferentialGeometry/AlgebraicOperations
##- "&tensor" : Help:DifferentialGeometry/AlgebraicOperations
##- "evalDG" : Help:DifferentialGeometry/evalDG
##- "seq" : Help:seq
##- "GenerateForms" : Help:DifferentialGeometry/Tools/GenerateForms
##- "GetComponents" :  Help:DifferentialGeometry/GetComponents
