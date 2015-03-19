##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/AlgebraicOperations
##TITLE DifferentialGeometry[algebraic operations]
##HALFLINE addition, subtraction, scalar multiplication, wedge product, tensor product
##CALLINGSEQUENCE
##- 'A' &plus 'B' - add two vectors, differential forms or tensors
##- 'A' &minus 'B'- subtract one vector, differential form or tensor from another
##- 'A' &mult 'B' - multiply a Maple expression by a vector, differential form or tensor
##- 'A' &wedge 'B'- form the wedge (or skew) product of a pair of differential forms or multi-vectors
##- 'A' &tensor 'B'- form the tensor product of a pair of tensors
##- 'A' &algmult 'B' - multiply two vectors in an algebra  
##PARAMETERS
##- A, B : Maple expressions, differential forms or tensors
##DESCRIPTION
##- In the DifferentialGeometry package the wedge product of  1-forms is defined in terms of the tensor product by
## __mrow(mi("&alpha;",fontstyle = "normal"),mo("&InvisibleTimes;"),mo("&and;"),mi("&beta;",fontstyle = "normal"),mo("&InvisibleTimes;"),mo("&equals;"),mo("&InvisibleTimes;"),mi("&alpha;",fontstyle = "normal"),mo("&InvisibleTimes;"),mo("&otimes;"),mo("&InvisibleTimes;"),mi("&beta;",fontstyle = "normal"),mo("&InvisibleTimes;"),mo("&uminus0;"),mo("&InvisibleTimes;"),mi("&beta;",fontstyle = "normal"),mo("&InvisibleTimes;"),mo("&otimes;"),mi("&alpha;",fontstyle = "normal"))__. 
##- When using these commands together within a single Maple expression, it is important to use parentheses to insure that the operations are executed in the correct order.
##- In an interactive Maple session, it is usually more convenient to use the commands "evalDG" and "DGzip" to perform these basic algebraic operations.
##- Here are the precise lists of admissible arguments for these commands.
##- 'A &plus B', 'A &minus B' -- 'A' and 'B': Maple expressions, vectors, differential forms of the same degree, differential biforms of the same bidegree, tensors with the same index type and density weights. 
##  'A' and 'B' must be defined on the same frame.
##- 'A &mult B' -- 'A': a Maple expression; 'B': a Maple expression, vector, differential form, differential biform, tensor. 'A' and 'B' must be defined on the same frame.
##- 'A &wedge B' -- 'A 'and 'B': Maple expressions or differential forms, differential biforms.  If 'A' and 'B' are forms, then the sum of their degrees cannot exceed the dimension of  the frame on which they are defined. 
## If 'A' and 'B' are bi-forms, then the sum of their horizontal degrees cannot exceed the dimension of the base manifold on which they are defined.  'A' and 'B' must be defined on the same frame.
##- 'A &tensor B' -- 'A' and 'B': Maple expressions, vectors, differential 1-forms, tensors.  'A' and 'B' must be defined on the same frame.
##- These commands are part of the DifferentialGeometry package, and so can be used in the forms given above only after executing the command with(DifferentialGeometry).
##EXAMPLES
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(LieAlgebras):
##- 
##- Use "DGsetup" to define a 3-dimensional manifold 'M' with coordinates '[x, y, z]'.
##> DGsetup([x, y, z], M, verbose);
##-(nolead) 
##-(nolead) **Example 1.**
##-(nolead) Create linear combinations of vector fields and differential 1-forms using '&plus' and '&mult'.
##> X1 := D_x &plus D_z;
##> X2 := ((3*z) &mult D_x) &plus ((- 2*y) &mult D_y);
##> X3 := X2 &minus ((3*z) &mult X1);
##> alpha1 := (sin(z) &mult dx) &minus (cos(y) &mult dz);
##> alpha2 := (cos(x) &mult dy) &plus (cos(z) &mult dz);
##-(nolead) 
##-(nolead) **Example 2.**
##-(nolead) Create differential 2-forms using '&plus' and '&mult' and '&wedge'.
##> alpha3 := (2 &mult (dx &wedge dy)) &plus (5 &mult (dy &wedge dz));
##> alpha4 := alpha1 &wedge alpha2;
##> alpha5 := (alpha1 &wedge alpha2) &minus alpha3;
##> alpha6 := alpha1 &wedge alpha3;
##-(nolead) 
##-(nolead) **Example 3.**
##- Create various tensors using '&plus', '&mult' and '&tensor'.
##> T1 := X1 &tensor X1;
##> T2 := X1 &tensor alpha1;
##> T3 := 1 &tensor (dx &wedge dy);
##> T4 := dx &tensor dx &tensor D_y &tensor D_z &tensor dz;
##> T5 := (1/y^2) &mult (dx &t dx + dy &t dy);
##-(nolead)
##-(nolead) **Example 4.**
##- Create a multi-vector using '&plus', '&mult' and '&tensor'.
##> V1 := (2 &mult (D_x &wedge D_y))  &plus (3 &mult (D_y &wedge D_z));
##-(nolead
##-(nolead) **Example 5.**
##- Use the command "AlgebraLibraryData" to retrieve the structure equations for the quaternions.
##> LA := AlgebraLibraryData("Quaternions", Q);
##- Initialize.
##> DGsetup(LA, [e,i, j, k], [theta]);
##- Calculate some simple sums and products of quaternions.
##> Q1 := i &algmult j;
##> Q2 := (e &plus i &plus j  &plus k) &algmult (e &minus (i &plus j  &plus k));
##
##SEEALSO
##- "DifferentialGeometry", "DGzip", "evalDG"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "DGzip" : Help:DifferentialGeometry/DGzip
##- "evalDG" : Help:DifferentialGeometry/evalDG
##- "AlgebraLibraryData" : Help:DifferentialGeometry/LieAlgebras/AlgebraLibraryData
