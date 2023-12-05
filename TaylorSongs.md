# Lily Mayer
Code development and implementation. Also, helped to create more sophisticated queries and implement them. Developed and expanded the script with members and reviewed the final results 

# Gina Seo
Worked with other members to create the code outline. Also helped contribute to finalizing SQL queries. Developed a good work ethic and management with the other teamates.

# Jesigga Sigurdardottir 
Found and finalized dataframe, finalized formating, created questions, and worked on explenations of wuestions.

# Kiley Wonser
Helped to create slightly more sophisticated questions. Developed and expanded the descriptions with members and reviewed the final results with the team.

```python
import pandas as pd
import matplotlib.pyplot as plt


```

Read in dataset from Github
```python
#reads in dataset fron github
data = pd.read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2023/2023-10-17/taylor_all_songs.csv')
```
Subsets of the dataframe with the attributes that we will use.
```python
#subsets the dataframe to only attributes of interest
taylor_data = data[['album_name', 'album_release', 'artist', 'featuring', 'track_name', 'danceability', 'energy', 'acousticness']]
print(taylor_data)
```

# Questions:
# 1. What is the most danceable song?
 Spotify's API takes in all the elements that went into creating a song and gives it a score from 0.0 to 1.0 on how "danceable" it is. Based on the how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity

 ```python
#Question 1: What is the most danceable song?
dancing = taylor_data[['track_name', 'danceability']].sort_values('danceability', ascending=False)
dancing_max = dancing.head(1)
print(dancing_max)
```
Observe that the track 'I Think He Knows' is the most danceable song with a danceability of 0.897


# 2. What is the most danceable album? 
 Out of all the songs that were released from 2006 to 2023, this only takes in songs that were released as part of an album while excluding any songs that are not part of the main albums. This would mean that it takes in the average danceability score from each album and compare it to scores from other albums

 ```python
#Question 2: What is the most danceable album on average?
dancing_albums = taylor_data[['album_name', 'danceability']].groupby(['album_name'])
dancing_albums_sorted = dancing_albums.first().sort_values('danceability', ascending=False)
dancing_albums_max = dancing_albums_sorted.head(1)
print(dancing_albums_max)
```
Observe that the album '1989' is the most danceable album with an average danceability of 0.789


# 3. What is the most energetic song?
Based on perceptual measure of intensity and activity between 0.0 and 1.0 typically sounding more fast, loud, and noisy with more energy.

```python
#Question 3:  What is the most energetic song?
energy = taylor_data[['track_name', 'energy']].sort_values('energy', ascending=False)
energy_max = energy.head(1)
print(energy_max)
```
Observe that the track 'Haunted' is the most energetic song with a energy level of 0.95

# 4. What is the most energetic album on average?
Based on perceptual measure of intensity and activity between 0.0 and 1.0 typically sounding more fast, loud, and noisy with more energy, these values are taken by the average of all the songs on the album.

```python
#Question 4: What is the most energetic album on average?
energy_albums = taylor_data[['album_name', 'energy']].groupby(['album_name'])
energy_albums_sorted = energy_albums.first().sort_values('energy', ascending=False)
energy_albums_max = energy_albums_sorted.head(1)
print(energy_albums_max)
```
Observe that the album 'Red' is the most energetic album with an average energy level of 0.825

# 5. How does energy correlate to danceability?
Making a graph to see the trend of dancebility vs. energy for each song.

```python
#Question 5: How does energy correlate to danceability?
energy_lst = pd.DataFrame(energy)['energy'].tolist()
dancing_lst = pd.DataFrame(dancing)['danceability'].tolist()
plt.subplot(3, 1, 1)
plt.scatter(energy_lst, dancing_lst)
plt.title("Energy vs. Danceability")
plt.xlabel("Energy")
plt.ylabel("Danceability")
```
Observe that the energy and danceability are almost linearly related. As energy of the song increases, so the the danceability.


# 6. What is the most acoustic song?


```python
#Question 6: What is the most acoustic song?
acoustic = taylor_data[['track_name', 'acousticness']].sort_values('acousticness', ascending=False)
acoustic_max = acoustic.head(1)
print(acoustic_max)
```
Observe that the track 'It's Nice To Have A Friend' is the most acoustic song with an acousticness of 0.971

# 7. What is sthe most acoustic album?


```python
#Question 7: What is the most acoustic album?
acoustic_albums = taylor_data[['album_name', 'acousticness']].groupby(['album_name'])
acoustic_albums_sorted = acoustic_albums.first().sort_values('acousticness', ascending=False)
acoustic_albums_max = acoustic_albums_sorted.head(1)
print(acoustic_albums_max)
```
Observe that the album 'evermore' is the most acoustic album with an average acousticness of 0.833

# 8. What is the trend in acousticness over time?

```python
#Question 8: What is the trend in acousticness over time?
acoustic_release = taylor_data[['album_release', 'acousticness']].dropna().sort_values('album_release', ascending=True)
album_release_dates = pd.DataFrame(acoustic_release)['album_release'].tolist()
acousticness_values = pd.DataFrame(acoustic_release)['acousticness'].tolist()
```
