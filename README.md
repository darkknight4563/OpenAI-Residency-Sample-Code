# Building AI Course Project: Crypto Currency Trading System

Final project for the Building AI course.

## Summary

This endeavor explores a novel approach of intertwining AI's analytical power with the dynamic world of cryptocurrencies to craft a basic trading system. The primary aim is to alleviate the hurdles faced by human traders such as emotional biases and manual data analysis, by employing AI to generate trading signals based on market trends and potential price movements. The exploration of this idea is embarked upon with a conservative stance, excluding complex or risky trading strategies, to ensure a solid foundation before advancing to more intricate methods.

## Background

The fascination with cryptocurrency trading has surged, yet the journey is often impeded by human emotions and the tiresome manual search for trading opportunities. This project advocates for a symbiotic relationship between human intuition and AI's computational prowess, aiming to capitalize on each's strengths while mitigating their weaknesses. Initially, the scope is narrowed down to basic trading strategies ensuring a controlled and manageable environment for the project to thrive.

## How is it used?

The system is conceived to first serve personal trading endeavors, with a vision of scaling it up to aid the wider retail trading community. The figure below sketches a rudimentary model of the envisaged AI-based trading solution, hinting at broader considerations like risk management and transaction costs which, for now, rest on human discretion.

![trading-system-basic](https://github.com/krohts/building-AI-project/blob/main/AI-empowered-trading-system-basic.png)

## Data sources and AI methods

The project leans on diverse data sources ranging from daily crypto trading stats, market indices, to various other metrics from platforms like CoinMarketCap, TradingView, and others. At its core, logistic regression will steer the AI's classification tasks, yet the doors are open for future expansion into deep learning and sentiment analysis, harnessing a spectrum of data for well-rounded decision-making.

## Challenges

A few challenges loom ahead:

1. Engrossment in details
2. Over-stretching the project scope
3. Uncertainty in finding a working solution

Addressing these challenges hinges on adhering to a Minimum Viable Product (MVP) approach, ensuring a focused and pragmatic stride towards the goals set. The absence of a working solution, albeit unlikely, still holds value in the lessons learned and the knowledge acquired.

##Importing Necessary Libraries:
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.neural_network import MLPRegressor

##Data Loading and Preprocessing:
# Load data
data = pd.read_csv('crypto_data.csv')

# Preprocess data
data = data.dropna()

# Split data into training and testing sets
train_data, test_data = train_test_split(data, test_size=0.2, random_state=42)

##Neural Network Architecture:
# Define neural network architecture
mlp = MLPRegressor(hidden_layer_sizes=(2, 2), activation='relu', solver='adam')

# Fit the model
mlp.fit(train_data[['feature1', 'feature2', 'feature3', 'feature4', 'feature5']], train_data['price'])

# Make predictions
predictions = mlp.predict(test_data[['feature1', 'feature2', 'feature3', 'feature4', 'feature5']])

##Evaluation:
# Evaluate model
from sklearn.metrics import mean_absolute_error
mae = mean_absolute_error(test_data['price'], predictions)
print(f'Mean Absolute Error: {mae}')

##Example of a Trading Signal Generation:
def generate_trading_signal(price_data):
    # Assuming price_data is a pandas DataFrame with price information
    signal = []
    for i in range(1, len(price_data)):
        if price_data['Close'].iloc[i] > price_data['Close'].iloc[i-1]:
            signal.append('Buy')
        else:
            signal.append('Sell')
    price_data['Signal'] = ['Hold'] + signal  # Assume 'Hold' for the first entry as there's no prior day to compare
![Alt text for the image](https://github.com/darkknight4563/OpenAI-Residency-Sample-Code/blob/main/DALL%C2%B7E%202023-10-06%2010.39.22%20-%20Oil%20painting%20in%20the%20style%20reminiscent%20of%20the%20Renaissance%20era_%20An%20allegorical%20depiction%20of%20the%20symbiotic%20relationship%20between%20human%20intuition%20and%20AI.%20A.png)
![Alt text for the image](https://github.com/darkknight4563/OpenAI-Residency-Sample-Code/blob/main/DALL%C2%B7E%202023-10-06%2010.39.08%20-%20Illustration_%20An%20intricate%20flowchart%20showcasing%20the%20process%20of%20the%20AI%20trading%20system.%20Starting%20from%20data%20collection%20from%20sources%20like%20CoinMarketCap%20an.png)


# Usage:
generate_trading_signal(price_data)

##Visualization:
```python
import matplotlib.pyplot as plt

# Plotting the actual vs predicted values
plt.figure(figsize=(10, 6))
plt.plot(test_data['price'].values, label='Actual Prices')
plt.plot(predictions, label='Predicted Prices')
plt.title('Actual vs Predicted Prices')
plt.legend()
plt.show()


7. **User Interaction**:
If your project has a user interface or accepts user input, you could include a code snippet demonstrating this functionality.

```markdown
```python
# Assuming a simple function to get user input and return a prediction
def get_user_input():
    features = []  # List to hold user input
    features.append(float(input("Enter feature 1: ")))
    features.append(float(input("Enter feature 2: ")))
    # ... get remaining feature values
    return np.array(features).reshape(1, -1)  # Reshape for single prediction

# Get user input
user_input = get_user_input()

# Make a prediction
user_prediction = mlp.predict(user_input)
print(f'Predicted Price: {user_prediction[0]}')


8. **Troubleshooting**:
If there are common issues users might run into, you could include a section with troubleshooting steps.

```markdown
## Troubleshooting

- **Issue**: Model not converging
  - **Solution**: Try adjusting the learning rate or the number of iterations, or ensure your data is normalized.
- **Issue**: Missing data
  - **Solution**: Ensure all data files are located in the correct directory, or check for missing values in your data and handle them accordingly.

##Further Development:
## Further Development

- Implementing deep learning for better prediction accuracy.
- Incorporating real-time data feeds for live trading signals.
- Adding a user-friendly interface for easier interaction.
- Expanding the trading strategy to include more complex indicators and order types.

##Contributing:
## Contributing

Feel free to fork this project and submit your own pull requests to contribute. All contributions are welcome!



## What next?

The roadmap ahead encompasses detailed understanding of the trading domain, data gathering, model development, and iterative testing. The process, although outlined in a linear fashion, embraces an iterative nature, constantly revisiting previous steps for refinement. Beyond the current project, there's potential for evolving into a full-fledged algorithmic trading strategy, possibly venturing into a subscription-based service model aiding retail traders.

![trading-system-full](https://github.com/krohts/building-AI-project/blob/main/AI-empowered-trading-system-full.png)

## Acknowledgments

Special thanks to Rafael Schultze-Kraft for shedding light on the intricacies of cryptocurrency price prediction and sharing invaluable resources which have served as a beacon of inspiration for this project. His work can be found [here](https://hackernoon.com/dont-be-fooled-deceptive-cryptocurrency-price-predictions-using-deep-learning-bf27e4837151).
