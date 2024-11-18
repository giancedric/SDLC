# Pseudo Code

## Team members: Gian and V

### Start

Initialize game -
Initialize game grid (size depends on screen/device)
Initialize score = 0
Initialize highscore = 0 (or highest score last recorded)
Initialize game speed = normal
Intialize elements within sequence = ornaments 1, 2, 3, 4

Start game loop -
While game is running:
    Display chirstmas tree sprite
    Display ornaments 1, 2, 3, and 4
    Display score and settings/menu
    Random sequence

### Process

    for each ornament in sequence:
        Light up ornament
        Turn off ornament
    
### Input

    for each ornament == player input:
        Light up ornament
        Turn off ornament

### Output

    If sequence != player input:
        Display final score
        Display "Restart"
    else:
        Display "Next round!"
        score += 1

### End

    If player loses or exits the game:
        Display final score
        Display "Restart" and "Quit" 
        if score > highscore then
            highscore = score
            Display "Highscore: "
