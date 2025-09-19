# Go OCR
<p align="center"><img height="100px" src="https://stickershop.line-scdn.net/stickershop/v1/product/1349132/LINEStorePC/main.png;compress=true"> <img width="220px" src="https://miro.medium.com/max/866/1*CBkz7f_KjNh_wVuqLp-m0A.png" /></p>

Implementasi Optical Character Recognition menggunakan Golang API dan Tesseract

## Pendahulan
Aplikasi ini adalah backend API yang melayani upload file gambar KTP yang akan diproses menjadi data text.
Saya menggunakan library 
```text
https://github.com/otiai10/gosseract 
```
untuk me-convert image menjadi text sebagai perantara antara
aplikasi backend go dengan **tesseract**. 
Tesseract adalah open source yang dibangun oleh google berbasis bahasa C++
```text
https://opensource.google/projects/tesseract
```
Untuk API nya sendiri menggunakan beberapa third party yakni **echo** dan **graceful**

## Cara Instalasi 
Ada 2 metode yakni secara langsung  atau secara docker. Pertama-tama, anda clone dulu repository ini
- Instalasi langsung 
    1. Pastikan di server / komputer anda sudah  ada internet. Karena akan dilakukan  docnload library2 
       dari internet
    2. Karena saya pakai mac, maka bisa ikuti step-step berikut :
       ```text
           https://tesseract-ocr.github.io/tessdoc/Compiling.html#macos
       ```   
    3. Setelah semua terinstall, anda bisa arahkan ke folder utama **go-ocr** dan menjalankan aplikasi dengan mengetik sebagai berikut :
       ```text
           go run main.go
       ```

- Instalasi melalui docker 
    1. Harus ada internet karena dalam melakukan extract aplikasi ke docker akan menginstall library dary internet.
    2. Pada folder utama **go-ocr** , ketik command berikut (pembentukan docker image):
    ```text
         docker build -t go-ocr . 
    ```    
    3. Menjalankan container docker :
    ```text
         docker run -p 8080:8080 go-ocr
    ```   

## Implementasi 

- Anda dapat menggunakan postman, lalu   masukkan link url ini :
```
   method POST http://localhost:8080/go_ocr/v1/ktp/request
```  
- Berikut ini jika dijalankan menggunakan curl 
```text
curl --location --request POST 'http://localhost:8080/go_ocr/v1/ktp/request' \
--form 'file=@{PATH_FILE}/ktpcontoh2.jpg'
```
