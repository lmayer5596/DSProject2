# DSProject2 

A Python/Pandas script that analyzes the dataset of Taylor Swift songs pulled from Spotify's API 

Dataset: 'https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2023/2023-10-17/taylor_all_songs.csv' 


# Introduction
Taylor Swift is that rarest of pop phenomena: a superstar who managed to completely cross over from country to the mainstream, becoming an enduring pop culture icon and conquering the world in the process. Swift shed her country roots like they were a second skin, revealing that she was perhaps the savviest populist singer/songwriter of her generation, one who could harness the zeitgeist, make it personal and, just as impressively, perform the reverse. 


# Progress
In this project, we will analyze an imported dataset from Spotfiy's API on Swift's discography. From the raw data, we have decided to extract information regarding the ratings of the artist's songs and albums whether it is on danceability, accousticness, etc. 

Our chosen topic holds significant importance in our current times and society, as Swift is a major force within the music industry and other sectors as well. It also holds benefits for those wanting to explore in-depth knowledge of how music streaming services, such as Spotify, input billions of songs into Hadoop-based data lakes and run multiple complex analyses of specific elements that contribute to each production. 

Delving into our queries and code, our team calculates how and why Swift's discography has become so popular with the general public by analyzing Spotify's raw dataset on danceability, energetic-ness, and accoustic-ness. We then create visual graphs to support our hypotheses and highlight the trends and statistics of her musical catalog. 

Given Swift's massive discography, from her debut in 2006 to the present day, we divided the variables into multiple subsets of the dataframe and only included specific attributes of interest. Out of all attributes, our team decided to pick out the album names, date of release, artist, featured artists, song name, danceability, energy, and accoustic. With this information, we then created 8 queries that guides us in implementing our code. 

Before going into the queries, we imported pandas and matplotlib in order code and graph visual data into the system. From there, we implemented the Spotify API dataset from github with a variable called 'data' and created another variable called 'taylor_data' in order to extract the specific attributes of interest that we defined earlier.  

# Queries
For our first two queries we wanted to find the most danceble Taylor Swift song and the most danceble Taylor Swift album. In order to do that we selected the columns track_name and dancebility from the data and sorted the data in descending order. From this we were able to select the top track by calling the head of the data and print it using the print statement.
We used this same process or the second two queries where we wanted to find the most energetic Taylor Swift song and the most energetic Taylor Siwft album. 
For the fifth query we wanted to find the correlation between dancibility and energy represented by a graph. The first two lines intialized the data for dancibility and energy ratings. After that we used matplot subplot to create and position the graph. 
For the following two queries we used the same method from the first four queries to find the most acoustic Taylor Swift song and the most acoustic Taylor Swift album. 
For the eighth query we wanted to find the trend in acousticness of Taylor Swift albums over time using a confidence interval. We selected the columns acousticness and the album release date and sorted them in ascending order. From there we used the same method as the fifth clearly and used matplot subplot to create and position the graph. 
