# Meteorite

Installer & smart package manager for Meteor

## Summary

Meteorite makes life easier until Meteor core has it's own smart package installer

## Installation

    npm install -g meteorite

## Command line

Meteorite installs a utility called `mrt` that works just like `meteor` except it

  1) Installs a project specific instance of meteor this first time you run an app

  2) Installs smart package dependencies listed in `smart.json` in the project's meteor instance
  
  3) Installs smart packages recursively if your app uses packages that have their own `smart.json`

  4) Runs the `meteor` command using the project's meteor instance. `mrt` supports all of `meteor`'s subcommands (e.g. `run`, `deploy`, etc). 

  5) Includes a subcommand `mrt install` that runs the installation steps (1-3) without running `meteor`

## Configuration

*Note: We only support git repositories right now. We plan to add the ability to specify a path to a local package also.*

A sample `smart.json`

    {
      "meteor": {
        "branch": "devel"
      },
      "packages": {
        "simple-secure": {
          "git": "https://github.com/possibilities/simple-secure.git",
          "branch": "experimental"
        },
        "demostrap": {
          "git": "https://github.com/possibilities/meteor-demostrap.git",
          "tag": "v0.0.1"
        }
      }
    }

Any dependency listed without specifying a branch, tag or ref will use the repo's master branch. If `meteor` is not specified at all the latest release will be used.

## Usage

Install everything in `smart.json` and run a project-specific copy of `meteor` (*run* is the default and therefore optional)

    mrt run
    
Just install everything listed in `smart.json`, but don't run any underlying `meteor` command

    mrt install

## Contributing

See [Contributing](https://github.com/possibilities/meteorite/wiki/Contributing)
