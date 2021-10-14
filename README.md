# Data 512 A2 Bias

This project aims to explore the concept of bias through data on Wikipedia political figure articles from various countries. The two matrices we are looking at are articles-per-population, percentage of the number of politician articles as a proportion of the country population, and high-quality, the proportion of politician articles that are of GA and FA-quality. The code used for data cleaning and analysis, and my reflection and observation from this project are stored in the Jupyter notebook `hcds-a2-bias`.


## Data and tools
We used two datasets in this project:
- Politicians by Country from the English-language Wikipedia: The dataset contains data on most English-language Wikipedia articles within the category "Category:Politicians by nationality" and subcategories. The dataset and documentation can be accessed through [page_data.csv](https://figshare.com/articles/dataset/Untitled_Item/5513449). The dataset is released under the CC-BY-SA 4.0 license.
- Population mid-2020 (millions): The dataset contains population record for countries and sub-regions in mid 2020. The dataset and documentation can be accessed here [WPDS_2020_data.csv](https://www.prb.org/international/indicator/population/table/) 

To generate Wikipedia article quality, we used a machine learning system called ORES, "Objective Revision Evaluation Service". ORES is a machine learning tool that can provide estimates of Wikipedia article quality. We used the ORES REST [documentation](https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context_revid_model). It expects a revision ID for article, which is the third column in the Wikipedia dataset, a model, which is "articlequality", and a context, which is "enwiki". The machine learning tool is built based on the peer-reviewed [Wikipedia content assessment](https://en.wikipedia.org/wiki/Wikipedia:Content_assessment) procedures.These quality classes are a sub-set of quality assessment categories developed by Wikipedia editors. The article quality estimates are, from best to worst:
- FA - Featured article
- GA - Good article
- B - B-class article
- C - C-class article
- Start - Start-class article
- Stub - Stub-class article

### Other datasets
After cleaning the data, we have our final dataset for analysis stored in `wp_wpds_countries_by_country.csv`. The dataset has the following attributes:
- country: The country of the article
- article_name: The name of the article
- revision_id: The revision id for the article used to generate quality score prediction
- article_quality_est.: The quality score prediction
- population: The population of the country

In additional, we have the following datasets storing data we cannot use for analysis:
- `wp_no_prediction.csv`: This datasets stores Wikipedia pages that does not have a revision ID match to the ORES data tool.
- `wp_wpds_countries-no_match.csv`: This datasets stores Wikipedia pages that does not have a country match to the Population dataset.
