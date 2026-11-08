# CurseForge page text

## Summary (under 90 words)

Puppets lets you spawn fake players that the server treats as real ones, then control them. Press O for a menu or use /puppet. They walk, mine, build, fight, follow you, run simple scripts, or replay something you recorded yourself (other mods' keys included). You can take one over and play as it, give them jobs like mining or farming, and take control of mobs too. Made for testing multiplayer stuff on your own. Fabric, Forge and NeoForge, 1.20.1 to 26.3.

## Description

I made this because testing anything multiplayer on your own is a pain. Teams, claims, vehicles with seats, minigames, anything that needs a second player. Puppets gives you as many extra players as you want and lets you control them without opening more game windows.

A puppet joins the server as an actual player. It shows up in the tab list and `/list`, counts for `@a`, takes damage, gets hungry, keeps its inventory and is saved like anyone else. Other mods see it as a normal player.

### Getting started

Open your world to LAN with cheats on (or be op on a server), then press **O**. Type a name, hit Spawn, pick the puppet in the list and use the buttons. Hovering a button shows the command it runs, so you pick up the commands as you go. Everything works from commands too: `/puppet help` lists the basics.

Only the server needs the mod. Install it on your client as well if you want the menu and driving.

### What they can do

- Walk, jump, sneak, sprint, look around, use items, attack, mine (once, held down, or every few ticks), drop, swap hands
- Open chests and machines, click slots, press buttons, trade with villagers, write signs
- Follow you or another player, walk to a spot, wander, guard an area from mobs
- Run any command as them
- Wear any player's skin

### Recording

Press Record, do the thing yourself, press Stop. Any puppet can replay it, either where you recorded it or starting from where it stands. It records what your game sends the server, so it also replays other mods' keybinds and buttons, even for mods Puppets knows nothing about.

### Scripts

Scripts are plain text files, one action per line:

```
repeat 4
  move forward
  wait 1s
  turn right
end
@Alice say done
```

`wait`, `repeat`, `loop`, `waituntil`, and `@Name` to control other puppets from the same script. A broken line gets skipped and logged, it won't crash anything.

### Driving

`/puppet Bob possess` (or the Drive button) puts you in the puppet. Your keys and mouse move it and you see through its eyes. Press O to go back to your own body.

If someone's already driving it, you join them: both your keys count, and it looks wherever whoever moved their mouse last is looking. Or use Watch to just ride along behind its eyes.

### Jobs

Give a puppet a job and it gets on with it like a player would. It uses real tools at normal speed (they wear down), eats when it's hungry, empties its inventory into a chest when it's full, and stops and tells you why if it runs out of something.

- **miner**: digs out ores in an area, tunnelling to ones it can't see
- **quarry**: digs out everything in an area, top layer first
- **lumberjack**: chops trees and replants saplings
- **farmer**: harvests, replants, and tills dirt near water if it has a hoe
- **courier**: moves items from one chest to another
- **fisher**: fishes with a rod and reels in when something bites
- **crafter**: crafts a recipe at a crafting table over and over

Example: `/puppet Steve job miner radius 10 store 100 64 200`

### Mobs

`/puppet mob take` turns the mob you're looking at into a puppet (or use the Mobs page in the menu). Its normal AI switches off and it does what you tell it: walk, jump, pathfind somewhere, follow you, attack, ride things, play scripts and recordings. You can drive it too.

They can also do whatever their kind can actually do: horses jump and rear, farmer villagers harvest and plant, tamed wolves and cats sit, sheep eat grass, creepers light their fuse, endermen pick blocks up and put them down.

Turn on **unrestricted** and any mob can place and break blocks, fly, talk in chat, hit things, go faster or teleport.

### Other stuff

- `/puppet shadow` logs you off and leaves a puppet of you standing there until you come back
- Puppets that were online come back after a restart
- `/puppet spawn Bob count 5` for a crowd, `/puppet all <action>` to control them all at once
- Built-in support for Superb Warfare vehicles (puppets drive, man the guns and shoot at whoever you name, and can fly a plane in a circle with `sbw orbit`; mob puppets can drive too), TACZ guns, Trinkets and Curios. Everything else works through recordings
- `check` commands that return 1 or 0, handy for command blocks and automated tests
- An addon API if you want to add your own actions or behaviours (there's an example addon)
- 100 puppets cost about 7ms a tick in my testing

### Versions

| Minecraft | Loaders |
| --- | --- |
| 1.20.1 | Fabric, Forge |
| 1.21.1 | Fabric, Forge, NeoForge |
| 1.21.11 | Fabric, Forge, NeoForge |
| 26.3 | Fabric, NeoForge |

Fabric needs Fabric API.

### FAQ

**Is this like Carpet's /player?** Similar idea, but Puppets has a menu, recording, scripts, driving, jobs and mobs, and runs on Forge and NeoForge too. Carpet is great for technical stuff and works fine alongside this.

**Do puppets count towards the player limit?** Yes, they're real players. Set `maxPuppets` in the config if you want a cap.

**Can they be on a real server?** Yes. They use offline-mode UUIDs from their names, so they never clash with real accounts.

**Does it work with other mods?** I tested it in a 300-mod pack. If a mod does something with players, it should work with puppets.

Found a bug or have an idea? Let me know. Made by @azerbaiGH.
