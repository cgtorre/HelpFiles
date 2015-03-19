##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/OverviewOfGeneralRelativity
##TITLE An Overview of General Relativity computations with DifferentialGeometry 
 
##DESCRIPTION
##- The GR-Tensor package, developed by K. Lake, P. Musgrave and D. Polleny, has long provided the general relativity community with an excellent collection of command for symbolic computations in general relativity. This functionality is also now available within "DifferentialGeometry" package and with the DifferentialGeometry subpackage "Tensor". 
##- This worksheet provides a quick introduction to General Relativity computations using "DifferentialGeometry". 
#  
##SECTION 1. Getting Started
##-(nolead) In this section we give a quick illustration of the use of the 'DifferentialGeometry' software to perform a standard calculation in General Relativity. 
## We shall solve the Einstein vaccum equations for spherically symmetric metrics in 4-dimensions. 
## We check that the solution is of Petrov type D and we show that there are 4 Killing vectors.  
## First load the DifferentialGeometry package, the Tensor subpackage and the Tools subpackage. 
##> with(DifferentialGeometry): with(Tensor): with(Tools):
##>(show=false) Typesetting:-State() := "extended": 
##-(nolead) All calculations in DifferentialGeometry begin by using the "DGsetup" command to initialize the computational environment. 
## For our illustration we shall use standard spherical coordinates We use the name __mi("M1")__ to designate the computational environment (in this case a 4-dimensional manifold) which we are creating. 
##> DGsetup([t, r, theta, phi], M1, verbose);  
##-(nolead) The coordinate vectors and the 1-forms are now defined and these can be used to construct general vector fields, differential forms and tensors. 
## Use +/- for addition and substraction, \* for scalar multiplication, &t for tensor product and &w for wedge product. 
## The command "evalDG" is used to insure that these operations are properly performed in 'DifferentialGeometry'. 
##-(nolead)  
##-(nolead) Here is the usual form for the static (time-independent), rotational invariant metric that is used as the starting ansatz for solving the Einstein equations. 
## The two functions __mrow(mi("A",italic = "true",mathvariant = "italic"),mfenced(mrow(mi("r",italic = "true",mathvariant = "italic"))))__ and __mrow(mi("B",italic = "true",mathvariant = "italic"),mfenced(mrow(mi("r",italic = "true",mathvariant = "italic"))))__ will be determined by the Einstein equations 
##> g := evalDG( A(r) *dt &t dt + B(r)* dr &t dr + r^2*(dtheta &t dtheta + sin(theta)^2* dphi &t dphi));   
##-(nolead) To solve the Einstein equations for this metric, we first calculate the "Einstein tensor". 
##> Ein := EinsteinTensor(g);    
##-(nolead) The command "DGinfo" is a utility program that can be used to obtain information about the computational environment and information about various 
## 'DifferentialGeometry' objects.
## Here we use "DGinfo"to extract all the coefficients of the Einstein tensor.  
##> EinEq := DGinfo(Ein, "CoefficientSet");   
##-(nolead) Now we use the Maple command "pdsolve" to integrate these differential equations: 
##> Soln := pdsolve(EinEq);   
##-(nolead) The constant '_C1' is essentially the mass of the point source of the gravitional field. The constant '_C2' is easily normalized to -1 by a re-scaling of time. 
##> gS := subs({_C1 = - 2*m, _C2= -1},subs(Soln, g));  
##-(nolead) This is the Schwarzschild metric in standard coordinates. The Einstein tensor vanishes as required. 
##> EinsteinTensor(gS); 
##-(nolead)  
##-(nolead) The metric admits 4 "Killing vectors".  
##> K := KillingVectors(gS); 
##> subs({sqrt(1-cos(2*theta)) = sqrt(2)*sin(theta)}, K); 
##-(nolead) The "Petrov" type of this metric is \"D\".
##> PetrovType(gS);   
##-(nolead) It is often convenient to store the entries of a metric in a symmetric matrix. 
##> convert(convert(gS, DGArray), Matrix); 
##-(nolead)  
##SECTION 2. Algebraic Manipulations of Tensors 
##-(nolead) We use a simple metric defined on a 3-dimensional space to illustrate some basis algebraic manipulations with tensors.
##-(nolead)
##-(nolead) First define a coordinate chart with coordinates 
##> DGsetup([x, y, z], M2); 
##-(nolead) Define a metric __mrow(mi("g",italic = "true",mathvariant = "italic"))__. 
##> g2 := evalDG(z*(dx&t dy + dy &t dx) + x^2*dz &t dz);   
##-(nolead) Calculate the "inverse metric " 
##> h := InverseMetric(g2);  
##-(nolead) Define a rank 3 tensor. 
##> T := evalDG(dx &t D_y &t dz); 
##-(nolead) "Lower" the second index of T. 
##> RaiseLowerIndices(g2, T, [2]); 
##-(nolead) "Raise" the 1st and 3rd indices of T using the inverse metric __mrow(mi("h",italic = "true",mathvariant = "italic"))__.  
##> RaiseLowerIndices(h, T, [1,3]);   
##-(nolead) "Rearrange" the 1st and 2nd indices. 
##> RearrangeIndices(T, [[1,2]]);   
##-(nolead) "Symmmetrize" over the 1st and 3rd indices 
##> SymmetrizeIndices(T, [1, 3], "Symmetric"); 
##SECTION 3. Derivatives
##-(nolead) One can compute the "exterior derivative" of a differential form, the "Lie derivative" of any tensor field with respect to a vector field or the "covariant derivative" of any tensor field with respect to a "connection" 
##> DGsetup([x, y, z], N);  
##-(nolead) Define a 1-form and calculate the exterior derivative. 
##> omega := evalDG(sin(x) *dy + x^2*dz); 
##> ExteriorDerivative(omega);   
##-(nolead) Define a vector field __mrow(mi("X",italic = "true",mathvariant = "italic"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"))__ 
## and a tensor __mrow(mi("T",italic = "true",mathvariant = "italic"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"))__ and calculate the Lie derivative. 
##> X := evalDG(y*D_x + x*D_z); 
##> T := evalDG(x^2*D_y &t dz); 
##> LieDerivative(X, T);   
##-(nolead) Define a connection and calculate the covariant derivative of __mrow(mi("T",italic = "true",mathvariant = "italic"),mo(".",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"))__ 
##> C := Connection(a*D_z &t dx &t dy); 
##> CovariantDerivative(T, C); 
##SECTION 4. Useful Utilities 
##-(nolead) The 'DifferentialGeometry' package has many useful utilites for working with differential forms and tensors.  
## For example, we can easily construct a general metric as follows. ("GenerateSymmetricTensors", "DGzip") 
##> DGsetup([x, y, z], N); 
##> S := GenerateSymmetricTensors([dx, dy , dz], 2); 
##> g := DGzip([a1,a2,a3,a4,a5,a6](x, y, z), S, "plus"); 
##-(nolead) As another example, we can get the components of any tensor with respect to any basis with the command "GetComponents". 
##> B := evalDG([dx , dx -dy, dx +2*dy -dz]); 
##> alpha := evalDG(dx - 3*dy + 5*dz); 
##> GetComponents(alpha, B); 
##-(nolead)  
##SECTION 5. Curvature Tensors
##-(nolead) The "Riemann curvature tensor", the "Ricci tensor", the "Ricci scalar" and the "Weyl tensor" of a metric are easily computed. Here we use the Godel metric. 
##> DGsetup([x, y, z, t], M5);   
##-(nolead) To define the metric, we first define a 1-form and then define the metric in terms of the 1-form. 
##> omega := evalDG(dt + exp(x)*dz); 
##> g5 := evalDG(dx &t dx + dy &t dy +1/2*exp(2*x)*dz &t dz - omega &t omega); 
##-(nolead) Here is the curvature tensor (as a type (1, 3)) tensor. 
##> CurvatureTensor(g5); 
##-(nolead) Here is the Ricci tensor. 
##> RicciTensor(g5); 
##-(nolead) Here is the Ricci scalar. 
##> RicciScalar(g5); 
##-(nolead)  
##SECTION 6. Working with Orthonormal Tetrads
##-(nolead) Many calculations in General Relativity can be dramatically simplified by defining an orthonormal tetrad and by expressing the metric 
## and all other tensors in terms of this orthonormal tetrad. This is particularly true when a co-frame can be chosen with simple structure equations. 
##-(nolead) A simple illustration of this is provided by the Godel metric from the previous example. 
##> DGsetup([x, y, z, t], M6); 
##> omega := evalDG(dt + exp(x)*dz); 
##> g6 := evalDG(dx &t dx + dy &t dy +1/2*exp(2*x)*dz &t dz - omega &t omega); 
##> Omega := evalDG([dx, dy, 1/sqrt(2)*exp(x)*dz, omega]);  
##-(nolead) We use "TensorInnerProduct "to check that the forms in the list define an orthonormal tetrad. 
##> TensorInnerProduct(g6, Omega, Omega);  
##-(nolead) The command "FrameData" calculates the structure equations for this frame and stores the results in a format that can be used by DGsetup. 
##> FD := FrameData(Omega, O6); 
##-(nolead) What is nice about this co-frame is that the structure functions are all constant -- even though there was an exponetial function in the metric.   
## We run "DGsetup" again to create a new computational environment which used this co-frame and these structure equations. 
##> DGsetup(FD, [E], [theta]); 
##> newg6 := evalDG(theta1 &t theta1 + theta2 &t theta2 + theta3 &t theta3 - theta4 &t theta4);  
##-(nolead) The curvature tensor and the Ricci tensor take simple forms in terms of this frame. 
##> CurvatureTensor(newg6);
##> RicciTensor(newg6); 
##-(nolead)  
##SECTION 7. Working with Null Tetrads and the Newman-Penrose Formalism
##-(nolead) The 'DifferentialGeometry' package supported computations in all the different formalisms for general relativity -- 
## coordinate calculations, orthonormal tetrads, null tetrads and the Newman-Penrose formalism, and the two-component spinor formalism. 
## The tools are readily available for moving from one formalism to another.   
##-(nolead) 
##-(nolead) In this example we calculate the Newman-Penrose curvature scalars for a metric. 
##> DGsetup([r, u, x, y], M7); 
##> g7 := evalDG(dr &t du + du &t dr -((2*(3*x*r+m))*du &t du)/r-(1/4)*(r^2*dx &t dx)/x^3-(1/4)*(r^2*dy &t dy)/x^3);   
##-(nolead) The command "DGGramSchmidt" and "NullTetrad" provide useful tools for constructing null tetrads. Here is the one that we shall use for this example 
##> NT := evalDG([D_r, (3*x*r+m)*D_r/r+D_u, I*sqrt(2)*x^(3/2)*D_x/r+sqrt(2)*x^(3/2)*D_y/r, -I*sqrt(2)*x^(3/2)*D_x/r+sqrt(2)*x^(3/2)*D_y/r]);   
##-(nolead) Here are the Newman-Penrose "curvature scalars" for this null tetrad. 
##> NP := NPCurvatureScalars(NT, output = ["WeylScalars"]);   
##SECTION 8. Two Component Spinor Formalism
##-(nolead) As a quick illustration of the 2-component spinor formalism, we calculate the Weyl spinor for the metric from the previous paragraph. 
## To work with spinors we use "DGsetup" to specify both the coordinates for the space-time and also the coordinates to be used for the spinors and their complex conjugates.  
##> DGsetup([r, u, x, y], [z1, z2, w1, w2], M8);  
##-(nolead) Here is metric as before.  
##> g8 := evalDG(dr &t du + du &t dr -((2*(3*x*r+m))*du &t du)/r-(1/4)*(r^2*dx &t dx)/x^3-(1/4)*(r^2*dy &t dy)/x^3);  
##-(nolead) Here is the null tetrad as before. 
##> NT := evalDG([D_r, (3*x*r+m)*D_r/r+D_u, I*sqrt(2)*x^(3/2)*D_x/r+sqrt(2)*x^(3/2)*D_y/r, -I*sqrt(2)*x^(3/2)*D_x/r+sqrt(2)*x^(3/2)*D_y/r]);   
##-(nolead) We use the null tetrad to construction an orthonormal tetrad. 
##> OT := OrthonormalTetrad(NT);   
##-(nolead) We use the orthonormal tetrad to define the "solder form" as a spin-tensor __mrow(msubsup(mi("&#963;",italic = "false"),mrow(mi("a",italic = "true",mathvariant = "italic"),italic = "true",mathvariant = "italic"),mrow(mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),mi("AX",italic = "true",mathvariant = "italic"),mo("'",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.1111111em",rspace = "0.0em"),italic = "true",mathvariant = "italic"),superscriptshift = "0",subscriptshift = "0",msemantics = "[none,none]"))__. 
##> sigma := SolderForm(OT);  
##-(nolead) Here is the null vector as a 2-component spinor. 
##> convert(D_r, DGspinor, sigma, [1]); 
##-(nolead) We use "SpinorInnerProduct" to check that the contracted product re-produces the metric. 
##> SpinorInnerProduct(sigma, sigma);   
##-(nolead) Here is the "Weyl spinor".  
##> WeylSpinor(sigma);   
##-(nolead) 
##SECTION 9. Congruences
##-(nolead) "Line congruences" (especially null congruences) play an important role in the geometric analysis of space-times. 
## We continue with the metric from the previous example. We show that the congruence defined by D_ris defines a shear-free "principal null direction". 
##> U := D_r; 
##> V := evalDG((3*x*r+m)*D_r/r+D_u); 
##> W := WeylTensor(g8): 
##> GRQuery(U, g8, W, "PrincipalNullDirection");   
##-(nolead) Here are the properties of the null congruence defined by __mrow(mi("U",italic = "true",mathvariant = "italic"))__. 
##> CongruenceProperties(g8, U, V); 
##SECTION 10. Electro-Vac Spacetimes
##-(nolead) A space-time is called an electro-vac space-time if there exists an electromagneic field which solves the Einstein-Maxwell field equations. 
## The problem of deciding if a space-time is electro-vac can be solved using the command "RainichConditions" and "RainichElectromagneticField". Here is a simple example. 
##> DGsetup([t, x, y, z], M10); 
##> g10 := evalDG(4/3*t^2* dx &t dx + t*(exp(-2*x)* dy &t dy + exp(2*x)*dz &t dz) - dt &t dt);   
##-(nolead) Test to see if the Rainich conditions for a spacetime hold. 
##> RainichConditions(g10);   
##-(nolead) We conclude the space-time is an electro-vac spacetime. Here is the electro-magnetic field. 
##> F := RainichElectromagneticField(g10); 
##> F := simplify(F) assuming t > 0;  
##-(nolead) We check that the Einstein equations are satisfied (See "EinsteinTensor", "EnergyMomentumTensor"). 
##> T := EnergyMomentumTensor("Electromagnetic", g10, F); E := EinsteinTensor(g10); E &minus T;  
##-(nolead) We check that the Maxwell equations (see "MatterFieldEquations") are satisfied. 
##> MatterFieldEquations("Electromagnetic", g10, F);   
##-(nolead)  
##SECTION 11. Exact Solution DataBase
##-(nolead) An data-base of exact solutions of the Einstein equations can be accessed using either the "Browse" and or the "MetricSearch" commands from the 'DifferentialGeometry' 
## "Library" sub-package.  
##-(nolead)  
##SECTION 12. Other Features
##- Transformation between space-times can be constructed. See "Transformation", "Pullback," "Pushforward" 
##- The "Segre" classification of space-time can be calculated. 
##- The "KillingVector" and "PetrovType" commands support case-splitting for metrics which depend upon arbitrary parameters or functions. 
##- "Killing tensors", "Killing-Yano tensors", "Killing spinors" and "recurrent tensors" can all be calculated.  
##- The "LieAlgebras" package provides all the tools needed for a complete algebraic analysis of the Killing vectors of a space-time. 
##- The "isotropy subalgebra "and "isotropy type" of a Lie algebra of Killing vectors can be determined. These are useful properties for classificating Killing vectors. 
##- Invariant metrics for any Lie algebra of vector fields can be easily computed using the command "InvariantGeometricObjectFields" in the "GroupActions" package. 
##- Residual diffeomorphism groups for reductions of space-times can be calculated with the command "InfinitisimalPseudoGroupNormalizer" 
##- Futur releases of 'DifferentialGeometry' will include commands for working with the Einstein-Yang-Mills equations and for abstractly solving the Einstein equations 
## on homogeneous spaces and low cohomogeneity manifolds.  
##SEEALSO
##- "Physics[D_]"
##- "Physics[Christoffel]"
##- "Physics[Einstein]"
##- "Physics[Ricci]"
##- "Physics[Riemann]"
##- "Physics[Weyl]"
##XREFMAP
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Tensor" : Help:DifferentialGeometry/Tensor
##- "DGsetup" : Help:DifferentialGeometry/DGsetup
##- "evalDG" : Help:DifferentialGeometry/evalDG
##- "Einstein tensor" : Help:DifferentialGeometry/Tensor/EinsteinTensor
##- "DGinfo" : Help:DifferentialGeometry/Tools/DGinfo
##- "pdsolve " : Help:pdsolve
##- "Killing vectors" : Help:DifferentialGeometry/Tensor/KillingVectors
##- "Petrov" : Help:DifferentialGeometry/Tensor/Petrov
##- "inverse metric " : Help:DifferentialGeometry/Tensor/InverseMetric
##- "Lower" : Help:DifferentialGeometry/Tensor/RaiseLowerIndices
##- "Raise" : Help:DifferentialGeometry/Tensor/RaiseLowerIndices
##- "Rearrange" : Help:DifferentialGeometry/Tensor/RearrangeIndices
##- "Symmmetrize" : Help:DifferentialGeometry/Tensor/SymmetrizeIndices
##- "exterior derivative" : Help:DifferentialGeometry/ExteriorDerivative
##- "Lie derivative" : Help:DifferentialGeometry/LieDerivative
##- "covariant derivative" : Help:DifferentialGeometry/Tensor/CovariantDerivative
##- "connection" : Help:DifferentialGeometry/Tensor/Connection
##- "GenerateSymmetricTensors" : Help:DifferentialGeometry/Tensor/GenerateSymmetricTensors
##- "DGzip" : Help:DifferentialGeometry/DGzip
##- "GetComponents" : Help:DifferentialGeometry/Tensor/GetComponents
##- "Riemann curvature tensor" : Help:DifferentialGeometry/Tensor/CurvatureTensor
##- "Ricci tensor" : Help:DifferentialGeometry/Tensor/RicciTensor
##- "Ricci scalar" : Help:DifferentialGeometry/Tensor/RicciScalar
##- "Weyl tensor" : Help:DifferentialGeometry/Tensor/WeylTensor
##- "TensorInnerProduct " : Help:DifferentialGeometry/Tensor/TensorInnerProduct
##- "FrameData" : Help:DifferentialGeometry/FrameData
##- "DGGramSchmidt" : Help:DifferentialGeometry/Tensor/DGGramSchmidt
##- "NullTetrad" : Help:DifferentialGeometry/Tensor/NullTetrad
##- "curvature scalars" : Help:DifferentialGeometry/Tensor/NPCurvatureScalars
##- "solder form" : Help:DifferentialGeometry/Tensor/SolderForm
##- "SpinorInnerProduct" : Help:DifferentialGeometry/Tensor/SpinorInnerProduct
##- "Weyl spinor" : Help:DifferentialGeometry/Tensor/WeylSpinor
##- "Line congruences" : Help:DifferentialGeometry/Tensor/LineCongruences
##- "principal null direction" : Help:DifferentialGeometry/Tensor/PrincipalNullDirection
##- "RainichConditions" : Help:DifferentialGeometry/Tensor/RainichConditions
##- "RainichElectromagneticField" : Help:DifferentialGeometry/Tensor/RainichElectromagneticField
##- "EinsteinTensor" : Help:DifferentialGeometry/Tensor/EinsteinTensor
##- "EnergyMomentumTensor" : Help:DifferentialGeometry/Tensor/EnergyMomentumTensor
##- "MatterFieldEquations" : Help:DifferentialGeometry/Tensor/MatterFieldEquations
##- "Browse" : Help:DifferentialGeometry/Library/Browse
##- "MetricSearch" : Help:DifferentialGeometry/Library/MetricSearch
##- "Library" : Help:DifferentialGeometry/Library
##- "Transformation" : Help:DifferentialGeometry/Transformation
##- "Pullback," : Help:DifferentialGeometry/Pullback
##- "Pushforward" : Help:DifferentialGeometry/Pushforward
##- "Segre" : Help:DifferentialGeometry/Tensor/SegreType
##- "KillingVector" : Help:DifferentialGeometry/Tensor/KillingVectors
##- "PetrovType" : Help:DifferentialGeometry/Tensor/PetrovType
##- "Killing tensors" : Help:DifferentialGeometry/Tensor/KillingTensor
##- "Killing-Yano tensors" : Help:DifferentialGeometry/Tensor/KillingYano
##- "Killing spinors" : Help:DifferentialGeometry/Tensor/KillingSpinors
##- "recurrent tensors" : Help:DifferentialGeometry/Tensor/RecurrentTensor
##- "LieAlgebras" : Help:DifferentialGeometry/LieAlgebras
##- "isotropy subalgebra " : Help:DifferentialGeometry/GroupActions/IsotropySubalgebra
##- "isotropy type" : Help:DifferentialGeometry/Tensor/IsotropyType
##- "InvariantGeometricObjectFields" : Help:DifferentialGeometry/GroupActions/InvariantGeometricObjectFields
##- "GroupActions" : Help:DifferentialGeometry/GroupActions
##- "InfinitisimalPseudoGroupNormalizer" : Help:DifferentialGeometry/GroupActions/InfinitesimalPseudoGroupNormalizer
