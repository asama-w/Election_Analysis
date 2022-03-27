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

## Election Audit Python Script
Using python coding, the analysis of over hundreds thousands of data collected can be automatically carried out and the requested results are automatically output in a text file without the need of manually scrolling through data on excel and manually typing the output results.

To execute the analysis of the dataset in python, there are command lines that set the path to load the data and the path to save the result data. This process gives flexibility to the analysis as the path to the file can be changed to the meet the dataset you would like to analyze.

In this project,
- The **raw dataset** which wil be analyzed is in `election_results.csv` in `Resources` folder
- The **text file** which will save the analyzed results is `election_results.txt` in `analysis` folder
- The full version of **python script** is in `PyPoll_Challenge.py`

### The examples of the codes used in this python script
- Create the paths to load and save files
```python
import csv
import os

# Add a variable to load a file from a path.
file_to_load = os.path.join("Resources", "election_results.csv")
# Add a variable to save the file to a path.
file_to_save = os.path.join("analysis", "election_results.txt")
```
- To read the csv file and analyze it;

```python
total_votes = 0

with open(file_to_load) as election_data:
    reader = csv.reader(election_data)
    
    header = next(reader)

    # For each row in the CSV file.
    for row in reader:
        # Add to the total vote count
        total_votes = total_votes + 1
```

- To output the results in VSCode terminal and save the results to the text file;

```python
with open(file_to_save, "w") as txt_file:
  largest_county_turnout = (
        f"-------------------------\n"
        f"Largest County Turnover: {largest_county_candidate}\n"
        f"-------------------------\n"
    )
    # Print the output in VSCode terminal
    print(largest_county_turnout)

    # 8: Save the county with the largest turnout to a text file.
    txt_file.write(largest_county_turnout)
```
## Election Audit Results
By executing the final code in `PyPoll_Challange.py`, the similar results output is printed on terminal and saved in a text file, as shown in the following screenshots.

### Command Output (in VSCode Terminal)

![command_output](https://github.com/asama-w/Election_Analysis/blob/main/Additional%20Images/VSCode_Terminal_output.png)

### Text File Output (in election_results.txt)

![textfile_output](https://github.com/asama-w/Election_Analysis/blob/main/Additional%20Images/Text_file_output.png)

### Election Outcomes
1. Total Number of Votes: **369,711 votes**

2. There are total of 3 counties in this election: 
    
    The county name, total votes count, and percentage of total votes, are shown in the following table in a descending order.
    |No.|County|Total Votes|Percentage of Total Votes|Note|
    |:----:|:----:|:----:|:----:|:----:|
    |1.|Denver|306,055 |82.8% |Largest number of votes|
    |2.|Jefferson|38,855|10.5%| - |
    |3.|Arapahoe|24,801 | 6.7%| - | 
    
3. There are total of 3 candidates in this election: 

    The candidate name, total votes count, and percentage of total votes, are shown in the following table in a descending order.
    |No.|Candidate|Total Votes|Percentage of Total Votes|Note|
    |:----:|:----:|:----:|:----:|:----:|
    |1.|Diana DeGette|272,892 |73.8% |Winner|
    |2.|Charles Casper Stockham|85,213|23.0%| - |
    |3.|Raymon Anthony Doane|11,606 | 3.1%| - | 
    
4. The **winner of this election** based on popular vote is **Diana DeGette**.
    |Candidate|Total Votes|Percentage of Total Votes|Note|
    |:----:|:----:|:----:|:----:|
    |Diana DeGette|272,892 |73.8% |Winner|

## Election Audit Summary
