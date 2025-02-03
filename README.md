# code_alpha_hangmangame
A text based Hangman Game
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
  
