# Cambridge YLE Vocabulary Dataset

The Cambridge Young Learner's English series of standardized English tests recommends that students of a certain level should already know certain English words. This dataset collects into a tidy `csv` file those words in both British and American English, the levels at which they should be known, their parts of speech, and thematic category.

There is also a Google Sheets which you can copy and query more quickly: <https://docs.google.com/spreadsheets/d/1_JpZPO8QjzKbOrhq75Pu4JFsc7bTBonr16KxAigXrFw/edit?usp=sharing>

## Data source

I pulled all of the data from `149681-yle-flyers-word-list.pdf`, which is an official test prep resource distributed freely by Cambridge English and hosted on the Cambridge English website. <https://www.cambridgeenglish.org/images/149681-yle-flyers-word-list.pdf>

## Methodology

Nothing fancy, just a lot of copying, pasting, a spreadsheet, and overabundant free time.

## Data structure

The data comprises 1,114 rows of data, 1 header row, and 39 columns. All data is either a string or boolean.

### String columns

The first two columns, `britsh` and `american` contain all of the words in British and American English, respectively. They are usually identical except for cases like "mum" vs. "mom". I considered leaving the `american` column blank except for only those cases where its different from `british` but decided against because it allows people working primary with American English to write simpler queries.

The `irregular_plural` column predictably contains entries that are irregular plurals of nouns, such as *child* -> *children*. All other rows are an empty string.

### Boolean columns

There are 36 boolean columns that can divided into 3 kinds: part of speech, YLE level, and theme.

- part of speech: `adjective`,  `adverb`,  `conjunction`,  `determiner`,  `discourse_marker`,  `exclamation`,  `interrogative`,  `noun`,  `possessive`,  `preposition`,  `pronoun`,  `title`, `verb`.
- YLE level: `starters`, `movers`, `flyers`.
- theme: `animals`,  `body_and_face`,  `clothes`,  `colours`,  `family_and_friends`,  `food_and_drink`,  `health`,  `home`,  `materials`,  `names`,  `numbers`,  `places_and_directions`,  `school`,  `sports_and_leisure`,  `time`,  `toys`,  `transport`,  `weather`,  `work`,  `world_around_us`.

## Adjustments

This dataset is not a direct copy from the source material. It contains some opinionated changes made in the interest of completeness, clarity, and query-ability.

- Additional context has been added to many words within the `british` and `american` columns. Context always follows its word and is wrapped in parentheses. There are two kinds of context. One type is phrasal, e.g. *catch (a ball)* or *break (take a)*. Notice that normal grammatical order is not preserved in some cases. Another kind of context is categorical, e.g. *keyboard (computer)* or *letter (alphabet)*. Often the context was already perfectly clear from the categories, but I wanted every value in the two vocabulary columns to be unique.
- The word *for* was listed under Starters as a preposition (e.g., "This is for you.") and under Flyers as a preposition of time (e.g., "For an hour."). In this dataset both variations are categorized as only a preposition, but the two versions are accompanied by context hints. The Starters word is now *for (you)* and the Flyers word is *for (an hour)*.
- The word *businessman / woman* was split into two words, *businessman* and *businesswoman* and irregular plurals were added.
- *mom* was added as the American English equivalent of *mum*.
- Changed *so* {`adverb`, `discourse_marker`, `starters`} and *so* {`adverb`, `conjuntion`, `flyers`} into *so (...)* {`discourse_marker`, `starters`}, *so (big)* {`adverb`, `starters`}, and *so (a ... b)* {`conjunction`, `flyers`}.
- Changed *well (feel)* {`adjective`, `adverb`, `movers`} in to *well* {`adjective`, `movers`} and *well (do)* {`adverb`, `movers`}.

## Copyright and license

Pre A1 Starters, A1 Movers, and A2 Flyers are copyright Cambridge University Press and Cambridge English Assessment.

This dataset is a transformative derivative work distributed under the Creative Commons Attribution Share Alike 4.0 International license (a.k.a CC-BY-SA-4.0). See `LICENSE.txt` for more information or visit <https://choosealicense.com/licenses/cc-by-sa-4.0/>


