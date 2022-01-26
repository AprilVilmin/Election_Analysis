# Electing with Python: Analysis of Python Code Written for Colorodo Board of Elections


## Overview of Election Audit
Company XYZ has been hired to aid Tom in creating a Python script to help audit of a Colorado congressional district. Company XYZ has been tasked with writing code for many metrics in Python including, but not limited to: counting the number of votes, the percentage of votes for each candidate, the number of votes for each candidate, and the winner, the county with the most votes, the number of votes per county and the percentage of votes per county. We originally looked at cadidate metrics, but Tom's manager liked that data so much, he know wants us to look at county metrics. This has been done in Excel in the past, but Tom's manager wants to look at doing it automatically in the future. If this is successful it will be used in our districts and other types of elections in the future.


## Election Audit Results

Using Python Tom and Company XYZ were able to give concise answers to the following questions:
- How many votes were cast in this congressional election? 369,711
 To get this we first initalize a total vote counter (total_votes = 0) and then add to the total vote count (total_votes = total_votes + 1) and lastly we use the following code  to print the code to terminal or text file:
 
 ### Print the final vote count (to terminal)
    election_results = (
        f"\nElection Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n\n"
        f"County Votes:\n")
    print(election_results, end="")

    txt_file.write(election_results)


- Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.
 Jefferson: 10.5% (38,855), Denver: 82.8% (306,055), Arapahoe: 6.7% (24,801)
 
 
      for county_name in county_votes_dictionary
        #### 6b: Retrieve the county vote count.
        votes = county_votes_dictionary.get(county_name)
        #### 6c: Calculate the percentage of votes for the county.
        vote_percentage = float(votes) / float(total_votes) * 100
        county_results = (
        f"{county_name}: {vote_percentage:.1f}% ({votes:,})\n")
        
        #### 6d: Print the county results to the terminal.
        print(county_results)
        #### 6e: Save the county votes to a text file.
        txt_file.write(county_results)
        
- Which county had the largest number of votes? Denver
  To get this we begin by tracking the lagest_county (largest_county = "") and largest_county_voter_turnout (largest_county_voter_turnout = 0), we then write an if statement for this and then print it to the terminal and text file. Below is a snippet of code contining the if statement:
  
  #### 6f: Write an if statement to determine the winning county and get its vote count.
        if (votes > largest_county_voter_turnout):
            largest_county_voter_turnout = votes
            largest_county = county_name

- Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.
  Charles Casper Stockham: 23.0% (85,213), Diana DeGette: 73.8% (272,892), Raymon Anthony Doane: 3.1% (11,606)
  
  To get this you need to first create a list (candidate_options = []) and a dictionary (candidate_votes = {}, then track the winning_candidate (winning_candidate = ""), winning_count (winning_count = 0), and winning_percentage (winning_percentage = 0), then get the candidate_name from each row (candidate_name = row[2]), if the candidate is not already in the list add it using the following logic:

        # If the candidate does not match any existing candidate add it to
        # the candidate list
        if candidate_name not in candidate_options:

            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)

            # And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0

        # Add a vote to that candidate's count
        candidate_votes[candidate_name] += 1
        
   Then we need to get the vote count by candidate and the percentage by candidate and then print to the terminal and prtint to the text file.
   
   # Save the final candidate vote count to the text file.
    for candidate_name in candidate_votes:

        # Retrieve vote count and percentage
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        # Print each candidate's voter count and percentage to the
        # terminal.
        print(candidate_results)
        #  Save the candidate results to our text file.
        txt_file.write(candidate_results)
        
- Which candidate won the election, what was their vote count, and what was their percentage of the total votes?
  Winner: Diana DeGette, Winning Vote Count: 272,892, Winning Percentage: 73.8%
  
  Below is a screenshot of the results when the Python code is ran to the Terminal.
  
  
  
  ![Module 3 Results Screenshot](https://github.com/AprilVilmin/Election_Analysis/blob/main/Module%203%20Results%20Screenshot.png)


## Election Audit Summary

In a summary statement, provide a business proposal to the election commission on how this script can be used—with some modifications—for any election. Give at least two examples of how this script can be modified to be used for other elections.




### Challenges and Difficulties Encountered
Being new to Python, one of the biggest issues that myself and others at company XYZ faced was troubleshooting issues found. It was nice when the code editor would tell you what line the error was on, but sometimes the error would be caused by something on another line. There were other times when the issue wouldn't throw an error, but it was obvious that one was there when you compared it to the exepected results on the challenge.
d

