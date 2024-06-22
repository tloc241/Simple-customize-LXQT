# Simple-customise-lxqt
#Preview

![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/913a85fc-67e8-457e-a30f-6d0c2655fb5c)

Custom DE dont have to install or download too much app
## Index

- [1. Debian & Lubuntu](#Debian-and-Lubuntu)
  - [1.1. Custom grub select menu](#Custom-grub-select-menu-debian)
  - [1.2. Change lxqt boot logo](#Change-lxqt-boot-logo-debian)
  - [1.3. Change lxqt lock screen](#Change-lxqt-lock-screen-debian)
  - [1.4. Customise in the main desktop](#Customise-in-the-main-desktop-debian)
  - [1.5. Troubleshoot](#Troubleshoot-debian)
- [2. Arch](#Arch)
  - [2.1. Custom grub select menu ](#Custom-grub-select-menu-arch)
  - [2.2. Change lxqt boot logo](#Change-lxqt-boot-logo-arch)
  - [2.3. Change lxqt lock screen](#Change-lxqt-lock-screen-arch)
  - [2.4. Customise in the main desktop](#Customise-in-the-main-desktop-arch)
  - [2.5. Troubleshoot](#Troubleshoot-arch)
 
## Debian and Lubuntu

I'm really recommend you to install Nala, Nala can be alot faster compare to apt, to install Nala you can open terminal by ctrl+alt+t, then you ctrl +c this line: `sudo apt install -y nala` and press enter.

It'll ask for password (bcs you use sudo) just type in and enter again. For now on much of command that have 'apt', 'apt-get' can replace with nala (add-apt can't replace bcs it add repo so you can install with nala ok)
### Custom grub select menu (debian)
To custom grub you have to install grub customizer. To install simply open terminal (ctrl+alt+t) and type: 
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo nala install -y grub-customizer
```
and it will done the job for you.
After it done doing it thing, you press 'super key / windows key' on you keyboard and search for grub customizer and open it. 
#### At here you can change name and add more custom boot
![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/c52de175-83f8-44aa-a003-3c706324d447)

At default, Lubuntu have an Ubuntu name, you can simply by double left click to the tile, after changing you have to type the save button on the top left of the windowx.
To customise the GUi you can do it here to, but much of the time it won't work so i gonna tell you an alternative/manual way

First, go to gnome-look.org, then go to search bar and search for grub theme, at there you can find the theme that favor your eyes 

After download it, you have to add it into a config file, this is how you do it:

1. Open file manager, then ctrl + l show you can change the directory,
2. Type `/usr/share/grub/themes/`
3. In there press ```f4``` on your keyboard, it'll show up a terminal
4. Type `cd ~/Downloads`, you can open another file manager and go to Downloads and extract to themes you just download of simply extract it through terminal by `upzip <file name>`, then `ls` to show your file name.
5. After extract you have to type this: `sudo mv <folder you just extract> /usr/share/grub/themes` .
6. Type this in file manager directory: `etc/default/grub.d/` and find a `grub-theme.cfg` file, open it up.
7. At here you have to change the line below: `/usr/share/grub/themes/<your theme name>/theme.txt` ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/f421f6b3-d7ca-43af-8518-13ec7ce47625)
8. Open terminal and type: `sudo update-grub` and now you can `reboot` and enjoy your new grub UI now. ![IMG_20240506_180823_353](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/0ba5caf6-412d-4519-bc20-db50ce799a50)

Bonus: to change icon you have two way of doing that

Option 1. Go to icons folder of your theme then open it with gimp (`sudo nala install -y gimp`) and drag your picture into it and save it by ctrl shift e and close it, it'll show warning, just discard it.

Option 2: 
1. Go to `/boot/grub/` and find `grub.cfg` find, make a backup of that file. After that open it with featherpad or nano depend on you
2. find the line that have menuentry in it then you add `--class` to it like the image below 

![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/0c7c262c-a969-4cce-9a7e-48662cf9c8e7)

After that remember to save it, and that all

**Don't 'sudo update-grub, it will reset everything you had made**

![lol](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/1351abb9-ffd3-4a04-934f-c6e5b632ddd5)

### Change lxqt boot logo (debian)

1. To change this you have to install plymouth, just simply type: `sudo nala install -y plymouth`

2. After install it go to gnome-look.org and type plymouth theme to download. I'm highly recommend you to check [this](https://www.gnome-look.org/p/2106821) out
3. Done download go to extract it, now you file this directory: `/usr/share/plymouth/themes`
4. press f4 to open terminal, now move your file to it by: `cd ~/Downloads` , then `ls` (it help you to find the folder name)
5. now type `sudo mv <your folder name> /usr/share/plymouth/themes`
6. now open file manager and go to `/usr/share/plymouth/themes` and find the file name `default.plymouth`
7. change the line `ImageDir` to the path of your folder 

![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/aece6579-3881-44c1-b3e6-82c1c6e43732)

or use this commandline:{ ### *my-plymouth-theme* should be replaced with the theme-name which you downloaded (without the **)

```
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/*my-plymouth-theme*/*my-plymouth-theme*.plymouth 120
```

 With this command, you need to select the theme `sudo update-alternatives --config default.plymouth`

8. type this in terminal `sudo update-initramfs -u -k all`

And that all, enjoy your custom boot logo 

![Screenshot_20240514-143641](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/85339a72-a3cf-410f-8c61-7349fae0adff)

### Change lxqt lock screen (debian)

LXQT use sddm at is lock screen so it can be change as well, unfortunally, i only capable to make [MarianArlt sddm](https://github.com/MarianArlt/sddm-sugar-dark) work, other sddm lock sreen you found on gnome-look might not work, and i don't know how to fix it either, sr

1. Download sddm theme, like i said above only MarianArlt themes work, some [MarianArlt](https://github.com/MarianArlt/sddm-sugar-dark) alternative also work, you can check out [sugar dark](https://github.com/MarianArlt/sddm-sugar-dark), [sugar candy](https://github.com/Kangie/sddm-sugar-candy), [the-zero885 lubuntu-sddm-theme](https://github.com/the-zero885/lubuntu-sddm-theme).
2. extract the file you just download, and move it to sddm folder:
```
/usr/share/sddm/themes
cd ~/Downloads
ls
sudo mv <folder name> /usr/share/sddm/themes
```
3. If you using lxqt on lubuntu like mine, just rename ubuntu-theme folder (for backup resson) :
```
cd /usr/share/sddm/themes/
sudo mv ubuntu-theme ubuntu-theme-bakcup
```
If you using lxqt in other distro just rename lubuntu folder: 
```cd /usr/share/sddm/themes/
sudo mv lubuntu lubuntu-bakcup
```
4. Now `rename` your theme folder to ubuntu-theme / lubuntu theme depend on your distro
5. `log out` to see if it work 

![Screenshot_20240514-145923](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/b7b809f4-3b01-4920-b165-612b96fcd641)

### Customise in the main desktop (debian)
![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/86fb4823-877e-4603-9556-e939a0de78db)

*Install Ulauncher :*
1. just type in terminal `sudo nala install -y ulauncher` and it'll do it thing, if it fail just add respo `sudo add-apt-repository universe -y && sudo add-apt-repository ppa:agornostal/ulauncher -y`
2. Now open ulauncher, it will show up a searchbar look on the righ, you see to wheel thing, click into it, it'll show this GUI ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/dc4a9162-af90-4d90-bf8f-6050e75669c9)
3. click to `launch at login` and close it

**Optional:**
1. To change theme you have to download ulauncher theme (https://www.pling.com/p/1995620)
2.  then go to `~/.config/ulauncher` (if it don't show up just open it angain and f5)
3. `Move` your themes to there, and `rename` it to user-themes
4. go back to ulauncher app, go to color themes and change to your themes just add

*Install Plank*
1. Type in terminal: `sudo nala install -y plank` and wait
2. After it done, try to open to by typing in terminal plank
3. if it work now you can change it thing, do the same thing in below picture
![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/8d61e216-26f4-42ba-92bb-e097b90fb2c6)![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/2362b38f-4681-4948-b51a-2b380b29c6c1)
4. to make plank auto start when login you have to `open session setting`
5. go to `autostart` tab
6. press `add` button
7. name it plank, command also plank
8. press ok and close it

*Panel*
1. Go to this website of [the author](https://www.pling.com/p/1995620)
2. After download it, extract it
3. open another file manager and go to `~/.config/lxqt/` and change panel.conf file name to `panel-00.conf`
4. move the `panel.conf` you just download in `~/.config/lxqt/`
5. log out to see if it work or not

**Optional:** *Add transparancy to panel*
1. tick on background color, and set opacity to below 70% 

![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/a68dd22d-7960-455d-85dd-e11e0ccf3ebb)

In case you want to make the panel smaller, this is how:
1. open up the `panel.conf` file in `~/.config/lxqt/`
2. then open that file up, look for line `width` ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/f7c796c5-3fab-4523-aa0f-a99be4cce705)
3. now save it. log out to check does it work or not.

**Make sure to turn on compton** (if you don't have compton, just install it: `sudo nala install -y compton`)
1. set compton to auto run, to do that you have to `open session setting`
2. go to `autorun` tab
3. `add` compton to it (similar to plank)

**Optional** *Windows and tilling themes*
*Change windows themes*

At default, LXQT have a few collection of palette for you to choice. But none of those fit your taste, here is how to add more palette into:
1. you have to `download` a theme, you can check [this](https://www.pling.com/p/2119028/) if your want.
2. `extract` the zip file you just get
3. `copy` that file to `~/.local/share/lxqt/` (if the lxqt folder does not exist, create it first)
noite: if you download the theme i put above, the one you have to move is `Breeze-Lxqt`
4. after moving it, you have to `open` it up. It must of the time have 2 folder. you have to move all of the file outside it, like this: ![screen54](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/dca0d99a-23a8-4946-a72b-821bf1bc1b90)
5. now you can go to `Appearance` and change to the new palette you just add by pressing `load palette`

*Change system title bar*
1. found the one you like, you can check [this](https://www.gnome-look.org/p/1755582)
2. `extract` it, and move it to `/usr/share/themes/`
3. now search for `openbox setting` and change it to the theme you just add

LXQT also have picom preinstall, but you cant config it, you have to config it throught compton: `~/.config/compton.conf`

*install tiling windows*
1. navigate to `~/.config/openbox/rc.xml`, make a `backup` of this file
2. open this file with featherpad or nano
3. add this thing to this place ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/e76929a3-c491-4e10-8705-53ab6dae0eb2)

(at middle keyboard and keybind) copy all in tiling.txt file to `rc.xml`

4. save it
5. Run command in terminal to reconfigure openbox for the shortcut to take effect. `openbox --reconfigure`

**Optional** *Change icons themes*
1. `Install` icon themes, highly recommend [this](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme) `sudo nala install papirus-icon-theme`
2. Now open `appearences` and go to `icon themes`, change to the one you just done install

**Optional** *Change terminal theming.*

LXQT use Qterminal at it main (it also have xterm preinstall), xterm is a no go, Qterminal in the other hand pretty good at customize. But if you want to flexing to people online using neofetch then i recommend you switch to xfce4-terminal. The resson is Qternimal itselt can't render custom image. 

*Changing theme in Qterminal*
*Changing theme in Qterminal* (if none of the color scheme preinstall don't fit your taste then you can check the below)
1. Qterminal theme is reliant palette so u have to check *Windows and tilling themes* above
2. After you done, `open` up the terminal and go to `file->preferences->appearences->color scheme` and change it to the one you just add
*Changing theme in Xfce4-terminal*
1. `Download` the theme online, i'm highly recommend [this](https://github.com/nordtheme/xfce-terminal/tree/develop)
2. `Extract` the download file, and move it to `~/.local/share/xfce4/terminal/colorschemes/`
3. `open` up xfce4-terminal, go to `edit` tab and chosse `preferences`, go to `colors` and change `presets` to the theme you just add

*Changing font for terminal*
1. `Download` font from the web, [this](https://www.nerdfonts.com/font-downloads) one is really good, expecially the gohu font one
2. `extract` it, and move it to `~/local/share/fonts/` (if it don't have that folder just create it)
3. `open` up your terminal, go to `edit` tab (Qterminal is file tab) and chosse `preferences`,  go to `appearences` and change `font` to the one you just add

Note: If you want your terminal transparent, find the `opacity` thing, and change it to your liking.

### Troubleshoot (debian)

If the panel just disable, try to delete the new one u just add and rename the original one back to normal.

If it still can't fix it then you have to reinstall lxqt desktop (do not worry, it won't earse any of your customization anyway): `sudo apt install --reinstall lubuntu-desktop` (you have to use apt, nala don't work on this)

If it still giving you a problem, then i think you should reinstall gpu driver (no recommend), you can go to this website to install [it.](https://github.com/lutris/docs/blob/master/InstallingDrivers.md)

if you have trouble with extracting file, go to `edit` tab (upper left), go to `preferences`, go to `advanced tab`, in `archiver integration` swicth it to `lxqt-archiver` and it should fix now

if you press `f4` of right-click to open up the terminal but it keep showing up xterm, here is how to fix it: go to `edit` tab (upper left), go to `preferences`, go to `advanced tab`, in `terminal emulator` change it to `qterminal` or anything else you use (EX: xfce4-terminal)
## Arch 
first, install `yay` or `paru` depend on u, if `yay` this [link](https://www.tecmint.com/install-yay-aur-helper-in-arch-linux-and-manjaro/), if `paru` this [link](https://github.com/Morganamilo/paru)
### Custom grub select menu (arch)
To install grub-customizer type:`yay -S grub-customizer`
#### At here you can change name and add more custom boot
![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/c52de175-83f8-44aa-a003-3c706324d447)

At default, Lubuntu have an Ubuntu name, you can simply by double left click to the tile, after changing you have to type the save button on the top left of the windowx.
To customise the GUi you can do it here to, but much of the time it won't work so i gonna tell you an alternative/manual way

First, go to gnome-look.org, then go to search bar and search for grub theme, at there you can find the theme that favor your eyes 

After download it, you have to add it into a config file, this is how you do it:

1. Open file manager, then ctrl + l show you can change the directory,
2. Type `/usr/share/grub/themes/`
3. In there press ```f4``` on your keyboard, it'll show up a terminal
4. Type `cd ~/Downloads`, you can open another file manager and go to Downloads and extract to themes you just download of simply extract it through terminal by `upzip <file name>`, then `ls` to show your file name.
5. After extract you have to type this: `sudo mv <folder you just extract> /usr/share/grub/themes` .
6. Type this in file manager directory: `etc/default/grub.d/` and find a `grub-theme.cfg` file, open it up.
7. At here you have to change the line below: `/usr/share/grub/themes/<your theme name>/theme.txt` ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/f421f6b3-d7ca-43af-8518-13ec7ce47625)
8. Open terminal and type: `sudo update-grub` and now you can `reboot` and enjoy your new grub UI now. ![IMG_20240506_180823_353](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/0ba5caf6-412d-4519-bc20-db50ce799a50)

Bonus: to change icon you have two way of doing that

Option 1. Go to icons folder of your theme then open it with gimp (`yay -S gimp`) and drag your picture into it and save it by ctrl shift e and close it, it'll show warning, just discard it.

Option 2: 
1. Go to `/boot/grub/` and find `grub.cfg` find, make a backup of that file. After that open it with featherpad or nano depend on you
2. find the line that have menuentry in it then you add `--class` to it like the image below 

![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/0c7c262c-a969-4cce-9a7e-48662cf9c8e7)

After that remember to save it, and that all

**Don't 'sudo update-grub, it will reset everything you had made**

![lol](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/1351abb9-ffd3-4a04-934f-c6e5b632ddd5)

### Change lxqt boot logo (arch)
1. To change this you have to install plymouth, just simply type: `yay -S plymouth`

2. After install it go to gnome-look.org and type plymouth theme to download. I'm highly recommend you to check [this](https://www.gnome-look.org/p/2106821) out
3. Done download go to extract it, now you file this directory: `/usr/share/plymouth/themes`
4. press f4 to open terminal, now move your file to it by: `cd ~/Downloads` , then `ls` (it help you to find the folder name)
5. now type `sudo mv <your folder name> /usr/share/plymouth/themes`
6. now open file manager and go to `/usr/share/plymouth/themes` and find the file name `default.plymouth`
7. change the line `ImageDir` to the path of your folder 

![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/aece6579-3881-44c1-b3e6-82c1c6e43732)

or use this commandline:{ ### *my-plymouth-theme* should be replaced with the theme-name which you downloaded (without the **)

```
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/*my-plymouth-theme*/*my-plymouth-theme*.plymouth 120
```

 With this command, you need to select the theme `sudo update-alternatives --config default.plymouth`

8. type this in terminal `sudo update-initramfs -u -k all`

And that all, enjoy your custom boot logo 

![Screenshot_20240514-143641](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/85339a72-a3cf-410f-8c61-7349fae0adff)

### Change lxqt lock screen (arch)
Bcs lxqt ship with sddm out of the box so you don't have to install it
1. Download sddm theme, these are some that i know working: [MarianArlt](https://github.com/MarianArlt/sddm-sugar-dark), [sugar dark](https://github.com/MarianArlt/sddm-sugar-dark), [sugar candy](https://github.com/Kangie/sddm-sugar-candy), [the-zero885 lubuntu-sddm-theme](https://github.com/the-zero885/lubuntu-sddm-theme).
2. extract the file you just download, and move it to sddm folder:
```
/usr/share/sddm/themes
cd ~/Downloads
ls
sudo mv <folder name> /usr/share/sddm/themes
```
3. If you using lxqt on lubuntu like mine, just rename ubuntu-theme folder (for backup resson) :
```
cd /usr/share/sddm/themes/
sudo mv ubuntu-theme ubuntu-theme-bakcup
```
If you using lxqt in other distro just rename lubuntu folder: 
```cd /usr/share/sddm/themes/
sudo mv lubuntu lubuntu-bakcup
```
4. Now `rename` your theme folder to ubuntu-theme / lubuntu theme depend on your distro
5. `log out` to see if it work 

![Screenshot_20240514-145923](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/b7b809f4-3b01-4920-b165-612b96fcd641)
### Customise in the main desktop (arch)
![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/86fb4823-877e-4603-9556-e939a0de78db)

*Install Ulauncher :*
1. just type in terminal `yay -S ulauncher` and it'll do it thing
2. Now open ulauncher, it will show up a searchbar look on the righ, you see to wheel thing, click into it, it'll show this GUI ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/dc4a9162-af90-4d90-bf8f-6050e75669c9)
3. click to `launch at login` and close it

**Optional:**
1. To change theme you have to download ulauncher theme (https://www.pling.com/p/1995620)
2.  then go to `~/.config/ulauncher` (if it don't show up just open it angain and f5)
3. `Move` your themes to there, and `rename` it to user-themes
4. go back to ulauncher app, go to color themes and change to your themes just add

*Install Plank*
1. Type in terminal: `yay -S plank` and wait
2. After it done, try to open to by typing in terminal plank
3. if it work now you can change it thing, do the same thing in below picture
![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/8d61e216-26f4-42ba-92bb-e097b90fb2c6)![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/2362b38f-4681-4948-b51a-2b380b29c6c1)
4. to make plank auto start when login you have to `open session setting`
5. go to `autostart` tab
6. press `add` button
7. name it plank, command also plank
8. press ok and close it

*Panel*
1. Go to this website of [the author](https://www.pling.com/p/1995620)
2. After download it, extract it
3. open another file manager and go to `~/.config/lxqt/` and change panel.conf file name to `panel-00.conf`
4. move the `panel.conf` you just download in `~/.config/lxqt/`
5. log out to see if it work or not

**Optional:** *Add transparancy to panel*
1. tick on background color, and set opacity to below 70% 

![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/a68dd22d-7960-455d-85dd-e11e0ccf3ebb)

In case you want to make the panel smaller, this is how:
1. open up the `panel.conf` file in `~/.config/lxqt/`
2. then open that file up, look for line `width` ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/f7c796c5-3fab-4523-aa0f-a99be4cce705)
3. now save it. log out to check does it work or not.

**Make sure to turn on compton** (if you don't have compton, just install it: `yay -S compton`)
1. set compton to auto run, to do that you have to `open session setting`
2. go to `autorun` tab
3. `add` compton to it (similar to plank)

**Optional** *Windows and tilling themes*
*Change windows themes*

At default, LXQt have a few collection of palette for you to choice. But none of those fit your taste, here is how to add more palette into:
1. you have to `download` a theme, you can check [this](https://www.pling.com/p/2119028/) if your want.
2. `extract` the zip file you just get
3. `copy` that file to `~/.local/share/lxqt/` (if the lxqt folder does not exist, create it first)
noite: if you download the theme i put above, the one you have to move is `Breeze-Lxqt`
4. after moving it, you have to `open` it up. It must of the time have 2 folder. you have to move all of the file outside it, like this: ![screen54](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/dca0d99a-23a8-4946-a72b-821bf1bc1b90)
5. now you can go to `Appearance` and change to the new palette you just add by pressing `load palette`

*Change system title bar*
1. found the one you like, you can check [this](https://www.gnome-look.org/p/1755582)
2. `extract` it, and move it to `/usr/share/themes/`
3. now search for `openbox setting` and change it to the theme you just add

LXQT also have picom preinstall, but you cant config it, you have to config it throught compton: `~/.config/compton.conf`

*install tiling windows*
1. navigate to `~/.config/openbox/rc.xml`, make a `backup` of this file
2. open this file with featherpad or nano
3. add this thing to this place ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/e76929a3-c491-4e10-8705-53ab6dae0eb2)

(at middle keyboard and keybind) copy all in tiling.txt file to `rc.xml`

4. save it
5. Run command in terminal to reconfigure openbox for the shortcut to take effect. `openbox --reconfigure`

**Optional** *Change icons themes*
1. `Install` icon themes, highly recommend [this](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme) `yay -S papirus-icon-theme`
2. Now open `appearences` and go to `icon themes`, change to the one you just done install

*Changing theme in Qterminal* (if none of the color scheme preinstall don't fit your taste then you can check the below)
1. Qterminal theme is reliant palette so u have to check *Windows and tilling themes* above
2. After you done, `open` up the terminal and go to `file->preferences->appearences->color scheme` and change it to the one you just add

*Changing theme in Xfce4-terminal*
1. `Download` the theme online, i'm highly recommend [this](https://github.com/nordtheme/xfce-terminal/tree/develop)
2. `Extract` the download file, and move it to `~/.local/share/xfce4/terminal/colorschemes/`
3. `open` up xfce4-terminal, go to `edit` tab and chosse `preferences`, go to `colors` and change `presets` to the theme you just add

*Changing font for terminal*
1. `Download` font from the web, [this](https://www.nerdfonts.com/font-downloads) one is really good, expecially the gohu font one
2. `extract` it, and move it to `~/local/share/fonts/` (if it don't have that folder just create it)
3. `open` up your terminal, go to `edit` tab (Qterminal is file tab) and chosse `preferences`,  go to `appearences` and change `font` to the one you just add

Note: If you want your terminal transparent, find the `opacity` thing, and change it to your liking.
### Troubleshoot (arch)

If the panel just disable, try to delete the new one u just add and rename the original one back to normal.

If you few a lot of lag then i'm highly recommend you to install driver: 
```
yay -S nvidia-dkms nvidia-utils lib32-nvidia-utils nvidia-settings
then reboot
```
if you have trouble with extracting file, go to `edit` tab (upper left), go to `preferences`, go to `advanced tab`, in `archiver integration` swicth it to `lxqt-archiver` and it should fix now

if you press `f4` of right-click to open up the terminal but it keep showing up xterm, here is how to fix it: go to `edit` tab (upper left), go to `preferences`, go to `advanced tab`, in `terminal emulator` change it to `qterminal` or anything else you use (EX: xfce4-terminal)

<3 <3 THANKS YOUR GUY FOR READING <3 <3

