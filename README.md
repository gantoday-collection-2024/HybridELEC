# HybridELEC
HybridELEC aims to bring **side-by-side dual-booting** support to **CoreELEC** and **EmuELEC** on **internal storage** many assumed impossible, it is born as a byproduct of heavily reverse-engineering the **Xiaomi mibox3/3c (MDZ-16-AA)**, but is supposed to work on similiar hardware (**gxbb_p200_1g**).   
Unlike upstream **CoreELEC** and **EmuELEC**, **HybridELEC** only offers **USB Burning Tool** flashable images, and is distributed on a per-device level, as the dual-booting feature relies on modifying the partition layout via [**device-tree**](https://github.com/7Ji/HybridELEC/blob/25cf23d6e737d6a85f01da149851b4e4a0efbf84/projects/Amlogic/packages/device-tree-mibox3/hybrid.dts) during the USB Burning process.   


## Project Structure
The main **hybrid-1.0** branch is only for introducing the project via this page, and packging the whole image. The modified **CoreELEC** and **EmuELEC** sources reside on [**coreelec-9.2**][coreelec-9.2] and [**emuelec-4.3**][emuelec-4.3] branches

## Build yourself
You need to clone the whole respository, checkout and build the modified branch of **CoreELEC** and **EmuELEC** respectively, then get back to **HybridELEC** and combine the images:
````
git clone https://github.com/7Ji/HybridELEC.git
git checkout coreelec-9.2
CUSTOM_VERSION=1.0 PROJECT=Amlogic DEVICE=mibox3 PROFILE=hybrid make
git checkout emuelec-4.3
CUSTOM_VERSION=1.0 PROJECT=Amlogic DEVICE=mibox3 PROFILE=hybrid make
git checkout hybridelec-1.0
CUSTOM_VERSION=1.0 PROJECT=Amlogic DEVICE=mibox3 make
````

## License
As a derived work of CoreELEC and EmuELEC, HybridELEC itself is licensed under **GPLv2**, check branch [**coreelec-9.2**][coreelec-9.2] and [**emuelec-4.3**][emuelec-4.3] to view the upstream licenses.  

## Closed-source blobs
Even though **HybridELEC** itself is open-source, there are several closed-source blobs included in the repository:  
1. **u-boot** needed to build the image is extracted from the stock image shipped from **Xiaomi**
2. The tool to build it is also closed-source blob leaked from **Amlogic**


[coreelec-9.2]: https://github.com/7Ji/HybridELEC/tree/coreelec-9.2
[emuelec-4.3]: https://github.com/7Ji/HybridELEC/tree/emuelec-4.3
