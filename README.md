# Canadian Rental Price Prediction

This project predicts monthly asking rents for Canadian rental listings and evaluates how well the models generalize to previously unseen cities.

## Models

Two regression approaches are compared:

- **Gamma generalized linear model (GLM):** models positive, right-skewed rental prices.
- **Generalized additive model (GAM):** captures nonlinear relationships and geographic variation using a spatial smooth of latitude and longitude.

Models are trained on listings from selected cities and evaluated on listings from entirely held-out cities. This city-based split provides a more realistic test of geographic generalization than a random train–test split.

## Data

The analysis uses the [25,000+ Canadian Rental Housing Market dataset](https://www.kaggle.com/datasets/sergiygavrylov/25000-canadian-rental-housing-market-june-2024), a June 2024 snapshot of Canadian rental listings.
