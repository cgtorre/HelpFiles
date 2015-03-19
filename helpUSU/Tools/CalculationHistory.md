##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Tools/CalculationHistory
##TITLE DifferentialGeometry:-Tools[CalculationHistory]
##CALLINGSEQUENCE
##-      CalculationHistory:-Update('S',' exp')
##-      CalculationHistory:-Get('S')
##-      CalculationHistory:-Clear()
##PARAMETERS
##-    S : an unassigned name or string
##-    exp : any Maple expression
##DESCRIPTION
##- The 'CalculationHistory' module is a collection of three simple commands for storing and retrieving the results of intermediate calculations.  
## The command 'Update(S, exp) 'stores the Maple expression 'exp' in a table (called the 'HistoryTable') with table index 'S'.'  'Only the 10 most current values of 'exp' are retained in the 'HistoryTable'.  The command 'Get(S) 'retrieves these values.  The command 'Clear()' clears all stored values in the 'HistoryTable'.
##- At present, the commands "Query/Indecomposable", "Decompose" and "Nilradical" use the 'CalculationHistory' module and store intermediate results which can be recalled.
##- The number of calculations stored in the 'HistoryTable' can be specified by the 'DifferentialGeometry:-Preferences' command.
##- This command is part of the DifferentialGeometry:-Tools package, and so can be used in the form CalculationHistory:-Update(...) only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.  It can always be used in the long form DifferentialGeometry:-Tools:-CalculationHistory:-Update.  The commands Get and Clear work the same way.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):with(Tools):with(LieAlgebras):
##> exports(CalculationHistory);
##-(nolead) 
##-(nolead) **Example 1.**
##- We begin with a simple example to illustrate the use of the three exports of the 'CalculationHistory' module.  The program 'Test' computes the sum of squares of the first 'n' integers.  The 'Update' command stores the individual terms in the sum.
##> Test := proc(n)
##>> local i, s, t;
##>> s := 0;
##>> for i to n do
##>> t := i^2;
##>> Tools:-CalculationHistory:-Update("Test", [i, t]);
##>> s := s + t;
##>> od;
##>> s
##>> end:
##-(nolead)
##- Run the program test.
##> Test(25);
##-(nolead) Retrieve the calculated values from the 'HistoryTable '-- only 10 values are stored.
##> Tools:-CalculationHistory:-Get("Test");
##-(nolead) Clear all calculated values.
##> Tools:-CalculationHistory:-Clear("Test");
##-(nolead) 
##-(nolead) ** Example 2.**
##-(nolead) The following example is taken from the help file for the 'LieAlgebras' command 'Decompose'.  A critical step in the algorithm involves factoring a certain polynomial.  This polynomial is stored in the 'HistoryTable' under the index \"'Decompose'.\"
##> L := _DG([["LieAlgebra", Alg3, [4]], [[[1, 3, 2], -2], [[1, 4, 1], -1], [[2, 3, 1], -1], [[2, 4, 2], -1]]]);
##> DGsetup(L);
##> Decompose():
##> CalculationHistory:-Get("Decompose");
##- 
##-(nolead) To perform the decomposition of the algebra, a factorization of the polynomial '-1/2 + \_z1^2' is required.  We perform this factorization by hand and rerun the 'DecomposeLieAlgebra' program using the hint option to pass the program the information it needs.
##> Decompose(hint = [x, [x^2 -1/2, [x-1/sqrt(2), x+1/sqrt(2)]]]);
##SEEALSO
##- "DifferentialGeometry", "LieAlgebras", "Decompose", "Preferences"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "LieAlgebras" : Help:DifferentialGeometry/LieAlgebras
##- "Decompose" : Help:DifferentialGeometry/LieAlgebras/Decompose
##- "Query/Indecomposable" :  Help:DifferentialGeometry/LieAlgebras/Query/Indecomposable
##- "Nilradical" : Help:DifferentialGeometry/LieAlgebras/Nilradical
##- "Preferences" : Help:DifferentialGeometry/Preferences
