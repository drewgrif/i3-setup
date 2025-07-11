# 🪟 i3-setup

![Made for Debian](https://img.shields.io/badge/Made%20for-Debian-A81D33?style=for-the-badge&logo=debian&logoColor=white)

A minimal but functional i3 rice script for Debian-based systems.  
Installs all core packages, window manager configs, and themes — ready to go out of the box.

> Part of the [JustAGuy Linux](https://github.com/drewgrif) window manager collection.

<img width="3440" height="1440" alt="2025-07-11_17-26" src="https://github.com/user-attachments/assets/6aaa3bd2-298e-4a7a-a08d-318988b49a09" />

---

## 🚀 Installation

### Quick Install
```bash
git clone https://github.com/drewgrif/i3-setup.git
cd i3-setup
chmod +x install.sh
./install.sh
```

### Installation Options

The installer supports the following options:

```bash
./install.sh [OPTIONS]

Options:
  --only-config      Only copy config files (skip packages and external tools)
  --export-packages  Export package lists for different distros and exit
  --help             Show help message
```

**New Features:**
- **Export packages**: Use `--export-packages` to see equivalent package lists for Arch Linux and Fedora
- **Streamlined installation**: Simpler, more reliable installation process
- **Better error handling**: Installation fails fast on errors to prevent partial setups

**Package Installation:** Packages are installed in logical groups (core, UI, file manager, audio, utilities, terminal, fonts) for better organization.

### Distribution-Agnostic Installation

<details>
<summary><strong>⚠️ UNSUPPORTED: Instructions for other distributions (click to expand)</strong></summary>

**IMPORTANT:** These instructions are provided as-is for advanced users. Non-Debian distributions are **NOT officially supported**. Package names and availability may vary. Use at your own risk.

**Arch Linux:**
```bash
# Install dependencies (package names may differ)
sudo pacman -S i3 sxhkd polybar rofi dunst picom thunar \
  xorg-xbacklight pamixer pavucontrol feh flameshot firefox \
  network-manager-applet xfce4-power-manager ttf-font-awesome

# Copy configuration files
./install.sh --only-config
```

**Fedora:**
```bash
# Install dependencies (package names may differ)
sudo dnf install i3 sxhkd polybar rofi dunst picom thunar \
  xbacklight pamixer pavucontrol feh flameshot firefox \
  network-manager-applet xfce4-power-manager fontawesome-fonts

# Copy configuration files
./install.sh --only-config
```

**openSUSE:**
```bash
# Install dependencies (package names may differ)
sudo zypper install i3 sxhkd polybar rofi dunst picom thunar \
  xbacklight pamixer pavucontrol feh flameshot firefox \
  NetworkManager-applet xfce4-power-manager fontawesome-fonts

# Copy configuration files
./install.sh --only-config
```

</details>

### Advanced Usage Examples

```bash
# Export package lists for other distributions
./install.sh --export-packages

# Update only configuration files (useful for non-Debian systems)
./install.sh --only-config
```

**Note:** The script can be run from any location - it automatically detects its directory.

---

## 📦 What It Installs

| Component             | Purpose                          |
|------------------------|----------------------------------|
| `i3`                  | Tiling window manager            |
| `sxhkd`               | Hotkey daemon                    |
| `picom` `(FT-Labs)`   | Compositor for transparency      |
| `polybar`             | Status bar                       |
| `rofi`                | Application launcher             |
| `dunst`               | Notifications                    |
| `wezterm`             | Terminal emulator (main)         |
| `st`                  | Simple terminal (scratchpad)     |
| `firefox-esr`         | Default web browser              |
| `thunar` + plugins    | File manager                     |
| `nala`                | Better apt frontend              |
| `pipewire`            | Audio handling                   |
| `flameshot`,          | Screenshot tools                 |
| `micro`               | Terminal text editor             |
| `redshift`            | Night light                      |
| `qimgv`               | Lightweight image viewer         |
| `fzf`, etc.           | Utilities & enhancements         |

**Optional during install:**
- `geany` + plugins - Lightweight IDE (installer will prompt)

> 📄 _Need help with Geany? See the full guide at [justaguylinux.com/documentation/software/geany](https://justaguylinux.com/documentation/software/geany)_

---

## 🎨 Appearance & Theming

- Minimal theme with custom wallpapers
- Polybar with optimized layout: system info (left), workspaces (center), controls (right)
- Enhanced polybar with multiple font support (Roboto Mono, FontAwesome, Hack Nerd Font)
- Dunst, rofi, and GTK themes preconfigured
- Wallpapers stored in `~/.config/i3/wallpaper`
- GTK Theme: [Orchis](https://github.com/vinceliuice/Orchis-theme)
- Icon Theme: [Colloid](https://github.com/vinceliuice/Colloid-icon-theme)

> 💡 _Special thanks to [vinceliuice](https://github.com/vinceliuice) for the excellent GTK and icon themes._

---

## 🔑 Keybindings Overview

| Key Combo              | Action                                |
|------------------------|----------------------------------------|
| `Super + Enter`        | Launch terminal (wezterm)              |
| `Super + Shift + Enter`| Toggle scratchpad terminal             |
| `Super + Space`        | Launch rofi                            |
| `Super + Q`            | Close focused window                   |
| `Super + H`            | Help via keybind viewer                |
| `Super + V`            | Audio mixer (pulsemixer) in scratchpad |
| `Super + Shift + R`    | Restart i3                             |
| `Super + 1-9,0`        | Switch to workspace 1-10               |
| `Super + Shift + 1-9,0`| Move window to workspace 1-10          |
| `Super + Minus`        | Move window to scratchpad              |
| `Super + Equal`        | Show/hide scratchpad                   |

Keybindings are configured via:

- `~/.config/i3/sxhkd/sxhkdrc`
- `~/.config/i3/scripts/help` (run manually or with `Super + H`)

---

## 📂 Configuration Files

```
~/.config/i3/
├── config                 # Main i3 config
├── workspaces.conf        # Workspace definitions
├── rules.conf             # Window rules and appearance
├── sxhkd/
│   └── sxhkdrc            # Keybinding configuration
├── polybar/
│   ├── config.ini
│   └── polybar-i3
├── dunst/
│   └── dunstrc
├── rofi/
│   ├── config.rasi
│   ├── keybinds.rasi
│   └── power.rasi
├── picom/
│   └── picom.conf
├── scripts/
│   ├── autostart.sh
│   ├── changevolume
│   ├── power
│   ├── scratchpad
│   └── help
├── wallpaper/
│   └── (wallpaper images)
```

### Terminal Configuration

The setup uses two terminals for different purposes:
- **Main terminal** (`Super + Enter`): Uses wezterm by default
- **Scratchpad terminal** (`Super + Shift + Enter`): Enhanced auto-detection with comprehensive fallback support

#### Scratchpad Terminal Support

The scratchpad system now supports multiple terminal emulators with intelligent fallback:

**Supported terminals:** st, ghostty, alacritty, kitty, wezterm, xfce4-terminal, gnome-terminal, konsole, urxvt

**Priority order:**
1. User-defined via `I3_SCRATCHPAD_TERMINAL` environment variable
2. st (preferred for speed and minimal resource usage)
3. Automatic fallback through available terminals

To customize the scratchpad terminal, set the environment variable in your shell config:
```bash
export I3_SCRATCHPAD_TERMINAL=ghostty  # or any terminal you prefer
```

**Advanced scratchpad usage:**
```bash
# Launch custom applications in scratchpad mode
Super + Shift + Enter    # Default terminal scratchpad
Super + V                # Pulsemixer scratchpad
# Or via script: scratchpad app_name app_command
```

---

## 🎨 Modular Configuration

This i3 setup uses a modular configuration approach for better organization:
- **config**: Main i3 configuration with includes
- **workspaces.conf**: Workspace definitions (1-10)
- **rules.conf**: Window rules, borders, gaps, and scratchpad settings
- **sxhkd/sxhkdrc**: All keybindings managed by sxhkd for consistency

This modular approach makes it easy to:
- Understand and modify specific aspects of the configuration
- Share configurations between different window managers
- Keep the main config file clean and focused

---

## 📺 Watch on YouTube

Want to see how it looks and works?  
🎥 Check out [JustAGuy Linux on YouTube](https://www.youtube.com/@JustAGuyLinux)
