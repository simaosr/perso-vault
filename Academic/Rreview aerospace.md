The authors present a work on the 

The manuscript is reasonbly written, but clear in general. 
Although the optimization is used as a proof of concept for the CNN model that is presented, it has some flaws that should be addressed, either by fundamenting the choice of the optimization problem or by making some changes to it. 

Chapter 2
The benefits of the choice of using CNN to predict the aerodynamic coefficients of the airfoils is not clear to me. What are the benefits of using the image vs using the coordinates directly? It introduces at least on extra step (converting the airfoils to images)

Chapter 3
Line 229 -  It is mentioned that CNN requires a lot data for the training process. How much is a lot?  Can you provide a quantification for this affirmation?



Chapter 5

- In the description of the NSGA-II algorithm, the term domination is mentioned but not explained. A simple description of what the term means would make the manuscript more clear. Also, a reference for the NSGA-II should be added.
- The choice of minimizing the lift coefficient is not clearly fundamented in the manuscript. Why not try to maximize it? 
- In the pareto front presented in the manuscript there seems to be no trade-off, one would choose the airfoil with highest lift and lowest Cd/Cl.