# Spotify Data Analysis

Exploratory data analysis of a Spotify songs dataset in a Jupyter notebook. It looks at the audio features Spotify provides for each track and compares how they are distributed for the positive and negative classes of the dataset's `target` label, as groundwork for building a classification model later.

## Dataset

`spotify_data.csv` contains 2,017 songs from the [Spotify Song Attributes dataset on Kaggle](https://www.kaggle.com/datasets/geomack/spotifyclassification). Each row has the song title, the artist and these audio features from the Spotify Web API:

acousticness, danceability, duration_ms, energy, instrumentalness, key, liveness, loudness, mode, speechiness, tempo, time_signature and valence.

The `target` column is a binary label. In the Kaggle dataset description, 1 marks songs the dataset author liked and 0 marks songs they did not.

## What the notebook does

- Loads the CSV and checks missing values, column types, shape and summary statistics
- Finds the artists with the most tracks in the dataset
- Lists the five quietest tracks by loudness
- Lists the five most danceable songs and their artists
- Lists the five most instrumental tracks
- Plots histograms with density curves for ten audio features (tempo, loudness, acousticness, danceability, duration_ms, energy, instrumentalness, liveness, speechiness, valence), split into positive (`target = 1`) and negative (`target = 0`) songs

## Findings

These come from the notebook outputs:

- The dataset has 2,017 rows and 16 columns, with no missing values.
- Drake has the most tracks (16), followed by Rick Ross (13), Disclosure (12), Backstreet Boys (10) and WALK THE MOON (10).
- All five quietest tracks are below -29 dB, and three of them are classical pieces.
- The most danceable song is "Flashwind - Radio Edit" by Ben Remember (0.984), followed by "SexyBack" by Justin Timberlake (0.967).
- The most instrumental track is "Senseless Order" by Signs of the Swarm (0.976).
- Positive songs tend to be more danceable: their danceability peaks at around 0.73, compared with about 0.62 for negative songs.
- Negative songs include a small group of very low-energy tracks (energy below 0.2), which is almost absent from the positive class.
- Positive songs have a longer tail at higher speechiness and lean slightly towards higher valence. Features such as acousticness and instrumentalness look similar for both classes.

## Tech stack

- Python
- pandas
- Matplotlib and seaborn
- Jupyter Notebook

## Project structure

```
Spotify-Data-Analysis/
├── Spotify Project.ipynb   # analysis notebook
├── spotify_data.csv        # dataset
└── requirements.txt
```

## Getting started

```bash
git clone https://github.com/Hamza-Tahirr/Spotify-Data-Analysis.git
cd Spotify-Data-Analysis

python -m venv venv
source venv/bin/activate        # on Windows: venv\Scripts\activate

pip install -r requirements.txt
jupyter notebook "Spotify Project.ipynb"
```

The notebook reads `spotify_data.csv` from the project folder, so start Jupyter from there. seaborn is kept below 0.14 because the notebook uses `sns.distplot`, which is deprecated in newer versions.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
