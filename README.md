# Canadian Rental Price Prediction

This project predicts monthly asking rents for Canadian rental listings and evaluates how well the models generalize to previously unseen cities.

## Models

Two regression approaches are compared:

- **Gamma generalized linear model (GLM):** models positive, right-skewed rental prices.
- **Generalized additive model (GAM):** captures nonlinear relationships and geographic variation using a spatial smooth of latitude and longitude.

Models are trained on listings from selected cities and evaluated on listings from entirely held-out cities. This city-based split provides a more realistic test of geographic generalization than a random train–test split.

## Data

The analysis uses the [25,000+ Canadian Rental Housing Market dataset](https://www.kaggle.com/datasets/sergiygavrylov/25000-canadian-rental-housing-market-june-2024), a June 2024 snapshot of Canadian rental listings.

The dataset includes:

- Monthly asking price in CAD
- City and province
- Latitude and longitude
- Property type
- Bedrooms and bathrooms
- Square footage
- Lease, furnishing, smoking, and pet information

## Results

| Model | MAE | RMSE | Gamma deviance |
|---|---:|---:|---:|
| Gamma GLM | TBD | TBD | TBD |
| Spatial GAM | TBD | TBD | TBD |

_Add a short interpretation of which model performed better and where errors were largest._

## Reproducing the Analysis

1. Download `rentfaster.csv` from Kaggle.
2. Place it in `[your data directory]`.
3. Install the required R packages.
4. Render the report:

```r
rmarkdown::render("[report-name].Rmd")
