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

#### Installation / Usage:

**From source (any platform with Python 3):**
```
$ git clone <this-repo-url>
$ cd dnd-tools
$ pip install numpy
$ python setup.py install
$ dnd-tools
```

Or run directly:
```
$ python scripts/dnd-tools
```

**Arch-based distros** (original AUR package):
```
yay -S dnd-tools
```

---

#### Changelog (v0.2.0):

**Critical bug fixes:**
- Fixed SyntaxError (missing colon) that prevented the script from running
- Fixed broken boolean logic in all skill proficiency assignments across 13 class/race sections (`if x or y == "value"` was always true)
- Fixed garbled loot table entry ("Potrange of keys in dictionaryion of fire breath" -> "Potion of fire breath")
- Fixed multiple variable name typos in skill assignments (skill_peception, skill_surviavl, skill_slieght, etc.)
- Fixed Cleric Medicine skill setting wrong variable (skill_insight instead of skill_medicine)
- Fixed Bard Animal Handling setting skill_religion instead of skill_animal
- Fixed Wizard Insight using wrong modifier (mod_int instead of mod_wis)

**High priority fixes:**
- Replaced unsafe stdout redirection for character save with proper file I/O and path sanitization
- Added input validation for all integer inputs (no more crashes on non-numeric input)
- Replaced recursive input validation with while loops to prevent stack overflow
- Fixed "Intimation" typo to "Intimidation" in Sorcerer skill prompt

**Code quality improvements:**
- Removed Python 2 compatibility shim (xrange/raw_input)
- Extracted roll_dice(), roll_gem(), roll_items() helpers to reduce loot function duplication (~745 lines reduced to ~273)
- Removed unnecessary math and itertools imports
- Normalized input case handling with .lower() and input_yn() helper
- Added docstrings to all major functions
- Fixed loop variable shadowing global char_class

---

**Bugs:**
Please review existing issues before making a new issue report. Be as clear and descriptive as possible when making bug reports, including output logs and what steps you've attempted to remedy the problem yourself.

**Contributing:**
See [CONTRIBUTING.md](CONTRIBUTING.md).
