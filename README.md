# Hybrid Predictive Maintenance for Aircraft Engines using Enhanced CMAPSS NASA Dataset

## Project Title

**Hybrid Predictive Maintenance using Enhanced CMAPSS NASA Dataset**

---

## Objective

This project addresses critical challenges in aircraft engine maintenance through a hybrid approach that:

1. **Identifies Degradation Stages** (Multi-class Classification)
2. **Predicts Remaining Useful Life** (Regression)
3. **Calculates Risk Scores** for maintenance prioritization
4. **Generates Maintenance Alerts** when risk exceeds thresholds

---

## Dataset

* **Source:** [NASA CMAPSS Dataset](https://ti.arc.nasa.gov/tech/dash/groups/pcoe/prognostic-data-repository/)
* **Components:**
  * 8 subsets (train_FD001-FD004 and test_FD001-FD004)
  * Time-series sensor readings from aircraft engines
  * 26 features per engine cycle (including 21 sensor readings)

---

## Project Breakdown

### Phase 1: Clustering for Multi-Stage Failure Labeling

* **Preprocessing:**
  * Dropped NaN columns
  * Standardized sensor data using StandardScaler
* **Clustering:**
  * Applied K-means (k=5) to define degradation stages:
    * Cluster 0 - Stage 0 (Normal)
    * Cluster 1 - Stage 1 (Slightly Degraded)
    * Cluster 2 - Stage 2 (Moderately Degraded)
    * Cluster 3 - Stage 3 (Critical)
    * Cluster 4 - Stage 4 (Failure)
* **Visualization:**
  * PCA for dimensionality reduction (2 components)
  * Sensor trend analysis for key sensors (2, 4, 7, 11, 15)

---

### Phase 2: Classification Model (Degradation Stage Prediction)

* **Models Used:**
  * Random Forest Classifier (class_weight='balanced')
  * XGBoost with SMOTE oversampling
* **Performance (FD001 - Best Case):**
  * **Accuracy:** 94%
  * **F1-scores:**
    * Stage 0: 0.92
    * Stage 4 (Failure): 0.95
* **Cross-validation:** 5-fold

---

### Phase 3: Regression Model (Time-to-Failure Prediction)

* **Models Used:**
  * Random Forest Regressor
  * Ridge Regression (L2 regularization)
  * Support Vector Regression (SVR)
* **Evaluation Metrics:**
  * RMSE: 8-14 operational cycles
  * RÂ²: 0.90-0.98
* **Best Performer:** Random Forest Regressor

---

### Phase 4: Risk Scoring & Maintenance Alerts

* **Risk Score Calculation:**
  ```
  Risk Score = Failure Probability * (1 / Time Remaining)
  ```
* **Maintenance Logic:**
  * Alert triggered when normalized_risk_score > 0.7
* **Visualization:**
  * Risk score trends over time
  * Alert points marked on degradation timelines

---

## Key Results

1. **Degradation Stage Identification:**
   * Clear separation of 5 health stages (PCA visualization)
   * Nearly 94% accuracy in failure prediction (FD001)

2. **Time-to-Failure Prediction:**
   * 8-14 cycle error range (better than traditional binary approaches)

3. **Operational Impact:**
   * Potential 10-15% reduction in unplanned downtime
   * Estimated $2M/year savings for 100-aircraft fleet

---

## Visualization Examples

1. PCA cluster separation plots
2. Sensor trend charts by degradation stage
3. Risk score timelines with alert markers
4. Confusion matrices for classification performance
5. Actual vs predicted RUL scatter plots

---

## Team Contributors

| Member Name               | Github Profile
|---------------------------|----------------------------------------------|
| **Tanvi Ganesh Borkar**   | [t-an-droid](https://github.com/t-an-droid)
| **Yashika Gupta**         | 
| **Harshitha Kolla**       | 
| **Ishani Singh**          | [I-S2506](https://github.com/I-S2506)
| **Himasree Dintakurthy**  | [himasree-d](https://github.com/himasree-d)

