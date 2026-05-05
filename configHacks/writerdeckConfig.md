# Config Hacks
For my Writerdeck setup, I boot to the command line (no desktop environment), and then start up the apps I want to use in single labwc instances. This is my setup for that.

# Software Used
* Alacritty
* Obsidian (installed as a flatpak)
* labwc for window management
* waybar to monitor battery use

### bash aliases
add these aliases to the bottom of the .bashrc file:
```
alias obsidian='setterm -cursor off; sudo dmesg -D; labwc -s "flatpak run md.obsidian.Obsidian" &>/dev/null; sudo dmesg -E; setterm -cursor on; reset; clear'
alias ala='setterm -cursor off; sudo dmesg -D; labwc -s alacritty &>/dev/null; sudo dmesg -E; setterm -cursor on; reset; clear'
```

### Alacritty
No special setup is needed

### Obsidian
Install the md.obsidian.Obsidian flatpak, then run these commands to set the flatpak to launch in a native Wayland wrapper instead of an XWayland wrapper:
`flatpak override --user --socket=wayland md.obsidian.Obsidian`
`flatpak override --user --env=ELECTRON_OZONE_PLATFORM_HINT=wayland md.obsidian.Obsidian`

### labwc
Add these window rules (and keyboard shortcut if you want a session killswitch) to ~/.config/labwc/rc.xml
```
<?xml version="1.0"?>
<openbox_config xmlns="http://openbox.org/3.4/rc">
	<touch deviceName="11-0038 generic ft5x06 (00)" mapToOutput="DSI-2" mouseEmulation="yes"/>
	
	<windowRules>
		<windowRule identifier="alacritty">
			<maximized>yes</maximized>
			<border>false</border>
		</windowRule>
		<windowRule identifier="Obsidian">
			<maximized>yes</maximized>
			<border>false</border>
			<ignoreGeometry>yes</ignoreGeometry>
		</windowRule>
		<windowRule type="normal">
			<maximized>yes</maximized>
			<fullscreen>yes</fullscreen>
			<decorations>no</decorations>
			<ignore_configure_request>yes</ignore_configure_request>
			<skipPager>yes</skipPager>
			<skipTaskbar>yes</skipTaskbar>
		</windowRule>
	</windowRules>

	<keyboard>
		<keybind key="W-q">
			<action name="Exit" />
		</keybind>
	</keyboard>
</openbox_config>
```

Add this line to the ~/.config/labwc/autostart file to automatically start the Waybar battery monitoring at the start of every labwc session:
```
waybar &
```

### waybar
~/.config/waybar/config
```
{
    "layer": "overlay",
    "position": "top",
    "height": 26,
    "modules-center": ["clock"],
    "modules-left": ["cpu", "temperature"],
    "modules-right": ["custom/battery"],
    "exclusive": false,
    "passthrough": true,

    "custom/battery": {
        "exec": "python3 /home/writer/.ups/bat_status.py",
        "interval": 5,
        "format": "{}",
        "tooltip": false
    },
    "clock": {
        "interval": 60,
        "format": " 🕗 {:%H:%M}"
    },
    "cpu": {
        "interval": 1,
        "format": "▩ CPU: {usage}%",
        "max-length": 10
    },
    "temperature": {
        "critical-threshold": 80,
        "format": " | 🌡 Temp: {temperatureC}°C",
        "format-critical": " | 🌡 Temp: {temperatureC}°C"
    }
}
```

~/.config/waybar/style.css
```
window#waybar {
    background-color: rgba(15, 15, 15, 1);
    font-size:1.25em
}

#custom-battery {
    padding: 0 0px;
    background: transparent;
        color: #777777;
}

#cpu {
        color: #777777;
}

#temperature {
        color: #777777;
}

#clock {
        color:#777777;
}

```
