# CHI Draft Tutorial: A Guide to Text Analysis in R for Humanists
...
# What is R?
R is a programming language and software environment for statistical computing and graphics. It is widely used for data analysis, statistical modeling, and data visualization. R is particularly popular among statisticians, data scientists, and researchers in various fields. For humanists, one of the many uses of R is analyzing text data, which involves processing, analyzing, and visualizing text from various sources like books, articles, social media, or any other written content. R provides a rich ecosystem of packages (collections of functions and tools) that can help you with different aspects of text analysis, such as cleaning and preprocessing text, finding patterns, sentiment analysis, topic modeling, and generating word clouds.

R is open source, which means its source code is freely available and can be modified, shared, and distributed by anyone. The R project is licensed under the GNU General Public License (GPL), which guarantees the freedom to use, study, share, and modify the software. R is developed and maintained by the R Development Core Team, a group of volunteers from around the world who contribute their time and expertise to improve and enhance the software. This team is responsible for coordinating updates, fixing bugs, and incorporating new features. R is continuously updated through new releases, with major releases happening once or twice a year. These releases often include improvements in performance, new features, and bug fixes. The R community also plays a crucial role in maintaining and updating R by contributing packages, reporting bugs, and providing suggestions for improvements.

The [Comprehensive R Archive Network (CRAN)](https://cran.r-project.org/) is a central repository for R packages, which is also maintained by the R Development Core Team and other volunteers. CRAN provides a platform for developers to submit their packages, and it ensures that these packages are compatible with the latest version of R and pass certain quality checks. This extensive collection of packages is a major reason why R is popular for a wide range of applications, including text analysis.


## Why choose R?
Text analysis is typically conducted in either R or Python. While both R and Python are popular programming languages for data analysis, there are several reasons why you might choose to use R for analyzing text data:

- Comprehensive statistical analysis: R was originally designed for statistical analysis and has a vast array of built-in statistical functions and packages. This makes it easy for beginners to perform various statistical tests and analyses on text data.

- User-friendly data manipulation: R's syntax is considered more readable and user-friendly for data manipulation tasks. Packages like dplyr, tidyr, and stringr in the tidyverse ecosystem make it simple for beginners to clean, reshape, and manipulate text data.

- Visualization: R is known for its powerful visualization capabilities, especially with the ggplot2 package. It enables users to create high-quality and customizable visualizations of text data, which can be particularly helpful for understanding patterns and trends in the data.

- Rich ecosystem for text analysis: R has a rich ecosystem of packages specifically designed for text analysis, such as tm, quanteda, tidytext, and many more. These packages provide a wide range of functions to preprocess, analyze, and visualize text data, making it easier for beginners to get started with text analysis in R.

- Community support and resources: R has a large and supportive community of users, which includes academics, statisticians, and data scientists. This means that there are plenty of resources, such as tutorials, blog posts, and forums, available for learning and troubleshooting text analysis tasks in R.

- Integrated development environment (IDE): RStudio, a popular IDE for R, offers a user-friendly environment with features like syntax highlighting, code completion, and integrated help, making it easier for beginners to learn and use R for text analysis.

While Python is also a powerful language for text analysis with packages like NLTK, spaCy, and gensim, R offers a unique combination of statistical capabilities, user-friendly data manipulation, powerful visualization tools, and a rich ecosystem of text analysis packages. As a result, some beginners might find R more suitable for text analysis tasks.

## What is RStudio?
[RStudio](https://posit.co/products/open-source/rstudio/) is an integrated development environment (IDE) for R, which provides a user-friendly interface for writing, editing, and executing R code. RStudio makes it easy to work with R scripts, manage your data and variables, visualize your results, and install and use R packages. Here are some of the main features of RStudio that help you write and execute R scripts:

- Source editor: RStudio provides a powerful source editor with features like syntax highlighting, code completion, and code folding. This makes writing and editing R code more efficient and enjoyable.

- Console: The console in RStudio is where you can directly type and execute R commands. It shows the output of your code and any error messages if something goes wrong.

- Environment and history: RStudio keeps track of your variables, functions, and data in the Environment tab. This makes it easy to see what's available in your workspace and manage your objects. The History tab shows the list of commands you've executed previously, allowing you to easily reuse or modify them.

- Plots, packages, and help: RStudio organizes other useful tools and information in separate tabs. The Plots tab displays the visualizations you create, the Packages tab helps you manage and install R packages, and the Help tab provides access to the documentation for R functions and packages. This can be helpful when learning to use new packages!

To get started with RStudio, you can create a new R script (File > New File > R Script) or open an existing one. Then, you can write your R code in the source editor, and execute it by either highlighting the code and clicking the "Run" button or pressing "Ctrl + Enter" (Windows/Linux) or "Cmd + Enter" (Mac). The output will be displayed in the console, and any generated plots or visualizations will appear in the Plots tab.

## What is the tidyverse?
The [tidyverse](https://www.tidyverse.org/) is a collection of R packages designed to make data science tasks easier and more efficient by providing a consistent and coherent set of tools for data manipulation, visualization, and modeling.

To understand the tidyverse's role in text analysis, let's break it down into a few key aspects:

- Data manipulation: The tidyverse includes packages like dplyr and tidyr that help you clean, organize, and transform data. In the context of text analysis, this can involve converting text data into a structured format, removing unwanted characters, or splitting text into words or sentences.

- Data visualization: ggplot2 is a package within the tidyverse that helps you create visually appealing and informative graphics. For text analysis, you can use ggplot2 to visualize word frequencies, sentiment scores, or relationships between words and other variables.

- Data modeling: The tidyverse also includes tools for modeling data, such as linear regression, decision trees, or clustering. These can be useful for text analysis to identify patterns, make predictions, or group similar texts together.

- Text-specific packages: Although not part of the core tidyverse, there are text-focused packages like tidytext that integrate well with the tidyverse ecosystem. Tidytext allows you to perform common text analysis tasks like tokenization (splitting text into words or phrases), sentiment analysis, and counting word frequencies using tidyverse-style syntax.

# Using R
## How is text data structured in R?
Document-term matrices (DTMs), term-document matrices (TDMs), tibbles, character vectors, dataframes, and corpuses are all data structures used for handling and analyzing text data in R. They have different characteristics and are suitable for various stages of text analysis. In this section, you'll find a brief description of how they relate to each other and differ from one another:

Character vectors: A character vector is a one-dimensional array of character strings in R. It can be used to store raw text data, such as individual sentences or documents. Character vectors serve as the basic building blocks for more complex data structures like corpuses and dataframes.
```
	text_data <- c("The quick brown fox jumps over the lazy dog.",
		       "The early bird catches the worm.",
		       "A stitch in time saves nine.")
```

Corpuses: A corpus is a collection of text documents, usually stored as a list of character vectors or a specialized data structure provided by text analysis packages like quanteda. A corpus is useful for storing and managing large volumes of text data before preprocessing and transforming it into more structured formats like DTMs, TDMs, or tibbles.
```
	# Using the tm package, we can create a corpus from the character vector.
	library(tm)

	corpus_data <- VCorpus(VectorSource(text_data))
```

Dataframes: A dataframe is a two-dimensional, tabular data structure in R that can store columns of different data types. It is a versatile and commonly used data structure for data manipulation and analysis. When working with text data, dataframes can be used to store tokenized or sentiment data. However, tibbles are a more modern and preferred alternative to dataframes within the tidyverse ecosystem.
```
	# A dataframe example with tokenized text data:
	tokenized_data <- data.frame(Document = c(1, 1, 1, 2, 2, 3, 3),
				     Token = c("The", "quick", "brown", "The", "early", "A", "stitch"))
```

Tibbles: Different from the adorable but proliferative [tribble](http://memory-alpha.wikia.com/wiki/Tribble), a tibble is a modern data frame format in R, specifically designed to work within the tidyverse ecosystem. Tibbles offer improved printing and subsetting capabilities compared to traditional dataframes. Tibbles can be used to store and manipulate tokenized text data or sentiment data, making them suitable for text analysis tasks in the tidyverse context.
```
	# Creating a tibble with tokenized text data using the tibble package:
	library(tibble)

	tokenized_tibble <- tibble(Document = c(1, 1, 1, 2, 2, 3, 3),
				   Token = c("The", "quick", "brown", "The", "early", "A", "stitch"))
```

Document-term matrices (DTMs): A DTM is a matrix representation of text data, where each row represents a document, and each column represents a term (word). The elements in the matrix indicate the frequency of terms in the documents. DTMs are useful for text mining, information retrieval, and machine learning tasks that require a structured representation of text data. They are often derived from corpuses or dataframes/tibbles containing tokenized data.
```
	# Creating a DTM from the character vector using the tm package:
	library(tm)

	corpus_data <- VCorpus(VectorSource(text_data))
	dtm_data <- DocumentTermMatrix(corpus_data)
```

Term-document matrices (TDMs): A TDM is the transpose of a DTM, with each row representing a term and each column representing a document. TDMs are used for similar purposes as DTMs but can be more efficient for certain operations, such as calculating term frequencies across documents.
```
	# Creating a TDM from the character vector using the tm package:
	library(tm)

	corpus_data <- VCorpus(VectorSource(text_data))
	tdm_data <- TermDocumentMatrix(corpus_data)
```

In summary, character vectors and corpuses are typically used for storing and managing raw text data. Dataframes and tibbles are used for handling structured text data, such as tokenized or sentiment data. DTMs and TDMs are matrix representations of text data used for text mining and machine learning tasks. These data structures serve different purposes in various stages of text analysis and can be transformed and used interchangeably, depending on the specific requirements of a given task. These examples illustrate the basic structure of each data type using a small text dataset. Note that some of these data types, such as corpuses, DTMs, and TDMs, rely on specific text analysis packages (e.g., tm), while others, like character vectors, dataframes, and tibbles, use base R or tidyverse functions.

## What is a package? Which packages are useful for text analysis?
In R, a package is a collection of functions, data, and documentation that extends the capabilities of the base R language. Functions are pre-written pieces of code that perform specific tasks or calculations. Packages are created by the R community to solve particular problems or provide additional functionality in areas like data manipulation, visualization, and statistical modeling.

To find packages in R, you can:

- Search the Comprehensive R Archive Network (CRAN): CRAN is the official repository for R packages. You can browse or search for packages on the [CRAN website](https://cran.r-project.org/). Most packages on CRAN come with documentation, including a description, user manual, and examples.

- Use search engines: You can search for R packages using general search engines like Google or specialized search engines like [Rseek](https://rseek.org/).

- Explore GitHub: Many R package developers host their code here on GitHub!

To install a package in R, follow these steps:

1. Open R or RStudio.
2. Use the install.packages() function to install the package. For example, to install the "dplyr" package, you would type:
	```
	install.packages("dplyr")
	```
3. Press Enter or Return on your keyboard to execute the command. R will download and install the package from CRAN. This process might take a few moments, depending on the package size and your internet connection.
Once the package is installed, you need to load it into your R session using the library() function. For example, to load the "dplyr" package, you would type:
	```
	library(dplyr)
	```
Now you can use the functions and datasets provided by the package in your R session.

Remember that package installation is a one-time process, but you'll need to load the package using library() each time you start a new R session and want to use its functions.

### Some common packages used in text analyis include:

- [readr](https://readr.tidyverse.org/): A part of the tidyverse, readr provides functions for reading text files and other data formats into R. It offers better performance and more consistent behavior than base R functions. Use readr to import text data into R for analysis.

- [stringr](https://stringr.tidyverse.org/): A tidyverse package that simplifies string manipulation tasks in R. It provides consistent, easy-to-use functions for common string operations like pattern matching, substring extraction, and text replacement. Use stringr for text preprocessing and cleaning.

- [tidytext](https://cran.r-project.org/web/packages/tidytext/vignettes/tidytext.html): A package designed to work with the tidyverse ecosystem, tidytext provides functions for tokenizing, analyzing, and visualizing text data in a tidy data format. It allows you to seamlessly integrate text analysis with other tidyverse tools. Use tidytext for tokenization, sentiment analysis, and n-gram analysis in a tidy data context.

- [tm](https://tm.r-forge.r-project.org/): A comprehensive text mining package, tm provides functions for preprocessing, managing, and analyzing text data. It supports various data structures, like corpuses, DTMs, and TDMs. Use tm for text mining tasks, such as text classification, clustering, and topic modeling.

- [quanteda](http://quanteda.io/): A powerful package for text analysis, quanteda provides tools for text preprocessing, corpus management, and text mining. It has a clean and consistent syntax, making it easy to learn and use. Use quanteda as an alternative to tm for text mining and analysis.

- [dplyr](https://dplyr.tidyverse.org/): A core tidyverse package, dplyr provides functions for data manipulation and transformation in a clean and consistent syntax. It works with dataframes and tibbles. Use dplyr for filtering, selecting, and transforming your text data during analysis.

- [tidyr](https://tidyr.tidyverse.org/): Another core tidyverse package, tidyr focuses on reshaping and cleaning data. It provides functions for converting data between long and wide formats, filling missing values, and more. Use tidyr to create and maintain tidy text data.

- [ggplot2](https://ggplot2.tidyverse.org/): A popular data visualization package in the tidyverse, ggplot2 is based on the Grammar of Graphics. It allows you to create complex and customizable visualizations using a consistent and modular syntax. Use ggplot2 for visualizing patterns and trends in your text data.

- [wordcloud](https://cran.r-project.org/web/packages/wordcloud/wordcloud.pdf): A package for creating word clouds, wordcloud visualizes the frequency of words in text data by displaying words in various sizes and colors. Use wordcloud for visually exploring word frequencies in your text data.

- [igraph](https://r.igraph.org/): A package for network analysis and visualization, igraph can be used to explore relationships between words, phrases, or documents in text data by creating and visualizing graphs. Use igraph to analyze and visualize relationships in your text data.

- [topicmodels](https://cran.r-project.org/web/packages/topicmodels/topicmodels.pdf): The topicmodels package provides functions for fitting topic models, such as Latent Dirichlet Allocation (LDA), to text data. Topic modeling is a technique used to discover underlying themes or topics within a collection of documents. You might choose this package when you want to group documents based on shared themes or extract hidden patterns within a large corpus of text.

## How do I structure scripts in R?
### Structure code sequentially 
R reads and executes code sequentially from top to bottom, line by line. Each line of code or command is executed in the order it appears in the script, and the result of each line may depend on the lines before it.

This sequential execution is important to remember when writing R code, as the order of your commands can impact the results. Variables, functions, or libraries should be defined or loaded before they are used in the script.

Here's a simple example to illustrate how R reads code:
```
	# Step 1: Load the 'stringr' library for text manipulation
	library(stringr)

	# Step 2: Assign a character vector containing sentences to the variable 'text_data'
	text_data <- c("The quick brown fox jumps over the lazy dog.",
		       "The early bird catches the worm.",
		       "A stitch in time saves nine.")

	# Step 3: Assign the result of a function (convert text_data to lowercase) to the variable 'lowercase_text'
	lowercase_text <- str_to_lower(text_data)

	# Step 4: Print the 'lowercase_text' variable
	print(lowercase_text)
```
In this example, R reads the code from top to bottom. It first loads the stringr library, then creates the text_data variable, converts the text data to lowercase and assigns it to the lowercase_text variable, and finally prints the lowercase_text variable.

### Use <- to assign outcomes to variables
In R, the <- symbol is known as the assignment operator. It is used to assign a value or the result of an expression to a variable. The <- operator points from the value (or expression) to the variable that will store the value.

Using the assignment operator, you can create and assign values to variables in your R code. Here's a simple example to illustrate how the assignment operator works:
```
	# Assign a character vector containing sentences to the variable 'text_data'
	text_data <- c("The quick brown fox jumps over the lazy dog.",
		       "The early bird catches the worm.",
		       "A stitch in time saves nine.")

	# Load the 'stringr' library for text manipulation
	library(stringr)

	# Assign the result of a function (convert text_data to lowercase) to the variable 'lowercase_text'
	lowercase_text <- str_to_lower(text_data)

	# Print the 'lowercase_text' variable
	print(lowercase_text)
```
In this example, we used the assignment operator <- to create variables for storing the original text data and the result of a text processing function (converting the text to lowercase).

### Use the pipe operator (%>%) to simplify complex functions
The pipe operator (%>%) in R is a convenient way to chain multiple functions together in a more readable and organized manner. It was introduced by the magrittr package and is widely used within the tidyverse ecosystem. The pipe operator takes the output of one function and passes it as the input to the next function, allowing you to perform a sequence of operations in a more intuitive and clean way.

Here's a simple example to illustrate how the pipe operator works:

Suppose you have a character vector text_data containing sentences, and you want to perform the following operations:

1. Convert the text to lowercase.
2. Remove punctuation and special characters.
3. Split the text into words (tokenize).

Without the pipe operator, you would nest the functions like this:
```
	library(stringr)

	text_data <- c("The quick brown fox jumps over the lazy dog.",
		       "The early bird catches the worm.",
		       "A stitch in time saves nine.")

	cleaned_data <- str_split(str_replace_all(str_to_lower(text_data), "[^a-zA-Z\\s]", ""), "\\s+")
```
With the pipe operator, you can rewrite the code in a more readable way:
```
	library(stringr)
	library(magrittr) # Load the magrittr package for the pipe operator

	cleaned_data <- text_data %>%
	  str_to_lower() %>%
	  str_replace_all("[^a-zA-Z\\s]", "") %>%
	  str_split("\\s+")
```
In this example, the pipe operator %>% helps to chain the text preprocessing operations in a sequential manner, making the code easier to read and understand. Note that if you are using the tidyverse, the pipe operator is already included, so you don't need to load the magrittr package separately!

### Best practices for formatting your code in R
Formatting code in R involves writing your code in a clean, consistent, and readable manner. Proper code formatting makes it easier for you and others to understand, maintain, and debug your code. Here are some general guidelines:

- Indentation: Use consistent indentation (2 or 4 spaces are common) to make your code easier to read. Do not mix spaces and tabs for indentation.
```
	# Good
	text_data <- c("The quick brown fox jumps over the lazy dog.",
		       "The early bird catches the worm.",
		       "A stitch in time saves nine.")

	# Bad (inconsistent indentation)
	text_data<-c("The quick brown fox jumps over the lazy dog.",
		  "The early bird catches the worm.",
	  "A stitch in time saves nine.")
```
- Spacing: Use spaces around operators, commas, and parentheses for better readability.
```
	# Good
	cleaned_data <- text_data %>%
	  str_to_lower() %>%
	  str_replace_all("[^a-zA-Z\\s]", "") %>%
	  str_split("\\s+")

	# Bad (lack of spaces)
	cleaned_data<-text_data%>%
	  str_to_lower()%>%
	  str_replace_all("[^a-zA-Z\\s]","")%>%
	  str_split("\\s+")
```
- Line length: Keep your code lines reasonably short (around 80 characters) to make it easier to read and avoid horizontal scrolling.
```
	# Good
	cleaned_data <- text_data %>%
	  str_to_lower() %>%
	  str_replace_all("[^a-zA-Z\\s]", "") %>%
	  str_split("\\s+")

	# Bad (long lines)
	cleaned_data <- text_data %>% str_to_lower() %>% str_replace_all("[^a-zA-Z\\s]", "") %>% str_split("\\s+")
```
- Variable and function names: Use meaningful and consistent naming conventions for your variables and functions. In R, it's common to use lowercase words separated by underscores (snake_case) for variable and function names.
```
# Good
	word_count <- function(text) {
	  tokenized_text <- str_split(text, "\\s+")
	  length(tokenized_text[[1]])
	}

	# Bad (inconsistent and unclear naming)
	WordCount <- function(t) {
	  tokenizedText <- str_split(t, "\\s+")
	  length(tokenizedText[[1]])
	}
```
- Comments: Use comments to explain your code and make it more understandable. Start comments with the # symbol, followed by a space.
```
	# Good
	# Count the number of words in a given text
	word_count <- function(text) {
	  tokenized_text <- str_split(text, "\\s+")
	  length(tokenized_text[[1]])
	}

	# Bad (lack of comments)
	word_count <- function(text) {
	  tokenized_text <- str_split(text, "\\s+")
	  length(tokenized_text[[1]])
	}
```
# Topic Modeling in R
## What is topic modeling?

Topic modeling is a technique in natural language processing (NLP) that aims to discover hidden themes or "topics" within a large collection of documents. The idea is to uncover the underlying structure of the documents by identifying patterns in the words they contain. Topic modeling can help you understand and organize large amounts of text data, such as news articles, research papers, or social media posts.

Among computational topic models, Latent Dirichlet Allocation (LDA) is a popular algorithm that works on the assumption that each document is a mixture of several topics, and each topic is a collection of related words. In LDA, the topics are "latent" or hidden variables that the algorithm tries to discover based on the distribution of words in the documents.

Here's a simple overview of how LDA works:

1. You decide on the number of topics you want the algorithm to discover (let's say, K topics).

2. The algorithm randomly assigns each word in each document to one of the K topics.

3. Then, it iteratively refines these assignments by considering two factors:
	a. How prevalent each topic is across all documents (i.e., how many documents contain a particular topic).
	b. How likely each word is to belong to a specific topic (i.e., how often a word appears in a topic across all documents).

4. The algorithm continues to refine the topic-word assignments until it reaches a stable state or a predefined number of iterations.

5. Finally, LDA provides two key outputs: the distribution of topics across documents and the distribution of words within each topic.

On a more detailed level, LDA uses three parameters to control the behavior of the algorithm and influence the results. These parameters are:

- Number of topics (K): This parameter determines how many topics the LDA algorithm will attempt to discover in the document collection. Choosing the right number of topics is crucial, as it can affect the quality and interpretability of the results. Too few topics might lead to broad, overlapping themes, while too many topics might result in overly specific or fragmented themes. There is no one-size-fits-all approach to selecting the number of topics, and it often requires trial and error, domain knowledge, or evaluation methods like coherence scores or perplexity.

- Alpha (α): This parameter influences the distribution of topics across documents. In LDA, each document is assumed to be a mixture of topics, and alpha determines how "concentrated" or "diverse" the topic mixture is for each document. A low alpha value will result in documents dominated by a small number of topics, while a high alpha value will lead to a more uniform distribution of topics across documents. The optimal alpha value depends on the specific dataset and research question; it may require experimentation or tuning to achieve the best results.

- Beta (β): This parameter affects the distribution of words within each topic. Beta determines how "concentrated" or "diverse" the word distribution is for each topic. A low beta value will result in topics with a few dominant words, while a high beta value will lead to more evenly distributed words within topics. Similar to alpha, the optimal beta value depends on the dataset and the desired level of word specificity within each topic.

In practice, LDA implementations often set default values for alpha and beta (for example, 50/K for alpha and 0.1 for beta). These default values may work well for some datasets, but it's important to remember that adjusting these parameters can have a significant impact on the quality and interpretability of the results. Experimenting with different parameter values and evaluating the output can help you find the best configuration for your specific use case.

## What are some common issues I might encounter when working with social media text?
When working with unconventional text data in R, especially data scraped from social media, you might encounter several common issues. 

- Encoding issues: Social media data may contain various character encodings, special characters, or emojis, which might cause issues when loading or processing the data in R. Ensure that you correctly handle encoding and properly convert the text data to a consistent format, such as UTF-8. You can use the iconv() function or the stringi package to convert encodings.

- Incomplete or messy data: Social media data can be noisy, containing incomplete sentences, misspellings, slang, or abbreviations. Clean and preprocess the text data by removing unnecessary elements (e.g., URLs, mentions, special characters), expanding abbreviations, and correcting misspellings. See the next section for more details on this process!

- Handling multi-language data: Social media data may contain text in multiple languages, which can be challenging to analyze and process. Detect and separate the data by language using packages like textcat, cld2, or cld3. Then, preprocess and analyze each language separately using appropriate tools and resources, such as language-specific stopword lists and stemming algorithms.

Large datasets: Social media data can be vast, making it challenging to manage and process using conventional methods. Use efficient data manipulation packages like dplyr or data.table for handling large datasets. 

Informal language and context-specific terms: Social media content often contains informal language, slang, and context-specific terms that may not be found in standard language resources like dictionaries or sentiment lexicons. Create custom dictionaries, lists, or lexicons tailored to the specific context or domain of your data. You can manually curate these resources or use techniques like word embeddings or unsupervised learning algorithms to discover and group similar terms.

## A topic modeling workflow for social media texts
### Scrape texts
### Clean and preprocess the dataset
Data cleaning, also known as data preprocessing or data wrangling, is the process of preparing and transforming raw data into a more structured, consistent, and usable format. This step is essential in any data analysis project, as it ensures the data is accurate, reliable, and suitable for the desired analysis or modeling techniques. For text data, this may include: 

- Removing duplicates: Sometimes, datasets contain duplicate entries or records. These duplicates can distort the analysis results and lead to incorrect conclusions. Data cleaning involves identifying and removing duplicate records to ensure the dataset's integrity.

- Handling missing values: In real-world datasets, it's common to encounter missing or incomplete data. Data cleaning involves addressing these missing values, either by filling them in with appropriate estimates (e.g., mean, median, or mode), or by removing the records with missing data if they are not critical to the analysis.

- Correcting inconsistencies: Datasets may contain inconsistencies, such as variations in how data is entered or recorded (e.g., different date formats, spelling variations, or units of measurement). Data cleaning aims to standardize these inconsistencies to ensure the data is uniform and comparable.

- Fixing errors and typos: Data may contain errors or typos, such as incorrect data entries or misspelled words. Data cleaning involves identifying and correcting these errors to improve the dataset's accuracy and reliability.

- Filtering and selecting relevant data: In some cases, datasets may contain irrelevant, redundant, or unnecessary information that doesn't contribute to the analysis. Data cleaning involves filtering and selecting the relevant data that aligns with the research questions or objectives.

- Transforming data: Sometimes, data needs to be transformed or converted into a different format or structure to be compatible with specific analysis techniques or tools. Data cleaning may involve reorganizing, aggregating, or normalizing the data to prepare it for further analysis.

### Fit and train your model
Fitting a model on training data is an essential step in the process of building and evaluating machine learning models, including topic models like Latent Dirichlet Allocation (LDA). The main reason for using training data is to avoid overfitting and to ensure that the model generalizes well to new, unseen data.

Overfitting occurs when a model learns to perform very well on the data it was trained on but performs poorly on new, unseen data. This is because the model has learned the specific characteristics or noise in the training data instead of the underlying patterns that generalize to new data. 

Generalization is the ability of a model to perform well on new, unseen data. By fitting the model on training data and evaluating it on separate test data, you can assess how well the model generalizes to new examples. This is crucial because, in practice, you'll want your model to make accurate predictions or provide meaningful insights when analyzing data it hasn't encountered before.

Fitting a model on training data and evaluating it on test data allows you to measure its performance using various metrics, such as coherence scores or perplexity for topic models. This can help you compare different models, adjust parameters, or select the best model for your specific use case.

However, in some cases, a researcher might decide not to split their data into training and test sets, especially when working with a collection of short social media text, for the following reasons:

- Limited data: Social media posts are typically short, and the total amount of available data might be limited. Splitting the data into training and test sets can further reduce the data available for model training. In such cases, researchers might choose to use all available data for model training to maximize the information the model can learn from.

- Interpretability: When working with social media text, the primary goal might be to explore and understand the underlying themes or topics, rather than accurately predicting new data. In this case, researchers might prioritize model interpretability and meaningfulness over strictly measuring its predictive performance.

- Noisy data: Social media text often contains a lot of noise, like slang, abbreviations, and typos. In such situations, the traditional training-test split approach might not be as effective, as the model could struggle to learn meaningful patterns from the noisy data. Researchers might instead focus on cleaning and preprocessing the text to improve the quality of the data before fitting the model.

That said, it's important to note that not using training data to fit the model comes with its risks. Without a separate test set, it's more challenging to assess the model's ability to generalize to unseen data and avoid overfitting. Researchers should carefully weigh the pros and cons of not using a training-test split, considering the specific goals of their analysis and the characteristics of the social media text they are working with.

### Assess and interpret results
The evaluation of computational topic modeling results in the humanities is still a developing area of research. In more data-driven fields, two measures are often used to assess the model's results: 
- Coherence scores: A coherence score measures how semantically related the top words within a topic are. A higher coherence score indicates that the words in a topic are more likely to appear together in the same context, suggesting a more meaningful and interpretable topic. Coherence scores are often calculated using word co-occurrence statistics, like pointwise mutual information (PMI) or term frequency-inverse document frequency (TF-IDF).

- Perplexity: Perplexity measures how well a topic model predicts the words in a held-out set of documents (usually a test set). A lower perplexity score indicates that the model is better at predicting the words in the test set, suggesting a better fit to the data. However, perplexity is not always a good indicator of the interpretability or meaningfulness of the topics.

For humanists, especially researchers integrating computational topic modeling into a mixed qualitative and quantitative methodology, it may be more fruitful to use these measures as guidelines but to rely on domain knowledge and prioritize interpretability to a human reader. 

