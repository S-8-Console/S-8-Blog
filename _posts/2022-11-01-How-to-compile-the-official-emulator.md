---
title: How to compile the official S-8 emulator
date: 2022-11-01 17:54
categories: [other, compiling]
tags: [official-emulator, compiling]
---

## Foreword

In this guide I will expect you to have some basic knowledge about the command line/terminal.


## Why would you compile it yourself?

Well there are multiple reasons to compile the official S-8 emulator yourself I'll name a few here:

* You want to mod the existing emulator
* There is no official download for your operating system
* You want to challenge yourself

There are much more reasons for you to wanting to compile the official emulator, let's just get into the action!


## Requirements

To be able to follow this tutorial fluently you must have the following dependencies installed on your system:

* A stable rust version.
* Git
* SDL2

If you don't have any of these installed, don't worry! Let's go over them one by one and install each dependency.

### Install rust

To install rust you can simply go to the [official website](https://www.rust-lang.org/tools/install) and follow the instructions.

### Install Git

Installing git isn't as easy. That's why I have got intructions for each major operating system here:

#### Mac

On mac you can easily install git using the command line with a tool called [brew](https://brew.sh/) all you have to do is enter this in your terminal:

```bash
brew install git
```

And it will be installed for you.

#### Linux

On linux you can easily install git using your respective package manager. For ubuntu this would for example be:

```bash
sudo apt install git
```

An alternative would be to install [brew](https://brew.sh/) and install git via brew with this command:

```bash
brew install git
```

#### Windows

For windows you have to install the [gitforwindows](https://gitforwindows.org/) installer, and you'll have git!

### Install SDL2

Installing sdl2 is the most complex of all but still easy!

#### Mac

On mac you can easily install sdl2 using brew:

```bash
brew install sdl2
```

#### Linux

Depending on your package management tool, run the following command in your terminal to install SDL2 on Linux:

apt:
```bash
sudo apt-get install libsdl2-dev
```

dnf:
```bash
sudo dnf install SDL2-devel
```

yum:
```bash
yum install SDL2-devel
```


#### Windows

* Download MSVC development libraries from http://www.libsdl.org/ (SDL2-devel-2.0.x-VC.zip).

* Unpack SDL2-devel-2.0.x-VC.zip to a folder of your choosing (You can delete it afterwards).

* Copy all lib files from ```SDL2-devel-2.0.x-VC\SDL2-2.0.x\lib\x64\```

To your library folder of choice, if you installed rust with rustup that is:

```
C:\Users\{Your Username}\.rustup\toolchains\{current toolchain}\lib\rustlib\{current toolchain}\lib
```

* Copy SDL2.dll from ```SDL2-devel-2.0.x-VC\SDL2-2.0.x\lib\x64\```

to anywhere you like, you will need it later.

## Finally compiling!

Finally! Now that you got all of the required dependencies on your system. We can finally start compiling the program!

First we will need to clone the s-8-core and the s-8-desktop repository from github.

We can easily do this by running these commands:


For s-8-core
```bash
git clone https://github.com/s-8-console/s-8-core
```

For s-8-desktop
```bash
git clone https://github.com/s-8-console/s-8-desktop
```

You probably don't know what these 2 repositories do. Don't worry, I'll explain it!

The S-8-Core repository handles the core calculations and operations for the S-8 console, let's call it the backend.

The S-8-Desktop repository handles the rendering and the interpetation of everything that S-8-Core has done, this could be like the mapping of colors or how big the screen is scaled. Let's call it the frontend.

Now that we have acquired that knowledge, let's finally compile!

### For Mac And Linux

The mac and linux users can just go into the s-8-desktop directory and execute the cargo project like this:

Go into the s-8-desktop directory
```bash
cd s-8-desktop
```

Execute the project with the example roms!
```bash
cargo run roms/pineapple-pizza/GAME_ROM roms/pineapple-pizza/SPRITE_ROM roms/FONT_SET
```

If you get an error saying it can't find a dependency called s-8-core, then you'll have to edit the cargo.toml file and change the path from the s_8_core dependency to the corresponding folder with the s-8-core repository, as shown here:

```toml
s_8_core = {path = "../s-8-core" }
                    ____________
                         |
                         |
           This path-----
```

### For Windows

The Windows users have to go into the s-8-desktop directory include the SDL2.dll file in that directory.

After that you can go into the s-8-desktop directory in your terminal, and execute the s-8-emulator with the example roms!


Go into the s-8-desktop directory
```bash
cd s-8-desktop
```

Execute the cargo project with the example roms:

```bash
cargo run roms/pineapple-pizza/GAME_ROM roms/pineapple-pizza/SPRITE_ROM roms/FONT_SET
```

And BAM! That's it, you have successfully compiled the official S-8-Emulator yourself! Amazing!

## Afterword

Thank you for following my tutorial. I will always take suggestions on how to improve them, if you have a suggestion. Contact me on discord: Stan xD#7662

I hope you'll have a beautiful day!
