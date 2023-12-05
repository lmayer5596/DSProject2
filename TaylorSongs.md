```python
import pandas as pd
import matplotlib.pyplot as plt


```


```python
#reads in dataset fron github
data = pd.read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2023/2023-10-17/taylor_all_songs.csv')

#subsets the dataframe to only attributes of interest
taylor_data = data[['album_name', 'album_release', 'artist', 'featuring', 'track_name', 'danceability', 'energy', 'acousticness']]
print(taylor_data)
```

#Questions:
#1: What is the most danceable song?
#1: What is the most danceable song? (Spotify's API takes in all the elements that went into creating a song and gives it a score from 0.0
 to 1.0 on how "danceable" it is)
#2: What is the most danceable album on average? (Out of all the songs that were released from 2006 to 2023, this only takes in songs
 that were released as part of an album while excluding any songs that are not part of the main albums. This would mean that it takes
 in the average danceability score from each album and compare it to scores from other albums)
#3: What is the most energetic song?
#4: What is the most energetic album on average?
#5: How does energy correlate to danceability?
#6: What is the most acoustic song?
#7: What is sthe most acoustic album?
#8: What is the trend in acousticness over time?


```python
#Question 1: What is the most danceable song?
dancing = taylor_data[['track_name', 'danceability']].sort_values('danceability', ascending=False)
dancing_max = dancing.head(1)
print(dancing_max)
#Observe that the track 'I Think He Knows' is the most danceable with a danceability of 0.897
```


```python
#Question 2: What is the most danceable album on average?
dancing_albums = taylor_data[['album_name', 'danceability']].groupby(['album_name'])
dancing_albums_sorted = dancing_albums.first().sort_values('danceability', ascending=False)
dancing_albums_max = dancing_albums_sorted.head(1)
print(dancing_albums_max)
#Observe that the album '1989' is the most danceable with an average danceability of 0.789
```


```python
#Question 3:  What is the most energetic song?
energy = taylor_data[['track_name', 'energy']].sort_values('energy', ascending=False)
energy_max = energy.head(1)
print(energy_max)
#Observe that the track 'Haunted' is the most energetic with a energy level of 0.95
```


```python
#Question 4: What is the most energetic album on average?
energy_albums = taylor_data[['album_name', 'energy']].groupby(['album_name'])
energy_albums_sorted = energy_albums.first().sort_values('energy', ascending=False)
energy_albums_max = energy_albums_sorted.head(1)
print(energy_albums_max)
#Observe that the album 'Red' is the most energetic with an average energy level of 0.825
```


```python
#Question 5: How does energy correlate to danceability?
energy_lst = pd.DataFrame(energy)['energy'].tolist()
dancing_lst = pd.DataFrame(dancing)['danceability'].tolist()
plt.subplot(3, 1, 1)
plt.scatter(energy_lst, dancing_lst)
plt.title("Energy vs. Danceability")
plt.xlabel("Energy")
plt.ylabel("Danceability")
#Observe that the energy and danceability are almost linearly related. As energy of the song increases, so the the danceability.
```


```python
#Question 6: What is the most acoustic song?
acoustic = taylor_data[['track_name', 'acousticness']].sort_values('acousticness', ascending=False)
acoustic_max = acoustic.head(1)
print(acoustic_max)
#Observe that the track 'It's Nice To Have A Friend' is the most acoustic with an acousticness of 0.971
```


```python
#Question 7: What is the most acoustic album?
acoustic_albums = taylor_data[['album_name', 'acousticness']].groupby(['album_name'])
acoustic_albums_sorted = acoustic_albums.first().sort_values('acousticness', ascending=False)
acoustic_albums_max = acoustic_albums_sorted.head(1)
print(acoustic_albums_max)
#Observe that the album 'evermore' is the most acoustic with an average acousticness of 0.833
```


```python
#Question 8: What is the trend in acousticness over time?
acoustic_release = taylor_data[['album_release', 'acousticness']].dropna().sort_values('album_release', ascending=True)
album_release_dates = pd.DataFrame(acoustic_release)['album_release'].tolist()
acousticness_values = pd.DataFrame(acoustic_release)['acousticness'].tolist()
```