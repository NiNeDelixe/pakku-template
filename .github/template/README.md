<h1 align="center">%%myproject%%</h1>
<p align="center"><b><i>%%description%%</i></b></p>
<h1 align="center">
    <a href="%%pakku_url%%/blob/main/LICENSE.md"><img src="https://img.shields.io/github/license/%%myorg%%/%%myproject%%?style=for-the-badge&logo=github" alt="License"></a>
</h1>

## Features
- **Pakku:**
    - Easily control mods and resource packs, handling dependencies for you.
        - Mods can be pulled from CurseForge, Modrinth, and even GitHub releases!
            - [Manual overrides work as well](https://juraj-hrivnak.github.io/Pakku/adding-manual-overrides.html)
        - Mods and folders can be easily marked as client or server-side only, or even to [not export at all](https://github.com/NiNeDelixe/pakku-template/blob/cfda140750ebd454094415e32a4f971d49153428/pakku.json#L31C1-L34C10)!
    - Simultaneous CurseForge and Modrinth Modpack Support[^1]
    - Mods can be easily fetched (more on that below)
- **CI/CD (GitHub Actions):**
    - **Autolinting**
        - By default, will **automatically fix** any lint issues in the KubeJS folder, keeping your code organized hassle-free.
            - This behavior can be easily changed as applicable, if you prefer it to check pull requests
        - Custom Rules for Recipe Spacing, Call Chains and GTm Multiblocks (and more) included
    - **Auto-updating:**
        - **Automatically sync your instance's mods** with the repository
        - **Automatically sync your instance's modloader version** (and more) with the repository
            - Supports Forge and NeoForge
    - **Build and Release**
        - Automatically builds on commit, and will push to CurseForge on a version change (Server packs included)
        - Automatically Diffs Mods and Pull Requests, and attaches your changelog
        - Can replace text with the update number, useful for the main menu or loading screen.
        - Can publish a truncated changelog to Discord if a webhook is provided.
- **Other:**
    - Very quick setup for contributors
    - VSC Workspace (in the `.vscode` folder)
    - Issue and PR templates
    - `.gitignore` (including some mod configs that add a last edited date)

### Requirements
* This template was written with [Prism Launcher](https://prismlauncher.org/) in mind. Those using other launchers will need to adjust setup instructions as needed to allow their launcher to recognize the template as an instance. Launchers without the ability to set pre-launch commands will need to fetch mods manually (see below).

## Setup
### As a standalone template
1. Clone the repository
2. Change MC and loader version with [`java -jar pakku.jar set -v <mc_version> -l <loader>=<loader_version>`](#) command or import an existing modpack

### As a template for a new project
1. Clone your copy of this template into an empty [`(instancename)\minecraft`](https://github.com/user-attachments/assets/f9de6554-925d-4827-b51c-c7159e6f915f) folder
2. Copy the contents of `(instancename)\minecraft\.pakku\prism-overrides`[^2] into your `(instancename)` folder to have a working [Prism Instance](https://prismlauncher.org/).[^3]

By default, the pack comes with a set of mods most packdevs find useful (optimization mods, KubeJS, Jade, etc); To add your mods and resourcepacks, open the project's `/minecraft/` folder in a terminal (using a code editor such as VSC is recommended), and run [`java -jar pakku.jar add [<options>] [<projects>]`](https://juraj-hrivnak.github.io/Pakku/managing-projects.html#adding-projects). Pakku will handle dependencies for you.

### Importing into an existing repository
1. In your existing Minecraft instance's `/minecraft/` folder, ensure that you have one of the following available: `manifest.json` `modrinth.index.json` `.mrpack`, or a CurseForge `.zip` file. [(You can generate one with Prism)](https://github.com/user-attachments/assets/88f3518d-604f-46d9-a319-775c6daa05cb)
2. Clone the `%%myproject%%` template somewhere, copy over everything but `pakku-lock.json` (and `.gitattributes` and `.git` folder, of course) to your project root.
3. Open up your terminal, [change directory](https://www.wikihow.com/images/thumb/0/08/Change-Directories-in-Command-Prompt-Step-7-Version-2.jpg/v4-460px-Change-Directories-in-Command-Prompt-Step-7-Version-2.jpg.webp) to your instance's `/minecraft/` folder, and run [`java -jar pakku.jar import <file from step 1>`](https://juraj-hrivnak.github.io/Pakku/managing-projects.html#adding-projects)
4. Edit `minecraft/pakku.json`, and `minecraft/.pakku/prism-overrides/` as applicable, and add `java -jar pakku.jar fetch` to your instance's [pre-launch commands](https://github.com/user-attachments/assets/494a632d-1af4-453d-9329-5454ac3d22da)

Don't forget to link to this page in your README so contributors will know how to set up their own instance!

### Contributing to an existing repository that uses this template
1. Clone your fork of the repository into an empty [`(instancename)\minecraft`](https://github.com/user-attachments/assets/f9de6554-925d-4827-b51c-c7159e6f915f) folder, and copy the contents of `(instancename)\minecraft\.pakku\prism-overrides` into your `(instancename)` folder to have a working Prism Instance. From there, you can start your newly created instances and the mods will be downloaded for you.[^3]
