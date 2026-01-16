# CSAS_Curling_Data_Challenge

# README: Mixed Doubles Power Play Strategic Analysis
This submission contains the analytical framework used to determine optimal opening strategies for the Mixed Doubles Power Play. The included code processes historical telemetry to establish statistical benchmarks for defensive (Shot 7) and offensive (Shot 8) success.

### File Descriptions
##### 1. powerplay_defense.ipynb

This is the primary documented code file. It is a self-contained Jupyter Notebook that performs the following operations:

- Data Integration: Joins Stones.csv and Ends.csv to create a unified dataset for Power Play ends.

- Spatial Categorization: Implements coordinate-based binning to identify stone locations (e.g., Inside Edge House, True Center, and High Guards).

- Perspective Logic: Calibrates stone coordinates to ensure offensive "True Split" analysis is accurate regardless of delivery order.

- Statistical Computation: Calculates the Failure Rate (allowing 2+ points) for defensive tasks and Average Points/Big End Probability for offensive tasks.

- Outcome Analysis: Filters results by game context (Score, Timing) and execution quality (Points) to isolate the "Safety Floor" of specific shots.

### Reproducibility Requirements

##### Data Files

This code is designed to run using the standardized CSV files provided by the data challenge (e.g., Stones.csv, Ends.csv, Games.csv). Per the submission guidelines, these datasets are not included in this zip file. To run the analysis:
Ensure the competition CSV files are located in the same working directory as the notebook.
The notebook assumes standard column headers as defined in the challenge documentation.

##### Dependencies

The analysis was performed using standard Python data science libraries:

- pandas: For data manipulation and merging.

- numpy: For coordinate calculations and categorical binning.

- matplotlib / seaborn: For generating the spatial and statistical visualizations included in the report.
