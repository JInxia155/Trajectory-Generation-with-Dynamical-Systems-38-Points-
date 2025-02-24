Download Link : https://programming.engineering/product/trajectory-generation-with-dynamical-systems-38-points/

# Trajectory-Generation-with-Dynamical-Systems-38-Points-
Trajectory Generation with Dynamical Systems [38 Points]
Name, Surname, ID Number

Problem 4.1 Trajectory Generation with Dynamical Systems [38 Points]

In this exercise we will use the Dynamic Motor Primitives (DMPs), described by the following dynamical system,

                        ¨y =
                        	

                        2 ( ( (g y) ( ˙y= )) + fw (z)) ,
                        	

                        (1)

                        z˙ =
                        	

                        z z,
                        	

                        (2)

where y is the state of the system, ˙y and ¨y are the first and second time derivatives, respectively. The attractor’s goal is denoted by g and the forcing function by fw. The parameters and control the spring-damper system. The phase variable is denoted by z and the temporal scaling coeﬃcient by . The forcing function fw is given by

fw (z) =
	

P
	

K
	

i (z) wi z
	

= (z)
	

T
	

w,
	

with i (z) =
	

z z
	

,
	

(3)

Kj
		

0 j (z)
	

Kj 1 j (z)
		

i=0
						

i ( )
		
	

P =
						

P =
			

where the basis functions i (z) are Gaussian basis given by
	

ci )2 =hi ,
				
				

i (z) = exp
	

0.5 (z
				

(4)

where the centers c are equally distributed in the phase z, and the width h is an open parameter. For the programming exercises a basic environment of a double link pendulum is provided, as well as the computation of the i (z).

    Similarities to a PD controller [2 Points]

Transform Equation (1) to have a similar structure to a PD-controller,

                        ¨yz = KP yzd es yz + KD ˙yzd es ˙yz + uf f
                        	

                        (5)

and write down how the following quantities Kp, Kd , yd es and ˙yd es look like in terms of the DMP parameters. z z

Name, Surname, ID Number

    Stability [2 Points]

Explain why the DMPs are stable when t ! 1 and what would the equilibrium point be.

    Double Pendulum – Training [12 Points]

Implement the DMPs and test them on the double pendulum environment. In order to train the DMPs you

have to solve Equation (1) on the forcing function. Before starting the execution, set the goal g position to be the same as in the demonstration. Then, set the parameters to = 25, = 6.25, z = 3=T, = 1. Use N = 50 basis functions, equally distributed in z. Use the learned DMPs to control the robot and plot in the same figure both the demonstrated trajectory and the reproduction from the DMPs. You need to implement the DMP-based controller (dmpCtl.py) and the training function for the controller parameters (dmpTrain.py). To plot your results you can use dmpComparison.py. Refer to example.py to see how to call it.

Name, Surname, ID Number

    Double Pendulum – Conditioning on the Final Position [3 Points]

Using the trained DMPs from the previous question, simulate the system with diﬀerent goal positions: first with qt=end = f0, 0.2g and then with qt=end = f0.8, 0.5g. Generate one figure per DoF. In each figure, plot the demonstrated trajectory and the reproduced trajectories with diﬀerent goal positions. How do you interpret the result?

    Double Pendulum – Temporal Modulation [3 Points]

Using the trained DMPs from the previous question, simulate the system with diﬀerent temporal scaling factors = f0.5, 1.5g. Generate one figure per DoF and explain the result.

Name, Surname, ID Number

f) Probabilistic Movement Primitives – Radial Basis Function [3 Points]

We now want to use ProMPs. Before we train them, we need to define some basis functions. We decide to use N = 30 radial basis functions (RBFs) with centers uniformly distributed in the time interval [0 2b, T + 2b], where T is the end time of the demonstrations. The bandwidth of the Gaussian basis (std) is set to b = 0.2. Implement these basis functions in getProMPBasis.py. Do not forget to normalize the basis such at every time-point they sum-up to one! Attach a plot showing the basis functions in time.

    Probabilistic Movement Primitives – Training [7 Points]

In this exercise you will train the ProMPs using the imitation learning data from getImitationData.py and the RBFs defined in the previous question. Modify the proMP.py in order to estimate weight vectors wi reproducing the diﬀerent demonstrations. Then, fit a Gaussian using all the weight vectors. Generate a plot showing the desired trajectory distribution in time (mean and std) as well as the trajectories used for imitation.

Name, Surname, ID Number

    Probabilistic Movement Primitives – Number of Basis Functions [2 Points]

Evaluate the eﬀects of using a reduced number of RBFs. Generate two plots showing the desired trajectory distribution and the trajectories used for imitation as in the previous exercise, but this time use N = 20 and N = 10 basis functions. Briefly analyze your results.

i) Probabilistic Movement Primitives – Conditioning [4 Points]

Using Gaussian conditioning calculate the new distribution over the weight vectors wi such as the trajectory has a via point at position y = 3 at time tcond = 1150 with variance y = 0.0002. Use again 30 basis functions.

Assuming that the probability over the weights is given by N wj w, w and the probability of being to that

position is given by N y j w, y , show how the new distribution over w is computed (how does the mean and variance look like)?

Then, in a single plot, show the previous distribution (learned from imitation) and the new distribution (after conditioning). Additionally, sample K = 10 random weight vectors from the ProMP, compute the trajectories and plot them in the same plot. Analyze briefly your results.

5
