# Festive Focus

# 1. Unit Testing the Game Mechanics

## 1. Sequence Generation

### Key Questions

- Is the sequence generated randomly?
- Does each round correctly add a new step to the sequence?
- Does the sequence persist accurately across rounds?

### Example Tests

- Test that a new step is added to the sequence after each round.
- Ensure that the sequence is randomly generated.
- Verify that the sequence does not reset mid-game unless the player loses.

## 2. User Input Matching

### Key Questions

- Does the game correctly detect when the user’s input matches the sequence?
- Does the game handle mismatched input properly by ending the game or resetting?

### Example Tests

- Test that input is validated step-by-step against the generated sequence.
- Ensure that incorrect input ends the game and displays the correct feedback.
- Verify that matched input progresses the game to the next round.

## 3. Button Interaction

### Key Questions

- Do the buttons light up or play sounds when pressed?
- Are buttons disabled while the sequence is playing to prevent user interference?

### Example Tests

- Verify that the correct button lights up during the sequence display.
- Test that buttons do not respond to user input during the sequence playback.
- Ensure button interactions (like lighting or sound) match their intended function.

## 4. Score and Progress Tracking

### Key Questions

- Does the game track the user’s score based on correct inputs or rounds completed?
- Does the game increase difficulty by adding new steps or speeding up sequences?

### Example Tests

- Test that the score increases after each successfully completed round.
- Verify that the sequence playback speed increases after specific rounds.
- Ensure progress resets when the game restarts.

## 5. Game State Management

### Key Questions

- Does the game reset properly when restarted?
- Does the game handle "Game Over" scenarios correctly?

### Example Tests

- Verify that all variables (score, sequence, and round) reset on a new game.
- Ensure the “Game Over” message appears upon failure and allows restarting.

## 6. Visual and Audio Feedback

### Key Questions

- Are sound and visual effects synchronized with button presses and sequence playback?
- Does the feedback enhance the user’s ability to follow the sequence?

### Example Tests

- Test that the correct sound plays for each button during the sequence.
- Verify that visual effects (like button lighting) activate and deactivate as expected.
- Ensure that audio and visual feedback align perfectly during playback.

# Part 2: Logic Testing the Game Mechanics

# A) Identifying Calculations

## 1. Score Calculations

- Does the score increase correctly for every successful match?
- Are penalties applied for incorrect sequences?

## 2. Level Progression

- Does the game become more challenging as levels increase (e.g., longer sequences or shorter time limits)?

## 3. Game State Management

- Does the game properly reset when restarted?
- Are game-over scenarios handled correctly?

# B) Logic Tests for Verification

## 1. Score Calculations

#### Test Case 1: Click the corresponding ornaments in the correct sequence

- Input: Player clicks the correct sequence of ornaments.
- Expected Outcome: +1 points added to the score.
- Test Data:
- Initial score: 0
- After one match: Score = 1

### Test Case 2: Click incorrectly

- Input: Player click the corresponding ornaments in wrong sequence.
- Expected Outcome: No points added and a Game over
- Test Data:
- Initial score: 50
- After wrong sequence: Score = Game Over

## 2. Game State Management

#### Test Case 1: Game resets correctly after loss

- Input: Player chooses to restart the game.
- Expected Outcome: Score resets to 0 and sequence clears.

#### Test Case 1: Game stops after player loses

- Input: Player click the corresponding ornaments in wrong sequence.
- Expected Outcome: a Game over

## 3. Boundary Testing the Game Mechanics

### A) Identifying Scenarios

### Maximum Score

- What happens when the score reaches its upper limit?
- Does the game display the correct score or overflow?

### Minimum Score

- Can the score drop below 0?
- Should the score stop at 0, or can it go negative?

### Maximum Level

- What happens if the player continues leveling up past the expected maximum level?
- Does the game’s difficulty or sequence length scale properly?

### Maximum Sequence Length

- Can the game handle a long sequence without crashing or slowing down?
- Are all sequence elements displayed and tracked correctly?

### Game Restart

- Does restarting the game reset all scores, levels, and sequences correctly?

### Input Boundaries

- What happens if the player clicks a card outside the play area or double-clicks a card too quickly?

## B) Boundary Test Scenarios and Expected Outcomes

### Maximum Score

### Test Case: Reach the game’s maximum possible score (e.g., 9999 points)

- Input: Play until the score reaches 9999.
- Expected Outcome:
- Score remains stable at 9999.
- No overflow errors or crashes.

### Minimum Score

#### Test Case: Test if the score can drop below 0

- Input: Trigger penalties until the score reaches 0 or lower.
- Expected Outcome:
- Score stops at 0 (if negatives aren’t allowed).
- No graphical or functional errors.

### Maximum Level

#### Test Case: Progress beyond the maximum defined level

Input: Complete sequences until the level exceeds the upper limit (e.g., Level 20).

- Expected Outcome:
- Game either caps the level at the maximum (e.g., Level 20) or continues scaling properly.
- No crashes or unplayable difficulty spikes.

### Maximum Sequence Length

#### Test Case: Reach a sequence length that tests the display or memory capacity

- Input: Progress until the sequence reaches 20+ elements.
- Expected Outcome:
- All elements display correctly and are trackable.
- No lag, crashes, or incorrect matches.

### Game Restart

#### Test Case: Restart the game after achieving a high level and score

- Input: Click "Restart Game" after completing Level 10.
- Expected Outcome:
- Score resets to 0, level resets to 1, and sequence clears.
- No lingering elements from the previous game session.

### Input Boundaries

#### Test Case: Click outside the valid play area or double-click quickly

- Input: Click a non-ornament area or click the same card twice in quick succession.
- Expected Outcome:
- No action occurs for invalid clicks.
- Double-clicking does not break game logic or sequences.

# Part 4: Integration Testing for the Memory Game

## A) Identifying Game Interactions

### Gameplay and Scoring

- Interaction: When a player completes a sequence correctly, the score is updated.
- Considerations: Does the scoring update accurately without affecting ongoing gameplay?

### Gameplay and Levels

- Interaction: When a player completes a sequence, the game should increase difficulty (longer sequences).
- Considerations: Does the transition to the next level maintain proper game flow?

### Menus and Gameplay

- Interaction: Starting or restarting the game from the menu should reset all game elements (e.g., score, levels, sequence).
- Considerations: Does navigating the menu interrupt active gameplay correctly?

### Sound Effects and Game Actions

- Interaction: When a player clicks an ornament, a sound should play.
- Considerations: Are sounds triggered without delay or overlap, and are they tied to the correct actions?

## B) Writing Integration Tests

### Gameplay and Scoring

- Test Case: Ensure score updates correctly after a sequence is completed.
- Input: Correctly match a sequence of 5 ornaments.
  - Expected Outcome:
    - The score increases by the appropriate value.
    - Gameplay continues smoothly without interruption.

### Gameplay and Levels

- Test Case: Verify level progression after a sequence is completed.
- Input: Complete a sequence successfully.
  - Expected Outcome:
    - A new, longer sequence is generated.
    - Difficulty adjusts without resetting prior progress (e.g., score).

### Menus and Gameplay

- Test Case: Restart the game from the main menu.
- Input: Start a game, then press "Restart" in the menu.
  - Expected Outcome:
    - Score resets to 0.
    - The first sequence is reloaded.
    - Ongoing game data (e.g., active sequence) is cleared.

### Sound Effects and Game Actions

- Test Case: Ensure sound effects play when ornaments are clicked.
- Input: Click each ornament in the sequence.
  - Expected Outcome:
    - The correct sound plays for each ornament.
    - No overlapping or delayed sounds occur.

### Gameplay and UI Boundaries

- Test Case: Ensure the gameplay state does not interfere with menu interactions.
- Input: Pause the game and access the menu during an active sequence.
  - Expected Outcome:
    - Gameplay pauses and resumes correctly.
    - Menu actions do not cause gameplay errors.

# Part 5: Handling Bad Input and Run-Time Errors for the Memory Game

## A) Identifying Scenarios to Handle

### Invalid User Input

Example:

- The player clicks outside the game area.
- The player clicks an ornament out of sequence.

Handling:

- Ignore invalid inputs and keep the game running smoothly.
- Provide visual/audio feedback for out-of-sequence clicks, such as a sound or flashing the screen.

### Unexpected Game States

Example:

- The sequence array becomes empty or corrupted during gameplay.
- The game gets stuck waiting for input after a logic error.

Handling:

- Reset the game to the last valid state or display an error message prompting the player to restart.

### Error Handling

Example:

- Save data becomes corrupted.
- The app runs out of memory or crashes mid-game.

Handling:

- Display a message to the user: "An error occurred. Restarting the game."
- Safely reset the game and clear corrupted data without closing the app.

## B) Writing Tests for Bad Input and Errors

### Test Case: Invalid Clicks

Condition:

- Simulate clicks outside the game area or on the wrong ornaments.

Expected Outcome:

- Invalid clicks are ignored.
- The correct sequence remains intact.
- An error sound or visual cue provides feedback.

### Test Case: Empty Sequence Array

Condition:

- Force the game to have an empty sequence.

Expected Outcome:

- The game resets to a default sequence.
- A message informs the player: "Error detected: Restarting the game."

### Test Case: Corrupted Save File

Condition:

- Simulate a corrupted save file when loading.

Expected Outcome:

- The game skips the load process.
- A message prompts the user to start a new game: "Save data corrupted. Starting fresh."

### Test Case: Simultaneous Clicks

Condition:

- Simulate two ornaments being clicked at the same time.

Expected Outcome:

- Only the first click is registered.
- The game continues without breaking the sequence logic.
