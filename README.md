# ML1676
Samsung ML1676 MAC Driver
Tested on 

- macOS version：

```
ProductName:		macOS
ProductVersion:		15.3.1
BuildVersion:		24D70

```
- HardwareVersion : MBP2019 Intel
```
Model Name: MacBook Pro
Model Identifier: MacBookPro15,1
Processor Name: 6-Core Intel Core i9
Processor Speed: 2.9 GHz
```

Quick solution：

- Step1: Download the pkg dirver "SamsungPrinterDriversFixed.pkg" and install it

- Step2: Connect ML1676 to your Mac USB port，add printer driver in macOS control center， choose“Samsung ML-1860 Serises” in the driver list

Good Luck！ End  Here.


Slow solution for those who whant to know how it works and come from:
- Step1: Download "Samsung Printer Drivers v2.6 for OS X“ from Apple.https://support.apple.com/kb/dl905?locale=en_US  , then drag the pkg file from the dmg to a place, as ~/Downloads/

- Step2: Unpack the pkg file "SamsungPrinterDrivers.pkg" and bypass two chekings controled by Apple.

- Step3: Rebuild the pkg file with the hacked files.

Step1&Step2:
```
mkdir ML1676
cd ML1676
cp -v ~/Downloads/SamsungPrinterDrivers.pkg ./
pkgutil --expand SamsungPrinterDrivers.pkg ./SamsungPrinterDrivers 
```
then edit the file 'SamsungPrinterDrivers/Distribution' in the SamsungPrinterDrivers  folder

```
# bbedit or code 
code SamsungPrinterDrivers/Distribution
```

add ```return true;``` at the begining of the function ```installationCheck()``` and ``` commonRequirments()``` to bypass the checkings.

Step3:
```
#to show which dir you are in
 $ pwd                                                                
/Users/mac/Desktop/ML1676 

#repack the folder to a new pkg file
pkgutil --flatten SamsungPrinterDrivers SamsungPrinterDriversFixed.pkg
```