# Cylc language package for Atom

An Atom extension that provides language support for Cylc workflow configuration files.

## Features

Syntax highlighting:
- Cylc 7
- Cylc 8
- ISO 8601 datetimes
- Jinja2 (can be used with a Jinja extension e.g. [atom-jinja2](https://atom.io/packages/atom-jinja2))

Check [here](https://github.com/cylc/cylc-flow/issues/2752) for info on supported syntax features.

## Installation

Currently, the only way to install is to clone the repository into your `.atom/` directory:
```
cd `~/.atom/`
git clone --recurse-submodules https://github.com/cylc/language-cylc.git
```
Note the `--recurse-submodules` option is necessary. Downloading the source repository as a ZIP won't work.

Then, in Atom, go to `Edit > Config...` and add the desired suite file extensions to your Atom config file under `core.customFileTypes.source.cylc`, like this:
```cson
"*":
  core:
    customFileTypes:
      "source.cylc": [
        "cylc"
        "rc"
      ]
```

## Issues

Please report any syntax highlighting issues at [cylc/cylc-textmate-grammar](https://github.com/cylc/cylc-textmate-grammar/issues). Any other issues with the extension should be reported [here](https://github.com/cylc/language-cylc/issues).

## Contributing

This repo includes the [cylc/cylc-textmate-grammar](https://github.com/cylc/cylc-textmate-grammar) repo as a git submodule. If you don't have experience with submodules, you should [read the docs](https://git-scm.com/book/en/v2/Git-Tools-Submodules) first.

The cylc-textmate-grammar repo contains a JSON TextMate grammar file which is used by Atom for syntax highlighting (symlinked to by `/grammars/cylc.json`). Read the [Atom guide on creating a TextMate grammar](https://flight-manual.atom.io/hacking-atom/sections/creating-a-legacy-textmate-grammar/) for more information. **Note:** do not edit the JSON file when contributing; instead you should edit the JavaScript grammar file and build it, as explained in the [contributing](https://github.com/cylc/cylc-textmate-grammar#contributing) section of cylc-texmate-grammar. Any edits will be part of that repo as opposed to this repo.

On the other hand, any contributions to Atom-specific features are to be made in this repo, not the submodule.
