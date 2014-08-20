# Synopsis

A command line utility to ease the `link`-ing of local bower modules
Almost completely based on and fully compatible with npm-workspace by Mario Casciaro.

## Install

```
npm install -g bower-workspace
```

## Configure workspace links

Create a `workspace.json` in your workspace dir, and create mappings `module name -> module dir`
```sh
{
  "links": {
    "prj2": "prj2",
    "prj3": "prj3"
  }
}
```

Then

### To install and link everything in your workspace
```sh
cd myBowerWorkspace
bower-workspace install
```

### To install and link only one module
```sh
cd myBowerWorkspace/prj1
bower-workspace install
```

### To clean your workspace (remove all bower_components directories)
```sh
cd myBowerWorkspace
bower-workspace clean
```

## Package an app for deployment

When you are ready to deploy your app, you can package all your modules for production, including all your private/local only modules. Just use these 3 options:

* `-c`: Copy the packages into `bower_components` instead of linking them
* `-g`: Remove `.git` directories from dependencies while copying. This is so you can package your production app under a new repo (e.g. for use in a PaaS)
* `-p`: Installs only production dependencies (ignores `devDependencies`)

__Example__
```sh
cd myNodeJsWorkspace/yourapp
bower-workspace install -cgp
```

Your app is now ready for deployment.
