# Roblox Player Display & Stats System

A comprehensive Roblox game system featuring custom player overhead displays with roles, ranks, and a robust checkpoint-based progression system with DataStore persistence.

## 📦 Features

### PlayerDisplayClient
- **Custom Overhead Display**: Minimalist, clean player name tags with role badges
- **Role System**: Support for Owner, Developer, HeadAdmin, Admin, Mod, Cheater, and Helper roles
- **Animated Colors**: Multiple color animation types (rainbow, RGB pulses, galaxy effects, etc.)
- **Verified Users**: Custom checkmark badges with rainbow animation
- **Premium Integration**: Displays Roblox Premium icon
- **Rank System**: Dynamic rank titles based on summit count (from "Cupuh Banget" to "GOD")
- **Custom Titles**: Personalized titles for specific users

### StatsCore
- **Sequential Checkpoint System**: Anti-skip validation ensures players complete checkpoints in order
- **DataStore Persistence**: Automatic save/load of player progress
- **Summit Tracking**: Counts successful summit completions
- **Self-Healing Validation**: Prevents checkpoint skipping exploits
- **Auto-Respawn**: Teleports players to their last checkpoint on spawn
- **Flexible Folder Support**: Works with "CheckPoint", "Checkpoint", and custom summit folders
- **Touch Detection**: Robust touch detection with cooldown and debounce systems

## 🚀 Installation

### PlayerDisplayClient Setup
1. Copy `PlayerDisplayClient.lua`
2. Place in:
   - `StarterPlayer > StarterPlayerScripts` (recommended), or
   - `StarterGui`
3. Configure the settings at the top of the script

### StatsCore Setup
1. Copy `StatsCore.server.lua`
2. Place in `ServerScriptService`
3. Create folders in Workspace:
   - `CheckPoint` or `Checkpoint` (for checkpoint parts)
   - `Summit` (for summit/finish parts)
4. Name checkpoint parts sequentially: `CP_1`, `CP_2`, `Checkpoint 3`, etc.

## ⚙️ Configuration

### PlayerDisplayClient Configuration

```lua
-- Verified Users
local VerifiedUsersList = {
    ["Username"] = true,
}

-- Roles
local ROLES = {
    Owner = { ["username"] = true },
    Developer = { ["username"] = true },
    -- ... add more roles
}

-- Custom Titles
local CUSTOM_TITLES = {
    ["Username"] = "CEO",
}

-- Custom Colors
local CUSTOM_COLOR_TYPES = {
    ["Username"] = "rainbow",  -- Available: rainbow, pink_pulse, purple_galaxy, etc.
}
```

### StatsCore Configuration

```lua
local CONFIG = {
    SUMMIT_FOLDER_NAME = "Summit",          -- Summit parts folder name
    TOUCH_COOLDOWN_SEC = 0.8,               -- Cooldown between touches
    RESPAWN_TO_LAST_CP = true,              -- Enable checkpoint respawn
    TELEPORT_OFFSET = Vector3.new(0, 3, 0), -- Spawn offset from checkpoint
    DEBUG_LOG = RunService:IsStudio()       -- Debug mode (Studio only)
}
```

## 📊 Rank System

The system includes 20+ rank tiers based on summit count:

| Summit Count | Rank | Color |
|--------------|------|-------|
| 10000+ | 🌟 GOD | Gold |
| 8000+ | ⚡ Dewa | Purple |
| 6500+ | 🔥 Si Paling Pro | Red Orange |
| 5000+ | ❄️ Too EZ for me | Sky Blue |
| 4000+ | 🌪️ Juara | Steel Blue |
| 3500+ | 💎 Pendaki Elite | Light Cyan |
| 3000+ | 🏆 Jago Mampus | Gold |
| 2500+ | ⚔️ Legendaris | Orange |
| 2000+ | 🗡️ Udah Gila | Purple |
| 1800+ | 🌀 Mendaki Tanpa Henti | Indigo |
| 1600+ | 🔮 Master Summit | Medium Purple |
| 1400+ | ⭐ Pendaki Langit | Yellow |
| 1200+ | 🚀 Tak Terhentikan | Cyan |
| 1000+ | 👑 Master | Gold |
| 100+ | 🏔️ Jago Banget | Green |
| 50+ | 💪 Tryhard | Orange |
| 25+ | 🔥 Lumayan Jago | Red Orange |
| 10+ | 🗿 Pendaki Pemula | Tan |
| 0-9 | 🤡 Cupuh Banget | White |

## 🎨 Available Color Animations

- `rainbow` - Full spectrum color cycle
- `pink_pulse` - Pulsing pink gradient
- `purple_galaxy` - Galaxy purple transition (4-phase cycle)
- `owner_rainbow` - Smooth rainbow for owners
- `random_rgb_new_1` to `random_rgb_new_6` - Various RGB sine wave animations
- `random_rgb_1`, `random_rgb_2` - Classic RGB animations
- `blue_rgb` - Blue-dominant RGB cycle
- `red_rgb` - Red-dominant RGB cycle
- `black_random_rgb` - Dark RGB cycle with black base

## 🔧 How It Works

### Checkpoint System
1. Players must touch checkpoints **sequentially** (CP_1 → CP_2 → CP_3...)
2. Skipping checkpoints is automatically prevented
3. Progress is saved to DataStore automatically
4. On respawn, players teleport to their last checkpoint

### Summit System
1. Players must complete ALL checkpoints before touching the summit
2. Successful summit increments the summit counter
3. Checkpoint progress resets to 0 after summit
4. Summit count is displayed in the overhead display

### Display System
1. Displays role badge with emoji (if applicable)
2. Shows custom title with animated color (if configured)
3. Displays Premium icon (⭐) and verified checkmark (✓) with rainbow animation
4. Shows dynamic rank based on summit count
5. Updates in real-time as player progresses

## 📝 Leaderstats Structure

```
leaderstats (Folder)
├── Summit (IntValue) - Total summits completed
└── Checkpoint (IntValue) - Last checkpoint reached
```

## 🛡️ Anti-Exploit Features

- **Sequential Validation**: Players cannot skip checkpoints
- **Touch Cooldown**: Prevents rapid touch spam (0.8s default)
- **Debounce System**: Per-part touch tracking per player
- **Self-Healing Logic**: Automatically corrects invalid checkpoint values
- **Server-Side Authority**: All validation logic runs on the server
- **Checkpoint Clamping**: Automatically limits checkpoint value to maximum available

## 🐛 Debug Mode

Enable debug logging in Studio:
```lua
DEBUG_LOG = RunService:IsStudio()
```

Debug messages include:
- ✓/✗ Checkpoint validation results
- 🏆 Summit completion logs
- ↺ Player respawn notifications
- Player state synchronization
- Checkpoint clamping operations

## 📋 Requirements

- Roblox Studio
- DataStoreService enabled in game settings
- Properly configured checkpoint and summit parts in Workspace
- Parts must be `BasePart` instances (Part, MeshPart, UnionOperation, etc.)

## 🔄 Version History

- **v2.1** (PlayerDisplayClient) - Optimized & clean implementation with improved layout
- **v4** (StatsCore) - Sequential checkpoint system with self-healing and respawn support

## 👤 Author

**Custom by ItoRenz00**

## 📄 License

Free to use and modify for your Roblox games. Credit appreciated but not required.

## 🤝 Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.

## ⚠️ Important Notes

1. **DataStore Key**: Uses `SummitStore_V4` - change version suffix if migrating from older systems
2. **Folder Names**: Supports both "CheckPoint" and "Checkpoint" naming conventions
3. **Part Naming**: Checkpoints must include numbers in their name or parent name (e.g., `CP_1`, `Checkpoint 2`, `CP-3`)
4. **Performance**: Optimized for large player counts with debounce and cooldown systems
5. **Character Respawn**: Uses `HumanoidRootPart` touch detection as fallback for reliable checkpoint detection
6. **Coalescing**: Automatically merges duplicate leaderstats values on player join

## 🎯 Best Practices

1. **Checkpoint Naming**: Use consistent naming like `CP_1`, `CP_2`, etc.
2. **Part Size**: Make checkpoint parts large enough to be easily touched
3. **CanTouch Property**: Automatically enabled by the script
4. **Testing**: Test in Studio with debug mode enabled first
5. **DataStore**: Ensure API services are enabled in Game Settings

## 📞 Support

For issues or questions:
- Check the debug console in Studio (press F9)
- Verify folder and part naming conventions
- Ensure DataStoreService is enabled in game settings
- Check that parts have `CanTouch` enabled
- Verify checkpoint parts contain sequential numbers

## 🎮 Example Setup

```
Workspace/
├── CheckPoint/
│   ├── CP_1 (BasePart)
│   ├── CP_2 (BasePart)
│   ├── CP_3 (BasePart)
│   └── ... (more checkpoints)
└── Summit/
    └── SummitPart (BasePart)

ServerScriptService/
└── StatsCore.server.lua

StarterPlayer/
└── StarterPlayerScripts/
    └── PlayerDisplayClient.lua
```

## 🔍 Troubleshooting

**Problem**: Checkpoints not registering
- Ensure parts are named with numbers (CP_1, Checkpoint 2, etc.)
- Check that `CanTouch` is true on parts
- Verify parts are descendants of CheckPoint/Checkpoint folder

**Problem**: Players can skip checkpoints
- This should be impossible with the sequential system
- Check server console for validation messages
- Ensure only one StatsCore script is running

**Problem**: Progress not saving
- Enable DataStoreService in Game Settings > Security
- Check for DataStore errors in server console
- Verify game is published (DataStore requires published games)

**Problem**: Display not showing
- Ensure PlayerDisplayClient is in correct location
- Check for script errors in client console (F9)
- Verify leaderstats folder exists on player

---

**Made with ❤️ for the Roblox development community**
