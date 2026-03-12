2. Enter the current game state in the top frame:
- **Grill**: space‑separated numbers (21–36) that are face‑up. By default all are pre‑filled.
- **Opponents’ top helpings**: up to four opponents, leave blank if none.
- **Your top helping**: if you already have a tile on your stack (optional).
3. In the **Dice** area, use the buttons to add dice to your current roll (one die per click). The dice appear in the lower canvas.
- Click on any die in the lower canvas to cycle its face (1 → 2 → 3 → 4 → 5 → worm → 1…).
- The “Take all dice of symbol” buttons are enabled only for symbols that are both present in the roll **and** not already fixed.
- Click a symbol button to move all dice of that symbol to the fixed (taken) area.
- Use **Clear roll** to remove all dice from the current roll (e.g., after a mistake).
4. At any point, click:
- **Should I stop now?** – get advice based on your fixed dice.
- **Suggest symbol to take** – get the optimal symbol to take from the current roll (requires dice in the remaining area).
5. When you decide to end your turn, click **Stop turn** – the program calculates the worm outcome (gain, loss, or no change).
6. Click **Reset turn** to start a new turn while keeping the game state (grill, opponents) unchanged.

## How It Works

The decision engine uses dynamic programming over all possible dice collections (0–8 dice, 6 symbols). For each collection it computes the expected worm gain from that point onward, given:
- The visible face‑up helpings on the grill.
- The top helpings of opponents (which can be stolen).
- Your own top helping (which you lose on a failed turn).

The expected value considers all possible future rolls and the optimal choice of symbol. The result is a policy that tells you whether stopping now is better than continuing, and which symbol to take after a roll.

## Project Structure

- `game_models.py` – data structures: `Helping`, `Player`, `GameState`.
- `dice_utils.py` – precomputation of all dice roll outcomes and all possible collections.
- `decision_engine.py` – reward functions, dynamic programming, `TurnPolicy` class.
- `gui.py` – the Tkinter GUI described above.
- `main.py` – entry point.

## License

This project is open source and available under the MIT License.
