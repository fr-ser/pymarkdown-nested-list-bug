# PyMarkdown Nested List Bug

This repo is there to reproduce a bug in PyMarkdown.

Here is the bug: <https://github.com/jackdewinter/pymarkdown/issues/1357>

## Setup

The repo uses poetry to manage the dependencies, but any other way to install `pymarkdownlnt` is also fine.

1. Install Python (this example uses 3.12)
2. Install Poetry
3. Create a virtual environment and install dependencies via poetry: `poetry install --no-root`

## Reproduction Steps

1. Run command: `poetry run pymarkdown scan bug.md`

   - See this output:

     ```txt
     bug.md:17:5: MD005: Inconsistent indentation for list items at the same level [Expected: 3; Actual: 4] (list-indent)
     ```

   - as the item at line 17 is in a list with a double digit number it should be 4 (and not 3)
