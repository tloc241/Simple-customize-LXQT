# simple-customise-lxqt
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
2. type /usr/share/grub/themes/ ,
3.  in there press f4 on your keyboard, it'll show up a terminal
4.  type cd ~/Downloads, you can open another file manager and go to Downloads and extract to themes you just download of simply extract it through terminal by 'upzip <file name>', then ls to show your file name.
5.   After extract you have to type this: 'sudo mv <folder you just extract> /usr/share/grub/themes .
6. Type this in file manager directory: 'etc/default/ and find a grub.conf file, open it up.
7. At here you have to change the line below: /usr/share/grub/themes/<your theme name>/theme.txt ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/f421f6b3-d7ca-43af-8518-13ec7ce47625)
8. open terminal and type: 'sudo update-grub' and now you can reboot and enjoy your new grub UI now. ![IMG_20240506_180823_353](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/0ba5caf6-412d-4519-bc20-db50ce799a50)

Bonus: to change icon you have to way of doing that
1. go to icons folder of your theme then open it with gimp (sudo nala install -y gimp) and drag your picture into it and save it by ctrl shift e and close it, it'll show warning, just discard it.
2. go to grub customizer and edit your boot directory, add this line above 'search --no-floppy --fs-uuid --se' : menuentry ''change this to your boot default name'' --class 'changde this to your icon name' { .

   ![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/57ebf595-ebe5-4b24-bfc9-0bcf7a0521cd)

After that remember to press save icon.

# 2. Change lubuntu boot logo

1. To change this you have to install plymouth, just simply type: 'sudo nala install -y plymouth'

2. After install it go to gnome-look.org and type plymouth theme to download. I'm highly recommend you to check this out https://www.gnome-look.org/p/2144745
3. Done download go to extract it, now you file this directory: /usr/share/plymouth/themes
4. press f4 to open terminal, now move your file to it by: cd ~/Downloads , then ls (it help you to find the folder name)
5. now type sudo mv <your folder name> /usr/share/plymouth/themes
6. now open file manager and go to /usr/share/plymouth/themes and find the file name default.plymouth
7. change the line ImageDir to the path of your folder 

![image](https://github.com/tloc241/simple-customise-lxqt/assets/112869206/aece6579-3881-44c1-b3e6-82c1c6e43732)

8. 



