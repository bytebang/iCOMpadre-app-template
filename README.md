# iCOMpadre App Template

Create a repository from this GitHub template to start a standalone iCOMpadre app. The included GitHub Actions workflow builds the app and its documentation into an SD-card package.

## Start developing

1. On GitHub, select **Use this template** and create a repository for your app.
2. Update this README, `mkdocs.yml`, `docs/index.md`, and `sdcard/index.html` with your app's name and purpose.
3. Adapt or remove the example files in `sdcard/` and write the user documentation in `docs/`.
4. Push a commit to `main`, or run **Build SD card app** manually from the repository's Actions tab.

The app name is taken from the GitHub repository name. If `sdcard/main.lua` exists, the workflow replaces `APP_NAME` in its first-line app marker with that name. Keep the marker as the first line so iCOMpadre can identify the running app.

The workflow copies `sdcard/` into `/<repository-name>/` on the SD card and builds `docs/` into `/<repository-name>/docs/`. Source documentation stays in `docs/`; only the generated site is packaged.

## Starter structure

```text
<repository-name>/
├── .github/
│   └── workflows/
│       └── build.yml
├── README.md
├── mkdocs.yml
├── docs/
│   └── index.md
└── sdcard/
    ├── index.html
    └── main.lua
```

The HTML page is optional for Lua-only apps. The Lua program is optional for browser-only apps. Remove whichever example files your app does not need.

## Build locally

Install Python 3 and MkDocs, then build and validate the documentation:

```sh
python -m pip install mkdocs
mkdocs build --strict
```

The GitHub Actions workflow performs this documentation build, assembles the SD-card folder, and publishes it as the **`sdcard-<repository-name>`** artifact. Download the artifact from a successful workflow run and extract its contents to the SD card root.

For app behavior and the `main.lua` start mechanism, see the [iCOMpadre PROGRAM mode documentation](https://github.com/bytebang/iCOMpadre/blob/main/docs/operating-modes/program.md).
