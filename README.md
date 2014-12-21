# vagrant_ionic_wya

Vagrant project files to set up the Ionic build/test environment for the TVSD WhereYouAt client.

## Pre-requisites
To use this project, you must first have Vagrant installed and working. Please visit [vagrantup.com](https://vagrantup.com) for more information. Especially ensure that the command `vagrant ssh` works for Vagrant boxes.

## Preparation
Before running, this Vagrant project and the [ionic_wya](https://github.com/TVSD/ionic_wya) must be cloned into the correct locations.

1. Create a `client` folder which will contain this project & the ionic_wya project.
2. In the `client` folder, clone the `ionic_wya` project. You should now have a `client\ionic_wya` folder.
3. In the `client` folder, clone this project. You should now have a `client\vagrant_ionic_wya` folder.
4. You should now have the following directory structure:
   ```
   client\
     ionic_wya\
     vagrant_ionic_wya\
   ```
5. Check which Vagrant boxes you have installed. To do this, open a command prompt and run the following command: `vagrant box list`. Make a note of the boxes you have installed.
6. In a text editor, open the `client\vagrant_ionic_wya\Vagrantfile`. Toward the beginning of the file, there will be a section similar to the following:
   ```
   # Uncomment one of the boxes below depending on the box you currently have.
   # If you don't have either box, uncomment the first one.
   # To find which boxes are on your system: $ vagrant box list
   #config.vm.box = "drifty/ionic-android"
   #config.vm.box = "drifty_ionic"
   ```
   Uncomment the line with the name of a box you already have installed and save the file.

## Running the project in Ionic (quick)
1. `vagrant up` in the `client\vagrant_ionic_wya` folder.
2. `vagrant ssh`
3. `cd /project && ionic serve`
4. Open `http://localhost:8100/` in your browser.

## Running the project in Ionic (detailed)
1. Open the `client` folder in your command prompt.

   On Windows, you can double-click the `client` folder in Explorer, shift+right-click in an empty area of the folder and select "Open command window here".
2. Change directories to the `vagrant_ionic_wya` folder:
   ```
   cd vagrant_ionic_wya
   ```
3. Start the Vagrant box using the command `vagrant up`
4. Once the box has loaded, SSH into the Vagrant box using the command `vagrant ssh`
5. You should now be at a command prompt within the Vagrant VM:
   ```
   Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-34-generic i686)

   Last login: Sun Dec 21 17:44:41 2014 from 10.0.2.2
   vagrant@ionic-android:~$
   ```
6. At the Vagrant box's Linux command prompt, change directories to the Ionic project directory:
   ```
   vagrant@ionic-android:~$ cd /project
   ```
7. Run the project:
   ```
   vagrant@ionic-android:/project$ ionic serve
   ```
   If prompted, choose the non-`localhost` option when serving.
8. On your host system, open a web browser and go to `http://localhost:8100/`.
9. When development is finished, be sure to shut down or suspend the Vagrant box. Do not just close the command prompt as the box will continue consuming host resources as the VM runs in the background.

   I recommend suspend if you intend to return to the project later, and shutting down if you will not be developing for some time. You can also destroy the box, but you will then need to wait for Vagrant to re-import the box and also wait for the provisioner to update Ionic, which can take a while.
