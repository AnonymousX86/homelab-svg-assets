# Adding a new icon

Most of this is taken from the [CONTRIBUTING.md](https://github.com/simple-icons/simple-icons/blob/develop/CONTRIBUTING.md) file from the [Simple Icons](https://simpleicons.org/) project

## 1. Get software

1. Download [Inkscape](https://inkscape.org/). It's free for Windows, Mac, and Linux.
1. Install [svgo](https://github.com/svg/svgo) (this is used to optimize SVGs)
1. Install `scour` on Linux (not sure if this is needed on Windows or Mac)
    - Arch = `sudo pacman -S scour`
    - Ubuntu = `sudo apt-get install python3-scour`

## 2. Setup Inkscape

You only need to do this once:

1. `Edit-->Preferences-->Behavior-->Transforms-->Scale stroke width` = Enabled

## 3. Identify logo

When possible, logos should be sought from official sources first, only then falling back on unofficial sources. The order below should be the preferred order.

1. About pages, Press pages, Media Kits, and Brand Guidelines (example [here](https://github.com/logos) and [here](https://www.hashicorp.com/brand))
1. Website images (example [here](https://gohugo.io/))
1. GitHub repositories (example [here](https://github.com/kubernetes/kubernetes/blob/master/logo/logo.svg))
    - If the main project repo doesn't contain any images, be sure to check for a repo that contains a project website (example [here](https://github.com/lxc/linuxcontainers.org/blob/master/static/img/containers.svg)) or a repo that specifically contains branding and logos (example [here](https://github.com/miniflux/logo/blob/master/icon.svg))
1. Wikipedia (example [here](https://en.wikipedia.org/wiki/OpenZFS))

## 4. Adding an icon

1. Open each file with Inkscape
1. Resize the document and viewbox to 48x48
1. Select all elements of the icon and create a group (this helps during resizing/alignment)
1. Resize the icon to 48x48px (ensuring to retain ratio)
1. Center the icon on page both horizontally and vertically (the icon should be touching at least two sides of the document now)
1. Clean up document (`File--->Clean Up Document`)
1. Save the SVG file to the `assets` directory
    1. Be sure to use `Optimized SVG` filetype
    1. On the `SVG Output` tab, check box `Enable viewboxing`

## 5. Name the icon

Each icon will have two names:
- A filename (e.q., `filename.svg`)
- A display name

Adhere to the following rules when choosing filenames:

1. Use the lowercase [ISO basic Latin alphabet](https://en.wikipedia.org/wiki/ISO_basic_Latin_alphabet) with no whitespaces.
   | Correct                 | Incorrect               |
   |-------------------------|-------------------------|
   | `github.svg`            | `GitHub.svg`            |
   | `microsoftedge.svg`     | `microsoft edge.svg`    |
1. Replace symbols in the brand name with their spelled-out words.
   | Correct                 | Incorrect               |
   |-------------------------|-------------------------|
   | `cplusplus.svg`         | `c++.svg`               |
   | `diagramsdotnet.svg`    | `diagrams.net.svg`      |
1. Use a dash (`-`) to indicate a separate version of the icon.
   ```
   bash-dark.svg
   bash-light.svg
   ```
1. When a brand is part of the product name, use it in the filename.
   | Correct                 | Incorrect               |
   |-------------------------|-------------------------|
   | `apachesolr.svg`    | `solr.svg`              |

## 6. Optimizing an icon

1. Run `svgo` to optimize the image (the default settings are fine) 
   ```
   svgo assets/filename.svg
   ```

## 7. Annotating an icon

Manually check each icon to ensure it has these settings:

- The SVG namespace
    ```
    xmlns="http://www.w3.org/2000/svg"
    ```
- A 48x48 viewbox
    ```
    viewBox="0 0 48 48"
    ```

Below is a partial example of a file.
```
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 48 48">...</svg>
```


## 8. Updating the README

Add the icon to the table in `README.md` using the following guidelines:

1. Use alphabetical order by the display name (not the filename)
1. The display name can have symbols (e.g., `C++` or `Diagrams.net`)
1. Separate version of the icon should have descriptive display names (e.g., `Bash (dark)` and `Bash (light)`)
1. The display name should be stylized as per the brand's requirements (e.g., `ownCloud` instead of `OwnCloud`)
1. The display name can have more information about the icon (e.g., the Linux penguin's name is Tux!)