# Unreal Engine 5 Starter template

Unreal Engine 5 Starter template for Git. A correct `git` setup example _with [`git-lfs`](https://git-lfs.github.com/)_ for Unreal Engine 5 and Unreal Engine 4 projects.

## Version Management Design and Conventions

This template implies some conventions to be used correctly, which are discussed below. You should be able copy and paste them into your project's `README.md` if you want to.

> If you are using `git` with Unreal Engine, you might want to also
> enable [One File Per Actor](https://dev.epicgames.com/documentation/en-us/unreal-engine/one-file-per-actor-in-unreal-engine)
> feature, as it provides a more atomic level versioning flow.

### Repo Structure

- `/Build`
- `/Config`
- `/Content`
    - `/MyGame`
    - `/MyGameDLC_01`
- `/Plugins`
- `/Raw`
    - `/MyGame`
    - `/MyGameDLC_01`
- `/Source`
    - `/Editor`
    - `/Game`

> `git-lfs` management rules are mostly defined for file types, and not _paths_, however there can entire paths marked to be managed by `git-lfs`. Without a special note, expect only type-based rules apply to a directory.

#### `/Build`

Holds files needed for building the engine or game, including files necessary for creating platform-specific builds.

#### `/Config`

Configuration files for setting values that control engine behavior. Values set in the game project Config files override the values set in the `Engine\Config` directory.

#### `/Content`

Holds content for the engine or game, including asset packages and maps.

#### `/Plugins`

Game plugins. Every plugin lives in a subdirectory of the `/Plugins` dir. A plugin internal directory structure is not strictly documented, so there are no assumptions on how a plugin is structured.
It may be useful to use git submodules to manage plugins in a more robust manner.
It is expected that each plugin will have it's own `.gitignore` file in it's subdirectory, as well other required specific git tweaks.

#### `/Raw`

**This directory is managed entirely by `git-lfs`.**

`/Raw` is a directory where you store assets in their source formats, in contrast to `/Content`, where assets are stored in the engine format (after the import). Having an asset in a source format is useful when you're still making updates to it. It may be a good idea to also have separate repos for managing work-in-progress assets (maybe in smaller collections or even idividually).

#### `/Source`

C++ source code is stored under the `/Source` path. As with most other directories, this directory is managed by standard git (and not `git-lfs`). That means no blobs. Do not put here any `.dll`s, `.exe`s, `.zip`s and other binaries. Only text files are allowed.
Generated text files can reside in the local `/Source` dir, but should be ignored by git with additional entries in `.gitignore`.

#### `/Source/Editor`

Source files used by just the editor.

#### `/Source/Game`

Source files in a game project directory are organized by module; one directory per module.

### Content Structure

All game content is placed in a sub-folder. eg. __Content/MyGame/UI/...__ This helps in migrating between projects and splitting your content from marketplace packs that are added like __Content/MyMarketplacePack/...__

When testing out local assets that are not ready to be used by other members of your team (or perhaps never should be) you can put them in your __Developer__-folder. You can enable this folder in the view options of the Content Browser. These assets will not show up in searches by other developers.

- `/MyGame`
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

#### `/Art`

Art related assets, except UI/FX.

#### `/Audio`

Audio related assets. `/Data` folder can be used for __SoundClasses__ or any other sound related logic.

#### `/Core`

The core gameplay logic, such as __GameInstance__ or __GameMode__.

#### `/FX`

Contains various particle effects.

#### `/Input`

All player input related logic.

#### `/Movies`

Pre-rendered movies. This directory also used by the [Async Loading Screen](https://www.fab.com/listings/f8aabb9a-7c96-4f79-97ff-04bcc146e595) plugin.

#### `/Shared`

Commonly used resources, such as __Master Materials__.

#### `/UI`

Any UI related content, logic and resource.

### Marketplace Importing

It’s recommended to use a dedicated Marketplace content project to import the packs first. This is your staging area before migrating pieces into your main project. This lets you review and filter out unwanted content early.

## How to use

1. Set up `git` and `git-lfs`.
2. Copy the files and folders to your project. All of them in one go or selectively as you wish.
3. Rename directories starts with `MyGame` to your project's name.

## Related resources

### Unreal Engine Offical Documentation

- [Activating Source Control](https://dev.epicgames.com/documentation/en-us/unreal-engine/source-control-in-unreal-engine)
- [Recommended Asset Naming Conventions](https://dev.epicgames.com/documentation/en-us/unreal-engine/recommended-asset-naming-conventions-in-unreal-engine-projects)
- [Directory Structure](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-engine-directory-structure)
