# TF-IDF Vectorizing
---

## Importing Libraries

The following libraries are imported in this program:

- **TfidfVectorizer**: This library is imported from the `sklearn.feature_extraction.text` module. It implements the Term Frequency-Inverse Document Frequency (TF-IDF) algorithm, which is commonly used to measure the importance of each word in a document.

- **pandas**: This library is used for data manipulation and analysis in a tabular format.

- **math**: The `ceil` function from this module is used later in the code to round up a decimal number to the nearest integer.

- **re**: This module provides regular expression support for pattern matching and text manipulation.

- **csv**: This module is built-in to Python and provides functionality to read from and write to CSV files.

- **train_test_split**: This function is imported from the `sklearn.model_selection` module. It is commonly used to split a dataset into training and testing subsets for machine learning models.


## Creating dataframe using pandas

- **Loading the CSV**: The CSV file is loaded using the `read_csv()` function from the pandas library.

- **Cleaning the Data**: The missing values in the content column are filled using the forward fill method. The content column is then extracted from the dataframe.

- **Data Manipulation**: The title column is removed from the dataframe using the `drop()` function. The 'content' column is then renamed to 'original_content' using the `rename()` function. Three new columns, 'new_content', 'removed_lines' and 'top_sentence_tf_idf', are added to the dataframe using the `insert()` function.

- **Printing the Contents**: The contents of the 'content' column are printed using the `print()` function.


## Data cleaning and sentence summarization

- For each item in the "contents" list, the code applies regular expression (regex) operations to clean the text data by replacing bad characters with their actual counterparts, removing special characters, and replacing double whitespaces with periods. 

- The sentences in the cleaned text data are then split into individual sentences, and the TF-IDF algorithm is applied using the `TfidfVectorizer()` function from the `sklearn.feature_extraction.text` module to calculate the importance of each sentence in the document.

- The sentences are then ranked based on their TF-IDF scores, and the top 10% of the sentences are selected as the most important sentences in the document. The remaining sentences are stored as removed lines. 

- The code then generates a summary of the text using the selected sentences, and the removed lines are also stored. The summary and removed lines are inserted into the new_content and removed_lines columns of the DataFrame, respectively.

- The TF-IDF score of the top sentence is also stored in the top_sentence_tf_idf column of the DataFrame.

- Finally, the code returns the DataFrame with the new columns added and the text data summarized and cleaned.


## Saving to csv

- The `to_csv()` function of the pandas module is used to save the dataframe to a new csv file, namely 'cleaned_news_set.csv'.

- The `index=False` parameter is used to avoid saving the index column of the dataframes.


## Making a train-test split

- The `train_test_split()` function from the `sklearn.model_selection` module is used to split the data into training and testing sets. The function takes the data and the size of the testing set as input and returns two separate datasets for training and testing.

- In this case, the testing set is 10% of the total dataset, which is specified using the `test_size` parameter. The `random_state` parameter is set to a fixed value to ensure that the same split is obtained every time the code is run.

- Finally, the code saves the training and testing sets as separate CSV files using the `to_csv()` function provided by pandas.