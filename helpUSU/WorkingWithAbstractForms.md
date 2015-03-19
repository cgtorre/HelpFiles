##PROCEDURE(helpmw,test,nospec,nodoti,postprocess="helpmw_execute") DifferentialGeometry/WorkingWithAbstractForms
##TITLE Working with abstract differential forms
##DESCRIPTION
##-  This worksheet provides additional information for working with abstract differential forms, that is, differential forms which are defined abstractly without reference to any underlying system of coordinates. 
## This new functionality of DifferentialGeometry is intended to supercede the "difforms "package.
##- There are 2 different ways of using DifferentialGeometry to calculate with abstract differential forms.  
## The first way mirrors the scenerio current provided by difforms -- one defines a list of forms (using "DGsetup") by simply specifying their degrees. 
## Then one can calculate wedge products and exterior derivatives of these forms. Equations for exterior derivatives can be specified.
## For the second method one indicates which of the 1-forms being defined constitute a co-frame for the underlying manifold.  
## In this setting, the vector fields dual to the given 1-forms are automatically created by DGsetup.  Wedge products, interior products, exterior derivatives and Lie derivatives can all be computed.
##-  The functionalities provided by "DGzip", "GetComponents", "Annihilator", "DGbasis" and "DGinfo" are available as appropriate.
##EXAMPLES     
##>(show=false) Typesetting:-State() := "extended":
##> with(DifferentialGeometry): with(Tools):
##-(nolead) 
##-(nolead) **Example 1.**
##-(nolead) Create an abstract manifold __mrow(mi("M",italic = "true",mathvariant = "italic"))__ with a function 
## __mrow(mi("f",italic = "true",mathvariant = "italic"),mo(",",fence = "false",separator = "true",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.3333333em"), mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"))__1-forms __mrow(msub(mi("&#945;",italic = "false"),mi(""),subscriptshift = "0"),mo(",",fence = "false",separator = "true",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.3333333em"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),msub(mi("&#946;",italic = "false"),mi(""),subscriptshift = "0"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"))__ 
## and a 2-form __mrow(msub(mi("&#963;",italic = "false"),mi(""),subscriptshift = "0"))__.
##> DGsetup('[f = dgform(0) , alpha = dgform(1), beta = dgform(1), sigma = dgform(2)]', [], M); 
##-(nolead) The command "DGinfo" gives the names all scalars and forms which are defined.  
##> DGinfo("AbstractForms"); 
##-(nolead) Scalar products, wedge products and sums of abstract forms can be defined. 
##> omega := evalDG(2*alpha &wedge beta + 4*sigma); 
##-(nolead) The command "DGinfo" can also be used to extract information about the form __mrow(msub(mi("&#969;",italic = "false"),mi(""),subscriptshift = "0"))__.
##> DGinfo(omega, "CoefficientSet");
##> DGinfo(omega , "CoefficientList", [sigma]);  
##-(nolead) New forms can be defined on M. 
##> DGinfo("AbstractForms"); 
##-(nolead) We can use the "DGzip" and "GetComponents" commands with abstract forms. 
##> Omega := evalDG([alpha &w beta, sigma]); 
##> zeta := DGzip([3, 5], Omega, "plus");
##> GetComponents(zeta, Omega);  
##-(nolead) We can take the "exterior derivative" of a form. 
##> rho:= ExteriorDerivative(alpha);  
##-(nolead) The 2-form dalpha has been added to list of defined forms and is now available for subsequent computations. 
##> DGinfo("AbstractForms");
##> ExteriorDerivative(rho);  
##-(nolead) Exterior derivatives of defined forms can be specified. 
##> DGsetup(M, [], [d(f) = f*alpha, d(beta) = 4*sigma + 5*alpha &wedge beta]);
##> ExteriorDerivative(f*beta);
##-(nolead) 
##- **Example 2.**
##-(nolead) In this example we illustrate calculations using the second calling sequence for working with abstract forms. 
## The 1-forms defining the co-frame are enclosed in separate list (the degrees of the forms defining the co-frame need not be given).
##> RemoveFrame(M);
##> DGsetup([f=dgform(0), g= dgform(0), [omega1, omega2, omega3], 'alpha' = dgform(2), 'beta' = dgform(3)], [d(omega1) = omega2 &w omega3], N);  
##-(nolead) All the functionality of **Example 1 ** is retained but now the manifold __mrow(mi("N",italic = "true",mathvariant = "italic"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"))__ is taken to have dimension 3. The 1-forms __mrow(mfenced(mrow(msub(mi("&#969;",italic = "false"),mrow(mn("1"),italic = "true",mathvariant = "italic"),subscriptshift = "0"),mo(",",fence = "false",separator = "true",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.3333333em"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),msub(mi("&#969;",italic = "false"),mrow(mn("2"),italic = "true",mathvariant = "italic"),subscriptshift = "0"),mo(",",fence = "false",separator = "true",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.3333333em"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),msub(mi("&#969;",italic = "false"),mrow(mn("3"),italic = "true",mathvariant = "italic"),subscriptshift = "0")),open = "{",close = "}"))__ 
## define a co-frame on __mrow(mi("N",italic = "true",mathvariant = "italic"),mo(" ",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"))__ 
## and the dual vector fields {__mrow(mi("D_",italic = "true",font_style_name = "Text",mathvariant = "italic"),mo("&InvisibleTimes;",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),msub(mi("&#969;",italic = "false",font_style_name = "Text"),mrow(mn("1",font_style_name = "Text"),italic = "true",font_style_name = "Text",mathvariant = "italic"),subscriptshift = "0"),mo(",",font_style_name = "Text",fence = "false",separator = "true",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.3333333em"),mi("D_",italic = "true",font_style_name = "Text",mathvariant = "italic"),mo(" ",font_style_name = "Text",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),msub(mi("&#969;",italic = "false",font_style_name = "Text"),mrow(mn("2",font_style_name = "Text"),italic = "true",font_style_name = "Text",mathvariant = "italic"),subscriptshift = "0"),mo(",",font_style_name = "Text",fence = "false",separator = "true",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.3333333em"),mi("D_",italic = "true",font_style_name = "Text",mathvariant = "italic"),mo(" ",font_style_name = "Text",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),msub(mi("&#969;",italic = "false",font_style_name = "Text"),mrow(mn("3",font_style_name = "Text"),italic = "true",font_style_name = "Text",mathvariant = "italic"),subscriptshift = "0"),mo("}",font_style_name = "Text",fence = "true",separator = "false",stretchy = "true",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.1666667em",rspace = "0.1111111em"),foreground = "[0,0,255]",font_style_name = "2D Output")__
## have been initialized.   
##> DGinfo("AbstractForms");
##> DGinfo("FrameBaseVectors");
##> DGinfo("FrameBaseForms");
##-(nolead) We can define vector fields on __mrow(mi("N",italic = "true",mathvariant = "italic"))__.
##> X := evalDG( a*D_omega1 + b*D_omega2 + c*D_omega3);
##-(nolead) We can calculate the "interior products" of vectors and forms.
##> Hook(X, omega1 &w omega3); 
##-(nolead) The interior products of {__mrow(mi("D_",italic = "true",font_style_name = "Text",mathvariant = "italic"),mo("&InvisibleTimes;",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),msub(mi("&#969;",italic = "false",font_style_name = "Text"),mrow(mn("1",font_style_name = "Text"),italic = "true",font_style_name = "Text",mathvariant = "italic"),subscriptshift = "0"),mo(",",font_style_name = "Text",fence = "false",separator = "true",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.3333333em"),mi("D_",italic = "true",font_style_name = "Text",mathvariant = "italic"),mo(" ",font_style_name = "Text",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),msub(mi("&#969;",italic = "false",font_style_name = "Text"),mrow(mn("2",font_style_name = "Text"),italic = "true",font_style_name = "Text",mathvariant = "italic"),subscriptshift = "0"),mo(",",font_style_name = "Text",fence = "false",separator = "true",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.3333333em"),mi("D_",italic = "true",font_style_name = "Text",mathvariant = "italic"),mo(" ",font_style_name = "Text",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"),msub(mi("&#969;",italic = "false",font_style_name = "Text"),mrow(mn("3",font_style_name = "Text"),italic = "true",font_style_name = "Text",mathvariant = "italic"),subscriptshift = "0"),mi(""),foreground = "[0,0,255]",font_style_name = "2D Output")__} with the 2-form alpha are automatically defined as new forms on __mrow(mi("N",italic = "true",mathvariant = "italic"),mo(".",fence = "false",separator = "false",stretchy = "false",symmetric = "false",largeop = "false",movablelimits = "false",accent = "false",lspace = "0.0em",rspace = "0.0em"))__ 
##> Hook(D_omega1, beta);
##> Hook(D_omega2, beta);
##> Hook(D_omega3, beta);
##> DGinfo("AbstractForms");
##> Hook(X, alpha); 
##-(nolead) Iterated interior products are known to be skew-symmetric: 
##> Hook(D_omega1, i_1beta); 
##> Hook(D_omega1, i_2beta); 
##> Hook(D_omega3, i_2beta);
##-(nolead) The forms are taken to be independent so the commands such as "Annihilator "and "DGbasis" will work in this setting.
##> Annihilator([D_omega1 + D_omega3]); 
##-(nolead) The "Lie derivative" of forms are computed from the Cartan formula.
##> LieDerivative(D_omega2, beta); 
##-(nolead) Here both terms in this equation are new forms which are added to the list of defined forms on __mrow(mi("N",italic = "true",mathvariant = "italic"))__.
##> DGinfo("AbstractForms");
##-(nolead) Equations for both exterior derivatives and interior products can be specified.
##> DGsetup(N, [] , [d(omega3) = 0, d(beta) = alpha &w alpha, hook(D_omega2, beta) = alpha]); 
##> LieDerivative(D_omega2, beta); 
##-(nolead) The "Lie bracket" can also be computed.
##> LieBracket(D_omega2, D_omega3);
##> DGsetup(N, [q = dgform(0)], [hook([D_omega2, D_omega3],domega2) = q]); 
##> LieBracket(D_omega2, D_omega3);
##SEEALSO
##- "DifferentialGeometry", "Annihilator", "DGbasis", "DGinfo", "DGsetup", "ExteriorDerivative", "Hook", "LieBracket", "LieDerivative"
##XREFMAP
##- "difforms " : Help:difforms
##- "DGsetup" : Help:DifferentialGeometry:-DGsetup
##- "DGzip" : Help:DifferentialGeometry:-DGzip
##- "GetComponents" : Help:DifferentialGeometry:-GetComponents
##- "Annihilator" : Help:DifferentialGeometry:-Annihilator
##- "DGbasis" : Help:DifferentialGeometry:-DGbasis
##- "DGinfo" : Help:DifferentialGeometry:-DGinfo
##- "DGinfo" : Help:DifferentialGeometry:-DGinfo
##- "DGzip" : Help:DifferentialGeometry:-DGzip
##- "GetComponents" : Help:DifferentialGeometry:-GetComponents
##- "exterior derivative" : Help:DifferentialGeometry:-ExteriorDerivative
##- "interior products" : Help:DifferentialGeometry:-Hook
##- "Annihilator " : Help:DifferentialGeometry:-Annihilator
##- "DGbasis" : Help:DifferentialGeometry:-DGbasis
##- "Lie derivative" : Help:DifferentialGeometry:-LieDerivative
##- "Lie brackets" : Help:DifferentialGeometry:-LieBrackets
##- "DifferentialGeometry" : Help:DifferentialGeometry
##- "Annihilator" : Help:DifferentialGeometry:-Annihilator
##- "DGbasis" : Help:DifferentialGeometry:-DGbasis
##- "DGinfo" : Help:DifferentialGeometry:-DGinfo
##- "DGsetup" : Help:DifferentialGeometry:-DGsetup
##- "ExteriorDerivative" : Help:DifferentialGeometry:-ExteriorDerivative
##- "Hook" : Help:DifferentialGeometry:-Hook
##- "LieBracket" : Help:DifferentialGeometry:-LieBracket
##- "LieDerivative" : Help:DifferentialGeometry:-LieDerivative
