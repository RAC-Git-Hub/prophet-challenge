# prophet-challenge
## The Challenge
For this project, you are assuming the role of a growth analyst at Mercado
Libre. Mercado Libre is the most popular e-commerce site in Latin America with
over 200 million users. This project involves analyzing the company's financial
and user data to see if there are ways to help the company grow. To accomplish
this, you need to find out if there is an ability to predict Google internet
search traffic and if that data can be used to successfully trade the company's
stock.

The process of this exercise should be accomplished in four steps:
>-  Step 1: Find unusual patterns in hourly Google search traffic.
>-  Step 2: Mine the search traffic data for seasonality.
>-  Step 3: Relate the search traffic to stock price patterns.
>-  Step 4: Create a time series model with Prophet.

## Getting Started
Before starting this assignment, make sure the user has a GitHub and a Google
account. Then take the following steps:
>-  Create a new repository for this project called prophet-challenge. 
>   **Do not add this homework assignment to an existing repository.**
>-  Clone the new repository to your computer.
>-  Inside your local Git repository, add the starter files from your file 
>   downloads.
>-  Push these changes to GitHub or GitLab.
>
>You will use Google Colab to complete this challenge; make sure to download your notebook file and place it in your
repository again after completing the challenge.
>### Instructions
>#### Step 1: Find Unusual Patterns in Hourly Google Search Traffic
>The data science manager asks if the Google search traffic for the company
>links to any financial events at the company. Or, does the search traffic
>data just present random noise? To answer this question, pick out any
>unusual patterns in the Google search data for the company, and connect them
>to the corporate financial events.
>
>   To do so, complete the following steps:
>   1. Read the search data into a DataFrame, and then slice the data to just
>   the month of May 2020. (During this month,  MercadoLibre released its
>   quarterly financial results.) Visualize the results. Do any unusual patterns
>   exist?
>-  2. Calculate the total search traffic for the month, and then compare the
>   value to the monthly median across all months.
>-  3. Did the Google search traffic increase during the month that MercadoLibre
>   released its financial results? Write your answer in the space provided in
>   the starter file.
>
>#### Step 2: Mine the Search Traffic Data for Seasonality
>Marketing realizes that they can use the hourly search data, too. If they
>can track and predict interest in the company and its platform for any time
>of day, they can focus their marketing efforts around the times that have
>the most traffic. This will get a greater return on investment (ROI) from
>their marketing budget.
>
>To that end, you want to mine the search traffic data for predictable seasonal
>patterns of interest in the company. To do so, complete the following steps:
>   1. Group the hourly search data to plot the average traffic by the hour of
>   day. Does the search traffic peak at a particular time of day or is it
>   relatively consistent?
>   2. Group the hourly search data to plot the average traffic by the day of
>   the week (for example, Monday vs. Friday). Does the search traffic get
>   busiest on any particular day of the week?
>   3. Group the hourly search data to plot the average traffic by the week of
>   the year. Does the search traffic tend to increase during the winter holiday
>   period (weeks 40 through 52)?
>   4. Are there any time based trends that you can see in the data? Write your
>   answer in the space provided in the starter file.

>1. The base URL is included in the starter code, along with the search string
>and query dates. Consult the New York Times Article Search API documentation
>(https://developer.nytimes.com/docs/articlesearch-product/1/overview) to help
>you build your query_url using these variables.
>
>If you accidentally delete these variables, they are:
>
>
>![Photo_6_001](https://github.com/RAC-Git-Hub/data-sourcing-challenge/blob/main/Photo_6_001.png)
>
>
>2. Create an empty list called reviews_list to store the reviews you retrieve
>   from the API.
>3. The Article Search API limits results to 10 per page, but we want to try to
>   retrieve 200. To do this, create a for loop to loop through 20 pages
>   (starting from page 0). Inside the loop, perform the following actions:
>-  Extend the query_url created in Step 1 to include the page parameter.
>-  Make a GET request to retrieve the page of results, and store the JSON data
>   in a variable called reviews.
>-  Add a 12-second interval between queries to stay within API query limits.
>
>   **Important:** The New York Times limits requests to 500 per day and 5 per
>   minute.
>-  Write a try-except clause that performs the following actions:
>       *   try : loop through the reviews["response"]["docs"] and append each
>       review to the list, then print out the query page number (i.e. the
>       *   number of times the loop has executed).
>       *   except : Print the page number that had no results then break from
>       the loop.
>
>       **Note:** If your loop breaks at the except clause, it is possible you
>       have tried to make a request that fell outside of the rate limit. You
>       should be able to loop through all 20 pages with the provided query
>       parameters.
>4. Preview the first five results in JSON format using json.dumps with the
>   argument indent=4 to format the data.
>5. Convert reviews_list to a Pandas DataFrame using json_normalize()
>6. Extract the movie title from the "headline.main" column and save it to a new
>   column "title" . To do this, you will use the Pandas apply() method and the
>   following lambda function:
>
>
>![Photo_6_002](https://github.com/RAC-Git-Hub/data-sourcing-challenge/blob/main/Photo_6_002.png)
>
>
>This code takes the string in the cell and extracts the characters between the
>unicode quotation marks, as long as a space and the word "Review" follows the
>closing quotation mark.
>
>7. Use the supplied extract_keywords function to convert the "keywords" column
>   from a list of dictionaries to strings using the apply() method.
>8. Create a list called titles from the "title" column using to_list() . These
>   titles will be used in the query for The Movie Database.
>### Part 2: Access The Movie Database API
>Consult the Search & Query for Details documentation
>(https://developer.themoviedb.org/docs/search-and-query-for-details) to build
>your query URLs. You will be making both types of requests to extract all of
>the details you need:
>-  The search query is used to find the movie ID from the search by title. Most
>   of this query is included in your starter code, as follows, but you will
>   need to include the movie title in the query.
>
>
>![Photo_6_003](https://github.com/RAC-Git-Hub/data-sourcing-challenge/blob/main/Photo_6_003.png)
>
>
>-  The movie query is made once you have the movie ID.
>
>
>You will use the titles list created in Part 1 to perform your queries with The
>Movie Database.
>1. Create an empty list called tmdb_movies_list to store the results from your
>API requests. This will contain a list of dictionaries.
>2. Create a variable called request_counter and initialize it with the value of
>1 . This counter should do the following:
>-  Increment by one every time you iterate through the titles list.
>-  Use time.sleep(1) when it reaches a multiple of 50.
>-  Print a message to indicate that the application is sleeping.
>3. Loop through the titles list created from the movie reviews DataFrame, and
>perform the following actions:
>-  Perform the actions outlined in Step 2.
>-  Perform a GET request that sends the title to The Movie Database search and
>   retrieves the JSON results.
>-  Use a try clause that performs the following actions:
>       *    Collect the movie ID from the first result.
>       *    Make a GET request using the movie query (starting with
>       https://api.themoviedb.org/3/movie/ ) and movie ID to retrieve the full
>       movie details in JSON format.
>       *    Extract the genre names from the results into a list called
>       genres.
>       *    Extract the spoken_languages' English name from the results
>       into a list called spoken_languages.
>       *    Extract the production_countries' name from the results into a
>       list called production_countries.
>       *    Create a dictionary with the following results: title,
>       original_title, budget, original_language, homepage, overview,
>       popularity, runtime, revenue, release_date, vote_average, vote_count, as
>       well as the genres, spoken_languages, and production_countries lists you
>       just created.
>       *    Append this dictionary to tmdb_movies_list.
>       *    Print out the name of the movie and a message to indicate that
>       the title was found.
>
>-  Use the except clause to print out a statement if a movie is not found.
>4. Preview the first five results in JSON format using json.dumps with the
>argument indent=4 to format the data.
>5. Convert the results to a DataFrame called tmdb_df with pd.DataFrame() . You
>don't need to use json_normalize() this time because we don't have nested
>objects.
>### Part 3: Merge and Clean the Data for Export
>Now that you have collected the data from both APIs, you need to merge the two
>DataFrames and clean the data, then export it for future use.
>1. Merge the New York Times reviews and TMDB DataFrames on the title column.
>2. The genres, spoken_languages, and production_countries columns were saved as
>lists, but we want the columns to be strings without the list characters ( [ ,
>] , and ' ). To fix these columns, perform the following actions:
>-  Create a list of the columns that need fixing called columns_to_fix.
>-  Create a list of characters to remove called characters_to_remove.
>-  Loop through columns_to_fix and do the following:
>       *   Use astype() to convert the column to a string.
>       *   Loop through the characters_to_remove and use the Pandas
>       str.replace() method to remove the character from the string.
>-  Print the head of the updated DataFrame to confirm the list characters were
>removed.
>3. Delete any duplicate rows and reset the index.
>4. Export data to a CSV file without the DataFrame's index.
>
## Sources
The starter codes were obtained in December 2023 from the instructional staff of
the OSU AI Bootcamp and were generated by edX Boot Camps LLC.
## Collaborators
Although this project was done individually, the skillset used to complete this 
assignment is a culmination of knowledge learned in the classroom setting which
includes lecture materials, example programming from instructors, interactive
dialogue in group settings among fellow students, independent internet research,
project-specific API documentation resources, and some general programming
guidance from sources such as CoPilot and ChatGPT. 