## Exploring The Sonic Archive
### Digital Tools for Richard Freedman's course at Heidelberg University, Fall 2026

This repository contains Jupyter Notebooks and related data for Richard Freedman's sessions during the course. They are designed for the CRIM Project JupyterHub, but most will also run in a local Python environment or in Google Colab.

The notebooks build on one another, from the basics of Python and data tables, through the analysis of encoded texts and scores, to experiments with Large Language Models:

1. **Python and Pandas Basics**: the building blocks: notebooks, Python, and data tables
2. **The Beatles**: a complete data workflow: clean, tidy, query, and chart a real dataset
3. **TEI**: encoded *texts*: reading XML, and finding patterns of rhyme
4. **MEI, music21, and CRIM Intervals**: encoded *music*: notes, intervals, patterns, and corpora
5. **LLM Analysis**: what Large Language Models can (and cannot) tell us about music

**How to use these notebooks:** open them in JupyterHub and run the cells in order, top to bottom. Within each folder, work through the notebooks in alphabetical order (A, B, ...). In the Beatles folder this matters: each notebook saves a file that the next one loads.

## Notebooks

### 01 Python and Pandas Basics

*The big idea: a notebook is a place to think with code. Python holds and transforms information; Pandas organizes it into tables we can question.*

**[A_Python_Basics.ipynb](01_Python%20Pandas%20Basics%20/A_Python_Basics.ipynb)**: How Jupyter notebooks work, and the core Python every later notebook relies on, taught with music-themed examples. Students learn to tell Markdown cells from code cells, and to recognize the basic kinds of data (text, numbers, True/False) and how to convert between them. They also meet the two containers used everywhere in data work: **lists** (ordered collections) and **dictionaries** (look-ups from keys to values).
- Running cells, importing libraries, printing results
- Data types, string methods, and type conversion
- Lists and dictionaries

**[B_Pandas_Basics.ipynb](01_Python%20Pandas%20Basics%20/B_Pandas_Basics.ipynb)**: An introduction to the **DataFrame**, the table at the heart of data analysis in Python, using metadata about Renaissance pieces from the [CRIM Project](https://crimproject.org). Students load live data from the CRIM website, then learn to inspect a table, select and reshape its rows and columns, sort and count, and combine two tables into one. A closing section shows why Pandas' built-in methods are usually better than writing loops.
- Loading JSON data into a DataFrame
- Inspecting, selecting (`loc`, `iloc`), adding, dropping, and renaming
- Sorting and counting (`sort_values`, `value_counts`)
- Combining tables (`concat`, `merge`)

### 02 The Beatles: Clean, Tidy, Find, Filter, Group, and Chart

*The big idea: a complete data workflow, from a messy spreadsheet to research questions and charts. Every step involves decisions that shape what the data can tell us.*

These four notebooks work with a single rich dataset, `Beatles_Belgrade_Complete.csv`. It combines **Spotify** audio features (energy, valence, danceability, ...) with metadata compiled at the **University of Belgrade**: songwriters, singers, albums, genre, style, theme and mood labels, and chart histories. Together they pursue questions such as: *How did the Beatles' sound change over time? Do Lennon, McCartney, and Harrison songs differ? Does chart success in the 1960s relate to popularity today?* The notebooks pose these questions but leave the interpretation to students.

**[A_Beatles_Clean_Data.ipynb](02_Beatles_Tidy_Clean_Filter_Group_Chart/A_Beatles_Clean_Data.ipynb)**: Real data is never ready to use, and cleaning it is part of the research, not a chore before it. Students find missing values and decide what each one *means*: sometimes it should be filled, sometimes dropped, and sometimes (as with chart positions) the gap itself is information. They then fix inconsistent values with three tools of increasing power, `replace()`, `map()`, and `apply()`, and correct data types. The result is saved as `beatles_clean.pkl`.
- Finding and interpreting missing data
- `replace()` vs. `map()` vs. `apply()`: which tool for which job
- Turning multi-label text into lists
- Reproducible cleaning, and saving to a Pickle

**[B_Beatles_Tidy_Data.ipynb](02_Beatles_Tidy_Clean_Filter_Group_Chart/B_Beatles_Tidy_Data.ipynb)**: The principles of **Tidy Data** (one variable per column, one observation per row), and why they make questions easy to answer. Students split UK and US album releases into separate columns, `explode` genre lists into one row per genre, and `melt` wide data into the long format that charts need. They also learn the costs: exploding every label column at once turns 278 songs into tens of thousands of rows, and in tidy data one row no longer equals one song. The result is saved as `beatles_tidy_genre.pkl`.
- `str.split()`, `explode()`, and `melt()`
- Choosing the right shape of data for the question
- Counting correctly in tidy data

**[C_Beatles_Find_Filter_Group.ipynb](02_Beatles_Tidy_Clean_Filter_Group_Chart/C_Beatles_Find_Filter_Group.ipynb)**: Almost every data-based claim rests on two moves: **filtering** (narrowing to the rows that match a condition) and **grouping** (summarizing and comparing categories). Students filter on numbers, text, and lists of labels; combine conditions; turn continuous values into categories with bins; and compare songwriters, years, albums, and genres with `groupby`. A recurring theme: a table of averages is not yet an answer. Ask how many songs stand behind each number, and how the categories were defined.
- Boolean masks, `isin()`, `str.contains()`, and combined conditions
- Bins with `cut()` and `qcut()`
- `groupby()`, `agg()`, `crosstab()`, and `transform()`

**[D_Beatles_Charts_Graphs.ipynb](02_Beatles_Tidy_Clean_Filter_Group_Chart/D_Beatles_Charts_Graphs.ipynb)**: A tour of the main chart types in [Plotly Express](https://plotly.com/python/plotly-express/), organized by the kind of question each one answers: bar charts for comparison, line charts for change over time, histograms and box plots for distributions, scatter and bubble plots for relationships, heatmaps for grids and correlations, and radar charts for profiles. Every chart is also an argument, so each one is followed by open questions for students to investigate, and a reminder that correlation is not causation.
- Matching the chart to the question
- Preparing data for charts with `groupby()` and `melt()`
- Customizing titles, labels, colors, and hover information

### 03 TEI: Encoded Texts

*The big idea: TEI XML records not only a text, but its structure and its history as a document, and that structure can be analyzed.*

**[A_EBBA_Ballads_TEI.ipynb](03%20TEI/A_EBBA_Ballads_TEI.ipynb)**: How a text is encoded in the Text Encoding Initiative (TEI) standard, using a single ballad from the [English Broadside Ballad Archive (EBBA)](https://ebba.english.ucsb.edu/ballad/37021/image). Students read and parse the XML with `lxml`, explore the metadata in the TEI header, and *see* the document's nested structure as an interactive network. They then move from structure to poetry, extracting stanzas and lines into a DataFrame and analyzing the ballad's rhymes.
- Parsing XML with `lxml`
- The TEI header: file, encoding, profile, and revision descriptions
- Visualizing a document's structure as a network
- From TEI to a DataFrame: stanzas, lines, and rhyme words

**[B_Du_Chemin_Rhyme_Network.ipynb](03%20TEI/B_Du_Chemin_Rhyme_Network.ipynb)**: From one poem to a whole corpus: the song texts of Du Chemin's *Chansons nouvelles* (the corpus of the [Lost Voices Project](https://digitalduchemin.org)), in [du_chemin_tei_texts.xml](03%20TEI/du_chemin_tei_texts.xml). Students use the rhyme and meter information encoded in TEI to build a table of every line, clean the rhyme words, and count which words rhyme together across the corpus. The result is a **rhyme network**, whose communities reveal the shared poetic vocabulary of the collection.
- Extracting encoded attributes (rhyme scheme, meter) from TEI
- Cleaning text with regular expressions
- Building and interpreting a weighted network, with community detection

### 04 MEI, music21, and CRIM Intervals: Encoded Music

*The big idea: once music is encoded, a computer can find notes, intervals, and recurring patterns, in one piece or across a whole corpus.*

**[Music21_Basics.ipynb](04%20MEI%20M21%20CRIM%20Intervals/Music21_Basics.ipynb)**: An introduction to [music21](https://web.mit.edu/music21/), the core library for computational musicology, using encoded scores (MEI and Humdrum) such as Chopin's Prelude Op. 28, No. 1 and a canzonet by Thomas Morley. Students learn how a score is represented in code: parts, measures, and notes, where each note is an object with pitch, octave, duration, and position. They also learn the difference between notes and rests, and between melodic intervals (within a voice) and harmonic intervals (between voices).
- Loading scores and reading their metadata
- Parts, measures, notes, rests, and durations
- Melodic and harmonic intervals

**[CRIM_Intervals_Duos.ipynb](04%20MEI%20M21%20CRIM%20Intervals/CRIM_Intervals_Duos.ipynb)**: [CRIM Intervals](https://github.com/HCDigitalScholarship/intervals) builds on music21 and returns its results as Pandas DataFrames, bringing the tools of the earlier notebooks to bear on music. Working with two-voice pieces by Bach, Bartók, and Morley, students chart the notes and intervals of a single piece, find recurring melodic and contrapuntal patterns (**n-grams**) and cadences, and then scale up to a **corpus**. They compare pieces side by side and build a network linking pieces that share melodic patterns.
- Notes, intervals, and n-grams as DataFrames
- Bar charts, radar plots, and heatmaps of musical features
- From one piece to a corpus
- Networks of pieces linked by shared patterns

### 05 LLM Analysis: Large Language Models and Music

*The big idea: LLMs are fluent, but are they accurate? When musical facts matter, we can let the model call real analysis tools, and test its answers against a known answer key.*

**[A_LLM_LangChain_Intro.ipynb](05_LLM_Analysis/A_LLM_LangChain_Intro.ipynb)**: The very basics of working with an LLM from Python, using [LangChain](https://www.langchain.com/). Students set up an API key safely, choose a model, send a first prompt, and see how a **system prompt** changes the model's behavior, and how firmly it holds.
- API keys and model selection
- Prompts and system prompts
- A reusable function for asking questions

**[Music_Analysis_LLM.ipynb](05_LLM_Analysis/Music_Analysis_LLM.ipynb)**: A controlled experiment in using LLMs for music analysis, with nine MEI scores by Bach, Bartók, and Morley. The same question is asked two ways: once with the LLM **reading a text summary** of the music, and once with the LLM **calling music21 tools** that open the scores and compute the answer. Both are compared with a correct answer computed directly in music21. The tasks range from easy to hard: metadata, note counts, pitch histograms, intervals, key, lyrics, and ranking pieces by difficulty. Students draw their own conclusions about where LLMs help, and where they guess.
- Tool-calling ("agentic") LLMs with LangChain and LangGraph
- Designing a fair comparison: same question, one variable changed
- Checking AI answers against verifiable computation
