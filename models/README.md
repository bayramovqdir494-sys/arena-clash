# Drop-in models

Combat does not raycast these meshes. Hits use the swing samples in `src/game/weapons.ts`. Replacing a file does not change when a blow lands.

Put self-contained `.glb` files here (textures packed inside the file). Missing files are ignored and the animated stand-ins stay.

| File | Slot |
| --- | --- |
| `player.glb` | Player rider |
| `enemy.glb` | Murmillo and eques rider |
| `boss.glb` | Titus |
| `horse.glb` | Mount |
| `chariot.glb` | Chariot |
| `sword.glb` | Sword, parented to the swinging mount |
| `flail.glb` | Flail handle, parented to the swinging mount |
| `spear.glb` | Spear / javelin, parented to the swinging mount |

## Weapons

Export with the grip at the origin and the blade along **+Z**. The game aims that mount from the hand toward the hit point every frame, so the mesh rides the real swing.

## Characters and horses

Files do not need a skeleton. An unrigged mesh is turned to face the rig (+Z forward, feet down, weapon grip at the hand), fitted to the stand-in, and skinned onto its bones, so the mesh walks, rides, swings, blocks, recoils, and falls with the animation that is already playing. Hits still use the weapon timing, not the mesh. A chariot without `wheelL` / `wheelR` nodes moves with the ram as one mesh.

Export with **+Y up, +Z forward**, and limbs hanging along **-Y**, in one piece or as separate meshes. A file that already contains at least six of the joint names below is driven from those nodes instead.

Joint names: `hips`, `torso`, `head`, `shoulderL`, `elbowL`, `handL`, `shoulderR`, `elbowR`, `handR`, `thighL`, `shinL`, `thighR`, `shinR`, `saddle`, `wheelL`, `wheelR`, `weaponTip`.

## If a file is missing

That slot keeps the procedural stand-in. The rest of the fight is unchanged.
