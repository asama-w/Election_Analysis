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

The following shows the screenshot of the dataset outline when opens in excel.

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
- Read the csv file and analyze it;

```python
total_votes = 0
# Create a county list and county votes dictionary.
county_options = []
county_votes = {}

with open(file_to_load) as election_data:
    reader = csv.reader(election_data)
    
    header = next(reader)

    # For each row in the CSV file.
    for row in reader:
        # Add to the total vote count
        total_votes = total_votes + 1
```
- Get county list and the total vote of each county;

```python
        # Get the candidate name from each row.
        candidate_name = row[2]
        # 3: Extract the county name from each row.
        county_name = row[1]
        if county_name not in county_options:

            # 4b: Add the existing county to the list of counties.
            county_options.append(county_name)

            # 4c: Begin tracking the county's vote count.
            county_votes[county_name] = 0

        # 5: Add a vote to that county's vote count.
        county_votes[county_name] += 1
```
- Output the results in VSCode terminal and save the results to the text file;

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
- Calculate the percentage of the total vote

```python
    for candidate_name in candidate_votes:
        # Retrieve vote count and percentage
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
```

## Election Audit Results
By executing the final code in `PyPoll_Challenge.py`, the similar results output is printed on terminal and saved in a text file, as shown in the following screenshots.

### Command Output (in VSCode Terminal)

![command_output](https://github.com/asama-w/Election_Analysis/blob/main/Additional%20Images/VSCode_Terminal_output.png)

### Text File Output (in election_results.txt)

![textfile_output](https://github.com/asama-w/Election_Analysis/blob/main/Additional%20Images/Text_file_output.png)

### Election Outcomes Summary
1. **Total Number of Votes:** 369,711 votes

2. **County List:** There are total of 3 counties in this election: 
    
    The county name, total votes count, and percentage of total votes, are shown in the following table in a descending order.
    |No.|County|Total Votes|Percentage of Total Votes|Note|
    |:----:|:----:|:----:|:----:|:----:|
    |1.|Denver|306,055 |82.8% |Largest number of votes|
    |2.|Jefferson|38,855|10.5%| - |
    |3.|Arapahoe|24,801 | 6.7%| - | 
    
3. **Candidate List:** There are total of 3 candidates in this election: 

    The candidate name, total votes count, and percentage of total votes, are shown in the following table in a descending order.
    |No.|Candidate|Total Votes|Percentage of Total Votes|Note|
    |:----:|:----:|:----:|:----:|:----:|
    |1.|Diana DeGette|272,892 |73.8% |Winner|
    |2.|Charles Casper Stockham|85,213|23.0%| - |
    |3.|Raymon Anthony Doane|11,606 | 3.1%| - | 
    
4. **The Winner of This Election** based on popular vote is **Diana DeGette**.
    |Winner Candidate|Total Votes|Percentage of Total Votes|Note|
    |:----:|:----:|:----:|:----:|
    |Diana DeGette|272,892|73.8% |Winner|

## Election Audit Summary
From the unknown number of candidates, counties, total votes by looking at the raw dataset to the straight-forward summary output of the election results generated from the Python script, we can tell that in this congressional election, there are total votes of 369,711 votes. Among the 3 candidates, Dianna DeGette came as number 1 and won the election by 73.8% of the total votes (272,892 votes), and  among the 3 counties, Denver county has the largest vote turnover, as high as 82.8% of the total votes (306,055 votes).

The analysis of this election results is done through the execution of different commands in Python. By writing the code and let the programme do the work as per command, the analysis of gigantic dataset becomes easier and the human-error can also be reduced. Instead of reading through each line for more than 300,000 lines in excel and eye-determining number of candidates or counties that is present in this election results, writing commands in python and let the programme extract the demand outputs (i.e. candidate list, county list, total number of vote for each of the items) within one script is a more refined method and a user-friendly way for debugging if errors were to occur. Additionally, the summary of the result, which is output in a separate text file and can be formatted to suit the style of the readers, is simpler and more readable for the ease of analysis.

This python script application does not only limit to this election analysis, but can also be modified and apply to other analysis, such as a major election with higher number of ballots, county, and candidates. As the dataset gets larger, there are more rows and columns of inputs, it is difficult and time-consuming to manually go through each line of the data and subtract the information from it, thus, modifying the Python codes is important.

By editing the file path in this command line to other desired csv file, this Python script can be used with other dataset, as long as the ballot ID, the county, and the candidate names are stored respectively in the similar column index order, the script will still run through all the rows of the dataset, collect the data in the selected column index, store it in the list and dictionary, and output it as instructed in the code.
For example, to analyze `federal_election_results.csv`, put the file in `Resources` folder and change the path name to federal_election_results.csv

```python
# 1. Using this code to analyze different dataset
#change this
file_to_load = os.path.join("Resources", "election_results.csv")
#to this
file_to_load = os.path.join("Resources", "federal_election_results.csv")
```
Another modification example that can be done is to check whether there are repeated Ballot ID stored in the dataset or not, to audit the correctness of the election results.
For example, when determining the `total_votes`
