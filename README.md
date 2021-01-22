# wmt_esp32_study
My ESP32 study


## esp32 msys dev env    
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

