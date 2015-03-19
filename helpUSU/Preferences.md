##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Preferences
##TITLE DifferentialGeometry[Preferences]
##CALLINGSEQUENCE
##- Preferences('keyword')
##- Preferences('keyword',' value')
##PARAMETERS
##- keyword : a string, the name of the particular preference
##- value : the value to be assigned to the preference
##DESCRIPTION
##- This command allows the user to control various display conventions used by the 'DifferentialGeometry' package; to specify the LaTeX formatting of 'DifferentialGeometry' objects such as vectors, differential forms and tensors; and to specify how commonly used Maple commands are used internally by 'DifferentialGeometry' procedures.
##- The following are the admissible keywords strings: 
##TABLE(width = 500, border = 0, alignment = center, colwidth = 1|1|1)
##ROW "DisplayFrameDefinitions" | "ErrorInfoLevel"  | "ErrorPrintLength"  
##ROW "HistoryDepth" | "JetNotation" | "Keywords"       
##ROW "PrettyPrint"  |  "PromptLength"  | "SafeMode" 
##ROW "Show"  | "ShowFramePrompt" |  "TensorDisplay"
##ROW "TeXBiformList" |  "TeXFormList" | "TeXLineBreak"     
##ROW "TeXPrintOrder" | "TeXVectorList" | "WedgeDisplay"  
##ROW "dsolve" |"nullspace" |  "pdsolve"              
##ROW "rref"  | "simplification"  |  "solve" 
##ENDTABLE                                                                   
##-  The  paragraphs below describes the use of each of these keywords.
##- This command is part of the DifferentialGeometry package, and so can be used in the form Preferences(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-Preferences.
##SECTION Details    
##>(show=false) Typesetting:-State() := "extended":
##SUBSECTION(collapsed=true, label=DisplayFrameDefinitions) \"DisplayFrameDefinitions\" 
##-(nolead) This preference controls what information is displayed when the command 'DGsetup' is executed. 
## When this preference is false, no display is displayed.  When this preference is true, the names of the coordinate variables and the labels for the frame vectors and coframe 1-forms are displayed.  The default preference is false.
##> with(DifferentialGeometry):
##> Preferences("DisplayFrameDefinitions");
##> DGsetup([x, y, z], E3);
##> Preferences("DisplayFrameDefinitions", true);
##> DGsetup([x, y, z], E3);
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label = "ErrorInfoLevel") \"ErrorInfoLevel\"
##-(nolead) This preference controls the amount of information provided by an error message from a 'DifferentialGeometry' command.  The default for 'ErrorInfoLevel' is 1.
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label=ErrorPrintLength) \"ErrorPrintLength\"
##-(nolead) For many of the error messages returned by the 'DifferentialGeometry' commands, 
## it is not necessary to display all the component information of the vectors, differential forms, and tensors provided as input.  
## By suppressing the component information, the error messages are generally much easier to read. 
## The 'ErrorPrintLength' preference controls the number of components which will be displayed 
## -- the first 'k' components will be displayed if the sum of their lengths does not exceed the integer specified by the 'ErrorPrintLength' preference.  
## The length of each component is calculated using the Maple 'length' command.  The default value for this preference is 0 so that no component information is displayed.  
## To display all component information, set this preference to infinity.
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label=HistoryDepth) \"HistoryDepth\"
##-(nolead) The 'Tools' command 'CalculationHistory' will store the results of certain critical intermediate computations which the user may wish to view.  The 'HistoryDepth' preference specifies the number of such computations to store.  The default value for this preference is 10.
##> with(DifferentialGeometry):
##-(nolead) To illustrate this preference, we create a small procedure called 'Test' and store some values calculated by this program using the 'CalculationHistory 'command.
##> Test := proc(n)
##>> local i;
##>> for i to n do
##>> Tools:-CalculationHistory:-Update("Test", [i, i^2])
##>> od; n^2 end: 
##-(nolead) Run the program 'Test'.
##> Test(25);
##-(nolead) Retrieve the calculated values.
##> Tools:-CalculationHistory:-Get("Test");
##-(nolead) Change the 'HistoryDepth' preference to 3.
##> Preferences("HistoryDepth", 3);
##-(nolead) 
##- Rerun the program 'Test' and retrieve the calculated values.  This time only 3 values are stored.
##> Test(25);
##> Tools:-CalculationHistory:-Get("Test");
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label=JetNotation) \"JetNotation\"
##-(nolead) In the mathematical literature, there are two standard index notations for representing derivatives of a function.  
## For example, if 'u = u(x, y)' then we have:
##-(nolead)  JetNotation1: 'u[1] = u\_x', 'u[2] = u\_y', 'u[1, 1] = u\_xx', 'u[1, 2] = u\_xy', 'u[2, 2] = u\_yy', 'u[1, 1, 1] = u\_xxx', 'u[1, 1, 2] = u\_xxy', 'u[1, 2, 2] = u\_xyy', 'u[2, 2, 2] = u\_yyy'.
##-(nolead) JetNotation2: 'u[1, 0] = u\_x', 'u[0, 1] = u\_y', 'u[2, 0] = u\_xx', 'u[1, 1] = u\_xy', 'u[0, 2] = u\_yy', 'u[3, 0] = u\_xxx', 'u[2, 1] = u\_xxy', 'u[1, 2] = u\_xyy', 'u[0, 3] = u\_yyy'.
##- The 'JetNotation' preference determines which notation is used by the 'DifferentialGeometry' package (and the 'JetCalculus' subpackage).  The default is 'JetNotation1'.
##> with(DifferentialGeometry):
##> Preferences("JetNotation");
##> DGsetup([x,y], [u], Jet, 3, verbose);
##> Preferences("JetNotation", "JetNotation2");
##> DGsetup([x, y], [u], Jet, 3, verbose);
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label=Keywords) \"Keywords\"
##-(nolead) The option 'Keywords' returns the list of all admissible keywords for the 'Preferences' procedure.
##> with(DifferentialGeometry):
##> Preferences("Keywords");
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label=DGPrettyPrint) \"PrettyPrint\"
##-(nolead) With the 'PrettyPrint' preference set to true, the components of vectors, differential forms and tensors are always displayed on the main text line -- they will not appear as numerators in fractions.  This is somewhat easier to read but has the disadvantage that the resulting outline (for vectors and 1-forms) cannot be copied and pasted.  The default for the 'PrettyPrint' preference is false.
##> with(DifferentialGeometry):
##> DGsetup([x, y, z], M):
##> Preferences("PrettyPrint");
##> X := evalDG(1/(x^2 + y^2)*dx &w dy - dx &w dz);
##> Preferences("PrettyPrint", true);
##> X := evalDG(1/(x^2 + y^2)*dx &w dy - dx &w dz);
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label=PromptLength) \"PromptLength\"
##-(nolead) This preference specifies the maximum number of characters that will be displayed in the frame prompt.
##> with(DifferentialGeometry):
##> DGsetup([x], Newton);
##> Preferences("PromptLength", 4);
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label=SafeMode) \"SafeMode\" 
##-(nolead) With the 'SafeMode' preference set to false, no global assignments are made for the coordinate vectors and 1-forms when the command 'DGsetup' is called.  Use this preference when writing programs in which temporary manifolds, Lie algebras, etc... need to be constructed.  This will avoid introducing globals into the Maple namespace.
##> with(DifferentialGeometry):
##> Preferences("SafeMode");
##> DGsetup([x], R1):
##> assigned(D_x), assigned(dx);
##-(nolead) Now set the 'SafeMode' preference to true.  The names 'D\_y' and 'dy' are not assigned nor are they protected.
##> Preferences("SafeMode", true);
##> DGsetup([y], R2):
##> assigned(D_y), assigned(dy);
##> D_y := 3;
##- Note that the coordinate vectors and forms for the frame 'R2' can still be accessed using commands from the 'Tools' subpackage.  In 'SafeMode', the internal representations of 'DifferentialGeometry' are displayed as output.
##> Tools:-DGvector(y);
##> Tools:-DGinfo("FrameBaseForms");
##> Preferences("SafeMode", false);
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label=Show) \"Show\"
##-(nolead) The option 'Show' returns the list of all the preference values.
##> with(DifferentialGeometry):
##> Preferences("Show");
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label=ShowFramePrompt) \"ShowFramePrompt\"
##-(nolead) With the 'ShowFramePrompt' set to false, the standard Maple prompt will be used.
##> with(DifferentialGeometry):
##> Preferences("ShowFramePrompt", false);
##> DGsetup([x, y], Gauss);
##> LieBracket(D_x, x*D_y);
##-(nolead) Notice that the prompt has remained the standard Maple prompt \'>\'.
##> Preferences("ShowFramePrompt", true);
##> DGsetup([x, y], Gauss);
##-(nolead) Now the prompt contains the name of the current frame.
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label =TensorDisplay) \"TensorDisplay\" 
##-(nolead) The preference 'TensorDisplay' controls how the tensor product is displayed in Maple output.  
## If this preference is 0, no symbol is printed; if this preference is 1, then \''&t'\' is printed.  The default 'TensorDisplay' preference is 0.
##> with(DifferentialGeometry):
##> DGsetup([x, y, z], M):
##> alpha := evalDG(2*dx &t dy - dy &t dz);
##> Preferences("TensorDisplay", 1);
##> alpha;
##> Preferences("TensorDisplay", 0);
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label=TeXFormList) \"TeXFormList\", \"TeXVectorList\", \"TeXBiformList\", \"TeXPrintOrder\", \"TeXLineBreak\" 
##-(nolead) These preferences control how the Maple 'latex' command will TeX the components of a vector, differential form or tensor.  These preferences must be set by the user for each frame.
##> with(DifferentialGeometry):
##> DGsetup([x, y, z], M): DGsetup([x, y, z], N):
##-(nolead) Specify the LaTeX representations for the frame '[D\_x, D\_y, D\_z] 'on 'M'.
##> Preferences("TeXVectorList", M, ["\\partial_x", "\\partial_y", "\\partial_z"]);
##-(nolead) Specify the LaTeX representations for the coframe '[dx, dy, dz]' on 'M'.
##> Preferences("TeXFormList", M, ["dx", "dy", "d,z"]); 
##-(nolead) Specify the LaTeX representations for the frame '[D\_x, D\_y, D\_z]' on 'N'.
##> Preferences("TeXVectorList", N, ["\\frac{\\partial\\hfill}{\\partial_x}", "\\frac{\\partial\\hfill}{\\partial_y}", "\\frac{\\partial\\hfill}{\\partial_y}"]); 
##-(nolead) Specify the LaTeX representations for the coframe '[dx, dy, dz]' on 'N'.
##> Preferences("TeXFormList", N, ["\\alpha", "\\beta", "\\gamma"]); 
##-(nolead) Define a vector 'X1' and a form 'alpha1' on 'M' and convert to LaTeX.
##> ChangeFrame(M);
##> X1 := evalDG(3*D_x - D_y + z*D_z);
##> alpha1 := evalDG(y*dx - sin(z)*dy + (1/z)*dz);
##> latex(X1);
##> latex(alpha1);
##-(nolead)
##-(nolead) Now LaTeX the same vector and form, but viewed as objects on 'N'.
##> ChangeFrame(N);
##> X2 := evalDG(3*D_x - D_y + z*D_z);
##> alpha2 := evalDG(y*dx - sin(z)*dy + (1/z)*dz);
##> latex(X2);
##> latex(alpha2);
##-(nolead)
##-(nolead) The 'TeXPrintOrder' preference allows the user to specify the ordering of components in the TeX representation of a vector, differential form, or tensor.
##> ChangeFrame(M):
##> Preferences("TeXPrintOrder", [dy, dz, dx]);
##> latex(alpha1);
##> TensorOrder := evalDG([dx &t dx, dy &t dy, dz &t dz, dx &t dy, dx &t dz, dy &t dz]);
##> Preferences("TeXPrintOrder", TensorOrder);
##> T := evalDG(dx &t dy + dy &t dy);
##> latex(T);
##-(nolead)
##-(nolead) To LaTeX a vector or a form the 'TeXPrintOrder' preference must now be reset.  Often, the user may wish to insert the 'latex' output into a LaTeX alignment environment.  With the 'TeXLineBreak' preference, a carriage return '\\' and alignment character '&' can be automatically placed.after any number of components.
##> Preferences("TeXLineBreak", [1]);
##> latex(X1);
##> Preferences("TeXLineBreak", [1, 2]);
##> latex(X1);
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label =WedgeDisplay) \"WedgeDisplay\" 
##-(nolead) The preference 'WedgeDisplay' controls how the wedge product of differential forms is displayed in Maple output.  
## If this preference is 0, no symbol is printed; if this preference is 1, a \''^'\' is printed; and if the preference is 2, 
## then \''&w'\' is printed.  The default 'WedgeDisplay' preference is 1.
##> with(DifferentialGeometry):
##> DGsetup([x, y, z], M):
##> alpha := evalDG(2*dx &w dy - dy &w dz);
##> Preferences("WedgeDisplay", 0);
##> alpha;
##> Preferences("WedgeDisplay", 2);
##> alpha;
##ENDSUBSECTION
##SUBSECTION(collapsed=true, label=dsolve) \"dsolve\", \"nullspace\",\"pdsolve\", \"rref\", \"simplification\", \"solve\" 
##-(nolead) These preferences allow the user to customize the procedures which will be used with 'DifferentialGeometry' programs for 'dsolve', 'LinearAlgebra:-Nullspace', 'pdsolve', 'LinearAlgebra:-ReducedRowEchelonForm', 'simplify', and 'solve'.
## Here is a simple example.
##> with(DifferentialGeometry):
##> DGsetup([x], M);
##> ExteriorDerivative(sqrt(x^2)); 
##-(nolead) To obtain the simpler result 'dx', we can change the simplification command used by the 'DifferentialGeometry 'package.  Call the new simplification command 'MySimplify' and pass this procedure name to the 'Preferences'. Then rerun the ExteriorDerivative command.
##> MySimplify := x -> simplify(x, symbolic);
##> Preferences("simplification", MySimplify);
##> ExteriorDerivative(sqrt(x^2));
##ENDSUBSECTION
##SEEALSO
##- "DifferentialGeometry", "Tools", "CalculationHistory", "DGsetup", "evalDG", "latex"
##XREFMAP
##- "DisplayFrameDefinitions" : Help:#DisplayFrameDefinitions
##- "ErrorInfoLevel" : Help:#ErrorInfoLevel
##- "ErrorPrintLength" : Help:#ErrorPrintLength
##- "HistoryDepth" : Help:#HistoryDepth
##- "JetNotation" : Help:#JetNotation
##- "Keywords" : Help:#Keywords
##- "Macros" : Help:#Macros
##- "PrettyPrint" : Help:#DGPrettyPrint
##- "PromptLength" : Help:#PromptLength
##- "SafeMode" : Help:#SafeMode
##- "Show" : Help:#Show
##- "ShowFramePrompt" : Help:#ShowFramePrompt
##- "TensorDisplay" : Help:#TensorDisplay
##- "TeXBiformList" : Help:#TeXFormList
##- "TeXFormList" : Help:#TeXFormList
##- "TeXLineBreak" : Help:#TeXFormList
##- "TeXPrintOrder" : Help:#TeXFormList
##- "TeXVectorList" : Help:#TeXFormList
##- "WedgeDisplay" : Help:#WedgeDisplay
##- "dsolve" : Help:#dsolve
##- "nullspace" : Help:#dsolve
##- "pdsolve" : Help:#dsolve
##- "rref" : Help:#dsolve
##- "simplification" : Help:#dsolve
##- "solve" : Help:#dsolve
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "CalculationHistory" : Help:DifferentialGeometry/Tools/CalculationHistory
##- "DGsetup" : Help:DifferentialGeometry/DGsetup
##- "evalDG" : Help:DifferentialGeometry/evalDG
##- "latex" : Help:latex
