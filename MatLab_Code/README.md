#Part 3: Testing the Effects of Potassium Concentration on Action Potential Curves

##Abstract
The goal of this study was to use the Connor-Stevens model to investigate the influences of extracellular potassium concentration on action potentials. The investigation was initially motivated by a curiosity to understand the effects of drugs that block potassium channels. The purpose was to gain a better understanding of potassium's role in the action potential of a neuron so that more complex conductance based models can be used to study these drugs. This study uses the Nernst equation to calculate seven different potassium reversal potentials based on a given vector of various extracellular potassium concentrations. We found that a more negative potassium reversal potential led to a failure in generating action potentials. However, increasing the extracellular potassium current increases the number of spikes produced by the action potential. 

##Question
What impact does the elevation of extracellular potassium ion concentration have on the shape of the action potential curve in the Connor-Stevens model?

##Setting up the Parameters
The parameters were taken from table 4.3 of Introductory Course in Computational Neuroscience textbook. The conductances for the neuron were slightly modified to change the units from μS to nS. Leak conductance nS, maximal sodium conductance = 12000 nS, maximal potassium conductance = 2000 nS and maximal A conductance nS. The reversal potentials for sodium and the leak channels were also set up as they are constant in the experiment. The sodium reversal potential,  = 55 mV and the leak reversal potential = -17 mV. Finally membrance capacitance is pF. 
