# What is My Music Taste?
 This project used the the **Spotify API** and the spotipy package to access my own Spotify user data, and to access public data. 


## 1.1 Accessing the Spotify API Credentials Flow 

Since I am accessing my own personal data, I used my credentials that are provided by your spotify web app. For different types of access, the API requires different Scopes to be used. This will require going through the authorization flow a few times in order to collect all relevant data. The first scope I will use is "playlist-read-collaborative", which will read in all of my playlists including those that are collaborative. Next I used "user-top-read' to access my top tracks, and finally 'user-saved-tracks' for my saved tracks.

## 1.2 Audio Features
To access the audio features of each song, I used sp.audio_features and applied it to every song in my dataframe. This consisted of information such as energy, loudness, key, tempo, and more.

## 1.3 Final Dataset

- **Uri**: The Spotify URI for the track.
- **Artist**: The Artist who performed the track
- **Name**: The name of the Track
- **Popularity**:The popularity of the track. The value will be between 0 and 100, with 100 being the most popular. The popularity of a track is a value between 0 and 100, with 100 being the most popular. The popularity is calculated by algorithm and is based, in the most part, on the total number of plays the track has had and how recent those plays are.
Generally speaking, songs that are being played a lot now will have a higher popularity than songs that were played a lot in the past. 
- **Release Date**: Date of release
- **Added At**: Date saved, added to playlist, or estimated recently listening time
- **Danceability**: Danceability describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. A value of 0.0 is least danceable and 1.0 is most danceable.
- **Energy**:Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy. For example, death metal has high energy, while a Bach prelude scores low on the scale. Perceptual features contributing to this attribute include dynamic range, perceived loudness, timbre, onset rate, and general entropy.
- **Key**: The estimated overall key of the track. Integers map to pitches using standard Pitch Class notation 
- **Loudness**:	The overall loudness of a track in decibels (dB). Loudness values are averaged across the entire track and are useful for comparing relative loudness of tracks. Loudness is the quality of a sound that is the primary psychological correlate of physical strength (amplitude). Values typical range between -60 and 0 db.
- **Mode**: Mode indicates the modality (major or minor) of a track, the type of scale from which its melodic content is derived. Major is represented by 1 and minor is 0.
- **Speechiness**:	Speechiness detects the presence of spoken words in a track. The more exclusively speech-like the recording (e.g. talk show, audio book, poetry), the closer to 1.0 the attribute value. Values above 0.66 describe tracks that are probably made entirely of spoken words. Values between 0.33 and 0.66 describe tracks that may contain both music and speech, either in sections or layered, including such cases as rap music. Values below 0.33 most likely represent music and other non-speech-like tracks.
- **Acousticness**:	A confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic.
- **Instrumentalness**: Predicts whether a track contains no vocals. “Ooh” and “aah” sounds are treated as instrumental in this context. Rap or spoken word tracks are clearly “vocal”. The closer the instrumentalness value is to 1.0, the greater likelihood the track contains no vocal content. Values above 0.5 are intended to represent instrumental tracks, but confidence is higher as the value approaches 1.0. 
- **Liveness**:	Detects the presence of an audience in the recording. Higher liveness values represent an increased probability that the track was performed live. A value above 0.8 provides strong likelihood that the track is live.
- **Valence**:	A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).
- **Tempo**:The overall estimated tempo of a track in beats per minute (BPM). In musical terminology, tempo is the speed or pace of a given piece and derives directly from the average beat duration.
- **Duration**: The duration of the track in milliseconds.
- **Time Signature**: 	An estimated overall time signature of a track. The time signature (meter) is a notational convention to specify how many beats are in each bar (or measure)

## 2. Analysis
I used correlation plots, distribution comparison, standard deviations, and means comparison to look at the audio features of each song to determine any patterns in my listening history. 
*Overall Takeaways* 
- Acousticness is negatively correlated with energy and loudness
- Duration is positively correlated with instrumentalness
- Loudness and Energy are very positively correlated

Distribution Comparisons:
- Acousticness: This typically sees a distribtion that’s U shaped, with a high skew towards a 0 value that dips, and has a slight upturn at values approaching 1. My distribution is heavily skewed towards 0, signifying that I listen to less acoustic music than typically seen.
- Danceability: This typically has a normal distribution around a mean value of ~.6. My distribution is fairly normal, but slight skewed towards higher values. with a mean score of .67, signifying I listen to dancier music than normal.
- Energy: This typically has a distribution that’s somewhat uniform, while being skewed closer to values of 1. My distribution lacks that uniform aspect and has more of a bell shape, but is still skewed closer to values of 1. Thus, I listen to fewer non-energetic songs than normal.
- Instrumentalness, Liveness, Speechiness, Tempo, and Valence: All look very similar to the distributions provided by Spotify.


It seems I have a more narrow taste in music when it comes to speechiness, liveness, and danceability, than I do for other features such as instrumentalness, acousticness, or valence. It’s interesting to note that Danceability, Acousticness, and Energy were features that distinguished my taste from the distribution of music on Spotify, however of those three, danceability had a low standard deviation. Thus, the danceability of a song seems to play a very important role in how I choose music.



## 3. Conclusions and future steps
I found that Danceability and springtime were major factors in how I was choosing and listening to music! In the spring time I listened to more popular, major music, where with danceability, I listened to more dancey music than the normal distribution, and had a more narrow mindset (determined by looking at the standard deviations of each metric) when it came to danceability. 

In the future, I could read in the playlists that I frequently listen to that were out of my user scope by manually inputting playlist uris that I know from expereince are frequent in my listening history. I could also save all of my "saved tracks" to a playlist and read that in, instead of using the saved-tracks scope. This would increase the scope of my dataset to include more of the music I listen to. Additionally, implementing a reccommendation system to come up with a way to see if I would be likely to like a song, and testing it out based off of listening to that music, would be another way to make this analysis more robust.

