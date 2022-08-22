# Unzip VScode and MSYS2
* https://code.visualstudio.com/sha/download?build=stable&os=win32-x64-archive VSCode.zip
* https://github.com/msys2/msys2-installer/releases/ msys2-base.sfx.exe


## data\user-data\User\settings.json:
    {
        "terminal.integrated.profiles.windows": {
            "msys mingw64": {
                // https://stackoverflow.com/questions/43302853/using-msys-shell-in-visual-studio-code
                "icon": "terminal-linux",
                "path": "${execPath}\\..\\msys64\\msys2_shell.cmd",
                "args": [
                    "-defterm",
                    "-here",
                    "-no-start",
                    "-mingw64"
                ]
            }
        }
    }

## msys64\etc\nsswitch.conf
    # Begin /etc/nsswitch.conf

    passwd: files db
    group: files db

    db_enum: cache builtin

    # db_home: cygwin desc
    db_home: /home/portable
    db_shell: cygwin desc
    db_gecos: cygwin desc

    # End /etc/nsswitch.conf

# Install GCC from bash
    pacman -Syuu
    pacman -S --needed base-devel mingw-w64-x86_64-gcc mingw-w64-x86_64-python
