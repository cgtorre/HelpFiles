##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/DGsetup
##TITLE DifferentialGeometry[DGsetup]
##HALFLINE set up a coordinate system, a frame, a Lie algebra, define a set of abstract forms
##CALLINGSEQUENCE
##- DGsetup('varlist1',' framename',' options')
##- DGsetup('varlist1',' varlist2',' framename',' options')
##- DGsetup('varlist1',' varlist2',' framename',' jetorder, options')
##- DGsetup('framedata',' options')
##- DGsetup('Liealgebradata',' options')
##- DGsetup('alg, rho, V)'
##- DGsetup('abstractforms',' streqn', 'framename')
##- 
##PARAMETERS
##- varlist1 : a list of unassigned Maple names
##- varlist2 : a list of unassigned Maple names
##- framename : an unassigned Maple name or a string
##- jetorder : a positive integer
##- framedata : the structure equations for an anholonomic frame, as calculated by the procedure "FrameData"
##- Liealgebradata : the structure equations for a Lie algebra, as calculated by the procedure "LieAlgebraData"
##- abstractforms : a list specifying a set of abstract forms, without reference to any underlying set of coordinates
##- streqn : a list of structure equations for the exterior derivatives and interior products of an abstract form 
##- options : a list of frame labels, a list of co-frame labels, the keyword '\'quiet\'' or '\'verbose\''
##DESCRIPTION
##- All computational sessions with the 'DifferentialGeometry' package begin with a call to the 'DGsetup' command.  
## This command fixes the coordinate names for the manifold being defined; 
## specifies the vectors and 1-forms to be used as local frames and co-frames on the manifold; 
## and stores all the computational rules needed to work with the given frame or co-frame.  
## It is also used by the "JetCalculus" package to initialize a jet space to any given order and by the "LieAlgebras" package to prepare 
## for computations with Lie algebras.
##- The following table summarizes the different calling sequences for 'DGsetup'.


##TABLE(width="80%", alignment=center, colwidth="1|12", border = 0)
##ROW **Ex 1.** | Create a 2-dimensional *manifold* __mrow(mi("M"))__ with local coordinates __mrow(mfenced(mrow(mi("x"),mo("&comma;"),mi("y"))))__. 
##ROW ``|`    `> DGsetup([x, y], M) 

##ROW **Ex 2.** | Create a *fiber bundle* __mrow(mi("E"))__ with fiber coordinates __mrow(mfenced(mrow(mi("u"),mo("&comma;"),mi("v"))))__ 
## over a 3-dimensional base space with coordinates __mrow(mfenced(mrow(mi("x"),mo("&comma;"),mi("y"), mo("&comma;"),mi("z"))))__.
##ROW ``|`    `> DGsetup([x, y, z], [u,v], M); 

##ROW **Ex 3.** | Create the 3rd order *jet space* __mrow(mi("J"))__  for 2 independent variables __mrow(mfenced(mrow(mi("x"),mo("&comma;"),mi("y"))))__  
## and 1 dependent variable __mrow(mfenced(mrow(mi("u"))))__. 
##ROW ``|`    `> DGsetup([x, y], [u], J, 3);  

##ROW **Ex 4a.** | Perform calculations on a 3-dimensional manifold __mrow(mi("N"))__ in terms of an *anholonomic frame* __mrow(mi("F"))__. 
## The command "FrameData"  is used to calculate the structure equations for the  frame and this is passed to 'DGsetup'. 
##ROW ``|`    `> DGsetup([x, y, z], M);  
##ROW ``|`    `> F := evalDG([D_x, x\*D_x + D_y, y D_x + D_z]);                                    
##ROW ``|`    `> FD := FrameData(F, N);                                                              
##ROW ``|`    `> DGsetup(FD);                                                                      

##ROW **Ex 4b.** | Perform calculations on a 3-dimensional manifold __mrow(mi("N"))__ in terms of an *anholonomic frame* __mrow(mi("F"))__. Label the frame
## vectors __mrow(mfenced(mrow(mi("X"),mo("&comma;"),mo("&InvisibleTimes;"),mi("Y"),mo("&comma;"),mo("&InvisibleTimes;"),mi("Z")),open = "&lsqb;",close = "&rsqb;"))__
## and the co-frame 1-forms __mrow(mfenced(mrow(mi("&alpha;",fontstyle = "normal"),mo("&comma;"),mo("&InvisibleTimes;"),mi("&beta;",fontstyle = "normal"),mo("&comma;"),mo("&InvisibleTimes;"),mo("&InvisibleTimes;"),mi("&sigma;",fontstyle = "normal")),open = "&lsqb;",close = "&rsqb;"))__. 
##ROW ``|`    `> DGsetup(FD, [X, Y, Z], [alpha, beta, sigma]); 

##ROW **Ex 5.** | Perform calculations on a 3-dimensional manifold __mrow(mi("N"))__ in terms of an *anholonomic co-frame* __mrow(mi("&Omega;"))__. The command  
## The command "FrameData" is used to calculate the structure equations for the frame and this is passed to 'DGsetup'. 
##ROW ``|`    `> DGsetup([x, y, z], M); 
##ROW ``|`    `> Omega := evalDG([dx, x\*dx + dy, y\*dx + dz]); 
##ROW ``|`    `> FD := FrameData(Omega, N);
##ROW ``|`    `> DGsetup(FD); 

##ROW ** Ex 6a.** | Initialize a *Lie algebra* 'alg1' defined by a set of 3 matrices __mrow(mi("A"),mo("&InvisibleTimes;"),mo("&equals;"),mo("&InvisibleTimes;"),mfenced(mrow(msub(mi("M"),mn("1")),mo("&InvisibleTimes;"),mo("&comma;"),mo("&InvisibleTimes;"),msub(mi("M"),mn("2")),mo("&comma;"),mo("&InvisibleTimes;"),msub(mi("M"),mn("3"))),open = "&lsqb;",close = "&rsqb;"))__.
## Use "LieAlgebraData" to calculate the structure equations for the Lie algebra and pass this result to 'DGsetup'. 
##ROW ``|`    `> A := [Matrix([[1, 0], [0, 0]]), Matrix([[0, 1], [0, 0]]), Matrix([[0, 0],[0, 1]])];  
##ROW ``|`    `> LD := LieAlgebraData(A, alg1);
##ROW ``|`    `> DGsetup(LD); 
 
##ROW ** Ex 6b.** | Initialize a *Lie algebra* 'alg1' defined by a set of 3 matrices. Label the basis elements for the Lie algebra as __mfenced(mrow(msub(mi("f"),mn("1")),mo("&comma;"),mo("&InvisibleTimes;"),mo("&InvisibleTimes;"),msub(mi("f"),mn("2")),mo("&comma;"),mo("&InvisibleTimes;"),mo("&InvisibleTimes;"),msub(mi("f"),mn("3"))),open = "&lsqb;",close = "&rsqb;")__
## and the dual 1-forms by __mfenced(mrow(msub(mi("&xi;",fontstyle = "normal"),mn("1")),mo("&comma;"),mo("&InvisibleTimes;"),msub(mi("&xi;",fontstyle = "normal"),mn("2")),mo("&comma;"),mo("&InvisibleTimes;"),msub(mi("&xi;",fontstyle = "normal"),mn("3"))),open = "&lsqb;",close = "&rsqb;")__ 
##ROW ``|`    `> DGsetup(LD, [f], [xi]):

##ROW ** Ex 7.** | Initialize a *Lie algebra* 'alg1' defined by a set of 3 vector fields __mrow(mi("&Gamma;",fontstyle = "normal"),mo("&InvisibleTimes;"),mo("&equals;"),mo("&InvisibleTimes;"),mfenced(mrow(msub(mi("X"),mn("1")),mo("&InvisibleTimes;"),mo("&comma;"),mo("&InvisibleTimes;"),msub(mi("X"),mn("2")),mo("&comma;"),mo("&InvisibleTimes;"),msub(mi("X"),mn("3"))),open = "&lsqb;",close = "&rsqb;"))__.
## Use "LieAlgebraData" to calculate the structure equations for the Lie algebra and passed this result to 'DGsetup'. 
##ROW ``|`    `> DGsetup([x, y], M);
##ROW ``|`    `> Gamma : = evalDG([D_x, D_y, y\*D_x - x\*D_y]);
##ROW ``|`    `> LD := LieAlgebraData(A, alg1): 
##ROW ``|`    `> DGsetup(LD); 

##ROW ** Ex 8.** | Initialize a *Lie algebra* 'alg1' from a set of structure equations. For other ways to initialize a Lie algebra,
## see "LieAlgebraData". 
##ROW ``|`    `> B := [x, y, h];
##ROW ``|`    `> S := [[h, x] = 2\*x, [h, y] = -2\*y, [x, y] = h]; 
##ROW ``|`    `> LD := LieAlgebraData( S, B, alg);
##ROW ``|`    `> DGsetup(LD);

##ROW ** Ex 9.** | Initialize a *classical simple Lie algebra*, say __mrow(mi("sl",italic = "true",mathvariant = "italic"),mfenced(mrow(mn("3"))))__, the Lie algebra of 
## trace-free matrices. See "SimpleLieAlgebraData". 
##ROW ``|`    `> LD := SimpleLieAlgebraData("sl(3)", alg);
##ROW ``|`    `> DGsetup(LD);

##ROW **Ex 10. ** |Initialize a *Lie algebra with coefficients in a representation*.
##ROW ``|`    `> LD := LieAlgebraData( [h,x] = 2*x, [h,y] = -2*y, [x,y] =h], [x, y, h], alg);
##ROW ``|`    `> DGsetup(LD);
##ROW ``|`    `> DGsetup([x1, x2, x3], V);
##ROW ``|`    `> A := Adjoint();
##ROW ``|`    `> rho := Representation(alg, V, Adjoint());
##ROW ``|`    `> DGsetup(alg, rho, R):

##ROW **Ex 11. ** | Initialize a set of *abstract differential forms* with a given set of structure equations. 
##ROW ``|`    `> DGsetup([f = dgform(0), alpha = dgform(1), beta = dgfom(2)]', '[d(beta)  = alpha &w beta], M) 

##ROW **Ex 12. ** | Initialize an *abstract co-frame* and set of abstract differential forms with a given set of structure equations. 
##ROW ``|`    `> DGsetup([[alpha, beta], f = dgform(0),  sigma = dgform(2)], [d(alpha) = f *sigma, hook(D_alpha, sigma) = beta], M): 
##ENDTABLE

##EXAMPLES
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(LieAlgebras):
##-(nolead)
##- **Example 1.  Use the first calling sequence to set up up a coordinate system on a manifold.**
##- In this first example, we create a 2-dimensional manifold 'M' with coordinates '[x, y]'.
##> DGsetup([x, y], M, verbose); 
##- The coordinates are now protected names which cannot be assigned values. 
##- The standard coordinate vectors 'D\_x', 'D\_y' and dual 1 forms 'dx', 'dy' have been defined and protected.  We display the internal representation of these vectors just to show that they have been assigned values. (Knowledge of this internal representation of various objects used in the 'DifferentialGeometry' package is not required of the user).
##> lprint(D_x):
##> lprint(dx);
##- Without the option '\'verbose\'', the information concerning the definition and protection of variable is suppressed.  This behavior of the 'DGsetup' command can be controlled globally with the "Preferences" command.
##> DGsetup([u, v], N);
##-(nolead) 
##- **Example 2.  Use the second calling sequence to set up coordinates on a vector or fiber bundle.**
##- In many situations in differential geometry, one deals with vector bundles or fiber bundles 'pi: E -> M'.  For these applications, use the second calling sequence to 'DGsetup'.  The
##- first argument 'varlist1' should be coordinates for the basis manifold 'M' and the second argument should be the list of coordinates for the fiber of the bundle 'E'.  Here is the command
##- for creating a rank-2 bundle over a 3-dimensional space.  The base coordinates are '[x, y, z]' and the fiber coordinates are '[u, v]'.
##> DGsetup([x, y, z], [u, v], P, verbose);
##- This particular use of 'DGsetup' could be used, for example, to study a 3-dimensional manifold imbedded in a 5-dimensional Riemannian manifold, where the vectors 'D\_u' and 'D\_v' define a local basis for the normal bundle.
##-(nolead) 
##- **Example 3.  Use the third calling sequence to set up coordinates on a jet bundle.**
## The 'JetCalculus' subpackage of the 'DifferentialGeometry' package contains an extensive set of commands for symbolic computations on jet spaces.  
## These spaces provide the natural mathematical setting for the geometric approach to the calculus of variations and to differential equations.  
## The third calling sequence for the 'DGsetup' command will create a jet space over a bundle 'pi: E -> M' with prescribed lists of independent variables (coordinates on 'M') and dependent variables (fiber coordinates on 'E').
## In addition to the coordinate vectors and coordinate differential forms on jet space, 'DGsetup' also defines and protects the contact forms on jet space.  See the "JetCalculus" overview page for additional information regarding these differential forms.
## The user may specify which of two notational conventions are to be used to denote the jet coordinates.  See the "Preferences" command for details.
##- First we initialize the 3rd order jet space for 1 independent and 2 dependent variables.
##> DGsetup([t], [x, y], J12, 3, verbose); 
##- Here is the initialization of the 3rd order jet space for 2 independent and 1 dependent variable.
##> DGsetup([x, y], [U], J21, 3, verbose); 
##-(nolead)
##- **Example 4.  Use the fourth calling sequence to set up an anholonomic frame on a manifold.**
##- It is extremely important, for many calculations in 'DifferentialGeometry', to work with frames and co-frames other than the coordinate frame (e.g. D\_x, D\_y, ...) and the coordinate co-frame (e.g. dx, dy ...). 
##  For example, curvature tensor calculations are often greatly simplified by working in an orthonormal frame. 
## To set up a frame for subsequent computations with the 'DifferentialGeometry' package, first use the "FrameData" command to calculate the structure equations for the frame or co-frame.  
## Then pass the output of the 'FrameData' command to 'DGsetup'.
##> DGsetup([x, y, z], M);
##- The three vectors in the list 'F' are the vectors that will be used as a frame.
##> F := evalDG([D_x, D_y + x*D_x, D_z + y*D_x]); 
##- The command "FrameData" calculates the structure equations for this frame. These structure equations are displayed with the convention that the first element of the frame is E1, the second element is E2, and so on.  
## The name of the manifold with coordinates '[x, y, z]' and anholonomic frame 'F' is 'M1'.
##> StructureEquations := FrameData(F,M1);
##- Pass the output of 'FrameData' to the command 'DGsetup'.  Now in place of the coordinate vectors 'D\_x', 'D\_y', 'D\_z' and coordinate form 'dx', 'dy', 'dz', 
## we shall use the vectors 'F[1]', 'F[2]', 'F[3]' and the dual 1 forms.  The default labels for the frame elements are 'E1', 'E2', 'E3' and the default labels for the co-frame elements are 'Theta1', 'Theta2', 'Theta3'.
##> DGsetup(StructureEquations, verbose);
##- As sample calculations on the manifold 'M1' we have:
##> LieBracket(E2, E3);
##> ExteriorDerivative(Theta1);
##- We can specify the labels for the frame and the co-frame as optional arguments to 'DGsetup'.  The second argument is a list of names for the frame elements and the third argument is a list of names for the co-frame elements.  If a list with just one name is given, then that name is used as the kernel name for the list of frame or co-frame elements.  For example:
##> DGsetup(StructureEquations,[X, Y, Z], [omega], verbose);
##-(nolead) 
##- **Example 5.  Use the fourth calling sequence to set up an anholonomic co-frame on a manifold.**
##- The same commands used in the previous example can be used to create an anholonomic co-frame on a manifold.
##> DGsetup([x, y, z], M); 
##- The three 1-foms in the list 'Omega' are the 1-forms that will be used as a co-frame.
##> Omega := evalDG([dx, x*dx+dy, y*dx+dz]); 
##- The command 'FrameData' calculates the structure equations for this co-frame.  
## These structure equations are displayed with the convention that the first element of the frame is __mrow(msub(mi("&#920;",italic = "false"),mi(""),subscriptshift = "0"))__1,
## the second element is __mrow(msub(mi("&#920;",italic = "false"),mi(""),subscriptshift = "0"))__2, and so on.  The name of the manifold with coordinates '[x, y, z]' and anholonomic frame 'Omega' is 'M1'.
##> StructureEquations := FrameData(Omega,M1);
##- Pass the output of "FrameData" to the command 'DGsetup'.  Now in place of the coordinate vectors 'D\_x', 'D\_y', 'D\_z' and coordinate form 'dx', 'dy', 'dz', we shall use the 1-forms 'Omega[1]', 'Omega[2]',  'Omega[3]' and the dual vector fields.  The default labels for the frame elements are 'E1', 'E2', 'E3' and the default labels for the co-frame elements are 'Theta1', 'Theta2', 'Theta3'.
##> DGsetup(StructureEquations, verbose);  
##-(nolead) 
##- **Example 6.  Use the fifth calling sequence to initialize a Lie algebra, defined by a set of matrices**
##- The 'DGsetup' command can also be used to initialize a Lie algebra the same way that 'DGsetup' is used to initialize an anholonomic frame on a manifold.  Typically, one first obtains the structure equations for the Lie algebra using the "LieAlgebraData" command and then passes these structure equations to 'DGsetup'.  Structure equations for a large number of Lie algebras can also be retrieved from the database of Lie algebras found in the "Library" package. 
##> M := [Matrix([[1,0],[0,0]]), Matrix([[0,1],[0,0]]), Matrix([[0,0],[0,1]])];
##- Calculate the structure equations for the matrix Lie algebra defined by the matrices 'M'.  Here 'e1' refers to the first matrix in 'M', 'e2' the second matrix, ....
##> StructureEquations := LieAlgebraData(M, Alg1);
##- The default names for the basis elements for the Lie algebra are 'e1', 'e2', 'e3'....  The default names for the basis elements for the dual elements of the Lie algebra are 'theta1', 'theta2', ....
##> DGsetup(StructureEquations, verbose); 
##- Again it is a simple matter to override this default labeling.
##> DGsetup(StructureEquations, [f], [xi], verbose);
##- **Example 7.  Use the fifth calling sequence to initialize a Lie algebra, defined by a set of vector fields** 
##- The same sequence of commands as illustrated in the previous example can be used to initialize a  Lie algebra from a set of vector fields. 
##> DGsetup([x, y], M7);  
##- Here are the vector fields we shall use. 
##> Gamma := evalDG([D_x, D_y, y*D_x - x*D_y]); 
##> LD := LieAlgebraData(Gamma, alg7); 
##> DGsetup(LD, [Tx, Ty, R], [omega]);
##> MultiplicationTable("LieTable"); 
##-(nolead)
##- **Example 8.  Use the fifth calling sequence to initialize a simple Lie algebra, defined by structure equations** 
##- The "LieAlgebraData" command, in conjunction with 'DGsetup',  can be used to initialize a Lie algebra from a set of structure equations.   
## First specify the basis elements.  These must be unassigned names. 
##> B := [x, y, h];  
##- Define a list of structure equations for a Lie algebra.  
##> S := [[h,x] = 2*x, [h,y] = -2*y, [x,y] = h]; 
##> LD := LieAlgebraData(S, B, alg8); 
##> DGsetup(LD); 
##- **Example 9.  Use the fifth calling sequence to initialize a simple Lie algebra, constructed from the command ** "SimpleLieAlgebraData" 
##- The LieAlgebra package contains tables of structures equations for the classical simple  and semi-simple matrix algebras. 
## These can be accessed with the command "SimpleLieAlgebraData". In this example we initialize __mrow(mi("sl",italic = "true",mathvariant = "italic"),mfenced(mrow(mn("3"))))__, the Lie algebra of __mrow(mn("3"),mo("&times;",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.2222222em",rspace = "0.2222222em"),mn("3"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"))__trace-free matrices. 
##> LD := SimpleLieAlgebraData("sl(3)", alg9); 
##> DGsetup(LD); 
##-(nolead)
##- **Example 10.  Use the sixth calling sequence to initialize a Lie algebra with coefficients in a representation** 
##- Exterior forms on Lie algebras can be generalized to allow for coefficients in a representation.  In this example we use the 3-dimensional Lie algebra defined in Example 7 and its adjoint representation. 
## First, define a 3-dimensional space to serve as the representation space.  
##> DGsetup([x1, x2, x3], V);  
##- Now  use the "Adjoint" and "Representation" commands to create the adjoint representation for __mrow(mi("alg7",italic = "true",mathvariant = "italic"))__. 
##> A := Adjoint(alg7); 
##> rho := Representation(alg7, V, A); 
##- Invoke the sixth calling sequence for *DGsetup*. 
##> DGsetup(alg7, rho, Rep1);  
##- At this point one can calculate, for example, the exterior derivative of  a 1-form on *alg7* with coefficients in V. 
##> DGsetup(alg7, rho, Rep1);
##-(nolead)
##- **Example 11.  Use the seventh  calling sequence to initialize a list of abstract differential forms** 
##- In this example we use 'DGsetup' to define a computational environment defined by a single scalar __mrow(mi("f",italic = "true",mathvariant = "italic"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"))__, a 1-form __mrow(msub(mi("&#945;",italic = "false"),mrow(mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),italic = "true",mathvariant = "italic"),subscriptshift = "0"))__and a 2-form __mrow(msub(mi("&#946;",italic = "false"),mi(""),subscriptshift = "0"))__.  The exterior derivative of __mrow(msub(mi("&#945;",italic = "false"),mi(""),subscriptshift = "0"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"))__is specified as __mrow(mi("d",italic = "true",mathvariant = "italic"),mfenced(mrow(mi("&#945;",italic = "false"))),mo("=",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.2777778em",rspace = "0.2777778em"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),mi("f",italic = "true",mathvariant = "italic"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),msub(mi("&#946;",italic = "false"),mi(""),subscriptshift = "0"))__. 
##> DGsetup([f = dgform(0), alpha = dgform(1), beta = dgform(2)], [d(alpha) = f*beta], M11);  
##> ExteriorDerivative(alpha); 
##> ExteriorDerivative(alpha &w beta &w beta); 
##- We use 'DGsetup' to add forms or structure equations.  
##> DGsetup(M11, [sigma = dgform(1)], [d(beta) = sigma &w beta]); 
##> ExteriorDerivative(beta);
##-(nolead) 
##- **Example 12.  Use the seventh calling sequence to initialize a co-frame and a list of abstract differential forms** 
##- This is essentially the same as Example 11 except that the first list, used to specify the list of abstract forms, now contains a sublist defining a co-frame.   
## In this example, we would like to label the co-frame as
## __mrow(mfenced(mrow(mi("&#969;1",italic = "true",mathvariant = "italic"),mo(",",fence = "false",separator = "true",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.3333333em"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),mi("&#969;2",italic = "true",mathvariant = "italic"),mo(",",fence = "false",separator = "true",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.3333333em"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),mi("&#969;3",italic = "true",mathvariant = "italic")),open = "[",close = "]"))__ 
## but these names were assigned to the 1-forms for the Lie algebra __mrow(mi("alg7",italic = "true",mathvariant = "italic"))__.  Therefore, we should first remove this frame.  
##> RemoveFrame(alg7); 
##> DGsetup([[omega1, omega2, omega3], beta1 = dgform(2)], [d(omega1) = omega2 &w omega3, d(omega2) = beta1], M12);  
##> ExteriorDerivative(omega1); 
##- In this setting interior products and Lie derivatives can be computed. 
##> Hook(D_omega2, beta1);  
##> LieDerivative(D_omega2, beta1); 
##- For more information on abstract differential forms in 'DifferentialGeometry', see "WorkingWithAbstractForms".
##-(nolead)
##SEEALSO
##- "DifferentialGeometry", "JetCalculus", "LieAlgebras", "ChangeFrame", "FrameData", "LieAlgebraData", "Preferences", "RemoveFrame" 
##XREFMAP
##- "JetCalculus" : Help:DifferentialGeometry/JetCalculus
##- "LieAlgebras" : Help:DifferentialGeometry/LieAlgebras
##- "FrameData" : Help:DifferentialGeometry:-FrameData
##- "FrameData" : Help:DifferentialGeometry:-FrameData
##- "LieAlgebraData" : Help:DifferentialGeometry:-LieAlgebras:-LieAlgebraData
##- "LieAlgebraData" : Help:DifferentialGeometry:-LieAlgebras:-LieAlgebraData
##- "LieAlgebraData" : Help:DifferentialGeometry:-LieAlgebra:-LieAlgebraData
##- "SimpleLieAlgebraData." : Help:DifferentialGeometry:-SimpleLieAlgebraData
##- "Preferences" : Help:DifferentialGeometry/Preferences
##- "JetCalculus" : Help:DifferentialGeomety/JetCalculus
##- "Preferences " : Help:DifferentialGeometry/Preferences
##- "FrameData" : Help:DifferentialGeometry/FrameData
##- "LieAlgebraData" : Help:LieAlgebras/LieAlgebraData
##- "Library" : Help:DifferentialGeometry/Library
##- "LieAlgebraData" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData
##- "SimpleLieAlgebraData" : Help:DifferentialGeometry/LieAlgebra/SimpleLieAlgebraData
##- "Adjoint" : Help:DifferentialGeometry/LieAlgebras/Adjoint
##- "Representation" : Help:DifferentialGeometry/LieAlgebra/Representation
##- "WorkingWithAbstractForms" : Help:DifferentialGeometry/WorkingWithAbstractForms
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "JetCalculus" : Help:DifferentialGeometry/JetCalculus
##- "LieAlgebras" : Help:DifferentialGeometry/LieAlgebras
##- "ChangeFrame" : Help:DifferentialGeometry/ChangeFrame
##- "FrameData" : Help:DifferentialGeometry/FrameData
##- "LieAlgebraData" : Help:DifferentialGeometry/LieAlgebras/LieAlgebraData
##- "Preferences" : Help:DifferentialGeometry/Preferences
##- "RemoveFrame" : Help:DifferentialGeometry/RemoveFrame
