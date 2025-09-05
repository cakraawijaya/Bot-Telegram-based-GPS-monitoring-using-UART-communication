[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.svg?style=flat)](https://github.com/ellerbrock/open-source-badges/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?logo=github&color=%23F7DF1E)](https://opensource.org/licenses/MIT)
![GitHub last commit](https://img.shields.io/github/last-commit/cakraawijaya/Bot-Telegram-based-GPS-monitoring-using-UART-communication?logo=Codeforces&logoColor=white&color=%23F7DF1E)
![Project1](https://img.shields.io/badge/Project-%2D1-Arduino-light.svg?style=flat&logo=arduino&logoColor=white&color=%23F7DF1E)
![Project2](https://img.shields.io/badge/Project-%2D2-Wemos-light.svg?style=flat&logo=espressif&logoColor=white&color=%23F7DF1E)
![Type](https://img.shields.io/badge/Type-Personal%20Experiment-light.svg?style=flat&logo=gitbook&logoColor=white&color=%23F7DF1E)

# Bot Telegram-based GPS monitoring using UART communication
Theft of goods is rampant in Indonesia today because it is first influenced by economic factors, then the lack of awareness from the local community in protecting their personal belongings, thus creating opportunities for thieves to be able to act. Therefore, this project was created as an effort to improve the security of goods in close proximity. In this case, the author tries to use the UART protocol on the Arduino and Wemos side. This project has been implemented and took approximately 1 month. There are 2 types of development boards used. Arduino Pro Micro is used to hold the coordinate data obtained from the sensor, then send the coordinate data to Wemos D1 Mini using UART communication protocol: Hardware Serial. While the Wemos D1 Mini is used to accommodate coordinate data from the Arduino Pro Micro using the UART communication protocol: Software Serial. Furthermore, the raw data that has been received is processed into useful information, then sent to the Telegram Bot. This Telegram bot can respond to users if there is interaction in it. The benefit of making this project is none other than to add insight. The result of this project is that the coordinates of personal items can be monitored at any time easily and quickly only through Telegram Bot, so that existing items will not be easily stolen.

<br><br>

## Project Requirements
| Part | Description |
| --- | --- |
| Development Board | • Arduino Pro Micro Leonardo ATMEGA32U4<br>• Wemos D1 Mini |
| Code Editor | Arduino IDE |
| Application Support | Telegram Bot |
| Driver | CH340 USB Driver |
| Communications Protocol | • Universal Asynchronous Receiver-Transmitter (UART)<br>• MTProto |
| IoT Architecture | 3 Layer |
| Programming Language | C/C++ |
| Arduino Library | • SoftwareSerial (default)<br>• TinyGPS++<br>• CTBot<br>• ArduinoJson |
| Sensor | GPS NEO6MV2 (x1) |
| Other Components | • Micro USB cable - USB type A (x1)<br>• Jumper cable (1 set)<br>• Li-ion battery 18650 5V (x1)<br>• 1-Slot battery holder (x1)<br>• Micro USB cable - 2 pin JST (x1) |

<br><br>

## Download & Install
1. Arduino IDE

   <table><tr><td width="810">
         
   ```
   https://bit.ly/ArduinoIDE_Installer
   ```

   </td></tr></table><br>
   
2. CH340 USB Driver

   <table><tr><td width="810">
   
   ```
   https://bit.ly/CH340_USBdriver
   ```
   
   </td></tr></table>
   
<br><br>

## Project Designs
<table>
<tr>
<th width="840">Infrastructure</th>
</tr>
<tr>
<td><img src="Assets/Documentation/Diagram/Infrastructure.jpg" alt="infrastructure"></td>
</tr>
</table>
<table>
<tr>
<th width="420">Block Diagram</th>
<th width="420">Pictorial Diagram</th>
</tr>
<tr>
<td><img src="Assets/Documentation/Diagram/Block Diagram.jpg" alt="block-diagram"></td>
<td><img src="Assets/Documentation/Diagram/Pictorial Diagram.jpg" alt="pictorial-diagram"></td>
</tr>
</table>
<table>
<tr>
<th width="840">Wiring</th>
</tr>
<tr>
<td><img src="Assets/Documentation/Table/Device Wiring.jpg" alt="wiring"></td>
</tr>
</table>

<br><br>

## Basic Knowledge
Basically, a device can be communicated with other devices either wirelessly or by cable. Communication between commonly used hardware is ``` Serial Communication ```. It can be known that there are three types of ``` Serial Communication ```, which include: ``` UART (Universal Asynchronous Receiver-Transmitter) ```, ``` SPI (Serial Peripheral Interface) ```, and ``` I2C (Inter Integrated Circuit) ```. ``` Serial UART communication ``` allows each device to act as a ``` master ``` or ``` slave ``` in a limited way. ``` Master ``` is the primary device that has full authority over the control of the Slave, while the ``` Slave ``` is the secondary device that is under the authority of the Master device. There are two kinds of ``` UART Serial Communication ```, namely ``` Hardware Serial ``` and ``` Software Serial ```. ``` Hardware serial communication ``` can be done by connecting the ``` TX ``` and ``` RX ``` pins ``` crosswise ``` on each development board, for example: ``` RX-TX ```, then ``` TX-RX ```. The ``` TX ``` pin is for ``` sending data ```, while the ``` RX ``` pin is for ``` receiving data ```. ``` Serial Software Communication ``` is more or less the same as ``` Serial Hardware Communication ``` in terms of cabling, but there are differences in terms of coding. By using this ``` Serial Software ``` you can overcome the constraints of the limitations of ``` RX ``` and ``` TX ``` pins on the development board. To communicate with this ``` Serial Software ``` is quite easy, namely by using certain ``` Digital Pins ``` as a ``` substitute for TX pins and RX pins ```.<br><br>

The ``` Arduino Pro Micro ``` has several pins that can support ``` Software Serial ``` which include :

<table width="840">
   <tr>
      <th width="420">Pin Name</th>
      <th width="420">Support</th>
   </tr>
   <tr>
      <td>8</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>9</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>10</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>16</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>14</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>15</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>Other Digital pins</td>
      <td>TX only</td>
   </tr>
</table><br><br>

The ``` Wemos D1 Mini ``` has several pins that can support ``` Software Serial ``` which include :

<table width="840">
   <tr>
      <th width="420">Pin Name</th>
      <th width="420">Support</th>
   </tr>
   <tr>
      <td>D0</td>
      <td>TX only</td>
   </tr>
   <tr>
      <td>D1</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>D2</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>D3</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>D4</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>D5</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>D6</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>D7</td>
      <td>RX and TX</td>
   </tr>
   <tr>
      <td>D8</td>
      <td>RX and TX</td>
   </tr>
</table><br>

Wemos D1 Mini Pinout Reference : <a href="Assets/Documentation/Pinout/Wemos D1 Mini.jpg">Click Here</a>

<br><br>

## Arduino IDE Setup
1. Open the ``` Arduino IDE ``` first, then open the project by clicking ``` File ``` -> ``` Open ``` :

   <table><tr><td width="810">
   
      • ``` APmicro_gpstracker.ino ```
      
      • ``` WD1mini_bot.ino ```

   </td></tr></table><br>
   
2. Fill in the ``` Additional Board Manager URLs ``` in Arduino IDE

   <table><tr><td width="810">
      
      Click ``` File ``` -> ``` Preferences ``` -> enter the ``` Boards Manager Url ``` by copying the following link :
   
      ```
      http://arduino.esp8266.com/stable/package_esp8266com_index.json
      ```

   </td></tr></table><br>
   
3. ``` Board Setup ``` in Arduino IDE

   <table>
      <tr><th>
         
      i
         
      </th><th width="780">
            
      How to setup the ``` Arduino Pro Micro ``` board
   
      </th></tr>
      <tr><td colspan="2" width="780">

      Select a board by clicking: ``` Tools ``` -> ``` Board ``` -> ``` Arduino AVR Boards ``` -> ``` Arduino Micro ```
              
      </td></tr>
   </table><br><table>
      <tr><th>
         
      ii
         
      </th><th width="775">

      How to setup the ``` Wemos D1 Mini ``` board
            
      </th></tr>
      <tr><td colspan="2" width="775">

      • Click ``` Tools ``` section -> ``` Board ``` -> ``` Boards Manager ``` -> Install ``` esp8266 ```.

      • Then selecting a board by clicking: ``` Tools ``` -> ``` Board ``` -> ``` ESP8266 Boards ``` -> ``` Wemos D1 Mini ```.
            
      </td></tr>
   </table><br>
   
4. ``` Change the Board Speed ``` in Arduino IDE

   <table>
      <tr><th>
         
      i
         
      </th><th width="780">
            
      How to change the speed of ``` Arduino Pro Micro ``` board
   
      </th></tr>
      <tr><td colspan="2" width="780">

      Click ``` Tools ``` -> ``` Upload Speed ``` -> ``` 9600 ```
              
      </td></tr>
   </table><br><table>
      <tr><th>
         
      ii
         
      </th><th width="775">

      How to change the speed of ``` Wemos D1 Mini ``` board
            
      </th></tr>
      <tr><td colspan="2" width="775">

      Click ``` Tools ``` -> ``` Upload Speed ``` -> ``` 115200 ```
            
      </td></tr>
   </table><br>
   
5. ``` Install Library ``` in Arduino IDE

   <table><tr><td width="810">
         
      Download all the library zip files. Then paste it in the: ``` C:\Users\Computer_Username\Documents\Arduino\libraries ```

   </td></tr></table><br>

6. ``` Port Setup ``` in Arduino IDE

   <table><tr><td width="810">
         
      Click ``` Port ``` -> Choose according to your device port ``` (you can see in device manager) ```

   </td></tr></table><br>

7. Change the ``` WiFi Name ```, ``` WiFi Password ```, and so on according to what you are currently using.<br><br>

8. Before uploading the program please click: ``` Verify ```.<br><br>

9. If there is no error in the program code, then please click: ``` Upload ```.<br><br>

10. If there is still a problem when uploading the program, then try checking the ``` driver ``` / ``` port ``` / ``` others ``` section.

<br><br>

## Telegram Bot Setup
1. Open <a href="https://t.me/botfather">@BotFather</a>.<br><br>

2. Type ``` /newbot ```.<br><br>

3. Type the desired bot name, for example: ``` personalgps_bot ```.<br><br>

4. Type the desired bot username, for example: ``` personalgps_bot ```.<br><br>

5. Also do it for bot image settings, bot descriptions, and so on according to your needs.<br><br>

6. Copy ``` your telegram bot API token ``` -> then paste it into the ``` #define botToken "YOUR_API_BOT_TOKEN" ``` section. 

   <table><tr><td width="810">
      
   For example :

   ```ino
   #define botToken "2006772150:AAE6Fdjk3KbiySkzV6CLbd6ClJDzgTfJ5y0"
   ```
   
   </td></tr></table><br><br>

## Get Started
1. Download and extract this repository.<br><br>
   
2. Make sure you have the necessary electronic components.<br><br>
   
3. Make sure your components are designed according to the diagram.<br><br>
   
4. Configure your device according to the settings above.<br><br>

5. Please enjoy [Done].

<br><br>

## Demonstration of Application
Via Telegram: <a href="https://t.me/personalgps_bot">@personalgps_bot</a>

<br><br>

## Highlights
<table>
<tr>
<th width="840">GPS Device</th>
</tr>
<tr>
<td><img src="Assets/Documentation/Experiment/GPS Device.jpg" alt="gps_device"></td>
</tr>
</table>
<table>
<tr>
<th width="840" colspan="2">Telegram Bot</th>
</tr>
<tr>
<td width="420"><img src="Assets/Documentation/Experiment/Telegram Bot-1.jpg" alt="telegram_bot1"></td>
<td width="420"><img src="Assets/Documentation/Experiment/Telegram Bot-2.jpg" alt="telegram_bot2"></td>
</tr>
</table>

<br><br>

## Component Testing
You can download the component test file via the following link: <a href="https://github.com/devancakra/Telegram-Bot-based-GPS-monitoring-with-UART-communication/tree/master/Assets/Component%20Testing">Click Here</a>

<br><br>

## <img src="https://github.com/user-attachments/assets/932b96eb-cbc7-42f1-8938-43cb431889a5" width="16" height="16"> Notes
<blockquote>
   If the item is out of the range of the router, it can be completely lost. To overcome this shortcoming, you can add a GSM module that comes with a SIM card in future research.
</blockquote>

<br><br>

## Appreciation
If this work is useful to you, then support this work as a form of appreciation to the author by clicking the ``` ⭐Star ``` button at the top of the repository.

<br><br>

## Disclaimer
This application is my own work and is not the result of plagiarism from other people's research or work, except those related to third party services which include: libraries, frameworks, and so on.

<br><br>

## LICENSE
MIT License - Copyright © 2024 - Devan C. M. Wijaya, S.Kom

Permission is hereby granted without charge to any person obtaining a copy of this software and the software-related documentation files to deal in them without restriction, including without limitation the right to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons receiving the Software to be furnished therewith on the following terms:

The above copyright notice and this permission notice must accompany all copies or substantial portions of the Software.

IN ANY EVENT, THE AUTHOR OR COPYRIGHT HOLDER HEREIN RETAINS FULL OWNERSHIP RIGHTS. THE SOFTWARE IS PROVIDED AS IS, WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, THEREFORE IF ANY DAMAGE, LOSS, OR OTHERWISE ARISES FROM THE USE OR OTHER DEALINGS IN THE SOFTWARE, THE AUTHOR OR COPYRIGHT HOLDER SHALL NOT BE LIABLE, AS THE USE OF THE SOFTWARE IS NOT COMPELLED AT ALL, SO THE RISK IS YOUR OWN.
