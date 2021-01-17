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

Öncelikle ![buradan](https://github.com/prusa3d/PrusaSlicer/releases) Prusa Slicer son sürümünün kaynak kodunu indirebilirsiniz.

# Derleme öncesi gerekli paketlerin kurulumu

```
sudo apt install cmake libboost-dev libboost-thread-dev libboost-filesystem-dev libboost-iostreams-dev  libboost-system-dev libboost-log-dev libboost-locale-dev libboost-regex-dev libcurl4-openssl-dev libdbus-1-dev libeigen3-dev libglew-dev libcereal-dev libnlopt-cxx-dev libopenvdb-dev libopenvdb-tools libcgal-dev libtbb-dev libtbb2
