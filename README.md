# Base-Rover-Configuration-C099-F9P (Wireless)
This is the tutorial for setting up two Ublox GNSS C099-F9P boards as Base &amp; Rover communication Wireless with RTK corrections.

# Highlights
• Application board for ZED-F9P  
• Flexible connectivity options, including Wi-Fi and Bluetooth  
• Arduino Mega shield connections for host expansion  

# Product description
The C099-F9P application board allows efficient evaluation of ZED-F9P, the u-blox F9 high precision positioning module. The ZED-F9P module provides multi-band GNSS positioning and built-in RTK technology providing centimeter-level accuracy to users. The C099-F9P application board integrates the ZED-F9P module and includes an ODIN-W2 short-range module for connectivity options.
The application board is designed to support the evaluation of the ZED-F9P module, while the ODIN-W2 module provides wireless connectivity capabilities for everyday use cases. Refer to the C099-F9P User Guide for details on supported configurations. The u-center evaluation software provides a powerful platform for
the evaluation of u-blox GNSS receivers. With U-center, data can be logged and visualized in real-time. The u-center software contains an NTRIP server/client which can be used to manage the RTCM correction stream to and from a C099-F9P application board.

<img src="https://content.u-blox.com/sites/default/files/2022-04/C099_Front-withcover_2018-Oct_CMYK.jpg" alt="Image" width="400">

# Setup:

The starting situation will be base on WiFi AP mode and rover in Wifi STA mode. You can use TeraTerm software for serial configurations.  
## Base operation in Wi-Fi AP mode: (Refer to Manual for details)

1. Configure C099-F9P to Wi-Fi AP mode by using the CLI command in the terminal:  
/mem_store/run wifi_ap  
2. Set the C099-F9P Wi-Fi and I2C interfaces to support base operation  
/mem_store/run base  

## Rover operation in Wi-Fi STA mode:
1. Configure C099-F9P to Wi-Fi STA mode by using the CLI command in the terminal:  
/mem_store/run wifi_sta  
2. Set C099-F9P to operate as a rover:  
/mem_store/run rover

Now, once the base and rover are connected (Indicating Purple Light) then we need to set base to a fixed location. You can use U-center software to set the base to a fixed location.  
<img src="https://community.emlid.com/uploads/default/original/2X/e/e785245664e452a3a7519b72c80abb6901dd0cfb.jpg" width="400">  

The .txt files are provided which you need to upload to the board as shown in the manual with the changes:    
• For Base, activate CFG-MSGOUT-RTCM_3X_TYPExxxx_I2C for all types also mentioned in file F9P Base moving base config C99.txt (I've copied the *RTCM*UART1 block and replaced UART1 by I2C).   
• For Rover, upload the F9P Rover config C99.txt as shown in the manual and set rover CFG-I2COUTPROT-NMEA to 0 in order to avoid traffic from rover to base.  

# Results:
Once everything is configured with the changes provided, the yellow RTK LED will glow indicating that the Rover is receiving RTCM corrections.






