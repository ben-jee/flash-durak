# Transfer Durak — Rules Specification

**Version:** 0.1 (draft)
**Last updated:** 2026-04-23
**Status:** Source of truth. If the code disagrees with this document, either the code is wrong or this document needs updating. Never let them drift.

---

## 1. Overview

Transfer Durak is a trick-taking card game descended from Russian Durak. Players shed cards by attacking opponents; the last player holding cards is the *durak* ("fool") and loses. This document specifies a custom variant with two distinctive rules:

1. **Ordered pickup** — when the talon is drawn from to refill hands, a strict order is followed.
2. **Flash mechanic** — a defender can reveal (rather than play) a trump of the same rank as the attacking card to transfer the attack while keeping the trump in hand. Each physical card can be flashed at most once per game per owner.

---

## 2. Setup

### 2.1 Deck

- Standard 52-card deck.
- Ranks: 2, 3, 4, 5, 6, 7, 8, 9, 10, J, Q, K, A (2 is lowest, A is highest).
- Suits: ♣ Clubs, ♦ Diamonds, ♥ Hearts, ♠ Spades.
- No jokers.

### 2.2 Players

- 2 to 6 players.
- Each player starts with an empty hand.

### 2.3 Dealing

1. Shuffle the deck.
2. Deal 6 cards to each player, one at a time, in seating order.
3. After dealing, flip the top card of the remaining deck face up — its suit is the **trump suit** for the game.
4. Place the flipped trump card at the bottom of the talon, perpendicular and partly visible (so all players can see the trump suit throughout the game). It will be the last card drawn from the talon.

### 2.4 Trump suit

- Any card of the trump suit beats any card of a non-trump suit, regardless of rank.
- Among trumps, higher rank beats lower rank.
- Among non-trumps of the same suit, higher rank beats lower rank.
- A non-trump card cannot beat a card of a different non-trump suit.

### 2.5 Starting player

- The player holding the **lowest trump card** in their hand attacks first.
- If no player holds a trump (only possible with small player counts and bad luck), the player holding the lowest-ranked card overall starts. *(Edge case — very rare but must be handled.)*
- This first attacker chooses the **direction of play** (clockwise or counter-clockwise). This direction is fixed for the entire game.

---

## 3. Turn structure

### 3.1 Roles in a round

- **Attacker** — the player whose turn it is to initiate the attack.
- **Defender** — the player being attacked. Always the next player in the direction of play, relative to the attacker, *unless* an attack has been transferred (see §5) — in which case the defender is whoever the attack is currently pointed at.
- **Throw-in players** — all other players. They may join the attack with matching-rank cards during the round.

### 3.2 Round flow

1. **Opening attack.** The attacker plays one card face up in front of the defender.
2. **Defender responds.** The defender chooses one of:
   - a) **Beat** the attacking card (see §4).
   - b) **Transfer** the attack by playing a card of the same rank (see §5.1).
   - c) **Flash** the attack by revealing a trump of the same rank (see §5.2).
   - d) **Pick up** — accept the attack, take the card into hand. The round continues (see §3.3).
3. **Further attacks.** After the first attack is resolved, the attacker and any throw-in players may add more attack cards, but only of ranks already present on the table (either as attack cards or defence cards). The defender must respond to each.
4. **Round ends.** When either:
   - The defender has successfully beaten every attack card on the table (successful defence), OR
   - The defender gives up and picks up all cards on the table (failed defence), OR
   - The maximum number of cards is reached (see §3.4).

### 3.3 Defender picks up

The defender can choose to pick up at any point. When they do:
- All cards on the table (attacks and any defences played so far) go into the defender's hand.
- Other players may still "pile on" — they may add more attack cards (of ranks already on the table) up to the defender's hand-size limit (see §3.4). The defender picks up these too.
- Once the defender has chosen to pick up, they no longer beat, transfer, or flash — they only receive cards.

### 3.4 Maximum table size

- The maximum number of attack cards in a round is equal to the **defender's hand size at the moment the round began**.
- Once that many attacks have been played, no more attacks can be added, even if the defender has beaten all of them.
- Example: defender started the round with 4 cards, so at most 4 attack cards can be played against them in this round.

---

## 4. Beating an attack card

The defender may beat an attack card by playing a card that satisfies one of:
- **Same suit, higher rank.** A 10♥ is beaten by any ♥ of J or higher.
- **Any trump, if the attack card is non-trump.** A 10♥ (non-trump; assume trump is ♠) is beaten by any ♠.
- **Trump, higher rank, if the attack card is trump.** A 10♠ (if ♠ is trump) is beaten only by J♠, Q♠, K♠, or A♠.

A defence card, once played, stays in front of the attack card it beats. It cannot be used to beat another attack card.

---

## 5. Transfer and flash

Both transfer and flash redirect the attack to the next player in the direction of play. The redirected-to player becomes the new defender and the round continues.

### 5.1 Transfer

- **Condition:** The defender plays a card from their hand of the **same rank** as the attack card (or, if there are multiple attack cards, the same rank as all of them — see §5.3).
- **Effect:** The transferred card is placed on the table as a new attack card. The attack, plus the new card, is redirected to the next player in direction of play. That player becomes the new defender.
- **Any suit** may be used to transfer (including trump).
- The transferred card is now on the table like any other attack card.

### 5.2 Flash

- **Condition:** The defender reveals (does not play) a card from their hand that is:
  - The **same rank** as the attack card, AND
  - Of the **trump suit**, AND
  - Has **not been flashed by this defender before in this game**.
- **Effect:** The attack is redirected to the next player in direction of play, exactly as with a transfer. The flashed card **stays in the defender's hand** — it is not placed on the table.
- The flashed card is now marked as "used" for flashing *for this player*. If the card later moves to another player's hand (e.g., they pick it up), the new owner has a fresh unused flash on it. If the card is played and ends up in the discard pile (*bita*), the mark is moot — it can never be flashed again because it can never return to a hand.
- To transfer again with a card that has been flashed by you, you must actually play the card (treat it as a normal transfer per §5.1).

### 5.3 Transfer/flash when multiple attack cards are on the table

- If there are multiple unanswered attack cards on the table, **all of them must be the same rank** for a transfer or flash to be legal, and the transferring/flashing card must match that rank.
- If defence cards have already been played against some attacks in the round, transfer and flash are no longer legal — once the defender has started beating cards, they are committed to defending.

### 5.4 Chaining

- The new defender (after a transfer or flash) has all the same options: beat, transfer, flash, or pick up.
- Chains may continue indefinitely, going around the table in the direction of play, until someone either beats, picks up, or cannot/will not pass further.
- A player who has already been part of the transfer chain *can* be transferred to again if the chain completes a loop (in small player counts).

### 5.5 Throw-ins during a transfer chain

- While an attack is being transferred/flashed through the chain, no throw-ins are allowed. Throw-ins begin only once the chain has stopped (someone begins beating, or picks up).

---

## 6. Throw-ins

- Once the first attack has been beaten, transferred back to being defended, or once the defender has chosen to pick up, any other player (not the defender) may throw in additional attack cards.
- **Rank constraint:** a thrown-in card's rank must match the rank of some card already on the table (attack or defence).
- **Size constraint:** the total number of attack cards in the round may not exceed the defender's hand size at the start of the round (§3.4).
- **Order:** throw-ins are processed in the order they are submitted. The server (authoritative game engine) is the arbiter of order.

---

## 7. Refilling hands

At the end of every round, before the next round begins, players refill their hands from the talon up to 6 cards each. If the talon is empty or runs out partway through refilling, players simply don't refill further.

### 7.1 Pickup order

Cards are drawn from the talon in the following order:

1. **The original attacker** of the round that just ended draws first (back up to 6).
2. **Throw-in players**, in the order they joined the attack (i.e., the order their first throw-in card was played).
3. **The defender draws last.**

This applies regardless of whether the defence was successful or failed. The defender always draws last.

### 7.2 Refill rules

- Each player draws one at a time until they reach 6 cards (or until the talon is empty).
- If multiple players are refilling and the talon runs out, the order of §7.1 determines who gets the remaining cards.
- The face-up trump card at the bottom of the talon is drawn last of all (it is the final card in the talon).

### 7.3 Players who didn't participate

- Players who were neither the attacker, a throw-in, nor the defender in the round do not refill at all for that round if they already have 6+ cards. If they have fewer than 6 cards (from previous rounds where they received cards), they refill after the throw-ins but before the defender.

*Note: This is a rule we should review — the above assumes non-participants also refill. Let me know if non-participants never refill at all.*

---

## 8. Who attacks next round

After a round ends, the next round's attacker is determined by the following rules, checked in order:

### 8.1 Rule 1: Successful defence

If the defender beat all attack cards (cards go to the discard pile, "bita"), **the defender becomes the next attacker**.

This applies even if the round involved transfers or flashes earlier, as long as the *final* defender in the chain successfully defended.

### 8.2 Rule 2: Failed defence after transfer or flash

If the defender (the final one in the chain) picked up, AND a transfer or flash occurred at any point during the round, **the player who first transferred or flashed becomes the next attacker**.

By definition, this is always the **original defender** of the round (the first player who was attacked), because only the first defender can initiate a transfer — subsequent defenders are responding to an already-transferred attack.

### 8.3 Rule 3: Failed defence, no transfer or flash

If the defender picked up, and no transfer or flash occurred during the round, **the next player in the direction of play (from the defender who picked up) becomes the next attacker**.

### 8.4 Note on successful defence after transfer

If transfers/flashes occurred in the chain but the final defender successfully defended, rule 8.1 applies — that final defender attacks next.

---

## 9. Winning and losing

- The game continues until the talon is empty AND all but one player have emptied their hands.
- A player who empties their hand while the talon is empty is **out** of the game — they play no further rounds.
- The last player holding cards is the **durak** (loser).
- If two players are left and both empty their hands in the same round (extremely rare), the game is a draw.

### 9.1 Play with fewer than 2 active players

- When only one player has cards left, the game ends immediately and they are the durak.
- A player who is out cannot attack, defend, or throw in.

---

## 10. Glossary

- **Attacker** — the player initiating an attack this round.
- **Bita** — the discard pile. Cards sent here are out of play for the rest of the game.
- **Defender** — the player currently being attacked.
- **Durak** — "fool"; the losing player.
- **Flash** — reveal a same-rank trump from hand to transfer the attack without playing the card. Once per card per owner per game.
- **Talon** — the draw pile (what remains of the deck after dealing).
- **Throw-in** — a non-defender adding an attack card of a rank already on the table.
- **Transfer** — play a same-rank card from hand to redirect the attack to the next player.
- **Trump** — the suit determined at setup; beats all non-trump suits.

---

## 11. Open questions / decisions still to make

1. **Non-participant refills** (§7.3) — confirm whether players who weren't attacker/thrower/defender still refill if under 6 cards, or are simply stuck with what they have until they participate in a round.
2. **Edge case: no trumps dealt** (§2.5) — confirm the fallback of "lowest card overall starts" when nobody has a trump.
3. **Draws** (§9) — confirm whether a tied final round is possible and how it should resolve.
4. **Cheating** (future) — rules for illegal play, call-out mechanic, penalties. Deferred to v2.

---

## 12. Revision log

- **0.1** (2026-04-23) — initial draft, based on conversation with Ben.
