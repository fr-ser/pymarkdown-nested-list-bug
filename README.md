# PyMarkdown Nested List Bug

This repo is there to reproduce a bug in PyMarkdown.

## Setup

The repo uses poetry to manage the dependencies, but any other way to install `pymarkdownlnt` is also fine.

1. Install Python (this example uses 3.12)
2. Install Poetry
3. Create a virtual environment and install dependencies via poetry: `poetry install --no-root`

## Reproduction Steps

1. Run command: `poetry run pymarkdown scan bug.md`

   - See this output:

     ```txt
     bug.md:14:5: MD007: Unordered list indentation [Expected: 4, Actual=5] (ul-indent)
     bug.md:15:5: MD007: Unordered list indentation [Expected: 4, Actual=5] (ul-indent)
     ```

   - in reality the indentation is already at 4

2. Run command: `poetry run pymarkdown fix bug.md`

   - This command always keeps "changing" the file and never stabilizes
   - The only change that is done is removing a space from the second item
     - This results in this scan output:

       ```txt
       bug.md:14:5: MD007: Unordered list indentation [Expected: 4, Actual=5] (ul-indent)
       bug.md:15:4: MD005: Inconsistent indentation for list items at the same level [Expected: 4; Actual: 3] (list-indent)
       ```
