## Web config
https://www.obitalk.com/obinet/login/

## HTTP interface
http://192.168.1.195
See Lastpass (obitalk.com) Notes for User/Pass

* Changes in the web portal seem to take effect almost immediately and cause a reboot of the device
* 
## Exporting Config
System Management/Device Update/Backup Configuration

Running Status isn't important just contains runtime detected stuff
AA User Prompts are for the Auto attendant

## Firmware (Manual)
Firmware announcement/procedure is here
http://www.obitalk.com/forum/index.php?topic=9.0
You want OBi2 & OBi3 Series Universal Adapters

[http://www.obihai.com/firmware/OBi2-latest.fw](http://www.obihai.com/firmware/OBi2-latest.fw)

Current FW is 3.2.2 (Build: 5898EX)

Latest is http://fw.obihai.com/OBi202-3-2-2-5921EX-332148940.fw

Cant force it just have to wait for FW to update automatically
In the XML you'll see what the next firmware will be

```
{([1-9]x?*(Mpli)):pp},
{(<##:>):li},
{(<**70:>(Mli)):li},
{(<**82:>(Mbt2)):bt2},
{(<**81:>(Mbt)):bt},
{(<**8:>(Mbt)):bt},
{**0:aa},{***:aa2},
{(<**1:>(Msp1)):sp1},
{(<**2:>(Msp2)):sp2},
{(<**3:>(Msp3)):sp3},
{(<**4:>(Msp4)):sp4},
{(<**9:>(Mpp)):pp},
{(Mpli):pli}
```

```
{([1-9]x?*(Mbt)):bt},{(<##:>):li},{(<**70:>(Mli)):li},{(<**82:>(Mbt2)):bt2},{(<**81:>(Mbt)):bt},{(<**8:>(Mbt)):bt},{**0:aa},{***:aa2},{(<**1:>(Msp1)):sp1},{(<**2:>(Msp2)):sp2},{(<**3:>(Msp3)):sp3},{(<**4:>(Msp4)):sp4},{(<**9:>(Mpp)):pp},{(Mpli):pli}
```

```
([1-9]x?*(Mpli)|[1-9]S9|[1-9][0-9]S9|911|**0|***|#|##|**70(Mli)|**8(Mbt)|**81(Mbt)|**82(Mbt2)|**1(Msp1)|**2(Msp2)|**3(Msp3)|**4(Msp4)|**9(Mpp)|(Mpli))
```
```
([1-9]x?*(Mbt)|[1-9]S9|[1-9][0-9]S9|911|**0|***|#|##|**70(Mli)|**8(Mbt)|**81(Mbt)|**82(Mbt2)|**1(Msp1)|**2(Msp2)|**3(Msp3)|**4(Msp4)|**9(Mpp)|(Mpli))
```
Useful call routing tutorial
https://www.dslreports.com/r0/download/2232642~00ffcbc06b0f67559d67e75ce10ffc98/OBi-DigitMapCallRoute-Tutorial-v1-1.pdf

DigitMap: ([1-9]xxxxxxxxxxx)



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc0MTk0OTMyNiw1MTU3NDU0NTAsLTE4Nj
ExMDgyMzEsNjg0MDc0MjA4LDU4MzQyNjExMSwtMzgzNTM0NDU0
LC0xODk0NjAzMjA3LC0xODkyMTA3NzA5LC0xNDUxMTY3ODEzLD
E3MTk3MzEyMTMsLTE1MjQ0NTgxNTJdfQ==
-->