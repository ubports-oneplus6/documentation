# Install the image

```
sudo mount -o rw,remount /
sudo apt update && sudo apt install -y anbox-ubuntu-touch android-tools-adb
mkdir ~/anbox-data
wget http://cdimage.ubports.com/anbox-images/android-armhf-64binder.img -O ~/anbox-data/android.img
touch ~/anbox-data/.enable
sudo chmod -R o+wrx /home/phablet/anbox-data/data
sudo start -q anbox-container
```

# Symlink Android documents to system

```
ln -s ~/anbox-data/data/media/0/Documents ~/Documents/android
ln -s ~/anbox-data/data/media/0/Pictures ~/Pictures/android
ln -s ~/anbox-data/data/media/0/Music ~/Music/android
ln -s ~/anbox-data/data/media/0/Movies ~/Videos/android
```

> **NOTE:** CURRENTLY IN TESTING! You should expect increased battery drain. Networking inside the container doesn't currently work.

