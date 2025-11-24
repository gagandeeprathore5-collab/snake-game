🐍 Game Overview
The game features a snake (represented by green blocks) that moves across a grid-based canvas, attempting to eat food (represented by red circles).

Objective: Eat as much food as possible to increase the score and the snake's length.

Controls: The snake is controlled using the arrow keys or WASD keys (W/Up, S/Down, A/Left, D/Right).

Game Over Conditions: The game ends if the snake collides with the canvas boundary (runs into a wall) or collides with its own body.

Scoring and Speed: Each piece of food eaten increases the score by 1. The game speed incrementally increases (interval decreases) with every piece of food eaten, making the game progressively more challenging.

🛠️ Key Components and Mechanisms
1. Tkinter Setup and Constants
GUI: The game uses the tk.Tk() root window and a tk.Canvas for drawing the game elements.

Grid System: The game area is divided into a grid, with constants like CANVAS_WIDTH, CANVAS_HEIGHT, and GRID_SIZE defining the dimensions. The snake and food positions are managed using grid coordinates (x, y).

Appearance: Constants define the colors for the background, snake, food, and text.

2. Snake Representation
The snake's body is stored as a collections.deque (double-ended queue) of (x, y) grid coordinates. Using a deque allows for efficient addition of a new head (using appendleft) and efficient removal of the tail (using pop) during movement.

3. Movement and Direction
The move_snake method handles the core game logic.

The snake's movement direction is stored in self.direction (e.g., (1, 0) for right).

Input Buffering: User input changes the self.next_direction, which is only applied in the next game loop iteration to self.direction. This prevents the snake from immediately turning 180 degrees into itself, a common rule in Snake games.

4. Game Loop
The game's flow is managed by the game_loop method, which is scheduled to run repeatedly using self.root.after(self.game_speed, self.game_loop).

In each iteration:

move_snake() is called to update the snake's position.

draw_elements() is called to redraw the snake and food on the canvas.

The game loop is scheduled again after the current self.game_speed delay (in milliseconds).

5. Collision and Food Logic
Food Generation (_generate_food): Food is placed randomly on an empty grid square that is not occupied by the snake.

Eating: If the new head position is the food_pos, the snake is not shortened (no pop() is called), effectively making it grow by one segment. A new food item is generated, and the score increases.

Collision (_check_collision): This method checks if the new head position is outside the grid bounds or if it overlaps with any part of the snake's existing body (self-collision).

6. Game State and Reset
Game Over (end_game): Sets self.game_over = True, displays the final score and a "GAME OVER" message, and shows the Restart button.

Reset (reset_game): Re-initializes all game state variables (snake, direction, score, speed) to their initial values, clears the messages, hides the restart button, and prepares for a new game.<img width="1920" height="1080" alt="Screenshot (57)" src="https://github.com/user-attachments/assets/1fd5d172-fa6b-49d7-b76a-af6357ab00d9" />

