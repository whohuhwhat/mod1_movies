## Flatiron School - Data Science

# Project 1: Webscraping and the Journey for the Most Succesful Movies

#### Project Members:  Florencia Leoni and Fhel Dimaano

The objective of this project was to perform exploratory data analysis on the film industry, define measures of success for a production company, and finish with **meaningful insights** that can help the CEO of the production company make the right business decisions to achieve success.

In order to accomplish this goal we gathered data by webscrabing and making API requests from the following websites:

            1. IMDB.com *Webscraping*
            2. TMDB.com *API requests*

The functions and scripts that were used in this project are in *Python and SQLite3*; you can find a clean commented version on the **Final_Code_Notebook**. If you'd like to see how we arrived at this point, please take a look at the files in the **Archive** folder.

The information pulled from webscraping and API requests was saved in csv files for conveniency. Those files can be found in the **Data** folder.

The database that was created to answer the SQLite queries can be foiund in the **movies.db** file.

Throughout the analysis we focused on 5 main questions:

        1. What has Lionsgate (fictional client) been up to in the past few years?
        2. Is there a relationship between average revenue and the days on 
            the week/months when a movie is released?
        3. Does higher budget mean higher returns?
        4. Do popularity and vote count affect movie revenue?
        5. What should the genre of the next movie be?

**The_Movie_Project** file goes through our process of answering these questions, along with additional insights and visualizations.

### Initial analysis of relationships between the numeric variables in the dataset

Below we see a pairplot constructed using the Seaborn library. This is a useful visualization to quickly detect patterns hidden in the data.
![pairplot](https://user-images.githubusercontent.com/30739929/55332611-ba8fea00-5463-11e9-9349-2d35c28f7ec1.png)

If we further explore this relationships in a correlation matrix, we can see that there is a strong correlation between vote_count and revenue, and vote count and budget. Could this be by chance, or is there something else happening here? We can also see, as expected a strong relationship between revenue and budget, just as we saw above.
<img width="926" alt="Heat Map" src="https://user-images.githubusercontent.com/30739929/55332654-d3000480-5463-11e9-9118-4bc24cc34952.png">

Finally, we took a look at what Lionsgate has been up to the past 8 years.  The table below, produced by SQL queries, shows that Lionsgate has found past success in the Hunger Games Franchise, 3:10 to Yuma, and Abduction.
<img width="895" alt="Lionsgate" src="https://user-images.githubusercontent.com/30739929/55332665-d98e7c00-5463-11e9-9221-ec4e5691051a.png">

### A tale of days and months...
One of the first patterns we analyzed was the amount of movies released per month, the average revenue of a movie released on a specific month, and which days returned the highest mean revenue.   where a release would make the highest average revenue.
<img width="975" alt="Data Wrangling - 04 - Quantity Released per month" src="https://user-images.githubusercontent.com/30739929/55335970-25442400-546a-11e9-9e5f-be7298846979.png">
Month vs Revenue
<img width="968" alt="01 Month vs Revenue" src="https://user-images.githubusercontent.com/30739929/55335975-29704180-546a-11e9-8776-688117c0b3ef.png">
Day vs Revenue
<img width="1000" alt="02 Day vs Revenue" src="https://user-images.githubusercontent.com/30739929/55335986-2c6b3200-546a-11e9-8fdc-23e4d3716305.png">

Even though more movies are released in January, and on Fridays, data shows those days are not the ones with the highest average revenue. On the contrary, the months with the highest mean revenue are May and June, closely followed by December and April; and the days of the week with the highest mean revenue are Tuesday and Wednesday.
This data led to our **first actionable insight**:  Movies should aim for a May, June or December release as those months returned the highest average revenue.

We went back to our data to look for other relationships.

### The higher the budget, the higher the returns?
We took a look at budget vs revenue to determine if higher budget meant higher revenue.  The following linear regression graph shows that while there is a relationship, it is not a strong one.  The line is pulled by outliers in the data, rather than showing a strong linear relationship, it shows a small clustering near the origin.


<img width="838" alt="03 Higher Budget Higher Returns" src="https://user-images.githubusercontent.com/30739929/55337299-62a9b100-546c-11e9-9c4c-0eb6019602e8.png">


### Is this a popularity contest?
As per the graph below, though initially it is clustering near the origin, there is a positive linear relationship between the vote count and the revenue. Meaning that after all the movie business IS a popularity contest.
<img width="627" alt="04 Popularity vs revenue" src="https://user-images.githubusercontent.com/30739929/55337303-663d3800-546c-11e9-80c8-4cb21c69b229.png">

This data led us to our **second actionable insight**  There is a correlation between popularity and revenue.  Public awareness through traditional marketing, social media and viral marketing will increase popularity.

### What should the genre of the next movie be?
The first bar chart shows the average revenue per genre from 2010 to 2018. We can see how Westerns are considerably most succesful than the rest. However, that bar is inflated by True Grit (2012), The Revenant (2015), Django Unchained (2012), The Hateful Eight (2015), and Bone Tomahawk (2015).
<img width="824" alt="05 genre after 2010" src="https://user-images.githubusercontent.com/30739929/55338344-8968e700-546e-11e9-9e45-d403875b8e02.png">

Then we take a look at individual years. From in 2016 to 2018 the genre with the highest mean revenue was Adventure. In this period we have movies such as Allegient, for the Divergent Series (2016), Pete's Dragon (2016), Captain America: Civil War, from the Captain America Series (2016), The Magnificent Seven (2016), Wonder Women (2017), The Fate of the Furious, from the The Fast and the Furious Series (2017), Valerian and The City of a Thousand Planets (2017), and Pirates of the Caribbean: Dead Men Tell No Tales, from the Pirates of the Caribbean Series (2017), Avengers: Infinity Wars, from the Avengers Series (2018) and Ready Player One (2018).

Mean Revenue by Genre (2016)
<img width="851" alt="06 genre 2016" src="https://user-images.githubusercontent.com/30739929/55338360-9554a900-546e-11e9-918b-99588d0e4b7c.png">
Mean Revenue by Genre (2017)
<img width="827" alt="07 genre 2017" src="https://user-images.githubusercontent.com/30739929/55338361-9554a900-546e-11e9-895c-04be44dc48a6.png">

Mean Revenue by Genre (2018)
<img width="837" alt="08 genre 2018" src="https://user-images.githubusercontent.com/30739929/55338362-9554a900-546e-11e9-93d1-f433767dbf90.png">

What do these have in common?  Our ***third actionable insight*** data finds that the trendiest genre is Adventure with the subgenres of superheroes, franchises, and futurism returning the highest mean revenue and popularity.

<img width="1439" alt="Screen Shot 2019-04-01 at 11 14 28 AM" src="https://user-images.githubusercontent.com/30739929/55338753-5a9f4080-546f-11e9-89a4-d44f20b37f00.png">
