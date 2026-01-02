# Unreal Engine 5 Starter Template

A Git template for Unreal Engine 5 projects.

## Getting Started

1. Use this template to create a new repository **OR** clone this repository to your local machine.
2. Change the default **MyProject** name to reflect your project name in:
    - Markdown files (README.md, CONTRIBUTION.md, ... etc.)
    - Directories (Raw, Source, Content)
    - The .gitignore file
3. Delete everything above this line.
4. Have fun!

<hr>

# MyProject

## Table of Contents

> [1. Git Setup](#1-git-setup)<br/>
> [2. Directory Structures](#2-directory-structures)<br/>
> [3. Contribution](#3-contribution)<br/>

## 1. Git Setup

A correct `git` setup example _with [`git-lfs`](https://git-lfs.github.com/)_ for Unreal Engine 5.

## 2. Directory Structures

With `git`, you might want to also enable [One File Per Actor](https://dev.epicgames.com/documentation/en-us/unreal-engine/one-file-per-actor-in-unreal-engine) feature, as it provides a more atomic level versioning flow.

### 2.1 Repo Structure

- `/Build`
- `/Config`
- `/Content`
    - `/MyProject`
    - `/MyProjectDLC_01`
- `/Documentation`
- `/Plugins`
- `/Raw`
    - `/MyProject`
    - `/MyProjectDLC_01`
- `/Source`
    - `/MyProjectEditor`
    - `/MyProjectGame`
- `/Resources`
    - `/Editor`
    - `/Game`

> `git-lfs` management rules are mostly defined for file types, and not _paths_ however, there can entire paths marked to be managed by `git-lfs`. Without a special note, expect only type-based rules apply to a directory.

`/Build`

Holds files needed for building the engine or game, including files necessary for creating platform-specific builds.

`/Config`

Configuration files for setting values that control engine behavior. Values set in the game project Config files override the values set in the `Engine\Config` directory.

`/Content`

Holds content for the engine or game, including asset packages and maps.

`/Documentation`

Holds content for the documentations, like README.md or CONTRIBUTION.md.

`/Plugins`

Game plugins. Every plugin lives in a subdirectory of the `/Plugins` dir. A plugin internal directory structure is not strictly documented, so there are no assumptions on how a plugin is structured.
It may be useful to use git submodules to manage plugins in a more robust manner.
It is expected that each plugin will have its own `.gitignore` file in its subdirectory, as well other required specific git tweaks.

`/Raw`

**This directory is managed entirely by `git-lfs`.**

`/Raw` is a directory where you store assets in their source formats, in contrast to `/Content`, where assets are stored in the engine format (after the import). Having an asset in a source format is useful when you're still making updates to it. It may be a good idea to also have separate repos for managing work-in-progress assets (maybe in smaller collections or even idividually).

`/Source`

C++ source code is stored under the `/Source` path. As with most other directories, this directory is managed by standard git (and not `git-lfs`). That means no blobs. Do not put here any `.dll`s, `.exe`s, `.zip`s and other binaries. Only text files are allowed.
Generated text files can reside in the local `/Source` dir, but should be ignored by git with additional entries in `.gitignore`.

`/Source/MyProjectEditor`

Source files used by just the editor.

`/Source/MyProjectGame`

Source files in a game project directory are organized by module; one directory per module.

`/Resources`

Project and Editor related resources. This directory is managed by `git-lfs`.

`/Resources/Editor`

Resource files used by the editor. For example, splash images.

`/Resources/Game`

Resource files used by the game, but not from the content browser. For example, these files can be images or assets used to build the game.

### 2.2 Content Structure

All game content is placed in a sub-folder. eg. __Content/MyProject/UI/...__ This helps in migrating between projects and splitting your content from FAB packs that are added like __Content/MyFabPack/...__

When testing out local assets that are not ready to be used by other members of your team (or perhaps never should be) you can put them in your __Developer__-folder. You can enable this folder in the view options of the Content Browser. These assets will not show up in searches by other developers.

- `/MyProject`
    - `/AI`
    - `/Art`
        - `/Characters`
        - `/Environment`
            - `/Buildings`
            - `/Landscape`
            - `/Props`
    - `/Audio`
        - `/Data`
        - `/Music`
        - `/SFX`
    - `/Characters`
    - `/Core`
    - `/Editor`
    - `/FX`
        - `/Art`
    - `/Input`
        - `/Actions`
    - `/Maps`
        - `/Development`
    - `/Movies`
    - `/Shared`
        - `/Materials`
    - `/UI`
        - `/Art`
        - `/Fonts`
        - `/Materials`

`/Art`

Art related assets, except UI/FX.

`/Audio`

Audio related assets. `/Data` folder can be used for __SoundClasses__ or any other sound related logic.

`/Core`

The core gameplay logic, such as __GameInstance__ or __GameMode__.

`/Editor`

Any Editor related content, logic and resource.

`/FX`

Contains various particle effects.

`/Input`

All player input related logic.

`/Movies`

Pre-rendered movies. This directory also used by the [Async Loading Screen](https://www.fab.com/listings/f8aabb9a-7c96-4f79-97ff-04bcc146e595) plugin.

`/Shared`

Commonly used resources, such as __Master Materials__.

`/UI`

Any UI related content, logic and resource.

### 2.3 FAB Importing

It’s recommended to use a dedicated FAB content project to import the packs first. This is your staging area before migrating pieces into your main project. This lets you review and filter out unwanted content early.

> **Note:** To help maintain a clean project and Git structure, this template only includes directories from the **Content** directory that starts with **MyProject**. For example, the **MyProjectDLC_01** directory will be included, but the automatically generated **Developers** or **Collections** directory won't be included by default. You can change this behavior by modifying the **.gitignore** file.

## 3. Contribution

- [MyProject - Contribution Guidelines](CONTRIBUTION.md)
