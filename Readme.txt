read  and write out  seperate files for 2017 to 2022:
	Notebook that extracts 2021 data from Iowa liquor sales data (initally other years were pulled too, but they were not used in the project and are commented out)


Liquor 2021 cleaned: Notebook  reads in the file created in above notebook cleans up and creates csv files for use in the project

create data for  product clustering: Notebook name is self explanatory

data quality check:
	Notebook does EDA to determine that  50 ml minis selling for over 10 dollars need to be excluded from the product clustering data

K means clustering of products Excludes 50 ml minis selling for over 10 dollars: 
	Notebook creates the DataFrame poor_quality consists of the excluded items and exports it. 
	It does the K-means product clustering and exports the file products_out which is used in the sub-clustering of the cluster everything_else.

K means  sub clustering  of  Everything Else  4 excludes 50 ml over 10 bucks -with graphs:

	It creates graphs.

get store information on clusters:
	It merges store and transactional data and appends cluster information and creates features using the clusters
	It creates and writes out stores_clust_info_combined2.csv to be used in further analysis
	It creates stores_in_zips to be used in the notebook, Census Combine Files_zip_level

stores_clust_info_combined2 analysis-new:
	EDA of stores_clust_info_combined2 which was created in the notebook, get store information on clusters. Notebook also creates hy_vee_liquor_or_spirit_df.csv for use in Census EDA

Percentage of revenue by category for product clusters:
	Notebook calculates percent of revenue by cateogry for each product cluster 

Kmeans Stores discovered 18 outliers: 
	Notebook is first attempt to cluster the stores using stores_clust_info_combined2.csv. 18 outliers were discovered mainly distilleries. 	
	The file stores_clust_info_combined3 was exported for use in the notebook "Kmeans Stores 18 outlier stores removed" in which the correct clustering of the stores was performed.



Kmeans Stores 18 outlier stores removed:
	Notebook clusters the stores, EDA on stores in clusters, graphs, writes out store_counts_df for use in Census EDA, writes out stores_clust_info_combined4 for use in agglomerative clusetering

agglomerative clustering of stores:
	Notebook clusters using hierarchical clustering to cluster the stores, but the silhouette scores are not as high as K-means.

Census DP05 Gender and Age:
	reads in Census data on Gender and Age, it extracts the needed information and creates dp05_pop_gender_age_estimates which is used in the notebook, Census Combine Files_zip_level.
	It also creates a file of just the zip codes and the respective population called pop_per_zip_df for mapping purposes

Census DP04 Own,Rent Status, Home Market Value:
	reads in Census data on housing, extracts needed information and creates dp04_new_housing which is used in the notebook, Census Combine Files_zip_level.

Census DP03  Occupation and Income:
	reads in Census data on occupation, extracts needed information and creates income_in_2020_inflation_adjusted_dollars which is used in the notebook, Census Combine Files_zip_level.

Census Education and Marital Status:
	reads in Census data and extracts education and marital status information and creates dp02_select_marital_edu which is used in the notebook, Census Combine Files_zip_level.

2015 Census DP05 Gender and Age:
	reads in Census data from 2015 extracts needed information and creates dp05_2015_pop_median_age_estimates which is used in the notebook, Census Combine Files_zip_level.

Census Combine Files_zip_level:
	pulls all Census data together as well as the post office data base (which has the primary city and county associated with each zip code) and the number of stores in each zip code.