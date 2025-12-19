# 🧊 cub3D

<div align="center">

![42 Badge](https://img.shields.io/badge/42-Network-000000?style=for-the-badge&logo=42&logoColor=white)
![C](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
![MLX42](https://img.shields.io/badge/MLX42-Graphics-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

A 3D game engine inspired by **Wolfenstein 3D**, built using raycasting techniques in C.

</div>

---

## 📖 About

**cub3D** is a project from the 42 Network curriculum that introduces the fundamentals of raycasting — the same technique used in early 90s games like Wolfenstein 3D and Doom. The goal is to create a dynamic first-person view inside a maze, rendering a 3D world from a 2D map.

This project is split into:
- **Mandatory**: Core raycasting engine with textured walls
- **Bonus**: Advanced features like doors, sprites, minimap, and mouse controls

---

## ✨ Features

| Mandatory | Bonus |
|-----------|-------|
| ✅ Raycasting 3D rendering | 🖱️ Mouse camera rotation |
| ✅ Textured walls (N/S/E/W) | 🔫 Animated weapon sprite |
| ✅ Floor & ceiling colors | 🚪 Interactive doors |
| ✅ Smooth WASD movement | 🗺️ Real-time minimap |
| ✅ Map file parsing (.cub) | 💥 Wall collision detection |

---

## 🛠️ Installation

### Prerequisites

```bash
# macOS (Homebrew)
brew install glfw cmake

# Linux (Debian/Ubuntu)
sudo apt-get install libglfw3 libglfw3-dev cmake build-essential
```

### Build

```bash
git clone https://github.com/sel-hasn/Cub3D.git
cd Cub3D

# Compile mandatory version
make

# Compile bonus version
make bonus
```

### ⚠️ Platform Notes

The project automatically detects your OS and uses the appropriate compiler flags:

| Platform | Linker Flags |
|----------|--------------|
| **macOS** | `-framework Cocoa -framework OpenGL -framework IOKit -lglfw` |
| **Linux** | `-ldl -lglfw -pthread -lm` |

**If you encounter MLX42 linking errors on Linux**, you may need to recompile the library:

```bash
# Clone and build MLX42 for your platform
git clone https://github.com/codam-coding-college/MLX42.git MLX42_build
cd MLX42_build
cmake -B build
cmake --build build -j4
cp build/libmlx42.a ../MLX42/
cp include/MLX42/MLX42.h ../MLX42/.MLX42.h
cd .. && rm -rf MLX42_build
```

---

## 🚀 Usage

```bash
# Run mandatory version
./cub3D maps/map_manda.cub

# Run bonus version
./cub3D_bonus maps/map.cub
```

---

## 🎮 Controls

| Key | Action |
|-----|--------|
| `W` | Move forward |
| `S` | Move backward |
| `A` | Strafe left |
| `D` | Strafe right |
| `←` `→` | Rotate camera |
| `Mouse` | Rotate camera (bonus) |
| `Space` | Open/Close door (bonus) |
| `ESC` | Exit game |

---

## �️ Map Configuration

Maps use the `.cub` format:

```
NO ./textur/uchi1.png
SO ./textur/uchi2.png
WE ./textur/uchi3.png
EA ./textur/uchi4.png

F 220,100,0
C 135,206,235

111111
100001
1000N1
100001
111111
```

| Element | Description |
|---------|-------------|
| `NO/SO/WE/EA` | Wall textures (North/South/West/East) |
| `F` | Floor color (R,G,B) |
| `C` | Ceiling color (R,G,B) |
| `0` | Empty space |
| `1` | Wall |
| `N/S/E/W` | Player spawn (facing direction) |
| `D` | Door (bonus) |

---

## 📁 Project Structure

```
cub3D/
├── MANDATORY/          # Core implementation
│   ├── cub.c           # Main entry point
│   ├── cast_rays.c     # DDA raycasting algorithm
│   ├── draw_3d.c       # 3D wall rendering
│   ├── parsing/        # Map file parsing
│   └── UTILS/          # Helper functions
├── BONUS/              # Bonus features
│   ├── door_bonus.c    # Door mechanics
│   ├── sprit_bonus.c   # Weapon sprites
│   ├── drawed_bonus.c  # Minimap rendering
│   └── mouse_events_bonus.c
├── MLX42/              # Graphics library
├── textur/             # Wall textures
├── gun/                # Weapon animation frames
└── maps/               # Map files
```

---

## � Resources

### Raycasting & Mathematics
- [Lode's Raycasting Tutorial](https://lodev.org/cgtutor/raycasting.html) — Comprehensive guide to raycasting
- [Ray-Casting Tutorial by F. Permadi](https://permadi.com/1996/05/ray-casting-tutorial-table-of-contents/) — Step-by-step raycasting explanation
- [3DSage YouTube Tutorial](https://www.youtube.com/watch?v=gYRrGTC7GtA) — Visual raycasting implementation

### MLX42 Graphics Library
- [MLX42 GitHub Repository](https://github.com/codam-coding-college/MLX42) — Official documentation
- [MLX42 Wiki](https://github.com/codam-coding-college/MLX42/wiki) — Usage examples and API reference

### 42 Project Resources
- [42 Docs - cub3D](https://harm-smits.github.io/42docs/projects/cub3d) — Project overview and tips

### Mathematics
- [DDA Algorithm Explained](https://en.wikipedia.org/wiki/Digital_differential_analyzer_(graphics_algorithm)) — Line drawing algorithm used in raycasting
- [Understanding FOV](https://www.scratchapixel.com/lessons/3d-basic-rendering/ray-tracing-generating-camera-rays/generating-camera-rays) — Field of view calculations

---

## 🔧 Troubleshooting

| Issue | Solution |
|-------|----------|
| `OPEN_MAX undeclared` | Already fixed in headers. If not, add `#define OPEN_MAX 1024` in `cub.h` |
| `mlx_* undefined reference` | Recompile MLX42 for your platform (see Installation section) |
| `-framework` errors on Linux | Makefile auto-detects OS. Run `make re` to rebuild |
| `libglfw.so not found` | Install GLFW: `sudo apt-get install libglfw3 libglfw3-dev` |
| Window doesn't open | Ensure you have OpenGL drivers installed |

---

## 👥 Contributors

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/sel-hasn">
        <img src="https://github.com/sel-hasn.png" width="100px;" alt="sel-hasn"/><br />
        <sub><b>sel-hasn</b></sub>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/ezahiri10">
        <img src="https://github.com/ezahiri10.png" width="100px;" alt="ezahiri10"/><br />
        <sub><b>ezahiri10</b></sub>
      </a>
    </td>
  </tr>
</table>

---

<div align="center">

Made with ❤️ at **42 Network**

</div> 
