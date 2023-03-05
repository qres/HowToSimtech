# How to SimTech: list and short description of useful tools

## Editors

### VS Code

#### Useful VS Code extensions

### atom

### Jetbrains IDEs

paid IDE for Java, Python, C, C++, PHP. There is a free [version for students](https://www.jetbrains.com/student/).

## Command Line Editors

### nano

The most simple option with self-explaining interface.

### Vim

More complex editor with many features. You should get a vim cheat sheet in the beginning.

### Emacs

More complex editor with many features. You should get a emacs cheat sheet in the beginning.

## Version Control

### git

- The [Git Book](https://git-scm.com/book/en/v2) is a good place to start.

### GitHub

Host for git repositories.
As a student you can [get 'github pro' for free](https://education.github.com/students), which includes features such as private repositories and github copilot. Requires an account.

### BitBucket

Free alternative to GitHub with private repositories.

## Markup languages

### Markdown

Good for writing pdf documents quickly. Not as nice as LaTeX but good enough for exercises.
See the markdown [cheat sheet](long_descriptions/markdown-cheat-sheet.md) for The most important markdown features.

#### pandoc

Format conversion tool

- Can compile markdown to pdf, html and many others.

The [Eisvogel](https://github.com/Wandmalfarbe/pandoc-latex-template) plugin is a useful extension to create well-formatted pdf files from markdown files.

## LaTeX - helpful tools

### Detexify

Draw the symbol you need and [detexify](http://detexify.kirelabs.org/classify.html) will tell you the corresponding LaTeX command and package.

### Mathpix

With [Mathpix](https://mathpix.com/) you can screenshot any equation and it guesses the underlying tex formula. Not Open source, but you get a limited number of screenshots per month for free. Requires an account. [LaTeX-OCR](https://github.com/lukas-blecher/LaTeX-OCR) is a free open-source alternative.

### Syntex

Use LaTeX with `--synctex=1` to link the produced pdf to your LaTeX source code. If you have syntex support in your pdf/ps/dvi viewer and your editor, you can ctrl-click on a paragraph to scroll to it and get it highlighted in the other document.

### latexmk

Automatically performs all steps needed to create the index, BibTeX/Biber, references, ...
You can get a continuous preview with the `-pvc` option.

### JabRef

[Jabref](http://www.jabref.org/) is a tool to manage your BibTeX references. You can search and tag the references, link them to pdfs and add summaries.

### IguanaTex

[IguanaTex](http://www.jonathanleroux.org/software/iguanatex/) is a PowerPoint plugin to use LaTeX formulas in your document.

#### LaTeX Editors

### TexMaker

### TexStudio

### VS-Code plugin

### Sublime plugin

- LaTeXTools
- LaTeX-cwl

### LyX

[LyX](https://www.lyx.org/Screenshots) is a WYSIWYM editor for documents which uses LaTeX internally and also exports to LaTeX code. The document and formulas are shown similarly to the final document. Mathematical formulas can either be written using the LaTeX code or with the various shortcuts (e.g `Alt-M G A` for alpha (read "alt math Greek alpha"), `Alt-M I` for integrals). You can write raw LaTeX via `ctrl-L` for features that are not natively supported by LyX.

## Debugging - C, C++ etc

### gdb

- You can modify the _startup script_ `~/.gdbinit`. There exists various init files to support _colored output_ ([copy this file in your init file](https://github.com/RAttab/dotfiles/blob/master/colors.gdb)) and many other other features.
- If you want to debug a program wich takes _command line arguments_ you can pass them like `gdb --args program param1 param2`.
- You can print the first three elements of _arrays_ using `p *ptr@3`. If you have a 3x2 matrix you can also use `p *ptr@3@2` which will give a clearer structure to the output than `p *ptr@6`.

### gdbgui

[gdbgui](https://gdbgui.com/screenshots.html) is a"Browser-based debugger for C, C++, go, rust, and more"

### Valgrind

Useful to find difficult _memory bugs_ when gdb doesn't catch them or doesn't give any useful information. Examples are _double free_-bugs, bugs which corrupted the allocator meta data (in this case you might get an error the next time you try to allocate any new memory) or reading _uninitialized memory_.

- You can use the flag `valgrind --track-origins=yes` to make valgrind track and report where you allocated uninitialized memory.
- Besides memory checks with the default `--tool=memcheck` there also exist many other tools. E.g. `--tool=cachegrind`, which compute _cache misses_ for the instruction cache and memory cache.
- Warning: valgrind will make your program run really slow.

## Profiling -- C, C++ etc

### perf

### Flamegraph

[Flamegraph](http://www.brendangregg.com/flamegraphs.html) is a nice way to [visualize](http://www.brendangregg.com/FlameGraphs/cpuflamegraphs.html) the results of `perf`.

- `perf script | ~/FlameGraph/stackcollapse-perf.pl | ~/FlameGraph/flamegraph.pl > flamegraph.svg` creates an interactive svg image from the perf script.
- You can also mix it with some `grep`, `sed`, oder `c++filt`.
- There also exists a [module](https://github.com/evanhempel/python-flamegraph) for python.

### Valgrind profiling

- For measuring _cache misses_. See the valgrind section in 'Debugging'

### c++filt

Demangles C++ names to make them more readable. Nice in combination with profiler output or flamegraphs.

## Debugging -- Cuda

### cuda-gdb

Gdb with cuda extension. You can also set _breakpoints in kernels_ and switch between threads to inspect the variables.

- You can also create an init file `~/cuda-gdbinit`. Just use the same file as for `gdb` if you want colored backtraces.
- To break on API errors like failed kernel launches or other error codes use `set cuda api_failures stop`.
- To check for _invalid memory addresses_, you can use `set cuda memcheck on` to enable something like `valgrind --tool=memcheck` for cuda. Warning: This makes your program much slower.
- TODO: problem with breakpoints on gpu connected to display.

## Profiling -- Cuda

### nvprof

Command line profiler for Cuda programs. You can also generate a file, which can be imported to `nvvp` using `--analysis-metrics -o file`. This helps with profiling a remote program.

- You can output the profiling in CSV format with a common time unit using `--csv -u us`.
- Profiling can be limited to specific kernels using `--kernels my_kernel`, which applies to following `--analysis-metrics`, `--events` or `--metrics` options.
- You can control the GPUs visible to your program by setting the environment variable `CUDA_VISIBLE_DEVICES`. Example: `CUDA_VISIBLE_DEVICES=0,2` masks out GPU 1. Run `nvidia-smi` to get the number of each GPU.

## Plotting

### matplotlib

Python library for plotting.

### gnuplot

Language especially for plotting. Can export to many formats including png, svg, latex.

- You can use the init file `.gnuplot` to run code or set settings startup
- Can fit arbitrary parameters to compute a function that approximates the data points using `fit`.
- You can also plot data using the output of shell commands: `plot '< python gen_data.py'` or `plot '< sed -n "s/^## //p" file'` or even with pipes `plot '< cat data/- | sed -n "s##re=\(.-\)##\1##p"'`

### PGFPlots

Handy LaTeX package to create plots directly in LaTeX. Can plot data in CSV or gnuplot format. Supports diagrams, graphs, box plots, 3d plots and many more.

- There are also higher level features as loops and random numbers.
- Becomes slow for many plots. You can avoid the recomputation of the plots by compiling them in another document into an PDF and include it with `\includegraphics`. This is done automatically if you use `\usepgfplotslibrary{external}` and `\tikzexternalize[prefix=TikzPictures/]` in your preamble.
- You can use gnuplot to plot your data.

## PDF viewer

### Zathura

### Ocular

## Shells

### Fish Shell

[Fish shell](https://fishshell.com/docs/current/tutorial.html) is a shell with useful autocompletion and many other features.

### ZSH

To get started, [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh/) is good to manage your zsh configuration.

## Job Scheduler

### Slurm

Job manager.
[Detailed description](long_descriptions/slurm.md)

## Libraries

### Python

- Numpy for efficient array/vector/matrix operations.
- [Scipy](https://docs.scipy.org/doc/scipy/reference/index.html) offers many useful algorithms. E.g. linear algebra, FFT and optimization.
- Sympy for symbolic computations, integrals and derivatives.
- Matplotlib for plotting.

### FEM

- FeniCS: Python
- deal.II: C++

## Code Documentation

### Doxygen

De facto standard tool for generating documentation from annotated C++ sources

### Sphinx

Documentation tool mostly used in python.

## Formatting

### Formatting in VS Code

there are many VS Code extensions providing linter for several programming languages and markdown. A linter is a tool that analyzes source code to flag programming errors, bugs, stylistic errors, and suspicious constructs.

### Python formatting

#### black

> Black is a PEP 8 compliant opinionated formatter. Black
> reformats entire files in place. Style configuration options
> are deliberately limited and rarely added.

#### flake8

> flake8 is a python tool that glues together pycodestyle,
> pyflakes, mccabe, and third-party plugins to check the style
> and quality of some python code.

#### pylint

> Pylint is a static code analyser for Python 2 or 3. The
> latest version supports Python 3.7.2 and above. Pylint
> analyses your code without actually running it. It checks for
> errors, enforces a coding standard, looks for code smells,
> and can make suggestions about how the code could be
> refactored.

## Miscellaneous

### Unofficial latex thesis template

An [unofficial latex template](https://github.com/latextemplates/scientific-thesis-template) for Scientific Computing theses at the Uni Stuttgart. See [overview and introduction](https://latextemplates.github.io/scientific-thesis-template/) for a template description.
