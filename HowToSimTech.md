# Editors

<details><summary>vs code</summary>
</details>

<details><summary>atom</summary>
</details>

# CLI Editors

<details><summary>nano</summary>
Die am einfachsten zu benutzende Option. Mit selbsterklärender Benutzung.
</details>

<details><summary>Vim</summary>
Komplexerer Command Line Editor mit komplexerer Bedinung aber extrem vielen Features. Am Anfang sollte man sich ein Vim-Cheat-Sheet googeln.
</details>

<details><summary>Emacs</summary>
Komplexerer Command Line Editor mit komplexerer Bedinung aber extrem vielen Features. Am Anfang sollte man sich ein Emacs-Cheat-Sheet googeln.
</details>

# Version Control

<details><summary>git</summary>

 * Das [Git Book](https://git-scm.com/book/en/v2) ist ein guter Startpunkt.
 * `git gui` um Commits zu erstellen und `gitk` um die History anzuschauen.

</details>

<details><summary>GitHub</summary>
Host für Git-Repositories.

 * Wenn man sich einen Studenten Account zulegt, kann man auch private Repos machen.

</details>

<details><summary>BitBucket</summary>
Kostenlose alternative zu GitHub mit privaten Repositories.
</details>

# Simple Documents

<details><summary>Markdown + pandoc</summary>
Good for writing pdf documents quickly. Not as nice as LaTeX but good enough for exercises.

 * Can compile markdown to pdf, html and many others.
 * Allows inline html, latex, latex formulas, ...

</details>

# LaTeX

<details><summary><a href="http://detexify.kirelabs.org/classify.html">Detexify</a></summary>
Male das Symbol das du brauchst und Detexify sagt dir den LaTeX-Befehl und das zugehörige Package.
</details>

<details><summary>Syntex</summary>
Wenn man LaTeX mit der Option `--synctex=1` kompiliert, wird eine `*.synctex.gz` Datei erstellt, die die Vorwärts- und Rückwärtssuche ermöglicht. Das heißt konkret, dass man im Editor bzw. PDF/PS/DVI-Viewer, der das unterstützt, durch Strg + Klick auf eine Stelle, jeweils zu der selben Stelle im anderen Programm kommt.
</details>

<details><summary>latexmk</summary>
Perl-Skript das automatisch die nötige Anzahl an Schritten für Index, BibTeX/Biber, Referenzen, etc. ausführt.

 * Die Option `Option -pvc` bewirkt automatisch eine kontinuierliche Vorschau.

</details>

<details><summary>JabRef</summary>
Tool zum Verwalten von Literatur für Latex auf Basis von BibTeX. Man kann suchen, PDFs verknüpfen und Zusammenfassungen schreiben.
</details>

<details><summary><a href="http://www.jonathanleroux.org/software/iguanatex/">IguanaTex</a></summary>
Plugin für PowerPoint um Latex-Formeln direkt einzubinden.
</details>

## Editors

<details><summary>TexMaker</summary>
</details>

<details><summary>VS-Code plugin</summary>
</details>

<details><summary>Sublime plugin</summary>

 * LaTeXTools
 * LaTeX-cwl

</details>

<details><summary><a href="https://www.lyx.org/Screenshots">Lyx</a></summary>
WYSIWYM Editor für Dokumente. Formeln werden direkt (fast) so gesetzt wie sie später aussehen. Verwendet intern LaTeX und kann auch den LaTeX Code exportieren.  Mit ein paar wenigen Shortcuts kann man sehr schell mathematische Formeln schreiben (z.B. `Alt-M G A` für Alpha (also "Alt Math Greek Alpha"), oder `Alt-M I` für Integrale).

 * Mit `Strg-L` kann man inline LaTeX schreiben, wenn der Editor bestimmte Funktionen nicht unterstützt.

</details>

# Debugging -- C, C++, ...

<details><summary>gdb</summary>

 * You can modify the _startup script_ `~/.gdbinit`. There exists various init files to support _colored output_ ([copy this file in the init file](https://github.com/RAttab/dotfiles/blob/master/colors.gdb)) and many other other features.
 * If you want to debug a program wich takes _command line arguments_ you can pass them like `gdb --args program param1 param2`.
 * You can print the first three elements of _arrays_ using `p *ptr@3`. If you have a 3x2 matrix you can also use `p *ptr@3@2` which will give a clearer structure to the output than `p *ptr@6`.

</details>

<details><summary>Valgrind</summary>
Useful if you have hard to find _memory bugs_ when gdb doesen't catch them or doesen't give any useful information. Examples are _double free_-bugs, bughs which corrupted the allocator meta data (in this case you might get an error the next time you try to allocate any new memory) or reading _uninitialized memory_.

 * You can use the flag `valgrind --track-origine=yes` to make valgrind track and report where you allocated uninitialized memory.
 * Besides memory checks with the default `--tool=memcheck` there also exist many other tools. E.g. `--tool=cachegrind` wich compute _cache misses_ for the instruction cache and memory chache.
 * Warning: valgrind will make you program run really slow.

</details>

# Profiling -- C, C++, ...

<details><summary>perf</summary>
</details>

<details><summary><a href="http://www.brendangregg.com/flamegraphs.html">Flamegraph</a></summary>

Nice way to [visually present](http://www.brendangregg.com/FlameGraphs/cpuflamegraphs.html) the results of `perf`.

 * There also exists a [module](https://github.com/evanhempel/python-flamegraph) for python.

</details>

<details><summary>Valgrind</summary>

 * For measuring _cache misses_. See the valgrind section in 'Debugging'

</details>

# Debugging -- Cuda

<details><summary>cuda-gdb</summary>
Gdb with cuda extension. You can also set _breakpoints in kernels_ and switch between threads to inspect the variables.

 * To check for _invalid memory addresses_, you can use `set cuda memcheck on` to enable something like `valgrind --tool=memcheck` for cuda
 * TODO: problem with breakpoints on gpu connected to display.

</details>

# Plotting

<details><summary>matplotlib</summary>
Python library for plotting.
</details>

<details><summary>gnuplot</summary>
Language especially for plotting. Can export to many formats including png, svg, latex.

 * You can use the init file `.gnuplot` to run code or set settings startup
 * Can fit arbitrary parameters to compute a function to approximate the data points.
 * You can also plot data using the output of shell commands: `plot '< python gen_data.py'` or `plot '< sed -n "s/^# //p" file'` or even with pipes `plot '< cat data/* | sed -n "s#re=\(.*\)#\1#p"'`

</details>

# PDF viewer

<details><summary>Zathura</summary>
</details>

<details><summary>Ocular</summary>
</details>
