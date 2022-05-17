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
	Notebook creates sub-clusters of everything_else.  Once the sub-clusters are created it unites them with the three other clusters of the products to form seven clusters.
	It writes out final_clusters to be used for further analysis.
	It creates graphs.

get store information on clusters:
	Notebook merges final_clusters with the transactions_2021 and stores_2021 to create the DataFrame store_trans_cluster which to be used in additional analysis.
	It creates and writes out stores_clust_info_combined2 to be used in further analysis
	It creates stores_in_zips to be used in the notebook, Census Combine Files_zip_level

Kmeans Stores discovered 18 outliers: 
	Notebook is first attempt to cluster the stores using stores_clust_info_combined2. 18 outliers were discovered mainly distilleries. 	
	The file stores_clust_info_combined3 was exported for use in the notebook "Kmeans Stores 18 outlier stores removed" in which the correct clustering of the stores was performed.



	