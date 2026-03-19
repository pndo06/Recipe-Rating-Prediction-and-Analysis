# What Makes a Recipe Highly Rated
by Phuong Do (pndo@ucsd.edu)

# Introduction
In this project, I'm working with the Recipes and Ratings datasets. These datasets contain recipes and ratings from food.com, and contain information including things like ingredients, preparation steps, nutritional values, and user ratings of different recipes. The question that my project is centered around is: What types of recipes tend to have higher average ratings? These datasets allow me to explore what factors might make a recipe highly rated by users. Also, my question is both important and useful because it helps us understand what makes a recipe popular to others, so that it can help recipe creators to create better recipes that are more likely to receive higher ratings, which is why readers should care about my datasets and question. In the Recipes and Ratings datasets, the Recipes dataset has 83782 rows and the Ratings dataset has 731927 rows. The relevant columns in those datasets are 'rating' (rating given for recipe), 'nutrition' (nutrition information of recipe, includinh things like calories, total fat, sugar, sodium, protein, saturated fat, and carbs), 'n_steps' (number of steps in recipe), 'description' (user-provided description of recipe), 'n_ingredients' (number of ingredients in recipe), and 'minutes' (number of minutes to prepare recipe).

# Data Cleaning and Exploratory Data Analysis
The data cleaning steps I took before doing any analysis are merging datasets, handling missing values, computing the average rating for each recipe, and converting the 'nutrition' column. 

I first merged the Recipes dataset and Ratings dataset together to get a single dataframe that has both the recipes and their corresponding ratings. This is a crucial first step for my analysis because by combining the two datasets, I will be able to analyze how recipe features (number of steps, number of ingredients, etc), are related to ratings. Since the Recipes and Ratings datasets were stored separately at first, it would not be possible to perform any analysis on the recipe features and the recipes' ratings without merging the two datasets together. 

Next, I handled missing values by replacing 0 ratings with NaN in the 'rating' column because there are recipes that don't receive a rating. This is an important step for my analysis because 0s represent missing ratings in the 'rating' column, not actual user ratings. So this step ensures that missing values are ignored by replacing with NaN when computing average ratings, for example, to avoid inaccurate analysis because keeping the 0s would lower the average ratings, which makes it seem like some recipes have bad ratings when in reality it's just that they didn't receive a rating. 

After this, I computed the average rating for each recipe by grouping the resulting merged dataframe by the recipe ID and taking the mean of user ratings. This step combines and averages multiple ratings per recipe into a single rating value per recipe so that each recipe gets one average rating, making the data nice and clean for analysis. 

Lastly, I converted the 'nutrition' column and created new separate columns for each nutritional category from the original 'nutrition' column. The 'nutrition' column was originally stored as strings that look like lists containing multiple values corresponding to different nutritional values (calories, sugar, carbs, etc). So by converting the 'nutrition' column into separate columns containg numeric values for each nutritional category, it makes it so much easier to do analysis on how different nutritional components are related to recipe ratings.

Here's my cleaned recipes dataframe:
<iframe
  src="assets/clean_recipes_df.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


This histogram shows the distribution of average recipe ratings. Most ratings seem to be concentrated between ratings 4 and 5, especially rating 5 where it has the most recipes, indicating that most recipes receive very high ratings, with very few recipes with low ratings.
<iframe
  src="assets/avg_rating_per_recipe.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
This scatter plot shows the relationship between the average rating of recipes and the number of steps. There seems to be a pretty positive relationship between the two features, as recipes with higher average ratings seem to have higher number of steps as well. 
<iframe
  src="assets/avg_rating_vs_n_steps.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
This table shows the average ratings of recipes and number of recipes grouped by the number of steps. While it looks like higher number of steps do have higher ratings, those groups have very few recipes shown in the 'count' column compared to groups with fewer number of steps. It would be more reliable if there are more recipes for the higher number of steps. Therefore, we can't say that there's a strong positive relationship between average ratings and the number of steps. This table helps us understand that the number of steps might not be a strong predictor of recipe ratings and that other features might be more important for later analysis and modeling.
<iframe
  src="assets/grouped_table.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
