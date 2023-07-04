No 4

    Teori yang mendukung mengenai project terkait
Codingan di atas merupakan implementasi dari sebuah fungsi bernama highlight_letters yang memiliki tujuan untuk mempertegas (highlight) huruf-huruf yang terdapat pada gambar. Berikut adalah teori yang mendukung langkah-langkah yang dilakukan dalam fungsi tersebut:

1.	Import library yang diperlukan:
•	cv2: Library OpenCV (Open Source Computer Vision) digunakan untuk memanipulasi gambar, seperti membaca gambar, mengubah warna gambar, dan menemukan kontur.
•	numpy: Library untuk operasi numerik pada Python, digunakan untuk memanipulasi array dan matriks.
•	matplotlib.pyplot: Library untuk membuat plot dan visualisasi data.

2.	Definisikan fungsi highlight_letters(image_path, text) dengan dua parameter masukan:
•	image_path: Lokasi file gambar yang ingin diproses.
•	text: Teks yang akan dicari dan dipertegas pada gambar.

3.	Load gambar menggunakan cv2.imread(image_path). Gambar akan dimuat dalam bentuk array dengan representasi warna BGR (Blue-Green-Red).

4.	Konversi gambar ke dalam skala keabuan (grayscale) menggunakan cv2.cvtColor(image, cv2.COLOR_BGR2GRAY). Ini dilakukan agar dapat diterapkan operasi ambang batas (thresholding) pada gambar dengan mudah.

5.	Terapkan thresholding binary menggunakan cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY_INV). Thresholding binary mengubah gambar ke dalam citra biner (hitam dan putih), dengan piksel di atas ambang batas menjadi putih dan piksel di bawah ambang batas menjadi hitam. Hasilnya disimpan dalam variabel thresh.

6.	Temukan kontur pada gambar biner menggunakan cv2.findContours(thresh, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE). Kontur adalah tepi atau batas dari objek yang ada dalam gambar. Hasilnya akan menyimpan daftar kontur dan hierarki yang berkaitan dengan kontur tersebut.

7.	Lakukan iterasi pada setiap kontur yang ditemukan dalam langkah sebelumnya.
8.	Dapatkan persegi panjang pembatas (bounding rectangle) dari setiap kontur menggunakan cv2.boundingRect(contour). Persegi panjang ini akan membungkus kontur dan digunakan untuk menggambar persegi panjang berwarna hijau di sekitar huruf pada gambar asli.

9.	Gambar persegi panjang berwarna hijau di sekitar huruf menggunakan cv2.rectangle(image, (x, y), (x + w, y + h), (0, 255, 0), 2). Parameter pertama adalah gambar yang akan dimodifikasi, parameter kedua adalah titik kiri atas persegi panjang, parameter ketiga adalah titik kanan bawah persegi panjang, parameter keempat adalah warna (dalam urutan BGR), dan parameter kelima adalah ketebalan garis.

10.	Simpan gambar yang telah dimodifikasi ke dalam file sementara menggunakan cv2.imwrite(temp_image_path, image). File ini akan digunakan untuk ditampilkan nanti.

11.	Tampilkan gambar asli dan gambar hasil segmentasi (highlight huruf) secara berdampingan menggunakan plt.subplots(1, 2, figsize=(10, 5)). Ini akan membuat plot dengan dua gambar (dua kolom) dalam satu baris.
12.	Tampilkan gamb
ar asli (sebelum segmentasi) pada sumbu pertama menggunakan axes[0].imshow(original_image). original_image dikonversi ke dalam mode warna RGB agar sesuai dengan format yang diterima oleh imshow(). Judul plot juga ditambahkan menggunakan axes[0].set_title("Original Image").

13.	Tampilkan gambar hasil segmentasi pada sumbu kedua menggunakan axes[1].imshow(segmented_image). segmented_image dibaca menggunakan plt.imread() karena file ini telah disimpan sebelumnya menggunakan cv2.imwrite(). Judul plot juga ditambahkan menggunakan axes[1].set_title("Segmented Image").

14.	Tampilkan plot dengan menggunakan plt.show().

15.	Hapus file gambar sementara menggunakan os.remove(temp_image_path).
Pada dasarnya, fungsi highlight_letters menggunakan teknik pengolahan gambar seperti thresholding, pencarian kontur, dan penggambaran persegi panjang untuk mempertegas huruf-huruf pada gambar. Hal ini memungkinkan pengguna untuk dengan mudah melihat kontur huruf-huruf dalam gambar yang diproses.

     Menjelaskan tahapan cara menyelesaikan project secara rinci

Berikut adalah penjelasan tahapan-tahapan dalam codingan di atas secara rinci:
1.	Mengimpor library yang diperlukan: cv2, numpy, matplotlib.pyplot, dan os.

2.	Mendefinisikan fungsi highlight_letters(image_path, text) dengan dua parameter masukan:
•	image_path: Lokasi file gambar yang ingin diproses.
•	text: Teks yang akan dicari dan dipertegas pada gambar.

3.	Memuat gambar menggunakan cv2.imread(image_path). Gambar dimuat sebagai array dengan representasi warna BGR (Blue-Green-Red).

4.	Mengubah gambar menjadi skala keabuan (grayscale) menggunakan cv2.cvtColor(image, cv2.COLOR_BGR2GRAY).

5.	Menerapkan thresholding biner untuk mendapatkan citra hitam dan putih menggunakan cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY_INV). Nilai ambang batas (threshold) adalah 127, sehingga piksel di atas ambang batas akan menjadi putih dan piksel di bawah ambang batas akan menjadi hitam. Hasilnya disimpan dalam variabel thresh.

6.	Mencari kontur pada gambar biner menggunakan cv2.findContours(thresh, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE). Kontur adalah tepi atau batas dari objek yang ada dalam gambar. Hasilnya menyimpan daftar kontur dalam variabel contours.

7.	Melakukan iterasi pada setiap kontur yang ditemukan dalam variabel contours.

8.	Mendapatkan persegi panjang pembatas (bounding rectangle) dari setiap kontur menggunakan cv2.boundingRect(contour). Koordinat dan dimensi persegi panjang ini disimpan dalam variabel x, y, w, dan h.

9.	Menggambar persegi panjang berwarna hijau di sekitar kontur menggunakan cv2.rectangle(image, (x, y), (x + w, y + h), (0, 255, 0), 2).
10.	Menyimpan gambar yang telah dimodifikasi ke dalam file sementara menggunakan cv2.imwrite(temp_image_path, image). File ini akan digunakan untuk ditampilkan nanti.

11.	Menampilkan gambar asli dan gambar hasil segmentasi (highlight huruf) secara berdampingan menggunakan plt.subplots(1, 2, figsize=(10, 5)). Ini akan membuat plot dengan dua gambar dalam satu baris.

12.	Menampilkan gambar asli (sebelum segmentasi) pada sumbu pertama menggunakan axes[0].imshow(original_image). original_image dikonversi ke dalam mode warna RGB agar sesuai dengan format yang diterima oleh imshow(). Judul plot juga ditambahkan menggunakan axes[0].set_title("Original Image").

13.	Menampilkan gambar hasil segmentasi pada sumbu kedua menggunakan axes[1].imshow(segmented_image). segmented_image dibaca menggunakan plt.imread() karena file ini telah disimpan sebelumnya menggunakan cv2.imwrite(). Judul plot juga ditambahkan menggunakan axes[1].set_title("Segmented Image").

14.	Menampilkan plot menggunakan plt.tight_layout() dan plt.show().

15.	Menghapus file gambar sementara menggunakan os.remove(temp_image_path).
Pada dasarnya, fungsi highlight_letters menggunakan teknik pengolahan gambar seperti thresholding, pencarian kontur, dan penggambaran persegi panjang untuk mempertegas huruf-huruf pada gambar. Langkah-langkah ini menghasilkan visualisasi yang memperlihatkan gambar asli dan gambar hasil segmentasi (highlight huruf) secara berdampingan.
