
Got it — here's a simple but practical project idea that still uses Pandas, NumPy, and Matplotlib:


---

Project Title:

"Netflix Movies & TV Shows EDA"


---

Overview:

Perform exploratory data analysis on Netflix's public dataset to understand trends in content types, genres, countries, and release years.


---

Dataset:

Netflix Titles Dataset (Kaggle)



---

What You'll Analyze:

1. Number of movies vs. TV shows


2. Most common genres


3. Content trends over the years


4. Countries producing most content


5. Average duration of movies and shows




---


Clean and small dataset (around 8K rows)

Easy date and category filtering

No complex calculations needed



---

Basic Analysis Ideas:

import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('netflix_titles.csv')

# Check basic info
print(df.head())
print(df['type'].value_counts())

# Bar plot: Movies vs TV Shows
df['type'].value_counts().plot(kind='bar', title='Content Type Distribution')
plt.show()

# Top 10 genres
df['listed_in'].str.split(', ', expand=True).stack().value_counts().head(10).plot(kind='barh', title='Top 10 Genres')
plt.show()

# Content added by year
df['date_added'] = pd.to_datetime(df['date_added'])
df['year_added'] = df['date_added'].dt.year
df['year_added'].value_counts().sort_index().plot(kind='line', marker='o', title='Content Added Over Years')
plt.show()




