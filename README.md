# Dust & Lead

**Play it in your browser: https://inkstaid.github.io/dust-and-lead/**

A 2D Wild West platformer prototype. In Dry Creek, 1899, the Crowe Boys took your horse and you go get her back.

## Play
Open `index.html` in Chrome or Safari. No install needed. (Firefox works with a keyboard, but its PS5 controller support on macOS is unreliable.)

The title screen is a painted scene: Dry Creek station at sundown with the logo. The cowboy on it twirls his revolver, reloads his shotgun and cleans his knife in turn. Press Space (Cross on a PS5 controller) to start. **H** (Triangle) there opens the character sheet.

Shots fly dead straight the way you're facing, Contra style.

**Pause** (P, Esc or Options) shows the controls and a few tips.

### Scoreboard
Finished runs go on one board shared by everyone who plays, ranked by time. Pauses don't count, and fewer deaths break a tie.
- **Riding out:** when you win, the game asks for your name, up to 12 letters or numbers:
  - **Keyboard:** type it, **Enter** saves, **Esc** skips.
  - **Controller:** the **D-pad** picks letters, **Cross** saves, **Circle** deletes.
  - It then shows the top ten with your run lit in gold, and your place if you didn't make the ten.
- **Viewing the board:** **L** (Square) on the title screen.
- **Offline:** you can still play and finish, but your time isn't saved.
- **Where scores live:** a Supabase table that anyone can read and add to, but no one can edit or delete. Runs under 45 seconds are refused.

### Controls
Two keyboard layouts work at the same time, one for each hand. The controller is unchanged.

| Action | Left hand | Right hand | PS5 controller |
|---|---|---|---|
| Move | W A S D | ↑ ← ↓ → | Left stick or D-pad |
| Jump | Space | Right Shift | Cross |
| Duck | S | ↓ | Left stick down or D-pad down |
| Drop through a plank or awning | S + Space | ↓ + Right Shift | Down + Cross |
| Interact (open a chest) | E | Enter | Triangle |
| Revolver | 1 | J | R2 or Circle |
| Shotgun | 2 | K | Square |
| Knife (stab) | 3 | L | Triangle |
| Reload (revolver and shotgun) | R | ; | L1 |
| Pause | Esc or P | Esc or P | Options |
| Music on/off | M | M | Create |

W and ↑ climb ladders; they don't jump. A left click also fires the revolver.

- **Idle routines:** stand still for a few seconds and Jack puts on the same show as the cowboy on the title screen, one after another: he draws the revolver, twirls it and spins it home; pulls the shotgun off his back, breaks it, loads two shells from his belt and slings it again; draws the knife, wipes the blade with a rag, turns it to the light, flips it and sheathes it. Any input ends it at once.
- **Reloading:** Jack loads the way the Crowe Boys do: a filling ring of six rounds (or two shells for the shotgun) and "RELOADING" over his head. He holds the revolver low and watches it, and keeps his feet.
- **Ducking** is about timing. Duck when an outlaw's gun flashes and his shot sails over you. Stay down, though, and he adjusts his aim low after a moment (quickest for Silas). Riflemen above you always aim at your body.

### The Crowe Boys fight back
- **Limited rounds:** outlaws carry 3 shots, riflemen 2 and Silas 6. When they're empty they back away to reload, with a filling ring and "RELOADING" over their heads. That's your window. Cornered with nowhere to run, they crouch where they are.
- **They duck too:** an outlaw who sees your shot coming can drop under it. Crouched, they're below a standing shot, so duck and fire low to hit them. Point-blank shots are too quick to dodge.
- **No hiding:** get out of sight behind crates or cover and they come after you, hopping up onto obstacles and dropping off ledges. Riflemen hold their perch.
- **Melee:** get right up close and they'll pistol-whip you after a quick white swipe, knocking you back. Ducking doesn't help, but your knife is faster.

### PS5 controller
Pair it with your Mac (System Settings → Bluetooth: hold Create + PS until the light bar flashes) or plug it in with USB-C, open the game, then press any button. You'll see "Controller connected". The controller rumbles when you shoot and when you're hit.

### Health and ammo
- **Hearts:** you have five. A pistol round costs one heart and a rifle round costs one and a half, so 4–5 hits kill you. After a hit you flicker for a moment, and shots pass through you. Health doesn't come back on its own. Tonics give back two hearts, and chests can hold hearts.
- **Limited ammo:** the HUD shows what's loaded and what's spare, like `6 / 18`.
  - Revolver: 6 in the cylinder and 18 spare to start, 48 spare at most.
  - Shotgun: 2 loaded and 4 spare to start, 12 spare at most.
  - When everything is empty, the gun clicks, and the knife still works.
- **Drops and chests:** most outlaws drop rounds, shells or cash. Chests always hold ammo, often a heart, and sometimes cash. The level has seven chests: a fixed one, plus six at random spots that change each run.
- **Respawn:** lighting a lantern saves your ammo. When you die, you come back there with full hearts and that ammo, and never with less than two reloads.

### Weapons
- **Revolver:** six shots, then a reload. Headshots kill instantly.
- **Knife:** a quick forward stab with a small lunge. It kills an outlaw in one hit and can knock a bullet out of the air.
- **Shotgun (close range):** 9 pellets in a wide spread that run out of force after about 180px. It kills up close, only staggers further out, and does no headshot kills. The boss takes at most about 3.5 damage per blast.

## The hero
Jack Rourke is a gunslinger with a readable silhouette.
- A studded brown hat with a creased crown and a wide brim curled at the sides.
- Dark hair, stubble, a heavy brow.
- A red neckerchief over a cream shirt and a dark waistcoat.
- A long rust-brown duster that hangs open, swept back off his hip. It sways when he stands still, streams out behind him when he runs and lifts when he jumps.
- A belt with a brass buckle, a cartridge belt and a holster on his hip.
- Dark trousers, worn boots and dark gloves.

When you haven't fired for a moment, the revolver goes back in the holster and its grip shows at his hip. His poses are:
- idle (breathing), and the three idle routines: revolver twirl, shotgun reload, knife cleaning
- an 8-frame run
- jump (the leading knee drives up, the coat trails) and fall (legs reaching for the ground, the coat lifting)
- aiming (the renderer handles any angle, for the Crowe Boys)
- kneel and shoot
- run and gun
- shotgun
- knife stab
- hit

The Crowe Boys are built the same way, each with their own silhouette:
- **Pistol gunmen:** lighter and quicker, with no coat. A low flat black hat with a red band, a red mask over the face, a sweat-stained shirt and a cowhide waistcoat, a bandolier and canvas trousers. They carry the revolver lowered until they draw.
- **Riflemen (the rooftop snipers):** a wide flat slate-grey brim, a dun mask, a long pale dust-coloured duster and a long rifle.
- **Silas:** bigger than his boys. A tall cream hat, grey hair, a grey stubble and a handlebar moustache, and a long black duster over a blood-red waistcoat and a white shirt.

### How the Crowe Boys die
How an outlaw goes down depends on what hit him:
- **Body shot:** one of three different falls, never the same one twice in a row:
  - he staggers back and falls
  - his knees buckle and he topples forward
  - the shot spins him round before he drops
- **Headshot:** the head pops in a burst of blood and bone. The body stands a beat with the neck spurting, drops to its knees, then goes over.
- **Buckshot:** he's thrown off his feet and lands on his back yards away.
- **Knife:** he folds up, drops to his knees and falls face down.

Every death sprays blood that stains the ground where it lands. A pool spreads out from under the body, hats fly off and tumble, and guns clatter down and stay where they land. The hero bleeds too when he goes down.

Press **H** on the title screen (or open `index.html#sheet`) to see the **character sheet**: every pose, the three Crowe Boys, the portrait at each level of health and the hero's palette, all drawn by the game's own code.

## Look and sound
The art direction follows how commercial pixel-art games are built ([resolution guide](https://notkey.studio/en/tutorials/choosing-the-right-render-resolution-for-a-pixel-art-game/), [SLYNYRD on parallax](https://www.slynyrd.com/blog/2019/11/12/pixelblog-23-parallax-scrolling) and [landscapes](https://www.slynyrd.com/blog/2026/5/27/pixelblog-62-landscape-backgrounds), [animation timing](https://www.sprite-ai.art/guides/animation-principles)):
- **Pixel canvas:**
  - **One grid:** the whole game is drawn on a 640×360 canvas, the same resolution as Blasphemous. One world unit is one pixel.
  - **Clean scaling:** the canvas is scaled up with hard edges, at a whole-number scale (2× at 720p, 3× at 1080p, 4× at 1440p) whenever that still fills most of the window.
  - **No mixels:** sprites, backgrounds, text and HUD all sit on that one pixel grid.
- **Own fonts:** two bitmap fonts made for the game, a 5×7 for labels and body text and a bold 7×9 for numbers and headings. No web fonts. Titles are the bold font blown up block by block and shaded like gold leaf, with a bevel, an outline and a drop shadow.
- **Calm backdrop:** the distance is hazy and low in contrast, so the street, the props and the characters read first.
- **Setting:** a sunset over canyon country, after the art-direction moodboard. Warm browns, rust, ochre and sand, set against a teal sky.
- **Depth:** the world is built in layers that each scroll at their own speed:
  - **Sky:** deep teal overhead, burning to gold round a low sun, with a hard ring of glare. Cloud banks are built from flattened puffs: lavender-grey on top and lit orange and gold underneath.
  - **Far mesas:** rose-grey buttes and spires, made of rock columns with flat caprock. Each column is lit on the side facing the sun, so rocks either side of the sun face it. Taller columns shade their neighbours, strata band them, and haze thickens toward their feet.
  - **Near buttes:** the same rock in deep red, less hazy.
  - **Canyon floor:** hazy bands out to the horizon, dotted with scrub and stones.
  - **Midground:** windmills with turning wheels, water towers, a barn, shacks, the far side of town with lamp-lit windows, a church, fences, a dead tree and a covered wagon. They're smaller and hazier than the street and rim-lit on the sun side.
  - **Red rock outcrops:** heaped boulders with dry grass, just behind the street, pushed back by the haze.
  - **Foreground:** dark boulders, grass clumps and the odd cactus or broken fence post passing in front, rim-lit, kept below the characters' feet.
- **The street you play on:** packed dirt with a sunlit lip, pebbles, ruts and dry grass hanging over the edge.
  - **The cut bank:** wavy sandstone layers under the dirt, some sticking out into the light and some eroded back into shadow, with hairline cracks. It gets darker and redder with depth.
  - **The drops:** unmistakable holes: black below a dim rim of the far wall, a bright lip where the dirt ends, a cliff face on each side (sunlit on one, in shadow on the other) and roots hanging into the dark.
- **Shadows:** each character throws a dithered shadow onto whatever is below: the street, a roof or a crate. It shrinks and fades as he jumps, and there's none over a drop.
- **One light:** everything in the world is lit by the low sun on the right: lit tops, a bright rim on the sun side, shadow on the far side and a dark outline. Characters are lit from their front and mirrored as a whole, like hand-drawn sprites.
- **Characters:** each is a small 3D model rendered straight onto the pixel grid:
  - bones wrapped in capsules and ellipsoids, with the coat made of hanging cloth strands
  - a z-buffer, and the sun in hard light bands per material (hat felt, skin, cloth, leather, denim, brass, steel)
  - shadows cast by the brim and arms
  - contour lines wherever one part passes in front of another, and a dark outline
  - eyes, brows, stubble, studs and buckles placed as single hand-set pixels
  - hand-drawn guns, rotated the RotSprite way

  Any pose, aim angle or fall comes out with the same proportions and light, and the drawn muzzle lands on the exact point bullets leave from.
- **Town:** every false front is built from real parts:
  - clapboard, vertical boards, board-and-batten or brick, with worn and peeled paint
  - trim at the corners, floors and cornice, with brackets
  - stepped, arched, pedimented or gabled parapets
  - framed, recessed windows: some lamp-lit from inside with curtains, others dark and catching the sky, some with shutters, bars on the bank's and the sheriff's
  - doors set back in shadow, carved signs with gilded or painted letters, and a stone footing

  Porches have a shingled roof on bracketed posts with a hanging lantern that glows, and the general store has a striped valance. Balconies have a railing of balusters. The wall sits in deep shade under each porch and balcony. Each building also has its own details: the saloon's lit batwing doors, the sheriff's star, the livery's barn doors and hay loft, the undertaker's coffins.
- **Props:**
  - crates with a nailed frame, a brace and a stencil
  - bulging barrels with iron hoops
  - hay bales with twine
  - sandstone ledges as heaped 3D boulders with a grassy top
  - plank walkways with posts and braces
  - ribbed 3D saguaros and barrel cacti with spines
  - a boxcar with a braced sliding door and spoked trucks
  - a black steam engine with brass bands and domes, a flared stack, a glowing headlamp, a cowcatcher and red drive wheels, and its wooden cab
  - telegraph poles with glass insulators and four sagging wires
  - the Dry Creek gate on log posts with a cow skull on top
  - the lookout tower with its pennant
  - a covered wagon, split-rail fences, hitching rails, a water trough holding the sky, a wagon wheel, lamp posts that glow, and the rail-yard track
- **Performance:** everything is built once and cached. A warm-up queue builds the town, props and the Crowe Boys' poses in the spare milliseconds of each frame, starting on the title screen, so nothing is built mid-fight.
- **Effects:**
  - Glows are drawn as hard-edged rings: lanterns, muzzle flashes, chests.
  - Muzzle flashes have a four-point star.
  - A dithered fade opens each run.
  - A hard-edged red frame shows when you're hurt.
  - The world goes grey when you die.
- **HUD:** one dark strip across the top:
  - **Left:** the portrait, name and hearts, then the knife, the revolver (a cylinder of rounds with loaded / spare) and the shotgun. The weapon in your hand gets a gold underline.
  - **Right:** cash.
  - **Portrait:** a painted bust of Jack in three states (fine, hurt, badly wounded), resampled onto a clean 42-pixel grid. It hangs just below the HUD strip like a badge.
  - **Portrait health cue:** the frame goes from steel to tarnished bronze to throbbing red, and the painting changes: a cut on the cheek, then blood down his face and on his kerchief.
- **Soundtrack:** a spaghetti-western score synthesized in the browser: nylon guitar, whistle, harmonica and hoofbeats, and a faster boss version. Everything is drawn in code and all sound is made in code.
- **From The Messenger:** snappy movement, hit-stop on big hits, and a quick respawn.

## Code
Everything lives in `index.html`:
- Level: `LEVELS` (the level's settings) and `buildDryCreek()`
- Player: `updatePlayer()` and `playerChecks()`
- Ladders and lasso: `climbLadder()`, `throwLasso()` and `swingRope()` (still in the engine, but Dry Creek has no ladders or hooks)
- Enemies: `FOE` (tuning) and `updateEnemy()`
- Weapons: `knifeHits()` and `fireShotgun()`
- Loot: `openChest()` and `collect()`
- Pixel renderer:
  - `PW` / `PH` (the 640×360 canvas), `resize()` (whole-number scaling) and `present()`
  - Fonts: `FONT_S`, `FONT_B`, `text()` and `logoText()`
- Background: `drawBackground()` with `buildSky()`, `buildClouds()`, `buildMesas()`, `buildPlain()`, the midground (`MIDS`, `MID_ITEMS`) and the rock outcrops (`buildOutcrop()`)
- Pixel toolkit: `Grid()` and `paintGrid()` (draw in materials, then light everything the same way), `pixCanvas()`
- World: `buildGround()` / `drawGround()` / `drawPits()`, `buildFacade()` / `drawAwning()` / `drawBalcony()` (the town), the props (`crateSprite()`, `barrelSprite()`, `rockSprite()`, `cactusSprite()`, `boxcarSprite()`, `locoSprite()` and more), the set dressing (`drawPoles()`, `drawSign()`, `drawDecor()`, `drawExtras()`) and `buildForeground()`
- Characters: `RIG` (the figure renderer: `OUTFITS` for each character's materials and build, the pose builder, the rasteriser and shading, and the guns), `charSprite()` (the sprite cache), `poseOf()` and the deaths (`initDeath()`, `deathPose()`)
- Warm-up: `warmQueue()` and `warmStep()`
- HUD: `hudGroups()`, `drawHUDShapes()`, `drawPortrait()` (with `woundLevel()`) and `drawMessages()`
- Music: `playStep()`
