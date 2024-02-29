[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.svg?style=flat)](https://github.com/ellerbrock/open-source-badges/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?logo=github&color=%23F7DF1E)](https://opensource.org/licenses/MIT)
![GitHub last commit](https://img.shields.io/github/last-commit/devancakra/Bot-Telegram-based-GPS-monitoring-using-UART-communication)
![Project](https://img.shields.io/badge/Project-Internet%20of%20Things-light.svg?style=flat&logo=arduino&logoColor=white&color=%23F7DF1E)

# Bot-Telegram-based-GPS-monitoring-using-UART-communication
<strong>Proyek Tunggal: Pemantauan GPS berbasis Bot Telegram menggunakan komunikasi UART</strong><br><br>
Pencurian barang sering terjadi di Indonesia. Hal ini bisa terjadi karena kurangnya kesadaran masyarakat dalam menjaga barang-barang pribadi. Oleh karena itu, proyek ini dibuat sebagai upaya untuk meningkatkan keamanan barang, dalam hal ini dengan menambahkan GPS dan komunikasi UART. Proyek ini telah dilaksanakan dan memakan waktu kurang lebih 1 bulan. Ada 2 jenis papan pengembangan yang dipakai. Arduino Pro Micro dipakai untuk menampung data koordinat yang diperoleh dari sensor, kemudian mengirimkan data koordinat ke Wemos D1 Mini. Pengiriman data tersebut menggunakan protokol komunikasi UART: Hardware Serial. Sedangkan Wemos D1 Mini menggunakan protokol komunikasi UART: Software Serial untuk menampung data koordinat tersebut. Selanjutnya, Wemos D1 Mini ini dipakai untuk mengolah data mentah yang ada menjadi informasi yang bermanfaat. Informasi tersebut lalu dikirimkan ke Bot Telegram. Bot Telegram ini dapat merespon pengguna jika ada interaksi. Manfaat dari pembuatan proyek ini tidak lain adalah untuk menambah wawasan. Hasil dari proyek ini yaitu letak koordinat barang pribadi dapat dipantau sewaktu-waktu dengan mudah dan cepat hanya melalui Bot Telegram, sehingga barang yang ada tidak akan mudah dicuri.

<br><br>

## Kebutuhan Proyek
| Bagian | Deskripsi |
| --- | --- |
| Papan Pengembangan | • Arduino Pro Micro Leonardo ATMEGA32U4<br>• Wemos D1 Mini |
| Editor Kode | Arduino IDE |
| Dukungan Aplikasi | Bot Telegram |
| Driver | USB-Serial CH340 |
| Protokol Komunikasi | • Universal Asynchronous Receiver-Transmitter (UART)<br>• MTProto |
| Bahasa Pemrograman | C/C++ |
| Pustaka Arduino | • SoftwareSerial (bawaan)<br>• TinyGPS++<br>• CTBot<br>• ArduinoJson |
| Sensor | GPS NEO6MV2 (x1) |
| Komponen Lainnya | • Kabel Mikro USB - USB tipe A (x1)<br>• Kabel jumper (1 set)<br>• Baterai Li-ion 18650 5V (x1)<br>• Tempat baterai 1 slot (x1)<br>• Kabel Mikro USB - JST 2 pin (x1) |

<br><br>

## Unduh & Instal
1. Arduino IDE

   <table><tr><td width="810">

   ```
   https://www.arduino.cc/en/software
   ```

   </td></tr></table><br>

2. USB-Serial CH340

   <table><tr><td width="810">

   ```
   https://bit.ly/CH340_Driver
   ```

   </td></tr></table>
   
<br><br>

## Rancangan Proyek
<table>
<tr>
<th width="420">Diagram Blok</th>
<th width="420">Diagram Ilustrasi</th>
</tr>
<tr>
<td><img src="https://github.com/devancakra/Telegram-Bot-based-GPS-monitoring-with-UART-communication/assets/54527592/36c483ca-9e5f-4d9d-aed3-95c02a0c73b5" alt="Block-Diagram"></td>
<td><img src="https://github.com/devancakra/Telegram-Bot-based-GPS-monitoring-with-UART-communication/assets/54527592/449a79ca-d05f-4e41-a063-4cbfa5a4221b" alt="Pictorial-Diagram"></td>
</tr>
</table>
<table>
<tr>
<th width="840">Pengkabelan</th>
</tr>
<tr>
<td><img width="840" src="https://github.com/devancakra/Telegram-Bot-based-GPS-monitoring-with-UART-communication/assets/54527592/ca52fea1-8949-4ed9-a398-1ee70edbe938" alt="Wiring"></td>
</tr>
</table>

<br><br>

## Pengetahuan Dasar
Pada dasarnya, suatu perangkat itu dapat dikomunikasikan dengan perangkat lain baik secara nirkabel maupun dengan kabel. Komunikasi antar perangkat keras yang umum digunakan salah satunya adalah ``` Komunikasi Serial ```. Dapat diketahui bersama bahwa ``` Komunikasi Serial ``` ini ada tiga jenis, yaitu meliputi: ``` UART (Universal Asynchronous Receiver-Transmitter) ```, ``` SPI (Serial Peripheral Interface) ```, dan ``` I2C (Inter Integrated Circuit) ```. ``` Komunikasi Serial UART ``` memungkinkan setiap perangkat dapat bertindak sebagai ``` master ``` atau ``` slave ``` secara terbatas. ``` Master ``` adalah perangkat utama yang memiliki otoritas penuh atas kontrol Slave, sedangkan ``` Slave ``` adalah perangkat sekunder yang berada di bawah otoritas perangkat Master. Ada dua macam ``` Komunikasi Serial UART ```, yaitu ``` Hardware Serial ``` dan ``` Software Serial ```.  ``` Komunikasi Hardware Serial ``` dapat dilakukan dengan cara menghubungkan pin ``` TX ``` dan pin ``` RX ``` secara ``` menyilang ``` pada masing-masing papan pengembangan, misalnya: ``` RX-TX ```, kemudian ``` TX-RX ```. Pin ``` TX ``` yaitu untuk ``` mengirim data ```, sedangkan pin ``` RX ``` yaitu untuk ``` menerima data ```. ``` Komunikasi Software Serial ``` ini kurang lebih sama dengan ``` Komunikasi Hardware Serial ``` dalam segi pengkabelan, namun ada perbedaan dalam segi pengkodean. Dengan menggunakan ``` Software Serial ``` inilah anda dapat mengatasi masalah keterbatasan pin ``` RX ``` dan ``` TX ``` yang ada di papan pengembangan. Untuk berkomunikasi dengan ``` Software Serial ``` ini cukup mudah, yaitu dengan menggunakan ``` Pin Digital ``` tertentu sebagai ``` pengganti pin TX dan pin RX ```.<br><br>

``` Arduino Pro Micro ``` memiliki beberapa pin yang dapat mendukung ``` Software Serial ``` yaitu meliputi :

<table width="840">
   <tr>
      <th width="420">Nama Pin</th>
      <th width="420">Mendukung</th>
   </tr>
   <tr>
      <td>8</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>9</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>10</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>16</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>14</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>15</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>Pin Digital lainnya</td>
      <td>Hanya TX</td>
   </tr>
</table><br><br>

``` Wemos D1 Mini ``` memiliki beberapa pin yang dapat mendukung ``` Software Serial ``` yaitu meliputi :

<table width="840">
   <tr>
      <th width="420">Nama Pin</th>
      <th width="420">Mendukung</th>
   </tr>
   <tr>
      <td>D0</td>
      <td>Hanya TX</td>
   </tr>
   <tr>
      <td>D1</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>D2</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>D3</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>D4</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>D5</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>D6</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>D7</td>
      <td>RX dan TX</td>
   </tr>
   <tr>
      <td>D8</td>
      <td>RX dan TX</td>
   </tr>
</table>

<br><br>

## Pengaturan Arduino IDE
1. Buka ``` Arduino IDE ``` terlebih dahulu, kemudian buka proyek dengan cara klik ``` File ``` -> ``` Open ``` :

   <table><tr><td width="810">
   
      • ``` APmicro_gpstracker.ino ```
      
      • ``` WD1mini_bot.ino ```

   </td></tr></table><br>
   
2. Isi ``` Url Pengelola Papan Tambahan ``` di Arduino IDE

   <table><tr><td width="810">
      
      Klik ``` File ``` -> ``` Preferences ``` -> masukkan ``` Boards Manager Url ``` dengan menyalin tautan berikut :
   
      ```
      http://arduino.esp8266.com/stable/package_esp8266com_index.json
      ```

   </td></tr></table><br>
   
3. ``` Pengaturan Board ``` di Arduino IDE

   <table>
      <tr><th>
         
      i
         
      </th><th width="780">
            
      Cara mengatur board ``` Arduino Pro Micro ```
   
      </th></tr>
      <tr><td colspan="2">

      Klik ``` Tools ``` -> ``` Board ``` -> ``` Arduino AVR Boards ``` -> ``` Arduino Micro ```
              
      </td></tr>
   </table><br><table>
      <tr><th>
         
      ii
         
      </th><th width="775">

      Cara mengatur board ``` Wemos D1 Mini ```
            
      </th></tr>
      <tr><td colspan="2">

      • Klik bagian ``` Tools ``` -> ``` Board ``` -> ``` Boards Manager ``` -> Instal ``` esp8266 ```.

      • Kemudian klik ``` Tools ``` -> ``` Board ``` -> ``` ESP8266 Boards ``` -> ``` Wemos D1 Mini ```.
            
      </td></tr>
   </table><br>
   
4. ``` Ubah Kecepatan Papan ``` di Arduino IDE

   <table>
      <tr><th>
         
      i
         
      </th><th width="780">
            
      Cara mengubah kecepatan board ``` Arduino Pro Micro ```
   
      </th></tr>
      <tr><td colspan="2">

      Klik ``` Tools ``` -> ``` Upload Speed ``` -> ``` 9600 ```
              
      </td></tr>
   </table><br><table>
      <tr><th>
         
      ii
         
      </th><th width="775">

      Cara mengubah kecepatan board ``` Wemos D1 Mini ```
            
      </th></tr>
      <tr><td colspan="2">

      Klik ``` Tools ``` -> ``` Upload Speed ``` -> ``` 115200 ```
            
      </td></tr>
   </table><br>
   
5. ``` Instal Pustaka ``` di Arduino IDE

   <table><tr><td width="810">
     
      Unduh semua file zip pustaka. Lalu tempelkan di: ``` C:\Users\Computer_Username\Documents\Arduino\libraries ```

   </td></tr></table><br>

6. ``` Pengaturan Port ``` di Arduino IDE

   <table><tr><td width="810">

      Klik ``` Port ``` -> pilih sesuai dengan port perangkat anda ``` (anda dapat melihatnya di Device Manager) ```
         
   </td></tr></table><br>

7. Ubah ``` Nama WiFi ```, ``` Kata Sandi WiFi ```, dan sebagainya sesuai dengan apa yang anda gunakan saat ini.<br><br>

8. Sebelum mengunggah program, silakan klik: ``` Verify ```.<br><br>

9. Jika tidak ada kesalahan dalam kode program, silakan klik: ``` Upload ```.<br><br>

10. Jika masih ada masalah saat unggah program, maka coba periksa pada bagian ``` driver ``` / ``` port ``` / ``` yang lainnya ```.

<br><br>

## Pengaturan Bot Telegram
1. Buka <a href="https://t.me/botfather">@BotFather</a>.<br><br>

2. Ketik ``` /newbot ```.<br><br>

3. Ketik nama bot yang diinginkan, contoh: ``` personalgps_bot ```.<br><br>

4. Ketik nama pengguna bot yang diinginkan, contoh: ``` personalgps_bot ```.<br><br>

5. Lakukan juga untuk pengaturan gambar bot, deskripsi bot, dan lain sebagainya menyesuaikan dengan kebutuhan anda.<br><br>

6. Salin ``` API token bot telegram anda ``` -> lalu tempelkan pada bagian ``` #define botToken "YOUR_API_BOT_TOKEN" ```. 

   <table><tr><td width="810">
      
   Contohnya :

   ```
   #define botToken "2006772150:AAE6Fdjk3KbiySkzV6CLbd6ClJDzgTfJ5y0"
   ```

   </td></tr></table><br><br>

## Memulai
1. Unduh dan ekstrak repositori ini.<br><br>

2. Pastikan anda memiliki komponen elektronik yang diperlukan.<br><br>
   
3. Pastikan komponen anda telah dirancang sesuai dengan diagram.<br><br>
   
4. Konfigurasikan perangkat anda menurut pengaturan di atas.<br><br>
    
5. Selamat menikmati [Selesai].

<br><br>

## Demonstrasi Aplikasi
Via Telegram: <a href="https://t.me/personalgps_bot">@personalgps_bot</a>

<br><br>

## Sorotan
<table>
<tr>
<th width="840">Perangkat GPS</th>
</tr>
<tr>
<td><img src="https://github.com/devancakra/Telegram-Bot-based-GPS-monitoring-with-UART-communication/assets/54527592/871ea86c-e63b-4304-a211-9a3bd9b4cf53" alt="gps_device"></td>
</tr>
</table>
<table>
<tr>
<th width="840" colspan="2">Bot Telegram</th>
</tr>
<tr>
<td width="420"><img src="https://github.com/devancakra/Telegram-Bot-based-GPS-monitoring-with-UART-communication/assets/54527592/73de4858-b062-4b4c-8457-c7bfe08684e7" alt="telegram_bot1"></td>
<td width="420"><img src="https://github.com/devancakra/Telegram-Bot-based-GPS-monitoring-with-UART-communication/assets/54527592/c6c7e0da-c522-4be8-9e0b-b0dbaa6223cc" alt="telegram_bot2"></td>
</tr>
</table>

<br><br>

## Pengujian Komponen
Anda dapat mengunduh berkas uji komponen melalui tautan berikut: <a href="https://github.com/devancakra/Telegram-Bot-based-GPS-monitoring-with-UART-communication/tree/master/Assets/Component%20Testing">Click Here</a>

<br><br>

## Penafian
Aplikasi ini dibuat dengan menyertakan sumber-sumber dari pihak ketiga. Pihak ketiga di sini adalah penyedia layanan, yang layanannya berupa pustaka, kerangka kerja, dan lain-lain. Saya ucapkan terima kasih banyak atas layanannya. Telah terbukti sangat membantu dan dapat diimplementasikan.

<br><br>

## LISENSI
LISENSI MIT - Hak Cipta © 2024 - Devan C. M. Wijaya, S.Kom

Dengan ini diberikan izin tanpa biaya kepada siapa pun yang mendapatkan salinan perangkat lunak ini dan file dokumentasi terkait perangkat lunak untuk menggunakannya tanpa batasan, termasuk namun tidak terbatas pada hak untuk menggunakan, menyalin, memodifikasi, menggabungkan, mempublikasikan, mendistribusikan, mensublisensikan, dan/atau menjual salinan Perangkat Lunak ini, dan mengizinkan orang yang menerima Perangkat Lunak ini untuk dilengkapi dengan persyaratan berikut:

Pemberitahuan hak cipta di atas dan pemberitahuan izin ini harus menyertai semua salinan atau bagian penting dari Perangkat Lunak.

DALAM HAL APAPUN, PENULIS ATAU PEMEGANG HAK CIPTA DI SINI TETAP MEMILIKI HAK KEPEMILIKAN PENUH. PERANGKAT LUNAK INI DISEDIAKAN SEBAGAIMANA ADANYA, TANPA JAMINAN APAPUN, BAIK TERSURAT MAUPUN TERSIRAT, OLEH KARENA ITU JIKA TERJADI KERUSAKAN, KEHILANGAN, ATAU LAINNYA YANG TIMBUL DARI PENGGUNAAN ATAU URUSAN LAIN DALAM PERANGKAT LUNAK INI, PENULIS ATAU PEMEGANG HAK CIPTA TIDAK BERTANGGUNG JAWAB, KARENA PENGGUNAAN PERANGKAT LUNAK INI TIDAK DIPAKSAKAN SAMA SEKALI, SEHINGGA RISIKO ADALAH MILIK ANDA SENDIRI.
