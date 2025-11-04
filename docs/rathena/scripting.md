# rAthena Scripts

### What can you do about rAthena scripts?
- Create NPC (shopkeepers, quest givers, warpers, etc.)
- Handle events (Onlnit, OnTimer, OnNPCKillEvent, etc)
- Manage Custom features (refineries, PvP warps, boss cages)

### How to modify scripts?
Scripts are written in .txt file and can be located inside: rathena/npc/custom

### How NPC Scripts are structured?

```txt
prontera,150,150,4	script	Ninong Crimson	100,{
  mes "[Test NPC by Crimsonen]";
	mes "Hello, adventurer";
	mes "Would you like to recieve 1,000 Zeny?";
	next;
	if(select("Yes:No") == 1) {
		Zeny += 1000;
		mes "[Test NPC by Crimsonen]";
		mes "You now have " + Zeny + " zeny!";
	} else {
		mes "[Test NPC by Crimsonen]";
		mes "Maybe next time!";
	}
	close;
}
```
**Explanation:**
- `prontera,150,150,4`
  - <map_name>,<x>,<y>,<direction> (4 = facing down)
- `script`
  - NPC type
- `Sample NPC`
  - Display Name
- `100`
  - Sprite ID (100 = default male sprite)
- `Inside {}`
  - Your dialogue, logic or code

### How to load the newly created custom script(s)?
1. Save your new script to:
```sh
rathena/npc/custom/test_npc.txt
```
2. Then add it to:
```sh
npc/scripts_custom.conf

# Example:
# npc: npc/custom/test_npc.txt
```
3. And then reload the game or restart the server:

```sh
@reloadscript
```
