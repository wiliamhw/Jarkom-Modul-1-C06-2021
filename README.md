# Jarkom-Modul-1-C06-2021

## Anggota Kelompok : 
- 05111940000004 | Nizar Mayraldo
- 05111940000087 | William Handi Wijaya
- 05111940000202 | Muhammad Naufaldillah

## Jawaban Praktikum
### 1. Sebutkan webserver yang digunakan pada [ichimarumaru.tech](http://ichimarumaru.tech/)!
Jawab:  
```
nginx/1.18.0 (Ubuntu)
Filter Expression: http.host == "ichimarumaru.tech"
```
Screenshot:  
![1a](https://user-images.githubusercontent.com/52129348/134642662-80dc0d62-4cde-4ded-b3e9-30c9ad8fbaed.png)
![1b](https://user-images.githubusercontent.com/52129348/134642762-8c16b487-547b-4241-914c-1295fc4992cb.png)



### 2. Temukan paket dari web-web yang menggunakan basic authentication method!
Jawab:  
```
Filter Expression: http.authbasic
Filter Expression: http.request.uri contains "login"
```
Screenshot:  
![2a](https://user-images.githubusercontent.com/68325900/134654242-e329b6b4-5541-4d6d-b2b2-8de000c43192.png)
![2b](https://user-images.githubusercontent.com/68325900/134654416-d36a1b52-028a-4751-b1e1-e6bf9fabc778.png)
![2c](https://user-images.githubusercontent.com/68325900/134654450-cc43ad3f-708f-4f8e-8baf-cd46d243ee26.png)
![2d](https://user-images.githubusercontent.com/68325900/134654532-d9a2c092-d87b-4724-987d-92d1e2737924.png)


### 3. Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!
Jawab:  
```
Filter Expression: http.host == basic.ichimarumaru.tech
```
Screenshot:  


### 4. Temukan paket mysql yang mengandung perintah query select
Jawab:  
```
Filter Expression: mysql.query contains "select" || mysql.query contains "SELECT"
```
Screenshot:  
![4a](https://user-images.githubusercontent.com/68325900/134654754-5e4bf6cc-afd9-4c92-90cf-e2802861411f.png)
![4b](https://user-images.githubusercontent.com/68325900/134654791-f9c3dd77-8504-40e6-b033-0a5e8cd336b5.png)
![4c](https://user-images.githubusercontent.com/68325900/134654804-449fd747-81ef-4cee-aaf3-d4b7c81a5755.png)


### 5. Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!
Jawab:  
```
Filter Expression: mysql.query contains "INSERT"
```
Screenshot:  


### 6. Cari username dan password ketika melakukan login ke FTP Server!
Jawab:  
```
Filter Expression: ftp.request.command == USER || ftp.request.command == PASS
```
Screenshot:  
![6](https://user-images.githubusercontent.com/52129348/134644331-02b5cd10-a70c-4a6e-aa6b-55672fca4a5e.png)


### 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama `0.zip, 1.zip, 2.zip, ..., 499.zip`. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya `Real.pdf`)
Jawab:  
```
Filter Expression: ftp-data and frame contains "Real.pdf"
```
1. Cari **Real.pdf** dengan filter expression di atas.
2. Follow TCP Stream, ganti ASCII dengan Raw.
3. Save as folder berformat zip.
4. Buka **Real.pdf** di dalam folder.  

Screenshot:  
![7a](https://user-images.githubusercontent.com/52129348/134644691-4b00ca58-6fc4-4f48-b93f-18718c1f40a1.png)
![7b](https://user-images.githubusercontent.com/52129348/134644747-dd2570f7-c917-400e-a242-76ee5434a2ba.png)


### 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!
Jawab:  
```
Filter Expression: ftp-data.command == RETR
```
Screenshot:  
![8](https://user-images.githubusercontent.com/52129348/134644909-687efc2f-d707-47a8-a8b7-1303cd0a59a7.png)  
Command untuk mengembalikan file adalah `RETR`. Namun, pada kasus ini, sepertinya tidak ada data yang dikembalikan.   

### 9. Dari paket-paket yang menuju FTP terdapat indikasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama `secret.zip`. Simpan dan buka file tersebut!
Jawab:  
```
Filter Expression: ftp-data and ftp-data.command contains "secret.zip"
```
1. Cari **secret.zip** dengan filter expression di atas.
2. Follow TCP Stream, ganti ASCII dengan Raw.
3. Save as folder berformat zip.
4. Buka folder.  

Screenshot:  
![9a](https://user-images.githubusercontent.com/52129348/134645080-812b0677-060e-4085-b356-53581fce9827.png)
![9b](https://user-images.githubusercontent.com/52129348/134645093-1aba71a8-e9cd-4f46-a914-805438bcd890.png)
![9c](https://user-images.githubusercontent.com/52129348/134645102-a1a39ccf-1047-45a0-912b-ea0ab6748197.png)


### 10. Selain itu terdapat `history.txt` yang kemungkinan berisi history bash server tersebut! Gunakan isi dari `history.txt` untuk menemukan password untuk membuka file rahasia yang ada di `secret.zip`!
Jawab:  
```
Filter Expression:
ftp-data and ftp-data.command contains "history.txt", 
ftp-data and ftp-data.command contains "bukanapaapa.txt"
```
1. Cari **history.txt** dengan filter expression di atas, kemudian buka packet tersebut.
2. Cari **bukanapaapa.txt** dengan filter expression di atas, kemudian buka packet tersebut.
3. Simpan password pada **bukanapaapa.txt**, yaitu berupa `d1b1langbukanapapajugagapercaya`.
4. Buka folder yang didapat pada nomor 9.
5. Masukan password untuk mengekstrak folder tersebut. 
6. Buka file didalam folder tersebut.  

Screenshot:  
![10a](https://user-images.githubusercontent.com/52129348/134646222-3b17e8c4-3b7c-4f0d-a706-8602b5f22861.png)
![10b1](https://user-images.githubusercontent.com/52129348/134646245-674a4042-4f89-4f92-8a27-d45c2dbeee11.png)
![10c](https://user-images.githubusercontent.com/52129348/134646261-4eca80c5-8ee4-40ec-b799-803eebf0b996.png)

### 11. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80! 

Jawab:
```
src port 80
```
1. Gunakan filter src port 80 capture pada awal menu wireshark
2. Kemudian pilih jaringan yg ingin dicoba
3. Coba untuk menguji package dengan mengakses web dengan http
Screenshot:
![no11](https://user-images.githubusercontent.com/55136116/134695641-95df5529-8d3b-44b3-9024-4f744c4c11cb.png)

### 12. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

Jawab:
```
dst port 21
```
1. Gunakan filter dst port 21 capture pada awal menu wireshark
2. Kemudian pilih jaringan Adaptive for loopback untuk menguji sever di local
3. Buka xampp dan aktifkan FileZilla server
4. Buka FileZilla client
5. Coba akses melalui local server port 21 menggunakan FileZilla client ke server
Screenshot:
![no12](https://user-images.githubusercontent.com/55136116/134696376-038ae1e8-e3a2-4b2d-8469-6fb11dacb0de.png)

### 13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443! 

Jawab:
```
dst port 443
```
1. Gunakan filter capture dst port 443 pada awal menu wireshark
2. Kemudian pilih jaringan yg ingin dicoba
3. Coba untuk menguji package dengan mengakses web dengan https
Screenshot:
![no13](https://user-images.githubusercontent.com/55136116/134696488-3da3491c-08e4-40d2-8935-4665bff7234a.png)


### 14. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id! 

Jawab:
```
ip.dst == 103.7.13.247
```
1. Pilih jaringan wifi/internet yang ada
2. Cari ip dari domain website menggunakan ping di cmd
3. Gunakan capture filter ip.dst == 103.7.13.247 (ip tersebut merupakan ip dari domain website)
Screenshot:
![no14](https://user-images.githubusercontent.com/55136116/134696541-ca4f8489-5f5b-4828-83b2-d41de649c96f.png)



### 15. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian! 

Jawab:
```
ip.src == 192.168.100.8
```
1. Buka cmd dan caru ip laptop kalian di cmd menggunakan ipconfig (IPv4)
2. Pilih jaringan wifi/internet yang ada
3. Cobb akses internet menggunakan aplikasi apapun
4. Gunakan capture filter ip.src == 192.168.100.8 (ip tersebut merupakan ip perangkat saya)
Screenshot:
![no15](https://user-images.githubusercontent.com/55136116/134696585-56a13e3e-d62a-4bd8-9366-826533be9355.png)
