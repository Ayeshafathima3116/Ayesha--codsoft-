import tkinter as tk
from tkinter import font
import random

# Define the options for the game
options = [('rock', 0), ('paper', 1), ('scissors', 2)]

# Initialize the scores
player_score = 0
computer_score = 0

def get_computer_choice():
    """Function to get the computer's choice"""
    return random.choice(options)

def player_choice(player_input):
    """Function to handle the player's choice and update the game state"""
    global player_score, computer_score

    computer_input = get_computer_choice()

    player_choice_label.config(text='You Selected : ' + player_input[0])
    computer_choice_label.config(text='Computer Selected : ' + computer_input[0])

    if player_input == computer_input:
        winner_label.config(text="Tie")
    elif (player_input[1] - computer_input[1]) % 3 == 1:
        player_score += 1
        winner_label.config(text="You Won!!!")
        player_score_label.config(text='Your Score : ' + str(player_score))
    else:
        computer_score += 1
        winner_label.config(text="Computer Won!!!")
        computer_score_label.config(text='Computer Score : ' + str(computer_score))

# Create the main application window
root = tk.Tk()
root.title("Rock Paper Scissors Game")
root.config(bg='#FFE873')
root.geometry('700x300')

app_font = font.Font(size=12)

# Title label
tk.Label(root, text='Rock Paper Scissors Game', font=font.Font(size=20), bg='#FFE873').pack()

# Winner label
winner_label = tk.Label(root, text="Let's start the Game...", fg='green', bg='#FFE873', font=font.Font(size=13), pady=8)
winner_label.pack()

# Frame for input buttons and score
input_frame = tk.Frame(root, bg='#FFE873')
input_frame.pack()

# Player options label
player_options = tk.Label(input_frame, text="Your Options : ", font=app_font, fg='grey', bg='#FFE873')
player_options.grid(row=0, column=0, pady=8)

# Buttons for player choices
rock_btn = tk.Button(input_frame, text='Rock', width=15, bd=0, bg='pink', pady=5, command=lambda: player_choice(options[0]))
rock_btn.grid(row=1, column=1, padx=8, pady=5)

paper_btn = tk.Button(input_frame, text='Paper', width=15, bd=0, bg='silver', pady=5, command=lambda: player_choice(options[1]))
paper_btn.grid(row=1, column=2, padx=8, pady=5)

scissors_btn = tk.Button(input_frame, text='Scissors', width=15, bd=0, bg='light blue', pady=5, command=lambda: player_choice(options[2]))
scissors_btn.grid(row=1, column=3, padx=8, pady=5)

# Score label
score_label = tk.Label(input_frame, text='Score : ', font=app_font, fg='grey', bg='#FFE873')
score_label.grid(row=2, column=0)

# Labels for player and computer choices and scores
player_choice_label = tk.Label(input_frame, text='You Selected : ---', font=app_font, bg='#FFE873')
player_choice_label.grid(row=3, column=1, pady=5)

player_score_label = tk.Label(input_frame, text='Your Score : 0', font=app_font, bg='#FFE873')
player_score_label.grid(row=3, column=2, pady=5)

computer_choice_label = tk.Label(input_frame, text='Computer Selected : ---', font=app_font, fg='black', bg='#FFE873')
computer_choice_label.grid(row=4, column=1, pady=5)

computer_score_label = tk.Label(input_frame, text='Computer Score : 0', font=app_font, fg='black', bg='#FFE873')
computer_score_label.grid(row=4, column=2, padx=(10, 0), pady=5)

# Run the main event loop
root.mainloop()

