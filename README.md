# Rock-Paper-Scissors
import random

# Dictionary to keep track of opponent's moves
opponent_history = []

def player(prev_play, opponent_history=[]):
    # Update opponent history
    opponent_history.append(prev_play)
    
    if len(opponent_history) == 0:
        # First move, pick randomly
        return random.choice(['R', 'P', 'S'])
    
    # Simple strategy: play the move that would beat the opponent's last move
    last_opponent_move = opponent_history[-1]
    
    # Determine the counter-move
    if last_opponent_move == 'R':
        return 'P'  # Paper beats Rock
    elif last_opponent_move == 'P':
        return 'S'  # Scissors beats Paper
    elif last_opponent_move == 'S':
        return 'R'  # Rock beats Scissors

# Example to test against a single opponent
if __name__ == "__main__":
    from RPS_game import play, quincy  # Assuming 'quincy' is one of the bots
    play(player, quincy, 1000, verbose=True)
