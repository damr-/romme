# Rummy
A Unity application which plays the famous game 'Rummy' against itself.

[Run in Browser (WebGL)](https://damr-.github.io/rummy/Builds/rummy/)

[Download (Windows)](https://github.com/damr-/rummy/raw/master/Builds/Rummy_Windows.zip) (outdated)

[Download (Mac OS)](https://github.com/damr-/rummy/raw/master/Builds/rummy-MacOS.zip)

## Rules
- 2 players (AI), each starts with 13 cards in their hand.
- At the beginning of their turn, the player draws a card. To end their turn, the player discards one card.
- The goal is to get rid of all the cards in one's hand. This means the all the cards in the player's hand are laid down, except one, which is then discarded to finish the game.
- After round 2, if a player can form card packs with a combined value greater than a minimum required value (usually 30 or 40), these packs are laid down. Card packs are sets and runs.
  - Sets are formed by 3 or 4 cards of the same rank but different suits. In a set of 3 cards, one can be replaced by a joker of the same color. Adding a joker with the correct color to a set of 3 cards is allowed.
  - Runs consist of at least 3 cards of the same suit which form an ascending sequence. A run can start with Ace-2-3 and end with Q-K-Ace but must not form loops (K-Ace-2 segments are forbidden). When creating a run of 3 cards, only one card can be replaced by a joker of the same color (adding more joker cards later is allowed though).
- A player who has laid down card packs possesses the ability to
  - pick up the top card of the discard stack instead of drawing one from the card stack at the start of their turn,
  - lay down sets/runs of any value during their turn,
  - add single cards to already laid down card packs during their turn. A card can also be added to a card pack where the joker originally replaced the card in question. In that case, the card replaces the joker and the latter is picked up by the player who replaced it.

## Remarks
- The players always try to lay down the highest valued card combination. They will never purposefully keep a finished card pack on their hands. Same goes for single cards.
- Once a player has laid down card packs and surpassed the minimum required value, they always try to get rid of the highest valued card to minimize losses if they lose the game.
- Players do not count/memorize the cards which had been discarded to figure out possible card combinations.
- Players *do* check for sets/runs in their hand cards which only consist of two cards ("duos") and try to keep them on hand for as long as possible. Since every card exists twice in the game, if the duo's missing card has already been laid down twice, the duo will *not* be kept.
- Starting with 13 cards, it is possible that the game ends in a draw. This happens when both players laid down 3 complete sets of 4 cards each. With one card remaining in their hand, neither player can win. In that case, the game is forcefully ended as a draw.
