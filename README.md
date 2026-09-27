


## Exploring The Sonic Archive
### Digital Tools for Richard Freedman's course at Heidelberg University, Fall 2026



This repository contains Jupyter Notebooks and related data for Richard Freedman's sessions during the course.  They will work nicely with the CRIM project JupyterHub, but you can also run most of them in a local environment or with Google Colab.

## Notebooks

### 01 Python Pandas Basics

**[A_Python_Basics.ipynb](01_Python%20Pandas%20Basics%20/A_Python_Basics.ipynb)**: A hands-on introduction to Jupyter Notebooks and core Python, using music-themed examples. Topics include:

- Markdown and code cells, and how to run them
- Importing libraries (`pandas`, `datetime`)
- Printing output with `print()`
- Basic data types (strings, integers, floats, booleans) and checking them with `type()`
- Working with strings: concatenation, f-strings and common string methods (`.upper()`, `.strip()`, `.split()`, etc.)
- Converting between types (`str()`, `int()`, `float()`)
- Lists: indexing, adding, removing and sorting items
- Dictionaries: key-value pairs, accessing and updating values
- A closing "Your Turn!" exercise, with a link to the [Encoding Music Python Basics Tutorial](https://github.com/RichardFreedman/Encoding_Music/blob/main/01_Tutorials/03_Python_Basics.md)

**[B_Pandas_Basics.ipynb](01_Python%20Pandas%20Basics%20/B_Pandas_Basics.ipynb)**: An introduction to the Pandas library and DataFrames, using metadata about Renaissance pieces from the [CRIM Project](https://crimproject.org) (Citations: The Renaissance Imitation Mass). Topics include:

- Loading JSON data from the CRIM API with `requests` and flattening it with `pd.json_normalize()`
- Inspecting a DataFrame with `.head()`, `.tail()`, `.info()` and `.shape`
- Working with rows: `.sample()`, selecting by position with `iloc` and by label with `loc`, and dropping rows and resetting the index
- Working with columns: listing, adding, dropping, renaming (including a `dict.fromkeys()` shortcut), checking dtypes, and reordering or subsetting
- Treating a column as a Series, with `.unique()` and `.nunique()`
- Sorting with `sort_values()` and counting with `value_counts()`
- Combining DataFrames with `pd.concat()` and `pd.merge()`, including cleaning key columns before a merge
- Tips for making the most of Pandas's built-in methods instead of writing loops

### 03 TEI

**[A_EBBA_Ballads_TEI.ipynb](03%20TEI/A_EBBA_Ballads_TEI.ipynb)**: An introduction to reading Text Encoding Initiative (TEI) XML with Python, using a single ballad from the [English Broadside Ballad Archive (EBBA)](https://ebba.english.ucsb.edu/ballad/37021/image). Topics include:

- Loading a TEI file from the web with `requests` and parsing it with `lxml`
- Exploring the four sections of the `<teiHeader>`: `<fileDesc>`, `<encodingDesc>`, `<profileDesc>` and `<revisionDesc>`
- Visualizing the TEI tree as interactive networks with `networkx` and `pyvis`, first for the header and then for the complete document
- Extracting the ballad's stanzas (`<lg>`) and lines (`<l>`) into a Pandas DataFrame
- Finding rhyme words, assigning a rhyme scheme to each stanza and exploring rhymes with the `pronouncing` library

**[B_Du_Chemin_Rhyme_Network.ipynb](03%20TEI/B_Du_Chemin_Rhyme_Network.ipynb)**: An exploration of rhyme across the complete set of poems from Du Chemin's *Chansons nouvelles*, the corpus behind the [Lost Voices Project](https://digitalduchemin.org). It uses the TEI file [du_chemin_tei_texts.xml](03%20TEI/du_chemin_tei_texts.xml). Topics include:

- How a poem is encoded in TEI, including the `rhyme` and `met` (meter) attributes on each poem
- Parsing the TEI with `lxml` to build a DataFrame with one row per line, recording the piece, stanza, line number and rhyme letter
- Cleaning line endings with regular expressions to find each line's rhyme word
- Grouping rhyme words by piece and rhyme letter, then counting how often pairs of words rhyme across the corpus
- Building a weighted rhyme network with `networkx`, finding communities with the Louvain method and visualizing it with `pyvis`

### 04 M21 and CRIM Intervals

**[Music21_Basics.ipynb](04%20MEI%20M21%20CRIM%20Intervals/Music21_Basics.ipynb)**: An introduction to Michael Cuthbert's [music21](https://web.mit.edu/music21/) library for finding notes, durations and intervals in encoded scores. It uses MEI and Humdrum (`**kern`) files in the `Music_21_Files` folder, including Chopin's Prelude Op. 28, No. 1 and a canzonet by Thomas Morley. Topics include:

- Loading MEI files, and converting Humdrum files to MEI with `verovio`
- Reading title and composer from the MEI file and adding them to the music21 score
- Listing voice parts and counting measures
- Finding the notes in a voice part, as pitch classes and as pitches with octave numbers, and the notes in a given measure
- Working with durations, such as finding every half note and the measures it falls in
- The difference between notes and rests, and the key attributes of a note object
- Finding notes in a particular octave
- Melodic intervals between adjacent notes and harmonic intervals between voices (with `chordify()`)
- Loading a score with lyrics, as a starting point for working with text

**[CRIM_Intervals_Duos.ipynb](04%20MEI%20M21%20CRIM%20Intervals/CRIM_Intervals_Duos.ipynb)**: An exploration of two-voice pieces with [CRIM Intervals](https://github.com/HCDigitalScholarship/intervals), a Python library that builds on music21 and returns its results as Pandas DataFrames. It uses the MEI files in the `MEI` folder: Bach's Two-Part Inventions, pieces from Bartók's *Mikrokosmos* and Morley's 1595 canzonets for two voices. Topics include:

- Loading a single piece and getting its notes, durations and metadata
- Adding measure and beat numbers with `detailIndex()`
- Charting the notes in a piece as bar charts and radar plots, with the pitches sorted by `sort_pitch_values` and arranged chromatically or by the circle of fifths
- Finding melodic and harmonic intervals and charting melodic intervals
- N-grams: a heat map of melodic n-grams, contrapuntal n-grams combining melodic and harmonic motion, and finding cadences
- Building a corpus with `CorpusBase` and applying the same analysis to every piece, with bar charts and radar plots comparing pieces
- A network of pieces linked by the melodic n-grams they share, visualized with `pyvis`





