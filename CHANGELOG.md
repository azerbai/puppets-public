# Changelog

## 1.0.0 (unreleased)

The first release.

**Builds:** Minecraft 1.20.1 (Fabric, Forge), 1.21.1 (Fabric, Forge, NeoForge), 1.21.11 (Fabric, NeoForge). Every
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
- NeoForge: mods that send data to joining players (Curios) no longer stop puppets joining.
- Puppets really jump, sneak and sprint (the API's hold-key methods had hidden the game's own).
- A mob taken mid-walk stops where it stands.
- Forge 1.21.1: if the world starts before Forge's event bus, `/puppet` registers on the first tick.
