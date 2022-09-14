# Stock Analysis

## Overview of Project
In this project we are working with the Colorado board of elections to do an election audit of the tabulated results for a U.S. congressional precinct in Colorado. We are working with Tom one of the employees and we have been tasked with reporting the total number of votes cast, the total number of votes for each candidate and the percentage of votes for each candidate. Lastly Tom would like us to show the winner of the election based on the popular vote.

### Purpose
The main purpose in this analysis is to determine if there is a way to automate this process using Python rather than manually doing it in Excel. We will explore some steps to do this below.

## Analysis and Challenges
We were provided a CSV file that contained header records and data records. The data records were the Ballot ID, County, and full candidate name. 

The first step was to create a way to open the csv file, read the contents and order them in a way that made sense. We used the import csv and import os functions to make the process of setting variables for input and output files easier.

Once we had set up to read in the file we created dictionaires to contain the different aspects of the data we needed to analyze. We will go over the data collected and break it down by section below.

## *Total number of votes - 369,711<br />
        We calculated the total number of votes cast in the election by initializing a counter and then using a for loop to cycle through the rows and add to the total vote count until the final result was returned.
        
![Total_Votes](/Resources/Total_Votes.png)

*Number and percentage of votes for each candidate
*Which county had the largest number of votes
*Number and percentage of votes for each county
*Winning candidate with vote count and percentage of the total votes

We created some VBA macros that allowed us to populate the Year, Total Volume and Return for DQ in 2017 and 2018. The results were surprising.




As you can see from this image, DQ did not perform well at all. Steve decided at this point that he wanted to be able to quickly compare all 12 of the stocks to determine the best performing stocks to suggest for his parent's portfolio.

In order to make the process more accessible we created a new macro assigned to a button that allowed Steve to input the year needed and returned the same data analysis for all stock tickers in the spreadsheet.

        yearValue = InputBox("What year would you like to run the analysis on?")

Then by assigning the tickers to an array we looped through all the tickers in the spreadsheet to determine the Total Volumes and Returns.

        'Assign the tickers to elements of the array
                tickers(0) = "AY"
                tickers(1) = "CSIQ"
                tickers(2) = "DQ"
                tickers(3) = "ENPH"
                tickers(4) = "FSLR"
                tickers(5) = "HASI"
                tickers(6) = "JKS"
                tickers(7) = "RUN"
                tickers(8) = "SEDG"
                tickers(9) = "SPWR"
                tickers(10) = "TERP"
                tickers(11) = "VSLR"

We encountered another challenge during this process. The runtime for the data analysis seemed to be rather slow. Steve requested a timer for us to determine the overall run time of each set of data.

        Dim startTime As Single
        Dim endTime  As Single

            startTime = Timer
            

            endTime = Timer
    
        MsgBox "This code ran in " & (endTime - startTime) & " seconds for the year " & (yearValue)

This code allowed us to display the runtime of the data analysis for each year at the end of the process.

![Pre_Refactoring_2017](/Resources/Pre_Refactoring_2017.png)
![Pre_Refactoring_2017](/Resources/Pre_Refactoring_2018.png)

As we can see from the above pictures the code did not take that long to run however the concern was as the data grew with more stocks added it could become quite cumbersome to research. We decided to refactor the code and use more arrays to expedite the analysis process. After refactoring the code by creating arrays for the outputs of tickerVolumes, tickerStartingPrices, and tickerEndingPrices as well as several other improvements to the code our runtimes were improved significantly.

![VBA_Challenge_2017](/Resources/VBA_Challenge_2017.png)
![VBA_Challenge_2018](/Resources/VBA_Challenge_2018.png)

### Analysis of Outcomes 
In the outcome tables below, we determined that the two stocks with the highest returns for 2017 and 2018 were ENPH and RUN.

![Stock_Data_2017](/Resources/Stock_Data_2017.png)
![Stock_Data_2018](/Resources/Stock_Data_2018.png)

You can see from the data that while DQ had a positive return in 2017 they fell off significantly in 2018.

### Summary

As shown in the previous examples of the pre refactored code vs refactored, there is a significant increase in the runtime of the process after refactoring. While the refactoring of code did require more research to determine the best practices, the potential outcome of increased productivity during research proved to be enough to justify the code enhancement.

The original VBA script vs the refactored code was also much bulkier than the final product of the refactored code.

