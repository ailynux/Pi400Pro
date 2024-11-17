# RetroStation 400: Turn your Pi 400 into a Retro Gaming Command Center

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Platform: Raspberry Pi 400](https://img.shields.io/badge/Platform-Raspberry%20Pi%20400-red.svg)

## 🎮 Overview

Transform your Raspberry Pi 400 into a sleek retro gaming station that pays homage to classic computer keyboards of the 1980s. The RetroStation 400 project combines the compact form factor of the Pi 400 with custom software to create an all-in-one gaming system that boots directly into a customized gaming interface.

## ✨ Features

- **Quick Boot Gaming Mode**: Boot directly into the gaming interface
- **Keyboard Mapping**: Pre-configured keyboard controls optimized for the Pi 400's layout
- **LED Integration**: Custom scripts to control the Pi 400's power LED for game status
- **Multi-System Support**: 
  - Commodore 64
  - ZX Spectrum
  - NES
  - SNES
  - SEGA Master System
  - Game Boy/Game Boy Color
- **Smart Save States**: Quick save/load using keyboard shortcuts
- **CRT Shader Effects**: Optional scanline effects for authentic retro feel

## 🛠️ Installation

1. Flash the latest Raspberry Pi OS Lite to your SD card
2. Clone this repository:
```bash
git clone https://github.com/yourusername/retrostation400.git
cd retrostation400
```

3. Run the installation script:
```bash
chmod +x install.sh
./install.sh
```

## 🔧 Configuration

### Hardware Requirements
- Raspberry Pi 400
- MicroSD card (32GB+ recommended)
- USB gamepad (optional)
- External display via HDMI

### Default Keyboard Controls
| Action | Key |
|--------|-----|
| Start Game | Enter |
| Pause | Space |
| Quick Save | F5 |
| Quick Load | F7 |
| Exit Game | Esc |
| Player 1 Movement | Arrow Keys |
| Player 1 Action | Left Alt/Left Ctrl |
| System Menu | F1 |

## 📚 Usage

1. Power on your Pi 400
2. Select your gaming system from the main menu
3. Choose your game
4. Use the keyboard controls or connected gamepad to play

### Custom LED Patterns
- Solid: System Ready
- Slow Blink: Game Loading
- Fast Blink: Saving State
- Pulse: Game Running

## 🔄 Updates

The RetroStation 400 can be updated using:
```bash
./update.sh
```

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

## 🐛 Known Issues

- Some SNES games may experience slight input lag
- LED control requires root privileges
- Save states might not work with all games

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- RetroPie project for emulation foundations
- Pi 400 community for testing and feedback
- Various emulator developers

## 📞 Support

- Create an issue in this repository
- Join our Discord community
- Check the [FAQ](docs/FAQ.md)

---
Made with ❤️ for the Pi 400 Community
