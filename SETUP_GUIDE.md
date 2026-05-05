# OpenWorlds Phase 1 Setup Guide

This guide will get you playing in **5 minutes**!

## Step 1: Prepare Your Scene

1. **Open Unity** with the OpenWorlds project
2. **Create a new scene** in `Assets/Scenes/`
   - Right-click in Project window → Create → Scene
   - Name it `MainGame`
3. **Save it** (Ctrl+S)

## Step 2: Set Up the Ground

1. In the **Hierarchy**, right-click → 3D Object → Plane
2. **Rename** it to `Ground`
3. **Set its scale:**
   - X: 100
   - Y: 1
   - Z: 100
4. **Create a Ground Layer:**
   - In Hierarchy, select Ground
   - In Inspector, Layer dropdown → Add Layer
   - Name it "Ground"
   - Assign it to the Ground object

## Step 3: Create the Player

1. Right-click in Hierarchy → 3D Object → Capsule
2. **Rename** to `Player`
3. **Set position:** Y = 1
4. **Add components:**
   - Add **Rigidbody** (Inspector → Add Component → Physics → Rigidbody)
   - Freeze Rotation (X, Y, Z) in Rigidbody
5. **Add First Person Camera:**
   - In Hierarchy under Player, create new empty object → Rename to `CameraHolder`
   - Set CameraHolder position: Y = 0.6
   - Drag the Main Camera under CameraHolder
   - Set Main Camera local position: (0, 0, 0)

## Step 4: Add Scripts to Player

1. **Select Player** in Hierarchy
2. **Add Component → Script** → Drag `FirstPersonController.cs` (from Assets/Scripts/Player/)
3. **Configure in Inspector:**
   - Ground Layer: Select "Ground"
   - Player Camera: Drag Main Camera into this field
4. **Add another Component** → Drag `BlockPlacer.cs`
5. **Configure in Inspector:**
   - Build Layer: "Default"
   - Placement Distance: 5
6. **Add another Component** → Drag `WorldSaveLoad.cs`

## Step 5: Create UI for Instructions

1. Right-click Hierarchy → UI → Legacy → Panel
   - This creates a Canvas with a Panel
2. **Delete the Panel** (we don't need it)
3. Right-click Canvas → UI → Legacy → Text
4. **Rename** to `InstructionsText`
5. **Set Position:** 
   - X: 0, Y: 0
   - Width: 300, Height: 400
   - Anchor: Top-Left
6. **Set Text to empty** (we'll fill it with code)
7. **Select Player** → In BlockPlacer component
   - Drag InstructionsText into the "Instructions Text" field

## Step 6: Test It!

1. **Make sure Ground has a Collider** (it should auto-add when you created the plane)
2. **Press Play** ▶️
3. **Test controls:**
   - WASD = Move
   - Mouse = Look around
   - Space = Jump
   - Left Click = Place block
   - Right Click = Delete block
   - Ctrl+S = Save
   - Ctrl+L = Load

## Troubleshooting

**Player falls through ground?**
- Make sure Ground has a BoxCollider component
- Ground Layer should be "Ground"
- Check FirstPersonController has Ground Layer assigned

**Can't place blocks?**
- Make sure Main Camera is set in BlockPlacer
- Check block size isn't 0

**Save doesn't work?**
- Check the Debug console (Window → General → Console)
- Save files are in: `C:\Users\[YourName]\AppData\LocalLow\DefaultCompany\OpenWorlds\Saves\`

## Next Steps

Once this works:
1. **Customize block colors** - Add different materials to BlockPlacer
2. **Add more block types** - Expand the inventory
3. **Set up backend** - We'll add multiplayer/sharing next!

---

**Questions?** Check the console for debug logs!
