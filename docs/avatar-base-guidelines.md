---
title: Avatar Base Guidelines
layout: default
---
CreatureTime developers must use this documentation as a guideline for our producing avatars.
# Workflow

> - All edits should be one directional.
> - All steps should only happen previously before their successor.
>   - Steps may be skipped for prototyping.

## Flow

| Step                                          | Notes                                                                                                                                                                                                         |
| :-------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ZBrush                                        | *We may use other high res modeling software.*                                                                                                                                                                |
| Multiresolution Modifier                      | *We MUST project any high res to a low res to allow the client to make edits or changes if they want without depending on other software. Any other sculpting or projection fixes may be done at this stage.* |
| [UV Unwrap](#uv-unwrap) & [Rigging](#rigging) | *[UV Unwrap](#uv-unwrap) and [Rigging](#rigging) can be done in parallel.*                                                                                                                                    |
| FBX Import, Shaders, Materials, Textures      | *Connect generated textures to materials and materials to the FBX.*                                                                                                                                           |

## UV Unwrap

| Step              | Notes                                                                                                                             |
| :---------------- | :-------------------------------------------------------------------------------------------------------------------------------- |
| UV Unwrap         | *UV unwrapping and rigging can be done in parallel.*                                                                              |
| Normal Baking     | *Normal baking for Substance Painter. This gives us more control over the normal baking when using the Multiresolution Modifier.* |
| Texture Baking    | *Sometimes we may bake textures out of Blender for usage further in the pipeline.*                                                |
| Substance Painter |                                                                                                                                   |

## Rigging

| Step            | Notes                            |
| :-------------- | :------------------------------- |
| Rigging         | *Set up the armature and bones.* |
| Weight Painting |                                  |

# Preparing for Release

## Blender File

> - The data names should match the object name in the Blender scene.
> * The *Blender File* should contain only the bare minimum for the package. 
> * Blender files should be saved with compression.
> * Images should be *packed* into the Blender file.
> * Anything unnecessary in the following should be removed from the distributed files:
>     * External file references  
>     * Third-party data (*RetopoFlow*’s text file, for example.)  
>     * Actions  
>     * Images  
>     * Meshes  
>     * Shape keys  
>     * Texts/Scripts  
>     * Worlds

> [!IMPORTANT]
> Should NOT require third-party plug-ins to open and modify. 

### Armatures

> - Naming should follow the following pattern: \[Prefix\]\[BoneName\]\[Suffix\].
> - Bones with multiple bones for length should have a suffix greater than 0: *\[Prefix\]\[BoneName\]\[BoneNumber\]*.
> - We may use the suffix *root* for animated bones like ears and tail to separate their physics and animations: *\[Prefix\]\[BoneName\]Root*.
> - Symmetrical bones should end with additional \_L for Left and \_R for Right.
> - We should NOT export automatic tip bones for the FBX. However, if we need tip bones, we should export them with the suffix Tip.

#### Humanoid Bones

##### Body

> [!CAUTION]
> Ignore Upper Chest. Weight Painting under the breasts variants without compensation.


> [!NOTE]
> Toes can be ignored. They are not necessary for the avatar unless there is a gain for assigning the toes for that specific avatar.

| Humanoid Bone | Armature Bone Name |
| :---- | :---- |
| Hips | Hips |
| Spine | Spine |
| Chest | Chest |
| Upper Chest | \- |
| Left Arm |  |
| Shoulder | Shoulder\_L |
| Upper Arm | Arm\_L |
| Lower Arm | ForeArm\_L |
| Hand | Hand\_L |
| Right Arm |  |
| Shoulder | Shoulder\_R |
| Upper Arm | Arm\_R |
| Lower Arm | ForeArm\_R |
| Hand | Hand\_R |
| Left Leg |  |
| Upper Leg | Leg\_L |
| Lower Leg | LowerLeg\_L |
| Foot | Foot\_L |
| Toes | Toes\_L |
| Right Leg |  |
| Upper Leg | Leg\_R |
| Lower Leg | LowerLeg\_R |
| Foot | Foot\_R |
| Toes | Toes\_R |

##### Head

> [!IMPORTANT]
> Do NOT use Jaw. The Jaw animations will be overridden by animations using humanoid avatars.

| Humanoid Bone | Armature Bone Name |
| :---- | :---- |
| Neck | Neck |
| Head | Head |
| Left Eye | Eye\_L |
| Right Eye | Eye\_R |
| Jaw | \- |

##### Left Hand

| Humanoid Bone | Armature Bone Name |
| :---- | :---- |
| Thumb |  |
| Thumb Proximal | Thumb1\_L |
| Thumb Intermediate | Thumb2\_L |
| Thumb Distal | Thumb3\_L |
| Index |  |
| Index Proximal | IndexFinger1\_L |
| Index Intermediate | IndexFinger2\_L |
| Index Distal | IndexFinger3\_L |
| Middle |  |
| Middle Proximal | MiddleFinger1\_L |
| Middle Intermediate | MiddleFinger2\_L |
| Middle Distal | MiddleFinger3\_L |
| Ring |  |
| Ring Proximal | RingFinger1\_L |
| Ring Intermediate | RingFinger2\_L |
| Ring Distal | RingFinger3\_L |
| Little |  |
| Little Proximal | PinkyFinger1\_L |
| Little Intermediate | PinkyFinger2\_L |
| Little Distal | PinkyFinger3\_L |

##### Right Hand

| Humanoid Bone | Armature Bone Name |
| :---- | :---- |
| Thumb |  |
| Thumb Proximal | Thumb1\_R |
| Thumb Intermediate | Thumb2\_R |
| Thumb Distal | Thumb3\_R |
| Index |  |
| Index Proximal | IndexFinger1\_R |
| Index Intermediate | IndexFinger2\_R |
| Index Distal | IndexFinger3\_R |
| Middle |  |
| Middle Proximal | MiddleFinger1\_R |
| Middle Intermediate | MiddleFinger2\_R |
| Middle Distal | MiddleFinger3\_R |
| Ring |  |
| Ring Proximal | RingFinger1\_R |
| Ring Intermediate | RingFinger2\_R |
| Ring Distal | RingFinger3\_R |
| Little |  |
| Little Proximal | PinkyFinger1\_R |
| Little Intermediate | PinkyFinger2\_R |
| Little Distal | PinkyFinger3\_R |

#### Miscellaneous Bones

| Humanoid Bone | Armature Bone Name |
| :---- | :---- |
| Jaw | Jaw |
| Tongue | Tongue |
| Tail | Tail |
| Left Ear | Ear\_L |
| Right Ear | Ear\_R |
### Meshes

> - Naming should follow the following pattern: *\[MeshName\]\_\[Variant\]*.
#### Shape Keys

> - Reuse face tracking shape keys as gesture expressions when face tracking is not added to the avatar.
> - VRChat visemes use the following naming convention: *vrc.v\_\[Viseme\]*.

> [!IMPORTANT]
> The Jaw and Tongue transforms are not done through shape keys. This restriction applies especially to Visemes and Unified Expressions. The transformations are done through the Animator in Unity using the VRChat Built-in Parameters.

| Shape Key | Notes |
| :---- | :---- |
| Basis |  |
| Substance | *If the mesh needs to be exploded for Substance.* |
| \=== Visemes \=== |  |
| vrc.v\_sil |  |
| vrc.v\_pp |  |
| vrc.v\_ff |  |
| vrc.v\_th |  |
| vrc.v\_dd |  |
| vrc.v\_kk |  |
| vrc.v\_ch |  |
| vrc.v\_ss |  |
| vrc.v\_nn |  |
| vrc.v\_rr |  |
| vrc.v\_aa |  |
| vrc.v\_ee |  |
| vrc.v\_ih |  |
| vrc.v\_oh |  |
| vrc.v\_ou |  |
| \=== Eye Look \=== |  |
| LookUp | *When eyes look up.* |
| LookDown | *When eyes look down.* |
| \=== Customization \=== |  |
| \[BodyPart\].\[Customization\] | *Allows customization to the mesh or avatar.* |
| \=== FT & Expressions \=== |  |
| \* | *Please refer to United Expressions.* |

### Export Settings

| Include |  |
| :---- | :---- |
| Limit to | Selected Objects |
| Object Types | Armature, Mesh |
| Custom Properties | False |

| Transform |  |
| :---- | :---- |
| Scale | 1.00 |
| FBX Units Scale | FBX Units Scale |
| Forward | \-Z Forward |
| Up | Y Up |
| Apply Unit | True |
| Use Space Transform | True |
| Apply Transform | True |

| Geometry |  |
| :---- | :---- |
| Smoothing | Face |
| Export Subdivision | False |
| Apply Modifiers | True |
| Loose Edges | False |
| Triangulate Faces | False |
| Tangent Space | True |
| Vertex Colors | None |
| Prioritize Active Color | False |

| Armature |  |
| :---- | :---- |
| Primary Bone Axis | Y Axis |
| Secondary Bone Axis | X Axis |
| Armature FBXNode Type | Null |
| Only Deform Bones | True |
| Add Leaf Bones | False |

| Bake Animation | True |
| :---- | :---- |
| Key All Bones | True |
| NLA Strips | True |
| All Actions | False |
| Force Start/End Keying | True |
| Sampling Rate | 1.00 |
| Simplify | 1.00 |

### Animations

> - Naming should follow the following pattern: *\[ActionName\]*.
> - We use the NLA Strips for exporting animations. Modify the actions until the action is finalized then add it to the NLA Strip.

> [!CAUTION]
> Ensure that the final animation in the NLA strip list is the export pose of the FBX. If it is not last in the list, the default pose in Unity will be what is the final animation.

## Substance File

> - Names for exported textures should follow the following pattern: *\[Mesh\]\_\[MapName\]\[Suffix\]\[UDIM\]*.
> - Substance files should have layers that are properly named and organized.
> - Texture Sets should be baked out at the same resolution as the exported files.
> - All textures should be exported as 8-bit unless otherwise stated.
>     - Normal maps should be exported as 16 bit.
>     - Emissive maps may be exported with 8-bit \+ dithering.

### Map Naming Convention

| Map Name | Map Name | Map Type |
| :---- | :---- | :---- |
| Base Color | BaseColor | RBG/RGBA |
| Ambient Occlusion | AmbientOcclusion | Grayscale |
| Emission | Emission | RBG |
| Metallic Smoothness | MetallicSmoothness | Composite |
| Metallic Smoothness Standard | MetallicSmoothness\_Standard | Composite |
| Normal | Normal | Normal |
| Global Mask | GlobalMask\[1-4\] | Composite |

> [!NOTE]
> Any maps not mentioned above should follow the same naming convention as above.

## Unity Package

> - Create a dedicated exportable scene within the project that contains everything for that package to properly export.
>   - Do NOT export the export scene.
> - The package should NOT contain any third-party files when exporting.

### Package Structure

> - Other directories within *CreatureTime/Avatars/\[ProjectName\]*:
> - These directories are followed in most cases. If the directory is not mentioned, try to follow a similar convention.

| Directory   | Description                                                                                                                                                                      |
| :---------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Accessories | May or may not come with the avatar bases, but will be used when accessories are created for the avatar base.                                                                    |
| Animations  | Contains the FX animation controller(s) and animations. May contain subdirectories for organization.                                                                             |
| Extensions  | Some projects have extensions that can be placed on the avatar using *VRCFury*.                                                                                                  |
| Materials   | Contains the materials associated with the project. Comes with standard and Poiyomi shaders by default. *Package should not come with Poiyomi shaders.*                          |
| Models      | Contains the FBXs or other 3D asset supported file types.                                                                                                                        |
| Prefabs     | Contains prefabs associated with the project.                                                                                                                                    |
| Scenes      | Any scenes associated with the project. Avatar base projects should contain a file to help beginners using the following naming convention: \[PackageName\] (Start Here\!).unity |
| Scripts     | Prefabs that contain preset settings that are re-used within the project. Ears and toes, for example, since they use the same settings.                                          |
| Textures    | Preset of textures for the project.                                                                                                                                              |
| Variants    | May or may not come with the avatar bases, but contains any variants of the avatar base. For example, the Customization Variant used for the public version of the avatar.       |
| VRChat      | VRChat specific assets such as Menus and Parameters.                                                                                                                             |

### Textures

#### Texture Import Setting for All Textures

| Setting          | Value  |
| :--------------- | :----- |
| Mip Streaming    | True   |
| Mipmap Filtering | Kaiser |

#### Texture Import Setting by Map Type

| Map Type | Texture Type | sRGB | Alpha Source | Alpha is Transparency |
| :---- | :---- | :---- | :---- | :---- |
| RGB | Default | True | None | \- |
| RGBA | Default | True | Input Texture Alpha | True |
| Grayscale | Default | False | None | \- |
| Composite | Default | False | Input Texture Alpha | False |
| Normal | Normal map | \- | \- | \- |

> [!IMPORTANT]
> Normal Maps should use the override and set to *RG Compressed BC5*.


> [!CAUTION]
> Do not use texture compression unless you absolutely have to since this may cause hitches when people are loading the avatar in VRChat.

### Materials

> - Naming should follow the following pattern: *\[ModelFileName\]-\[MaterialName\].* Allows for FBX Import to auto-map using *On Demand Remap* feature.

### FBX Import

> - Naming should follow the following pattern: \[ProjectName\]\_\[Variant\].

#### Model

| Setting | Value |
| :---- | :---- |
| Read/Write | True |
| Legacy Blend Shape Normals | False (Ignore VRChat’s auto-fix for this.) |
| Normals | Import |
| Blend Shape Normals | Import |
| Smoothing Angle | 180 |

#### Rig

| Setting | Value |
| :---- | :---- |
| Animation Type | Humanoid |

> [!NOTE]
> Please refer to [Armature Naming Convention](#armatures) for bone mapping in case Unity fails to properly assign bones.

#### Animation

> - Animation names should follow the Action naming convention from the FBX: *\[ActionName\]*.
> - When there are multiple animations exported from a single animation from the FBX, the animation name may have the sub animation context added to the name: *\[ActionName\]\_\[SubAnimation\]*.
> - Masks may be used to generate masked animations.
> - Transformation animations should be cleaned up if they have sub properties are not being used. Scale or Position, for example.

#### Materials

| Setting | Value |
| :---- | :---- |
| Material Creation Mode | Import via Material Description |
| On Demand Remap \- Naming | Model Name \+ Model’s Material |
| On Demand Remap \- Search | Recursive-Up |

# Release

## Naming Convention

| Extension/File            | Required Name                                                           |
| :------------------------ | :---------------------------------------------------------------------- |
| UnityPackage              | *\[ProjectName\]-\[Version\].unitypackage*                              |
| Blender                   | *\[ProjectName\]-\[Version\]-Blender.zip*                               |
| \[ProjectName\].blend     | The Blender file.                                                       |
| BlenderExportSettings.png | The export settings used in Blender for the \[ProjectName\].blend file. |
| Substance                 | *\[ProjectName\]-\[Version\]-Substance.zip*                             |
| \[ProjectName\].spp       | The Substance Painter file.                                             |
| Unzipped                  | *\[ProjectName\]-\[Version\]-\[WhatIsIt\]\[Extension\]*                 |

## Handling Versions

Released file structure should follow the following:
- Release
	- *\[ProjectName\]-1.0.0-ChangeLog.md*
	- 1.0.0: Initial release.
		- *\[ProjectName\]-1.0.0.unitypackage*
		- *\[ProjectName\]-1.0.0-Blender.zip*
		- *\[ProjectName\]-1.0.0-Substance.zip*
	- 1.0.1: Blender file was updated and everything down the pipeline was updated with the changes.
		- *\[ProjectName\]-1.0.1.unitypackage*
		- *\[ProjectName\]-1.0.1-Blender.zip*
		- *\[ProjectName\]-1.0.1-Substance.zip*
	- 1.0.2: Only a Unity issue was found and fixed.
		- *\[ProjectName\]-1.1.1.unitypackage*
	- 1.1.0: A change was made that means we need to bump the minor version.
		- *\[ProjectName\]-1.1.0.unitypackage*
		- *\[ProjectName\]-1.1.0-Blender.zip*
		- *\[ProjectName\]-1.1.0-Substance.zip*
	- 1.1.1: Change in the Substance file were exported and updated the textures in the Unity project.
		- *\[ProjectName\]-1.1.1.unitypackage*
		- *\[ProjectName\]-1.1.1-Substance.zip*
	- 1.1.2: Another simple Unity issue was found and fixed.
		- *\[ProjectName\]-1.1.2.unitypackage*

> [!NOTE]
> It is okay to have the published release files to be a version behind only if there were no changes to them to bump the version. For example:
> 	- *\[ProjectName\]-1.1.2.unitypackage*
> 	- *\[ProjectName\]-1.1.0-Blender.zip*
> 	- *\[ProjectName\]-1.1.1-Substance.zip*

# Project Structure

> - The root of the project is also the root of the Unity project.


> [!WARNING]
> Due to LFS not sufficient for large source files, .Source files and large content file types are ignored (including their backup files). Currently, committed into a private Google Drive, but need to find a better solution.

Only need to commit the following directories into version control.

- *\[ProjectName\]*
	- Assets/CreatureTime/Avatars/*\[AvatarName\]*
		- Models/.Source
			- *\[AvatarName\]*.blend (Blender)
			- *\[AvatarName\]*.spp (Substance Painter)
		- *Others mentioned in [Package Structure](#package-structure)*
	- .gitignore
