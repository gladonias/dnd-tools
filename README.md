# dnd-tools

**dnd-tools** is a set of interactive command line tools for Dungeons and Dragons 5th Edition.

This repository is a fork of [savagezen/dnd-tools](https://github.com/savagezen/dnd-tools).

The aim of this project, inspired by [donjon](http://donjon.bin.sh/), is to create an offline, cross-platform, GM/DM tool set.

---

#### Features:

- *Completely interactive:*  prompted with start menu after every function
- *Character generator:*  any or all stat blocks and features can be randomized
- *NPC generator:*  35 NPC classes with stat blocks populated as with character creation (fixed NPC stats are in the Monster Manual and many places online)
- *Save generated character:*  export generated character to text file
- *Dice roller:*  any number of dice, any number of sides, plus modifiers
- *Encounter calculator:* calculates modified experience per party size / level and monster party size (and CR)
- *Loot generator:* random loot tables based on CR and number of enemies
- *Initiative roller:* random d20 rolls for n number of players with initiative bonus
- *Tarokka card game:*  tarot card game from Curse of Strahd
- *Wild magic effects:*  effect roller for Wild Magic sorcerers

---

#### Requirements:

- Python 3.6 or later
- No external dependencies

Runs on **Linux**, **macOS**, and **Windows**.

---

#### Installation / Usage:

**From source (any platform with Python 3):**
```
$ git clone <this-repo-url>
$ cd dnd-tools
$ python setup.py install
$ dnd-tools
```

Or run directly without installing:
```
$ python3 scripts/dnd-tools
```

**Windows:**
```
python scripts\dnd-tools
```

**Arch-based distros** (original AUR package):
```
yay -S dnd-tools
```

---

#### Changelog:

**v0.3.1:**
- Fixed overlapping range in CR 5-10 loot table (values 67-69 were unreachable)
- Fixed coin generation for CR 0-4: gold pieces were always 0 (dice rolls never accumulated)
- Fixed coin output displaying electrum value instead of copper
- Fixed crash in CR 11-16 loot table (`random.choice(list(item))` used wrong variable)
- Fixed crash in CR 17+ loot table (keys from item_e looked up in item_d)
- Fixed Arcana base skill using Dexterity modifier instead of Intelligence
- Fixed armor name typos: "chain male"/"scale male"/"splint male" -> "mail" (5 occurrences)
- Fixed "Efretti chain" -> "Efreeti chain"
- Filled missing keys in loot tables: item_f (21-23), item_g_12 (7), item_h (62), item_i (76)

**v0.3.0:**
- Removed numpy dependency — script now uses only Python standard library
- Updated shebang to `python3` and removed Python 2 `__future__` imports
- Switched setup.py from deprecated `distutils` to `setuptools`
- Added `python_requires='>=3.6'` to setup.py
- Fixed missing keys in loot tables (item_b key 73, item_g keys 11-14 and 59)
- Fixed typos: "Sliver-plated" -> "Silver-plated", "Fochlucan bandor" -> "Fochlucan bandore", "Chineese" -> "Chinese"
- Fixed grammar: "A story witty storyteller" -> "A witty storyteller"
- Fixed unmatched parenthesis in Tarokka card output

**v0.2.0:**
- Fixed SyntaxError (missing colon) that prevented the script from running
- Fixed broken boolean logic in all skill proficiency assignments across 13 class/race sections
- Fixed garbled loot table entry ("Potion of fire breath")
- Fixed multiple variable name typos in skill assignments
- Replaced unsafe stdout redirection for character save with proper file I/O
- Added input validation for all integer inputs
- Replaced recursive input validation with while loops to prevent stack overflow
- Removed Python 2 compatibility shim
- Extracted loot helper functions to reduce duplication
- Normalized input case handling with `.lower()` and `input_yn()` helper
- Added docstrings to all major functions
- Fixed loop variable shadowing

---

**Bugs:**
Please review existing issues before making a new issue report. Be as clear and descriptive as possible when making bug reports, including output logs and what steps you've attempted to remedy the problem yourself.

**Contributing:**
See [CONTRIBUTING.md](CONTRIBUTING.md).
