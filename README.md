# Amazon_Vine_Analysis

## Overview

The purpose of this analysis is to analyze Amazon reviews written by members of the paid Amazon Vine program. 

> The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

<img src="https://github.com/stephperillo/Amazon_Vine_Analysis/blob/main/Resources/costume.jpg" alt="costume" width="500"/>

I chose the Pet Products reviews dataset out of approximately 50 Amazon datasets. I used PySpark to extract the dataset, transform the data, connect to an Amazon Web Services (AWS) Relational Database Service (RDS) instance, and load the transformed data into pgAdmin (ETL). Then I used Pandas to determine if there is any bias toward favorable reviews from Vine members in this dataset.

## Results

I extracted the dataset and transformed it into four DataFrames.

The following image shows the extracted data for the `customers_table`:
![customers_table.png](https://github.com/stephperillo/Amazon_Vine_Analysis/blob/main/Resources/customers_table.png)

After renaming the column, the `customers_table_df` now matches the schema for pgAdmin:
![customers_table_df.png](https://github.com/stephperillo/Amazon_Vine_Analysis/blob/main/Resources/customers_table_df.png)

`products_df`:
![products_df.png](https://github.com/stephperillo/Amazon_Vine_Analysis/blob/main/Resources/products_df.png)

<img src="https://github.com/stephperillo/Amazon_Vine_Analysis/blob/main/Resources/stroller.jpg" alt="costume" width="250"/>

`review_id_df`:
![review_id_df.png](https://github.com/stephperillo/Amazon_Vine_Analysis/blob/main/Resources/review_id_df.png)

`vine_df`:
![vine_df.png](https://github.com/stephperillo/Amazon_Vine_Analysis/blob/main/Resources/vine_df.png)

I uploaded the transformed data into the appropriate tables and ran queries in pgAdmin to confirm that the data was uploaded.

- How many Vine reviews and non-Vine reviews were there?

There were 10,215 Vine reviews and 2,633,399 non-Vine reviews for Pet Products in this dataset.

![total_reviews.png](https://github.com/stephperillo/Amazon_Vine_Analysis/blob/main/Resources/total_reviews.png)

- How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?

Out of all of the 5-star reviews, there were 4,343 Vine reviews and 1,641,210 non-Vine reviews.

5-star Vine Reviews:
![5star_vine.png](https://github.com/stephperillo/Amazon_Vine_Analysis/blob/main/Resources/5star_vine.png)

5-star non-Vine Reviews:
![5star_non-vine.png](https://github.com/stephperillo/Amazon_Vine_Analysis/blob/main/Resources/5star_non_vine.png)

- What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?

42.52% of Vine reviews were 5 stars and 62.32% of non-Vine reviews were 5 stars.

## Summary

Is there any positivity bias for reviews in the Vine program?

Since the percentage of 5-star unpaid reviews is higher than the percentage of paid 5-star reviews, there is not a large amount of evidence proving extreme positivity bias. That is not to say that there is no positivity bias. 

##### Recommendations

Additional analyses that I could do with the dataset to support my statement include:
Analyzing only verified purchases using the `verified_purchases` column would also help determine the certainty of a positivity bias. 
I could also find the percentage of Vine and non-Vine reviews that are 3 and 4 star-reviews to see how those numbers compare.
