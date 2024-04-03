# Jarkom-Modul-1-IT02-2024

Kelompok IT02 :
| Nama | NRP |
| -------------------- | ---------- |
| Samuel Yuma Krismata | 5027221029 |
| Marselinus Krisnawan Riandika | 5027221056 |

## Daftar Isi

[creds](#creds)</br>
[ATM or ATP or FTP ? 🤔](#atm-or-atp-or-ftp--🤔)</br>
[How Many packets ?!](#how-many-packets)</br>
[trace him](#trace-him)</br>
[mawleoleo](#malwleoleo)</br>
[whoami](#whoami)</br>
[fuzz](#fuzz)</br>
[evidence](#evidence)</br>
[secrets](#secrets)</br>
[malwaew](#malwaew)</br>

## creds

### Soal

Attacker menyadari jika dia bisa membuat clone ftp server dari target, temukan kredensialn dari server ftp yang dibuat oleh attacker

### Penyelesaian

Berdasarkan soal, kita diminta untuk menemukan credential dari server FTP, sehingga kita dapat menerapkan display filter `tcp` dan filter menggunakan string `login`.

![Screenshot 2024-04-02 130240](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/65670e64-736e-4b7b-9642-62fd1786098a)

Dari hasil filtering tersebut, ditemukan sebuah packet yang berisi info `Login Successful` . Selanjutnya, isi dari packet tersebut dianalisis dengan menggunakan follow TCP Stream

![image](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/992966b2-13cc-4cb7-80df-d4eb4f5d9ae1)

Dari hasil analisis, diperoleh credential seperti yang tertera pada screenshot. Selanjutnya credential tersebut digunakan untuk mengerjakan soal

![Screenshot 2024-03-30 211719](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/a0777494-f8af-490f-b7b6-146f78c7c931)

Dari hasil pengerjaan soal, diperoleh flag `JARKOM2024{s3curE_uR_FtP_IJ8lPbnygRFHC4Y}`

## ATM or ATP or FTP ? 🤔

### Soal

Pradityo mencoba mengembangkan server ftp, tetapi seseorang mencoba melakukan bruteforce login, bisakah Anda menganalisis apa yang terjadi?

### Penyelesaian

Berdasarkan soal, kita diminta untuk menganalisis bruteforce login yang terjadi, sehingga kita dapat melakukan display filter `tcp`

![Screenshot 2024-04-02 161430](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/f63d6c33-321b-4d90-a71e-706ee7a25ac5)

Selanjutnya, karena kita akan mencari response login yang berhasil dilakukan sehingga kita dapat melakukan filter menggunakan string `Response: 230` yang mana kode `230` sendiri adalah salah satu kode FTP yang muncul setelah client memasukkan password yang berhasil

![Screenshot 2024-04-02 161715](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/86b660f8-a524-4ce3-b17c-1fc9df232a38)

Dari hasil filtering tersebut, packet yang dicari berhasil ditemukan dan isi dari packet tersebut akan dianalisis dengan menggunakan follow TCP Stream dan dari hasil analisis, akan diperoleh sebuah password yang kemudian digunakan untuk mengerjakan soal

![Screenshot 2024-03-30 212748](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/31ee327b-32ee-417f-89ff-a236d05c87c0)

Dari hasil pengerjaan soal, diperoleh flag `JARKOM2024{Brut3f0rce_FtP_IhrlP79tQAVHC8Y}`

## How Many packets?!

### Soal

Sebagai kewajiban untuk laporan, aku diminta untuk mencari tahu berapa kali attempt login yang dilakukan oleh hacker. Dapatkah kamu membantuku untuk menganalisanya?

### Penyelesaian

Berdasarkan soal, kita diminta untuk mecari berapa banyak attempt yang dilakukan oleh hacker. Maka dari itu Kita hitung jumlah dari login yang terdapat dari TCP stream. Seperti pada screenshoot dibawah, apabila kita hitung secara manual, maka akan keluar angka 934. Dan pada saat dicoba dimasukkan pada soal, hasilnya benar.

![paket](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/143835215/9fad7308-1baa-4a40-9094-eeea3b9721d0)

Dari hasil pengerjaan soal, diperoleh flag `JARKOM2024{C0unt_uR_P4cket5_9JwkRbxjgAdo88t}`

## trace him

Selain menghitung jumlah packet, coba lacak juga ip penyerang tersebut!

### Soal

### Penyelesaian

Pertama tama kita lihat terlebih dahulu pada bagian dimana penyerang melakukan sebuah request. Kemudian setelah di klik, kita lihat ke bagian kiri bawah.

![image](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/143835215/8a999e9d-8ae2-4d5b-99f1-0d28956ebeb2)

Dapat dilihat pada bagian kiri bawah terdapat internet protocol Version 4, klik pada bagian itu. Kemudian seperti pada screenshot dibawah, akan ada source address. source address tersebut merupakan ip dari penyerang tersebut

![IPbjir](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/143835215/66389fa8-15c6-4a44-ab00-bc0a15e8684c)


Dari hasil pengerjaan soal, diperoleh flag `JARKOM2024{Wh3re'5_thE_S4uce_c6wRRbxtlRVoCr9}`

## malwleoleo

### Soal

Dapatkah kamu menemukan file malware yang dikirim oleh attacker melalui ftp?

### Penyelesaian

Pada soal, kita diminta untuk mencari nama file yang dikirim oleh attacker, untuk mencarinya, kita harus membuka TCP stream, kemudian setelah berada pada TCP stream, Kita cari stream dimana terdapat suatu nama file, Pada Kasus ini, nama filenya ialah m4L1c10us_W4re.c, seperti screenshot dibawah

![image](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/143835215/38233a7c-9950-4445-984c-dd661b6dff22)

Kemudian pada saat kita coba memasukkan m4L1c10us_W4re.c seperti pada screenshot dibawah, didapatkan Flag

![malwer](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/143835215/91f9589a-3c4c-46db-a4d4-527270114336)

Dari hasil pengerjaan soal, diperoleh flag `JARKOM2024{beC4refUl_0f_m4lwAr3_uJwkRznfQAFoC4q}`

## whoami

### Soal

Dapatkah kamu menemukan siapa identitas attacker?

### Penyelesaian

Berdasarkan soal, kita diminta untuk menemukan identitas attacker. Untuk itu, kita dapat melakukannya dengan follow TCP Stream 7 yang mana terdapat sebuah pesan yang harus dicode terlebih dahulu dengan base64

![image](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/e8e89c9d-9bfd-43a4-ad0b-9572cbe569a8)

Setelah decode selesai, diperoleh nama dari attacker yang digunakan untuk mengerjakan soal

![Screenshot 2024-03-30 220022](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/159bf6fb-1c25-4309-bd0f-a8410d696256)

Dari hasil pengerjaan soal, diperoleh flag `JARKOM2024{s3curE_uR_FtP_I6frVBPhLavEca9}`

## fuzz

### Soal

My website got hacked. Can you analyze this network traffic to help me track the attacker?

### Penyelesaian

Berdasarkan soal, kita diminta untuk melacak attacker. Untuk itu, kita dapat memantau TCP Stream 0 yang mana terdapat beberapa informasi yang dapat digunakan untuk menjawab soal

![Screenshot 2024-03-30 223738](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/aa611223-aae4-4117-898b-b920dc8ac98c)

Untuk menjawab soal berikutnya, kita perlu melakukan follow TCP Stream 1 dan disitu akan diperoleh nama tool yang dipakai untuk bruteforce login

![image](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/1d84d7eb-fb15-4bdd-9bd6-40a86ae83f39)

Untuk menjawab soal berikutnya, kita perlu menganalisis isi dari follow TCP Stream 1 untuk mendapatkan credential yang digunakan oleh attacker. Hal tersebut dapat dilakukan dengan mencari HTTP response `302 Found`

![Screenshot 2024-03-30 225842](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/3a754514-5c4b-40ad-81a5-6e5808f66287)

Dari hasil pengerjaan soal, diperoleh flag `JARKOM2024{s3m4ng4t_ya_<3_uhfCX7AtQRkH88B}`

## evidence

### Soal

Perusahaan nanomate baru saja kebobolan. Mereka menyewamu untuk mencari tahu bagaimana caranya pelaku bisa masuk.

### Penyelesaian

Untuk mengerjakan soal ini, pertama kita dapat melakukan follow pada salah satu HTTP Stream yang ada

![image](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/c9c47945-5734-45cc-b63c-fd84e5e2c450)

Dari hasil tersebut, diperoleh nama perusahaan dan web server untuk menjawab soal. Selanjutnya, kita akan mencari endpoint yang mana dapat diperoleh dengan menggunakan filter `http` dan scroll hingga menemukan endpoint `/app/includes/process_login.php` yang digunakan untuk menjawab soal

![image](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/c1efdf05-c861-40b1-b24c-d3bbcb79c496)

Terakhir, kita akan mencari credential dari pelaku yang dapat dilakukan dengan follow TCP Stream 1240 yang mana didalamnya terdapat informasi `Login Successful`

![image](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/d6dda3a4-c419-404a-8caf-014974b481f3)

![Screenshot 2024-03-30 221351](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/ecd25540-c8c1-493f-9566-1857329f845a)

Dari hasil pengerjaan soal, diperoleh flag `JARKOM2024{m4innya_h3bat_uhCkXb9HyAdel89}`

## secrets

### Soal

Temukan pesan rahasia dari attacker

### Penyelesaian

Untuk mengerjakan soal ini, pertama kita dapat menganalisis TCP Stream 14 yang mana didalamnya terdapat informasi tentang 2 file yang berbeda, yaitu ` m4L1c10us_W4re.c``` dan  `mirza.jpg` . Karena file ```m4L1c10us_W4re.c``` berisi pesan terenkripsi yang mengandung nama dari attacker, maka kita akan menganalisis file ```mirza.jpg```dengan cara `Exports Object > FTP-DATA`dan diperoleh teks`MIO MIRZA` sebagai jawaban dari soal

![Screenshot 2024-03-30 233217](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/118542326/0b413a5a-e468-446c-bbbc-cca00fa71dca)

Dari hasil pengerjaan soal, diperoleh flag `JARKOM2024{l0_Blm_tW_MIO_MIRZA?_uTr8R7pyiRVHCrq}`

## malwaew

Pada percobaan malwaew, disini kita diminta untuk mencari SHA 256 dari malware yang dimaksud oleh soal. 

Pada percobaan ini, pertama tama kita masuk ke bagian preferences dari wireshark, kemudian menuju ke bagian protocol TLS seperti pada screenshot dibawah ini 

![image](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/143835215/db143786-6271-4952-9086-de7212ca2b66)

Kemudian kita masukkan keylog pada PreMaster Secret log filename, kemudian klik ok. Kemudian kita beralih ke file > export HTTP seperti pada screenshot dibawah.

![image](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/143835215/9307e89f-ee99-4594-990e-9225fe0e0009)

Setelah itu klik pada filename invest_20.dll , kemudian klik save.

![image](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/143835215/8b152cbe-2f40-4f58-85b1-0ad531f3f84c)

Pada screenshot diatas, file yang sudah di save saya pindahkan menuju ke linux kemudian dengan command `sha256sum` didapatkan SHA256 dari invest_20.dll 

![image](https://github.com/samuelyuma/Jarkom-Modul-1-IT02-2024/assets/143835215/104733d0-44d2-47a3-894f-6683404e8a28)

Kemudian pada saat sha dicoba dimasukkan, maka kita mendapatkan Flag: `JARKOM2024{wow_how_u_solve_this_chfRYcnyy6FsRrB}`


