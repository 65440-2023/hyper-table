# [Hyper-Table](https://65440-2023.github.io/hyper-table/)

In discrete mathematics, especially theoretical computer science,
it is common to have a family of problems characterized by a finite set of
discrete parameters, and have a result (or open problem) for each problem
in the family.  How can we best organize this high-dimensional matrix of
information into a human-readable 2D table?

[***Hyper-Table***](https://65440-2023.github.io/hyper-table/)
is a tool for exploring the space of possible table layouts,
assuming the table must explicitly represent the entire space of problems.
You can drag around which parameters should be on the horizontal vs. vertical
axis, and in what priority order they should be expanded.

The tool comes with several example results tables from real papers
for you to experiment with.  Select one from the drop down.
You can also upload a [custom data file](#input-format).

This tool was built to illustrate the forthcoming paper
“Hardness Table Layout Hardness Table”
by MIT Hardness Group, Josh Brunner, Andy Tockman, Frederick Stock, Della Hendrickson, Hayashi Layers, Timothy Gomez, Erik D. Demaine, Jenny Diomidova (2025).
In particular, it includes several example tables from that paper.

## Input Format

The input file format is
[Tab-Separated Values (TSV)](https://en.wikipedia.org/wiki/Tab-separated_values),
except that lines starting with `%` are treated as comments.
The input consists of two parts, separated by a blank row (line).

Part 1 lists all the parameters and their possible values,
alternating with cell background color:

| Part 1 Example | | | | | |
|---|---|---|---|---|---|
| parameter 1 | value 1 | cell color 1 | value 2 | cell color 2 | ... |
| parameter 2 | value 1 | cell color 1 | value 2 | cell color 2 | ... |
| ... | ... | ... | ... | ... | ... |
| *[blank line]* | | | | | |

Part 2 starts with two rows that list which parameters to enumerate in the
horizontal and vertical dimension, respectively.
Then it lists all results, which list cell content, cell color,
and then pairs of parameters and their values
(where all unspecified parameters can take arbitrary values).

| Part 2 Example | | | | | | |
|---|---|---|---|---|---|---|
| horizontal param 1 | horizontal param 2 | ... |
| vertical param 1 | vertical param 2 | ... |
| result content 1 | cell color 1 | param 1 | value 1 | param 2 | value 2 | ... |
| result content 2 | cell color 2 | param 1 | value 1 | param 2 | value 2 | ... |
| ... | ... | ... | ... | ... | ... | ... |

If multiple results apply to the same cell, the earlier result takes precedence.
For example, you might want the last line to specify `open` with no parameters,
to cover every cell not otherwise specified by a result.
