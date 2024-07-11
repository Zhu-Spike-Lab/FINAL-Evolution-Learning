# Evolutionary Algorithms For Task Learning
contains 3 different evolution engines for task learning in RSNNs model for sine wave, robot arm, and moving digit task  
all engines are run using the standard rssn_env environment described in slack + download of the seaborn module for plotting

### Engine Code Breakdown
Each engine jupyter notebook follows the same template:
##### Dataset
Loads in the dataset for the specified task.
##### Building Connectivity and Neurons
Creates the specified connections from the input to recurrent, recurrent to recurrent, and recurrent to output layers. LIF neurons are generated with modifiable threshold and refractory period
##### Defining the Network
The RSNN is constructed using the connectivity and neurons as constructed above. 3 inhibitory neuron classes and the network size corresponding to the task will be specified here (if applicable). A custom loss function is defined.
##### Evolution
A genetic encoding and decoding function converts a model to a genetic representation by concatenating all of the parameters into a numpy array and decodes the gene back into the model format by reshaping the gene to the original parameter sizes.

The main evolution class runs the evolutionary process through the evolve function. It first generates an initial population of models, evaluates each model for 1 batch,
selects the 2 best models with the best fitness (lowest loss), and populates the next generation by uniquely crossing over and mutating the parent genes for each child. This process of reproduction is completed for the specified number of generations. The best performing model throughout evolution is saved as well as the initial and final populations. Evolution can be modified by changing the number of models in the initial population, the number of generations, the number of offspring models per generation, and the genetic mutation rate. 
##### Plotting
Each engine will contain different plotting functions relevant to the task as well as a heatmap and line plot to view the changes in weights of the different layers in the model. The robot and sine (3 inh neuron) engines contain plotting functions for violin plots that require loading in a trained backprop model for comparison. 

### Sine Wave Task
two separate engines have been built for the sine wave task, one implementing 3 inhibitory neuron classes and one with one inhibitory neuron class  
both of these engines are run using data loaded from the CSV file contained within the folder, default experiment is L1: explicit time   resetting with period can be changed out by using a different CSV file and updating the dataloader  

### Robot Arm Task
contains one engine which will evolve the model to learn the robot trajectories  
engine generated models have 3 inhibitory neuron classes  
data is loaded from generated trajectories from robot_trajectories.py  
contains some plotting functions that require a backprop-trained model for comparison, an example model path has been saved in results folder

### Digit Drift Task
note: engine currently does not implement models with LIF refractory period neurons and does not have 3 inhibitory neuron classes  
engine generates models to classify the direction of a moving digit  
directions.ipynb generates the frame sequences of the moving digit and saves them to movement_sequences.csv  
can be modified to support frames of different sizes  

### Results 
contains results ran on local machine for the robot arm task  
if model training method is not specified, it has been trained with EA  
