# iFootballManager

Building AI course project

## Summary

Manage a team on a budget! Find players that are outperforming their market value, maximize player quality within a given budget. Not every team is Manchester City and can afford high profile players.

## Background

* Teams function under a limited budget but still want to improve and be competitive with the money they have. How do they decide to buy new players? 
* Scouting multiple players across multiple leagues is expensive and relies on the quality of the scout. 
* Developing your own players is also a large investment that requires an expensive infrastructure. 

## How is it used?

The AI will gather data of all players for a given position and in a given league. It then suggests players to buy based on the available budget. Managers of football teams with limited resources can then decide where and with whom to strenghten their team and who to sell to free up budget.

Linear regression can be used to determine the predicted market price. The system can be trained with data from players that are recently traded and their stastics. 

Simple code example using NumPy:

```
def main():
  # example budget
  budget = 1000000
  
  # example number of players to buy
  players = 2
  
  # suppose we have the data in a text file with the player stats where first column is the player name, 
  # and the last column is their real market price (based on recent transfer), and the columns in between are player statistics 
  # like pass% shot% minutes played, etc, and the player market value in last column
  train_data = np.genfromtxt(StringIO(train_string), skip_header=1)
    
  # split the data into coefficients (x) and market value (y) 
  player_train_value = train_data[:, -1]
  player_train_coefficents = train_data[:, 1:-1]
  
  # fit a linear regression model to the data and get the coefficients
  c = np.linalg.lstsq(player_train_coefficents, player_train_value)[0]

  # Test data has similar data format compared to train data
  player_data = np.genfromtxt(StringIO(test_string), skip_header=1)
  player_values = player_data[:, -1]
  player_coef_data = player_data[:, 1:-1]
  player_names = player_data[:, 0]
  
  # save the player data and print out the predicted market values for the players in the data set
  player_predicted_values = (player_coef_data @ c)
  print(player_predicted_values)
  
  # optimize the budget and players to buy
  # first create a list of players by market value vs current market value 
  relative_market_value = []
  for i in range(len(player_predicted_values):
    current_player = { name: player_names[i], value_gain: player_values[i] - player_predicted_values[i] }
    relative_market_value.append(current_player)
  
  print(relative_market_value)
  
  # algorythm to maximize the budget and amount of players to be implemented below
    
main()
```
##  Data sources and AI methods
- **User data:** Questionnaires about skin type, allergies, lifestyle habits.  
- **Product databases:** Open cosmetic ingredient databases (e.g., INCI lists).  
- **Environmental data:** Climate conditions (humidity, temperature, UV index) via weather APIs.  
- **AI methods:**  
  - Classification models to detect skin type.  
  - Recommendation systems to match products with user profiles.  
  - NLP to analyze product reviews and extract sentiment.  
  - Computer vision (future extension) to analyze skin photos.  
  - Integration with external APIs (weather, product data) for richer evaluation.  

---

## Challenges
- AI can suggest suitable products, but it cannot guarantee how each individual’s skin will react.  
- Skin conditions are influenced by hormones, stress, and lifestyle factors that may not be captured in data.  
- Ingredient databases may be incomplete or inconsistent.  
- Recommendations cannot replace professional dermatological advice.  

---

##  What next?
- **Skin photo analysis:** Add computer vision to detect dryness, acne, or irritation directly from user images.  
- **Dynamic recommendations:** Suggest different routines depending on season, climate, or daily habits.  
- **Trend analysis:** Use NLP to track beauty trends and adapt recommendations accordingly.  
- **Wellness integration:** Expand beyond skincare into nutrition, sleep, and fitness for holistic beauty advice.  
- **Personalized categories:** Logistic regression to classify users into categories (basic care, advanced care, sensitive skin, premium care).  
- **Technical requirements:** Access APIs for weather, product ingredient data, and user health trackers.  

---

##  Acknowledgments
- **Data inspiration:** Open cosmetic ingredient databases, dermatology research papers.  
- **Libraries:** Python (pandas, scikit‑learn).  
- **Sources:** Beauty blogs, skincare forums, product review platforms.  
- **Community:** Building AI course project gallery and GitHub community projects.  

## 📎 Additional resources
- [INCI Decoder](https://incidecoder.com/) — база даних косметичних інгредієнтів.  
- [CosDNA](https://www.cosdna.com/) — аналіз складу продуктів та відгуки користувачів.  
- [OpenWeather API](https://openweathermap.org/api) — дані про кліматичні умови для персоналізованих рекомендацій.  
- [PubMed Dermatology](https://pubmed.ncbi.nlm.nih.gov/) — наукові статті про догляд за шкірою.  

---

