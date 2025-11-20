# EECS 118 -- P1: Searching for Something (Lab 2)

Version 0.1

In this project lab, you will debug your search algorithm from lab 1, and inspect and analyze the input and output of your search algorithms.

Note: Details about how to submit your work for this project lab will be provided later on Canvas assignments page.

---

## Instructions

See `README.md` for Lab 1 for setup and implementation instructions.

Add the following configuration to your `.vscode/launch.json` to run and debug your DFS implementation on the `tinyMaze`:

```json
{
	"name": "D.L2.DFS.TinyMaze",
	"type": "python",
	"request": "launch",
	"program": "${workspaceFolder}/p1_search/catman.py",
	"console": "integratedTerminal",
	"justMyCode": false,
	"stopOnEntry": false,
	"cwd": "${workspaceFolder}/p1_search",
	"args": [
		"-l", "tinyMaze",
		"-p", "SearchAgent",
		"-a", "fn=depthFirstSearch"
	]
}
```

[HINT] You can duplicate the above configuration and modify the `-l` argument to test on different mazes, such as `mediumMaze`.

---

## P2 Exercises

### E21 -- Test your debugging setup

1. Set a breakpoint at the beginning of your `depthFirstSearch` function in `p1_Search.py`.
2. Run the `D.L2.DFS.TinyMaze` configuration in VSCode.

Your program should pause at the breakpoint, allowing you to step through the code and inspect variables.

3. Locate the following GUI elements when the program is paused:
   - Activity Bar (vertical bar on the left side)
	 - Run and Debug (play button with a bug icon on the activity bar on the left)
	 - VARIABLES section (top left panel after clicking Run and Debug)
	 - WATCH section (below VARIABLES section)
	 - CALL STACK section (below WATCH section)
	 - BREAKPOINTS section (bottom left panel)
	 - DEBUG CONSOLE tab (bottom panel, next to TERMINAL tab)
    	 - Use `Ctrl/Cmd + Shift + Y` to toggle the DEBUG CONSOLE panel.
	 - DEBUG TOOLBAR (top center panel below the main menu, appears floating when debugging starts)

4. Try using the DEBUG TOOLBAR buttons to step over, step into, and continue execution.


### E22 -- Inspect search algorithm input

1. While paused at the beginning of `depthFirstSearch`, add a WATCH expression for `problem`.
2. Expand the `problem` variable in the VARIABLES section to inspect its attributes and methods.
3. Locate and note down the following information:
	 - The start state of the problem.
	 - The goal state(s) of the problem.
	 - The successors of the start state (you can call `problem.getSuccessors(problem.getStartState())` in the DEBUG CONSOLE to see this).
4. In the DEBUG CONSOLE, execute the following commands to further inspect the problem:
	 ```python
	 problem.getStartState()
	 ```
	 What is the output? Is it a state? What is the type of this state? Execute:
	 ```python
	 type(problem.getStartState())
	 ```
	 What is the output type? Is it what you expected?
	 
5. Next, execute:
	 ```python
	 problem.isGoalState(problem.getStartState())
	 ```
	 What is the output? Does it make sense given the start state and goal state(s) you noted earlier?
	 
	 
6. Finally, can you guess which state will return `True` when passed to `problem.isGoalState()`? Try to find such a state by inspecting the maze layout in the GUI. To test your guess, execute:
	 ```python
	 problem.isGoalState(your_guessed_state)
	 ```
	 Replace `your_guessed_state` with the state you think is the goal.

### E23 -- Create your own maze layout

1. Open the `p1_search/layouts` directory.
2. Open an existing layout file, such as `tinyMaze.lay`, to understand the format. Can you guess how the layout is represented in the file?
3. Create a new file named `myMaze.lay` (or any name ending in `.lay`). You can copy and paste from an existing layout file to get started.
4. Modify the layout to create your own maze. Block out the path that your catman chose (by running DFS on `tinyMaze`).
5. Save your new layout file.
6. Add a new configuration to your `.vscode/launch.json` to run your custom maze layout:

```json
{
	"name": "D.L2.DFS.MyMaze",
	"type": "python",
	"request": "launch",
	"program": "${workspaceFolder}/p1_search/catman.py",
	"console": "integratedTerminal",
	"justMyCode": false,
	"stopOnEntry": false,
	"cwd": "${workspaceFolder}/p1_search",
	"args": [
		"-l", "myMaze",
		"-p", "SearchAgent",
		"-a", "fn=depthFirstSearch"
	]
}
```
7. Run the new configuration in VSCode to see if your catman can navigate your custom maze layout. How did the new layout affect the search process?

### E24 -- Contemplation and Reflection

1. When does your catman start to move on the maze? Does it move when you are searching (running DFS)? Before? After? (hopefully not never!)
2. Does that make this algorithm an online or offline search algorithm? Why?
3. If you add a breakpoint right before you return the path to the goal in your `depthFirstSearch` function, can you inspect the path variable? What does it contain?
4. What happens if you modify one of the actions in the path variable before returning it? Does catman follow the modified path?


---

That's it for now.
