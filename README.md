# Cylc language package for Atom

![Check build](https://github.com/cylc/language-cylc/workflows/Check%20build/badge.svg?branch=master&event=push)

An Atom extension that provides language support for Cylc workflow configuration files.

## Features

Syntax highlighting:
- Cylc 7
- Cylc 8
- ISO 8601 datetimes
- Jinja2 (can be used with a Jinja extension e.g. [atom-jinja2](https://atom.io/packages/atom-jinja2))

Check [here](https://github.com/cylc/cylc-flow/issues/2752) for info on supported syntax features.

## Installation

Install from the Atom settings, [the Atom website](https://atom.io/packages/language-cylc), or by running `apm install language-cylc`.

By default, only files called `suite.rc` and `suite.rc.processed` (and with the future Cylc 8 extension `.cylc`) will use the package. If you want all `.rc` files to use it: in Atom, go to `Edit > Config...` and add the desired extension to your Atom config file under `core.customFileTypes.source.cylc`, like this:
```cson
"*":
  core:
    customFileTypes:
      "source.cylc": [
        "rc"
      ]
```

## Issues

Please report any syntax highlighting issues at [cylc/cylc-textmate-grammar](https://github.com/cylc/cylc-textmate-grammar/issues). Any other issues with the extension should be reported [here](https://github.com/cylc/language-cylc/issues).

## Contributing

This repo includes the [cylc/cylc-textmate-grammar](https://github.com/cylc/cylc-textmate-grammar) repo as a git submodule. If you don't have experience with submodules, you should [read the docs](https://git-scm.com/book/en/v2/Git-Tools-Submodules) first.

The cylc-textmate-grammar repo contains a JSON TextMate grammar file which is used by Atom for syntax highlighting (after running the build process, see below). Read the [Atom guide on creating a TextMate grammar](https://flight-manual.atom.io/hacking-atom/sections/creating-a-legacy-textmate-grammar/) for more information. **Note:** do not edit the JSON file when contributing; instead you should edit the JavaScript grammar file and build it, as explained in the [contributing](https://github.com/cylc/cylc-textmate-grammar#contributing) section of cylc-texmate-grammar.


To install a development copy of the package:
```
git clone --recurse-submodules https://github.com/cylc/language-cylc.git
cd language-cylc
apm link --dev
```
The `--recurse-submodules` option automatically initialises the cylc-textmate-grammar submodule. `apm link --dev` symlinks the clone to `~/.atom/dev/` so that it is loaded when you run Atom in dev mode:
```
atom --dev .
```

You can then edit the `/cylc-textmate-grammar/src/cylc.tmLanguage.js` grammar file. First, [read the contributing section](https://github.com/cylc/cylc-textmate-grammar#contributing) of the cylc-textmate-grammar repo - any such edits will be part of that repo as opposed to this vscode-cylc repo. After editing & saving the file, there is an npm build script:
```
npm run build
```
This will run the cylc-textmate-grammar build script which compiles the JSON grammar file, then copies it into `./grammars/cylc.json`. Reload the dev window using <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>F5</kbd>.


Contributions to Atom-specific features are to be made in this repo, not the submodule.
