##PROCEDURE((helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/ChangeFrame
##TITLE DifferentialGeometry[ChangeFrame]
##HALFLINE change the current or active frame
##CALLINGSEQUENCE
##- ChangeFrame('M')
##PARAMETERS
##- M : a Maple name or string, the name given to a previously initialized frame/coordinate system
##DESCRIPTION
##- This command simply changes the current frame to 'M'.
##- The procedure returns the name of the previously active frame.
##- This command is part of the DifferentialGeometry package, and so can be used in the form ChangeFrame(...) only after executing the command with(DifferentialGeometry).  It can always be used in the long form DifferentialGeometry:-ChangeFrame.
##EXAMPLES
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry):
##-(nolead) Create a few manifolds:
##> DGsetup([x, y], M): DGsetup([u, v], N): DGsetup([x, y, z], P):
##-(nolead) 
##-(nolead)  **Example 1.**
##- Change to the frame 'M', check the name of the current frame and obtain the default basis for the tangent space of the current frame.
##> ChangeFrame(M);
##> Tools:-DGinfo("CurrentFrame");
##> Tools:-DGinfo("FrameBaseVectors");
##-(nolead)
##-(nolead)  **Example 2.**
##-(nolead)  Change to the frame 'N', check the name of the current frame and obtain the default basis for the tangent space of the current frame.
##> ChangeFrame(N);
##> Tools:-DGinfo("CurrentFrame");
##> Tools:-DGinfo("FrameBaseVectors");
##-(nolead) 
##-(nolead)  **Example 3.**
##-(nolead)  Since the frame 'M' was used more recently than the frame 'P', the vectors 'D\_x' and 'D\_y' are vectors on 'M' while the vector 'D\_z' is a vector on 'P'.
##> Tools:-DGinfo(D_x, "ObjectFrame"), Tools:-DGinfo(D_y, "ObjectFrame"), Tools:-DGinfo(D_z, "ObjectFrame");
##> ChangeFrame(P);
##-(nolead) The vectors 'D\_x', 'D\_y' and 'D\_z' are now all defined on 'P'.
##> Tools:-DGinfo(D_x, "ObjectFrame"), Tools:-DGinfo(D_y, "ObjectFrame"), Tools:-DGinfo(D_z, "ObjectFrame");
##SEEALSO 
##- "DifferentialGeometry", "Tools", "DGinfo", "DGsetup", "RemoveFrame"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "DGinfo" : Help:DifferentialGeometry/Tools/DGinfo
##- "DGsetup" : Help:DifferentialGeometry/DGsetup
##- "RemoveFrame" : Help:DifferentialGeometry/RemoveFrame
