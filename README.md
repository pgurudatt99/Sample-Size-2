# Sample-Size-2
Calculating minimum required Sample size for testing difference of two means and proportions
#Calculation of Sample Size to test the difference between two population means
#Objective: Testing null hypothesis: M1=M2

import math
import numpy as np
from scipy import stats 
import pandas as pd

def calculate_sample_size(pooled_std_dev, confidence_level, margin_of_error):
    numerator = 2*((z_score_alpha + z_score_bita)*pooled_std_dev)**2
    denominator = (margin_of_error)**2
    sample_size = numerator/denominator   
    return math.ceil(sample_size)
z_score_alpha = 1.96
z_score_bita = 0.84
confidence_level = 0.95
n1=float(input('Number in first group: '))
n2=float(input('Number in second group: '))
SD1=float(input ('Enter SD for first group: '))
SD2=float(input('Enter SD for second group: '))
pooled_std_dev = (((n1-1)*SD1**2+(n2-1)*SD2**2)/(n1+n2-2))**0.5
margin_of_error = float(input ('Enter Margin of Error: ')) # use value less than or equal to difference of two means m1-m2
sample_size = calculate_sample_size(pooled_std_dev, confidence_level, margin_of_error)
print(f"Pooled SD: {pooled_std_dev}")
print(f"Sample size: {sample_size}")
Output:-
Number in first group: 100
Number in second group: 150
Enter SD for first group: 2
Enter SD for second group: 3
Enter Margin of Error: 1
Pooled SD: 2.6465132265047373
Sample size: 110
................................................................................................................................................
#Calculation of Sample Size to test the difference between two population proportions
#Objective: Testing null hypothesis: P1=P2

import math
import numpy as np
from scipy import stats 
import pandas as pd

def calculate_sample_size(proportion, margin_of_error):
    numerator = (p1*(100-p1)+p2*(100-p2))*((z_score_alpha + z_score_bita)**2)
    denominator = (margin_of_error)**2
    sample_size = numerator/denominator   
    return math.ceil(sample_size)
z_score_alpha = 1.96
z_score_bita = 0.84
confidence_level = 0.95
p1=float(input('Proportion in first group: '))
p2=float(input('Proportion in second group: '))
proportion=abs((p1+p2)/2)
margin_of_error = float(input ('Enter Margin of Error: ')) # use value less than or equal to difference of two means p1-p2
sample_size = calculate_sample_size(proportion, margin_of_error)
print(f"Sample size: {sample_size}")
Output:-
Proportion in first group: 50
Proportion in second group: 60
Enter Margin of Error: 10
Sample size: 385
