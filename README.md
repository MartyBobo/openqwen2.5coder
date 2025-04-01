# 🐍 OpenQwen2.5Coder - Roguelike Snake Game

A modern roguelike Snake game with class progression and skill development systems, powered by the Qwen 2.5 Coder LLM through Ollama.

![Python](https://img.shields.io/badge/python-3.12-blue)
![Pygame](https://img.shields.io/badge/pygame-2.5.2-green)
![License](https://img.shields.io/badge/license-MIT-yellow)

## 📋 Overview

OpenQwen2.5Coder combines the classic Snake game with roguelike elements such as:

- Character class system with unique abilities
- Skill progression and talent trees
- Procedurally generated levels
- RPG-style attribute development
- Special abilities and power-ups
- Enemy encounters and boss battles

The game leverages the Qwen 2.5 Coder LLM for dynamic content generation and game logic enhancement through the Ollama API.

## 🎮 Gameplay Features

- **Multiple Character Classes**: Choose from Warrior, Mage, Rogue, and more
- **Skill Trees**: Unlock and upgrade abilities as you progress
- **Procedural Generation**: Different game maps and challenges every time
- **Progression System**: Level up your snake and unlock new abilities
- **Dynamic Difficulty**: Adaptive gameplay that changes based on player skill
- **Achievement System**: Complete special challenges for rewards

## 🛠️ Technical Stack

- **Python 3.12+**: Core programming language
- **Pygame**: Game development library for rendering and input handling
- **Ollama**: Local LLM serving platform
- **Qwen 2.5 Coder**: 14B parameter LLM for dynamic game content
- **Docker**: Containerization for easy deployment

## 🚀 Installation

### Requirements

- Python 3.12+
- Docker (for Ollama deployment)
- 8GB+ RAM for running the LLM
- NVIDIA GPU recommended for better performance

### Setup Instructions

1. Clone the repository:

```bash
git clone https://github.com/MartyBobo/openqwen2.5coder.git
cd openqwen2.5coder
```

2. Set up the Python environment:

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

3. Install Ollama and set up the Qwen 2.5 Coder model (see [COMMANDS.md](COMMANDS.md) for detailed instructions)

4. Start the game:

```bash
python main.py
```

## 🖥️ Docker Support

The game can be run entirely in Docker for easy deployment. See [COMMANDS.md](COMMANDS.md) for detailed Docker setup instructions.

## 🎯 How To Play

1. Select a character class at the start screen
2. Use arrow keys or WASD to navigate
3. Collect food to grow and gain experience points
4. Press space to activate your current ability
5. Press Tab to open the skill tree menu
6. Press ESC to pause the game

## ✨ Game Mechanics

### Classes and Skills

Each class has unique starting attributes and skill trees:

- **Warrior**: High health, melee-focused abilities
  - Skills: Dash, Shield Wall, Berserker Rage
  
- **Mage**: Special abilities, ranged attacks
  - Skills: Fireball, Teleport, Time Slow
  
- **Rogue**: Fast movement, stealth mechanics
  - Skills: Invisibility, Poison, Speed Burst

### Progression

- Gain XP by collecting food and defeating enemies
- Level up to increase your base attributes
- Spend skill points to unlock and upgrade abilities
- Find special items to enhance your snake's capabilities

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgements

- Powered by [Qwen 2.5 Coder](https://github.com/QwenLM/Qwen2) from Alibaba Cloud
- [Ollama](https://github.com/ollama/ollama) for local LLM deployment
- [OpenManus](https://github.com/mannaandpoem/OpenManus) for agent framework inspiration