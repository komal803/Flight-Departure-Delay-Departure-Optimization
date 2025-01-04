# Introduction  

## 1.1 Problem Statement and Study Objectives  

Flight delays impose significant operational and economic challenges on airlines, airports, and passengers. As air traffic increases, limited airport resources such as gates and runways struggle to meet demand, leading to delays that impact fuel consumption, scheduling efficiency, and passenger satisfaction. This project addresses these challenges by designing a simulation model that replicates real-world flight departure processes while accounting for stochastic delays.  

Using a **Discrete Event Simulation (DES)** approach integrated with **Monte Carlo Simulation**, the project evaluates and optimizes gate and runway utilization to minimize delays. The model incorporates log-normal and Pareto distributions to replicate realistic delay scenarios and tests operational changes such as increasing gates, reallocating resources, or prioritizing flights with tighter schedules. By analyzing these factors, the simulation provides actionable insights for reducing departure delays and improving airport efficiency, supporting data-driven infrastructure investments and resource allocation strategies.  


## 1.2 System Boundary  

The system boundary defines the critical components and processes involved in flight departure operations at an airport. This includes:  

- **Arrival of Flights**: Flights arrive and request gate allocation, with delays influenced by gate availability and scheduling conflicts.  
- **Gate Processes**: Boarding delays are modeled using a log-normal distribution to capture variability in passenger readiness and staff efficiency.  
- **Runway Processes**: After boarding, flights request runway clearance for takeoff. Delays at this stage, including taxiing and sequencing, are modeled using a Pareto distribution to reflect variability in runway operations.  
- **Departure**: Flights successfully take off and exit the system, marking the completion of the departure process within the defined boundary.  

### Scope  
The study focuses on gate and runway resource utilization within a single airport. External factors such as weather, air traffic control, or other airports are excluded to maintain a manageable and focused scope. This approach isolates operational inefficiencies that are directly under the airport's control.  

### Fixed Parameters  
- Number of gates and runways  
- Operational hours of the airport  
- Pre-determined flight schedules  

### Variable Parameters  
- Stochastic arrival times of flights  
- Gate allocation durations  
- Taxi-out and runway clearance times  

These parameters collectively influence the dynamic behavior of the system and are key to understanding and optimizing airport operations.  


## 1.3 Key Performance Measures (KPM)  

This project evaluates system performance using the following key metrics:  

### Total Departure Delay  
- **Definition**: The total time flights spend in the system from gate arrival to successful takeoff.  
- **Significance**: Captures overall efficiency of resource allocation and process flow.  

### Gate Utilization  
- **Definition**: The percentage of time gates are occupied during the simulation period.  
- **Significance**: Reflects gate resource efficiency and identifies underutilized or overburdened gates.  

### Runway Utilization  
- **Definition**: The percentage of time runways are in use during the simulation period.  
- **Significance**: Highlights runway efficiency and potential bottlenecks, especially during peak operations.  

### Average Delay per Flight  
- **Definition**: The average delay time experienced by each flight.  
- **Significance**: Provides a practical indicator of passenger experience and operational efficiency.  

### Resource Waiting Time  
- **Definition**: The time flights spend waiting for gate or runway availability.  
- **Significance**: Offers insights into resource bottlenecks and their contribution to delays, helping identify areas for improvement.  

### Evaluation Goal  
The primary objective is to analyze these performance measures to:  
- Optimize airport resource utilization.  
- Reduce departure delays.  
- Enhance operational efficiency.  
- Improve the overall flight departure process.  

## 2. Modelling Approach  

### 2.1 Collect and Process Real Data  

The dataset for this project, sourced from Kaggle, comprises 484,550 rows of flight information. Key features include *DepDelay* (Departure Delay), *ArrDelay* (Arrival Delay), and various operational metrics. The data underwent pre-processing to ensure quality and suitability for modeling.  

#### Data Pre-Processing  
- **Handling Missing Values**: Rows with incomplete critical columns were removed to maintain data integrity and avoid bias.  
- **Shuffling the Data**: The dataset was shuffled to eliminate temporal patterns that might bias training and validation.  
- **Data Splitting**: The data was divided into two subsets:  
  - 50% for training  
  - 50% for testing  
  This ensured unbiased model evaluation.  

#### Exploratory Data Analysis (EDA)  
To understand relationships between variables and identify factors influencing flight delays, the following analyses were performed:  

1. **Correlation Analysis**:  
   - A correlation heatmap (*Figure 3*) was generated to visualize feature relationships.  
   - **Key Observation**: *DepDelay* (Departure Delay) showed strong correlations with *ArrDelay* (Arrival Delay), highlighting its importance in modeling flight delays.  

2. **Feature Selection**:  
   - Critical variables, such as *DepDelay*, were identified as primary drivers of delay patterns.  
   - These features were prioritized for modeling and simulation.  

3. **Statistical Distribution Fitting**:  
   - Departure delay data was analyzed for distributional properties.  
   - **Distributions Applied**: Log-normal and Pareto distributions were fitted to capture the stochastic nature of delays, effectively reflecting real-world patterns.  

#### Documentation and Visualization  
- **Correlation Heatmap** (*Figure 3*):  
  Visualizes feature relationships, with darker colors indicating stronger correlations. This emphasizes the role of *DepDelay* in predicting delay scenarios.  
- **Pre-Processing Rationale**:  
  Shuffling and data splitting ensured realistic, generalizable representation of the problem and eliminated dataset biases.  

### Correlation Heatmap  

The heatmap below visualizes the relationships between key features. Darker colors indicate stronger correlations, emphasizing the role of `DepDelay` in predicting delay scenarios.  

![Correlation Heatmap](images/correlation_heatmap.png "Figure 3: Correlation Heatmap")
