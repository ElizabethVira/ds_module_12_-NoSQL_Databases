# ds_module_12_-NoSQL_Databases
Homework Module 12 - PyMongo and Advanced Queries, Aggregation, Analysis, and Integration with MongoDB
=========
Objective
----
This project was done with the intention of use the NoSQL and create collections (tables) on MongoDB and import json to analyse the databases and performing queries, imported into a Jupyter Notebook, to perform data analysis, based on the following description:

The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

![alt text](./images/what_is_NoSQL.jpg)

Part 1: Database and Jupyter Notebook Set Up
===
Use NoSQL_setup_starter.ipynb for this section of the challenge.
---
1. Import the data provided in the establishments.json file from your Terminal. Name the database uk_food and the collection establishments. Copy the text you used to import your data from your Terminal to a markdown cell in your notebook.

2. Within your notebook, import the libraries you need: PyMongo and Pretty Print (pprint).

3. Create an instance of the Mongo Client.

4. Confirm that you created the database and loaded the data properly:

    - List the databases you have in MongoDB. Confirm that uk_food is listed.
    - List the collection(s) in the database to ensure that establishments is there.
    - Find and display one document in the establishments collection using find_one and display with pprint.

5. Assign the establishments collection to a variable to prepare the collection for use.

![alt text](./images/MongoDB_NoSQL.PNG)

Part 2: Update the Database
===
Use NoSQL_setup_starter.ipynb for this section of the challenge.
---

The magazine editors have some requested modifications for the database before you can perform any queries or analysis for them. Make the following changes to the establishments collection:

1. An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked you to include it in your analysis. Add the following information to the database:

![alt text](./images/dictionary_to_add_new_restaurant.PNG)

2. Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the BusinessTypeID and BusinessType fields.

3. Update the new restaurant with the BusinessTypeID you found.

4. The magazine is not interested in any establishments in Dover, so check how many documents contain the Dover Local Authority. Then, remove any establishments within the Dover Local Authority from the database, and check the number of documents to ensure they were deleted.

5. Some of the number values are stored as strings, when they should be stored as numbers.
    - Use update_many to convert latitude and longitude to decimal numbers.
    - Use update_many to convert RatingValue to integer numbers.

Part 3: Exploratory Analysis
===
Use NoSQL_analysis_starter.ipynb for this section of the challenge.
---
Eat Safe, Love has specific questions they want you to answer, which will help them find the locations they wish to visit and avoid.

Some notes to be aware of while you are exploring the dataset:

- RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.
    - Note: This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating. We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.

- The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.

Use the following questions to explore the database, and find the answers, so you can provide them to the magazine editors.

Unless otherwise stated, for each question:

- Use count_documents to display the number of documents contained in the result.

- Display the first document in the results using pprint.

- Convert the result to a Pandas DataFrame, print the number of rows in the DataFrame, and display the first 10 rows.

1. Which establishments have a hygiene score equal to 20?

2. Which establishments in London have a RatingValue greater than or equal to 4?

    Hint: The London Local Authority has a longer name than "London" so you will need to use $regex as part of your search.

3. What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

    Hint: You will need to compare the geocode to find the nearest locations. Search within 0.01 degree on either side of the latitude and longitude.

![alt text](./images/lat_&_long_Penang_Flavours.PNG)

4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.

    Hint: You will need to use the aggregation method to answer this.

    The first 5 rows of your resulting DataFrame should look something like this:

![alt text](./images/establishments_with_0_hygiene.PNG)

