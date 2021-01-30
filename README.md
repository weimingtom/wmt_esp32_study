# wmt_esp32_study
My ESP32 study

## msys   
* search baidupan, msys_esp-idf_v3.1.2_v1.rar  
* search baidupan, msys_esp-idf_v3.1.7_v1.rar  

## Old README  
* https://github.com/weimingtom/wmt_esp32_study/blob/main/README_001.md  

## esp32 msys2 dev env    
serach baidupan, esp32_blink_burn.jpg  
search baidupan, 快速入门.docx  
https://docs.espressif.com/projects/esp-idf/zh_CN/v3.1.7/get-started/index.html  
https://docs.espressif.com/projects/esp-idf/zh_CN/v3.1.7/get-started/windows-setup.html  
https://dl.espressif.com/dl/esp32_win32_msys2_environment_and_toolchain-20180110.zip  
https://dl.espressif.com/dl/esp-idf/releases/esp-idf-v3.1.2.zip  
https://dl.espressif.com/dl/esp-idf/releases/esp-idf-v3.1.7.zip  
(double click mingw32.exe)  
$ cd  
$ mkdir esp  
(unzip esp-idf-v3.1.2.zip to /msys32/home/a/esp)  
$ cd esp/esp-idf/  
$ export IDF_PATH=~/esp/esp-idf  
$ cd $IDF_PATH/examples/get-started/hello_world  
$ make clean  
$ make menuconfig  
(press tab key, exit, wait GENCONFIG end)  
$ make  
LD build/hello-world.elf  
esptool.py v2.6-beta1  
To flash all build output, run 'make flash' or:  
python /home/a/esp/esp-idf/components/esptool_py/esptool/esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 115200 --before default_reset --after hard_reset write_flash -z --flash_mode dio --flash_freq 40m --flash_size detect 0x1000 /home/a/esp/esp-idf/examples/get-started/hello_world/build/bootloader/bootloader.bin 0x10000 /home/a/esp/esp-idf/examples/get-started/hello_world/build/hello-world.bin 0x8000 /home/a/esp/esp-idf/examples/get-started/hello_world/build/partitions_singleapp.bin  

## ESP32 firmware flash, with flash_download_tool    
https://www.espressif.com/en/support/download/other-tools  
Flash Download Tools (ESP8266 & ESP32 & ESP32-S2)  
Windows PC	V3.8.5	2020.04.26	  
https://www.espressif.com/sites/default/files/tools/flash_download_tool_v3.8.5.zip  
(for NodeMCU-32S)  
Example Configuration->blink gpio number->2  
(CONFIG_BLINK_GPIO=2)  
In flash_download_tool_3.8.5.exe:  
bootloader.bin   0x1000  
blink.bin  0x10000  
partitions_singleapp.bin  0x8000  
see https://docs.ai-thinker.com/esp_download  

## 使用步骤  
如果想在windows下使用esp-idf，可以用旧的v3.1.7版本：  
（1）在官方的文档中下载windows工具链和3.1.7的esp-idf，不要自己git下载，因为这里涉及很多仓库检出，  
比较麻烦，还是直接下载好了。下载两个压缩包后放在一起（我把esp-idf解压到esp/esp-idf下）  
https://docs.espressif.com/projects/esp-idf/zh_CN/v3.1.7/get-started/index.html  
（2）使用mingw32.exe启动命令行（不要用其他exe），然后导出全局变量IDF_PATH，例如这样：export IDF_PATH=~/esp/esp-idf  
（3）编译examples/get-started/blink示例，在make menuconfig的时候把  
Example Configuration->blink gpio number修改成2，因为NodeMCU-32S（安信可的开发板）  
的灯是GPIO2控制的，然后make编译  
（4）如果想单独刷固件，可以参考安信可的文档：《如何为 ESP 系列模组烧录固件》  
https://docs.ai-thinker.com/esp_download  
而flash_download_tool在官网下：  
https://www.espressif.com/en/support/download/other-tools    
也可以用make flash刷固件，不过不够直观  


## doc  
* esp32 ref  
https://docs.espressif.com/projects/esp-idf/en/latest/index.html  

* 安信可-NodeMCU-32S 核心开发板, esp32    
http://wiki.aithinker.com/esp32/boards/nodemcu_32s  

* ESP8266 ESP32  
https://github.com/SmartArduino/SZDOITWiKi/wiki/ESP8266---ESP32  

* ESP-IDF Programming Guide  
https://docs.espressif.com/projects/esp-idf/en/latest/index.html  

* ESP32 资源  
https://www.espressif.com/zh-hans/products/hardware/esp32/resources  

* ESP32 技术参考手册 (pdf)    
https://www.espressif.com/sites/default/files/documentation/esp32_technical_reference_manual_cn.pdf  

* ESP32 常见问题 (pdf)  
https://www.espressif.com/sites/default/files/documentation/ESP32_FAQs__CN.pdf  

## Tools  
* esp-idf (for esp32)    
for windows, need msys2 (from dl.espressif.com) and esp-idf two parts      
https://docs.espressif.com/projects/esp-idf/en/stable/get-started/windows-setup.html  
https://dl.espressif.com/dl/esp32_win32_msys2_environment_and_toolchain-20180110.zip  
https://docs.espressif.com/projects/esp-idf/en/stable/get-started/  
$ cd ~/esp  
$ git clone -b v3.1.2 --recursive https://github.com/espressif/esp-idf.git  

* arduino plugin (for esp32)    
https://dl.espressif.com/dl/package_esp32_index.json  

* cdt (for esp8266, esp32)    
http://wiki.aithinker.com/ai_ide_install  
cygwin\opt\xtensa-lx106-elf  
cygwin\opt\xtensa-esp32-elf  

* FLASH_DOWNLOAD_TOOLS  
<> for esp32  
(baidupan) FLASH_DOWNLOAD_TOOLS_V3.6.2.2_v1_good.rar  

* esplorer  
<> for esp32, esp8266    
(baidupan) esplorer_v1.rar  

## 通过ESP-IDF工具安装器在windows下搭建esp32环境  
* https://blog.csdn.net/m0_50151793/article/details/110226199  

## HoloCubic--多功能透明显示屏桌面站  
https://github.com/peng-zhihui/HoloCubic  

## 安信可IDE 0.5版本esp-idf    
* https://dl.espressif.com/dl/esp-idf/releases/esp-idf-v2.0.zip  

## esp-idf v3.1.2 msys port  
费了很大的劲，终于把esp-idf v3.1.2搬到msys上，不同于官方的  
msys2方法和安信可的cygwin方法，我用我自己的方法解决绿色安装问题：  
（1）工具链：可以直接用msys2里面的工具链，在opt目录下。那个工具  
链不依赖mingw32，如果用安信可IDE版本，可能会依赖于cygwin的dll  
（2）kconfig的两个命令：esp-idf会在构建前调用mconf-idf和conf-idf，  
我测试过可以预编译，这样就不需要另外再加一个本机gcc工具链了。  
但是，这两个工具不容易编译，mconf-idf依赖于ncurses，而conf-idf  
依赖于一些linux特定的头文件，所以要费很大的功夫去改，甚至要改动  
esp-idf的构建文件。最后，我自己编译出魔改版的conf-idf，而  
mconf-idf直接复制conf-idf即可，因为我不需要menuconfig
（3）几个py脚本需要转成exe，否则会依赖于本地的python，我通过  
pyinstaller把以下几个脚本转为exe（同时需要改动esp-idf的构建脚本）：  
esptool、gen_esp32part和parttool  
