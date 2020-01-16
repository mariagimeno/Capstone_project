# CAPSTONE PROJECT – BLIND WINE TASTING 

This is my Capstone Project as part of the General Assembly Data Science Immersive Course

## GOAL

This project was inspired by my previous work, in food production. I decided to further extend my knowledge in this area by creating a model that is able to predict wine metadata (country, province and variety) based on the description of the wine given by a professional master. I used Web-Scraping techniques to collect data followed by some feature engineering. I worked with Natural Language Processing to build and compare some classification models to try to get the best accuracy score. I compared Logistic Regression, Random Forest and Naive Bayes models and increased accuracy 72% over the baseline where the target was the country, 40% where province was the target and 55% where the variety of the wine was the target. 



## DATASETS

There are three datasets, that I am going to use to analyze:

- "Small Wine Dataset", that initially contains the 37803 rows and 13 columns. This data was scraped from the website https://www.winemag.com/?s=&drink_type=wine&page=1
- "Big Dataset", that initially contains 141617 rows and 13 columns. This data was download form Kaggle, last actualization was in March 2019.
- "Concat Dataset": This dataset is a result of the small and big datasets union and contains 166715 rows and 12 columns.


## COLUMNS DESCRIPTIONS

These are the descripitons of the columns.

- 'country': The country that the wine is from
- 'description': A professional description of the wine
- 'designation': The vineyard within the winery where the grapes that made the wine are from. A vineyard is a plantation of grape-bearing vines, grown mainly for winemaking, but also raisins, table grapes and non-alcoholic grape juice. The science, practice and study of vineyard production is known as viticulture.
- 'points': The number of points WineEnthusiast rated the wine on a scale of 1-100 (though they say they only post reviews for wines that score >=80)
- 'price': The cost for a bottle of the wine in $
- 'province': The province or state that the wine is from
- 'region_1': The wine growing area in a province or state.
- 'region_2': Sometimes there are more specific regions specified within a wine growing area.
- 'taster_name': The name of the person who tests the wine
- 'taster_twitter_handle': I am going to drop this column
- 'title': The title of the wine review.
- 'variety': The type of grapes used to make the wine
- 'winery': The winery that made the wine
- 'vintage':The vintage year is the harvest year of the grapes from which the wine was made. This is a new column extracting from 'title' column.

## PARTS OF THE PROJECT

### SCRAPING DATA

This part of the project is formed for ['SCRAPING DATA'](SCRAPING DATA.md) file.

### CLEAN DATA

This part of the project is formed for 1 juypter notebook [“vino_clean_data_V1”](https://github.com/mariagimeno/ga_capstone_project/blob/master/vino_clean_data_V1.ipynb)


### EDA

This part of the project is formed for 2 juyper notebooks:

- ["vino_EDA_V1"](https://github.com/mariagimeno/ga_capstone_project/blob/master/vino_EDA_V1.ipynb): Contains the exploration data analysis of the small and big datasets.

- ["vino_EDA_V1-Conca"](https://github.com/mariagimeno/ga_capstone_project/blob/master/vino_EDA_V1-Conca.ipynb): Contains the exploration data analysis of the dataset that merges from the two datasets (small and big).



### FINDINGS AND TECHNICAL REPORT

For this part of the project, I created 4 jupyter notebooks:

- ["Wine_Findings_and_Technical_Report_Part_4_Country_V1"](Wine_Findings_and_Technical_Report_Part_4_country_V1.ipynb): Contains the models that I build it where the target is the country. For Small and Big datasets

- ["Wine_Findings_and_Technical_Report_Part_4_Province"](Wine_Findings_and_Technical_Report_Part_4-Province.ipynb): Contains the models that I build it where the target is the province. For Small and Big datasets

- ["Wine_Findings_and_Technical_Report_Part_4_Variety"](Wine_Findings_and_Technical_Report_Part_4-Variety.ipynb): Contains the models that I build it where the target is the variety. For Small and Big datasets

- ["Wine_Findings_and_Technical_Report_Part_4_concat"](https://github.com/mariagimeno/ga_capstone_project/blob/master/Wine_Findings_and_Technical_Report_Part_4_conca.ipynb): Contains the models that I build with the Concat data set where the target are the country, province and variety.

### PRESENTATION

The file [“Presentation_capstoneproject"](Capstone_presentation.pdf) is a short presentation with my findings and the most important insights of the project. 

### CONCLUSION

The conclusions, the improvements and learning from the project are in the ['CONCLUSIONS'](https://github.com/mariagimeno/ga_capstone_project/blob/master/CONCLUSION.md) folder. 
