## Overview
<a name="0.1"></a>
### We have a style guide, try to abide by  it.
* If a rule doesn't work for us, we can change it.
* This guide is a revision of https://github.com/TheDimin/ue5-style-guide
 ** If you wonder why a rule is the way it is, check that document.

### The project should look like a single person created it.
### If you see someone working either against a style guide or no style guide, try to correct them.
* It is far easier to help and to ask for help when people are consistent.

<a name="00"></a>
## 00. Globally Enforced Opinions

<a name="00.1"></a>
### 00.1 Forbidden Characters

<a name="identifiers-1"></a>
#### Identifiers
Any `Identifier`(Names) should strive to only have the following characters when possible

* ABCDEFGHIJKLMNOPQRSTUVWXYZ
* abcdefghijklmnopqrstuvwxyz
* 1234567890

<a name="anc"></a>
<a name="1"></a>

## Table of contents
- [Important Terminology](#important-terminology)
  - [Levels/Maps](#terms-level-map)
  - [Identifiers](#terms-identifiers)
  - [Cases](#terms-cases)
  - [Variables / Properties](#terms-var-prop)
    - [Property](#terms-property)
    - [Variable](#terms-variable)
- [0. Principles](#0)
  - [0.1 If your UE4 project already has a style guide, you should follow it](#0.1)
  - [0.2 All structure, assets, and code in any Unreal Engine 4 project should look like a single person created it, no matter how many people contributed](#0.2)
  - [0.3 Friends do not let friends have bad style](#0.3)
  - [0.4 A team without a style guide is no team of mine](#0.4)
  - [0.5 Don't Break The Law](#0.5)
- [00. Globally Enforced Opinions](#00)
  - [00.1 Forbidden Characters](#00.1)
    - [Identifiers](#identifiers)
- [1. Asset Naming Conventions](#anc)
  - [1.1 Base Asset Name - `Prefix_BaseAssetName_Variant_Suffix`](#base-asset-name)
    - [1.1 Examples](#1.1-examples)
  - [1.2 Asset Name Modifiers](#asset-name-modifiers)
    - [1.2.1 Most Common](#anc-common)
    - [1.2.2 Animations](#anc-animations)
  - [1.2.3 Artificial Intelligence](#anc-ai)
  - [1.2.4 Blueprints](#anc-bp)
  - [1.2.5 Materials](#anc-materials)
  - [1.2.6 Textures](#anc-textures)
    - [1.2.6.1 Texture Packing](#anc-textures-packing)
  - [1.2.7 Miscellaneous](#anc-misc)
  - [1.2.8 Paper 2D](#anc-paper2d)
  - [1.2.9 Physics](#anc-physics)
  - [1.2.10 Sounds](#anc-sounds)
  - [1.2.11 User Interface](#anc-ui)
  - [1.2.12 Effects](#anc-effects)
- [2. Content Directory Structure](#structure)
  - [2e1 Example Project Content Structure](#2e1)
  - [2.1 Folder Names](#structure-folder-names)
    - [2.1.1 Always Use PascalCase](#2.1.1)
    - [2.1.2 Never Use Spaces](#2.1.2)
    - [2.1.3 Never Use Unicode Characters And Other Symbols](#2.1.3)
  - [2.2 Use A Top Level Folder For Project Specific Assets](#structure-top-level)
    - [2.2.1 No Global Assets](#2.2.1)
    - [2.2.2 Reduce Migration Conflicts](#2.2.2)
      - [2.2.2e1 Master Material Example](#2.2.2e1)
    - [2.2.3 Samples, Templates, and Marketplace Content Are Risk-Free](#2.2.3)
    - [2.2.4 DLC, Sub-Projects, and Patches Are Easily Maintained](#2.2.4)
  - [2.3 Use Developers Folder For Local Testing](#structure-developers)
  - [2.4 All Map<sup>*</sup> Files Belong In A Folder Called Maps](#structure-maps)
  - [2.5 Use A `Core` Folder For Critical Blueprints And Other Assets](#structure-core)
  - [2.6 Do Not Create Folders Called `Assets` or `AssetTypes`](#structure-assettypes)
    - [2.6.1 Creating a folder named `Assets` is redundant](#2.6.1)
    - [2.6.2 Creating a folder named `Meshes`, `Textures`, or `Materials` is redundant](#2.6.2)
  - [2.7 Very Large Asset Sets Get Their Own Folder Layout](#structure-large-sets)
  - [2.8 `MaterialLibrary`](#structure-material-library)
  - [2.9 No Empty Folders](#structure-no-empty-folders)
- [3. Blueprints](#bp)
  - [3.1 Compiling](#bp-compiling)
  - [3.2 Variables](#bp-vars)
    - [3.2.1 Naming](#bp-var-naming)
      - [3.2.1.1 Nouns](#bp-var-naming-nouns)
      - [3.2.1.2 PascalCase](#bp-var-naming-case)
        - [3.2.1.2e Examples](#3.2.1.2e)
      - [3.2.1.3 Boolean `b` Prefix](#bp-var-bool-prefix)
      - [3.2.1.4 Boolean Names](#bp-var-bool-names)
        - [3.2.1.4.1 General And Independent State Information](#3.2.1.4.1)
        - [3.2.1.4.2 Complex States](#3.2.1.4.2)
      - [3.2.1.5 Considered Context](#bp-vars-naming-context)
        - [3.2.1.5e Examples](#3.2.1.5e)
      - [3.2.1.6 Do _Not_ Include Atomic Type Names](#bp-vars-naming-atomic)
      - [3.2.1.7 Do Include Non-Atomic Type Names](#bp-vars-naming-complex)
      - [3.2.1.8 Arrays](#bp-vars-naming-arrays)
    - [3.2.2 Editable Variables](#bp-vars-editable)
      - [3.2.2.1 Tooltips](#bp-vars-editable-tooltips)
      - [3.2.2.2 Slider And Value Ranges](#bp-vars-editable-ranges)
    - [3.2.3 Categories](#bp-vars-categories)
    - [3.2.4 Variable Access Level](#bp-vars-access)
      - [3.2.4.1 Private Variables](#bp-vars-access-private)
    - [3.2.5 Advanced Display](#bp-vars-advanced)
    - [3.2.6 Transient Variables](#bp-vars-transient)
    - [3.2.8 Config Variables](#bp-vars-config)
  - [3.3 Functions, Events, and Event Dispatchers](#bp-functions)
    - [3.3.1 Function Naming](#bp-funcs-naming)
    - [3.3.1.1 All Functions Should Be Verbs](#bp-funcs-naming-verbs)
    - [3.3.1.2 Property RepNotify Functions Always `OnRep_Variable`](#bp-funcs-naming-onrep)
    - [3.3.1.3 Info Functions Returning Bool Should Ask Questions](#bp-funcs-naming-bool)
    - [3.3.1.4 Event Handlers and Dispatchers Should Start With `On`](#bp-funcs-naming-eventhandlers)
    - [3.3.1.5 Remote Procedure Calls Should Be Prefixed With Target](#bp-funcs-naming-rpcs)
    - [3.3.2 All Functions Must Have Return Nodes](#bp-funcs-return)
    - [3.3.3 No Function Should Have More Than 50 Nodes](#bp-graphs-funcs-node-limit)
    - [3.3.4 All Public Functions Should Have A Description](#bp-graphs-funcs-description)
    - [3.3.5 All Custom Static Plugin `BlueprintCallable` Functions Must Be Categorized By Plugin Name](#bp-graphs-funcs-plugin-category)
  - [3.4 Blueprint Graphs](#bp-graphs)
    - [3.4.1 No Spaghetti](#bp-graphs-spaghetti)
    - [3.4.2 Align Wires Not Nodes](#bp-graphs-align-wires)
    - [3.4.3 White Exec Lines Are Top Priority](#bp-graphs-exec-first-class)
    - [3.4.4 Graphs Should Be Reasonably Commented](#bp-graphs-block-comments)
    - [3.4.5 Graphs Should Handle Casting Errors Where Appropriate](#bp-graphs-cast-error-handling)
    - [3.4.6 Graphs Should Not Have Any Dangling / Loose / Dead Nodes](#bp-graphs-dangling-nodes)
- [4. Static Meshes](#4)
  - [4.1 Static Mesh UVs](#s-uvs)
    - [4.1.1 All Meshes Must Have UVs](#s-uvs-no-missing)
    - [4.1.2 All Meshes Must Not Have Overlapping UVs for Lightmaps](#s-uvs-no-overlapping)
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
  - [6.4 Marketplace Specific Rules](#levels-mp-rules)
    - [6.4.1 Overview Level](#levels-mp-rules-overview)
    - [6.4.2 Demo Level](#levels-mp-rules-demo)
- [7. Textures](#textures)
  - [7.1 Dimensions Are Powers of 2](#textures-dimensions)
  - [7.2 Texture Density Should Be Uniform](#textures-density)
  - [7.3 Textures Should Be No Bigger than 8192](#textures-max-size)
  - [7.4 Textures Should Be Grouped Correctly](#textures-group)

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
| Static Mesh (01)        | S_Rock_01                                                  |
| Static Mesh (02)        | S_Rock_02                                                  |
| Static Mesh (03)        | S_Rock_03                                                  |
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
| Static Mesh             | S_         |            | Many use SM_. We use S_.         |
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
 ** Fix them immediately
  
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
##### 3.2.1.1 Nouns
All variable names must be clear, unambiguous, and descriptive nouns.
All variables must use PascalCasing

<a name="3.2.1.5"></a>
<a name="bp-vars-naming-context"></a>
##### 3.2.1.5 Considered Context
All variable names must not be redundant with their context as all variable references in Blueprint will always have context.
* Examples for variables inside `BP_PlayerCharacter` **BAD** `PlayerScore`,`PlayerKills` **GOOD* `Score`,`Kills`

<a name="3.2.1.8"></a>
<a name="bp-vars-naming-arrays"></a>
##### 3.2.1.8 Arrays

Arrays follow the same naming rules as above, but should be named as a plural noun.

Example: Use `Targets`, `Hats`, and `EnemyPlayers`, **not** `TargetList`, `HatArray`, `EnemyPlayerArray`.


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
If a class has only a small number of variables, categories are not required.
If a class has a moderate amount of variables (5+), all `Editable` variables should have a non-default category assigned.
  
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
This section describes how you should author functions, events, and event dispatchers. Everything that applies to functions also applies to events, unless otherwise noted.

<a name="3.3.1"></a>
<a name="bp-funcs-naming"></a>
#### 3.3.1 Function Naming
The naming of functions, events, and event dispatchers is critically important. Based on the name alone, certain assumptions can be made about functions. For example:

* Is it a pure function?
* Is it fetching state information?
* Is it a handler?
* What is its purpose?

These questions and more can all be answered when functions are named appropriately.

<a name="3.3.1.1"></a>
<a name="bp-funcs-naming-verbs"></a>
#### 3.3.1.1 All Functions Should Be Verbs
* All functions should all start with verbs. 
* They should be worded in the present tense whenever possible. 
* They should also have  context as to what they are doing.
  
Good examples:
* `Fire` - Good example if in a Character / Weapon class, as it has context. Bad if in a Barrel / Grass / any ambiguous class.
* `ReceiveMessage`
* `SortPlayerArray`
* `IsEnemy` - ["Is" is a verb.](http://writingexplained.org/is-is-a-verb)

Bad examples:

* `Dead` - Is Dead? Will deaden?
* `Rock`
* `ProcessData` - Ambiguous, these words mean nothing.
* `PlayerState` - Nouns are ambiguous.
* `Color` - Verb with no context, or ambiguous noun.

<a name="3.3.1.2"></a>
<a name="bp-funcs-naming-onrep"></a>
#### 3.3.1.2 Property RepNotify Functions Always `OnRep_Variable`

All functions for replicated with notification variables should have the form `OnRep_Variable`. This is forced by the Blueprint editor. If you are writing a C++ `OnRep` function however, it should also follow this convention when exposing it to Blueprints.

<a name="3.3.1.3"></a>
<a name="bp-funcs-naming-bool"></a>
#### 3.3.1.3 Info Functions Returning Bool Should Ask Questions

When writing a function that does not change the state of or modify any object and is purely for getting information, state, or computing a yes/no value, it should ask a question. This should also follow [the verb rule](#bp-funcs-naming-verbs).

This is extremely important as if a question is not asked, it may be assumed that the function performs an action and is returning whether that action succeeded.

Good examples:

* `IsDead`
* `IsOnFire`
* `IsAlive`
* `IsSpeaking`
* `IsHavingAnExistentialCrisis`
* `IsVisible`
* `HasWeapon` - ["Has" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)
* `WasCharging` - ["Was" is past-tense of "be".](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html) Use "was" when referring to 'previous frame' or 'previous state'.
* `CanReload` - ["Can" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)

Bad examples:

* `Fire` - Is on fire? Will fire? Do fire?
* `OnFire` - Can be confused with event dispatcher for firing.
* `Dead` - Is dead? Will deaden?
* `Visibility` - Is visible? Set visibility? A description of flying conditions?

<a name="3.3.1.4"></a>
<a name="bp-funcs-naming-eventhandlers"></a>
#### 3.3.1.4 Event Handlers and Dispatchers Should Start With `On`

Any function that handles an event or dispatches an event should start with `On` and continue to follow [the verb rule](#bp-funcs-naming-verbs). The verb may move to the end however if past-tense reads better.

[Collocations](http://dictionary.cambridge.org/us/grammar/british-grammar/about-words-clauses-and-sentences/collocation) of the word `On` are exempt from following the verb rule.

`Handle` is not allowed. It is 'Unreal' to use `On` instead of `Handle`, while other frameworks may prefer to use `Handle` instead of `On`.

Good examples:

* `OnDeath` - Common collocation in games
* `OnPickup`
* `OnReceiveMessage`
* `OnMessageRecieved`
* `OnTargetChanged`
* `OnClick`
* `OnLeave`

Bad examples:

* `OnData`
* `OnTarget`
* `HandleMessage`
* `HandleDeath`

<a name="3.3.1.5"></a>
<a name="bp-funcs-naming-rpcs"></a>
#### 3.3.1.5 Remote Procedure Calls Should Be Prefixed With Target

Any time an RPC is created, it should be prefixed with either `Server`, `Client`, or `Multicast`. No exceptions.

After the prefix, follow all other rules regarding function naming.

Good examples:

* `ServerFireWeapon`
* `ClientNotifyDeath`
* `MulticastSpawnTracerEffect`

Bad examples:

* `FireWeapon` - Does not indicate its an RPC of some kind.
* `ServerClientBroadcast` - Confusing.
* `AllNotifyDeath` - Use `Multicast`, never `All`.
* `ClientWeapon` - No verb, ambiguous.


<a name="3.3.2"></a>
<a name="bp-funcs-return"></a>
#### 3.3.2 All Functions Must Have Return Nodes

All functions must have return nodes, no exceptions.

Return nodes explicitly note that a function has finished its execution. In a world where blueprints can be filled with `Sequence`, `ForLoopWithBreak`, and backwards reroute nodes, explicit execution flow is important for readability, maintenance, and easier debugging.

The Blueprint compiler is able to follow the flow of execution and will warn you if there is a branch of your code with an unhandled return or bad flow if you use return nodes.

In situations like where a programmer may add a pin to a Sequence node or add logic after a for loop completes but the loop iteration might return early, this can often result in an accidental error in code flow. The warnings the Blueprint compiler will alert everyone of these issues immediately.

<a name="3.3.3"></a>
<a name="bp-graphs-funcs-node-limit"></a>
#### 3.3.3 No Function Should Have More Than 50 Nodes

Simply, no function should have more than 50 nodes. Any function this big should be broken down into smaller functions for readability and ease of maintenance.

The following nodes are not counted as they are deemed to not increase function complexity:

* Comment
* Route
* Cast
* Getting a Variable
* Breaking a Struct
* Function Entry
* Self

<a name="3.3.4"></a>
<a name="bp-graphs-funcs-description"></a>
#### 3.3.4 All Public Functions Should Have A Description

This rule applies more to public facing or marketplace blueprints, so that others can more easily navigate and consume your blueprint API.

Simply, any function that has an access specificer of Public should have its description filled out.

<a name="3.3.5"></a>
<a name="bp-graphs-funcs-plugin-category"></a>
#### 3.3.5 All Custom Static Plugin `BlueprintCallable` Functions Must Be Categorized By Plugin Name

If your project includes a plugin that defines `static` `BlueprintCallable` functions, they should have their category set to the plugin's name or a subset category of the plugin's name.

For example, `Zed Camera Interface` or `Zed Camera Interface | Image Capturing`.

<a name="3.4"></a>
<a name="bp-graphs"></a>
### 3.4 Blueprint Graphs

This section covers things that apply to all Blueprint graphs.

<a name="3.4.1"></a>
<a name="bp-graphs-spaghetti"></a>
#### 3.4.1 No Spaghetti

Wires should have clear beginnings and ends. You should never have to mentally untangle wires to make sense of a graph. Many of the following sections are dedicated to reducing spaghetti.

<a name="3.4.2"></a>
<a name="bp-graphs-align-wires"></a>
#### 3.4.2 Align Wires Not Nodes

Always align wires, not nodes. You can't always control the size and pin location on a node, but you can always control the location of a node and thus control the wires. Straight wires provide clear linear flow. Wiggly wires wear wits wickedly. You can straighten wires by using the Straighten Connections command with BP nodes selected. Hotkey: Q

Good example: The tops of the nodes are staggered to keep a perfectly straight white exec line.
![Aligned By Wires](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-good.png?raw=true "Aligned By Wires")

Bad Example: The tops of the nodes are aligned creating a wiggly white exec line.
![Bad](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-bad.png?raw=true "Wiggly")

Acceptable Example: Certain nodes might not cooperate no matter how you use the alignment tools. In this situation, try to minimize the wiggle by bringing the node in closer.
![Acceptable](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-acceptable.png?raw=true "Acceptable")

<a name="3.4.3"></a>
<a name="bp-graphs-exec-first-class"></a>
#### 3.4.3 White Exec Lines Are Top Priority

If you ever have to decide between straightening a linear white exec line or straightening data lines of some kind, always straighten the white exec line.

<a name="3.4.4"></a>
<a name="bp-graphs-block-comments"></a>
#### 3.4.4 Graphs Should Be Reasonably Commented

Blocks of nodes should be wrapped in comments that describe their higher-level behavior. While every function should be well named so that each individual node is easily readable and understandable, groups of nodes contributing to a purpose should have their purpose described in a comment block. If a function does not have many blocks of nodes and its clear that the nodes are serving a direct purpose in the function's goal, then they do not need to be commented as the function name and  description should suffice.

<a name="3.4.5"></a>
<a name="bp-graphs-cast-error-handling"></a>
#### 3.4.5 Graphs Should Handle Casting Errors Where Appropriate

If a function or event assumes that a cast always succeeds, it should appropriately report a failure in logic if the cast fails. This lets others know why something that is 'supposed to work' doesn't. A function should also attempt a graceful recover after a failed cast if it's known that the reference being casted could ever fail to be casted.

This does not mean every cast node should have its failure handled. In many cases, especially events regarding things like collisions, it is expected that execution flow terminates on a failed cast quietly.

<a name="3.4.6"></a>
<a name="bp-graphs-dangling-nodes"></a>
#### 3.4.6 Graphs Should Not Have Any Dangling / Loose / Dead Nodes

All nodes in all blueprint graphs must have a purpose. You should not leave dangling blueprint nodes around that have no purpose or are not executed.

**[⬆ Back to Top](#table-of-contents)**


<a name="4"></a>
<a name="Static Meshes"></a>
<a name="s"></a>
## 4. Static Meshes

This section will focus on Static Mesh assets and their internals.

<a name="4.1"></a>
<a name="s-uvs"></a>
### 4.1 Static Mesh UVs

If Linter is reporting bad UVs and you can't seem to track it down, open the resulting `.log` file in your project's `Saved/Logs` folder for exact details as to why it's failing. I am hoping to include these messages in the Lint report in the future.

<a name="4.1.1"></a>
<a name="s-uvs-no-missing"></a>
#### 4.1.1 All Meshes Must Have UVs

Pretty simple. All meshes, regardless how they are to be used, should not be missing UVs.

<a name="4.1.2"></a>
<a name="s-uvs-no-overlapping"></a>
#### 4.1.2 All Meshes Must Not Have Overlapping UVs for Lightmaps

Pretty simple. All meshes, regardless how they are to be used, should have valid non-overlapping UVs.

<a name="4.2"></a>
<a name="s-lods"></a>
### 4.2 LODs Should Be Set Up Correctly

This is a subjective check on a per-project basis, but as a general rule any mesh that can be seen at varying distances should have proper LODs.

<a name="4.3"></a>
<a name="s-modular-snapping"></a>
### 4.3 Modular Socketless Assets Should Snap To The Grid Cleanly

This is a subjective check on a per-asset basis, however any modular socketless assets should snap together cleanly based on the project's grid settings.

It is up to the project whether to snap based on a power of 2 grid or on a base 10 grid. However if you are authoring modular socketless assets for the marketplace, Epic's requirement is that they snap cleanly when the grid is set to 10 units or bigger.

<a name="4.4"></a>
<a name="s-collision"></a>
### 4.4 All Meshes Must Have Collision

Regardless of whether an asset is going to be used for collision in a level, all meshes should have proper collision defined. This helps the engine with things such as bounds calculations, occlusion, and lighting. Collision should also be well-formed to the asset.

<a name="4.5"></a>
<a name="s-scaled"></a>
### 4.5 All Meshes Should Be Scaled Correctly

This is a subjective check on a per-project basis, however all assets should be scaled correctly to their project. Level designers or blueprint authors should not have to tweak the scale of meshes to get them to confirm in the editor. Scaling meshes in the engine should be treated as a scale override, not a scale correction.

**[⬆ Back to Top](#table-of-contents)**


<a name="5"></a>
<a name="Niagara"></a>
<a name="ng"></a>
## 5. Niagara

This section will focus on Niagara assets and their internals.

<a name="5.1"></a>
<a name="ng-rules"></a>
### 5.1 No Spaces, Ever

As mentioned in [00.1 Forbidden Identifiers](#00), spaces and all white space characters are forbidden in identifiers. This is especially true for Niagara systems as it makes working with things significantly harder if not impossible when working with HLSL or other means of scripting within Niagara and trying to reference an identifier.

(Original Contribution by [@dunenkoff](https://github.com/Allar/ue5-style-guide/issues/58))


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

All levels should load with zero errors or warnings. If a level loads with any errors or warnings, they should be fixed immediately to prevent cascading issues.

You can run a map check on an open level in the editor by using the console command "map check".

Please note: Linter is even more strict on this than the editor is currently, and will catch load errors that the editor will resolve on its own.

<a name="6.2"></a>
<a name="levels-lighting-should-be-built"></a>
### 6.2 Lighting Should Be Built

It is normal during development for levels to occasionally not have lighting built. When doing a test/internal/shipping build or any build that is to be distributed however, lighting should always be built.

<a name="6.3"></a>
<a name="levels-no-visible-z-fighting"></a>
### 6.3 No Player Visible Z Fighting

Levels should not have any [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) in all areas visible to the player.

<a name="6.4"></a>
<a name="levels-mp-rules"></a>
### 6.4 Marketplace Specific Rules

If a project is to be sold on the UE4 Marketplace, it must follow these rules.

<a name="6.4.1"></a>
<a name="levels-mp-rules-overview"></a>
#### 6.4.1 Overview Level

If your project contains assets that should be visualized or demoed, you must have a map within your project that contains the name "Overview".

This overview map, if it is visualizing assets, should be set up according to [Epic's guidelines](http://help.epicgames.com/customer/en/portal/articles/2592186-marketplace-submission-guidelines-preparing-your-assets#Required%20Levels%20and%20Maps).

For example, `InteractionComponent_Overview`.

<a name="6.4.2"></a>
<a name="levels-mp-rules-demo"></a>
#### 6.4.2 Demo Level

If your project contains assets that should be demoed or come with some sort of tutorial, you must have a map within your project that contains the name "Demo". This level should also contain documentation within it in some form that illustrates how to use your project. See Epic's Content Examples project for good examples on how to do this.

If your project is a gameplay mechanic or other form of system as opposed to an art pack, this can be the same as your "Overview" map.

For example, `InteractionComponent_Overview_Demo`, `ExplosionKit_Demo`.

**[⬆ Back to Top](#table-of-contents)**


<a name="7"></a>
<a name="textures"></a>
## 7. Textures

This section will focus on Texture assets and their internals.

<a name="7.1"></a>
<a name="textures-dimensions"></a>
### 7.1 Dimensions Are Powers of 2

All textures, except for UI textures, must have its dimensions in multiples of powers of 2. Textures do not have to be square.

For example, `128x512`, `1024x1024`, `2048x1024`, `1024x2048`, `1x512`.

<a name="7.2"></a>
<a name="textures-density"></a>
### 7.2 Texture Density Should Be Uniform

All textures should be of a size appropriate for their standard use case. Appropriate texture density varies from project to project, but all textures within that project should have a consistent density.

For example, if a project's texture density is 8 pixel per 1 unit, a texture that is meant to be applied to a 100x100 unit cube should be 1024x1024, as that is the closest power of 2 that matches the project's texture density.

<a name="7.3"></a>
<a name="textures-max-size"></a>
### 7.3 Textures Should Be No Bigger than 8192

No texture should have a dimension that exceeds 8192 in size, unless you have a very explicit reason to do so. Often, using a texture this big is simply just a waste of resources.

<a name="7.4"></a>
<a name="textures-group"></a>
### 7.4 Textures Should Be Grouped Correctly

Every texture has a Texture Group property used for LODing, and this should be set correctly based on its use. For example, all UI textures should belong in the UI texture group.

**[⬆ Back to Top](#table-of-contents)**


## Major Contributors

* [Michael Allar](http://allarsblog.com): [GitHub](https://github.com/Allar), [Twitter](https://twitter.com/michaelallar)
* [CosmoMyzrailGorynych](https://github.com/CosmoMyzrailGorynych)
* [billymcguffin](https://github.com/billymcguffin)
* [akenatsu](https://github.com/akenatsu)

## License

Copyright (c) 2016 Gamemakin LLC

See [LICENSE](/LICENSE)

**[⬆ Back to Top](#table-of-contents)**


## Amendments

We encourage you to fork this guide and change the rules to fit your team's style guide. Below, you may list some amendments to the style guide. This allows you to periodically update your style guide without having to deal with merge conflicts.

# };
