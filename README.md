# nixos-ninja-system

Tags: Linux, NixOS, Software Development, Tech

This is my NixOS development setup on my MSI Stealth GS5. I'm sure this will work on most gaming laptops with some changes to accomodate for AMD hardware.

---

[2023-07-28 10-55-42.mp4](nixos-ninja-system%2050a5c92fc2de44cfa2beb4ba16efd3fb/2023-07-28_10-55-42.mp4)

![https://raw.githubusercontent.com/mike-ninja/ninja-nixos-setup/main/assets/overview.png](https://raw.githubusercontent.com/mike-ninja/ninja-nixos-setup/main/assets/overview.png)

---

![setup.png](https://raw.githubusercontent.com/mike-ninja/ninja-nixos-setup/main/assets/setup.png)

---

## Why NixOS? 🤓

So far, this is my second linux distro that I have delved into. The first one being Artix linux, which gave you this independence from systemd init system if you wished for it. Artix, since being within the same family as the Arch distro, also used the AUR package manager and from my experience, it is a pretty solid package-manager. So, now here is one of the biggest difference that me as a linux noob have come to appreciate with NixOS, and that is it’s one location where all the config files of the system is store. Meaning, no more getting lost on where a certain system config files can be located, now it’s all located in one file that configures everything! This approach allows for easier replication and my personal opinion, easier management.

## Who is this for? 🤔

I reckon this guide/setup is good for those who have played around in different linux distro’s but never found a way to independently setup their own system. I have kept the packages at a minimum, but ready enough for you to configure your own and start developing projects in.

## Step by Step Guide 📚

### Step 1: Installation 🔧

- **USB image**
    - Download a Minimal ISO Image at [LINK](https://nixos.org/download.html).
    - Create bootable USB using your favorite tool. So far, I have been using rufus for these kinds of jobs. Download rufus at [LINK](https://rufus.ie/en/).
- **Set up NixOS**
    - Follow manual installation guide. If you have made it this far, I’m pretty sure you can manage that. Installation guide at [LINK](https://nixos.org/manual/nixos/stable/index.html#sec-installation-manual).

### Step 2: Configuration ☑️

- **Clone Files**
    
    ```bash
    git@github.com:mike-ninja/ninja-nixos-setup.git
    ```
    
- **Tweak configuration.nix**
    
    ```bash
    # ...
    networking.hostName = "ninja-nixos";
    # ...
    ```
    
    ```bash
    
    # ...
    time.timeZone = "Europe/Amsterdam";
    # ...
    ```
    
    ```bash
    # ...
    users.users.ninja = {
    	isNormalUser = true;
    	extraGroups = [ "wheel" ];
    };
    # ...
    ```
    
- **Distribute Files (Will make a script for this at some point)**
    
    ```bash
    cd ninja-nixos-setup
    
    sudo cp configuration.nix /etc/nixos/
    
    sudo cp -r .config/* ~/.config
    ```
    

### Step 3: Rebuild Nix Package ⚙️

- Rebuild the system with new configuration.nix
    
    ```bash
    sudo nixos-rebuild switch
    ```
    
- Run Hyprland
    
    ```bash
    Hyprland
    ```
    

## Conclusion ✅

Hopefully everything was successful in your installation. I also want to remind that this installation will require some familarity with linux systems and using the terminal. In addition, I have not configured anything to initialize Hyprland at startup. I’ll leave that up to you to set up. Thanks and Enjoy!

### Packages Included 📦

- List
    
    ```bash
    vim
    neovim
    wget
    git
    kitty
    cargo
    waybar
    dunst
    libnotify
    rofi-wayland
    brightnessctl
    pciutils
    htop
    firefox-wayland
    networkmanagerapplet
    unzip
    gcc
    nushell
    nodejs
    ripgrep
    pavucontrol
    discord
    obs-studio
    gimp
    ```