### Deskripsi Statistik dari Gambar
Pada materi kali ini, kita akan mempelajari cara membuat deskripsi statistik dari gambar. Salah satu caranya yaitu dengan membuat histogram dari gambar. Histogram gambar dapat dipakai untuk menganalisis distribusi intensitas warna dari gambar. Setelah mendapatkan histogram dari gambar, kita akan mencoba menggunakan metode histogram equalization untuk meningkatkan kontras dari dari gambar kita.

#### Menyiapkan gambar
Karena kita akan membuat histogram dari gambar, tentu saja kita membutuhkan sebuah sampel gambar. Di sini saya sudah menyiapkan satu gambar mountain.jpg yang akan digunakan.

![mountain.jpg][mountain.jpg]

Siapkan juga satu file python untuk tempat kita menaruh script kodingan kita nantinya. Jangan lupa import dulu library yang akan dipakai, yaitu opencv, numpy, dan pyplot dari matplotlib.

![import.png][import.png]
 
Pertama kita akan memasukkan gambar kita dulu dengan menggunakan library opencv dengan cv.imread. Function ini menawarkan kita untuk dapat memasukkan gambar dalam format color ataupun grayscale. Karena histogram membutuhkan image dalam bentuk grayscale, kita menggunakan flag cv2.IMREAD_GRAYSCALE.

![imread.png][imread.png]
 
Dan apabila kita menampilkan gambarnya dengan cv2.imshow dapat dilihat gambar kita sudah diload dalam color space grayscale.

![grayscale_image.png][grayscale_image.png]

#### Membuat histogram
Untuk membuat histogram, kita memerlukan data intensitas dari setiap pixel yang ada pada gambar, lalu kita hitung untuk setiap intensitas ada berapa pixel. Untuk mendapatkan data tersebut, pertama mari kita mencoba print gambar kita terlebih dahulu.

![print_grayscale.png][print_grayscale.png]

Dan hasil yang didapatkan akan seperti ini.

![print_result.png][print_result.png]

Dapat dilihat bahwa gambar merupakan 2D array dengan ukuran (678, 1024) yang merupakan (height, width) dari gambar dalam ukuran pixel. Sedangkan setiap data pada array merupakan nilai intensitas dari setiap pixel.

![picture_properties.png][picture_properties.png]

Sekarang dengan data ini kita mau menghitung total pixel per intensitas. Ini dapat dilakukan dengan membuat array berukuran 256 dengan range 0-255 sesuai dengan range intensitas. Kita akan membuat array ini dengan library numpy dan menginisialisasi semua nilainya dengan 0.

![initialize_counter.png][initialize_counter.png]

Lalu kita akan looping untuk setiap pixel yang ada, dan menambahkan ke array sesuai dengan intensitas tiap pixelnya.

![loop.png][loop.png]
 
Dengan ini, kita sudah mengetahui total pixel untuk setiap intensitas. Misalnya terdapat total 3405 pixel yang memiliki intensitas 128, maka jika kita print intensity[128] akan mendapatkan hasil 3405.
Sekarang kita akan memasukkan array ini ke pyplot untuk diplot histogramnya.

![histogram_result.png][histogram_result.png]

Jika kita jalankan dapat dilihat bahwa histogram kita sudah muncul. Dapat dilihat total pixel untuk setiap intensity ada berapa.

![histogram_result_plotted.png][histogram_result_plotted.png]
 
Dapat kita simpulkan bahwa intensitas sekitar 45 memiliki total pixel paling banyak, dan untuk intensitas lainnya memiliki pixel lebih sedikit, bahkan tidak ada pixel yang memiliki intensitas antara 0-30an.

#### Histogram Equalization
Di sini kita akan mencoba meningkatkan kontras dari gambar kita dengan menggunakan metode histogram equalization. Histogram equalization akan menyebar intensitas sehingga area gambar yang memiliki kontras yang lebih rendah dapat memiliki kontras yang lebih tinggi.

![equalized_image.png][equalized_image.png]

Untuk membuktikan bahwa gambar yang telah di apply histogram equalization ini memiliki intensitas yang tersebar, maka kita akan menghitung total pixel untuk setiap intensitas pada gambar baru kita.

![loop_equ.png][loop_equ.png]

Jika kita plot maka kita dapat melihat histogram seperti ini.

![histogram_result_equ.png][histogram_result_equ.png]

Apabila kita mencoba menampilkan gambar yang telah di equalize, maka dapat kita lihat kontras dari gambar kita meningkat.

![mountain_equ.png][mountain_equ.png]

Apabila ingin membandingkan antara kedua gambar kita, kita dapat stack image kita menggunakan numpy terlebih dahulu sebelum di show.

![stack_image.png][stack_image.png]
 
Maka hasil akhirnya akan seperti gambar di bawah.

![comparison.png][comparison.png]

[mountain.jpg]: https://i.ibb.co/kSvzjG1/mountain.jpg
[import.png]: https://i.ibb.co/72T0RFG/import.png
[imread.png]: https://i.ibb.co/qMjLmCh/imread.png
[grayscale_image.png]: https://i.ibb.co/HYkFq7N/grayscale-image.png
[print_grayscale.png]: https://i.ibb.co/y6Bcg6Z/print-grayscale.png
[print_result.png]: https://i.ibb.co/dKs7NgY/print-result.png
[picture_properties.png]: https://i.ibb.co/8BSc95p/picture-properties.png
[initialize_counter.png]: https://i.ibb.co/vQK76Fj/initialize-counter.png
[loop.png]: https://i.ibb.co/v1LRhWf/loop.png
[histogram_result.png]: https://i.ibb.co/gSB6xzy/histogram-result.png
[histogram_result_plotted.png]: https://i.ibb.co/b6ykw9T/histogram-result-plotted.png
[equalized_image.png]: https://i.ibb.co/5xZyRSV/equalized-image.png
[loop_equ.png]: https://i.ibb.co/Q8phHVq/loop-equ.png
[histogram_result_equ.png]: https://i.ibb.co/TBxhdRY/histogram-result-equ.png
[mountain_equ.png]: https://i.ibb.co/D7yjHF4/mountain-equ.png
[stack_image.png]: https://i.ibb.co/MRd1f45/stack-image.png
[comparison.png]: https://i.ibb.co/YZwmwHM/comparison.png
