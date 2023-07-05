
# UAS PENGCIT mengenai pendeteksi plat

library yang saya gunakan:

numpy: untuk melakukan operasi matematika

open cv: membaca, menyimpan, konversi warna dll pada citra

matplotlib: untuk membuat visualisasi data dalam bentuk grafik, plot dan visualisasi lainnya

imutils: untuk memperluas fungsionalitas OpenCV.


langkah pengerjaannya:
1. membaca citra:membaca citra 'mobil.jpeg'menggunakan 'cv2.imread()' dan menyimpannya dalam variabel'image'.
2. mengubah ukuran citra (opsional):jika lebar citra lebih besar dari 1000 pixel, citra akan diubah ukurannya agar lebar citra menjadi 1000 piksel dan tingginya disesuaikan proporsional dengan lebar menggunakan 'cv2.resize()'
3. konversi citra ke grayscale: citra diubah menjadi skala abu-abu menggunakan 'cv2.cvtColor()'untuk mempermudah operasi selanjutnya.
4. filter bilateral: dilakukan bilateral filter pada citra grayscale untuk mengurangi noise dan tetap menjaga tepi menggunakan 'cv2.bilateralFilter()'
5. deteksi tepi(canny): tepi pada citra diidentifikasi dengan menggunakan algoritma canny edge detection pada citra hasil filter bilateral dengan 'cv2.canny()'
6. temukan kontur: melakukan pencarian kontur pada  citra hasil deteksi tepi menggunakan 'cv2.findContours()' dan 'imutils.grab_contours()'. Kontur-kontur tersebut kemudian diurutkan berdasarkan luasnya dengan menggunakan 'sorted()'.
7. Temukan Kotak yang Mengelilingi Objek: Mengiterasi melalui kontur-kontur yang diurutkan, kemudian mencari kontur yang memiliki tepat 4 titik dengan menggunakan  'cv2.approxPolyDP()' dan disimpan dalam variabel 'location'.
8. Buat Mask dan Potong Citra: Membuat mask dari kontur yang ditemukan dan memotong citra menggunakan 'cv2.drawContours()' dan 'cv2.bitwise_and()'.
9. Tampilkan Hasil: Menampilkan citra hasil potongan dan citra grayscale hasil deteksi tepi menggunakan 'plt.imshow()'.
10. Potong Bagian Objek: Menggunakan informasi dari mask, dilakukan pemotongan bagian objek mobil dari citra grayscale menggunakan indeks 'x1', 'x2', 'y1', dan 'y2' yang didapatkan dari nilai minimal dan maksimal di dalam mask.



