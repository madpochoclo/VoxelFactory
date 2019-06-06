# Voxel Factory 📦 :factory: 

> Voxel Factory is a simple Godot C# library that allows you to create voxel mesh easily using cubes. It handles the meshing for you and optimize it. 



## Usage

VoxelFactory can be used for anything in your project that needs procedural meshing. If you have a way to feed it some data. Then it will create the mesh no problem. You could use the library to create some voxel Items like in minecraft from pngs. You could feed it some chunk data so it will create the chunk mesh for you. If you want to create a procedural landscape using this library, you will need to handle the generation and multi-threading yourself.



## Installation

You can install this library manually using the provided dll file or you can also install it by downloading the nuget package.



## Exemples

If you have an image that you would like to extrude in voxels, all you need is the path to your image.

```csharp
 var VoxelFactory = new VoxelFactory();
 Mesh = VoxelFactory.CreateMeshFromIMG("res://New Piskel.png");
```

You can also add voxels manually like so:

```csharp
var VoxelFactory = new VoxelFactory();

VoxelFactory.AddVoxel(0, 0, 0, new Color(1, 0, 0));
VoxelFactory.AddVoxel(0, 1, 0, new Color(0, 1, 0));
Mesh = VoxelFactory.CreateMesh();
```

If you have a sprite node that has a texture that you want to extrude. 

```csharp
 var VoxelFactory = new VoxelFactory();
 var mySpriteNode = (Sprite)GetNode("mySpriteNode");
 Mesh = VoxelFactory.CreateMeshFromSprite(mySpriteNode);
```



## Documentation

#### Propreties

| Type     | Name            |
| -------- | --------------- |
| Material | DefaultMaterial |
| float    | VoxelSize       |

#### Methods

| Return type | Name                 |
| ----------- | -------------------- |
| Mesh        | CreateMeshFromIMG    |
| Mesh        | CreateMeshFromSprite |
| Mesh        | CreateMesh           |
| void        | AddVoxel             |
| void        | AddVoxels            |

#### Propreties Descriptions

- Default Material

The default material used on the mesh. By default, only the `VertexColorUseAsAlbedo`is enabled. You can override this before create a mesh to use a custom material.

- VoxelSize 

The size of a voxel. Default is `1` unit.

#### Methods Descriptions

- `Mesh` CreateMeshFromIMG(`string` path)

This will create a mesh from an image specified as `path`. For each pixel in the image, a voxel with the same color will be created. If the pixel is fully transparent, no voxel will be created.

- `Mesh` CreateMeshFromSprite(`Sprite` node)

This will create a mesh from a Sprite node. It will use the sprite texture as an image.

- `void` CreateMesh() 

Create a `Mesh` from the current data in the VoxelFactory. Use this if you are adding Voxels manually.

- `void` AddVoxel(`int` x, `int` y , `int` z, `Color` color, [overwrite])
- `void` AddVoxel(`Vector3` position, `Color` color)

Add a voxel at a specified position with a color to the VoxelFactory dataset. You can either use a Vector3 for the position or specify them one by one. You can specify if you want to overwrite if a voxel already exists at the position specified

- `void` AddVoxels(Dictionary<`Vector3`, `Color`>, [overwrite])

Add a bunch of voxels all at once that are in a Dictionary with the position as the key, and the color as the value. You can specify if you want to overwrite if a voxel already exists at the position specified

- `void` ClearVoxels()

Clears the dataset in the VoxelFactory
