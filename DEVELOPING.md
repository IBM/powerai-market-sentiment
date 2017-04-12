Tips for Developers
===================

The notebook is designed to be run top-down. Settings in early cells are used
in later cells. Some variables are also cleared to free up memory. So, although
you can often run single cell repeatedly while testing changes, you may want
to start over from the top if anything seems to be missing.

#### Notebook structure
* Setting credentials
* Installing Python packages
* Importing libraries
* Defining global variables and helper functions
* Acquiring the data
* Transforming the data
* Visualizing the information
* Summary

Setting credentials
-------------------
Credentials need to be added to the notebook to access dashDB. The credentials
and the dashDB table prefix are set near the top of the notebook to make it
more obvious that they need to be set and also to make it more obvious that
you will be saving a notebook with credentials. You should not share your
notebook with anyone that you would not share your dashDB credentials with
unless you use the ``share`` feature with the ``Only text and output`` or
``All content excluding sensitive code cells`` option.

The ```@hidden_cell``` magic is used to mark the credentials cells as "sensitive".
If you do any rearranging of sensitive code, remember to identify sensitive
cells with ``@hidden_cell``.

Installing Python packages
--------------------------
The notebook is using ```!pip install``` to install the Wordcloud Python package
from PyPI. You can follow this example if you decide to use additional Python
packages in your notebook. Check the output to see that the install was
successful. See the "Controlling output" section below for more information on
how we suppress/show the output. You might want to use ``DEBUG = True`` until
you've verified that the pip install was successful.

> **Note**:  After running a cell with pip install, you may need to restart
the kernel and then run the cells again from the top.
 
Importing libraries
-------------------
Import and some setup of libraries is done near the top. This is another
example of why cells need to run top-down. Keeping the imports near the top
is a Python PEP8 style convention. Python does not require this convention,
but Python developers are used to looking for imports at the top.

* Set ``DEBUG = True`` in the cell near the top. Run that cell and then re-run
  cells as needed to get more printed output.
* Make sure the pip install ran correctly. You might need to restart the
  kernel and run the cells from the top after the pip install runs the first
  time. Run the cell after the pip install with ``DEBUG = True`` to see the status.
* Many of the cells rely on variables that are set in earlier cells. Some of these
  are cleared in later cells. Start over at the top when troubleshooting.

Defining global variables and helper functions
----------------------------------------------
After the imports, a few global variables and helper functions are defined.
These allow for code re-use. These cells need to run before other cells can
use the functions and globals. These values do not change. You can change
and run the later cells over and over without always restarting from the top.

Acquiring the data
------------------
Follow the setup instructions to load the data in to dashDB and to set the
credentials and table prefix. After the setup, the code to load the data is
pretty straightforward.

The data is retrieved from the database by using the Spark JDBC connector and
is loaded into Spark DataFrames in the notebook called df_TWEETS and
df_SENTIMENTS. The DataFrames have the same column names as the tables
in dashDB.

Spark user-defined functions are used to map sentiments to numbers and back
again. These allow aggregation of records with mixed sentiments. The numeric
is aggregated into a mean() which can then be mapped back to a value of
'POSITIVE', 'NEGATIVE' or 'AMBIVALENT'.

The df_TWEETS and df_SENTIMENTS DataFrames are joined and aggregated into
a DataFrame named df_JOIN_TWEETS.

Transforming the data
---------------------
You can't analyze the data that you have just loaded into the data frames
the way it is. You must first transform the data. The following
transformations are performed on the data:

1) Remove the time from the timestamp values as only the date information is
   used.

2) Change the values in the string columns like user country, state and city
   to upper case.

3) Change the tweet posting location information from a string
   ('pos (42.000 42.000)') to a numeric value represented by the longitude
    and latitude coordinates. 

The output of the data transformation process is a new Spark DataFrame which
has the target structure on which to base the data analysis. This Spark
DataFrame called df_cleaned_tweets functions as the main data source for all
further processing.

Visualizing the information
---------------------------

#### Map the distribution of tweets by country
The df_cleaned_tweets DataFrame is aggregated by ``USER_COUNTRY`` to get a
DataFrame with the tweet count per country. This Spark DataFrame is then
converted to an in-memory Pandas DataFrame to prepare for plotting.
We used a ``df_`` prefix for Spark DataFrames and a ``p_df_`` prefix for
Pandas DataFrames.

The distribution by country is charted two very different ways using
Matplotlib for a bar chart and Google GeoChart for an interactive world map.

Following the plotting, the DataFrames for by-country aggregation are cleared
to free up resources.

#### Pie charts for tweet sentiments
The by-sentiment charting code process is very similar to the above by-country
process, but this time we used pie charts to show the sentiment percentages.

#### Analyzing Twitter timelines
To analyze the Twitter timeline, the data is aggregated by day and sentiment.
Again we use Pandas DataFrames and Matplotlib. Line charts are used.

The addMissingDates() helper function is used to provide a zero data point for
days with no tweets.

Plotting tweets by car-maker over time is another example. The process is
similar but with more subplots in this case.

#### Visualizing the popular topics during the peak
The recommended time period for the sake of this example, has a very
significant, very negative peak in September. We used a DataFrame filter
to focus on that data. The frequency of words used is calculated. "Stopwords"
are used to ignore words that are typically not interesting. In addition,
we filtered out the words that are 3 chars or less, start with "http" or
contain non-ascii characters. After a little trial and error to make the
results look nice, 3 words were added to stopwords.

The top-20 words are used to make a word cloud which is a great way to
visualize the hot topics during the peak. A pie chart is also used and
very effective. For the pie chart, it made sense to filter out 'Volkswagen'.
That is in the title and is redundant as a significant piece of the pie.
In the word cloud, however, the subject is a prominent part of the word cloud.

Controlling output
------------------
One of the great things about notebooks is that you can use them to document
what you are doing, show your work, show the results, and document your
conclusion -- all in one place. Sharing "your work" (the code) is a great
feature, but in our example we decided to use a few tricks to make the
"only text and output" web page look nice and clean.

#### %%capture captured_io
 
"%%capture captured_io" magic is used to capture the output when nothing else
works. We used that to hide the "!pip install" output and added a cell
right after it that will print the captured output if DEBUG is True.
   
#### if DEBUG

The DEBUG boolean and 'if' statements are used for the above and also
throughout the notebook wherever some print statements were handy during
development and might be handy in the future, but were not something we wanted
to share in the final output.
  
#### Ending with a semi-colon 

Notice the statements in the notebook that end with a semi-colon. It looks like
bad Python, but it is actually a trick to prevent these statements from
showing their result in the output.

#### @hidden_cell magic

The @hidden_cell magic is used to mark the credentials cells as "sensitive".
If you do any rearranging of sensitive code, remember to identify sensitive
cells with @hidden_cell.
