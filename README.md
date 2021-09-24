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
Screenshot:  
![9a](https://user-images.githubusercontent.com/52129348/134645080-812b0677-060e-4085-b356-53581fce9827.png)
![9b](https://user-images.githubusercontent.com/52129348/134645093-1aba71a8-e9cd-4f46-a914-805438bcd890.png)
![9c](https://user-images.githubusercontent.com/52129348/134645102-a1a39ccf-1047-45a0-912b-ea0ab6748197.png)


### 10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di `secret.zip`!
Jawab:  
```
Filter Expression:
ftp-data and ftp-data.command contains "history.txt", 
ftp-data and ftp-data.command contains "bukanapaapa.txt"
```
Screenshot:  
![10a](https://user-images.githubusercontent.com/52129348/134646222-3b17e8c4-3b7c-4f0d-a706-8602b5f22861.png)
![10b1](https://user-images.githubusercontent.com/52129348/134646245-674a4042-4f89-4f92-8a27-d45c2dbeee11.png)
![10c](https://user-images.githubusercontent.com/52129348/134646261-4eca80c5-8ee4-40ec-b799-803eebf0b996.png)
