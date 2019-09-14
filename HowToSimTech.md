# Editors

<details><summary>vs code</summary>
</details>

<details><summary>atom</summary>
</details>

<details><summary>Jetbrains IDEs</summary>

paid IDE for Java, Python, C, C++, PHP.

 * There is a free [version for students](https://www.jetbrains.com/student/).

</details>

# Command Line Editors

<details><summary>nano</summary>
The most simple option with self-explaining interface.
</details>

<details><summary>Vim</summary>
More complex editor with many features. You should get a vim cheat sheet in the beginning.
</details>

<details><summary>Emacs</summary>
More complex editor with many features. You should get a emacs cheat sheet in the beginning.
</details>

# Version Control

<details><summary>git</summary>

 * The [Git Book](https://git-scm.com/book/en/v2) is a good place to start.
 * You can use `git gui` to create commits and `gitk` to view the history.

</details>

<details><summary>GitHub</summary>

Host for git repositories.

 * You can create free private repositories with a student account.

</details>

<details><summary>BitBucket</summary>
Free alternative to GitHub with private repositories.
</details>

# Simple Documents

<details><summary>Markdown + pandoc</summary>

Good for writing pdf documents quickly. Not as nice as LaTeX but good enough for exercises.

 * Can compile markdown to pdf, html and many others.
 * Allows inline html and latex formulas, ...

</details>

# LaTeX

<details><summary>Detexify <a href="http://detexify.kirelabs.org/classify.html">↗</a></summary>
Draw the symbol you need and detexify will tell you the corresponding LaTeX command and package.
</details>

<details><summary>Syntex</summary>

Use LaTeX with `--synctex=1` to link the produced pdf to your LaTeX source code. If you have syntex support in your pdf/ps/dvi viewer and your editor, you can ctrl-click on a paragraph to scroll to it and get it highlighted in the other document.

</details>

<details><summary>latexmk</summary>

Automagically performs all steps needed to create the index, BibTeX/Biber, references, ...

 * You can get a continuous preview with the `-pvc` option.

</details>

<details><summary>JabRef <a href="http://www.jabref.org/">↗</a></summary>
Tool to manage your BibTeX references. You can search and tag the references, link them to pdfs and add summaries.
</details>

<details><summary>IguanaTex <a href="http://www.jonathanleroux.org/software/iguanatex/">↗</a></summary>
PowerPoint plugin to use LaTeX formulas in your document.
</details>

## Editors

<details><summary>TexMaker</summary>
</details>

<details><summary>TeXstudio</summary>
</details>

<details><summary>VS-Code plugin</summary>
</details>

<details><summary>Sublime plugin</summary>

 * LaTeXTools
 * LaTeX-cwl

</details>

<details><summary>LyX <a href="https://www.lyx.org/Screenshots">↗</a></summary>

WYSIWYM editor for documents which uses LaTeX internally and also exports to LaTeX code. The document and formulas are shown similarly to the final document. Mathematical formulas can either be written using the LaTeX code or with the various shortcuts (e.g `Alt-M G A` for alpha (read "alt math Greek alpha"), `Alt-M I` for integrals).

 * You can write raw LaTeX via `ctrl-L` for features that are not natively supported by LyX.

</details>

## Templates

<details><summary>scientific-thesis-template <a href="https://github.com/latextemplates/scientific-thesis-template">↗</a></summary>
Unofficial LaTeX template of Computer Science at University of Stuttgart.
See <a href="http://latextemplates.github.io/scientific-thesis-template/">overview and instructions</a></summary>.

</details>


# Debugging -- C, C++, ...

<details><summary>gdb</summary>

 * You can modify the _startup script_ `~/.gdbinit`. There exists various init files to support _colored output_ ([copy this file in your init file](https://github.com/RAttab/dotfiles/blob/master/colors.gdb)) and many other other features.
 * If you want to debug a program wich takes _command line arguments_ you can pass them like `gdb --args program param1 param2`.
 * You can print the first three elements of _arrays_ using `p *ptr@3`. If you have a 3x2 matrix you can also use `p *ptr@3@2` which will give a clearer structure to the output than `p *ptr@6`.

</details>

<details><summary>gdbgui <a href="https://gdbgui.com/screenshots.html">↗</a></summary>
"Browser-based debugger for C, C++, go, rust, and more"
</details>

<details><summary>Valgrind</summary>

Useful to find difficult _memory bugs_ when gdb doesn't catch them or doesn't give any useful information. Examples are _double free_-bugs, bugs which corrupted the allocator meta data (in this case you might get an error the next time you try to allocate any new memory) or reading _uninitialized memory_.

 * You can use the flag `valgrind --track-origins=yes` to make valgrind track and report where you allocated uninitialized memory.
 * Besides memory checks with the default `--tool=memcheck` there also exist many other tools. E.g. `--tool=cachegrind`, which compute _cache misses_ for the instruction cache and memory cache.
 * Warning: valgrind will make your program run really slow.

</details>

# Profiling -- C, C++, ...

<details><summary>perf</summary>
</details>

<details><summary>Flamegraph <a href="http://www.brendangregg.com/flamegraphs.html">↗</a></summary>

Nice way to [visualize](http://www.brendangregg.com/FlameGraphs/cpuflamegraphs.html) the results of `perf`.

 * `perf script | ~/FlameGraph/stackcollapse-perf.pl | ~/FlameGraph/flamegraph.pl > flamegraph.svg` creates an interactive svg image from the perf script.
 * You can also mix it with some `grep`, `sed`, oder `c++filt`.
 * There also exists a [module](https://github.com/evanhempel/python-flamegraph) for python.

</details>

<details><summary>Valgrind</summary>

 * For measuring _cache misses_. See the valgrind section in 'Debugging'

</details>

<details><summary>c++filt</summary>
Demangles C++ names to make them more readable. Nice in combination with profiler output or flamegraphs.
</details>

# Debugging -- Cuda

<details><summary>cuda-gdb</summary>

Gdb with cuda extension. You can also set _breakpoints in kernels_ and switch between threads to inspect the variables.

 * You can also create an init file `~/cuda-gdbinit`. Just use the same file as for `gdb` if you want colored backtraces.
 * To break on API errors like failed kernel launches or other error codes use `set cuda api_failures stop`.
 * To check for _invalid memory addresses_, you can use `set cuda memcheck on` to enable something like `valgrind --tool=memcheck` for cuda. Warning: This makes your program much slower.
 * TODO: problem with breakpoints on gpu connected to display.

</details>

# Profiling -- Cuda

<details><summary>nvprof</summary>

Command line profiler for Cuda programs. You can also generate a file, which can be imported to `nvvp` using `--analysis-metrics -o file`. This helps with profiling a remote program.

 * You can output the profiling in CSV format with a common time unit using `--csv -u us`.
 * Profiling can be limited to specific kernels using `--kernels my_kernel`, which applies to following `--analysis-metrics`, `--events` or `--metrics` options.
 * You can control the GPUs visible to your program by setting the environment variable `CUDA_VISIBLE_DEVICES`. Example: `CUDA_VISIBLE_DEVICES=0,2` masks out GPU 1. Run `nvidia-smi` to get the number of each GPU.

</details>

# Plotting

<details><summary>matplotlib</summary>
Python library for plotting.
</details>

<details><summary>gnuplot</summary>

Language especially for plotting. Can export to many formats including png, svg, latex.

 * You can use the init file `.gnuplot` to run code or set settings startup
 * Can fit arbitrary parameters to compute a function that approximates the data points using `fit`.
 * You can also plot data using the output of shell commands: `plot '< python gen_data.py'` or `plot '< sed -n "s/^# //p" file'` or even with pipes `plot '< cat data/* | sed -n "s#re=\(.*\)#\1#p"'`

</details>

<details><summary>PGFPlots</summary>

Handy LaTeX package to create plots directly in LaTeX. Can plot data in CSV or gnuplot format. Supports diagrams, graphs, box plots, 3d plots and many more.

 * There are also higher level features as loops and random numbers.
 * Becomes slow for many plots. You can avoid the recomputation of the plots by compiling them in another document into an PDF and include it with `\includegraphics`. This is done automatically if you use `\usepgfplotslibrary{external}` and `\tikzexternalize[prefix=TikzPictures/]` in your preamble.
 * You can use gnuplot to plot your data.

</details>

# PDF viewer

<details><summary>Zathura</summary>
</details>

<details><summary>Ocular</summary>
</details>

# Shells

<details><summary>Fish Shell <a href="https://fishshell.com/docs/current/tutorial.html">↗</a></summary>
Shell with useful autocompletion and many other features.
</details>

<details><summary>ZSH</summary>

Shell with useful autocompletion and many other features.

 * To get started, [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh/) is good to manage your zsh configuration.

</details>

# Job Scheduler

<details><summary>Slurm</summary>

Job manager.

 * `srun --ntasks=42 script.sh` allocates 42 tasks and runs the job in your terminal. The default is one task per node.
 * `srun --ntasks=42 --pty bash` allocates 42 tasks and starts an interactive session. Use `exit` to exit the interactive session.
 * `sbatch --ntasks=1 script.sh` allocates and runs script. script gets _copied_ to an other location and is executed, once there are enough resources available. In contrast to `srun` the script is _only_ run on the first node! You can use `srun` inside the batch script.
 * `squeue` to see the current jobs in the job queue.
 * `scancel` to kill your jobs or revoke them from the queue.
 * `salloc --ntasks=42` allocate recources for yourself, but stay on login node. If you want to use the recources use `srun` afterwards. Useful if one job contains multiple `srun` commands, as you don't have to reallocate recources for each job. Use `exit` to exit the allocation.
 * Use `--job-name="Bob"` to give your job a descriptive name.
 * Use `--time=8:00:00` to set the upper limit for the runtime of your program.
 * If you run a batch script with `srun` or `sbatch` you can also define the command line parameters inside the script using `#SBATCH --ntasks=42`.

```bash
srun -n4 hostname # runs hostname on four nodes
# prints allocated compute nodes

salloc -n4 # allocate four nodes
  hostname
  # print the current login node
  srun hostname # runs hostname on all allocated nodes
  # prints allocated compute nodes
  srun -n2 hostname # runs hostname on two of the allocated nodes
  # prints allocated compute nodes
exit

echo -e '#!/usr/bin/env bash\nhostname' > script.sh
sbatch -n4 script.sh # submits the script
# returns immediately and stores the output of the job into a file
# output file contains only the host name for the first node

echo -e '#!/usr/bin/env bash\nsrun hostname' > script.sh
sbatch -n4 script.sh # submits a script to run hostname on four nodes
# returns immediately and stores the output of the job into a file
# output file contains the host names for all compute nodes

echo -e '#!/usr/bin/env bash\n#SBATCH -n4\n#SBATCH --output myoutfile\nsrun hostname' > script.sh
sbatch script.sh
# prints the host name of all four allocated nodes into `myoutfile`
```

Some more advanced stuff:

 * Slurm sets various environment variables which you can use in your scripts.
 * You can queue multiple versions of one `sbatch` job using [task arrays](https://slurm.schedmd.com/job_array.html) with `--array=0-17`. You can use the environment variable `SLURM_ARRAY_TASK_ID` in your scripts to find out which array task you are executing.

```
# program we want to run with different parameters
echo "sleep 3;echo $1" > smartprogram.sh
# batch script which uses the array id to change the parameters
echo -e '#!/usr/bin/env bash\nsrun bash smartprogram.sh $SLURM_ARRAY_TASK_ID' > script.sh
# run a program multiple times
sbatch -n1 --array=3-5 script.sh
# outputs the numbers 3,4 and 5 in three output files
```

</details>

# Libraries

<details><summary>Python</summary>

 * Numpy for efficient array/vector/matrix operations.
 * [Scipy](https://docs.scipy.org/doc/scipy/reference/index.html) offers many useful algorithms. E.g. linear algebra, FFT and optimization.
 * Sympy for symbolic computations, integrals and derivatives.
 * Matplotlib for plotting.

</details>

<details><summary>FEM</summary>

 * FeniCS: Python
 * deal.II: C++

</details>

# Code Documentation

<details><summary>Doxygen</summary>
</details>

<details><summary>Sphinx</summary>
</details>
