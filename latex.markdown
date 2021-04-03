## What is LaTeX?

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
