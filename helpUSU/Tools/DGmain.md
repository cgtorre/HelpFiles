##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/Tools/DGmain
##TITLE DifferentialGeometry:-Tools[DGmain]
##CALLINGSEQUENCE
##-      DGmain:-'export'('args')
##PARAMETERS
##- export : one of: '&mult', '&plus', '&minus', '&tensor', '&wedge', 'Hook', 'DGzip'
##- args   : the arguments appropriate for the 'DifferentialGeometry' command of the same name
##DESCRIPTION
##- The module 'DGmain' contains 'DifferentialGeometry' procedures identical to procedures in the "DifferentialGeometry" package -- 
## the sole difference being that no argument checking or validation is performed by 'DGmain' procedures.  The 'DGmain' procedures can therefore be used in programming situations where the arguments to the procedures '&mult', '&plus', '&minus', '&tensor', '&wedge', 'Hook', 'DGzip' are known to be valid.
##- This command is part of the DifferentialGeometry:-Tools package, and so can be used in the form DGmain:-&mult only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.  It can always be used in the long form DifferentialGeometry:-Tools:-DGmain:-&mult.  The other valid exports work the same way.
##EXAMPLES    
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tools):
##> exports(DGmain);
##-(nolead) 
##-(nolead) Define a coordinate system '[x, y, z, w]'.
##> DGsetup([x, y, z, w], M); 
##-(nolead) Create two procedures which will determine the time needed to compute 'D\_x + D\_y + D\_z + D\_w':
##> Test1 := proc(n)
##>> local T, i;
##>> T := time();
##>> for i to n do
##>> D_x &plus D_y &plus D_z &plus D_w; 
##>> od;
##>> time() - T;
##>> end:
##> Test2 := proc(n)
##>> local T, i;
##>> T := time();
##>> for i to n do
##>> DGmain:-`&plus`(DGmain:-`&plus`(DGmain:-`&plus`(D_x, D_y), D_z), D_w);
##>> od;
##>> time() - T;
##>> end:
##-(nolead)
##-(nolead)  We see that Test2, which uses DGmain, is faster. 
##> Test1(1000);
##> Test2(1000);
##SECTION See Also 
##- "DifferentialGeometry", "Tools", "&minus", "&mult", "&plus", "&tensor", "&wedge", "DGzip", "Hook"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "&minus" : Help:DifferentialGeometry/&minus
##- "&mult" : Help:DifferentialGeometry/&mult
##- "&plus" : Help:DifferentialGeometry/&plus
##- "&tensor" : Help:DifferentialGeometry/&tensor
##- "&wedge" : Help:DifferentialGeometry/&wedge
##- "DGzip" : Help:DifferentialGeometry/DGzip
##- "Hook" : Help:DifferentialGeometry/Hook
