This is a dictionary of all the different dataframes used in this entire project, their source URLs and other important distinctions between them.

### dataset.csv

- This is the primary dataset that every other dataframe is built off of.
- **Built by:** `Dataset_Curation.ipynb`

-> UNDP Human Development Report 2025: Composite indices, complete time series (`data/HDR25_Composite_indices_complete_time_series.csv`) 

File: https://hdr.undp.org/sites/default/files/2025_HDR/HDR25_Composite_indices_complete_time_series.csv 
Download page: https://hdr.undp.org/data-center/documentation-and-downloads 

-> World Bank World Development Indicators (WDI), source ID 2 
Database: https://databank.worldbank.org/source/world-development-indicators 
API: https://api.worldbank.org/v2/ 
Python module used to import api: https://pypi.org/project/wbgapi/ 

### substituted_years.csv
- This is a csv file that contains the datapoints that were substituted back in using the lookback window
- **Built by:** `Dataset_Curation.ipynb`

-> Note: The following sets are not saved CSVs, just built everytime the code runs
### Train / Test / Validation sets (`x_trv`, `y_trv`, `x_te`, `y_te`, `x_tr`, `y_tr`, `x_v`, `y_v`)

- This is the splitting up of the primary dataset for the purpose of model fitting and evaluation
- **Built by:** `Preprocessing.ipynb`

*Key ->*
 trv: (training + validation) split
 te: test split
 tr: train split
 v: validation split

### Processed sets ('x_tr_clean', 'x_v_clean', 'x_te_clean')
- **Built by:** `Preprocessing.ipynb`
- This is the training, validation and test data after being preprocessed (imputing, OHE, missing indicators etc.)

### PCA sets
- Processed data put through Principal Component Analysis
- 'components', 'pca_data': **Built by:** `Preprocessing.ipynb` , made from x_tr_clean and x_v_clean respectively
- 'x_pca_tr', 'x_pca_v': **Built by:** `Training&Evaluation.ipynb` , made from x_tr_clean and x_v_clean 
### Feature sets

- **Built by:** `Training&Evaluation.ipynb`
- `x_num_clean`, `x_num_pca`, `x_num_v`: numerical columns only, scaled 
- `x_cat_clean`, `x_cat_pca`, `x_cat_v`: one-hot and missingness columns only, not scaled
- `x_combined_pca`, `x_combined_v`: all columns, scaled and PCA
- 'x_no_region_pca', 'x_no_region_v' : all columns except the region columns
- 'x_no_sector_pca', 'x_no_sector_v' : all columns except the dominant sector columns

-all '_v' sets are PCA on x_v_clean while (`x_num_clean`,`x_cat_clean`,`x_combined_pca`,'x_no_region_pca','x_no_sector_pca') are based on x_tr_clean
-Rest are based on x_tr_clean but also undergo PCA
