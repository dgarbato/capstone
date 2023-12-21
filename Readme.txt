-----------------------------------------------------------------------------------------------------
NOTE: All notebook names are in quotes to make things easier to read.  All csv files have underscores.
----------------------------------------------------------------------------------------------------



"read  and write out  seperate files for 2017 to 2022":
	Notebook that extracts 2021 data from Iowa_Liquor_Sales (initally other years were pulled too, but they were not used in the project and are commented out) 
	writes out liquor_2021 

	

"Liquor 2021 cleaned": 
	Notebook  reads in the files, liquor_2021 and Iowa_Liquor_Products
	It  cleans up and creates csv files for use in the project: transactions_2021, products_2021, stores_2021, vendors_2021, catefories_2021, product_proof

	
"Combine Categories": Notebook consolidates category names. It reads in catefories_2021, products_2021. It writes out  categories, categories_items
	
"create data for  product clustering":
    	Notebook reads in transactions_2021, products_2021,
	Notebook name is self explanatory
    
	It writes out clustering_data_num_unique_stores

"data quality check":
	Notebook does EDA to determine that  50 ml minis selling for over 10 dollars need to be excluded from clustering_data_num_unique_stores

"K means clustering of products Excludes 50 ml minis selling for over 10 dollars":
	Notebook name is self explanatory
	it reads in clustering_data_num_unique_stores, categories_items
	It writes out poor_data_quality_items,kmeans_outliers  for use in "get store information on clusters"
	
	It writes out  product_clusters for use in the sub-clustering of Everything Else

"K means  sub clustering  of  Everything Else  4 excludes 50 ml over 10 bucks -with graphs":
	Notebook reads in product_clusters 
	It does sub-clustering of Everything Else
	It writes out final_clusters for use in notebooks: "get store information on clusters" and "Percentage of revenue by category for product clusters."
	
	

"get store information on clusters":
	Notebook merges store and transactional data and appends cluster information and creates features using the clusters which are later used in clustering the stores.
	It reads in: final_clusters, poor_data_quality_items, kmeans_outliers, transactions_2021, stores_2021
	It creates and writes out stores_clust_info_combined2 to be used in "stores_clust_info_combined2 analysis-new" and "Kmeans Stores discovered 18 outliers"
	It writes out stores_in_zips to be used in the notebook, "Census Combine Files_zip_level"

"stores_clust_info_combined2 analysis-new":
	EDA of stores_clust_info_combined2 which was created in the notebook, "get store information on clusters". Notebook also writes out hy_vee_liquor_or_spirit_df.csv for use in Census EDA

"Percentage of revenue by category for product clusters":
	Notebook calculates percent of revenue by cateogry for each product cluster and creates graphs
	It reads in final_clusters, transactions_2021, stores_2021 

"Kmeans Stores discovered 18 outliers": 
	Notebook reads in stores_clust_info_combined2
	Notebook is first attempt to cluster the stores using stores_clust_info_combined2. 18 outliers were discovered mainly distilleries. 	
	It writes out  stores_clust_info_combined3 for use in the notebook "Kmeans Stores 18 outlier stores removed" in which the  clustering of the stores was performed.



"Kmeans Stores 18 outlier stores removed":
	Notebook reads in stores_clust_info_combined3 
	Notebook clusters the stores, EDA on stores in clusters, graphs, 
	writes out stores_clust_info_combined4 for use in "agglomerative clustering of stores"  
	writes out stores_clust_info_combined5__ which was not used anywhere.
	writes out store_counts_df for use in "EDA Census data Newest Most recent"

"agglomerative clustering of stores":
	Notebook read in stores_clust_info_combined4 
	Notebook clusters using hierarchical clustering to cluster the stores, but the silhouette scores are not as high as K-means.

"Census DP05 Gender and Age":
	reads in Census data on Gender and Age, it extracts the needed information and writes out dp05_pop_gender_age_estimates which is used in the notebook, "Census Combine Files_zip_level".
	It also creates a file of just the zip codes and the respective population called pop_per_zip_df for mapping purposes

"Census DP04 Own,Rent Status, Home Market Value:"
	reads in Census data on housing, extracts needed information and writes out dp04_new_housing which is used in the notebook, "Census Combine Files_zip_level".

"Census DP03  Occupation and Income":
	reads in Census data on occupation, extracts needed information and writes out income_in_2020_inflation_adjusted_dollars which is used in the notebook, "Census Combine Files_zip_level".

"Census Education and Marital Status":
	reads in Census data and extracts education and marital status information and writes out dp02_select_marital_edu which is used in the notebook, "Census Combine Files_zip_level".



"2015 Census DP05 Gender and Age":
	reads in Census data from 2015 extracts needed information and writes out dp05_2015_pop_median_age_estimates which is used in the notebook,"Census Combine Files_zip_level".

"Census Combine Files_zip_level":
	reads in: dp05_pop_gender_age_estimates, dp04_new_housing, income_in_2020_inflation_adjusted_dollars, dp05_2015_pop_median_age_estimates, stores_in_zips, dp02_select_marital_edu, land_area_census 
	It also reads in the post office database 
	pulls all Census data together as well as the post office data base (which has the primary city and county associated with each zip code) and the number of stores in each zip code.
	writes out census_combined4


"EDA Census data Newest  Most recent":
	EDA on census data
	reads in census_combined4, hy_vee_liquor_or_spirit_df, store_counts_df,  
	write out census_combined5

"geopandas-zips":

	reads in transactions_2021, stores_2021, census_combined5 
	reads in US zip code shape file, tl_2020_us_zcta520.shp
	creates maps of Iowa at zip level
	writes out land_area_census with land area by zip code for use in "Census Combine Files_zip_level"
