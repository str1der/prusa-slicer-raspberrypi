# prusa-slicer-raspberrypi

![Screenshot](https://github.com/str1der/prusa-slicer-raspberrypi/blob/main/Prusa-Slicer.png)

Prusa slicer 2.3.0 kararlı son sürümünün Raspberry pi 4 için derlenmiş 64 bitlik sürümüdür. 2020-05-27-raspios-buster-arm64 üzerinde çalışmaktadır. 2020-08-20-raspios-buster-arm64 üzerinde de test edilmiştir.

# Kurulum

Kurulum için aşağıdaki komutu kullanabilirsiniz. 

```
sudo apt install ./prusa-slicer_2.3.0_arm64.deb
```
veya

```
sudo dpkg -i ./prusa-slicer_2.3.0_arm64.deb
```



# Derleme
Prusa Slicer 2.3.0 versiyonunu kullanabilmek için indirdiğiniz deb paketini kurup yukarıdaki komutlardan birini kullanarak yüklemeniz yeterlidir. Fakat kendiniz kaynak koddan derlemek iserseniz aşağıdaki adımları takip ederek debian paketi oluşturabilirsiniz. 

Öncelikle [buradan](https://github.com/prusa3d/PrusaSlicer/releases) Prusa Slicer son sürümünün kaynak kodunu indirebilirsiniz.

# Derleme öncesi gerekli paketlerin kurulumu

```
sudo apt install cmake libboost-dev libboost-thread-dev libboost-filesystem-dev libboost-iostreams-dev  libboost-system-dev libboost-log-dev libboost-locale-dev libboost-regex-dev libcurl4-openssl-dev libdbus-1-dev libeigen3-dev libglew-dev libcereal-dev libnlopt-cxx-dev libopenvdb-dev libopenvdb-tools libcgal-dev libtbb-dev libtbb2
```

# Derleme işlemleri 
Paket dosyasını indirdikten ve arşivden çıkardıktan sonra aşağıdaki komutları sırası ile uygulayınız. 
```
cd "paket-dizin-yolu"
mkdir build
cd build
cmake .. -DCMAKE_BUILD_TYPE=Release -DSLIC3R_WX_STABLE=1 -DSLIC3R_FHS=1 -DSLIC3R_BUILD_TESTS=OFF
make -j$(nproc) DESTDIR=$PWD/deb install
```

# DEB paketi hazırlama

Derleme işlemleri tamamlandıktan sonra aşağıdaki komutları çalıştırarak .deb paketini oluşturabilirsiniz. 

```
cat > deb/DEBIAN/control <<EOD
Package: prusa-slicer
Version: 2.3.0
Maintainer: fkarakutuk <https://bfkarakutuk.wordpress.com/>
Priority: optional
Section: science
Bugs: https://github.com/str1der/prusa-slicer-raspberrypi/issues
Homepage: https://github.com/str1der/prusa-slicer-raspberrypi
Depends: libboost-all-dev, libcurl4, libglew2.1, libtbb2, libnlopt0, libopenvdb5.2, libqhull7, libwxgtk3.0-gtk3-0v5, libcgal-dev, libglu1-mesa, libwxgtk3.0-0v5
Architecture: arm64
Description: Prusa-Slic3r 2.3.0
 compiled for raspberry pi 4 running 2020-05-27-raspios-buster-arm64.
EOD


fakeroot dpkg-deb -b ./deb/ .
```

# prusa-slicer-raspberrypi

Prusa slicer 2.3.0 is a 64 bit version of the final version compiled for Raspberry pi 4. Runs on 2020-05-27-raspios-buster-arm64. Also tested on 2020-08-20-raspios-buster-arm64.

# Setup

To use it, you can use the command below.

```
sudo apt install ./prusa-slicer_2.3.0_arm64.deb
```

or

```
sudo dpkg -i ./prusa-slicer_2.3.0_arm64.deb
```



# Compilation
To use Prusa Slicer 2.3.0 version, you can install the deb package you downloaded and use one of the commands. However, to compile from source code, you can create a debian package by following the source.

First, download the source code of Prusa Slicer latest version from [here](https://github.com/prusa3d/PrusaSlicer/releases).

# Installation of required packages before compilation

```
sudo apt install cmake libboost-dev libboost-thread-dev libboost-filesystem-dev libboost-iostreams-dev libboost-system-dev libboost-log-dev libboost-locale-dev libboost-regex-dev libcurl4-openssl-dev libdbus-1 -dev libeigen3-dev libglew-dev libcereal-dev libnlopt-cxx-dev libopenvdb-dev libopenvdb-tools libcgal-dev libtbb-dev libtbb2
```

# Compilation processes
After downloading the package and extracting it from the archive, follow the commands below in order.
```
cd "package-directory-path"
mkdir build
cd build
cmake .. -DCMAKE_BUILD_TYPE=Release -DSLIC3R_WX_STABLE=1 -DSLIC3R_FHS=1 -DSLIC3R_BUILD_TESTS=OFF
make -j$(nproc) DESTDIR=$PWD/deb install
```

# Preparing a DEB package

After the compilation is complete, you can create the .deb package by running the commands below.

```
cat > deb/DEBIAN/control <<EOD
Package: prusa-slicer
Version: 2.3.0
Maintainer: fkarakutuk <https://bfkarakutuk.wordpress.com/>
Priority: optional
Section: science
Bugs: https://github.com/str1der/prusa-slicer-raspberrypi/issues
Homepage: https://github.com/str1der/prusa-slicer-raspberrypi
Depends: libboost-all-dev, libcurl4, libglew2.1, libtbb2, libnlopt0, libopenvdb5.2, libqhull7, libwxgtk3.0-gtk3-0v5, libcgal-dev, libglu1-mesa, libwxgtk3.0-0v5
Architecture: arm64
Description: Prusa-Slic3r 2.3.0
 compiled for raspberry pi 4 running 2020-05-27-raspios-buster-arm64.
EOD


fakeroot dpkg-deb -b ./deb/ .
```





