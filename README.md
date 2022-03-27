# Analysis of the Election Audit
## Election Audit Overview
### Purpose of the analysis
The purpose of this project is to utilize Python to automate the analysis of a large dataset, in order to help Tom who is an employee of the Colorado Board of Elections, audit the election results and generate a vote count report for the US congressional district election.

The given tasks for the python script to be executed in the vote count report includes;
1. Total number of votes cast
2. A complete list of candidates who received votes
3. Total number of votes each candidate received
4. Percentage of votes each candidate won
5. The winner of the election based on popular vote

### Election Data Resources
The to-be-analyzed election results are stored in a csv file named `election_results.csv`, which has over 300,000 inputs. There are 3 categories of data collected: Ballot ID, County, and Candidate name. 

The screenshot of the data outline when opens in excel is shown in the following.

![data_outline](https://github.com/asama-w/Election_Analysis/blob/main/Additional%20Images/Data_cvs_example.png)

## Election Audit Results
By using python coding, the analysis of over hundreds thousands of data collected can be automatically carried out and the requested results are automatically output in a text file without the need of manually scrolling through data on excel and manually typing the output results.

To execute the analysis of the dataset in python, there are command lines that set the path to load the data, and path to save the result data. This process gives flexibility to the analysis as the path to the file can be changed to the meet the dataset you would like to analyze.

In this project,
- The raw dataset which wil be analyzed is in `election_results.csv` in `Resources` folder
- The analyzed results that will be saved as a text file is in `election_results.txt` in `analysis` folder
- The full version of python script is in `PyPoll_Challenge.py`

The example of the codes that create the paths to these files are shown below;

```python
import csv
import os

# Add a variable to load a file from a path.
file_to_load = os.path.join("Resources", "election_results.csv")
# Add a variable to save the file to a path.
file_to_save = os.path.join("analysis", "election_results.txt")
```


### Command Output (in VSCode Terminal)
![command_output](https://github.com/asama-w/Election_Analysis/blob/main/Additional%20Images/VSCode_Terminal_output.png)

### Text File Output
![textfile_output](https://github.com/asama-w/Election_Analysis/blob/main/Additional%20Images/Text_file_output.png)

## Election Audit Summary
