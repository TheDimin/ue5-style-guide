## Overview
<a name="0.1"></a>
### We have a style guide, try to abide by  it.
* If a rule doesn't work for us, we can change it.
* This guide is a revision of https://github.com/Allar/ue5-style-guide
 ** If you wonder why a rule is the way it is, check that document.
 
<a name="0.2"></a>
### The project should look like a single person created it.

<a name="0.3"></a>
### If you see someone working either against the style guide, try to correct them.
* It is easier to help and ask for help when people are consistent.

<a name="0.4"></a>
### Department specific items are marked accordingly
* `DP` `VA` `PR`

<a name="0.5"></a>
<a name="identifiers"></a>
### Any `Identifier` should strive to only have the following characters when possible
* ABCDEFGHIJKLMNOPQRSTUVWXYZ
* abcdefghijklmnopqrstuvwxyz
* 1234567890

<a name="1"></a>

## Table of contents
- [1. Asset Naming Conventions](#anc)
- [2. Content Directory Structure](#structure)
- [3. Blueprints `PR` `DP`](#bp)
  - [3.1 Compiling](#bp-compiling)
  - [3.2 Variables](#bp-vars)
  - [3.3 Functions, Events, and Event Dispatchers](#bp-functions)
  - [3.4 Blueprint Graphs](#bp-graphs)
- [4. Static Meshes `VA`](#4)
  - [4.1 Static Mesh UVs](#s-uvs)
  - [4.2 LODs Should Be Set Up Correctly](#s-lods)
  - [4.3 Modular Socketless Assets Should Snap To The Grid Cleanly](#s-modular-snapping)
  - [4.4 All Meshes Must Have Collision](#s-collision)
  - [4.5 All Meshes Should Be Scaled Correctly](#s-scaled)
- [5. Niagara](#Niagara)
  - [5.1 No Spaces, Ever](#ng-rules)
- [6. Levels / Maps](#levels)
  - [6.1 No Errors Or Warnings](#levels-no-errors-or-warnings)
  - [6.2 Lighting Should Be Built](#levels-lighting-should-be-built)
  - [6.3 No Player Visible Z Fighting](#levels-no-visible-z-fighting)
- [7. Textures `VA`](#textures)
  - [7.1 Dimensions Are Powers of 2](#textures-dimensions)
  - [7.2 Texture Density Should Be Uniform](#textures-density)
  - [7.3 Textures Should Be No Bigger than 8192](#textures-max-size)
  - [7.4 Textures Should Be Grouped Correctly](#textures-group)

<a name="anc"></a>
<a name="1.0"></a>
## 1. Asset Naming Conventions
Naming conventions should be treated as law.

<a name="base-asset-name"></a>
<a name="1.1"></a>
### 1.1 All assets should have a _Base Asset Name_. 
* Any asset that is part of this logical group should follow the standard of  `Prefix_BaseAssetName_Variant_Suffix`.
* `Prefix` and `Suffix` are to be determined by the asset type through the following [Asset Name Modifier](#asset-name-modifiers) tables.

`BaseAssetName` should be determined by a short and easily recognizable name related to the context of this group of assets.

`Variant` is either a short and easily recognizable name that represents logical grouping of assets that are a subset of an asset's base name.
* For unique and specific variations of assets, use an descriptive word. for example a `Rat` with green skin becomes `Rat_Green`
* For unique but generic variations of assets, use two digit number starting at `01`. As example, `Rock_01`, `Rock_02`, `Rock_03`
* You can chain Variant names togheter As example, `Rock_Green_01`

<a name="1.1-examples"></a>
#### 1.1 Examples
##### 1.1e1 Rocks

| Asset Type              | Asset Name                                                 |
| ----------------------- | ---------------------------------------------------------- |
| Static Mesh (01)        | SM_Rock_01                                                  |
| Static Mesh (02)        | SM_Rock_02                                                  |
| Static Mesh (03)        | SM_Rock_03                                                  |
| Material                | M_Rock                                                     |
| Material Instance (Snow)| MI_Rock_Snow                                               |

<a name="asset-name-modifiers"></a>
<a name="1.2"></a>
### 1.2 Asset Name Modifiers
When naming an asset, use these tables to determine the prefix and suffix to use with an asset's [Base Asset Name](#base-asset-name).

<a name="anc-common"></a>
<a name="1.2.1"></a>
#### 1.2.1 Most Common

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Level / Map             |            |            | [Should be in a folder called Maps.](#2.4) |
| Blueprint               | BP_        |            |                                  |
| Material                | M_         |            |                                  |
| Static Mesh             | SM_        |            |                                  |
| Skeletal Mesh           | SK_        |            |                                  |
| Texture                 | T_         | _?         | See [Textures](#anc-textures)    |
| Particle System         | PS_        |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-animations"></a>
<a name="1.2.2"></a>
#### 1.2.2 Animations

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Aim Offset              | AO_        |            |                                  |
| Aim Offset 1D           | AO_        |            |                                  |
| Animation Blueprint     | ABP_       |            |                                  |
| Animation Composite     | AC_        |            |                                  |
| Animation Montage       | AM_        |            |                                  |
| Animation Sequence      | A_         |            |                                  |
| Blend Space             | BS_        |            |                                  |
| Blend Space 1D          | BS_        |            |                                  |
| Level Sequence          | LS_        |            |                                  |
| Morph Target            | MT_        |            |                                  |
| Paper Flipbook          | PFB_       |            |                                  |
| Rig                     | Rig_       |            |                                  |
| Skeletal Mesh           | SK_        |            |                                  |
| Skeleton                | SKEL_      |            |                                  |

<a name="anc-ai"></a>
<a name="1.2.3"></a>
### 1.2.3 Artificial Intelligence

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| AI Controller           | AIC_       |            |                                  |
| Behavior Tree           | BT_        |            |                                  |
| Blackboard              | BB_        |            |                                  |
| Decorator               | BTDecorator_ |          |                                  |
| Service                 | BTService_ |            |                                  |
| Task                    | BTTask_    |            |                                  |
| Environment Query       | EQS_       |            |                                  |
| EnvQueryContext         | EQS_       | Context    |                                  |

<a name="anc-bp"></a>
<a name="1.2.4"></a>
### 1.2.4 Blueprints

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Blueprint               | BP_        |            |                                  |
| Blueprint Component     | BP_        | Component  | I.e. BP_InventoryComponent       |
| Blueprint Function Library | BPFL_   |            |                                  |
| Blueprint Interface     | BPI_       |            |                                  |
| Blueprint Macro Library | BPML_      |            | Do not use macro libraries if possible. |
| Enumeration             | E          |            | No underscore.                   |
| Structure               | F or S     |            | No underscore.                   |
| Tutorial Blueprint      | TBP_       |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-materials"></a>
<a name="1.2.5"></a>
### 1.2.5 Materials

| Asset Type                    | Prefix     | Suffix     | Notes                            |
| ----------------------------- | ---------- | ---------- | -------------------------------- |
| Material                      | M_         |            |                                  |
| Material (Post Process)       | PP_        |            |                                  |
| Material Function             | MF_        |            |                                  |
| Material Instance             | MI_        |            |                                  |
| Material Parameter Collection | MPC_       |            |                                  |
| Subsurface Profile            | SP_        |            |                                  |
| Physical Materials            | PM_        |            |                                  |
| Decal                         | M_, MI_    | _Decal     |                                  |

<a name="anc-textures"></a>
<a name="1.2.6"></a>
### 1.2.6 Textures

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Texture                 | T_         |            |                                  |
| Texture (Diffuse/Albedo/Base Color)| T_ | _D      |                                  |
| Texture (Normal)        | T_         | _N         |                                  |
| Texture (Roughness)     | T_         | _R         |                                  |
| Texture (Alpha/Opacity) | T_         | _A         |                                  |
| Texture (Ambient Occlusion) | T_     | _O         |                                  |
| Texture (Bump)          | T_         | _B         |                                  |
| Texture (Emissive)      | T_         | _E         |                                  |
| Texture (Mask)          | T_         | _M         |                                  |
| Texture (Specular)      | T_         | _S         |                                  |
| Texture (Metallic)      | T_         | _M         |                                  |
| Texture (Packed)        | T_         | _*         | See notes below about [packing](#anc-textures-packing). |
| Texture Cube            | TC_        |            |                                  |
| Media Texture           | MT_        |            |                                  |
| Render Target           | RT_        |            |                                  |
| Cube Render Target      | RTC_       |            |                                  |
| Texture Light Profile   | TLP        |            |                                  |

<a name="anc-textures-packing"></a>
<a name="1.2.6.1"></a>
#### 1.2.6.1 Texture Packing
It is common practice to pack multiple layers of texture into one texture. An example of this is packing Emissive, Roughness, Ambient Occlusion together as the Red, Green, and Blue channels of a texture respectively. To determine the suffix, simply stack the given suffix letters from above together, e.g. `_ERO`.

Packing 4 channels of data into a texture (RGBA) is not recommended except for an Alpha/Opacity mask in the Diffuse/Albedo's alpha channel as a texture with an alpha channel incurs more overhead than one without.

<a name="anc-misc"></a>
<a name="1.2.7"></a>
### 1.2.7 Miscellaneous

| Asset Type                 | Prefix     | Suffix     | Notes                            |
| -------------------------- | ---------- | ---------- | -------------------------------- |
| Animated Vector Field      | VFA_       |            |                                  |
| Camera Anim                | CA_        |            |                                  |
| Color Curve                | Curve_     | _Color     |                                  |
| Curve Table                | Curve_     | _Table     |                                  |
| Data Asset                 | *_         |            | Prefix should be based on class. |
| Data Table                 | DT_        |            |                                  |
| Float Curve                | Curve_     | _Float     |                                  |
| Foliage Type               | FT_        |            |                                  |
| Force Feedback Effect      | FFE_       |            |                                  |
| Landscape Grass Type       | LG_        |            |                                  |
| Landscape Layer            | LL_        |            |                                  |
| Matinee Data               | Matinee_   |            |                                  |
| Media Player               | MP_        |            |                                  |
| File Media Source          | FMS_       |            |                                  |
| Object Library             | OL_        |            |                                  |
| Redirector                 |            |            | These should be fixed up ASAP.   |
| Sprite Sheet               | SS_        |            |                                  |
| Static Vector Field        | VF_        |            |                                  |
| Substance Graph Instance   | SGI_       |            |                                  |
| Substance Instance Factory | SIF_       |            |                                  |
| Touch Interface Setup      | TI_        |            |                                  |
| Vector Curve               | Curve_     | _Vector    |                                  |

<a name="anc-physics"></a>
<a name="1.2.9"></a>
### 1.2.9 Physics

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Physical Material       | PM_        |            |                                  |
| Physics Asset           | PHYS_      |            |                                  |
| Destructible Mesh       | DM_        |            |                                  |

<a name="anc-sounds"></a>
<a name="1.2.10"></a>
### 1.2.10 Sounds

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Dialogue Voice          | DV_        |            |                                  |
| Dialogue Wave           | DW_        |            |                                  |
| Media Sound Wave        | MSW_       |            |                                  |
| Reverb Effect           | Reverb_    |            |                                  |
| Sound Attenuation       | ATT_       |            |                                  |
| Sound Class             |            |            | No prefix/suffix. Should be put in a folder called SoundClasses |
| Sound Concurrency       |            | _SC        | Should be named after a SoundClass |
| Sound Cue               | A_         | _Cue       |                                  |
| Sound Mix               | Mix_       |            |                                  |
| Sound Wave              | A_         |            |                                  |

<a name="anc-ui"></a>
<a name="1.2.11"></a>
### 1.2.11 User Interface

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Font                    | Font_      |            |                                  |
| Slate Brush             | Brush_     |            |                                  |
| Slate Widget Style      | Style_     |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-effects"></a>
<a name="1.2.12"></a>
### 1.2.12 Effects

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Particle System         | PS_        |            |                                  |
| Material (Post Process) | PP_        |            |                                  |

**[⬆ Back to Top](#table-of-contents)**

<a name="2"></a>
<a name="structure"></a>
## 2. Content Directory Structure
The directory structure style of a project should be considered law. 
* Asset naming conventions and content directory structure go hand in hand, and a violation of either causes unneeded chaos.

> If you are using the prefix [naming convention](#1.2) above, using folders to contain assets of similar types such as `Meshes`, `Textures`, and `Materials` is a redundant practice as asset types are already both sorted by prefix as well as able to be filtered in the content browser.

<a name="2e1"><a>
### 2e1 Example Project Content Structure
<pre>
|-- Content
    |-- <a href="#2.2">GenericShooter</a>
        |-- Art
        |   |-- Industrial
        |   |   |-- Ambient
        |   |   |-- Machinery
        |   |   |-- Pipes
        |   |-- Nature
        |   |   |-- Ambient
        |   |   |-- Foliage
        |   |   |-- Rocks
        |   |   |-- Trees
        |   |-- Office
        |-- Characters
        |   |-- Bob
        |   |-- Common
        |   |   |-- <a href="#2.7">Animations</a>
        |   |   |-- Audio
        |   |-- Jack
        |   |-- Steve
        |   |-- <a href="#2.1.3">Zoe</a>
        |-- <a href="#2.5">Core</a>
        |   |-- Characters
        |   |-- Engine
        |   |-- <a href="#2.1.2">GameModes</a>
        |   |-- Interactables
        |   |-- Pickups
        |   |-- Weapons
        |-- Effects
        |   |-- Electrical
        |   |-- Fire
        |   |-- Weather
        |-- <a href="#2.4">Maps</a>
        |   |-- Campaign1
        |   |-- Campaign2
        |-- <a href="#2.8">MaterialLibrary</a>
        |   |-- Debug
        |   |-- Metal
        |   |-- Paint
        |   |-- Utility
        |   |-- Weathering
        |-- Placeables
        |   |-- Pickups
        |-- Weapons
            |-- Common
            |-- Pistols
            |   |-- DesertEagle
            |   |-- RocketPistol
            |-- Rifles
</pre>

The reasons for this structure are listed in the following sub-sections.

<a name="2.1"></a>
<a name="structure-folder-names"><a>
### 2.1 Folder Names
These are common rules for naming any folder in the content structure.

<a name="2.1.1"></a>
#### 2.1.1 Always Use PascalCase

<a name="2.1.2"></a>
#### 2.1.2 Never Use Spaces

<a name="2.1.3"></a>
#### 2.1.3 only Use allowed specifiers.
* `a-z`, `A-Z`, `1-9`

<a name="2.2"></a>
<a name="structure-top-level"><a>
### 2.2 All project assets should exist under `Content/RodentInSubmarine`

<a name="2.2.1"></a>
#### 2.2.1 No Global Assets
* Every asset should have a purpose otherwise it does not belong in a project. 

<a name="2.3"></a>
<a name="structure-developers"></a>
### 2.3 Use Developers Folder For Local Testing

<a name="2.4"></a>
<a name="structure-maps"></a>
### 2.4 All Map[<sup>*</sup>](#terms-level-map) Files Belong In A Folder Called Maps

<a name="2.5"></a>
<a name="structure-core"></a>
### 2.5 Use A `Core` Folder For Critical Blueprints And Other Assets

<a name="2.6"></a>
<a name="structure-assettypes"></a>
### 2.6 Do Not Create Folders Called `Assets` or `AssetTypes`

<a name="2.6.1"></a>
#### 2.6.1 Creating a folder named `Assets` is redundant
All assets are assets.

<a name="2.6.2"></a>
#### 2.6.2 Creating a folder named `Meshes`, `Textures`, or `Materials` is redundant
* Want to view only static mesh in `Environment/Rocks/`? Simply turn on the Static Mesh filter.
Not doing this also prevents the inevitability of someone putting a static mesh or a texture in a `Materials` folder.

<a name="2.7"></a>
<a name="structure-large-sets"></a>
### 2.7 Very Large Asset Sets Get Their Own Folder Layout
* This can be seen as a pseudo-exception to [2.6](#2.6).
  
There are certain asset types that have a huge volume of related files where each asset has a unique purpose. The two most common are Animation and Audio assets. If you find yourself having 15+ of these assets that belong together, they should be together.

For example, animations that are shared across multiple characters should lay in `Characters/Common/Animations` and may have sub-folders such as `Locomotion` or `Cinematic`.

> This does not apply to assets like textures and materials.

**[⬆ Back to Top](#table-of-contents)**

<a name="3"></a>
<a name="bp"></a>
## 3. Blueprints (PR AND DP)

This section will focus on Blueprint classes and their internals. When possible, style rules conform to [Epic's Coding Standard](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard).

Remember: Blueprinting badly bears blunders, beware! (Phrase by [KorkuVeren](http://github.com/KorkuVeren))

<a name="3.1"></a>
<a name="bp-compiling"></a>
### 3.1 Compiling
* Blueprints should compile with zero warning and zero errors.
** Fix them asap
** Fix them before asking for help (Unless you don't know how to solve the warnings/errors)
  
## DO NOT STORE BROKEN BLUEPRINTS IN SOURCE CONTROL
  * Shelve them instead.

<a name="3.2"></a>
<a name="bp-vars"></a>
### 3.2 Variables

The words `variable` and `property` may be used interchangeably.

<a name="3.2.1"></a>
<a name="bp-var-naming"></a>
#### 3.2.1 Naming

<a name="3.2.1.1"></a>
<a name="bp-var-naming-nouns"></a>
##### 3.2.1.1 All variable names must be clear, unambiguous, descriptive nouns, and use PascalCasing

<a name="3.2.1.5"></a>
<a name="bp-vars-naming-context"></a>
##### 3.2.1.5 All variable names must not be redundant with their context
* Examples for variables inside `BP_PlayerCharacter` **BAD** `PlayerScore`,`PlayerKills` **GOOD* `Score`,`Kills`

<a name="3.2.1.8"></a>
<a name="bp-vars-naming-arrays"></a>
##### 3.2.1.8 Arrays
* Arrays follow the same naming rules as above, but should be named as a plural noun.
* Example: Use `Targets`, `Hats`, and `EnemyPlayers`, **not** `TargetList`, `HatArray`, `EnemyPlayerArray`.


<a name="3.2.2"></a>
<a name="bp-vars-editable"></a>
#### 3.2.2 Do not arbitrarily mark variables as `Editable`.


<a name="3.2.2.1"></a>
<a name="bp-vars-editable-tooltips"></a>
##### 3.2.2.1 All `Editable` variables should have a description in their `Tooltip`

<a name="3.2.2.2"></a>
<a name="bp-vars-editable-ranges"></a>
##### 3.2.2.2 All `Editable` variables should make use of an slider range
  * Only use value range if the bounds of the value are known

<a name="3.2.3"></a>
<a name="bp-vars-categories"></a>
#### 3.2.3 Categories
* If a class has only a small number of variables, categories are not required.
* If a class has a moderate amount of variables (5+), all `Editable` variables should have a non-default category assigned.
  
> You can define sub-categories by using the pipe character `|`, i.e. `Config | Animations`.

<a name="3.2.4"></a>
<a name="bp-vars-access"></a>
#### 3.2.4 Treat `Editable` variables as public variables. Treat non-editable variables as protected variables.


<a name="3.2.5"></a>
<a name="bp-vars-advanced"></a>
#### 3.2.5 If a variable should be editable but often untouched, mark it as `Advanced Display`

<a name="3.2.6"></a>
<a name="bp-vars-transient"></a>
#### 3.2.6.2 Transient variables should always be initialized as zero or null

<a name="3.2.7"></a>
<a name="bp-vars-config"></a>
#### 3.2.8 Do not use the `Config Variable` flag

<a name="3.3"></a>
<a name="bp-functions"></a>
### 3.3 Functions, Events, and Event Dispatchers

<a name="3.3.1"></a>
<a name="bp-funcs-naming"></a>
#### 3.3.1 Function Naming

<a name="3.3.1.1"></a>
<a name="bp-funcs-naming-verbs"></a>
#### 3.3.1.1 All Functions start with Verbs
* They should be worded in the present tense whenever possible. 
* They should have context as to what they are doing.
  
Good examples:
* `Fire` - Good example if in a Character / Weapon class, as it has context. Bad if in a Barrel / Grass / any ambiguous class.
* `ReceiveMessage`
* `SortPlayerArray`
* `IsEnemy` - ["Is" is a verb.](http://writingexplained.org/is-is-a-verb)

Bad examples:
* `Dead` - Is Dead? Will deaden?
* `ProcessData` - Ambiguous, these words mean nothing.

<a name="3.3.1.2"></a>
<a name="bp-funcs-naming-onrep"></a>
#### 3.3.1.2 Property RepNotify Functions Always use `OnRep_VariableName`

<a name="3.3.1.3"></a>
<a name="bp-funcs-naming-bool"></a>
#### 3.3.1.3 Info Functions Returning Bool Should Ask Questions
* Should be marked const as they don't modify the blueprint
* Good examples: `IsDead` `IsOnFire` `IsAlive` `CanReload`

Bad examples: `Fire`,`Dead`
* `OnFire` - Can be confused with event dispatcher for firing.

<a name="3.3.1.4"></a>
<a name="bp-funcs-naming-eventhandlers"></a>
#### 3.3.1.4 Event Handlers and Dispatchers Should Start With `On`
* `Handle` is not allowed. It is 'Unreal' to use `On` instead of `Handle`, while other frameworks may prefer to use `Handle` instead of `On`.

Good examples: `OnDeath` `OnPickup` `OnTargetChanged`
Bad examples: `HandleDeath` `OnData` `OnTarget`


<a name="3.3.2"></a>
<a name="bp-funcs-return"></a>
#### 3.3.2 All Functions Must Have Return Nodes

<a name="3.3.3"></a>
<a name="bp-graphs-funcs-node-limit"></a>
#### 3.3.3 No Function Should Have More Than 50 Nodes
  
The following nodes are not counted as they are deemed to not increase function complexity:
* Comment
* Route
* Cast
* Getting a Variable
* Breaking a Struct
* Function Entry
* Self

<a name="3.3.5"></a>
<a name="bp-graphs-funcs-plugin-category"></a>
#### 3.3.5 All blueprint libary Functions Must Be Categorized By Project Name

<a name="3.4"></a>
<a name="bp-graphs"></a>
### 3.4 Blueprint Graphs

<a name="3.4.1"></a>
<a name="bp-graphs-spaghetti"></a>
#### 3.4.1 No Spaghetti
* Clear beginning and ends

<a name="3.4.2"></a>
<a name="bp-graphs-align-wires"></a>
#### 3.4.2 Align Wires Not Nodes
* Use Q to allign nodes.

Good example: The tops of the nodes are staggered to keep a perfectly straight white exec line.
![Aligned By Wires](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-good.png?raw=true "Aligned By Wires")

Bad Example: The tops of the nodes are aligned creating a wiggly white exec line.
![Bad](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-bad.png?raw=true "Wiggly")

Acceptable Example: Certain nodes might not cooperate no matter how you use the alignment tools. In this situation, try to minimize the wiggle by bringing the node in closer.
![Acceptable](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-acceptable.png?raw=true "Acceptable")

<a name="3.4.3"></a>
<a name="bp-graphs-exec-first-class"></a>
#### 3.4.3 White Exec Lines Are Top Priority

<a name="3.4.4"></a>
<a name="bp-graphs-block-comments"></a>
#### 3.4.4 Graphs Should Be Reasonably Commented

<a name="3.4.5"></a>
<a name="bp-graphs-cast-error-handling"></a>
#### 3.4.5 Graphs Should Handle Casting Errors Where Appropriate

<a name="3.4.6"></a>
<a name="bp-graphs-dangling-nodes"></a>
#### 3.4.6 Graphs Should Not Have Any unused nodes
  
**[⬆ Back to Top](#table-of-contents)**


<a name="4"></a>
<a name="Static Meshes"></a>
<a name="s"></a>
## 4. Static Meshes

This section will focus on Static Mesh assets and their internals.

<a name="4.1"></a>
<a name="s-uvs"></a>
### 4.1 Static Mesh UVs

<a name="4.1.1"></a>
<a name="s-uvs-no-missing"></a>
#### 4.1.1 All Meshes Must Have UVs

<a name="4.1.2"></a>
<a name="s-uvs-no-overlapping"></a>
#### 4.1.2 All Meshes Must Not Have Overlapping UVs for Lightmaps (Still a thing in ue5?)
  
<a name="4.2"></a>
<a name="s-lods"></a>
### 4.2 LODs Should Be Set Up Correctly

<a name="4.3"></a>
<a name="s-modular-snapping"></a>
### 4.3 Modular Assets should have measurements
  * 1, 2 or 4 meter a piece.
  
<a name="4.4"></a>
<a name="s-collision"></a>
### 4.4 All Meshes Must Have Collision
* Regardless of whether an asset is going to be used for collision in a level

<a name="4.5"></a>
<a name="s-scaled"></a>
### 4.5 All Meshes Should Be Scaled Correctly
* Scaling meshes in the engine should be treated as a scale override, not a scale correction.

**[⬆ Back to Top](#table-of-contents)**


<a name="5"></a>
<a name="Niagara"></a>
<a name="ng"></a>
## 5. Niagara

This section will focus on Niagara assets and their internals.

<a name="5.1"></a>
<a name="ng-rules"></a>
### 5.1 No Spaces, Ever
As mentioned in [00.1 Forbidden Identifiers](#00)

**[⬆ Back to Top](#table-of-contents)**


<a name="6"></a>
<a name="Levels"></a>
<a name="levels"></a>
## 6. Levels / Maps

[See Terminology Note](#terms-level-map) regarding "levels" vs "maps".

This section will focus on Level assets and their internals.

<a name="6.1"></a>
<a name="levels-no-errors-or-warnings"></a>
### 6.1 No Errors Or Warnings
* They should be fixed immediately to prevent cascading issues.
  
> You can run a map check on an open level in the editor by using the console command "map check".

<a name="6.2"></a>
<a name="levels-lighting-should-be-built"></a>
### 6.2 Lighting Should Be Built (Not relevant in ue5 ?)

<a name="6.3"></a>
<a name="levels-no-visible-z-fighting"></a>
### 6.3 No Player Visible Z Fighting

<a name="7"></a>
<a name="textures"></a>
## 7. Textures
  
<a name="7.1.1"></a>
<a name="textures-dimensions"></a>
### 7.1 Dimensions Are Powers of 2
* Textures do not have to be square.
* Exception for UI textures

For example, `128x512`, `1024x1024`, `2048x1024`, `1024x2048`, `1x512`.
  
<a name="7.1.2"></a>
<a name="textures-dimensions"></a>
### Texture conventions
  * Hero: 2048 x 2048
  * Secondary: 1024 x 1024
  * Designer materials: 2048 x 2048

<a name="7.2"></a>
<a name="textures-density"></a>
### 7.2 Texture Density Should Be Uniform
  
<a name="7.3"></a>
<a name="textures-max-size"></a>
### 7.3 Textures Should Be No Bigger than 8192

<a name="7.4"></a>
<a name="textures-group"></a>
### 7.4 Textures Should Be Grouped Correctly

**[⬆ Back to Top](#table-of-contents)**


## Major Contributors

* [Michael Allar](http://allarsblog.com): [GitHub](https://github.com/Allar), [Twitter](https://twitter.com/michaelallar)
* [CosmoMyzrailGorynych](https://github.com/CosmoMyzrailGorynych)
* [billymcguffin](https://github.com/billymcguffin)
* [akenatsu](https://github.com/akenatsu)
* [Damian]

## License

Copyright (c) 2016 Gamemakin LLC

See [LICENSE](/LICENSE)

**[⬆ Back to Top](#table-of-contents)**


## Amendments

We encourage you to fork this guide and change the rules to fit your team's style guide. Below, you may list some amendments to the style guide. This allows you to periodically update your style guide without having to deal with merge conflicts.

# };
