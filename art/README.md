# Character art

One folder per character: `swordsman`, `archer`, `mage`, `paladin`, `demon`, `vampire`, `cavalryman`, `gunner`.

Name each frame `<action>-<number>.png`, numbered from 1 with no gaps:

| Action | Files |
|---|---|
| Standing | `standing-1.png`, `standing-2.png`, ... |
| Attacking | `attacking-1.png`, ... |
| Blocking | `blocking-1.png`, ... |
| Hurt | `hurt-1.png`, ... |

- Canvas 120 x 144 pixels, transparent, the character facing **right**, feet on row 140 (see `design/pixel-fable/art-brief.md`).
- The game plays whatever frames are in the folder, in number order. Adding or replacing frames needs no code change and no build: just reload the game.
- One frame for an action: the game moves it in code (a bob while standing, a lunge to attack, a step back to block, a jolt back when hurt).
- No frame for an action: the standing frames are used. No standing frame: a labelled placeholder is drawn.

## Frame-by-frame moves (the Swordsman so far)

A character can also have moves drawn frame by frame, each in its own folder: `art/<character>/<move>/NN.png` (two-digit
numbers, starting at 00 or 01 as the art session made them). The Swordsman has `basic`, `heavy`, `block`, `hurt`,
`pin-down-cast`, `pin-down-swords` (the cage drawn over the opponent), `charged-attack`, `charged-attack-pillar` (the pillar
alone, so the game can slide it to the opponent) and `killing-blow-head`, `-throat`, `-heart`.

These pictures can be wider than 120 pixels; they still face right with the feet on row 140. Each move's frame count, width,
where the standing sprite sits inside it (sprite_x), speed and hit frame are listed once in `game-src/game/02-move-art.js` (`MOVE_ART`),
copied from the art session's `manifest.json`. A new character's moves need only a new entry there, plus a rebuild.
The originals and their previews are in `design/pixel-fable/sprites/<character>-moves/`.
