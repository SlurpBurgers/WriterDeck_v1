# WriterDeck v1
I will be adding more information to this file, including some print and assembly instructions, as well as some software files for cool writerdeck functionality.
![alt text](https://github.com/SlurpBurgers/WriterDeck_v1/blob/main/img/expl_darkBg.png "exploded view of the printed parts")

# Bill of Materials
| Item | Qty |
| --- | --- |
| Raspberry Pi | 1 |
| Waveshare UPS Module 3s | 1 |
| 18650 Liion Cell | 3 |
| Mechanical Swtich | 48 |
| Keycap Set | 1 |
| RP2040  | 1 |
| ADS1115 | 1 |
| PS2 Joystick Module | 1 |
| 2 Wire Pogo Pin Connector | M/F set |
| Right-angle USB extender | 1 |


# Writerdeck Setup and Config
[writerdeckConfig.md](https://github.com/SlurpBurgers/WriterDeck_v1/blob/main/configHacks/writerdeckConfig.md)
This is my current setup for distraction free workflows.

I use labwc as a standalone window manager to run a single app at once, the config linked is to set up two apps to run in this fashion:
* Obsidian (as a flatpak)
* alacritty (to run the TUI word processors)

Obsidian is pretty self-explanatory, and I use it when I need to switch between multiple documents quickly, or to organize larger scale projects. Alacritty is used to launch your choice of TUI word processor apps for distraction-free writing. Wordgrinder, Pure, Micro, VIM, etc are all great choices and I am still cycling between them to get a feel for what will work in a longer-term workflow.

### Example Screenshots
#### wordgrinder
![alt text](https://github.com/SlurpBurgers/WriterDeck_v1/blob/main/configHacks/screenshots/wordgrinder.png "wordgrinder running in labwc with a waybar instance for battery info")

#### Obsidian
![alt text](https://github.com/SlurpBurgers/WriterDeck_v1/blob/main/configHacks/screenshots/obsidian.png "obsidian running in labwc with a waybar instance for battery info")

#### pure
![alt text](https://github.com/SlurpBurgers/WriterDeck_v1/blob/main/configHacks/screenshots/pure.png "pure running in labwc with a waybar instance for battery info")
