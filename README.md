Game Development Instructions: Blackjack-Style Card Game

I want to build a card game based on the classic rules of Blackjack, with the option to introduce original mechanics, special abilities, and a roguelike progression system.

1. Core Game Logic (Classic Rules)
Objective

The goal is to beat the dealer. To do this, the player must:

Get exactly 21 points.
Have a higher score than the dealer without exceeding 21.
Win if the dealer exceeds 21 points and busts.
Card Values
Number cards (2–10): Worth their face value.
Face cards (Jack, Queen, King / J, Q, K): Worth 10 points each.
Ace (A): Worth either 1 or 11 points, depending on what is most beneficial for the hand. If counting the Ace as 11 would cause the hand to exceed 21, it automatically counts as 1.
2. Round Flow
Initial Bets

At the beginning of each round, the player places a bet using chips or points.

Initial Deal
The player receives two face-up cards.
The dealer receives two cards: one face-up and one face-down.
Player's Turn

The player analyzes their current score and the dealer's visible card, then chooses one of the following actions:

Hit: Draw another card. The player can continue drawing cards until they choose to stand or exceed 21. If their score goes over 21, they immediately lose the round.
Stand: Keep the current score and end the player's turn.
Double Down (Optional): Double the initial bet, draw exactly one additional card, and automatically end the player's turn.
Dealer's Turn

Once the player finishes their turn, the dealer reveals the hidden card and follows a fixed set of rules.

The dealer cannot make independent decisions. Their actions are determined automatically:

If the dealer's total is 16 or less, they must draw another card.
If the dealer's total is 17 or higher, they must stand.
Determining the Winner

After the dealer finishes their turn, compare both scores:

If the player busts, the player loses immediately.
If the dealer busts, the player wins.
If neither busts, the player with the score closest to 21 wins.
If both have the same score, the round ends in a push, and the player's original bet is returned.
3. Basic Game Architecture

I want the game logic to follow this sequence:

Create a standard 52-card deck.
Shuffle the deck.
Deal two cards to the player and two cards to the dealer.
Start the player's turn.
Allow the player to choose between hitting, standing, or doubling down if that option is available.
After every hit, recalculate the player's score.
If the player exceeds 21, end the round immediately and register a loss.
If the player stands, begin the dealer's turn.
Reveal the dealer's hidden card.
Make the dealer draw cards automatically while their total is below 17.
Stop the dealer's turn when they reach 17 or higher, or bust.
Compare the final scores.
Determine the winner, resolve the bet, and display the round's result.
Allow the player to start another round.
Important: Ace Calculation

The Ace needs special handling to ensure that the score is always calculated correctly.

The scoring system should work as follows:

Initially count each Ace as 11 points.
Add up the values of all the cards in the hand.
If the total exceeds 21 and the hand contains an Ace currently counted as 11, subtract 10 points from the total, effectively changing that Ace's value from 11 to 1.
Repeat this adjustment for additional Aces if the total still exceeds 21.
The final score should use the highest possible value that does not exceed 21 whenever possible.

This calculation must work for both the player and the dealer.

4. Original Mechanics and Game Customization

I also want the game to support optional mechanics that make it different from traditional Blackjack.

Special Card Abilities

Certain cards could have unique effects when drawn.

Examples:

Jack: Allows the player to discard the most recently drawn card.
King: Forces the dealer to draw one additional card, even if their total is already 17 or higher.

These abilities should be designed as modular mechanics so that more special cards can be added later without rewriting the entire game system.

Dynamic Target Score

Instead of always using 21 as the target, I want to explore a system where the target score changes between rounds.

For example, a roulette wheel or random event could determine whether the target for the next round is 19, 21, 23, or 25.

The scoring rules and bust conditions should adapt to the selected target.

Campaign and Roguelike Mode

I want to explore a campaign mode inspired by games like Balatro and Inscryption.

In this mode, the player progresses through a series of increasingly difficult opponents, each with unique rules and mechanics.

Examples of special dealer encounters:

A dealer who starts each round with two hidden cards.
A dealer who always starts with a total of 10 points.
A dealer who can ignore certain standard rules.
Boss encounters that introduce unique restrictions or special abilities.

Each opponent should feel different and force the player to adapt their strategy.

Consumable Items

The game should also include consumable items that temporarily alter the rules or influence a hand.

Examples:

Stabilizing Potion: Subtracts 2 points from the player's current hand total to prevent a bust.
Special Chips: Allow the player to modify a card's value or influence the dealer's next action.
Emergency Item: Provides a limited-use ability to recover from a dangerous situation.

These items could be collected throughout the campaign and used strategically.

5. Overall Development Goal

I want to build the game with a modular structure, keeping the core Blackjack rules separate from the special abilities, items, dealer behaviors, and campaign systems.

The initial version should focus on making the classic Blackjack gameplay fully functional, including card dealing, score calculation, player actions, dealer AI, betting, and round resolution.

Once the core system works reliably, I want to expand it with original mechanics, special encounters, consumable items, and roguelike progression.

The goal is to create a game that is easy to understand at first but becomes increasingly strategic and unpredictable as the player progresses.
