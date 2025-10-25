# 🎮 Roblox Player Display System

[![Version](https://img.shields.io/badge/version-2.2-blue.svg)](https://github.com/yourusername/player-display-system)
[![Roblox](https://img.shields.io/badge/platform-Roblox-red.svg)](https://www.roblox.com)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

A customizable and feature-rich player display system for Roblox games with animated titles, roles, and rank progression.

## ✨ Features

- 🏆 **Dynamic Rank System** - 20+ rank titles based on Summit count
- 👑 **Role Management** - Owner, Developer, Admin, Mod, Helper, and more
- 🎨 **Animated Colors** - 15+ color animation effects (Rainbow, Galaxy, RGB pulses)
- ✅ **Verified Badges** - Animated checkmarks for verified users
- 💎 **Premium Support** - Displays Roblox Premium icon
- 🎯 **Custom Titles** - Personalized titles with animated colors
- 📊 **Real-time Updates** - Summit count updates dynamically
- 🔧 **Easy Configuration** - Simple tables for setup

## 📦 Installation

1. **Download** the `PlayerDisplayClient.lua` file
2. **Place** it in either:
   - `StarterPlayer` → `StarterPlayerScripts` (recommended)
   - `StarterGui`
3. **Configure** the tables in the configuration section
4. **Test** in your game!

## ⚙️ Configuration

### 1. Adding Roles

```lua
local ROLES = {
    Owner = {
        ["Username1"] = true,
        ["Username2"] = true
    },
    Developer = { 
        ["ItoRenz00"] = true,
        ["DevPlayer1"] = true
    },
    Admin = {
        ["Admin1"] = true,
        ["Admin2"] = true
    }
}
```

### 2. Adding Custom Titles

```lua
local CUSTOM_TITLES = {
    ["ItoRenz00"] = "CEO",
    ["Player1"] = "VIP Member",
    ["Player2"] = "Content Creator",
    ["Admin1"] = "Senior Admin"
}
```

### 3. Adding Color Animations

```lua
local CUSTOM_COLOR_TYPES = {
    ["ItoRenz00"] = "random_rgb_new_6",
    ["Player1"] = "rainbow",
    ["Player2"] = "purple_galaxy",
    ["Admin1"] = "blue_rgb",
    
    -- Owner Rainbow (Special Effect)
    ["OwnerUsername1"] = "owner_rainbow"
}
```

### 4. Adding Verified Users

```lua
local VerifiedUsersList = {
    ["ItoRenz00"] = true,
    ["Player1"] = true,
    ["VIPUser"] = true
}
```

## 🎨 Available Color Types

| Color Type | Description |
|------------|-------------|
| `rainbow` | Classic rainbow cycle |
| `owner_rainbow` | Slow elegant rainbow (for owners) |
| `purple_galaxy` | Purple to pink galaxy effect |
| `pink_pulse` | Pulsing pink animation |
| `blue_rgb` | Blue-cyan transitions |
| `red_rgb` | Red-orange-pink gradient |
| `black_random_rgb` | Dark RGB transitions |
| `random_rgb_new_1` to `random_rgb_new_6` | Various RGB effects |
| `random_rgb_1` & `random_rgb_2` | Alternative RGB animations |

## 🏆 Rank System

The system includes 20+ ranks based on Summit count:

| Summit Count | Rank | Color |
|--------------|------|-------|
| 10,000+ | 🌟 GOD | Gold |
| 8,000+ | ⚡ Dewa | Purple |
| 6,500+ | 🔥 Si Paling Pro | Orange Red |
| 5,000+ | ❄️ Too EZ for me | Deep Sky Blue |
| 3,000+ | 🏆 Jago Mampus | Gold |
| 1,000+ | 👑 Master | Gold |
| 100+ | 🏔️ Jago Banget | Forest Green |
| 50+ | 💪 Tryhard | Orange |
| 25+ | 🔥 Lumayan Jago | Orange Red |
| 10+ | 🗿 Pendaki Pemula | Tan |
| 0-9 | 🤡 Cupuh Banget | White |

## 🎯 Display Features

### Line 1: Role + Custom Title
- Shows role with colored brackets
- Displays custom title with animated colors
- Special owner rainbow effect

### Line 2: Name Display
- Premium icon (if applicable)
- Player DisplayName
- Animated verified checkmark (if applicable)

### Line 3: Rank + Summit
- Dynamic rank title with color
- Real-time summit count
- Auto-updates on value change

## 🔧 Advanced Settings

### Adjusting View Distance

```lua
mainGui.MaxDistance = 50  -- Default: 50 studs
-- Options: 35 (close), 50 (optimal), 100 (far), math.huge (infinite)
```

### Customizing Role Colors

```lua
local ROLE_BRACKET_COLORS = {
    Owner = Color3.fromRGB(255, 215, 0),      -- Gold
    Developer = Color3.fromRGB(0, 200, 255),  -- Cyan
    HeadAdmin = Color3.fromRGB(220, 20, 60),  -- Crimson
    Admin = Color3.fromRGB(50, 205, 50),      -- Lime Green
    Mod = Color3.fromRGB(255, 140, 0)         -- Dark Orange
}
```

### Adding New Roles

```lua
-- 1. Add to ROLES table
local ROLES = {
    YourNewRole = {
        ["Username1"] = true
    }
}

-- 2. Add emoji (optional)
local ROLE_EMOJI = {
    YourNewRole = "🎯"
}

-- 3. Add bracket color (optional)
local ROLE_BRACKET_COLORS = {
    YourNewRole = Color3.fromRGB(255, 0, 255)
}
```

## 📋 Requirements

- **Roblox Studio** or **Roblox Game**
- **LocalScript** placement (StarterPlayerScripts or StarterGui)
- **Leaderstats** with `Summit` IntValue for rank system

### Required Player Data Structure

```lua
Player
└── leaderstats (Folder)
    └── Summit (IntValue)
```

## 🐛 Troubleshooting

### Custom Title Not Showing?

1. ✅ Check username spelling (case-sensitive)
2. ✅ Ensure player is added to a ROLE
3. ✅ Add to CUSTOM_TITLES table
4. ✅ Add to CUSTOM_COLOR_TYPES table
5. ✅ Player must reset/respawn

### Display Not Appearing?

1. ✅ Verify script location (StarterPlayerScripts)
2. ✅ Check console for errors (F9)
3. ✅ Ensure leaderstats/Summit exists
4. ✅ Wait 5-10 seconds after spawn

### Colors Not Animating?

1. ✅ Check CUSTOM_COLOR_TYPES table
2. ✅ Verify color type name spelling
3. ✅ Ensure custom title exists

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 Changelog

### Version 2.2 (Current)
- ✅ Enhanced multi-user support for custom titles
- ✅ Expanded color animation options
- ✅ Improved verified user system
- ✅ Optimized display distance (50 studs)
- ✅ Separated owner rainbow effects
- ✅ Added 10+ example configurations

### Version 2.1
- ✅ Initial release with role system
- ✅ Dynamic rank progression
- ✅ Animated color effects
- ✅ Premium and verified support

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**ItoRenz00**

- Custom Roblox Display System
- Version 2.2 - Optimized & Enhanced

## 🌟 Support

If you find this helpful, please:
- ⭐ Star this repository
- 🐛 Report bugs via Issues
- 💡 Suggest features
- 🔄 Share with others

## 📞 Contact

For questions or support:
- Create an issue on GitHub
- Contact via Roblox: [[ItoRenz00](https://www.roblox.com/users/7976793837/profile)]
- Contact via Github: [[ItoRenz](https://github.com/ItoRenz))]

---

**Made with ❤️ for the Roblox Community**
