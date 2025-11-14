# Computing with Speculations

This repository contains the example Python code (v. 3.11) of the paper entitled *Computing with Speculations*.

The example code uses a random inferential Brownian ordinary reasoning to compute an inference chain (from a hypothesis to a consequence) composed of:
- Only induction steps.
- Only abduction steps.
- A mix of induction and abduction steps.

The example is an interactive Jupyter notebook. In particular, this code has different parameters: **n_atoms**, **cut**, **max_iter**, and **mix_induction_abduction**. 
The first one defines the number of atoms to use to construct the power set. 
The second one defines the threshold in $[-1, 1]$ used to reduce the size of the power set in order to reduce the complexity.
The third one defines the number of iterations used to attempt to generate an inference chain in order to avoid infinite loops. 
The last one is a Boolean parameter that facilitates the operation of a mixed inference chain, which is comprised of both inductions and abductions. 
In particular, by disabling it, we enable chains of only inductions or only abductions.

In our algorithm, we remove the newly found element in the inference chain from the power set to avoid circular loops.

The algorithm is not deterministic and relies on pseudo-random generations, i.e., no solution can be found due to the limitations imposed on the steps (the parameter **max_iter** in this case).  

The total number of atoms, represented by lowercase letters, can be fixed before the generation is carried on; the premise **p** and the consequent **q** that is to be reached via a (possibly mixed) chain of forward and backward deductions and abductions are given in the respective fields by inserting the letters representing the atoms. Each time a parameter is modified, a new chain is produced and displayed.

In order to reduce the complexity, we constructed a **pair_compatibility** dictionary that randomly assigns a value in $[-1, 1]$ to every pair of possible atoms. 
Subsequently, the compatibility of each element of the power set is computed by summing the values of every pair of compatible elements within the power set. 
Only elements of the power set with a general compatibility greater than or equal to a certain threshold (the parameter **cut** defined above) are considered.
