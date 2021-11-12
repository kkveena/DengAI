How to Build and run the model
Please Extract zip file to a local Windows directory
Pynton environment should be available in local environment. It is recommened to install Anaconda
Data Processing and Model code is in Jupyter notebook
Inline commets are provided in Jupyter notebook for underlying assumptions and context
Below is directory structure
Information
	Actual codebase is in Sandbox directory . Following is a breif description
	- sandbox
		-dengAI-SanJuan.ipynb --> It creates feature data (based on climate and environment data provided as per 
		(https://dengueforecasting.noaa.gov/)
		Underlying code preprocesses the data , imputes data and create feature list for SanJuan indexed by (city, year, weekofyear)
		as per https://www.drivendata.org/competitions/44/dengai-predicting-disease-spread/page/82/
		
		- dengAI-Iquitos.ipynb --> It creates feature data (based on climate and environment data provided as per 
		(https://dengueforecasting.noaa.gov/)
		Underlying code preprocesses the data , imputes data and create feature list for Iquitos indexed by (city, year, weekofyear)
		as per https://www.drivendata.org/competitions/44/dengai-predicting-disease-spread/page/82/
		
		-dengAI-modelling.ipynb --> This is actual modelling code. It will find the best model to predict dengu outbreak for respective cities
		In process, It will create output file to predict "total_cases" of outbreak for respectivecity indexed by (city, year, weekofyear)
		It will also plot various graphs to aid in analyzing best performing model
		
	-output
		- dfIquitos.csv --> It is processed feature list for City Iquitos indexed by (city, year, weekofyear)
		- dfSanJuan.csv --> It is processed feature list for City San Juan indexed by (city, year, weekofyear)
		- IquitosPredictions_PCA.csv --> It is prediction of total cases on test data for Iquitos indexed by (city, year, weekofyear)
		- SanJuanPredictions_NegativeBinomial.csv --> It is prediction of total cases on test data for San Juan indexed by (city, year, weekofyear)
		
	-data (Files are downloaded from (https://dengueforecasting.noaa.gov/)
		(Iquitos City feature list)
		- Iquitos_Training_Data.csv --> For  'total_cases' feature
		- iquitos_noqc.csv --> 'ndvi_location_1', 'ndvi_location_2', 'ndvi_location_3', 'ndvi_location_4' features
		- IquitosPE000084377.csv --> 'station_max_temp_c', 'station_min_temp_c','station_avg_temp_c', 'station_diur_temp_rng_c', 
		  and 'precipitation_amt_mm' features
		- Iquitos.xlsx (ReanalysisHumidity tab) --> 'reanalysis_air_temp_k','reanalysis_dew_point_temp_k', 'reanalysis_relative_humidity_percent',
		  'reanalysis_specific_humidity_g_per_kg' features
		- Iquitos.xlsx (RanalysisTemp tab) --> 'reanalysis_min_air_temp_k', 'reanalysis_max_air_temp_k', 'reanalysis_precip_amt_kg_per_m2',
		  'reanalysis_tdtr_k', 'reanalysis_avg_temp_k' features
		- Iquitos.xlsx (SatellitePrecip tab) --> 'reanalysis_sat_precip_amt_mm' feature
		- Iquitos_Precip.xlsx --> 'station_precip_mm' feature
		
		(San Juan City feature list)
		- San_Juan_Training_Data.csv --> For  'total_cases' feature
		- sanJuan_noqc.csv --> 'ndvi_location_1', 'ndvi_location_2', 'ndvi_location_3', 'ndvi_location_4' features
		- SanJuanRQW00011641.csv --> 'station_max_temp_c', 'station_min_temp_c','station_avg_temp_c', 'station_diur_temp_rng_c', 
		  and 'precipitation_amt_mm' features
		- SanJuan.xlsx (ReanalysisHumidity tab) --> 'reanalysis_air_temp_k','reanalysis_dew_point_temp_k', 'reanalysis_relative_humidity_percent',
		  'reanalysis_specific_humidity_g_per_kg' features
		- SanJuan.xlsx (ReanalysisTemp tab) --> 'reanalysis_min_air_temp_k', 'reanalysis_max_air_temp_k', 'reanalysis_precip_amt_kg_per_m2',
		  'reanalysis_tdtr_k', 'reanalysis_avg_temp_k' features
		- SanJuan.xlsx (SatellitePrecip tab) --> 'reanalysis_sat_precip_amt_mm' feature
		- SanJuan_Precip.xlsx --> 'station_precip_mm' feature
		
	-plots (various plots for model analysis
		-SanJuanHistoGram.png --> Feature Data distribution for SanJuan
		-IquitosHistoGram.png --> Feature Data distribution for Iquitos
		-SanJuanHeatMap.png --> Feature correlation Heat Map for SanJuan
		-IquitosHeatMap.png --> Feature correlation Heat Map for Iquitos
		-SanJuanCorr.png --> Horizontal correlation for SanJuan
		-IquitosCorr.png --> Horizontal correlation for Iquitos
		-Linear Regression_sj.png --> Actual vs Fitted - Linear Regression for SanJuan
		-Decision Tree_sj.png --> Actual vs Fitted - Decision Tree for SanJuan
		-Random Forest_sj.png --> Actual vs Fitted - Random Forest for SanJuan
		-Random Forest-Best Params_sj.png --> Actual vs Fitted - Random Forest-Best Params for SanJuan
		-PCA_sj.png --> Actual vs Fitted - Actual vs Fitted - PCA for SanJuan
		-NegativeBinomial_sj.png --> Actual vs Fitted - Actual vs Fitted - PCA for SanJuan
		-MSEvsRMSEPlot_sj.png --> MSE vs RMSE plot for all underlying models for SanJuan
		-Linear Regression_iq.png --> Actual vs Fitted - Linear Regression for Iquitos
		-Decision Tree_iq.png --> Actual vs Fitted - Decision Tree for Iquitos
		-Random Forest_iq.png --> Actual vs Fitted - Random Forest for Iquitos
		-Random Forest-Best Params_iq.png --> Actual vs Fitted - Random Forest-Best Params for Iquitos
		-PCA_iq.png --> Actual vs Fitted - Actual vs Fitted - PCA for Iquitos
		-NegativeBinomial_iq.png --> Actual vs Fitted - Actual vs Fitted - PCA for Iquitos
		-MSEvsRMSEPlot_iq.png --> MSE vs RMSE plot for all underlying models for Iquitos

Run
	Please execute below files in squence
	1. dengAI-SanJuan.ipynb will produce feature list output file for SanJuan (dfSanJuan.csv)
	2. dengAI-Iquitos.ipynb will produce feature list output file for Iquitos (dfIquitos.csv.csv)
	3. dengAI-modelling.ipynb will produce prediction file for respective cities (SanJuan and Iquitos as SanJuanPredictions_NegativeBinomial.csv and IquitosPredictions_PCA.csv respectively. It will also plot figures (as described under "plots" directory) for model analysis