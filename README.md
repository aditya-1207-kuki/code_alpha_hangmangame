import random

# List of words to choose from
words = ["python", "hangman", "programming", "computer", "developer", "code", "algorithm"]

# Function to display the current state of the word
def display_word(word, guessed_letters):
    displayed = ''.join([letter if letter in guessed_letters else '_' for letter in word])
    return displayed

# Function to play the game
def play_hangman():
    word = random.choice(words)  # Randomly select a word
    guessed_letters = []  # List to store guessed letters
    incorrect_guesses = 0  # Counter for incorrect guesses
    max_incorrect_guesses = 6  # Limit on the number of incorrect guesses

    print("Welcome to Hangman!")
    print("Try to guess the word. You have a limited number of incorrect guesses.")
    
    while incorrect_guesses < max_incorrect_guesses:
        print(f"\nCurrent word: {display_word(word, guessed_letters)}")
        print(f"Incorrect guesses left: {max_incorrect_guesses - incorrect_guesses}")
        
        guess = input("Guess a letter: ").lower()

        # Validate the input
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a valid single letter.")
            continue

        # If the letter has already been guessed
        if guess in guessed_letters:
            print("You've already guessed that letter.")
            continue

        # Add the guessed letter to the list
        guessed_letters.append(guess)

        # Check if the guess is in the word
        if guess in word:
            print(f"Good guess! The letter {guess} is in the word.")
        else:
            incorrect_guesses += 1
            print(f"Incorrect guess. The letter {guess} is not in the word.")

        # Check if the player has won
        if all(letter in guessed_letters for letter in word):
            print(f"\nCongratulations! You've guessed the word: {word}")
            break

    # If the player has run out of guesses
    if incorrect_guesses == max_incorrect_guesses:
        print(f"\nSorry, you've run out of guesses. The word was: {word}")

# Start the game
play_hangman()
