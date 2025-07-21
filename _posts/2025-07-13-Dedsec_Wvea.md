
<p align="center">
<img src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExNjZvOWpmM2Frc3gyc25vaGJ6YWZydDZtcjE5cGgzYXRwNjQ1cXd2eSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xTcnTkOxwiOUdVIZiw/giphy.gif", width="300", height="300">
</p>

<h1 align="center">DEDSEC_WVEA</h1>
<h4 align="center">Wifi Vendo Exhaustion Attack</h4>

### DESCRIPTION
DEDSEC_WVEA is a WiFi Vendo exhaustion attack tool designed to demonstrate how easily public WiFi vendo systems can be disrupted through basic network abuse.

The tool works by sending a large number of fake connection attempts to overwhelm the vendo system. As a result, the vendo becomes overloaded and unable to handle new connections from real users, preventing them from accessing the service or purchasing data.

### INSTALLATION
    git clone https://github.com/0xbitx/DEDSEC_WVEA.git
    cd DEDSEC_WVEA
    sudo pip3 install scapy tabulate psutil pyudev
    chmod +x dedsec_wvea 
    ./dedsec-wvea
    
    or
    
    sudo apt install ./dedsec-wvea.deb
    dedsec-wvea
  
### TESTED ON FOLLOWING
* Kali Linux 
* Parrot OS 

## Legal Disclaimer

This tool is intended for educational and security research purposes only. Unauthorized usage may be illegal in your jurisdiction. The author is not responsible for any misuse of this tool.

