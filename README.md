# Predict-the-FIFA-World-Cup-Winner
In soccer, teams are given FIFA Ratings, which are numerical values representing each team’s relative skill level. Higher FIFA ratings indicate better previous game results, and given two teams’ FIFA ratings, it’s possible to estimate the probability that either team wins a game based on their current ratings. The FIFA Ratings from just before the two previous World Cups are available as the May 2018 Men’s FIFA Ratings and March 2019 Women’s FIFA Ratings.  Using this information, we can simulate the entire tournament by repeatedly simulating rounds until we’re left with just one team. And if we want to estimate how likely it is that any given team wins the tournament, we might simulate the tournament many times (e.g. 1000 simulations) and count how many times each team wins a simulated tournament.</br>


# Testing
Your program should behave per the examples below. Since simulations have randomness within each, your output will likely not perfectly match the examples below.</br>

### $ python tournament.py 2018m.csv</br>
* Belgium: 20.9% chance of winning</br>
* Brazil: 20.3% chance of winning</br>
* Portugal: 14.5% chance of winning</br>
* Spain: 13.6% chance of winning</br>
* Switzerland: 10.5% chance of winning</br>
* Argentina: 6.5% chance of winning</br>
* England: 3.7% chance of winning</br>
* France: 3.3% chance of winning</br>
* Denmark: 2.2% chance of winning</br>
Croatia: 2.0% chance of winning</br>
* Colombia: 1.8% chance of winning</br>
* Sweden: 0.5% chance of winning</br>
* Uruguay: 0.1% chance of winning</br>
* Mexico: 0.1% chance of winning</br>
* $ python tournament.py 2019w.csv</br>
* Germany: 17.1% chance of winning</br>
* United States: 14.8% chance of winning</br>
* England: 14.0% chance of winning</br>
* France: 9.2% chance of winning</br>
* Canada: 8.5% chance of winning</br>
* Japan: 7.1% chance of winning</br>
* Australia: 6.8% chance of winning</br>
* Netherlands: 5.4% chance of winning</br>
* Sweden: 3.9% chance of winning</br>
* Italy: 3.0% chance of winning</br>
* Norway: 2.9% chance of winning</br>
* Brazil: 2.9% chance of winning</br>
* Spain: 2.2% chance of winning</br>
* China PR: 2.1% chance of winning</br>
* Nigeria: 0.1% chance of winning</br>
You might be wondering what actually happened at the 2018 and 2019 World Cups! For Men’s, France won, defeating Croatia in the final. Belgium defeated England for the third place position. For Women’s, the United States won, defeating the Netherlands in the final. England defeated Sweden for the third place position.</br>



# Understanding
Start by taking a look at the 2018m.csv file. This file contains the 16 teams in the knockout round of the 2018 Men’s World Cup and the ratings for each team. Notice that the CSV file has two columns, one called team (representing the team’s country name) and one called rating (representing the team’s rating).</br>

The order in which the teams are listed determines which teams will play each other in each round (in the first round, for example, Uruguay will play Portugal and France will play Argentina; in the next round, the winner of the Uruguay-Portugal match will play the winner of the France-Argentina match). So be sure not to edit the order in which teams appear in this file!</br>

Ultimately, in Python, we can represent each team as a dictionary that contains two values: the team name and the rating. Uruguay, for example, we would want to represent in Python as {"team": "Uruguay", "rating": 976}.</br>

Next, take a look at 2019w.csv, which contains data formatted the same way for the 2019 Women’s World Cup.</br>

Now, open tournament.py and see that we’ve already written some code for you. The variable N at the top represents how many World Cup simulations to run: in this case, 1000.</br>

The simulate_game function accepts two teams as inputs (recall that each team is a dictionary containing the team name and the team’s rating), and simulates a game between them. If the first team wins, the function returns True; otherwise, the function returns False.</br>

The simulate_round function accepts a list of teams (in a variable called teams) as input, and simulates games between each pair of teams. The function then returns a list of all of the teams that won the round.</br>

In the main function, notice that we first ensure that len(sys.argv) (the number of command-line arguments) is 2. We’ll use command-line arguments to tell Python which team CSV file to use to run the tournament simulation. We’ve then defined a list called teams (which will eventually be a list of teams) and a dictionary called counts (which will associate team names with the number of times that team won a simulated tournament). Right now they’re both empty, so populating them is left up to you!</br>

Finally, at the end of main, we sort the teams in descending order of how many times they won simulations (according to counts) and print the estimated probability that each team wins the World Cup.</br>

Populating teams and counts and writing the simulate_tournament function are left up to you!</br>

# Implementation Details
Complete the implementation of tournament.py, such that it simulates a number of tournaments and outputs each team’s probability of winning.</br>

First, in main, read the team data from the CSV file into your program’s memory, and add each team to the list teams.</br>

The file to use will be provided as a command-line argument. You can access the name of the file, then, with sys.argv[1].</br>
Recall that you can open a file with open(filename), where filename is a variable storing the name of the file.</br>
Once you have a file f, you can use csv.DictReader(f) to give you a “reader”: an object in Python that you can loop over to read the file one row at a time, treating each row as a dictionary.</br>
By default, all values read from the file will be strings. So be sure to first convert the team’s rating to an int (you can use the int function in Python to do this).</br>
Ultimately, append each team’s dictionary to teams. The function call teams.append(x) will append x to the list teams.</br>
Recall that each team should be a dictionary with a team name and a rating.</br>
Next, implement the simulate_tournament function. This function should accept as input a list of teams and should repeatedly simulate rounds until you’re left with one team. The function should then return the name of that team.</br>

You can call the simulate_round function, which simulates a single round, accepting a list of teams as input and returning a list of all of the winners.
Recall that if x is a list, you can use len(x) to determine the length of the list.</br>
You should not assume the number of teams in the tournament, but you may assume it will be a power of 2.</br>
Finally, back in the main function, run N tournament simulations, and keep track of how many times each team wins in the counts dictionary.</br>

For example, if Uruguay won 2 tournaments and Portugal won 3 tournaments, then your counts dictionary should be {"Uruguay": 2, "Portugal": 3}.</br>
You should use your simulate_tournament to simulate each tournament and determine the winner.</br>
Recall that if counts is a dictionary, then syntax like counts[team_name] = x will associate the key stored in team_name with the value stored in x.</br>
You can use the in keyword in Python to check if a dictionary has a particular key already. For example, if "Portugal" in counts: will check to see if "Portugal" already has an existing value in the counts dictionary.</br>
