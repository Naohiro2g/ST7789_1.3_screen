Gerber data for breakout board

## How to use the display as main screen of Raspberry Pi.

#### Add three lines to the file
`/etc/modules`

```
spi-bcm2835
flexfb
fbtft_device
```

#### Make a new file with two lines.
`/etc/modprobe.d/fbtft.conf`

```
options fbtft_device name=flexfb speed=32000000 gpios=reset:27,dc:25
options flexfb setaddrwin=0 width=240 height=240 init=-1,0x11,-2,120,-1,0x36,0x00,-1,0x3A,0x05,-1,0xB2,0x0C,0x0C,0x00,0x33,0x33,-1,0xB7,0x35,-1,0xBB,0x1A,-1,0xC0,0x2C,-1,0xC2,0x01,-1,0xC3,0x0B,-1,0xC4,0x20,-1,0xC6,0x0F,-1,0xD0,0xA4,0xA1,-1,0x21,-1,0xE0,0x00,0x19,0x1E,0x0A,0x09,0x15,0x3D,0x44,0x51,0x12,0x03,0x00,0x3F,0x3F,-1,0xE1,0x00,0x18,0x1E,0x0A,0x09,0x25,0x3F,0x43,0x52,0x33,0x03,0x00,0x3F,0x3F,-1,0x29,-3
```

#### make fbcp command and install

```
git clone https://github.com/tasanakorn/rpi-fbcp</span>
cd rpi-fbcp/
mkdir build
cd build
cmake ..
make
sudo install fbcp /usr/local/bin/fbcp
```


#### Add a line to kick the fbcp at startup
`/etc/rc.local`

```
fbcp &
```  
  


#### Rotation settings
`/boot/config/txt`

```
hdmi_force_hotplug=1
hdmi_cvt=240 240 60 1 0 0 0
hdmi_group=2
hdmi_mode=1
hdmi_mode=87
#display_rotate = 1 # Upside down
display_rotate=2 #Right way up
#display_rotate=3 # Left
```




# ST7789_1.3_screen
ST7789_1.3_screen

Blog post - https://facelesstech.wordpress.com/2019/01/27/1-3-screen-with-raspberry-pi/

