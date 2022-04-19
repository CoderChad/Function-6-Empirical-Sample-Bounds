# Function-6-Empirical-Sample-Bounds



a) Take in 2 input arguments, in this order: 1) A variable that represents the dataset/distribution/sample. 2) The probability
mass bounds that define the center of the distribution (e.g. 95, 99 or 50) – in contrast to the tails.


b) The function should compute the upper bound (where the right tail starts) and the lower bound (where the left tail starts)


c) The function should return the values computed in b), either as two variables, or one variable with two elements.


d) Assumptions: The first input argument can be anything – a list, dataframe or numpy array containing real numbered values,
but you can assume it to be a 1D numpy array with arbitrary length, by default. The second input argument should be a real
number from 0.01 to 99.99 that determines the location of the bounds (where the tails start).


e) Make sure the function has a clear header as to what inputs the function assumes, what outputs it produces and when it
was written.


import numpy as np

def empiricalSampleBounds(data,p):

    # sort the data in ascending order 
    ascend=np.sort(data)

    # length of the array 
    N=len(ascend)

    # one percentile corresponds with this many datapoints, unrounded
    onep=N/100

    # probability mass in each tail
    tail=(100-p)/2

    # each tail should contain this many datapoints
    N_tail=int(tail*onep)
    
    # lower bound 
    lb=ascend[N_tail-1]

    # upper bound
    ub=ascend[-(N_tail+1)]
    
    return lb,ub

# dataset one
file='sampleInput1.csv'

# this is the first input, the data
data=np.genfromtxt(file,delimiter=" ")

# this is the second input, the probability mass bounds
# will look at a list of them to compare result
ps=[95,99,50]

for p in ps:
    lb,ub=empiricalSampleBounds(data,p)
    print(p,lb,ub)

# dataset two
file='sampleInput2.csv'

# this is the first input, the data
data=np.genfromtxt(file,delimiter=" ")

# this is the second input, the probability mass bounds
# will look at a list of them to compare result
ps=[95,99,50]

for p in ps:
    lb,ub=empiricalSampleBounds(data,p)
    print(p,lb,ub)
