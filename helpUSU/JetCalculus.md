##PROCEDURE(help) DifferentialGeometry[JetCalculus]
##TITLE  Overview of the JetCalculus package
##DESCRIPTION
##- Jet spaces play a fundamental role in the geometric approach to the calculus of variations and to differential equations.  The `JetCalculus`
## package is a specialized package for symbolic computations on jet spaces and is fully compatible with the other packages and commands in 'DifferentialGeometry'.
##- This package contains commands for "prolonging" both vector fields and transformations to jet spaces and for calculating "Euler-Lagrange" 
## equations for variational problems with any number of independent and dependent variables and any number of derivatives.
##- Jet spaces admit a very important generalization of the de Rham complex which is called the variational bicomplex -- 
## so named because one of the differentials in the variational bicomplex  can be identified with the Euler-Lagrange operator for the 
## calculus of variations.  The JetCalculus packages provides the full functionality needed for computations within the theoretical framework 
## of the variational bicomplex, including the "horizontal" and "vertical" exterior derivative operators, the associated homotopy operators 
## and the "integration by parts" operator.
##- This package can be used in conjunction with the "PDEtools" package for the systematic analysis of symmetries of differential equations, 
## for the study of conservation laws and integrable evolution equations, for the study of invariant variational  problems, and for the inverse problem to the calculus of variations.  
## It will also be of interest to those working in the areas of integrable systems and exterior differential systems.
##- The `JetCalculus` package is a sub-package of DifferentialGeometry.  Each command in the JetCalculus package can be accessed by using either the
## long form or the short form of the command name in the command calling sequence.
##
##
##SECTION List of the JetCalculus commands
##-(nolead) The following is a list of available commands 
##TABLE(width = 625, border = 0, alignment = center, colwidth = 1|1|1)
##ROW "AssignTransformationType" | "AssignVectorType" | "DifferentialEquationData"     
##ROW "EulerLagrange" | "EvolutionaryVector" | "GeneralizedLieBracket"        
##ROW "GeneratingFunctionToContactVector" |   "HigherEulerOperators"  | "HorizontalExteriorDerivative" 
##ROW "HorizontalHomotopy" | "IntegrationByParts" | "Noether"                      
##ROW "ProjectedPullback" | "ProjectionTransformation" | "Prolong"                     
##ROW "PushforwardTotalVector" | "TotalDiff" | "TotalJacobian"                
##ROW "TotalVector" | "VerticalExteriorDerivative" |  "VerticalHomotopy"             
##ROW "ZigZag" | `` |``    
##ENDTABLE
##
##-(nolead) A brief description of the sub-package's commands is as follows
##- "AssignTransformationType": assign a type (projectable, point, contact, ...) to a transformation.
##- "AssignVectorType": assign a type (projectable, point, contact, ...) to a vector.
##- "DifferentialEquationData": create a data structure for a system of differential equations.
##- "EulerLagrange": calculate the Euler-Lagrange equations for a Lagrangian.
##- "EvolutionaryVector": find the evolutionary part of a vector field.
##- "GeneralizedLieBracket": find the Lie bracket of two generalized vector fields.
##- "GeneratingFunctionToContactVector": find the contact vector field defined by a generating function.
##- "HigherEulerOperators": apply the higher Euler operators to a function or a differential bi-form.
##- "HorizontalExteriorDerivative": calculate the horizontal exterior derivative of a bi-form on a jet space.
##- "HorizontalHomotopy": apply the horizontal homotopy operator to a bi-form on a jet space.
##- "IntegrationByParts": apply the integration by parts operator to a differential bi-form.
##- "Noether": find the conservation law for the  Euler-Lagrange equations from a given symmetry of the Lagrangian
##- "ProjectedPullback": pullback a differential bi-form of type (r, s) by a transformation to a differential bi-form of type (r, s).
##- "ProjectionTransformation": construct the canonical projection map between jet spaces of a fiber bundle.
##- "Prolong": prolong a jet space, vector field, transformation, or differential equation to a higher order jet space.
##- "PushforwardTotalVector": pushforward a total vector field by a transformation.
##- "TotalDiff": take the total derivative of an expression, a differential form or a contact form.
##- "TotalJacobian": find the Jacobian of a transformation using total derivatives.
##- "TotalVector": find the total part of a vector field.
##- "VerticalExteriorDerivative": calculate the vertical exterior derivative of a bi-form on a jet space.
##- "VerticalHomotopy": apply the vertical homotopy operator to a bi-form on a jet space.
##- "ZigZag": lift a dH-closed form on a jet space to a d-closed form.
##
##
##SEEALSO
##- "DifferentialGeometry", "GroupActions", "Library", "LieAlgebras", "Tensor", "Tools", "PDEtools"
##
##
##XREFMAP
##- "long form" : Help:UsingPackages#longform
##- "short form" : Help:UsingPackages#shortform
##- "PDEtools" : Help:PDETools
##- "prolonging" : Help:DifferentialGeometry[JetCalculus][Prolong]
##- "Euler-Lagrange" : Help:DifferentialGeometry[JetCalculus][EulerLagrange] 
##- "AssignTransformationType" : Help:DifferentialGeometry[JetCalculus][AssignTransformationType]
##- "AssignVectorType" : Help:DifferentialGeometry[JetCalculus][AssignVectorType]
##- "DifferentialEquationData" : Help:DifferentialGeometry[JetCalculus][DifferentialEquationData]
##- "EulerLagrange" : Help:DifferentialGeometry[JetCalculus][EulerLagrange]
##- "EvolutionaryVector" : Help:DifferentialGeometry[JetCalculus][EvolutionaryVector]
##- "GeneralizedLieBracket" : Help:DifferentialGeometry[JetCalculus][GeneralizedLieBracket]
##- "GeneratingFunctionToContactVector" : Help:DifferentialGeometry[JetCalculus][GeneratingFunctionToContactVector]
##- "HigherEulerOperators" : Help:DifferentialGeometry[JetCalculus][HigherEulerOperators]
##- "HorizontalExteriorDerivative" : Help:DifferentialGeometry[JetCalculus][HorizontalExteriorDerivative]
##- "HorizontalHomotopy" : Help:DifferentialGeometry[JetCalculus][HorizontalHomotopy]
##- "IntegrationByParts" : Help:DifferentialGeometry[JetCalculus][IntegrationByParts]
##- "Noether" : Help:DifferentialGeometry[JetCalculus][Noether]
##- "ProjectedPullback" : Help:DifferentialGeometry[JetCalculus][ProjectedPullback]
##- "ProjectionTransformation" : Help:DifferentialGeometry[JetCalculus][ProjectionTransformation]
##- "Prolong" : Help:DifferentialGeometry[JetCalculus][Prolong]
##- "PushforwardTotalVector" : Help:DifferentialGeometry[JetCalculus][PushforwardTotalVector]
##- "TotalDiff" : Help:DifferentialGeometry[JetCalculus][TotalDiff]
##- "TotalJacobian" : Help:DifferentialGeometry[JetCalculus][TotalJacobian]
##- "TotalVector" : Help:DifferentialGeometry[JetCalculus][TotalVector]
##- "VerticalExteriorDerivative" : Help:DifferentialGeometry[JetCalculus][VerticalExteriorDerivative]
##- "VerticalHomotopyDifferentialGeometry" : Help:DifferentialGeometry[JetCalculus][VerticalHomotopy]
##- "ZigZag" : Help:DifferentialGeometry[JetCalculus][ZigZag]


