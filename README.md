![libGDX Logo](libgdx_logo.svg#gh-light-mode-only)
![libGDX Logo](libgdx_logo_dark.svg#gh-dark-mode-only)

[![GitHub Actions Build Status](https://img.shields.io/github/actions/workflow/status/amilego/libgdx/build-publish.yml?branch=master&label=GitHub%20Actions)](https://github.com/libgdx/libgdx/actions?query=workflow%3A%22Build+and+Publish%22)

[![Latest Version](https://img.shields.io/maven-central/v/com.amilego.gdx/gdx?label=Version)](https://search.maven.org/artifact/com.amilego.gdx/gdx)
[![Snapshots](https://img.shields.io/maven-metadata/v?metadataUrl=https%3A%2F%2Fcentral.sonatype.com%2Frepository%2Fmaven-snapshots%2Fcom%2Familego%2Fgdx%2Fgdx%2Fmaven-metadata.xml&label=Snapshots)](https://central.sonatype.com/repository/maven-snapshots/com/amilego/gdx/gdx/maven-metadata.xml)

# libGDX (AmiLego fork)

## Introduction

This is a **fork** of [the original libGDX repository](https://github.com/libgdx/libgdx), maintaining by [the AmiLego organization](https://github.com/amilego).

To use this fork library, you can just replace the group ID from `com.badlogicgames.gdx` to `com.amilego.gdx` in your Gradle build script or Maven file.

## Changes We Made

This fork is intended to provide a **minimal version** of libGDX, so some features are removed to reduce the size of the library.

### 🚫 1. Removed Features

| Removed Feature            | Affected Artifact                                         | Affected Package                            |
| :------------------------- | :-------------------------------------------------------- | :------------------------------------------ |
| LWJGL2 desktop backend     | `:gdx-backend-lwjgl`                                      | `.backends.lwjgl`                           |
| GWT / HTML5 backend        | `:gdx-backends-gwt`                                       | `.gdx.backends.gwt`                         |
| iOS backend                | `:gdx-backend-robovm`, `:gdx-backend-robovm-metalangle` | `.backends.ios`                             |
| Box2D physics extension    | `:gdx-box2d`                                              | `.physics.box2d`                            |
| Bullet physics extension   | `:gdx-bullet`                                             | `.physics.bullet`                           |
| Developer tools            | `:gdx-tools`                                              | `.tools`                                    |
| Scene2D UI toolkit         | `:gdx`                                                    | `.scenes.scene2d`                           |
| Tiled map API              | `:gdx`                                                    | `.maps`                                     |
| Networking API             | `:gdx`                                                    | `.net`                                      |
| XML utilities              | `:gdx`                                                    | `.utils.XmlReader`, `.utils.XmlWriter`      |
| Localization utilities     | `:gdx`                                                    | `.utils.I18NBundle`, `.utils.TextFormatter` |
| Base64 utilities           | `:gdx`                                                    | `.utils.Base64Coder`                        |
| LZMA compression utilities | `:gdx`                                                    | `.utils.compression`                        |
| Test suite                 | /                                                         | `tests/*`                                   |

<details>
<summary>Some removals also affect the remaining APIs.</summary>

- With the removal of Scene2D, `ScissorStack` is relocated from `com.badlogic.gdx.scenes.scene2d.utils` to `com.badlogic.gdx.graphics`, and `SkinLoader` (as well as the skin / i18n asset support in `AssetManager`) is removed.
- With the removal of the networking API, the network-related methods of `Pixmap` are removed as well. `Gdx.net`, `Application#getNet()`, and the `Net` implementations of each backend are also removed.

</details>

### ⚙️ 2. Modified Features

| Modified Feature          | Affected Artifact   | Details                                                       |
| :------------------------ | :------------------ | :------------------------------------------------------------ |
| ANGLE native packaging    | `:gdx-lwjgl3-angle` | Natives are repackaged into the LWJGL-style layout `<os>/<arch>/angle/`, and `ANGLELoader` is updated accordingly. See [libgdx/libgdx #7822](https://github.com/libgdx/libgdx/pull/7822). |

### 🔨 3. Build and Others

| Change               | Description                                                                 |
| :------------------- | :-------------------------------------------------------------------------- |
| Maven coordinates    | Artifacts are published under the group ID `com.amilego.gdx`, with versioning tracking upstream libGDX. |
| CI and publishing    | The build-and-publish workflow is adjusted for the AmiLego organization. |
| POM metadata         | SCM and developer metadata now point to `AmiLego/libgdx`. |

## Licensing

This fork respects the original license: [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0). Thank you libGDX contributors!

<br>

---

> [!NOTE]
> 
> The content below is the raw README of the upstream repository libgdx/libgdx.

---

<br>

![libGDX Logo](libgdx_logo.svg#gh-light-mode-only)
![libGDX Logo](libgdx_logo_dark.svg#gh-dark-mode-only)

[![GitHub Actions Build Status](https://img.shields.io/github/actions/workflow/status/libgdx/libgdx/build-publish.yml?branch=master&label=GitHub%20Actions)](https://github.com/libgdx/libgdx/actions?query=workflow%3A%22Build+and+Publish%22)

[![Latest Version](https://img.shields.io/maven-central/v/com.badlogicgames.gdx/gdx?label=Version)](https://search.maven.org/artifact/com.badlogicgames.gdx/gdx)
[![Snapshots](https://img.shields.io/maven-metadata/v?metadataUrl=https%3A%2F%2Fcentral.sonatype.com%2Frepository%2Fmaven-snapshots%2Fcom%2Fbadlogicgames%2Fgdx%2Fgdx%2Fmaven-metadata.xml&label=Snapshots)](https://central.sonatype.com/repository/maven-snapshots/com/badlogicgames/gdx/gdx/maven-metadata.xml)

[![Discord Chat](https://img.shields.io/discord/348229412858101762?logo=discord)](https://libgdx.com/community/discord/)

## Cross-platform Game Development Framework
**[libGDX](https://libgdx.com) is a cross-platform Java game development framework based on OpenGL (ES), designed for Windows, Linux, macOS, Android, web browsers, and iOS.** It provides a robust and well-established environment for rapid prototyping and iterative development. Unlike other frameworks, libGDX does not impose a specific design or coding style, allowing you the freedom to create games according to your preferences.

## Open Source, Feature Packed, and Fostering a Large Third-Party Ecosystem
libGDX is released under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0.html), offering unrestricted usage in both commercial and non-commercial projects. While not mandatory, we appreciate any credit given to libGDX when you release a game or app using it. Check out our [showcase](https://libgdx.com/showcase/) for a selection of popular libGDX-powered games. With libGDX, you gain access to a comprehensive set of tools and features to develop multi-platform 2D and 3D games using Java.

Moreover, libGDX boasts a vibrant third-party ecosystem, with numerous [tools](https://libgdx.com/dev/tools/) and libraries that streamline development tasks. Explore the [awesome-libgdx](https://github.com/rafaskb/awesome-libgdx#readme) repository for a curated list of libGDX-centered libraries, serving as an excellent starting point for newcomers in the libGDX community.

![](https://libgdx.com/assets/images/index_showcase/game0.png)
###### An example game created with libGDX: [Pathway](https://store.steampowered.com/app/546430/Pathway/) by Robotality. Discover more captivating games in our [Showcase](https://libgdx.com/showcase/).

## Getting Started with libGDX / Documentation
Thanks to Gradle, you can easily set up libGDX without the need to download the framework itself. Your favorite build tool can handle everything for you. Additionally, we offer a convenient [setup tool](https://libgdx.com/dev/#how-to-get-started-with-libgdx) that automates project creation and downloads all the necessary components. Check out our **[website](https://libgdx.com/wiki/start/setup)** for instructions on getting started or refer to our comprehensive **[wiki](https://libgdx.com/wiki/)**.

- [Creating a libGDX Project](https://libgdx.com/wiki/start/setup)
- [Building a Simple Game](https://libgdx.com/wiki/start/a-simple-game)
- [Tutorials & Demos](https://libgdx.com/wiki/start/demos-and-tutorials)

We provide the libGDX [javadocs](https://javadoc.io/doc/com.badlogicgames.gdx) online for easy reference. Additionally, the javadocs are bundled with every libGDX distribution, ensuring smooth integration with your preferred IDE.

## Community & Contribution
Stay up to date with the **latest libGDX news** by following our [blog](https://libgdx.com/news/). For engaging discussions and support, join our official [libGDX Discord](https://libgdx.com/community/discord/).

### Reporting Issues
Use the **[Issue Tracker](https://github.com/libgdx/libgdx/issues)** here on GitHub to report any issues you encounter. Before submitting, please read our [Getting Help](https://libgdx.com/wiki/articles/getting-help) guide, which walks you through the process of reporting an issue effectively.

### Contributing to the Codebase
libGDX benefits greatly from contributions made by our dedicated developer community. We appreciate any assistance in making libGDX even better. Check out the [CONTRIBUTING.md](https://github.com/libgdx/libgdx/blob/master/.github/CONTRIBUTING.md) file for details on how to contribute. Note that contributing involves working directly with libGDX's source code, a process that regular users do not typically undertake. Refer to the [Working with the Source](https://libgdx.com/dev/from-source/) article for guidance.

You can also support our infrastructure (build server, web server, test devices) by contributing financially through our [Patreon](https://patreon.com/libgdx)!
