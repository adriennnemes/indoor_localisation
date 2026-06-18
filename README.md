# Indoor Localization using WiFi Signals

## Project Overview

This project explores indoor positioning using WiFi RSSI (Received Signal Strength Indicator) fingerprints. The goal was to estimate device locations inside a building based solely on WiFi signal measurements collected from multiple access points.

The project focuses on the complete machine learning workflow, including data preparation, exploratory data analysis, feature engineering, model development, validation, and performance improvement.

Rather than relying on complex localization algorithms, the project investigates how a carefully designed k-Nearest Neighbors (k-NN) approach can be enhanced through domain knowledge and signal-aware preprocessing techniques.


## Objectives

- Estimate indoor device positions using WiFi signal fingerprints
- Investigate the impact of device orientation on localization accuracy
- Improve a baseline k-NN model through feature engineering and weighting strategies
- Evaluate model robustness using cross-validation and hyperparameter tuning
- Gain practical experience with real-world noisy sensor data


## Dataset

The dataset consists of offline reference measurements and online test measurements collected inside an indoor environment.

Each observation contains:

- WiFi access point identifiers (MAC addresses)
- RSSI signal strength values
- Device orientation
- Ground-truth position coordinates (X, Y)

To improve data quality, only the most stable access points were selected for modeling.


## Data Preparation

Several preprocessing steps were performed before model development:

- Selection of the most reliable WiFi access points
- Creation of a complete signal matrix for all reference points
- Handling of missing RSSI values through mean-value imputation
- Transformation of orientation values into comparable categories
- Reshaping and filtering of measurement data
- Preparation of offline and online datasets for localization tasks

The project highlights the importance of data cleaning and preprocessing in achieving reliable machine learning results.


## Exploratory Data Analysis (EDA)

The exploratory phase focused on understanding:

- Distribution of WiFi signal strengths
- Coverage of measurement locations
- Device orientation patterns
- Signal variability across access points
- Spatial characteristics of the indoor environment

Several visualizations were created to identify patterns and better understand how signal behavior influences localization performance.


## Modeling Approach

### Baseline Model

A standard k-Nearest Neighbors (k-NN) model was implemented as the initial benchmark.

For each new observation:

1. The nearest reference points were identified based on RSSI similarity.
2. The predicted position was calculated from neighboring observations.

While simple and interpretable, the baseline approach did not consider device orientation and treated all neighbors equally.

### Model Improvements

To better reflect real-world conditions, two enhancements were introduced.

#### Orientation Filtering

Only reference measurements with similar device orientations were considered.

This addresses the fact that WiFi signal strength can vary significantly depending on how a device is oriented.

#### Distance Weighting

Neighbors were weighted according to their distance from the query point.

Closer observations received greater influence on the final position estimate, reducing the impact of less relevant neighbors.


## Hyperparameter Optimization

Model parameters were optimized using cross-validation.

Different combinations of:

- k (number of neighbors)
- orientation filtering thresholds

were evaluated to identify the most robust configuration.

This process helped reduce overfitting and ensured that model selection was based on systematic evaluation rather than manual trial and error.


## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook


## Key Learnings

This project provided practical experience in:

- Indoor positioning systems
- WiFi fingerprinting techniques
- Data preprocessing and cleaning
- Exploratory data analysis
- Feature engineering
- k-NN based machine learning models
- Hyperparameter tuning
- Cross-validation
- Working with noisy real-world sensor data

One of the most important lessons learned was that data quality and domain-specific preprocessing often have a greater impact on performance than the choice of machine learning algorithm itself.


## Future Improvements

Potential future extensions include:

- Testing alternative localization algorithms
- Evaluating additional distance metrics
- Incorporating more access points and signal features
- Real-time localization deployment
- Comparing k-NN with more advanced machine learning approaches
