##PROCEDURE(help, nospec, postprocess="helpmw_execute") DifferentialGeometry/Tools/DGinfo
##TITLE DifferentialGeometry:-Tools[DGinfo]
##HALFLINE obtain information about  DifferentialGeometry objects
##CALLINGSEQUENCE
##-      DGinfo('X', 'keyword')
##PARAMETERS
##- 'X' : a 'DifferentialGeometry' object
##- 'keyword' : a keyword string
##DESCRIPTION
##- The command 'DGinfo' provides a user friendly interface to the internal representations of all the objects and frames created by the 'DifferentialGeometry' software.
##- The keyword strings accepted by the 'DGinfo' command are: 
##TABLE(width = 750, border = 0, alignment = center, colwidth = 1|1|1)
##ROW "AbstractForms" | "BiformDegree" | "CoefficientGrading"
##ROW "CoefficientList" | "CoefficientSet" | "CoframeLabels"
##ROW "CurrentFrame" | "DiffeqType" | "DiffeqVariables"
##ROW "DomainFrame" | "DomainOrder" | "ExteriorDerivativeFormStructureEquations"
##ROW "ExteriorDerivativeFunctionStructureEquations" | "FormDegree" | "FrameBaseDimension"
##ROW "FrameBaseForms" | "FrameBaseVectors" | "FrameDependentVariables"
##ROW "FrameFiberDimension" | "FrameFiberForms" | "FrameFiberVectors"
##ROW "FrameGlobals" | "FrameHorizontalBiforms" | "FrameIndependentVariables"
##ROW "FrameInformation" | "FrameJetDimension" | "FrameJetForms"
##ROW "FrameJetOrder" | "FrameJetVariables" | "FrameJetVectors"
##ROW "FrameLabels" | "FrameNames" | "FrameProtocol"
##ROW "FrameVerticalBiforms" | "FunctionOrder" | "Grading"
##ROW "HorizontalCoframeLabels" | "JacobianMatrix" | "JetIndets"
##ROW "JetNotation" | "JetSpaceDimension" |  "Keywords"
##ROW "LieAlgebraDimension" | "LieBracketStructureEquations" |  "LieBracketStructureFunction"
##ROW "LieBracketStructureFunctionList" | "LieDerivativeFunctionStructureEquations" | "NonJetIndets" 
##ROW "ObjectAttributes" | "ObjectComponents" | "ObjectFrame"
##ROW "ObjectGenerators" | "ObjectOrder" | "ObjectType" 
##ROW "RangeFrame" |"RangeOrder" | "RepresentationMatrices"
##ROW "TensorDensityType" |"TensorGenerators" | "TensorIndexPart1"
##ROW "TensorIndexPart2" | "TensorIndexType" | "TensorType"
##ROW "TransformationType" | "VectorType" | "VerticalCoframeLabels" 
##ROW "Weight" | `` | ``
##ENDTABLE
                                                     
##- This command is part of the DifferentialGeometry:-Tools package and so can be used in the form DGinfo(...) only after executing the commands with(DifferentialGeometry) and with(Tools) in that order.  It can always be used in the long form DifferentialGeometry:-Tools:-DGinfo(...).

##SECTION Function, Vector, DifferentialForm, and Tensor Information
##>(show=false) Typesetting:-State() := "extended":

##SUBSECTION(collapsed = true, label = "BiformDegree") \"BiformDegree\"
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y], [u], E, 2):
##-(nolead)
##-(nolead) **Example 1.**
##> alpha1 := evalDG(Dx &wedge Dy);
##> DGinfo(alpha1, "BiformDegree");
##-(nolead) **Example 2.**
##> alpha2 := evalDG(Dx &wedge Cu[]);
##> DGinfo(alpha2, "BiformDegree");
##-(nolead) **Example 3.**
##> alpha3 := evalDG(Cu[1] &wedge Cu[2]);
##> DGinfo(alpha3, "BiformDegree");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "CoefficientList") \"CoefficientList\": list some or all of the coefficients of a vector, differential form, or tensor.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y, z, w], M):
##> alpha := evalDG(a*dx &w dy + b*dx &w dz + c*dy &w dz + d*dx &w dw + e*dz &w dw);
##> DGinfo(alpha, "CoefficientList", "all");
##> DGinfo(alpha, "CoefficientList", [dx &w dy, dx &w dz, dy &w dw]);
##> DGinfo(alpha, "CoefficientList", [[1,2], [1,3], [2,4]]);
##ENDSUBSECTION 

##SUBSECTION(collapsed = true, label = "CoefficientSet") \"CoefficientSet\": find the set of all the coefficients of a vector, differential form, or tensor.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y, z, w], M):
##-(nolead)
##-(nolead) **Example 1.**
##> alpha := evalDG(a*dx &w dy + b*dx &w dz + b*dy &w dz + c*dx &w dw + a*dz &w dw); 
##> DGinfo(alpha, "CoefficientSet");
##-(nolead) **Example 2.**
##> X := DGzero("vector");
##> DGinfo(X, "CoefficientSet");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "CoefficientList") \"CoefficientList\": list some or all of the coefficients of a vector, "differential form, or tensor.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y, z, w], M):
##> alpha := evalDG(a*dx &w dy + b*dx &w dz + c*dy &w dz + d*dx &w dw + e*dz &w dw);
##> DGinfo(alpha, "CoefficientList", "all");
##> DGinfo(alpha, "CoefficientList", [dx &w dy, dx &w dz, dy &w dw]);
##> DGinfo(alpha, "CoefficientList", [[1,2], [1,3], [2,4]]);
##ENDSUBSECTION 

##SUBSECTION(collapsed = true, label = "DiffeqType") \"DiffeqType\": find the type of the system of differential equations
##> with(DifferentialGeometry): with(JetCalculus): with(Tools):
##> DGsetup([x, y], [u, v], E, 2):
##> Delta := DifferentialEquationData([u[2] + v[1], u[1] - v[2]], [u[1], v[1]]); 
##> DGinfo(Delta, "DiffeqType");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "DiffeqVariables") \"DiffeqVariables\": list the jet variables in the differential equation to be solved for
##> with(DifferentialGeometry): with(JetCalculus): with(Tools):
##> DGsetup([x, y], [u, v], E, 2):
##> Delta := DifferentialEquationData([u[2] + v[1], u[1] - v[2]], [u[1], v[1]]); 
##> DGinfo(Delta, "DiffeqVariables");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FormDegree") \"FormDegree\": the degree of a differential form
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y, z], M): 
##-(nolead)
##-(nolead) **Example 1.**
##> alpha := evalDG(dx +dy);
##> DGinfo(alpha, "FormDegree");
##-(nolead) **Example 2.**
##> beta := evalDG(3*dx &w dy + 4*dy &w dz - dx &w dz);
##> DGinfo(beta, "FormDegree");
##-(nolead) **Example 3.**
##> nu := evalDG(dx &w dy &w dz);
##> DGinfo(nu, "FormDegree");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FunctionOrder") \"FunctionOrder\": the order of the highest jet coordinate appearing in a Maple expression.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1**.
##> DGsetup([x, y], [u, v], E):
##> f1 := u*x + v*y;
##> DGinfo(f1, "FunctionOrder"); 
##-(nolead) **Example 2**.
##> DGsetup([x, y], [u], J, 1):
##> f1 := u[1]*x + u[2];
##> DGinfo(f1, "FunctionOrder");
##-(nolead) **Example 3.**
##> f1 := u[1, 1, 2]*x + u[2, 2, 2, 2];
##> DGinfo(f1, "FunctionOrder");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "ObjectAttributes") \"ObjectAttributes\": list all the properties of a vector, differential form, tensor, or transformation.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y, z], M): DGsetup([u, v], N):
##-(nolead) 
##-(nolead) **Example 1**.
##> X := evalDG(a*D_x + b*D_y + c*D_z);
##> DGinfo(X, "ObjectAttributes");
##-(nolead) **Example 2**.
##> alpha := evalDG(d*dx &w dy + e*dx &w dz + f*dy &w dz); 
##> DGinfo(alpha, "ObjectAttributes");
##-(nolead) **Example 3**.
##> T := evalDG(r*D_x &t dx + s*D_z&t dy + t*D_z &t dx); 
##> DGinfo(T, "ObjectAttributes");
##-(nolead) **Example 4**.
##> Phi := Transformation(M, N, [u = x^2 + y^2 + z^2, v = x*y*z]);
##> DGinfo(Phi, "ObjectAttributes");
##-(nolead) **Example 5.**
##> DGsetup([[gamma1, gamma2, gamma3, gamma4], chi = dgform(3)], [], P):
##> ExteriorDerivative(chi);
##> DGinfo(dchi, "ObjectAttributes");
##-(nolead) **Example 6.**
##> Hook(D_gamma1, chi);
##> DGinfo(i_1chi, "ObjectAttributes");
##-(nolead) **Example 7.**
##> Hook([D_gamma2, D_gamma3], chi);
##> DGinfo(i_2_3chi, "ObjectAttributes");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "ObjectComponents") \"ObjectComponents\": list all the components of a vector, differential form, tensor, or transformation.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y, z], M): DGsetup([u, v], N):
##-(nolead)
##-(nolead) **Example 1.**
##> X := evalDG(a*D_x + b*D_y + c*D_z);
##> DGinfo(X, "ObjectComponents");
##-(nolead) **Example 2.**
##> alpha := evalDG(d*dx &w dy + e*dx &w dz + f*dy &w dz);
##> DGinfo(alpha, "ObjectComponents");
##-(nolead) **Example 3.**
##> T := evalDG(r*D_x &t dx + s*D_z&t dy + t*D_z &t dx);
##> DGinfo(T, "ObjectComponents");
##-(nolead) **Example 4.**
##> Phi := Transformation(M, N, [u = x^2 + y^2 + z^2, v= x*y*z]);
##> DGinfo(Phi, "ObjectComponents");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "ObjectFrame") \"ObjectFrame\": return the frame with respect to which the object is defined. 
##> with(DifferentialGeometry): with(Tools): 
##> DGsetup([x, y], [u], M, 1): DGsetup([r,s,t], N):
##-(nolead) **Example 1.**
##> X := evalDG(D_x -3*D_y);
##> DGinfo(X, "ObjectFrame");
##-(nolead) **Example 2.**
##> T := evalDG(D_r &t D_s &t dt);
##> DGinfo(T, "ObjectFrame");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "ObjectGenerators") \"ObjectGenerators\": list the monomial vectors in a vector or the monomial 1-forms in a differential form.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y, z, w], M):
##-(nolead) **Example 1.**
##> X := evalDG(y*D_x + z*D_z);
##> DGinfo(X, "ObjectGenerators");
##-(nolead) This means that 'X' has only the 1st and 3rd elements from the standard basis for the tangent bundle.
##-(nolead) **Example 2.**
##> alpha := evalDG(w*dx &w dy + x*dx &w dw + z^2*dy &w dw); 
##> DGinfo(alpha, "ObjectGenerators");
##-(nolead) This means that 'alpha' do not contain the 3rd element ('dz') from the standard basis for the cotangent bundle.
##ENDSUBSECTION


##SUBSECTION(collapsed = true, label = "ObjectOrder") \"ObjectOrder\": the order of the jet space on which the object is defined.
##> with(DifferentialGeometry): with(JetCalculus): with(Tools):
##-(nolead) 
##-(nolead) **Example 1**.
##> DGsetup([x, y], [u, v], E, 3):
##> f := u[2]*x + v[]*y;
##> DGinfo(f, "ObjectOrder");
##-(nolead) **Example 2**.
##> alpha := evalDG(du[1]*x + du[2,2]);
##> DGinfo(alpha, "ObjectOrder");
##-(nolead) **Example 3.**
##> beta := evalDG(du[1, 1, 2]*x + u[2, 2, 2, 2]*dy);
##> DGinfo(beta, "FunctionOrder");
##-(nolead) **Example 4.**
##> X := evalDG(u[1]*D_u[]);
##> X3 := Prolong(X, 2);
##> DGinfo(X3, "FunctionOrder");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "ObjectType") \"ObjectType\": the type of the 'DifferentialGeometry' object.
##> with(DifferentialGeometry): with(Tools): with(LieAlgebras):
##> DGsetup([x, y], [u], M, 1):
##-(nolead) 
##-(nolead) **Example 1.**
##> f := sin(x)*cos(y);
##> DGinfo(f, "ObjectType");
##-(nolead) **Example 2.**
##> X := evalDG(D_x + y*D_u[]);
##> DGinfo(X, "ObjectType");
##-(nolead) **Example 3.**
##> alpha := evalDG(dx &w dy + dx &w du[1]);
##> DGinfo(alpha, "ObjectType");
##-(nolead) **Example 4.**
##> theta := evalDG(Dx &w Cu[1]); 
##> DGinfo(theta, "ObjectType");
##-(nolead) **Example 5.**
##> T := evalDG(dx &t D_y + dy &t D_y);
##> DGinfo(T, "ObjectType");
##-(nolead) **Example 6.**
##> A := Vector([1, 2]);
##> DGinfo(A, "ObjectType");
##-(nolead) **Example 7.**
##> B := Matrix([1, 2]);
##> DGinfo(B, "ObjectType");
##-(nolead) **Example 8.**
##> B:= Matrix([[1, 2], [3, 4]]); 
##> DGinfo(B, "ObjectType");
##-(nolead) **Example 9.**
##> Phi := IdentityTransformation();
##> DGinfo(Phi, "ObjectType");
##-(nolead) **Example 10.**
##> L := LieAlgebraData(evalDG([D_x, x*D_x, x^2*D_x]));
##> DGinfo(L, "ObjectType");
##-(nolead) **Example 11.**
##> DGsetup([x, y], M);
##> F := FrameData([y*dx, x*dy], N);
##> DGinfo(F, "ObjectType");
##-(nolead) **Example 12.**
##> DGsetup([x, y], V);
##> R := [Matrix([[1, 0], [0, 0]]), Matrix([[0, 1], [0, 0]]), Matrix([[0, 0], [0, 1]])];
##> L := LieAlgebraData(R, Alg);
##> DGsetup(L);
##> rho := Representation(Alg, V, R);
##> DGinfo(rho, "ObjectType");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "TensorDensityType") \"TensorDensityType\": the density weight of a tensor.
##> with(DifferentialGeometry): with(Tools): with(Tensor):
##> DGsetup([x, y],[u, v, w], E):
##> g := evalDG(dx &t dx + dy &t dy);
##-(nolead) **Example 1.**
##> rho := MetricDensity(g, 3);
##> T1 := D_x &tensor rho;
##> DGinfo(T1, "TensorDensityType");
##-(nolead) **Example 2.**
##> T2 := PermutationSymbol("cov_vrt");
##> DGinfo(T2, "TensorDensityType");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "TensorGenerators") \"TensorGenerators\": a list of the monomial tensors which generate a given tensor.
##> with(DifferentialGeometry): with(Tools): with(Tensor):
##> DGsetup([x, y], [u, v, w], E):
##-(nolead) 
##-(nolead) **Example 1.**
##> T1 := evalDG(dx &t dx &t dx);
##> DGinfo(T1, "TensorGenerators"); 
##-(nolead) **Example 2.**
##> T2 := evalDG(dx &t D_y &t dy);
##> DGinfo(T2, "TensorGenerators"); 
##-(nolead) **Example 3.**
##> T3 := evalDG(du &t D_v &t dy);
##> DGinfo(T3, "TensorGenerators");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "TensorIndexPart1") \"TensorIndexPart1\": the tensor character of a tensor index type.
##> with(DifferentialGeometry): with(Tools):
##> DGinfo("con_bas", "TensorIndexPart1");
##> DGinfo("cov_bas", "TensorIndexPart1");
##> DGinfo("con_vrt", "TensorIndexPart1");
##> DGinfo("cov_vrt", "TensorIndexPart1");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "TensorIndexPart2") \"TensorIndexPart2\": the spatial type of a tensor index type.
##> with(DifferentialGeometry): with(Tools):
##> DGinfo("con_bas", "TensorIndexPart2");
##> DGinfo("cov_bas", "TensorIndexPart2");
##> DGinfo("con_vrt", "TensorIndexPart2");
##> DGinfo("cov_vrt", "TensorIndexPart2");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "TensorIndexType") \"TensorIndexType\": the full tensor index type of a tensor.
##> with(DifferentialGeometry): with(Tools): with(Tensor):
##> DGsetup([x, y], [u, v], E):
##-(nolead) **Example 1.**
##> T1 := evalDG(D_x &t D_y);
##> DGinfo(T1, "TensorIndexType");
##-(nolead) **Example 2.**
##> T2 := evalDG(dx &t D_y);
##> DGinfo(T2, "TensorIndexType");
##-(nolead) **Example 3.**
##> T3 := evalDG(du &t D_v);
##> DGinfo(T3, "TensorIndexType");
##-(nolead) **Example 4.**
##> T4 := evalDG(D_x &t D_v);
##> DGinfo(T4, "TensorIndexType");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "TensorType") \"TensorType\": the full tensor index type and weight of a tensor.
##> with(DifferentialGeometry): with(Tools): with(Tensor):
##> DGsetup([x, y], [u, v], E):
##-(nolead)
##-(nolead) **Example 1.**
##> T1 := evalDG(D_x &t D_y);
##> DGinfo(T1, "TensorType");
##-(nolead) **Example 2.**
##> T2 := PermutationSymbol("con_bas");
##> DGinfo(T2, "TensorType");
##-(nolead) **Example 3.**
##> T3 := evalDG(du &t D_v);
##> DGinfo(T3, "TensorType");
##-(nolead) **Example 4.**
##> T4 := PermutationSymbol("cov_vrt");
##> DGinfo(T4, "TensorType");
##-(nolead) **Example 5.**
##> T5 := PermutationSymbol("cov_bas") &tensor PermutationSymbol("con_vrt");
##> DGinfo(T5, "TensorType");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "VectorType") \"VectorType\": the type (projectionable, point, contact, ...) of a vector field and its order of prolongation.  See 'AssignVectorType' for details.
##> with(DifferentialGeometry): with(Tools): with(JetCalculus):
##> DGsetup([x,y], [u], E, 1):
##-(nolead) **Example 1.**
##> X1 := evalDG(D_x + u[] *D_u[]); 
##> X1a := AssignVectorType(X1);
##> DGinfo(X1a, "VectorType");
##-(nolead) **Example 2.**
##> X2 := Prolong(u[]*D_x - x *D_u[], 1); 
##> DGinfo(X2, "VectorType");
##-(nolead) **Example 3.**
##> X3 := GeneratingFunctionToContactVector(u[]*u[1]*u[2]); 
##> X3a := AssignVectorType(X3);
##> DGinfo(X3a, "VectorType");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "Weight") "\Weight\": the weight of a monomial form in a graded Lie algebra with coefficients
##> with(DifferentialGeometry): with(Tools):
##-(nolead)
##> LD:=LieAlgebraData([[x3, x4] = e1, [x3, x5] = x2, [x4, x5] = x3], [x1,x2,x3,x4,x5], Alg, grading = [-3, -3, -2, -1, -1]);
##> DGsetup(LD):
##> DGsetup([w1, w2, w3, w4, w5], V, grading = [-3, -3, -2, -1, -1]):
##> rho:= Representation(Alg, V, Adjoint(Alg));
##> DGsetup(Alg, rho, AlgV);
##-(nolead) **Example 1.**
##> alpha1 := evalDG(w3 *theta5);
##> DGinfo(alpha1, "Weight");
##-(nolead) **Example 2.**
##> alpha2 := evalDG(w3 * theta1 &w theta5);
##> DGinfo(alpha2, "Weight");
##-(nolead) **Example 3.**
##> alpha3 := evalDG(w1 * theta3 &w  &w theta4 &w theta5);
##> DGinfo(alpha3, "Weight");
##ENDSUBSECTION
##SECTION Transformation Information

##SUBSECTION(collapsed = true, label = "DomainFrame") \"DomainFrame\": the domain frame of a transformation.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y], M): DGsetup([u, v], N):
##> Phi := Transformation(M, N, [ u =x*y, v= 1/x + 1/y]);
##> DGinfo(Phi, "DomainFrame");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "DomainOrder") \"DomainOrder\": the jet space order of the domain of a transformation.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y], M): DGsetup([u, v], N): DGsetup([t], [w], J, 1):
##-(nolead) 
##-(nolead) **Example 1.**
##> Phi1 := Transformation(M, N, [u =x*y, v= 1/x + 1/y]);
##> DGinfo(Phi1, "DomainOrder");
##-(nolead) **Example 2.**
##> Phi2 := Transformation(J, M, [x = w[1], y = w[1, 1]]);
##> DGinfo(Phi2, "DomainOrder");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "JacobianMatrix") \"JacobianMatrix\": the Jacobian Matrix of a transformation.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y], M): DGsetup([u, v, w], N): 
##-(nolead) 
##-(nolead) **Example 1.**
##> Phi := Transformation(M, N, [u = x*y, v = 1/x + 1/y, w = x + y]);
##> DGinfo(Phi, "JacobianMatrix");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "RangeFrame") "RangeFrame\": the range frame of a transformation.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y], M): DGsetup([u, v], N):
##> Phi := Transformation(M, N, [u =x*y, v= 1/x + 1/y]);
##> DGinfo(Phi, "RangeFrame");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "RangeOrder") \"RangeOrder\": the jet space order of the range of a transformation.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y], M): DGsetup([u, v], N): DGsetup([t], [w], J, 1):
##-(nolead) 
##-(nolead) **Example 1.**
##> Phi1 := Transformation(M, N, [u =x*y, v= 1/x + 1/y]);
##> DGinfo(Phi1, "RangeOrder");
##-(nolead) **Example 2.**
##> Phi2 := Transformation(M, J, [t= x, w[]= y, w[1] = y^2]);
##> DGinfo(Phi2, "RangeOrder");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "RepresentationMatrices") \"RepresentationMatrices\": the list of matrices defining a representation of a Lie Algebra
##> with(DifferentialGeometry): with(LieAlgebras): with(Tools):
##-(nolead) 
##> DGsetup([x, y], V);
##> R := [Matrix([[1, 0], [0, 0]]), Matrix([[0, 1], [0, 0]]), Matrix([[0, 0], [0, 1]])];
##> L := LieAlgebraData(R, Alg);
##> DGsetup(L);
##> rho := Representation(Alg, V, R);
##> DGinfo(rho, "RepresentationMatrices"); 
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "TransformationType") \"TransformationType\": the type (projectionable, point, contact, ...) of a transformation.  See AssignTransformationType for details.
##> with(DifferentialGeometry): with(Tools): with(JetCalculus):
##> DGsetup([x], [u], E, 1):
##-(nolead)
##-(nolead) **Example 1.**
##> Phi1 := Transformation(E, E, [x = x^2, u[] = u[]*x]);
##> Phi1A := AssignTransformationType(Phi1);
##> DGinfo(Phi1A, "TransformationType"); 
##-(nolead) **Example 2.**
##> Phi2 := Transformation(E, E, [x = u[], u[] = x]);
##> Phi2A := AssignTransformationType(Phi2);
##> DGinfo(Phi2A, "TransformationType");
##-(nolead) **Example 3.**
##> Phi3 := Transformation(E, E, [x = -2*u[1] + x, u[] = -u[1]^2 + u[], u[1] = u[1]]);
##> Phi3A := AssignTransformationType(Phi3);
##> DGinfo(Phi3A, "TransformationType");
##ENDSUBSECTION

##SECTION Frame Information

##SUBSECTION(collapsed = true, label = "AbstractForms") \"AbstractForms\": the list of forms defined in an abstract frame.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##> DGsetup([[sigma1, sigma2, sigma3], tau = dgform(2), xi = dgform(3)], [], P):
##-(nolead)
##-(nolead) **Example 1.**
##> DGinfo(P, "AbstractForms");
##-(nolead) **Example 2.**
##> ExteriorDerivative(tau);
##> DGinfo(P, "AbstractForms");
##-(nolead) **Example 3.**
##> Hook(D_sigma1, xi);
##> Hook([D_sigma2, D_sigma3], xi);
##> DGinfo(P, "AbstractForms");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "CoefficientGrading") \"CoefficientGrading\": the grading of the coefficients in a Lie algebra with coefficients
##> with(DifferentialGeometry): with(LieAlgebras): with(Tools):
##-(nolead)
##-(nolead) **Example 1.**
##> LD:=LieAlgebraData([[x3, x4] = e1, [x3, x5] = x2, [x4, x5] = x3], [x1,x2,x3,x4,x5], Alg, grading = [-3, -3, -2, -1, -1]);
##> DGsetup(LD):
##> DGsetup([w1, w2, w3, w4, w5], V, grading = [-3, -3, -2, -1, -1]):
##> rho:= Representation(Alg, V, Adjoint(Alg));
##> DGsetup(Alg, rho, AlgV):
##> DGinfo(AlgV, "CoefficientGrading");
##> DGinfo(AlgV, "CoefficientGrading", output = "list");
##> DGinfo(output = "coefficients", "CoefficientGrading");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "CoframeLabels") \"CoframeLabels\": list the labels used to input and display the basis of 1-forms for the cotangent space.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "CoframeLabels"); 
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], M):
##> F := FrameData([y*dx, z*dy, dz], N);
##> DGsetup(F, [X], [omega]):
##> DGinfo(N, "CoframeLabels");
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], E, 2):
##> DGinfo(E, "CoframeLabels");
##-(nolead) **Example 4.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "CoframeLabels");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "CurrentFrame") \"CurrentFrame\": the name of the currently active frame.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x], M): DGsetup([y], N):
##> DGinfo("CurrentFrame");
##> LieBracket(D_x, x*D_x);
##> DGinfo("CurrentFrame");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "ExteriorDerivativeFormStructureEquations") \"ExteriorDerivativeFormStructureEquations\"**: list the formulas for the exterior derivatives of a frame with protocol '\"LieAlgebra\"' or '\"AnholonomicFrame\"'.
##> with(DifferentialGeometry): with(Tools):
##-(nolead)
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo("ExteriorDerivativeFormStructureEquations"); 
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], M):
##> F := FrameData([y*dx, z*dy, dz], N);
##> DGsetup(F, [X], [omega]):
##> DGinfo(N, "ExteriorDerivativeFormStructureEquations");
##-(nolead) **Example 3.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "ExteriorDerivativeFormStructureEquations");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "ExteriorDerivativeFunctionStructureEquations") \"ExteriorDerivativeFunctionStructureEquations\": list the formulas for the exterior derivatives of the coordinate functions for a frame with protocol or '\"moving\_frame\"'.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo("ExteriorDerivativeFunctionStructureEquations"); 
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], M):
##>> F := FrameData([y*dx, z*dy, dz], N);
##> DGsetup(F, [X], [omega]):
##> DGinfo(N, "ExteriorDerivativeFunctionStructureEquations");
##-(nolead) **Example 3.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "ExteriorDerivativeFunctionStructureEquations");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameBaseDimension") \"FrameBaseDimension\": the dimension of the base manifold 'M' for a frame defining a bundle 'E -> M'; the dimension of 'M' for a frame defining a manifold 'M'; the dimension of the Lie algebra for a frame defining a Lie algebra.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameBaseDimension");
##-(nolead) 
##-(nolead) **Example 2.**
##> DGsetup([x, y], [u, v, w], E):
##> DGinfo(E, "FrameBaseDimension"); 
##-(nolead) **Example 3.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "FrameBaseDimension");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameBaseForms") \"FrameBaseForms\": the basis 1-forms for the cotangent space of the base manifold 'M' for a frame defining a bundle 'E -> M'; the basis 1-forms for the cotangent space 'M' for a frame defining a manifold 'M'; the dual 1-forms of a Lie algebra for a frame defining a Lie algebra.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameBaseForms");
##-(nolead) 
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], M):
##>> F := FrameData([y*dx, z*dy, dz], N);
##> DGsetup(F, [X], [omega]):
##> DGinfo(N, "FrameBaseForms");
##-(nolead) 
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], E, 2):
##> DGinfo(E, "FrameBaseForms");
##-(nolead) 
##-(nolead) **Example 4.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "FrameBaseForms");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameBaseVectors") \"FrameBaseVectors\": the basis vectors for the tangent space of the base manifold 'M' for a frame defining a bundle 'E -> M'; the basis vectors for the tangent space 'M' for a frame defining a manifold 'M'; the basis vectors of a Lie algebra for a frame defining a Lie algebra.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameBaseVectors");
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], M):
##> F := FrameData([y*dx, z*dy, dz], N);
##> DGsetup(F, [W], [omega]):
##> DGinfo(N, "FrameBaseVectors");
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], E, 2):
##> DGinfo(E, "FrameBaseVectors");
##-(nolead) **Example 4.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "FrameBaseVectors");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameDependentVariables") \"FrameDependentVariables\": the dependent or fiber variables for a frame defining a bundle 'E -> M'.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameDependentVariables");
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], [u, v], E):
##> DGinfo(M, "FrameDependentVariables");
##-(nolead) **Example 3.**
##> DGsetup([x, y, z], [u, v], J, 1):
##> DGinfo(M, "FrameDependentVariables");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameFiberDimension") \"FrameFiberDimension\": the dimension of the fiber for a frame defining a bundle 'E -> M'.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameFiberDimension");
##-(nolead) 
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], [u, v], E):
##> DGinfo(E, "FrameFiberDimension");
##-(nolead) 
##-(nolead) **Example 3.**
##> DGsetup([x, y, z], [u, v], J, 1):
##> DGinfo(J, "FrameFiberDimension");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameFiberForms") \"FrameFiberForms\": the coordinate basis of vertical 1-forms for a fiber bundle 'E -> M'.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameFiberForms");
##-(nolead) **Example 2**
##> DGsetup([x, y, z], [u, v], E):
##> DGinfo(E, "FrameFiberForms");
##-(nolead) **Example 3**
##> DGsetup([x, y, z], [u, v], J, 1):
##> DGinfo(J, "FrameFiberForms");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameFiberVectors") \"FrameFiberVectors\": the coordinate basis of vertical vectors for a fiber bundle 'E -> M'.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameFiberVectors");
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], [u, v], E):
##> DGinfo(E, "FrameFiberVectors");
##-(nolead) **Example 3.**
##> DGsetup([x, y, z], [u, v], J, 1):
##> DGinfo(J, "FrameFiberVectors");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameGlobals") \"FrameGlobals\": the list of Maple names that are assigned or protected when a frame is defined using the 'DGsetup' command.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameGlobals");
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], M):
##> F := FrameData([y*dx, z*dy, dz],N);
##> DGsetup(F, [W], [omega]):
##> DGinfo(N, "FrameGlobals");
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], E, 2):
##> DGinfo(E, "FrameGlobals");
##-(nolead) 
##-(nolead) **Example 4.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "FrameGlobals");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameHorizontalBiforms") \"FrameHorizontalBiforms\": the list of horizontal biforms on a jet space
##> with(DifferentialGeometry): with(Tools): 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameHorizontalBiforms");
##-(nolead) 
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], [u, v], J, 1):
##> DGinfo(J, "FrameHorizontalBiforms");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameIndependentVariables") \"FrameIndependentVariables\": the coordinate variables of the base manifold 'M' for a frame defining a bundle 'E -> M'; the coordinate variables of 'M' for a frame defining a manifold 'M'; the internally defining coordinate variables of the Lie algebra for a frame defining a Lie algebra.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameIndependentVariables");
##-(nolead) 
##-(nolead) **Example 2.**
##> Omega := evalDG([y*dx, z*dy, dz]);
##> F := FrameData(Omega, N);
##> DGsetup(F, [X], [omega]):
##> DGinfo(N, "FrameIndependentVariables");
##-(nolead) 
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], E, 2):
##> DGinfo(E, "FrameIndependentVariables");
##-(nolead) 
##-(nolead) **Example 4.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "FrameIndependentVariables");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameInformation") \"FrameInformation\": a complete display of all information pertaining to a given frame.
##> with(DifferentialGeometry): with(Tools):
##-(nolead)
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameInformation");
##-(nolead) 
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], M):
##> F := FrameData([y*dx, z*dy, dz], N);
##> DGsetup(F, [W], [omega]):
##> DGinfo(N, "FrameInformation");
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], E, 2):
##> DGinfo(E, "FrameInformation");
##-(nolead) **Example 4.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "FrameInformation");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameJetDimension") \"FrameJetDimension\": the total dimension of the frame.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameJetDimension"); 
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], [u, v], N):
##> DGinfo(N, "FrameJetDimension");
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], E, 2):
##> DGinfo(J, "FrameJetDimension");
##-(nolead) **Example 4.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "FrameJetDimension");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameJetForms") \"FrameJetForms\": the basis of all 1-forms for the frame.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameJetForms");
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], [u, v], N):
##> DGinfo(N, "FrameJetForms");
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], J, 2):
##> DGinfo(J, "FrameJetForms");
##-(nolead) **Example 4.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "FrameJetForms");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameJetOrder") \"FrameJetOrder\": the jet space order of the frame.
##> with(DifferentialGeometry): with(Tools): with(JetCalculus):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], [u, v], N):
##> DGinfo(N, "FrameJetOrder"); 
##-(nolead) **Example 2.**
##> DGsetup([x, y], [u], J, 2):
##> DGinfo(J, "FrameJetOrder"); 
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], J, 2):
##> Prolong(4);
##> DGinfo(J, "FrameJetOrder");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameJetVariables") \"FrameJetVariables\": the list of all variables for the frame.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameJetVariables"); 
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], [u, v], N):
##> DGinfo(N, "FrameJetVariables");
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], J, 2):
##> DGinfo(J, "FrameJetVariables");
##-(nolead) **Example 4.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "FrameJetVariables");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameJetVectors") \"FrameJetVectors\": the list of all basis vectors for the frame.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameJetVectors");
##-(nolead) 
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], [u, v], N):
##> DGinfo(N, "FrameJetVectors");
##-(nolead) 
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], J, 2):
##> DGinfo(J, "FrameJetVectors");
##-(nolead) 
##-(nolead) **Example 4.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "FrameJetVectors");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameLabels") \"FrameLabels\": list the labels used to input and display the basis of vectors for the tangent space.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameLabels"); 
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], M):
##> F := FrameData([y*dx, z*dy, dz], N);
##> DGsetup(F, [W], [omega]):
##> DGinfo(N, "FrameLabels");
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], E, 2):
##> DGinfo(E, "FrameLabels");
##-(nolead) **Example 4.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "FrameLabels");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameNames") \"FrameNames\": the list of initialized frames
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##> DGinfo("FrameNames");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameProtocol") \"FrameProtocol\": the name of the frame protocol; this protocol controls the computation rules for many operations in 'DifferentialGeometry'.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameProtocol");
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], M):
##> F := FrameData([y*dx, z*dy, dz], N);
##> DGsetup(F, [X], [omega]):
##> DGinfo(N, "FrameProtocol");
##-(nolead) **Example 3.**
##> DGsetup([x, y], [u], E, 2):
##> DGinfo(E, "FrameProtocol");
##-(nolead) **Example 4.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "FrameProtocol");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "FrameVerticalBiforms") \"FrameVerticalBiforms\": the list of the contact 1-forms for a frame defining a jet space.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "FrameVerticalBiforms");
##> DGsetup([x, y], [u, v], J, 2):
##> DGinfo(J, "FrameVerticalBiforms");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "Grading") \"Grading\": the grading of a Lie algebra
##> with(DifferentialGeometry): with(LieAlgebras): with(Tools):
##-(nolead) **Example 1.**
##> LD:=LieAlgebraData([[x3, x4] = e1, [x3, x5] = x2, [x4, x5] = x3], [x1,x2,x3,x4,x5], Alg, grading = [-3, -3, -2, -1, -1]);
##> DGsetup(LD);
##> DGinfo(Alg, "Grading");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "HorizontalCoframeLabels") \"HorizontalCoframeLabels\": the list of labels, used for display purposes, for the horizontal biforms defined on a jet space.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "HorizontalCoframeLabels");
##> DGsetup([x, y], [u, v], J, 2):
##> DGinfo(J, "HorizontalCoframeLabels");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "LieBracketStructureEquations") \"LieBracketStructureEquations\": a matrix giving the Lie brackets of the frame basis vectors for a frame with protocol '\"LieAlgebra\"' or '\"AnholonomicFrame\"'.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "LieBracketStructureEquations"); 
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], M):
##> F := FrameData([y*dx, z*dy, dz], N);
##> DGsetup(F, [W], [omega]):
##> DGinfo(N, "LieBracketStructureEquations");
##-(nolead) **Example 3.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "LieBracketStructureEquations");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "LieBracketStructureFunction") \"LieBracketStructureFunction\": a specific structure function for a frame with '\"LieAlgebra\"' or '\"AnholonomicFrame\"' protocol.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##>> F := FrameData([y*dx, z*dy, dz], N);
##> DGsetup(F, [W], [omega]):
##> DGinfo(N, "LieBracketStructureEquations");
##> DGinfo([1,2,1], "LieBracketStructureFunction");
##> DGinfo([2,3,2], "LieBracketStructureFunction");
##> DGinfo([2,3,3], "LieBracketStructureFunction");
##-(nolead) **Example 2.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "LieBracketStructureEquations");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "LieBracketStructureFunctionList") \"LieBracketStructureFunctionList \": a list of structure function for a frame with \"LieAlgebra\" or \"AnholonomicFrame\" protocol.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "LieBracketStructureFunctionList");
##-(nolead) **Example 2.**
##> DGsetup([x, y, z], M):
##> F := FrameData([y*dx, z*dy, dz], N);
##> DGsetup(F, [W], [omega]):
##> [LieBracket(W1, W2), LieBracket(W1, W3), LieBracket(W2, W3)];
##> DGinfo(N, "LieBracketStructureFunctionList");
##-(nolead) **Example 3.**
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGsetup(L1):
##> DGinfo(Alg1, "LieBracketStructureFunctionList");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "LieDerivativeFunctionStructureEquations") \"LieDerivativeFunctionStructureEquations\": a matrix specifying the Lie derivatives of the coordinate variables with respect to the frame basis vectors for a frame with '\"AnholonomicFrame\"' protocol.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> F := FrameData([y*dx, z*dy, dz], N);
##> DGsetup(F, [X], [omega]):
##> DGinfo(N, "LieDerivativeFunctionStructureEquations");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "VerticalCoframeLabels": ) \"VerticalCoframeLabels\": the list of labels, used for display proposes, for the vertical biforms defined on jet space.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> DGinfo(M, "VerticalCoframeLabels");
##> DGsetup([x, y], [u, v], J, 1):
##> DGinfo(J, "VerticalCoframeLabels");
##ENDSUBSECTION

##SECTION Miscellaneous

##SUBSECTION(collapsed = true, label = "JetNotation") \"JetNotation\": the choice of jet notation for a frame defining the jet space or fiber bundle.
##> with(DifferentialGeometry): with(Tools):
##> DGsetup([x, y], [u], J1, 2):
##> DGinfo(J1, "FrameJetVariables");
##> DGinfo(J1, "JetNotation");
##> Preferences("JetNotation", "JetNotation2");
##> DGsetup([x, y], [u], J2, 2):
##> DGinfo(J2, "FrameJetVariables");
##> DGinfo(J2, "JetNotation");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "JetIndets") \"JetIndets\": the list of frame variables appearing in a Maple expression.  See the Maple 'indets' command.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> f1 := a*x^2 + b*y;
##> indets(f1);
##> DGinfo(f1, "JetIndets");
##-(nolead) **Example 2.**
##> DGsetup([x, y], [u,v], E, 2):
##> f2 := u[2,2]*c + exp(v[])*d;
##> DGinfo(f2, "JetIndets");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "JetSpaceDimension") \"JetSpaceDimension\": the dimension of a jet space of a given order for a given fiber bundle 'E'.
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) Example 1.
##> DGsetup([x], [u], J1, 1):
##> DGinfo(3, "JetSpaceDimension", J1);
##> DGinfo(4, "JetSpaceDimension", J1);
##-(nolead) Example 2.
##> DGsetup([x, y], [u], J2, 1):
##> DGinfo(2, "JetSpaceDimension", J2);
##> DGinfo(3, "JetSpaceDimension", J2);
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "Keywords") \"Keywords\": the keyword strings accepted by the 'DGinfo' command.
##> with(DifferentialGeometry): with(Tools):
##> DGinfo("Keywords");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "LieAlgebraDimension") \"LieAlgebraDimension\": the dimension of a Lie algebra, defined by a 'LieAlgebraData' structure.
##> with(DifferentialGeometry): with(Tools):
##> L1 := _DG([["LieAlgebra", Alg1, [4]], [[[2, 4, 1], 1], [[3, 4, 3], 1]]]);
##> DGinfo(L1, "LieAlgebraDimension");
##ENDSUBSECTION

##SUBSECTION(collapsed = true, label = "NonJetIndets") \"NonJetIndets\": the list of Maple names other than frame variables appearing in a Maple expression. 
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##> DGsetup([x, y, z], M):
##> f1 := a*x^2 + b*y;
##> indets(f1);
##> DGinfo(f1, "NonJetIndets"); 
##-(nolead) **Example 2.**
##> DGsetup([x, y], [u,v], E, 2):
##> f2 := u[2,2]*c + exp(v[])*d;
##> DGinfo(f2, "NonJetIndets");
##ENDSUBSECTION

##SEEALSO
##-(nolead) "DifferentialGeometry", "Tools", "JetCalculus", "LieAlgebras"

##XREFMAP
##- "AbstractForms" : Help:#AbstractForms
##- "BiformDegree" : Help:#BiformDegree
##- "CoefficientGrading" : Help:#CoefficientGrading
##- "CoefficientList" : Help:#CoefficientList
##- "CoefficientSet" : Help:#CoefficientSet
##- "CoframeLabels" : Help:#CoframeLabels
##- "CurrentFrame" : Help:#CurrentFrame
##- "DiffeqType" : Help:#DiffeqType
##- "DiffeqVariables" : Help:#DiffeqVariables
##- "DomainFrame" : Help:#DomainFrame
##- "DomainOrder" : Help:#DomainOrder
##- "ExteriorDerivativeFormStructureEquations" : Help:#ExteriorDerivativeFormStructureEquations
##- "ExteriorDerivativeFunctionStructureEquations" : Help:#ExteriorDerivativeFunctionStructureEquations
##- "FormDegree" : Help:#FormDegree
##- "FrameBaseDimension" : Help:#FrameBaseDimension
##- "FrameBaseForms" : Help:#FrameBaseForms
##- "FrameBaseVectors" : Help:#FrameBaseVectors
##- "FrameDependentVariables" : Help:#FrameDependentVariables
##- "FrameFiberDimension" : Help:#FrameFiberDimension
##- "FrameFiberForms" : Help:#FrameFiberForms
##- "FrameFiberVectors" : Help:#FrameFiberVectors
##- "FrameGlobals" : Help:#FrameGlobals
##- "FrameHorizontalBiforms" : Help:#FrameHorizontalBiforms
##- "FrameIndependentVariables" : Help:#FrameIndependentVariables
##- "FrameInformation" : Help:#FrameInformation
##- "FrameJetDimension" : Help:#FrameJetDimension
##- "FrameJetForms" : Help:#FrameJetForms
##- "FrameJetOrder" : Help:#FrameJetOrder
##- "FrameJetVariables" : Help:#FrameJetVariables
##- "FrameJetVectors" : Help:#FrameJetVectors
##- "FrameLabels" : Help:#FrameLabels
##- "FrameNames" : Help:#FrameNames
##- "FrameProtocol" : Help:#FrameProtocol
##- "FrameVerticalBiforms" : Help:#FrameVerticalBiforms
##- "FunctionOrder" : Help:#FunctionOrder
##- "Grading" : Help:#Grading
##- "HorizontalCoframeLabels" : Help:#HorizontalCoframeLabels
##- "JacobianMatrix" : Help:#JacobianMatrix
##- "JetIndets" : Help:#JetIndets
##- "JetNotation" : Help:#JetNotation
##- "JetSpaceDimension" : Help:#JetSpaceDimension
##- "JetSpaceVariables" : Help:#JetSpaceVariables
##- "Keywords" : Help:#Keywords
##- "LieAlgebraDimension" : Help:#LieAlgebraDimension
##- "LieBracketStructureEquations" : Help:#LieBracketStructureEquations
##- "LieBracketStructureFunction" : Help:#LieBracketStructureFunction
##- "LieBracketStructureFunctionList" : Help:#LieBracketStructureFunctionList
##- "LieDerivativeFunctionStructureEquations" : Help:#LieDerivativeFunctionStructureEquations
##- "NonJetIndets" : Help:#NonJetIndets
##- "ObjectAttributes" : Help:#ObjectAttributes
##- "ObjectComponents" : Help:#ObjectComponents
##- "ObjectFrame" : Help:#ObjectFrame
##- "ObjectGenerators" : Help:#ObjectGenerators
##- "ObjectOrder" : Help:#ObjectOrder
##- "ObjectType" : Help:#ObjectType
##- "RangeFrame" : Help:#RangeFrame
##- "RangeOrder" : Help:#RangeOrder
##- "RepresentationMatrices" : Help:#RepresentationMatrices
##- "TensorDensityType" : Help:#TensorDensityType
##- "TensorGenerators" : Help:#TensorGenerators
##- "TensorIndexPart1" : Help:#TensorIndexPart1
##- "TensorIndexPart2" : Help:#TensorIndexPart2
##- "TensorIndexType" : Help:#TensorIndexType
##- "TensorType" : Help:#TensorType
##- "TransformationType" : Help:#TransformationType
##- "VectorType" : Help:#VectorType
##- "VerticalCoframeLabels" : Help:#VerticalCoframeLabels
##- "Weight" : Help:#Weight
##- "AssignTransformationType" : Help:DifferentialGeometry/JetCalculus/AssignTransformationType
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tools" : Help:DifferentialGeometry/Tools
##- "JetCalculus" : Help:DifferentialGeometry/JetCalculus
##- "LieAlgebras" : Help:DifferentialGeometry/LieAlgebras
