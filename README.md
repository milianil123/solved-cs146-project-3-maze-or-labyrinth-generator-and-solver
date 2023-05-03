Download Link: https://assignmentchef.com/product/solved-cs146-project-3-maze-or-labyrinth-generator-and-solver
<br>
<strong>Maze or Labyrinth Generator and Solver  </strong>(see greek mythology: Ariadne’s thread)

The goal of this project is to write a program that will automatically generate and solve mazes. Each time you run the program, it will generate and print a new random maze and the solution. You will use depth-first search (DFS) and breadth-first search (BFS). Submit your code, and also JUnit test cases for it.

<ol>

 <li>Generating a Maze:</li>

</ol>

To generate a maze, first start with a grid of rooms with walls between them. The grid contains r rows and r columns for a total of r*r rooms. For example, Figure 1 is a 4×4 grid of 16 rooms. The missing walls at the top left and bottom right of the maze border indicate the starting and finishing rooms of the maze.




Our objective here is to create a <em>perfect</em> maze (see Figure 3), the simplest type of maze for a computer to generate and solve. A perfect maze is defined as a maze which has one and only one path from any point in the maze to any other point. This means that the maze has no inaccessible sections, no circular paths, no open areas.

Now, begin removing interior walls to connect adjacent rooms. The difficultly in generating a perfect maze is in choosing which walls to remove. Walls should be removed to achieve the following maze characteristics:

<ol>

 <li>Randomized: To generate unpredictable different mazes, walls should be selected randomly as candidates for removal.</li>

 <li>Single solution: There should be only one path between the starting room and the finishing room (for simplicity always use as starting and finishing rooms the ones in Figure 1, i.e. , starting the upper left room and finishing the lower right room) . Unnecessarily removing too many walls will make the maze too easy to solve. Therefore, a wall should not be removed if some other path already connects the two rooms on either side of the wall. For example, in Figure 2, the wall between <em>a</em> and <em>f</em> should not be removed because walls have previously been removed that create <em>a</em> path between <em>a</em> and <em>f</em> through <em>b, c, d, e</em>.</li>

 <li>Fully connected: Enough walls must be removed so that every room (therefore also the finishing room) is reachable from the starting room. There must be no rooms or areas that are completely blocked off from the rest of the maze.</li>

</ol>

We now give a simple maze generation algorithm and that uses Depth First Search. Here’s the DFS algorithm written as pseudocode:

create a CellStack (LIFO) to hold a list of cell locations set TotalCells= number of cells in grid choose the starting cell and call it CurrentCell set VisitedCells = 1




<strong>while</strong> VisitedCells &lt; TotalCells find all neighbors of CurrentCell with all walls intact <strong>if</strong> one or more found choose one at random knock down the wall between it and CurrentCell push CurrentCell location on the CellStack make the new cell CurrentCell

add 1 to VisitedCells

<strong>else </strong>pop the most recent cell entry off the CellStack make it CurrentCell




Note that we can eliminate recursion by the use of a stack (this DFS implementation differs from the one we have seen in class).

When the while loop terminates, the algorithm is completed. Every cell has been visited and thus no cell is inaccessible. Also, since we test each possible cell to see if we’ve already been there, the algorithm prevents the creation of any open areas, or paths that circle back on themselves.




<ol>

 <li>Model a maze:</li>

</ol>

Represent the maze as a graph data structure, where rooms (cells) are vertices and removed walls are edges between vertices. For help you can use the book <u>“Data Structures and Algorithms in</u> <u>Java”</u> (Chapter 13). You can use directions north, south, west and east for the neighbors of each cell.

<ol>

 <li>Solving the Maze:</li>

</ol>

After generating a maze, your program should solve the maze (find a path from the starting room to the finishing room)

<ol>

 <li>using DFS and</li>

 <li>using BFS.</li>

</ol>

Each search algorithm will begin at the starting room and search for the finishing room by traversing wall openings. The search should terminate as soon as the finishing room is found. For each search algorithm, you will output the order in which rooms where visited and indicate the shortest solution path from starting to finishing room.

Input:  The program should accept the number of rows and columns r of the maze (use values like r=4, 5, 6, 7, 8, 10).

Output: The program should print and save in a file the maze, then the DFS solution, and then the BFS solution. The maze is printed in ASCII using the vertical bar ‘|’ and dash ‘-‘ characters to represent walls, ‘+’ for corners, and space character for rooms and removed walls. The starting and finishing rooms should have exterior openings as shown.




For the DFS and BFS solutions, the maze should be output twice, one for each algorithm. The first maze output for each algorithm should show the order that the rooms were visited by the algorithm. The maze should be printed exactly as above except that rooms should be printed with the loworder digit of the visitation order number. The starting room is ‘0’. Unvisited rooms should remain a space character. The second maze output for each algorithm should show the shortest solution path, using hash ‘#’ character for rooms and wall openings on the solution path. Note: you don’t have to add “#” in between cells (like in the example). The path also is given on a single line and consists of the index of printed cells, separated by single spaces. On the next line the length of the solution path, and on the following line the total number of cells visited, including cells that were not completely explored (i.e., colored grey).

You will need to view the output in a fixed-width font.

Following is sample output for the maze in Figure 3:




DFS:







Path: (0,0) (1,0) (2,0) (2,1) (3,1) (3,2) (2,2) (2,3) (3,3)

Length of path: 9

Visited cells: 11




BFS:




Path: (0,0) (1,0) (2,0) (2,1) (3,1) (3,2) (2,2) (2,3) (3,3)

Length of path: 9

Visited cells: 13




<ol>

 <li>Testing</li>

</ol>

First, create and solve your own maze (see examples in sample.zip) and store them as ASCII. It is easy to see in the ASCII if you have a perfect maze and if the solution is correct. Use the ASCII for the JUnit cases (is the printing equal to the one given in ASCII).  Note: Every time you run your program the same “random” maze should be created and solved (see help with random seed). Test on your mazes as well as mine.

<strong>Programming Standards:  </strong>

<ul>

 <li>Your header comment must describe what your program does.</li>

 <li>You must include a comment explaining the purpose of every variable or named constant you use in your program.</li>

 <li>You must use meaningful identifier names that suggest the meaning or purpose of the constant, variable, method, etc.</li>

 <li>Precede every major block of your code with a comment explaining its purpose. You don’t have to describe how it works unless you do something tricky.</li>

 <li>You must use indentation and blank lines to make control structures more readable.</li>

</ul>