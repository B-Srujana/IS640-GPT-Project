# Milestone 1: Dataset Exploration and Preparation

## Dataset Description
The dataset used in this project contains detailed information about TV series from IMDb, organized into separate CSV files for different genres. It includes the following attributes:

- **Title**: Name of the TV series.
- **IMDb ID**: Unique identifier for the series on IMDb.
- **Release Year**: Year the series was released.
- **Genre**: Genre(s) of the series.
- **Cast**: Key cast members.
- **Synopsis**: A brief summary of the series (*focus of this project*).
- **Rating**: Average rating on IMDb (scale of 1–10).
- **Runtime**: Duration of episodes or total runtime.
- **Certificate**: Content rating (e.g., PG-13, TV-MA).
- **Number of Votes**: Total votes received.
- **Gross Revenue**: Total revenue generated (if available).

The dataset contains **236,828 rows** and **11 columns**, with some missing values in columns like `Runtime`, `Certificate`, and `Gross Revenue`.

## Objective
The primary objective is to preprocess the dataset's **Synopsis** column and use it as input for training a GPT-based text generation model. The tasks include:
- Cleaning and tokenizing the synopsis data.
- Transforming the data for use in text generation models.

## Dataset Justification
The IMDb TV series dataset was chosen for the following reasons:
- **Rich Text Data**: The `Synopsis` column provides diverse and descriptive text, making it ideal for text generation tasks.
- **Domain Applicability**: Insights into the entertainment industry and potential for creative applications, such as generating fictional synopses or extending existing ones.
- **Large Volume**: A significant number of entries ensures sufficient data for training robust models.

## Data Cleaning and Preparation

### Exploration
- Combined the dataset from multiple genre-specific CSV files into a single DataFrame.
- Inspected the data structure, data types, and missing values:
  - `Synopsis` column: No missing values, making it ideal for analysis.
  - Observed missing data in unrelated columns like `Gross Revenue` and `Certificate`.

### Cleaning
- Converted all text in the `Synopsis` column to lowercase.
- Replaced non-alphanumeric characters (excluding dots) with spaces to maintain text consistency.

**Example**:
- **Original**: "Miles Morales catapults across the Multiverse!"
- **Cleaned**: "miles morales catapults across the multiverse."

### Saving Processed Data
- Created a new DataFrame (`cleaned_data`) with the cleaned `Synopsis` text.
- Renamed the column to `text` for compatibility with downstream processing.
- Saved the cleaned data to `tv_series_synopsis_full.csv`.

### Summary of Cleaned Data
- **Shape**: 236,828 rows × 1 column (`text`).
- **Example Cleaned Text**:
  - "miles morales catapults across the multiverse where he encounters a team of spiderpeople charged with protecting its very existence."

## Next Steps

### Character Mapping
- Mapped unique characters in the dataset to integer IDs for tokenization.
- Created `encode` and `decode` functions for efficient text-to-numeric and numeric-to-text conversions.

### Data Splitting
- Divided the dataset into:
  - **Training set**: 90% of the data.
  - **Validation set**: 10% of the data.

### Batch Creation
- Defined a batch loading function to generate random input-output pairs.
- Developed a loss estimation function for evaluating model performance.

### Fine-Tuning GPT
- Established hyperparameters for training:
  - **Batch size**: 32
  - **Sequence length**: 128
  - **Learning rate**: 1 × 10⁻³
  - **Transformer architecture**: 8 layers, 8 attention heads, 128 embedding size.
