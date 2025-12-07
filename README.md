# coffee-yield-classification
Machine learning model to predict coffee yield for smallholder farmers in East Africa using Random Forest classification
# Coffee Yield Classification in East Africa

A machine learning solution to predict coffee yield categories for smallholder farmers across East Africa using agronomic and climatic features.

## Project Overview

This project applies the **Nine Wheels of Statistical Machine Learning** framework to develop a predictive model that helps smallholder coffee farmers in East Africa optimize yield through data-driven decisions.

**Problem**: Smallholder farmers lack information about what drives coffee yield, leading to suboptimal resource allocation and financial instability.

**Solution**: A trained Random Forest model that predicts yield categories (Low/Medium/High) based on farm features, enabling farmers and extension agents to implement targeted interventions.

## Dataset

- **Sample Size**: 300 farms
- **Features**: 10 agronomic and climatic variables
  - Rainfall (mm)
  - Temperature (°C)
  - Soil pH
  - Nitrogen content (%)
  - Altitude (meters)
  - Fertilizer application (kg/hectare)
  - Planting density (plants/hectare)
  - Irrigation events (count)
  - Soil moisture (%)

- **Target**: Yield category
  - Low: ≤ 800 kg/hectare
  - Medium: 800-1200 kg/hectare
  - High: > 1200 kg/hectare

## Model Performance

**Random Forest (Winning Model)**
- Test Accuracy: 1
- 95% Confidence Interval: [1 1]

**Key Finding**: Rainfall and soil pH are the most important predictors of coffee yield.

## Files in This Repository

- `coffee_yield_model.rds` – Trained Random Forest model (R format)
- `model_importance.csv` – Feature importance scores (open in Excel)
- `model_summary.txt` – Model details and performance metrics
- `README.md` – This file
- `data/` – Synthetic training dataset
- `notebooks/` – Complete analysis following Nine Wheels of SML framework
  - Wheel 1: Problem Formulation
  - Wheel 2: Data Exploration
  - Wheel 3: Model Specification
  - Wheel 4: Learning Criteria
  - Wheel 5: Optimization
  - Wheel 6: Regularization
  - Wheel 7: Validation
  - Wheel 8: Statistical Inference
  - Wheel 9: Deployment

## How to Use

### Load the Trained Model
```r
library(randomForest)

rf_model <- readRDS("coffee_yield_model.rds")

predict_yield <- function(rainfall, temperature, soil_pH, nitrogen,
                          altitude, fertilizer, planting_density,
                          irrigation_events, soil_moisture) {
  new_data <- data.frame(rainfall, temperature, soil_pH, nitrogen,
                         altitude, fertilizer, planting_density,
                         irrigation_events, soil_moisture)
  prediction <- predict(rf_model, new_data, type = "class")
  return(prediction)
}

# Example prediction
result <- predict_yield(rainfall = 1800, temperature = 22, soil_pH = 6.0,
                       nitrogen = 0.15, altitude = 1800, fertilizer = 150,
                       planting_density = 4500, irrigation_events = 15,
                       soil_moisture = 50)
print(result)  # Output: Low/Medium/High
```

## Actionable Recommendations

Based on predicted yield category:

**Low Yield**
- Increase rainfall/irrigation
- Improve soil pH (target 5.8-6.5)
- Boost nitrogen fertilizer application

**Medium Yield**
- Maintain current practices
- Consider modest fertilizer increases

**High Yield**
- Maintain optimal practices
- Document and share with neighboring farmers

## Deployment

The model is designed for deployment to smallholder farmers through:
- **Extension agents** – Train agents to use prediction function
- **Regional rollout** – Phased implementation across East Africa
- **Quarterly updates** – Continuous model refinement with new data

## Author

**richill25**

## License

This project is open source and available for agricultural development use.

## References

Framework: Nine Wheels of Statistical Machine Learning (Prof. Ernest Fokoué, AIMS)

