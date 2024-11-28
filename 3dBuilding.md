# 3D Building Configuration Guide

## Grid Specifications
- Grid Size: 8x8 cells
- Cell Size: 1 unit × 1 unit
- Base Height: 0.1 units (ground tile thickness)

## Building Dimensions
Each building occupies a single grid cell (1×1 unit) with varying heights:

### Resource Production Buildings
| Building Type        | Height (units) | Base Width | Base Depth | Resolution | Special Features |
|---------------------|----------------|------------|------------|------------|------------------|
| Power Plant         | 0.8           | 0.8        | 0.8        | 64×64     | Glowing elements |
| Iron Mine           | 0.6           | 0.8        | 0.8        | 64×64     | Excavator arm    |
| Factory            | 1.0           | 0.8        | 0.8        | 128×128   | Chimney stacks  |
| Worker Management  | 0.7           | 0.8        | 0.8        | 64×64     | Office windows   |
| Farm               | 0.4           | 0.8        | 0.8        | 64×64     | Greenhouse dome  |

### Special Buildings
| Building Type      | Height (units) | Base Width | Base Depth | Resolution | Special Features |
|-------------------|----------------|------------|------------|------------|------------------|
| Launch Pad        | 0.3           | 0.8        | 0.8        | 128×128   | Platform details |
| AI Research       | 0.9           | 0.8        | 0.8        | 128×128   | Antenna arrays   |
| Radar            | 1.2           | 0.8        | 0.8        | 128×128   | Rotating dish    |
| Rocket Storage   | 1.5           | 0.8        | 0.8        | 128×128   | Hangar doors     |

## Material Properties
- Base Material: MeshStandardMaterial
- Roughness: 0.7
- Metalness: 0.3

### Building-Specific Colors
| Building Type      | Color (Hex) | Description        |
|-------------------|-------------|-------------------|
| Power Plant       | #ffd700     | Golden yellow     |
| Iron Mine         | #cd853f     | Rustic brown      |
| Factory          | #4682b4     | Steel blue        |
| Worker Management | #9370db     | Soft purple       |
| Farm             | #32cd32     | Lime green        |
| Launch Pad       | #b22222     | Fire brick red    |
| AI Research      | #4169e1     | Royal blue        |
| Radar            | #708090     | Slate gray        |
| Rocket Storage   | #daa520     | Golden rod        |

## Grid Cell Properties
- Cell Border: 0.05 units thick
- Cell Color: #2a4858 (default)
- Selected Cell Color: #4a90e2
- Cell Spacing: None (cells are adjacent)

## Performance Optimization
- Use instanced meshes for repeated elements
- LOD (Level of Detail) settings:
  - Full detail: 0-10 units distance
  - Medium detail: 10-20 units distance
  - Low detail: >20 units distance
- Texture resolution requirements:
  - Basic buildings: 64×64
  - Complex buildings: 128×128
  - Normal maps: Same as diffuse textures
  - Metalness/Roughness maps: Half resolution of diffuse

## Shadow Configuration
- Cast Shadows: Enabled for all buildings
- Receive Shadows: Enabled for buildings and grid
- Shadow Map Size: 1024×1024
- Shadow Type: PCFSoft
- Shadow Bias: 0.0001

## Animation Guidelines
- Building Placement:
  - Scale from 0 to full size over 0.3 seconds
  - Slight bounce at end (elastic easing)
- Hover Effect:
  - Subtle height increase (0.1 units)
  - Gentle glow outline
- Selection:
  - Pulsing outline effect
  - Color shift to highlight state

## Optimization Requirements
- Maximum vertex count per building: 500
- Maximum triangle count per building: 200
- Texture memory budget per building: 256KB
- Total draw calls target: <100 for full grid