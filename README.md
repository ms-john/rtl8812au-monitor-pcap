# rtl8812au-monitor-pcap
Use RTL8812AU to capture 802.11 raw data frame and dump to .pcap file on MacOS

### rtl8812au userspace driver
[devourer](https://github.com/openipc/devourer)

The RTL8812AU driver that simply devours its competitors

### usage
~~- Repair libusb driver~~

~~download [Zadig](https://github.com/pbatard/libwdi/releases/download/v1.5.0/zadig-2.8.exe)~~

~~![img.png](images/img.png)~~


- Command line
```shell
WiFiCapture [USB_VID]:[USB_PID] [WIFI_CHANNEL] [WIFI_CHANNEL_WIDTH] [PCAP_FILE_NAME]

#example:
#capture dongle (0B05:17D2) WIFI channel 36 channel width 80 to 80211.pcap

WiFiCapture 0B05:17D2 36 2 80211.pcap


```
- WIFI channel width enum
```c++
enum ChannelWidth_t {
  CHANNEL_WIDTH_20 = 0,
  CHANNEL_WIDTH_40 = 1,
  CHANNEL_WIDTH_80 = 2,
  CHANNEL_WIDTH_160 = 3,
  CHANNEL_WIDTH_80_80 = 4,
  CHANNEL_WIDTH_5 = 5,
  CHANNEL_WIDTH_10 = 6,
  CHANNEL_WIDTH_MAX = 7,
};
```

- 802.11 radio packet

![img_1.png](images/img_1.png)

### MacOS(arm64) Build

You can download and install libraries using the homebrew dependency manager:

```
brew install libusb libpcap
cd rtl8812au-monitor-pcap
cmake -G "Xcode" -S ./ -B "build"
cmake --build build --config Release --target WiFiCapture

```
