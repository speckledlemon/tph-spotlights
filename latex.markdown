## What is LaTeX?

LaTeX is a typesetting system used to create any kind of document with text: papers, books, letters, and even posters. Unlike word processors, it enforces the separation of formatting (how the text looks) from the actual content, while giving even more granular control over appearance if desired.

Writing LaTeX is similar to Markdown or HTML: it's a plain text markup language with macros to indicate properties that should be applied to parts of the text, but with a large ecosystem of packages which provide macros for handling different writing systems and written languages, formatting code, and [putting coffee rings on paper](http://legacy.hanno-rein.de/hanno-rein.de/archives/349). The file is then run through a compiler which performs text and page layout, then produces a PDF.

<!-- It combines a macro-based markup language with a  -->

<!-- To write in LaTeX  -->

### Why use LaTeX instead of a word processor or another markup language?

Compared to using a word processor, it automatically comes with all the benefits of being based on plain text:
- Inserting fully-customizable tables, equations, and images

### Getting up and running

The quickest way to get started is to make an account on [Overleaf](https://www.overleaf.com) and create a new project. It's entirely web-based and allows you to live edit with multiple people (like Google Docs) and even track changes. It also has Dropbox, Git, and GitHub integration.

If you prefer a local installation,

- If you want to install,
  - Windows: Miktex
  - macOS: TeX Live
  - Linux: distro package manager
- How to "compile"?

### Topics to cover

- document structure (Sectioning, Top-Matter, Abstract, Input, Includes, Document Classes)
- bibliographies (bibtex/biblatex? common citation styles?)
- images/figures and the concept of "floats"
- code snippets (`listings` and `minted`)
- equation environments
- important/popular latex packages
  - AMS-LaTeX, Babel, Microtype, Notes (for collaboration)
  - I have my own "package list" (like microtype, booktabs, siunitx, braket, mhchem, fixme) but am blind to others (babel) so would appreciate some input there
- Debugging

### Other todos

- Advanced section where we could link to topics such as "Making your own latex packages" , "Making your own .sty files" etc.
  - Reusing a common style file is better than copy-pasting the same preamble everywhere. Keep your style file under version control and reuse it across projects
- convert this doc to latex (good example of using pandoc?)
- pandoc
