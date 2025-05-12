import random
import time

class Player:
    def __init__(self, name):
        self.name = name
        self.position = 0

    def move(self, steps):
        self.position += steps
        if self.position > 50:
            self.position = 50

    def has_won(self):
        return self.position == 50

def roll_dice():
    return random.randint(1, 6)

def play_turn(player):
    input(f"\n{player.name}, press Enter to roll the dice...")
    dice = roll_dice()
    print(f"{player.name} rolled a 🎲 {dice}")
    player.move(dice)
    print(f"{player.name} is now at position {player.position}")

def play_game():
    print("🎯 Welcome to Console Ludo Game!")
    print("First to reach exactly 50 wins!\n")

    player1 = Player("Player 1")
    player2 = Player("Player 2")

    while True:
        play_turn(player1)
        if player1.has_won():
            print(f"\n🏆 {player1.name} WINS THE GAME!")
            break

        play_turn(player2)
        if player2.has_won():
            print(f"\n🏆 {player2.name} WINS THE GAME!")
            break

        time.sleep(1)

if __name__ == "__main__":
    play_game()
