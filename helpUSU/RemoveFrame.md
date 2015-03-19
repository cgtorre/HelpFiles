##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/RemoveFrame
##TITLE DifferentialGeometry[RemoveFrame]
##HALFLINE remove a frame from a Maple session
##CALLINGSEQUENCE
##- RemoveFrame('M')
##PARAMETERS
## M : an unassigned Maple name or a string
##DESCRIPTION
##- Remove a previously defined frame 'M' from the current Maple session.  All protected variables and frame and coframe labels associated with the frame 'M' become unassigned and unprotected.  
## The command returns the number of frames that remain available.
##- If the current frame is 'M' and 'M' is removed, then the current frame defaults to the first frame in an alphabetic listing of all remaining defined frames.
##- This command is part of the DifferentialGeometry package, and so can be used in the form RemoveFrame(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-RemoveFrame.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead) 
##-(nolead) **Example 1.**
##-(nolead) Create a pair of manifolds.
##> DGsetup([x, y], M, verbose):
##> DGsetup([u, v], N, verbose);
##-(nolead) The command 'DGinfo' can return a list of all defined manifolds, adapted frames, Lie algebras, etc. - everything created by 'DGsetup'.
##> Tools:-DGinfo("FrameNames");
##-(nolead) Note that 'u' is protected and 'D\_u' is assigned.
##> type(u, protected);
##> lprint(D_u);
##-(nolead)
##-(nolead) Now remove the frame 'N'.
##> RemoveFrame(N);
##-(nolead) The frame 'N' no longer shows up in the list of defined frames.
##> Tools:-DGinfo("FrameNames");
##-(nolead) The current frame is now 'M'.
##> Tools:-DGinfo("CurrentFrame");
##- Also, 'u' is no longer protected and 'D\_u' is unassigned.
##> type(u, protected);
##> lprint(D_u);
##SEEALSO
##- "DifferentialGeometry", "ChangeFrame", "DGinfo", "DGsetup"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "ChangeFrame" : Help:DifferentialGeometry/ChangeFrame
##- "DGinfo" : Help:DifferentialGeometry/Tools/DGinfo
##- "DGsetup" : Help:DifferentialGeometry/DGsetup
