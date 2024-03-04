import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Open the first file in read mode, the full path of the file must be used ensuring \ is replaced with \\ and remove “ at the start and end of the path
targetA = "C:\\Users\\abdul\\OneDrive\\Desktop\\Computer Science\\Problem 1 Coursework\\targetA.csv"

# Open the second file in read mode, the full path of the file must be used ensuring \ is replaced with \\ and remove “ at the start and end of the path
targetB ="C:\\Users\\abdul\\OneDrive\\Desktop\\Computer Science\\Problem 1 Coursework\\targetB.csv"

# Combine the contents of both files
combined_content = targetA + targetB

# Open a new file in write mode to save the combined files
with open('combined_file.txt', 'w') as combined_file:
    # Write the combined content to the new file in .txt format for python
    combined_file.write(combined_content)

# The combined data are in the combined_file.txt file
print("name of file: ", combined_file.name)

# This is to check whether the file is closed or not
print("closed or not: ", combined_file.closed)
