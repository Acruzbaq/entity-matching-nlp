# entity-matching-nlp
NLP pipeline for financial entity matching using fuzzy logic
# Entity Matching NLP Pipeline

## What does this project do?
This pipeline compares financial entity names from two different data sources 
and determines whether they refer to the same entity. This is a real case business solution.

## Why did I build this?
In financial data operations, entity names are rarely identical across systems.
A company can appear as "Goldman Sachs S.A. de C.V." in one source and 
"Goldman Sachs" in another. Manual comparison is slow and error-prone.
This pipeline automates that process. allowing to compare bis datasets in just a couple of minutes.

This is just a base case. The pipeline can be extended to cover different scenarios, such as integrating AI models, 
building more complex dictionaries, or narrowing the scope to a specific country or market sector. 
The sky is the limit!

## How does it work?
1. **Text Normalization** — Removes accents, punctuation, and legal suffixes
2. **Entity Classification** — Detects if the entity is a Corporate, Financial Instrument, or Public Entity
3. **Type Gate** — Blocks comparison if entities are from different market sectors
4. **Fuzzy Matching** — Scores name similarity using token_sort_ratio

## Tech Stack
- `rapidfuzz` — Main matching engine
- `cleanco` — Legal suffix detection across multiple countries
- `unidecode` — Text normalization
- `pandas` — Data manipulation

## Key Technical Decisions
- Evaluated **spaCy**, **sentence-transformers**, and **rapidfuzz**
- Discarded spaCy due to low precision for entity names, this library performs better when comparing larger bodies of text.
- Discarded transformers due to false positives between entities of the same sector, In other words,
    the semantic similarity was too broad for this specific use case. 
- Chose rapidfuzz for its balance between precision and literalness, specifically,
    the sort_token_ratio was the best fit for this project, as it focuses on whether the same words exist
   in both strings regardless of their order.

## Sample Data
- `sample_input.xlsx` — Example input file
- `sample_output.xlsx` — Expected output after running the pipeline

  
## Work in Progress
This project is actively being improved. Upcoming additions:
- Unit testing
- Error handling
- Evaluation metrics (precision, recall, F1)
- Data visualizations

## Author
Alex Cruz | Monterrey, México
