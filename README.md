# A book of Python in Rmarkdown
I love this book. It's not only written in Rmarkdown but also explains the fundamentals of Python in a live book in the web; totally reproducible.

Kudos to the author [Keh-Soon Yong (AP)](https://github.com/yongks), who published the original code in GitHub [here](https://github.com/yongks/python_bookdown): 

https://github.com/yongks/python_bookdown

What is extraordinary is that this book has been totally computed with Python as the coding engine, while the text is in [Rmarkdown](https://rmarkdown.rstudio.com/articles_intro.html). The plots have been generated by the Python package [matplotlib](https://matplotlib.org/), and [seaborn](https://seaborn.pydata.org/introduction.html).

Rmarkdown is the extended and  super-powered version of [Markdown](https://www.markdownguide.org/getting-started/), which uses some text symbols - such  as `#`, `*`, `_`, `[ ]`, `( )`, `$`, and others to add formatting to the document. Markdown and Rmarkdown documents are fully reproducible and can have version control with Git, since they are full text. This is continuation of *literate programming*[^1], initiated by Donald Knuth[^2]


My contribution consists of making this Python book even more reproducible: 

* adding instructions to build the Python environment with Anaconda (`environment.yml`); 
* adding a `Makefile` to automate the builds outside RStudio; 
* making the book available online as a website through *GitHub Pages* [here](https://f0nzie.github.io/yongks-python-rmarkdown-book/); 
* adding an R script to load the Python environment for each Rmarkdown document;
* Apply some formatting with `knitr` options


## The power of Rmarkdown
**Rmarkdown** opens infinite creation possibilities to data scientists, engineers and analysts for the production of documents, reports, analysis, tutorials, manuals, papers, thesis, presentations, slides, or even websites or blogs. Some of the advantages of writing your documents in Rmarkdown are:

- Documents are fully written in text which can be opened at any time with a simple text editor

- Documents are totally reproducible and able to be put under version control such as Git, and published to GitHub, GitLab, Bitbucket, or other cloud repositories

- Multiple coding languages can be embedded in a single document and executed during builds which makes calculations less error prone, or easier to pinpoint

- Plots, figures and images are generated by the code in Rmarkdown which make copy-and-paste a thing of the past

- Python and R can mutually interchange values of objects or variables in the same Rmarkdown document

- Rmarkdown documents can be built to be HTML books, Git books, PDF books, and other output formats


## Build the book
### R installation
I built this book with `R-3.6.3` in a **Debian-10** Linux operating system using [Visual Code Studio]() with the addition of some R friendly `vscode` extensions and [GNU `make`](https://www.gnu.org/software/make/). The `Makefile` file is included in the repo.

### Anaconda
The Anaconda version I used was the July version of 2020 (the name of the download is `Anaconda3-2020.07-Linux-x86_64.sh`). The Python version of the environment is `3.7`. But I also tested the book with Python `3.8` and the book works fine.

### Create the `conda` environment
When your Anaconda is ready, is the moment to create the Python environment using `conda`. The process takes few minutes - in my machine around 3 minutes). That Python environment will have all the packages necessary to run all the Python scripts in the book. Run this command from the terminal:

```
make conda_create
```

### Build the gitbook
You don't really need RStudio to build this book, but you need R installed. I took the challenge of building the book from the terminal window in `vscode`, with a little help of `Makefile` automation.

From a terminal, run:

    make gitbook1

or 

    make gitbook2


Both do the same thing: building the Rmarkdown book. I left the two options available for the reader to get familiar with `Makefile`; how to set environment variables from the shell, or set them from within R.

If the book builds successfully, it should open your browser with the main page of the book. This is all handled by `make` and the commands in `Makefile`.


## Optional after building the book
If you make changes to the Rmarkdown documents, you may want to tidy up or totally clean it from auxiliary folders and files that were generated during the knitting process. The are two rules in the `Makefile`: `tidy` and `clean `.

### Tidy up the folder
This deletes the auxiliary files that were created during the book building process.

    make tidy

### Clean up the folder
Does `make tidy` plus deletes the publication folder, to start over fresh.

    make clean


### Activate the `conda` environment
This is optional. I added it to document it for the next I have to work with book later. You activate it with:

```
make conda_activate
```

Of course, you could have typed this such trivial command on the terminal yourself.


## Original README
This is a minimal example of a book based on R Markdown and **bookdown** (https://github.com/rstudio/bookdown). Please see the page "[Get Started](https://bookdown.org/yihui/bookdown/get-started.html)" at https://bookdown.org/yihui/bookdown/ for how to compile this example into HTML. You may generate a copy of the book in `bookdown::pdf_book` format by calling `bookdown::render_book('index.Rmd', 'bookdown::pdf_book')`. More detailed instructions are available here https://bookdown.org/yihui/bookdown/build-the-book.html.

You can find the preview of this example at https://bookdown.org/yihui/bookdown-demo/.

[^1]: The literate programming paradigm, as conceived by Knuth, represents a move away from writing computer programs in the manner and order imposed by the computer, and instead enables programmers to develop programs in the order demanded by the logic and flow of their thoughts. https://en.wikipedia.org/wiki/Literate_programming

[^2]: Knuth is also the creator of the `TeX` computer typesetting system, the related METAFONT font definition language and rendering system, and the Computer Modern family of `typefaces`. https://en.wikipedia.org/wiki/Donald_Knuth
