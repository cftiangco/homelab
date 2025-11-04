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

#### Lesson 1 - Basic NPC Flow

```txt
prontera,150,150,4	script	Tutorial NPC	100,{

	mes "[Tutorial NPC]";
	mes "Hello there! Welcome to rAthena scripting!";
	next;

	mes "I can give you some items, Zeny, or warp you!";
	next;

	switch(select("Give me Apple:Give me Zeny:Warp me to Payon:Nothing")) {
		case 1:
			getitem 512, 5; // Apple ID 512
			mes "Here’s 5 Apples!";
			break;
		case 2:
			Zeny += 1000;
			mes "You got 1,000 Zeny!";
			break;
		case 3:
			warp "payon",100,100;
			end;
		default:
			mes "Okay, see you next time!";
			break;
	}
	close;
}
```

**Key Concept**
- mes
  - Show a message box to the player
- next  
  - Proceed to the next message box
- select("Option1:Option2:..")
  - Create a menu
- getitem <item_id>, <quatity/amount>
  - Give an item to the user
- warp <map>,<x>,<y>
  - Teleport the user
- end or close
  - Ends the script

#### Lesson 2 - Variables and Conditions
Use variables to remember things
```txt
prontera,160,160,4  script  Variable NPC    100,{
    if(#got_reward) {
        mes "You already claimed your reward!";
        close;
    }

    mes "Do you want your one-time reward?";
    if (select("Yes:No") == 1) {
        getitem 7898, 1;
        set #got_reward, 1;
        mes "You've recieved your one-time reward";
    }
    close;
}
```

***Explanation***
- @var
  - Temporary (lost when you logout)
- #var
  - Permanent (per-account)
- $var
  - Global (Shared by everyone)
