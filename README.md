# Canadian Rental Price Prediction

An R-based rental price prediction project comparing a Gamma generalized linear model (GLM) with a generalized additive model (GAM). The models are trained on rental listings from selected Canadian cities and evaluated on entirely unseen cities.

## Project Overview

Rental prices are positive, right-skewed, and influenced by nonlinear property and geographic effects. This project evaluates two approaches:

- **Gamma GLM with a log link**
- **GAM with nonlinear square-footage and spatial smooths**

Instead of randomly splitting individual listings, 20% of cities are held out for testing. This provides a more realistic measure of how well the models generalize to new geographic markets.

## Data

The project uses the [25,000+ Canadian Rental Housing Market dataset](https://www.kaggle.com/datasets/sergiygavrylov/25000-canadian-rental-housing-market-june-2024), containing Canadian rental listings collected in June 2024.

Predictors include:

- Square footage
- Bedrooms and bathrooms
- Property type
- Province
- Furnishing and smoking policies
- Cat and dog policies
- Latitude and longitude

The target variable is the advertised monthly rental price in Canadian dollars.

## Data Preparation

The preprocessing workflow:

- Removes duplicate property IDs
- Parses bedroom, bathroom, and square-footage values
- Removes non-residential listing types
- Excludes listings with nonpositive prices, bedrooms, or square footage
- Trims the most extreme 0.1% of price and square-footage values
- Converts categorical predictors to factors

Studios and room rentals are excluded from the final modeling dataset.

## Models

### Gamma GLM

The first model uses a Gamma distribution with a log link. It includes property characteristics, province, rental policies, and an interaction between latitude and longitude.

### Generalized Additive Model

The GAM models log rental price using:

- A smooth function of log square footage
- A two-dimensional spatial smooth of latitude and longitude
- Linear and categorical property characteristics

The model is fitted using restricted maximum likelihood.

## Results

Performance was measured on listings from held-out cities.

| Model | MAE | RMSE | MAPE |
|---|---:|---:|---:|
| Gamma GLM | $368 | $473 | 20.8% |
| GAM | **$254** | **$422** | **12.4%** |

### Prediction Accuracy

| Error tolerance | Gamma GLM | GAM |
|---|---:|---:|
| Within 5% | 14.3% | **30.1%** |
| Within 10% | 28.7% | **53.3%** |
| Within 20% | 57.9% | **82.7%** |
| Within 30% | 77.1% | **92.8%** |

The GAM achieved approximately:

- **31% lower MAE**
- **11% lower RMSE**
- **8.4 percentage points lower MAPE**
- Predictions within 20% of the listed price for **82.7%** of test observations

These results indicate that nonlinear property effects and geographic smoothing substantially improve prediction in unseen cities.
