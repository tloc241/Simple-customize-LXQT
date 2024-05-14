# Simple-customise-lxqt
#Preview

![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/913a85fc-67e8-457e-a30f-6d0c2655fb5c)

Custom DE dont have to install or download too much app

I'm really recommend you to install Nala, Nala can be alot faster compare to apt, to install Nala you can open terminal by ctrl+alt+t, then you ctrl +c this line: 'sudo apt install -y nala' and press enter.

It'll ask for password (bcs you use sudo) just type in and enter again. For now on much of command that have 'apt', 'apt-get' can replace with nala (add-apt can't replace bcs it add repo so you can install with nala ok)
# 1. Custom grub select menu
To custom grub you have to install grub customizer. To install simply open terminal (ctrl+alt+t) and type: 'sudo nala install -y grub-customizer' and it will done the job for you.
After it done doing it thing, you press 'super key / windows key' on you keyboard and search for grub customizer and open it. 
# At here you can change name and add more custom boot
![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/c52de175-83f8-44aa-a003-3c706324d447)

At default, Lubuntu have an Ubuntu name, you can simply by double left click to the tile, after changing you have to type the save button on the top left of the windowx.
To customise the GUi you can do it here to, but much of the time it won't work so i gonna tell you an alternative/manual way

First, go to gnome-look.org, then go to search bar and search for grub theme, at there you can find the theme that favor your eyes 

After download it, you have to add it into a config file, this is how you do it:

1. Open file manager, then ctrl + l show you can change the directory,
2. Type /usr/share/grub/themes/ ,
3. In there press f4 on your keyboard, it'll show up a terminal
4. Type cd ~/Downloads, you can open another file manager and go to Downloads and extract to themes you just download of simply extract it through terminal by 'upzip <file name>', then ls to show your file name.
5. After extract you have to type this: 'sudo mv <folder you just extract> /usr/share/grub/themes .
6. Type this in file manager directory: 'etc/default/ and find a grub.conf file, open it up.
7. At here you have to change the line below: /usr/share/grub/themes/<your theme name>/theme.txt ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/f421f6b3-d7ca-43af-8518-13ec7ce47625)
8. Open terminal and type: 'sudo update-grub' and now you can reboot and enjoy your new grub UI now. ![IMG_20240506_180823_353](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/0ba5caf6-412d-4519-bc20-db50ce799a50)

Bonus: to change icon you have two way of doing that
1. Go to icons folder of your theme then open it with gimp (sudo nala install -y gimp) and drag your picture into it and save it by ctrl shift e and close it, it'll show warning, just discard it.
2. Go to grub customizer and edit your boot directory, add this line above 'search --no-floppy --fs-uuid --se' : menuentry ''change this to your boot default name'' --class 'changde this to your icon name' { .

   ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/57ebf595-ebe5-4b24-bfc9-0bcf7a0521cd)

After that remember to press save icon.

# 2. Change lxqt boot logo

1. To change this you have to install plymouth, just simply type: 'sudo nala install -y plymouth'

2. After install it go to gnome-look.org and type plymouth theme to download. I'm highly recommend you to check this out: https://www.gnome-look.org/p/2106821
3. Done download go to extract it, now you file this directory: /usr/share/plymouth/themes
4. press f4 to open terminal, now move your file to it by: cd ~/Downloads , then ls (it help you to find the folder name)
5. now type sudo mv <your folder name> /usr/share/plymouth/themes
6. now open file manager and go to /usr/share/plymouth/themes and find the file name default.plymouth
7. change the line ImageDir to the path of your folder 

![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/aece6579-3881-44c1-b3e6-82c1c6e43732)

or use this commandline:{ ### *my-plymouth-theme* should be replaced with the theme-name which you downloaded (without the **)

sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/*my-plymouth-theme*/*my-plymouth-theme*.plymouth 120

 With this command, you need to select the theme

sudo update-alternatives --config default.plymouth}
8. type this in terminal 'sudo update-initramfs -u -k all'

And that all, enjoy your custom boot logo 

![Screenshot_20240514-143641](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/85339a72-a3cf-410f-8c61-7349fae0adff)

# 3. Change lxqt lock screen

LXQT use sddm at is lock screen so it can be change as well, unfortunally, i only capable to make MarianArlt sddm work, other sddm lock sreen you found on gnome-look might not work, and i don't know how to fix it either, sr

1. Download sddm theme, like i said above only MarianArlt themes work, show MarianArlt alternative also work, you can check sugar dark, sugar candy, the-zero885 lubuntu-sddm-theme
2. extract the file you just download, and move it to sddm folder: /usr/share/sddm/themes ('cd ~/Downloads'  'ls'   'sudo mv <folder name> /usr/share/sddm/themes'
3. If you using lxqt on lubuntu like mine, just rename ubuntu-theme folder (for backup resson) : 'cd /usr/share/sddm/themes/'   'sudo mv ubuntu-theme ubuntu-theme-bakcup'
If you using lxqt in other distro just rename lubuntu folder: 'cd /usr/share/sddm/themes/'   'sudo mv lubuntu lubuntu-bakcup'
4. Now rename your theme folder to ubuntu-theme / lubuntu theme depend on your distro
5. log out to see if it work 

![Screenshot_20240514-145923](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/b7b809f4-3b01-4920-b165-612b96fcd641)

# 4. Customise in the main desktop 
![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/86fb4823-877e-4603-9556-e939a0de78db)

If you want to look like mine, you have to install 2 app. Ulauncher and Plank

*Install Ulauncher :*
1. just type in terminal 'sudo nala install -y ulauncher' and it'll do it thing, if it fail just add respo 'sudo add-apt-repository universe -y && sudo add-apt-repository ppa:agornostal/ulauncher -y'
2. Now open ulauncher, it will show up a searchbar look on the righ, you see to wheel thing, click into it, it'll show this GUI ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/dc4a9162-af90-4d90-bf8f-6050e75669c9)
3. click to launch at login and close it
Optional:
4. To change theme you have to download ulauncher theme (https://www.pling.com/p/1995620)
5.  then go to /home/lo1402/.config/ulauncher (if it don't show up just open it angain and f5)
6. Monve your themes to there, and rename it to user-themes
7. go back to ulauncher app, go to color themes and change to your themes just add

*Install Plank*
1. Type in terminal: 'sudo nala install -y plank' and wait
2. After it done, try to open to by typing in terminal plank
3. if it work now you can change it thing, do the same thing in below picture
![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/8d61e216-26f4-42ba-92bb-e097b90fb2c6)![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/2362b38f-4681-4948-b51a-2b380b29c6c1)
4. to make plank auto start when login you have to open session setting
5. go to autostart tab
6. press add button
7. name it plank, command also plank
8. press ok and close it

*Panel*
1. Go to this website of the author https://www.pling.com/p/1995620
2. After download it, extract it
3. open another file manager and go to ~/.config/lxqt/ and change panel.conf file name to panel-00.conf
4. move the panel.conf you just download in ~/.config/lxqt/
5. log out to see if it work or not

Optional: *Add transparancy to panel*
1. tick on background color, and set opacity to below 70% 

![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/a68dd22d-7960-455d-85dd-e11e0ccf3ebb)

Make sure to turn on compton*
2. set compton to auto run, to do that you have to open session setting
3. go to autorun tab
4. add compton to it (similar to plank)

*Troubleshoot:*

If the panel just disable try to delete a new one and rename the original one to get back to normal.

If it still can't fix it then you have to reinstall lxqt desktop (do not worry, it won't earse any of your customization anyway): 'sudo apt install --reinstall lubuntu-desktop' (you have to use apt, nala don't work on this)

If it still have problem then i think you should install gpu driver, you can go to this website to install it (https://github.com/lutris/docs/blob/master/InstallingDrivers.md)

Optional *Dark mode*

To have dark mode in Lxqt you use have to search for appearence and set wiget style like mine: ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/454f0b89-fb29-4d13-b3be-a8febfbd3ab2)

LXQT also have picom preinstall, but you cant config it, you have to config it throught compton: ~/.config/compton.conf

*install tiling windows*
1. navigate to ~/.config/openbox/rc.xml, make a backup of this file
2. open this file with featherpad or nano
3. add this thing to this place ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/e76929a3-c491-4e10-8705-53ab6dae0eb2)

(at middle keyboard and keybind) copy all in tiling.txt file to rc.xml

4. save it
5. Run command in terminal to reconfigure openbox for the shortcut to take effect. 'openbox --reconfigure'

Optional: (kind of personal fix)

install auto-cpufreq (if you r using a laptop)

if you are using lenovo and want to change lenovo logo, go to lenovo logo tab one

if you using ibus but having problem, you can go to ibus troubleshoot tab one

if you have problem with pulseaudio, you can go to pulseaudio tab one

if your discord can't share audio in browser then go to discord fix tab one

THANKS YOUR GUY FOR READING. :) :)

