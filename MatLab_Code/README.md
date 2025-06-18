# Part 3: Testing the Effects of Potassium Concentration on Action Potential Curves

## Abstract
The goal of this study was to use the Connor-Stevens model to investigate the influences of extracellular potassium concentration on action potentials. The investigation was initially motivated by a curiosity to understand the effects of drugs that block potassium channels. The purpose was to gain a better understanding of potassium's role in the action potential of a neuron so that more complex conductance based models can be used to study these drugs. This study uses the Nernst equation to calculate seven different potassium reversal potentials based on a given vector of various extracellular potassium concentrations. We found that a more negative potassium reversal potential led to a failure in generating action potentials. However, increasing the extracellular potassium current increases the number of spikes produced by the action potential. 

## Question
What impact does the elevation of extracellular potassium ion concentration have on the shape of the action potential curve in the Connor-Stevens model?

##Setting up the Parameters
The parameters were taken from table 4.3 of Introductory Course in Computational Neuroscience textbook. The conductances for the neuron were slightly modified to change the units from μS to nS. Leak conductance nS, maximal sodium conductance = 12000 nS, maximal potassium conductance = 2000 nS and maximal A conductance nS. The reversal potentials for sodium and the leak channels were also set up as they are constant in the experiment. The sodium reversal potential,  = 55 mV and the leak reversal potential = -17 mV. Finally membrance capacitance is pF. 

## Setting up Time Vector
Various max time values were studied in the controled experiment to determine the best fit. Eventually, tmax was defined to be 150 ms as it ensures that the system has enough time to respond to changes in the potassium reversal potential without overcrowding the graph. Thus, a vector of time was created from 0 ms to 150 ms with a dt = 0.01 ms. 

## Setting up Dynamic Variables
The model uses differential equations to solve various variabels. Vectors for the membrane voltage, , applied current, , and the gating variabels are allocated to the same size as time. The membrane voltage is initialized to be the same as the leak conductance. The applied current is changed to 900 pA when time > 50 ms or time < 100 ms. The gating variables are initialized later in the for loop. 

## Finding E_k and E_A

Notice how the reversal potentials for the  and  channels were not initialized. This is a result of our dynamic extracellular potassium ion concentration, . Its vector  was created from 6 mM to 12 mM with a concentration step, dK, of 1 mM and a typical external concentration of 6 mM. These values were specifically chosen after a careful review of the  Nernst potential in the Introductory Course in Computational Neurosceince textbook as well the journal article entitled Extracellular Potassium Homeostasis: Insights from Hypokalemic Periodic Paralysis that defines a normal potassium concentration range. The internal concentration of potassium was set to the constant 150 mM. 
The Nersnt equation was used to find  where . It uses the boltzman constant , the charge of electrons , temperature  as well as the charge of a potassium ion  C. 
Additionally, the potassium concentration also affects the reversal potential of the A channel. Due to limited studies and formulas on the differences between the potassium and A channels, an assumption was made after evaulating several implementations of the model that the difference between their reversal potentials is minimal. As a result,  was found by subtracting a value of 2 from each corresponding  in the vector. 

Allocate  to be a zeros vector with the same size as . It stores the voltage at the peak of the action potential in each trial. This variable is later used in a graph against the various  values. 

## Creating the for Loops

Create a nested for loop with the outer for loop running through the different values of  and  while the inner for loop running through the time vector. 
The voltage dependent formulas used are from An Introductory Course in Computational Neuroscience textbook. However, they were slightly modified to account for the changes in the conductance parameters as well as time.  

## Conclusion
  As the concentration of the extracellular potassium increases, the potassium reversal potential becomes more positive. The rate of the potassium channel current is influenced by the driving force, denoted as  in the formula. As the reversal potential becomes more positive, the difference between the reversal potential and the membrane voltage becomes greater. Thus, the driving force increases the overall current of the potassium channel, which drives more potassium ions to leave the neuron during the repolarization phase. 
    Note that the first four trials don't produce action potential spikes. In these trials, is more negative than its typical value of -72 mV. There is a reduced driving force, thus more potassium ions remain in the neuron. The outward current of potassium is not signficant enough to repolarize the ion. This results in the neuron failing to produce an action potential and the membrane voltage is driven closer to the reversal potential of the leak channels as there are no other strong influences that drive the voltage. 
    The sharp increase seen in the third graph can be attributed to the potassium channels reaching a reversal potential that is equal to or greater than its typical value of -72 mV. As mentioned previously, increasing  increases the driving force of the potassium current. Since more potassium ions are flowing outward, the action potential is able to more rapidly repolarize, thus returning the membrane potential to its resting state faster. The membrane potential also approaches the sodium reversal potential. However, it appears to plateau before reaching -55 mV which may be due to the interplay between the various ion currents. 

