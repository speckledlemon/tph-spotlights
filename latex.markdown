## What is LaTeX?

LaTeX ([pronounciation](https://tex.stackexchange.com/q/17502)) is a typesetting system used to create any kind of document with text: papers, books, letters, and even posters.  Unlike word processors, it enforces the separation of formatting (how the text looks) from the actual content, while giving even more granular control over appearance if desired.

Writing LaTeX is similar to Markdown or HTML: it's a plain text markup language with macros to indicate properties that should be applied to parts of the text, but with a large ecosystem of packages which provide macros for handling different writing systems and written languages, formatting code, and [putting coffee rings on paper](http://legacy.hanno-rein.de/hanno-rein.de/archives/349).  The file is then run through a compiler which performs text and page layout, then produces a PDF.  If you're familiar with C or C++, LaTeX macros work similarly: you can think of them as direct text replacement, but the [details](https://www.overleaf.com/learn/latex/A_six-part_series:_How_do_TeX_macros_actually_work%3F) are quite complicated.

### Getting up and running

#### Online

The quickest way to get started is to make an account on [Overleaf](https://www.overleaf.com) and create a new project.  It's entirely web-based and allows you to live edit with multiple people (like Google Docs) and even track changes.  It also has Dropbox, Git, and GitHub integration.  Even if collaboration isn't important for you, generating the PDF only requires clicking a single button.

#### Locally

If you prefer a local installation, you must install a *distribution*, which has the same meaning as for Linux: the core and packages are fundamentally the same among each, but the nuts and bolts that deal with how everything is installed and how packages are managed are different.  Generally you don't need to worry about the differences, but you do need to pick one.  There are [many](https://tex.stackexchange.com/q/239199) available; some common ones are:
- Windows: [MiKTeX](https://miktex.org/)
- macOS: [MacTeX](http://tug.org/mactex/), also available through Homebrew
- Linux: TeX Live, most likely through your distro package manager

One reason you may prefer Overleaf when trying out LaTeX is that a full local install is about 4 GB when going the most convenient route of including all the packages you could possibly want, so you don't have to worry about missing one when using a minimal install.  You don't *need* packages to write LaTeX, but like third-party dependencies in programming languages, you will come to depend on certain ones over time.

With a local install, you will also require ways to write LaTeX files, compile them, and view the output.  There are editors like Texmaker <https://www.xm1math.net/texmaker/> that combine an editor, an automated way to generate the PDF, and a pane that lets you view the PDF, much like an IDE or a Markdown editor with preview.  However, any text editor works fine, since they all have LaTeX editing modes with handy shortcuts and snippets, and the output is viewable in any PDF reader. Standalone compiling can be confusing and is a topic on its own, but a wrapper that automatically handles things like including bibliographies is `latexmk`:
```
$ latexmk -pdf mydocument.tex
```
which comes packaged with distributions.

### Writing your first document and intro to environments

Create a new file, something like `hello_world.tex`, write
```latex
\documentclass{article}

\begin{document}
Hello, world!
\end{document}
```
and then compile however you do.  The result should be a PDF with big margins, the text "Hello, world!" near the top, and a lone "1" at the bottom center, which is from the automatic page numbering.  Congrats on your first LaTeX document!  We already see two important things:
1. Macros in LaTeX are written like `\verygoodthingy{a,b,soup}`, where the macro called `verygoodthingy` is called with the arguments `a`, `b`, and `soup`.  Two common variants are those that take options with or without keyword arguments (`\usepackage[final]{microtype}` and `\usepackage[separate-uncertainty=true,range-units=single]{siunitx}`) and those that take multiple argument blocks (`\multicolumn{3}{c}{numerical}` has 3).
2. In order to write anything, you need to first specify the kind ("class") of document (such as `article`, `book`, `report`, `letter`, `beamer`, and many others <https://tex.stackexchange.com/q/782>), then create the main document "environment" that text will be typeset in.  There are many different environments available (<https://latex.wikia.org/wiki/List_of_LaTeX_environments>), provided by built-in as well as external packages.  An environment is delimited by the `begin` and `end` macros, each taking the name of the environment.  All content that appears in the final output must be inside the `document` environment. Some macros must appear outside the `document` environment, but most are nested inside.

To see the effect of how environments change typesetting, compare the two following documents:
```latex
\documentclass{article}

\begin{document}
An example polynomial is f(x) = 2.45x + 7.2.
\end{document}
```
```latex
\documentclass{article}

\begin{document}
An example polynomial is
\begin{equation}
f(x) = 2.45x + 7.2
\end{equation}
\end{document}
```
where you should notice that in the first example, the equation is typeset as regular text and the spacing isn't what you'd expect for a mathematical equation.  It is also possible to write "inline" math, rather than the isolated and numbered "display" math,
```latex
\documentclass{article}

\begin{document}
An example polynomial is \(f(x) = 2.45x + 7.2\).
\end{document}
```
which is placed inside `\( ... \)` delimiters.

### Document structure

There are two kinds of structure in LaTeX: that of the (output) document being written, and that of the LaTeX file itself.  A LaTeX file consists of two main parts: the "preamble", where packages are set up and other configuration happens, and the actual document body, where the text to be displayed goes (think `<head>` and `<body>` from HTML).  Everything above the document body section (contained inside `\begin{document}` and `\end{document}`) can be considered the preamble.

The most common document class, the `article`, defines document structure using `\section{...}`, `\subsection{...}`, and `\subsubsection{...}`, while `report` and `book` add a top-level `\chapter{...}`.

### Topics to cover

- document structure (Sectioning, Top-Matter, Abstract, Input, Includes, Document Classes)
- bibliographies (bibtex/biblatex? common citation styles?)
- images/figures and the concept of "floats"
- code snippets (`listings` and `minted`)
- equation environments
- important/popular latex packages
  - AMS-LaTeX, Babel, Microtype, Notes (for collaboration)
  - I have my own "package list" (like microtype, booktabs, siunitx, braket, mhchem, fixme) but am blind to others (babel) so would appreciate some input there
- documentation for packages: `texdoc <package_name>` on the command line, CTAN
- Debugging

### Other todos

- Advanced section where we could link to topics such as "Making your own latex packages" , "Making your own .sty files" etc.
  - Reusing a common style file is better than copy-pasting the same preamble everywhere. Keep your style file under version control and reuse it across projects
- convert this doc to latex (good example of using pandoc?)
- pandoc

### Advanced and random topics

#### Digression: Math in LaTeX vs. Markdown, TeX vs. LaTeX

Markdown writers may know the use of `$ ... $` and `$$ ... $$` delimiters to enter inline and display math. These are actually borrowed from TeX and should not be used in LaTeX, though that doesn't stop people. The correct LaTeX delimiter pairs are `\( ... \)` and `\[ ... \]`. See https://tex.stackexchange.com/a/410874 for more details.

### Resources

- LaTeX Wiki: <https://latex.wikia.org/wiki/Main_page>
- TeX.SE, the LaTeX Stack Exchange: <https://tex.stackexchange.com/>
