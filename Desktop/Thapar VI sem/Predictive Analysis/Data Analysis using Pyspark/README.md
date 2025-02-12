# Data Analysis Using PySpark

## Overview
This project demonstrates data analysis using **PySpark**, focusing on music listening habits and genre preferences. It leverages large datasets to perform various queries, data manipulations, and visualizations efficiently.

## Features
- Data preprocessing and cleaning using PySpark
- Analysis of user listening behavior
- Identification of top artists, tracks, albums, and genres
- Integration of multiple datasets using joins
- Data visualization using Matplotlib

## Dataset Description
1. **listenings.csv**: Contains user listening records with attributes such as user ID, artist, track, album, and date.
2. **genre.csv**: Maps artists to their respective music genres.

## Technologies Used
- **PySpark** for big data processing
- **Google Colab** for execution
- **Matplotlib** for data visualization
- **Python 3**

## Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/your-repo.git
   ```
2. Install PySpark:
   ```bash
   pip install pyspark
   ```
3. (Optional) Run on Google Colab for easy execution.

## Data Analysis Workflow
1. **Data Loading:**
   - Mount Google Drive to access datasets.
   - Import CSV files using PySpark.

2. **Data Cleaning:**
   - Remove unnecessary columns (e.g., 'date').
   - Drop null values.

3. **Queries Performed:**
   - Top users listening to specific artists (e.g., Rihanna).
   - Top 10 famous tracks and albums.
   - Genre analysis: Popular genres and favorite genres per user.
   - Visualization of genre distribution using bar charts.

4. **Joining Datasets:**
   - Combined listening data with genre data using an inner join for advanced analysis.

## Example Queries
```python
# Query 1: Top 10 users who listened to Rihanna the most
q2 = listening_df.filter(listening_df.artist == 'Rihanna')\
    .groupBy('user_id')\
    .agg(count('user_id').alias('count'))\
    .orderBy(desc('count'))\
    .limit(10)
q2.show()

# Query 7: Top 10 popular genres
q7 = listening_df.join(genre_df, 'artist', 'inner')\
    .groupBy('genre')\
    .agg(count('genre').alias('count'))\
    .orderBy(desc('count'))\
    .limit(10)
q7.show()
```

## Visualization Example
```python
plt.bar(labels, counts)
plt.xlabel('Genres')
plt.ylabel('Counts')
plt.title('Genre Distribution')
plt.show()
```

## Results
- Identified top tracks, artists, and genres.
- Visualized genre popularity trends.
- Determined user-specific favorite genres.

## Contributing
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit changes (`git commit -m 'Add new feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a pull request.

## License
This project is licensed under the [MIT License](LICENSE).

## Acknowledgments
- [Apache Spark](https://spark.apache.org/)
- [Google Colab](https://colab.research.google.com/)
- [Matplotlib](https://matplotlib.org/)
