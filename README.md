# MICROSOFT MOVIES DEVELOPEMENT.
![download](https://user-images.githubusercontent.com/104550900/169835936-6aac7c8d-ea8f-4050-ad73-92465aa8cb78.png)

Analyst : Iyantom Ogari Juma.



## Project Description

Microsoft had announced they wanted to create a movie studio, but had no knowledge of the movie industry.This is where we come in our objectives we are to collect or use available data, clean it and make an analysis from the different sources of our data, and provide a recommendation to Microsoft that will draw insights for success in the movie industry.

### Data collection
Data for this project was provided by Moringa institution were from

Box Office Mojo. 
IMDB.
Rotten Tomatoes.
TheMovieDB. 
The Numbers.

### Insight Querries.

* In our analysis we looked at the following insights:
1. Which are the highest rated movies and how does it equate to the number of reviews votes by the public ?
2. What are the most profitable movies and what is their movie making budget ?
3. which movie studios gross the highest profit and which gross the highest profit margin ?

## Insight querry 1: Which are the higest rated movies and how does it correlate with the number of reviews votes?
To have an insight on the question we used the following `title basics` and `ratings` dataframes.
Merging the data in the dataframes to provide a joint dataframe that we found the mean that we used as a filter to find data above the mean also sorting the data enabling us to plot this scatter plot.
 ```python
# finding votes greater than the mean
movie_rating_df = merged_df[merged_df['numvotes'] >3524]
movie_rating_df.head()
```
```python
# sort the movies by ratings
ranked_movies_df = movie_rating_df.sort_values(by= ['numvotes'], ascending= False)
ranked_movies_df.head()
```
The scatter plot will show me the correlation between the number of votes casted and the rating of the movies.

![movierating](https://user-images.githubusercontent.com/104550900/169833377-a93457a7-a6f2-4ae7-abac-7f0bbfeed222.png)


The positive trendline shows that the higher the number of votes the higher the quality of the rating of movie.

**Conclusion** This show that the highest rated movies were exposed to to plenty of viewers who gave their review in form of a vote as shown in the scatter plot thus for a movie to have a high quality rating, Microsoft should expose it to the public as much as possible using advertisemnts so that they could rate the quality of the movies they produce.
## 2nd Insight : What is the budget of the most profitable movies ?


For profits we need we need the `budget_df` data and the `total_gross` data so as to calculate the profits from each movie.
This can be calculated by `Profit` = `worldwide_gross` - `production_budget`.
```python
# creating and calculating the profit column.
budget_df['profit'] = budget_df['worldwide_gross'] - budget_df['production_budget']

```
Sorting the data for plotting
```python
 sorting the profit column.
# ensuring no profit budget equal to 0 which will be an outlier
profitable_movies = budget_df.loc[budget_df['profit'] > 0]
# ranking the values with the highest profit.
profitable_ranked_df = profitable_movies.sort_values(by=['profit'], ascending=False)
# reset the index
profitable_ranked_df.reset_index(inplace=True)
profitable_ranked_df.head()
```
Lets plot a graph of profit aganist the budget for the movies using seaborn libraries.
![budgetprofit](https://user-images.githubusercontent.com/104550900/169835013-b5550d57-4514-49e8-a480-7ad84685df08.png)


The positive trend line shows that increase in budget will lead to increase in the profits of the movie produced. As shown in the scatter plot.


Getting the top 30 movies and finding their average profit and budget by filtering the data from production budget and profit.

![profit_bud_bar](https://user-images.githubusercontent.com/104550900/169835114-d25d152c-0dcf-4004-a22f-32dd9774c87f.png)

**Conclusion:** For Microsoft Studios to produce a good movie they need a budget of atleast **$ 187,738,700** million .

Which will achieve a profit of **$ 1,160,262,000**.  Which will be a Billion dollars with some change!!
## 3rd Insight: Which Studios grossed the highest profits?
We import the data from the `title gross` and `profitable ranked df` created from previous analysis.Convert the required columns datatypes to be uniform in form of datatypes then merging the data to create the `studio_gross` dataframe.
Calculation of profit margin
```python
# #Calculate the Profit Margin

studio_gross['profit_margin'] = studio_gross['profit'] / studio_gross['worldwide_gross']
```
group the data by studio using profit and profit margin mean to sort the data from the largest to the smallest sample.
```python
# sorting the data to get the profit per studio.

studio_profit_df = studio_gross.groupby('studio', as_index=False)[['profit', 'profit_margin']].mean().sort_values(by='profit', ascending=False)
```
sorting the data to get the values of profits larger than the mean so as to get the top studios.
ploting the graph of profit aganist studios.
![studiorating](https://user-images.githubusercontent.com/104550900/169835273-d5bd252c-46c3-4e4a-aaea-f845915f37bc.png)

Looking at the bargraph we can see the top studios based on the amount of profits that they make this will enable Microsoft to make a descion on the best studios to work with with the top being Uni. for Universal studios.

Lets check the profit margin of the top studios.By plotting a graph of studios aganist profit margin.
![Profitmargin](https://user-images.githubusercontent.com/104550900/169832630-c4deb885-f52b-48df-8570-7c44c6d8790e.png)

**Conclusion:**  Based on profit margin we can see that  the top studios with the best profit margins  which include Fox Studos and Universal Studios having the highest profit margin thus Microsoft can decide to contract them in movie production or collaborations.

## Acknowledgments

My Technical Mentors :
Antonny Muiko,
Terry Migwi,
Mark Tiba.
