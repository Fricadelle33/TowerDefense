# Deck of Secrets — The Fairy Well

## Description

The Fairy Well is a deck of secrets, powerful cards, unlockable as contract or elite rewards.
We strongly advise players to not look at or draw from the deck of secrets unless invited to.

## Number cards

Cards in the Well are numbered. The deck should not be shuffled at any point in time.
Whenever a player gains a Fairy Well card, he places the card face down, without looking at it next to the wave deck.
If they successfully complete the wave, players collectively read the card and apply the effect.

~~~yaml
Cards types: # Keep the secret in the rules — Write the directive on the card directly
  action: One player can add it to their deck.
  tower: >
    If a lower version of the tower exists on the board, upgrade it immediately and place it in that players' deck at the end of the wave. 
    Otherwise, add it to a player deck. 
  totem: Players can choose to use it or place it in the totem discard pile.
  elite: Players must place it at the bottom of the next wave deck. 
~~~

All fairy well cards will be identified with fairy_well:N in their respective files,
where N is the card order in the fairy well deck. Other cards won't have the fairy_well modifier.
