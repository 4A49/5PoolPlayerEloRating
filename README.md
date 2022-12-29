# 5PoolPlayerEloRating
Elo Rating system for a game of pool with 5 players

```
# Initialize the ratings for each player
ratings = {
    "player1": 1500,
    "player2": 1500,
    "player3": 1500,
    "player4": 1500,
    "player5": 1500
}

DEFINE function expected_score(rating, opponent_rating)
  RETURN 1 / (1 + 10 ** ((opponent_rating - rating) / 400))

DEFINE function update_ratings(winner, loser, ratings)
  SET winner_rating = ratings[winner]
  SET loser_rating = ratings[loser]
  
  # Calculate the expected scores for each player
  SET winner_expected = expected_score(winner_rating, loser_rating)
  SET loser_expected = expected_score(loser_rating, winner_rating)
  
  # Update the ratings based on the outcome of the match
  SET ratings[winner] = winner_rating + 32 * (1 - winner_expected)
  SET ratings[loser] = loser_rating + 32 * (0 - loser_expected)

# Loop through the games and update the ratings
FOR each game in games
  SET winner = game[0]
  SET loser = game[1]
  update_ratings(winner, loser, ratings)

# Print the updated ratings
PRINT ratings
```


This pseudocode defines a dictionary ratings that stores the initial ratings for each player. It then defines two functions: expected_score, which calculates the expected score for a player based on their rating and the rating of their opponent, and update_ratings, which updates the ratings of two players based on the outcome of a match.

To use this pseudocode, you would need to replace games with a list of tuples that contain the names of the winner and loser for each game played. The ratings will be updated after each game and the final ratings will be printed at the end. You can adjust the constant K in the update_ratings function to adjust the magnitude of the rating changes.
