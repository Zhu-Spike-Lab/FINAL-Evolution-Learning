# Evolutionary Algorithms For Task Learning
contains 3 different evolution engines for task learning in RSNNs model for sine wave, robot arm, and moving digit task  
all engines are run using the standard rssn_env environment described in slack + download of the seaborn module for plotting


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
