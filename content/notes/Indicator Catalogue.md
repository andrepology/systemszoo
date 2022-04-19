



### Crime Dashboards
+ Salina Community Dashboard
	+ Inmate Report
	+ Employment Data
	+ Weekly Crime Data (Police and Sheriff's Dept)
	+ **Incentive patterns**: fear
		+ Questionable? Some progress there by celebrating purses being returned etc. but? 
			+ ![[Pasted image 20220403135238.png]]
+ [SF District Attorney](https://www.sfdistrictattorney.org/policy/data-dashboards/)
	+ #meta: everyone has data dashboards. And it might be better than each group maintain their own: **what are we really doing for them?**
		+ make hypotheses "using data to drive office decisions"
		+ Thinking about MVP
		+ Kaggle-like model, where we ask/field challenges around indicators, and tokenise the **modeling**. 
			+ This is the huge bottleneck. 
	+ Has has six public data dashboards
		+ 1) Incidents, Arrests, and Prosecutions, 
			+ Literally more hosted powerBI. 
			+ Why not start there? 
				+ #visualisation #todo: need to have a widget class that wraps a plotting library and has out of box support for view manipulation. 
					+ For line, bar charts, pie
		+ 2) District Attorney Actions on Arrests Presented, 
		+ 3) Cases Prosecuted, 
		+ 4) Case Resolutions, 
		+ 5) Outcomes and Desistance; and 
		+ 6) Independent Investigations Bureau. 

+ [SFPD Crime Dashboard](https://www.sanfranciscopolice.org/stay-safe/crime-data/crime-dashboard)
	+ #crit: not especially interactive
	+ #meta: uses hosted Tableau
		+ Why not use this?
			+ Has neat support for sharing, downloading (solves journalism problem)
			+ Estremely robust and well-maintained. Can focus on getting the indicators **right** with these, and then moving from there. 
			+ So: experiment in jupyter, then move to tableau. 
		+ There is always going to be a need for a context panel, either to describe the data or model itself. Or just to supply more info. 

+ [Civic Hub](https://www.civichub.us/ca/san-francisco/gov/police-department/crime-data)
	+ **Anchors a table to a map** (Shared data source), perhaps exemplifying a widget: you have a View that can switch, but the underlying data is the same.

+ [Crime in New York City](https://www.kaggle.com/code/adamschroeder/crime-in-new-york-city)
	+ #meta: this is the modeling approach
		+ Crime dataset 
		+ Find years
		+ scope to indicator
			+ Crimes by burrough
			+ Ranking of crimes by frequency
			+ Crimes by time of day
			+ Crimes per population
			+ 2015 crimes per boro

+ [Electricity price forecasting with DNNs (+ EDA)](https://www.kaggle.com/code/dimitriosroussis/electricity-price-forecasting-with-dnns-eda)
	+ #meta: these need LONG descriptions (thousands of words), wondering what format we'll need to communicate a model in a terse way. Limit to description? Ah, seems so constrained. 
		+ #todo #presentation How does modeling not turn into presenting jupyter notebooks? 
		+ #meta: essentially, the modeling layer constitutes a 156 assignment. 
		+ Joins `wather_features.csv` and `energy_dataset.csv`
			+ Shows the extend to which good modeling is scarce, so we meed an open source protocol to contributing good models, perhaps with the community currency. 
			+ Like, here is an outline of the steps
				1. Exploration and Cleaning
					1. Energy Dataset
					2. Weather Features Dataset
				2. Visualizations and Time Series Analysis
					1. Interesting Viz
					2. Decomposition and Stationary Tests
						1. Stats (KPSS, Augmented Dickey-Fuller)
					3. Autocorrelation, partial corr and cross-corr
				3. Feature Engineering
					1. Feature Generation
						1. "Weekend" Feature
						2. City weights using population
					2. Feature Selection
						1. PCA
				4. Electricity Price Forecasting
					1. XGBoost
					2. Architecture comparison
						1. Stacked LSTM
						2. CNN
						3. CNN-LSTM
						4. Time Distributed MLP
						5. Encoder-Decoder
				5. Results
				6. References
		7. 

+ [House prices: Lasso, XGBoost, detailed EDA](https://www.kaggle.com/code/erikbruin/house-prices-lasso-xgboost-and-a-detailed-eda)
	+ Outline		
		1 Executive Summary
		2 Introduction
		3 Loading and Exploring Data
		3.1 Loading libraries required and reading the data into R
		3.2 Data size and structure
		4 Exploring some of the most important variables
		4.1 The response variable; SalePrice
		4.2 The most important numeric predictors
		4.2.1 Correlations with SalePrice
		4.2.2 Overall Quality
		4.2.3 Above Grade (Ground) Living Area (square feet)
		5 Missing data, label encoding, and factorizing variables
		5.1 Completeness of the data
		5.2 Imputing missing data
		5.3 Label encoding/factorizing the remaining character variables
		5.4 Changing some numeric variables into factors
		5.4.1 Year and Month Sold
		5.4.2 MSSubClass
		6 Visualization of important variables
		6.1 Correlations again
		6.2 Finding variable importance with a quick Random Forest
		6.2.1 Above Ground Living Area, and other surface related variables (in square feet)
		6.2.2 The most important categorical variable; Neighborhood
		6.2.3 Overall Quality, and other Quality variables
		6.2.4 The second most important categorical variable; MSSubClass
		6.2.5 Garage variables
		6.2.6 Basement variables
		7 Feature engineering
		7.1 Total number of Bathrooms
		7.2 Adding ‘House Age’, ‘Remodeled (Yes/No)’, and IsNew variables
		7.3 Binning Neighborhood
		7.4 Total Square Feet
		7.5 Consolidating Porch variables
		8 Preparing data for modeling
		8.1 Dropping highly correlated variables
		8.2 Removing outliers
		8.3 PreProcessing predictor variables
		8.3.1 Skewness and normalizing of the numeric predictors
		8.3.2 One hot encoding the categorical variables
		8.3.3 Removing levels with few or no observations in train or test
		8.4 Dealing with skewness of response variable
		8.5 Composing train and test sets
		9 Modeling
		9.1 Lasso regression model
		9.2 XGBoost model
		9.3 Averaging predictions

