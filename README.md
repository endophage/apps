# Docker Containerized Applications

> Note the contents in this repository will always favour how I run my system (i.e. pulseaudio, Gnome, etc...). Hopefully they still serve as a good starting point for people running with other configurations and I'd be happy to host community contributions on branches for other setups (like a KDE branch).

This repository contains Dockerfiles for building applications that can be run from docker containers. It also contains the necessary \*.desktop files for those applications to make it east for you to install them. Simply copy the .desktop file for the application you want to run to your `~/.local/share/applications/` directory, build the container from the Dockerfile using the image name and tag that can be found at the end of the `Exec` command in the .desktop file (or modify the `Exec` to use your own image name and tag).

If you followed the docker docs to the letter and don't have to `sudo docker` (i.e. you created the docker group, gave it root permissions, and added your user to it), you can remove the `gksu` part of the `Exec` command for a fully native-like experience of running your apps out of containers. Alternatively if you already have/prefer gksudo or are on KDE rather than Gnome and want to use `kdesu`, change the `Exec` line to use that tool instead. If you choose to use `gksu`, it will be default ask you for the root user's password. You probably don't want this behaviour. It can be configured to use `sudo` under the hood by running:

```
$ gconftool-2 --set --type boolean /apps/gksu/sudo-mode true
```

## Icons

For copyright reasons, I've chosen not to include any icons in this repository, just to avoid any potential issues. A quick Google search will turn up plenty of icons for any application. They will need to be converted to .png format if they are not already in that format (there are some other formats that work but .png is the most reliable).Using the `convert` tool from the `imagemagick` package, you can easily convert any icons you might find to a png.

```
$ ls
foo.gif
$ convert foo.gif foo.png
$ ls
foo.gif foo.png
```

If you find a .ico file, you might find that after running convert on it, you have multiple output images. This is because .ico files typically contain multiple images at different resolutions, pacakged up as a single file. The `identify` tool, also included in `imagemagick` will show you what resolutions are in the .ico and the output filenames should be numbered and match up to the numbered entries displayed by `identify`.

```
$ ls
foo.ico
$ identify foo.ico 
foo.ico[0] PNG 256x256 256x256+0+0 8-bit sRGB 213KB 0.000u 0:00.000
foo.ico[1] ICO 128x128 128x128+0+0 32-bit sRGB 213KB 0.000u 0:00.000
foo.ico[2] ICO 96x96 96x96+0+0 32-bit sRGB 213KB 0.000u 0:00.000
foo.ico[3] ICO 72x72 72x72+0+0 32-bit sRGB 213KB 0.000u 0:00.000
foo.ico[4] ICO 64x64 64x64+0+0 32-bit sRGB 213KB 0.000u 0:00.000
foo.ico[5] ICO 48x48 48x48+0+0 32-bit sRGB 213KB 0.000u 0:00.000
foo.ico[6] ICO 32x32 32x32+0+0 32-bit sRGB 213KB 0.000u 0:00.000
foo.ico[7] ICO 24x24 24x24+0+0 32-bit sRGB 213KB 0.000u 0:00.000
foo.ico[8] ICO 16x16 16x16+0+0 32-bit sRGB 213KB 0.000u 0:00.000
$ convert foo.ico foo.png
$ ls
foo-0.png  foo-1.png  foo-2.png  foo-3.png  foo-4.png  foo-5.png  foo-6.png  foo-7.png  foo-8.png  foo.ico
```  
