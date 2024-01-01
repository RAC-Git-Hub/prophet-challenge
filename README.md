# prophet-challenge
## The Challenge
For this project, you are assuming the role of a growth analyst at Mercado
Libre. Mercado Libre is the most popular e-commerce site in Latin America with
over 200 million users. This project involves analyzing the company's financial
and user data to see if there are ways to help the company grow. To accomplish
this, you need to find out if there is an ability to predict Google internet
search traffic and if that data can be used to successfully trade the company's
stock.

The process of this exercise shall be accomplished in following four steps:
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
>   the month of May 2020. (During this month, MercadoLibre released its
>   quarterly financial results.) Visualize the results.
> 
>![8-1_output](https://github.com/RAC-Git-Hub/prophet-challenge/blob/main/8-1_output.png?raw=true)
>
>Do any unusual patterns exist?
>
>   2. Calculate the total search traffic for the month, and then compare the
>   value to the monthly median across all months.
>   3. Did the Google search traffic increase during the month that MercadoLibre
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
>   day. 
>
>![8-2_output](https://github.com/RAC-Git-Hub/prophet-challenge/blob/main/8-2_output.png?raw=true)
>
>   Does the search traffic peak at a particular time of day or is it
>   relatively consistent?
>
>   2. Group the hourly search data to plot the average traffic by the day of
>   the week (for example, Monday vs. Friday).
>
>![8-3_output](https://github.com/RAC-Git-Hub/prophet-challenge/blob/main/8-3_output.png?raw=true)
>
>   Does the search traffic get busiest on any particular day of the week?
>
>   3. Group the hourly search data to plot the average traffic by the week of
>   the year. 
>
>![8-4_output](https://github.com/RAC-Git-Hub/prophet-challenge/blob/main/8-4_output.png?raw=true)
>
>Does the search traffic tend to increase during the winter holiday
>   period (weeks 40 through 52)?
>
>   4. Are there any time based trends that you can see in the data? Write your
>   answer in the space provided in the starter file.
>
>#### Step 3: Relate the Search Traffic to Stock Price Patterns
>You mention your work on the search traffic data during a meeting with people
>in the finance group at the company. They want to know if any relationship
>between the search data and the company stock price exists, and they ask if you
>can investigate.
>
>To do so, complete the following steps:
>   1. Read in and plot the stock price data. Concatenate the stock price data
>   to the search data in a single DataFrame.
>   2. Market events emerged during the year of 2020 that many companies found
>   difficult. But, after the initial shock to global financial markets, new
>   customers and revenue increased for e-commerce platforms. Slice the data to
>   just the first half of 2020 ( 2020-01 to 2020-06 in the DataFrame), and then
>   plot the data. 
>
>![8-5_output](https://github.com/RAC-Git-Hub/prophet-challenge/blob/main/8-5_output.png?raw=true)
>
>   Do both time series indicate a common trend that’s consistent
>   with this narrative?
>
>   3. Create a new column in the DataFrame named “Lagged Search Trends” that
>   offsets, or shifts, the search traffic by one hour. Create two additional
>   columns:
>-  “Stock Volatility”, which holds an exponentially weighted four-hour rolling
>   average of the company’s stock volatility
>
>-  “Hourly Stock Return”, which holds the percent change of the company's stock
>   price on an hourly basis
>
>   4. Does a predictable relationship exist between the lagged search traffic
>   and the stock volatility or between the lagged search traffic and the stock
>   price returns? Write your answer in the space provided in the starter file.
>
>#### Step 4: Create a Time Series Model with Prophet
>Now, you need to produce a time series model that analyzes and forecasts
>patterns in the hourly search data. To do so, complete the following steps:
>   1. Set up the Google search data for a Prophet forecasting model.
>   2. After estimating the model, plot the forecast. How's the near-term
>   forecast for the popularity of MercadoLibre?
>   3. Plot the individual time series components of the model to answer the
>   following questions in the space provided in the starter file:
>-  What time of day exhibits the greatest popularity?
>-  Which day of the week gets the most search traffic?
>-  What's the lowest point for search traffic in the calendar year?
>
## Sources
The starter codes were obtained in December 2023 from the instructional staff of
the OSU AI Bootcamp and were generated by edX Boot Camps LLC.
## Collaborators
Although this project was done individually, the skillset used to complete this 
assignment is a culmination of knowledge learned in the classroom setting which
includes lecture materials, example programming from instructors, interactive
dialogue in group settings among fellow students, independent internet research,
and some general programming guidance from sources such as CoPilot and ChatGPT. 