# Data

Raw datasets are not included in this repository because of their size.

## Expected local structure

Place the following files under `data/raw/` before running the notebook:

- `statcast_2015_full.csv`
- `statcast_2016_full.csv`
- `statcast_2017_full.csv`
- `statcast_2018_full.csv`
- `statcast_2019_full.csv`
- `statcast_2020_full.csv`
- `statcast_2021_full.csv`
- `statcast_2022_full.csv`
- `statcast_2023_full.csv`
- `war_daily_bat.txt`
- `war_daily_pitch.txt`

The dissertation analysis used locally stored annual Statcast CSV files and
Baseball-Reference WAR records. The repository does not treat the earlier
experimental Statcast downloader as part of the final analytical pipeline.

Generated intermediate files are written to `data/processed/` and are ignored
by Git.
