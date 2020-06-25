# NeovimJava Docker Image

## What this is

A premade 'environment' for developing java using neovim based on debian slim image, with everything installed and ready to go including language server, neovim, some configs, plugins and more.. A nice stable starting point for writing code using vim.

This image also serves as a template for setting up other neovim based development images, for example, seeing as we have a configured neovim, with CoC completion plugin, we can also install rust for example quite easily and then the cargo pkg mgr etc.

## Why un/optimised versions?

Simply put, we can make python 20% faster with optimisations, but the build time is extended by almost double with this turned on. So I made 2 versions, one with a faster python (optimised version), one with a faster build time (unomptimised version)

## First Things First

- clone this repo to where you want it, or wget/curl just the dockerfile only, as it will be all you need to build the docker image
- `cd` to directory contaning Dockerfile from this repo

## Build/Run the Container

### Build it
`docker build -t "nameToGiveYourContainer:Dockerfile" .`

### Find the ID of your new image
`docker images`

### Run it, launch a shell prompt
`docker run -it --entrypoint /bin/zsh <IDofyournewcontainer>`

## Setting Up Vim

- open vim `nvim`
- note: you will see an error such as "gruvbox not installed", we will install the plugins next step (note I might clone these repos in build on later update to make setup more smooth)
- in neovim hit the : or ; key, and type in `PlugInstall`
- it will now clone all of the packages needed for the plugins located in my vimrc ~/.config/nvim/init.vim
- relaunch vim, plugins should now load
- hit the ; or : key and type :CocInstall <package>
- replace package with coc-java i.e `:CocInstall coc-java` to install the java language server plugin for Coc (completion/language plugin)
- install the following packages using :CocInstall, coc-java, coc-snippets, coc-pairs
- This will install completion for java, snippets support (sysout etc), and autoclosing of pairs (match {} etc)
- Pretty much all the basics!
- next we can test our setup, we should be almost ready to go! (Our java_home is already set using my dockerfile)

## Testing nvim with java language completion and some extra goodies

- try `nvim test.java`
- you will see on the bottom bar, that the java language server is downloading as jlt.ds is not found (first launch only)
- it will download it for you automatically (its the language server from eclipse so lots of similar errors etc)
- once the language server is downloaded were are now ready to roll.

### Goodies

File Browser, command pallette, startup window, better shell

- In normal mode hit \n for a file browser
- In normal mode hit \\\ for a command pallete type thing built on fuzzy finder
- Launch neovim with `nvim` it will load a launch screen with recent files etc
- type `zsh` to launch a better shell with history and tab completions

# Preview Images

![Preview](https://i.ibb.co/7xmh5JV/Screen-Shot-2020-06-24-at-11-00-39-pm.png)
![Preview](https://i.ibb.co/9Nxh3hW/Screen-Shot-2020-06-24-at-11-00-48-pm.png)

