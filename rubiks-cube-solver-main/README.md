Here's a well-structured README.md for your Rubik's Cube Solver project:

```markdown
# Rubik's Cube Solver

A C++ implementation of a Rubik's Cube solver using various algorithms and data structures.

## Features

- Multiple cube representations:
  - 3D array model
  - 1D array model
  - Bitboard representation
- Several solving algorithms:
  - Depth-First Search (DFS)
  - Breadth-First Search (BFS)
  - Iterative Deepening DFS (IDDFS)
  - IDA* with pattern database heuristics
- Pattern database support:
  - Corner pattern database for heuristic calculations
  - Database generation utility

## Building

1. Clone the repository
2. Ensure you have CMake and a C++ compiler installed
3. Build the project:
   ```
   mkdir build
   cd build
   cmake ..
   make
   ```

## Usage

The main program demonstrates various cube operations and solving algorithms. You can modify the main.cpp to test different configurations:

```cpp
// Example usage:
RubiksCubeBitboard cube;
auto shuffleMoves = cube.randomShuffleCube(13);
IDAstarSolver<RubiksCubeBitboard, HashBitboard> solver(cube, "cornerDatabase.txt");
auto solution = solver.solve();
```

## Algorithms Implemented

### DFSSolver
- Depth-limited DFS solver
- Configurable depth limit
- Uses hashing for state tracking

### BFSSolver
- Complete BFS solver
- Guaranteed to find optimal solution (if one exists)
- Uses more memory than DFS

### IDDFSSolver
- Iterative deepening DFS
- Combines benefits of DFS and BFS
- Configurable maximum depth

### IDAstarSolver
- IDA* algorithm with pattern database heuristic
- Uses corner pattern database for efficient solving
- Currently configured to use pre-generated database

## Pattern Databases

The project includes functionality to generate and use pattern databases:

1. `CornerDBMaker` - generates a database of corner positions
2. Pre-generated databases can be loaded for faster solving

To generate a new database:
```cpp
CornerDBMaker dbMaker("database.txt", 0x99);
dbMaker.bfsAndStore();
```

## File Structure

```
Rubiks-Cube-Solver/
├── Model/                # Cube representations
│   ├── RubiksCube3dArray.cpp
│   ├── RubiksCube1dArray.cpp
│   └── RubiksCubeBitboard.cpp
├── Solver/               # Solving algorithms
│   ├── DFSSolver.h
│   ├── BFSSolver.h
│   ├── IDDFSSolver.h
│   └── IDAstarSolver.h
├── PatternDatabases/     # Pattern database code
│   ├── CornerPatternDatabase.h
│   └── CornerDBMaker.h
└── main.cpp              # Demonstration program
```

## Future Work

- Implement edge pattern databases
- Add more efficient heuristic functions
- Optimize memory usage for BFS
- Create GUI for visualization

## Author

Lakshya Mittal - Initial implementation
```

This README provides:
1. Clear project overview
2. Building instructions
3. Usage examples
4. Algorithm explanations
5. File structure
6. Future work suggestions
