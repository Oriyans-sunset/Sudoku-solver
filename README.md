# Sudoku Solver

A fast, easy-to-use Sudoku solver that can solve standard 9x9 Sudoku puzzles. This repository contains a solver implementation, utilities to parse puzzles, and example puzzles and tests. The solver is designed to be simple to integrate into other projects or to use from the command line.

## Table of Contents
- About
- Features
- Installation
- Usage
  - Command-line
  - Library / API
- Input Formats
- Examples
- Algorithm & Approach
- Performance
- Tests
- License

## About
This project provides a reliable Sudoku solving engine and a small set of tools to load puzzles, solve them, and print or export the solutions. It is suitable for educational purposes, integration into larger applications (puzzle apps, solvers, web demos), and for benchmarking different solving techniques.

## Features
- Solve standard 9x9 Sudoku puzzles (empty cells allowed).
- Accepts simple human-readable puzzle formats (see Input formats).
- Fast backtracking-based solver with constraint propagation enhancements.
- Optional utilities for validating puzzles and formatting output.
- Simple tests and example puzzles included.

## Installation
1. Clone the repository:
   ```
   git clone https://github.com/Oriyans-sunset/Sudoku-solver.git
   cd Sudoku-solver
   ```

2. Install dependencies:
   - Python (example)
     ```
     python3 -m venv venv
     source venv/bin/activate
     pip install -r requirements.txt
     ```

   - Node.js (example)
     ```
     npm install
     ```

## Usage
The repository can be used as a standalone CLI tool or as a library embedded in your code. Below are example usages—adjust to the actual script/entry point found in the repo.

### Command-line (examples)
- Provide a puzzle as an 81-character string (use `.` or `0` for blanks):
  ```
  # Python example
  python solve.py "53..7....6..195....98....6.8...6...34..8..6..2...3.6....28....419..5....8..79"
  ```

- Read a puzzle from a file:
  ```
  python solve.py --file puzzles/example1.txt
  ```

### Library / API (conceptual)
- Import the solver and call a solve function:
  ```py
  from sudoku_solver import solve, parse_puzzle

  puzzle = parse_puzzle("53..7....6..195....98....6.8...6...34..8..6..2...3.6....28....419..5....8..79")
  solution = solve(puzzle)
  print(solution)  # prints solved board or None if unsolvable
  ```

## Input Formats
The solver accepts the following common formats:
- 81-character string: row-major, use digits 1-9 for filled cells and `.` or `0` for empty cells.
- Multi-line 9x9 grid: 9 lines with 9 characters each (digits or `.`).
- Plain text files with one puzzle per line or separated by blank lines (adjust parser as necessary).

## Examples
Given this puzzle (dots represent blanks):
```
53..7....
6..195...
.98....6.
8...6...3
4..8.3..1
7...2...6
.6....28.
...419..5
....8..79
```

Command:
```
python solve.py "53..7....6..195....98....6.8...6...34..8..6..2...3.6....28....419..5....8..79"
```

Expected output (solved grid):
```
534678912
672195348
198342567
859761423
426853791
713924856
961537284
287419635
345286179
```

## Algorithm & Approach
This solver uses a depth-first backtracking search with common Sudoku optimizations:
- Constraint propagation (keep track of possible candidates for each cell).
- Heuristic choice of the next cell to try (choose the cell with the fewest candidates).
- Early pruning when a contradiction is found.

Alternative algorithms (optional enhancements):
- Dancing Links (Knuth's Algorithm X) to solve via exact cover.
- Advanced human-like strategies (naked/hidden pairs, X-wing, swordfish) for faster solving or for explaining steps.

## Performance
- Typical 9x9 puzzles solve instantly; most puzzles are solved in milliseconds with the backtracking + constraint improvements.
- Hardest-known puzzles may take longer but are still solved quickly compared to naive brute-force.

## Tests
Include unit tests for:
- Parsing different input formats.
- Solving known puzzles and validating results.
- Detecting unsolvable or invalid puzzles.

Run tests (example):
```
# Python (pytest)
pytest
```

## License
Add the license used for this repository (for example, MIT). If none is present, consider adding one to clarify usage rights.

Example:
```
MIT License
```