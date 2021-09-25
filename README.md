# Jarkom-Modul-1-C14-2021
Praktikum Jaringan Komputer Modul 1 - Crimping dan Wireshark

### Nama Anggota Kelompok:
1. 5111940000059      Dido Fabian Fayed <br>
2. 5111940000074	    Nur Ahmad Khatim <br>
3. 5111940000162	    Ramadhan Arif Hardijansyah

## Soal 1
Sebutkan webserver yang digunakan pada "ichimarumaru.tech"! 
### Cara Pengerjaan

## Soal 2
Temukan paket dari web-web yang menggunakan basic authentication method!
### Cara Pengerjaan

## Soal 3
Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!
### Cara Pengerjaan

## Soal 4
Temukan paket mysql yang mengandung perintah query select!
### Cara Pengerjaan

## Soal 5
Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!
### Cara Pengerjaan

## Soal 6
Cari username dan password ketika melakukan login ke FTP Server!
### Cara Pengerjaan
Wireshark filter expression : 
```ftp.request.command == PASS || ftp.request.command == USER
```
Maka akan muncul packet sebaga yang berisi `username` dan `password` yang digunakan untuk melakukan login ke FTP server
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/6_1.png)

## Soal 7
Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")
### Cara Pengerjaan
Wireshark filter expression : 
```ftp-data contains Real.pdf
```
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/7_1_Filter.png)
Show data as `Raw` lalu simpan sebagai file (save as) `.pdf`
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/7_2_Raw.png)
Buka file `.pdf` yang sudah disimpan
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/7_3_PDF.png)

## Soal 8
Cari paket yang menunjukan pengambilan file dari FTP tersebut!
### Cara Pengerjaan


## Soal 9
Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!
### Cara Pengerjaan
Wireshark filter expression : 
```ftp-data.command contains “secret.zip”
```
akan muncul tampilan seperti berikut:
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/9_1_Filter.png)
Show data as `Raw` lalu simpan sebagai file (save as) `.zip`
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/9_2_Raw.png)
Maka file sudah terunduh namun kita masih diminta untuk mendapatkan password untuk membukanya
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/9_3_ZIP.png)

## Soal 10
Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!
### Cara Pengerjaan
Wireshark filter expression : 
``` 
ftp-data.command contains “history.txt”, 
``` 
akan muncul tampilan packet sebagai berikut: 
<br>
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/10_1_Filter_History.png)
<br>
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/10_2_ASCII.png)

Didapati password ada di dalam `bukanapaapa.txt`  
Wireshark filter expression : 
```
ftp-data.command contains “bukanaapa.txt”
```
Output:
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/10_3_Filter_Bukanaapa.png)
Follow tcp stream, dan didapatkan password-nya 
<br> Password
```
d1b1langbukanapaapajugagapercaya`
```
Output:
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/10_4_ASCII.png)
<br>
Buka file zip yang sudah diunduh sebelumnya lalu
masukkan password yang didapatkan
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/10_5_Open_ZIP.png)
<br> Output pdf:
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/10_6_PDF.png)


## Soal 11
Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!
### Cara Pengerjaan
Wireshark filter expression untuk capture filter:
```
tcp src port 80
```
Wireshark filter expression:
```
tcp.port == 80
```
Output:
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/11_1.png)

## Soal 12
Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
### Cara Pengerjaan
Wireshark filter expression untuk capture filter:
```
port 21
```
Output:
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/12_1.png)

## Soal 13
Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!
### Cara Pengerjaan
Wireshark filter expression untuk capture filter:
```
dst port 443
```
Output:
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/13_1.png)

## Soal 14
Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!
### Cara Pengerjaan
Wireshark filter expression untuk capture filter:
```
dst host kemenag.go.id
```
Output:
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/14_1.png)

## Soal 15
Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
### Cara Pengerjaan
Buka Command Prompt, ketik `ipconfig` dan tekan enter
```
ipconfig
```
Output:
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/15_1_CheckIP.png)

Terlihat pada Wireless LAN adapter Wi-FI didapatkan IPv4 Address: `192.168.1.6`. Simpan IP address ini untuk mengambil paket dari IP address tersebut.

Wireshark filter expression untuk capture filter:
```
src host 192.168.1.6
```
Output:
![ssmodul1](https://github.com/DidoFayed/jarkom-modul-1-C14-2021/blob/main/ssmodul1/15_2_Filter.png)

## Kendala yang Dialami Selama Pengerjaan
1. ...
2. ...
