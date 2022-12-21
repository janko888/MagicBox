#  M401A（2+16G）已识别版本及对应安装armbian方法
  
   ```yaml
  目前已识别的M401A（2+16G）版本的版本类型主要有两个不同的型号，总结出不同的型号要刷写armbian需要使用不同的方法。
  
  💡Tip: 下面的类型均为魔百和M401A(2+16G)版本，主板上均有“江苏m401a”字样的字样，无法简单根据省份区分版本。
  💡Tip: m401a引导armbian时除了u盘最好不要插入其它usb设备(例如usb键盘)，有可能缓慢卡在启动环节。
   ```

## 1.类型A TYPE—A
   TYPE-A类型版子根据EMMC的不同，目前可分为强体质版本和弱体质版本。强体质版本一般可以用200000000hzEMMC参数和1.8GzhCPU参数的dtb驱动；弱体质版本可以用100000000hzEMMC参数和1.7GhzCPU参数的dtb驱动。
   
   ## 板子识别
   
   ####    1）TYPE-A强体质版本，ddr4内存是scy;emmc标识为sec 137字样;板子的logo文字印刷在靠近蓝牙芯片处.
   ![Image text](https://github.com/janko888/MagicBox/blob/main/M401A/img/type_a_s.png?raw=true)
   
   SEC内存特写
   ![Image text](https://github.com/janko888/MagicBox/blob/main/M401A/img/m401a_emmc_sec.png?raw=true)
  
   ###     2）TYPE-A弱体质版本，总体同上面强体质版本，emmc标识为silicongo.
   SILICONGO 内存特写
   ![Image text](https://github.com/janko888/MagicBox/blob/main/M401A/img/m401a_emmc_silicongo.png?raw=true)
   
   ## 刷写armbian方式
   
   ```yaml
   1.固件，使用TYPE-A类型的[m401a固件](https://github.com/janko888/MagicBox/blob/main/M401A/firmware/TYPE_A_M401A.zip)，即常见的江苏版安卓9_原厂官改_开启ROOT_线刷固件包，固件识别内存为2G;
   
   2.使用[ophub库] (https://github.com/ophub/amlogic-s9xxx-armbian/releases)的armbian,下载最新的s905l3a的镜像,dtb选择meson-g12a-s905l3a-m401a.dtb
   
   3.写入emmc时使用 armbian-install （这里可以不加-m yes）,依次选择306、ext4分区;
   
   ```
   
   💡Tip: TYPE-A版本的M401A可以兼容大部分m401a\cm311-1a的固件，包括下面的TYPE-B版本的固件。
   
   💡Tip: TYPE-A高体质版本可以尝试使用[最高1900MHZ的dtb](https://github.com/janko888/MagicBox/blob/main/M401A/firmware/DTB_M401A_TYPE_A1900.zip)。 (内核5.15.x)
   
   💡Tip: TYPE-A低体质版本可以尝试使用[最高1800MHZ的dtb](https://github.com/janko888/MagicBox/blob/main/M401A/firmware/DTB_M401A_TYPE_A1800.zip)。 (内核5.15.x)
   
   
  
   
   
   ## 2.类型B TYPE—B
   TYPE-B类型版子特点是内存不同于TYPE-A,使用大部分M401A的固件都只能识别1G的内存，无法启动usb的armbian.暂时发现有一个311-1a的固件可以使用。
   
   ## 板子识别
   
   ####    TYPE-B版本，ddr4内存是CXMT;emmc标识为silicongo字样;板子的logo文字印刷在靠近USB接口处.
   ![Image text](https://github.com/janko888/MagicBox/blob/main/M401A/img/type_b_s.png?raw=true)
   
   ## 刷写armbian方式：
   ```yaml
   1.固件，使用TYPE-B类型的[CM311固件](https://github.com/janko888/MagicBox/blob/main/M401A/firmware/TYPE_B_CM311-1a.zip),cm311-1a_YST安卓9-S905L3A线刷固件包，固件可以识别内存为2G;其它常用的m401a固件一般显示内存为1G，暂无发现可以驱动armbian的版本，表现为启动logo后黑屏无响应。
   
   2.使用[ophub库](https://github.com/ophub/amlogic-s9xxx-armbian/releases)的armbian,下载最新s905l3a的镜像,dtb选择meson-g12a-s905l3a-m401a.dtb
   
   3.写入emmc时使用 armbian-install -m yes （重要，这里必须写入bin，否则无法emmc启动及再由usb启动）,依次选择306、ext4分区;
   ```
   
   
