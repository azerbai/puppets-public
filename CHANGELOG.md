# Changelog

## 1.1.0 (2026-11-13)

**Five more Minecraft versions.** Puppets now runs on 1.16.5, 1.18.2, 1.19.2, 1.20.4 and 1.21.4 as well, on Fabric and Forge, plus NeoForge from 1.20.4. That's nine versions and 22 builds in all. Every build passes the same in-game test: spawning, walking, jumping, following, scripts, the menu, driving, recording and replay, and inventory. The 1.16.5 build runs on Java 8, like the game itself.

**Smarter wars**
- Tanks and aircraft go looking for enemies across the whole battlefield (up to 1,024 blocks), instead of only what's nearby. Gunners hold fire until a target is close enough to hit.
- An aircraft with no enemy in sight circles where it is, instead of falling out of the sky. A helicopter on the ground lifts off and waits.
- A tank stuck on a rock or a wall backs off at an angle and tries again.
- The War page opens without a puppet picked. The whole-war buttons work, and the ones for a single puppet are greyed out.

**For addon makers**
- Addons can add their own commands, run something every server tick, and add pages to the menu's War screen.
- A new war advisor hook lets an addon steer puppets in a fight: where to move, when to hold fire, where to fly, how wide to circle and how close to drive.

**On the older versions (1.16.5 to 1.19.2)**, signs only have a front, so recorded sign edits all go on the front. Superb Warfare and TACZ support is only on the versions those mods exist for.

## 1.0.0 (2026-11-08)

The first release.

**Builds:** Minecraft 1.20.1 (Fabric, Forge), 1.21.1 (Fabric, Forge, NeoForge), 1.21.11 (Fabric, Forge, NeoForge), 26.3 (Fabric, NeoForge). Every
build passes the same in-game test: spawning, walking, jumping, following, scripts, the menu, driving, recording and
replay, inventory and stats; the mob test checks every mob feature below.

### Puppets
- Real players: tab list, `/list`, damage, air, hunger, saving, riding.
- The menu (O): spawn, pick, and work any puppet; every button shows its command.
- Actions: move, jump, sneak, sprint, look, turn, use, attack, mine (once, held or every N ticks), drop, swap, slots,
  screens (click, buttons, trade, signs), mount, run any command, say, respawn, kill.
- Behaviours: follow, goto, wander, guard, stay.
- Recording and replay, including other mods' packets; replay in place or relative.
- Plain-text scripts: wait, repeat, loop, waituntil, @Name, log, stop.
- Possession: drive a puppet with your own keys and see through its eyes.
- Shadow: a puppet of you stays when you log off.
- Skins from any player, kept across restarts. Rejoin after restart.
- Named mod support: Superb Warfare, TACZ, Trinkets, Curios, Rackcraft.
- Superb Warfare: puppets change seats, fire mounted guns at a named target (the turret keeps tracking it between
  shots), and fly aircraft in a circle with `sbw orbit <x> <y> <z> <radius>`, using the same mouse and throttle a
  player's client sends. An AC-130 holds about ±8 blocks of a 200-block circle.
- Helicopters: `sbw goto <x y z>`, `sbw hover` and `sbw orbit` fly an SBW helicopter (Mi-28, AH-6) with the collective,
  the mouse and its own hover mode; it hovers within about a block and circles within about a block of the ring.
  Gunners aim along SBW's own firing solution, so they hit from a moving aircraft.
- Puppet warfare: `/puppet <name> team <team>`, `/puppet <name> fight [teams]`, `/puppet war red blue`. Each puppet finds the
  nearest enemy on another team and fights with what it has: planes and helicopters circle over them, tanks close in
  and fire, gunners track and fire, TACZ riflemen keep their distance and reload, archers aim for the drop, and the
  rest charge in with swords (hitting the vehicle if the enemy is inside one).
- Loadouts: `/puppet kit save <name>` keeps what you carry and wear; `/puppet <name> kit <name>` hands it out.
- Wars that keep going: `/puppet war red blue respawn` brings the fallen back after 5s where they started, with their
  kit. `/puppet peace` ends it. Mob puppets join wars too (`/puppet mob <name> team red`): zombies charge, skeletons
  shoot, golems smash.
- Anti-air: puppets crewing an HPJ-11 or LAV-AD (or holding an Igla) go for aircraft first; `fight prefer air|ground`
  to choose. Puppets fire Superb Warfare's own hand-held guns and launchers, and reload them.
- Rounds: `/puppet war red blue rounds 5`. A round ends when one team is left standing; everyone goes back where they
  started with what they started with, until a team has won 5. A war without rounds or respawns ends by itself when
  one side is gone.
- The war's score on screen: bars at the top for the round and score and for each team (still up, kills, fighters
  and vehicles lost), a casualty list in the sidebar (every kill as `killer [weapon] victim`, every vehicle or
  emplacement destroyed), each kill above the hotbar, and a title for each round and the winner. `/puppet war hud
  off` hides it (config `warHud`). It's all the game's own bars, sidebar and titles, so players without the mod see it.
- Igla homing: puppets keep their Igla's sights up while the missile flies (it only stays guided while its owner
  aims), aim under its launch kick and lead the aircraft, and hold fire when it's too close to turn.
- A puppet that can't see an enemy goes after the nearest one instead of standing still, and one trapped in a pit
  digs a staircase out (config `digOut`).
- Pathfinding: puppets walking somewhere find their way round walls, up steps and round lava (config `pathfinding`).
- Patrols: `/puppet <name> patrol <x y z> <x y z>... [once] [wait <ticks>]`.
- Chat orders: say "Bob, follow me", "Bob, come here", "Bob, stay", "everyone, guard" (config `chatOrders`).
- Mob puppets drive Superb Warfare vehicles too: possess one in the driver's seat, or `/puppet mob <name> sbw <keys>`.
- `check` for automated tests; addon API with an example addon.

### Jobs
- miner, quarry, lumberjack, farmer, courier, fisher, crafter (plus guard), by command or the menu's Jobs page.
- Real tools at real speed, digging only what it can see (tunnelling to hidden ores), eating when hungry, emptying
  into a chest, picking up drops, and stopping with a reason when it runs out of something.

### Driving together
- A second driver joins the first: keys add up, the look follows whoever turned last; a co-driver takes over when
  the main driver lets go.
- Watch: look through a puppet's eyes without driving.

### Mob puppets
- Take over any mob (`/puppet mob take`, or the menu's Mobs page); its own AI stands down.
- Walk, look, jump, goto, come, follow, wander, stay, attack, mount; scripts and recordings; driving.
- Per kind: horses jump high and rear, farmers harvest and plant, tamed pets sit, sheep graze, creepers ignite,
  endermen pick up and place blocks.
- Unrestricted: place, break, fly, talk, hit, speed, teleport.
- Own mind: hand its AI back while it stays a puppet.

### Fixed during testing

- TACZ: puppets no longer sprint into range (TACZ won't fire or reload on the run).
- NeoForge: mods that send data to joining players (Curios) no longer stop puppets joining.
- Puppets really jump, sneak and sprint (the API's hold-key methods had hidden the game's own).
- A mob taken mid-walk stops where it stands.
- Forge 1.21.1: if the world starts before Forge's event bus, `/puppet` registers on the first tick.
