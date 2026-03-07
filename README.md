# BlenderMCP Forge

A fork of [BlenderMCP](https://github.com/ahujasid/blender-mcp) — reforged with Claude Code for autonomous 3D asset creation workflows.

## What's different from the original?

- **Telemetry completely removed** — no data sent anywhere, supabase dependency stripped
- **Bug fixes** — fixed broken URL validation, screenshot temp file collisions, temp file leaks, bare exception handling
- **Optimized for Claude Code** — not Claude Desktop, not Cursor — Claude Code

### Planned improvements
- Screenshot feedback loop for autonomous iterate-until-satisfied workflows
- Multi-angle viewport capture and camera control tools
- Export tools (GLTF/FBX/OBJ) for direct integration with game engines
- Expanded modeling tools (primitives, modifiers, booleans, batch operations)
- Material creation from scratch
- File system integration — export directly into your project's asset folder

## Features

- **Two-way communication**: Connect Claude AI to Blender through a socket-based server
- **Object manipulation**: Create, modify, and delete 3D objects in Blender
- **Material control**: Apply and modify materials and colors
- **Scene inspection**: Get detailed information about the current Blender scene
- **Code execution**: Run Python code in Blender from Claude
- **Viewport screenshots**: Capture the 3D viewport for visual feedback
- **Poly Haven integration**: Download models, textures, and HDRIs
- **Hyper3D Rodin**: Generate 3D models from text or images
- **Sketchfab**: Search and download models
- **Hunyuan3D**: AI-powered 3D model generation

## Components

1. **Blender Addon (`addon.py`)**: Socket server inside Blender that receives and executes commands
2. **MCP Server (`src/blender_mcp/server.py`)**: MCP bridge between Claude Code and the Blender addon

## Installation

### Prerequisites

- Blender 3.0 or newer
- Python 3.10 or newer
- [uv package manager](https://docs.astral.sh/uv/getting-started/installation/)

**Mac:**
```bash
brew install uv
```

**Windows:**
```powershell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```
Then add to PATH:
```powershell
$localBin = "$env:USERPROFILE\.local\bin"
$userPath = [Environment]::GetEnvironmentVariable("Path", "User")
[Environment]::SetEnvironmentVariable("Path", "$userPath;$localBin", "User")
```

### Claude Code Setup

```bash
claude mcp add blender -- uvx --from git+https://github.com/Jyhed/blender-mcp-forge blender-mcp
```

### Environment Variables

- `BLENDER_HOST`: Host address for Blender socket server (default: `localhost`)
- `BLENDER_PORT`: Port number for Blender socket server (default: `9876`)

### Installing the Blender Addon

1. Download `addon.py` from this repo
2. Open Blender
3. Go to Edit > Preferences > Add-ons
4. Click "Install..." and select the `addon.py` file
5. Enable the addon by checking the box next to "Interface: Blender MCP"

## Usage

1. In Blender, open the 3D View sidebar (press N)
2. Find the "BlenderMCP" tab
3. Enable Poly Haven / Hyper3D / Sketchfab if desired
4. Click "Connect to Claude"
5. Start prompting in Claude Code

### Example Commands

- "Create a low poly dungeon scene with a dragon guarding gold"
- "Make this car red and metallic"
- "Create a sphere and place it above the cube"
- "Set up studio lighting"
- "Point the camera at the scene, make it isometric"
- "Generate a 3D model of a garden gnome through Hyper3D"
- "Download a rock model from Poly Haven and texture it"

## Troubleshooting

- **Connection issues**: Make sure the Blender addon server is running before using Claude Code
- **Timeout errors**: Break complex requests into smaller steps
- **First command fails**: This is a known issue — subsequent commands should work

## Credits

Original project by [Siddharth Ahuja](https://github.com/ahujasid/blender-mcp). This fork is maintained by [Jyhed](https://github.com/Jyhed).
