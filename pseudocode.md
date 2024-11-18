# Pseudo Code

## Team members: Gian and V

### Start


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