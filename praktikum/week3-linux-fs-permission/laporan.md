
# Laporan Praktikum Minggu [3]
Topik: Manajemen File dan Permission di Linux

---

## Identitas
- **Nama**  : [Rizki Fernanda Rahardi]  
- **NIM**   : [250320573]  
- **Kelas** : [1DSRA]

---

## Tujuan
Tujuan dari praktikum minggu ini adalah untuk memberikan pemahaman yang mendalam mengenai pengelolaan file dan direktori di sistem operasi Linux, serta pengaturan hak akses dan kepemilikan file. Dalam praktikum ini, mahasiswa diharapkan dapat mengoperasikan perintah dasar Linux seperti ls, pwd, cd, dan cat untuk melakukan navigasi pada sistem file, serta mampu menjelaskan hasil dari perintah-perintah tersebut. Selain itu, mahasiswa juga diharapkan dapat menggunakan perintah chmod dan chown untuk mengatur hak akses dan kepemilikan file dengan benar. Pemahaman mengenai bagaimana hak akses file berfungsi sangat penting, khususnya dalam konteks keamanan sistem, sehingga mahasiswa akan dapat mengidentifikasi dan menganalisis makna dari kode permission seperti rwxr-xr--. Praktikum ini juga bertujuan untuk melatih mahasiswa dalam mendokumentasikan seluruh hasil percobaan dengan baik dan menyusunnya dalam laporan yang terstruktur, serta mengunggah hasilnya ke repositori GitHub tepat waktu. Dengan demikian, mahasiswa tidak hanya menguasai penggunaan perintah-perintah dasar Linux, tetapi juga memahami konsep manajemen file dan permission yang esensial dalam pengelolaan sistem Linux secara aman dan efisien.

---

## Dasar Teori

1.	  Sistem Berkas (File System) di Linux
Sistem berkas di Linux mengatur cara penyimpanan dan pengelolaan file serta direktori dalam komputer. Setiap file atau direktori dalam Linux disusun dalam hierarki pohon terstruktur, dimulai dari direktori root (/). Pengguna berinteraksi dengan sistem berkas menggunakan perintah dasar seperti ls untuk melihat isi direktori, cd untuk berpindah antar direktori, dan pwd untuk mengetahui direktori aktif saat ini.

2.	 Hak Akses dan Permission pada File
Setiap file di Linux memiliki permission yang menentukan siapa yang dapat mengakses file tersebut dan apa yang bisa dilakukan terhadapnya. Ada tiga jenis hak akses yang dapat diberikan: read (r), write (w), dan execute (x). Hak akses ini terbagi untuk tiga kategori pengguna: owner (pemilik), group (grup), dan others (pengguna lain). Pengaturan hak akses ini berfungsi untuk membatasi akses ke file demi menjaga keamanan dan privasi data.

3.	Perintah chmod (Change Mode)
Perintah chmod digunakan untuk mengubah hak akses (permission) pada file atau direktori. Dengan perintah ini, pengguna dapat menentukan siapa yang dapat membaca, menulis, atau mengeksekusi file. Mode pengaturan permission dapat dilakukan dalam format simbolik (misalnya rwxr-xr--) atau numerik (misalnya 755), yang memberi fleksibilitas dalam pengelolaan hak akses.

4.	 Perintah chown (Change Owner)
Perintah chown digunakan untuk mengubah kepemilikan file atau direktori, baik itu pemilik (owner) maupun grup (group). Dengan menggunakan chown, administrator sistem dapat mengelola hak akses berdasarkan kepemilikan, memastikan bahwa hanya pengguna yang berwenang yang memiliki kontrol atas file atau direktori tertentu.

5.	Keamanan Sistem dengan Manajemen Permission
Sistem Linux memberikan kontrol penuh kepada administrator untuk mengatur hak akses melalui chmod dan chown, yang sangat penting dalam konteks keamanan. Dengan pengaturan permission yang tepat, pengguna dapat memastikan bahwa hanya pihak yang berwenang yang dapat mengakses atau memodifikasi file sensitif, serta melindungi sistem dari potensi ancaman atau kerusakan yang disebabkan oleh akses yang tidak sah.

---

## Langkah Praktikum
1.	Setup environment di Linux (Ubuntu/WSL).
2.	Pastikan folder kerja berada di dalam direktori repositori Git praktikum: praktikum/week3-linux-fs-permission/.
3.	Jalankan perintah pwd untuk melihat direktori aktif.
4.	Jalankan perintah ls -l untuk menampilkan daftar file dan direktori dengan informasi detail.
5.	Pindah ke direktori /tmp dengan perintah cd /tmp.
6.	Jalankan perintah ls -a untuk melihat file tersembunyi di dalam direktori /tmp.
7.	Jalankan perintah cat /etc/passwd | head -n 5 untuk membaca 5 baris pertama dari file /etc/passwd.
8.	Buat file baru dengan perintah echo "Hello <Nama> <NIM>" > percobaan.txt.
9.	Cek status file dengan perintah ls -l percobaan.txt.
10.	Ubah permission file dengan perintah chmod 600 percobaan.txt.
11.	Periksa kembali dengan perintah ls -l percobaan.txt.
12.	Ubah pemilik file menggunakan perintah sudo chown root percobaan.txt.
13.	Periksa perubahan kepemilikan file dengan perintah ls -l percobaan.txt.
14.	Ambil screenshot hasil terminal dan simpan di direktori praktikum/week3-linux-fs-permission/screenshots/.
15.	Tambahkan analisis hasil eksperimen ke dalam laporan laporan.md.
16.	Gunakan perintah git add ., git commit -m "Minggu 3 - Linux File System & Permission", dan git push origin main untuk mengunggah laporan.

---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```bash
pwd
ls -l
cd /tmp
ls -a
cat /etc/passwd | head -n 5
echo "Hello <NAME><NIM>" > percobaan.txt
ls -l percobaan.txt
chmod 600 percobaan.txt
ls -l percobaan.txt
sudo chown root percobaan.txt
ls -l percobaan.txt

```

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/week.3.png)

---

## Analisis

1.	Eksperimen 1 
Hasil eksperimen ini menunjukkan bagaimana perintah seperti pwd, ls -l, dan ls -a digunakan untuk mengeksplorasi dan memahami struktur file di Linux. Perintah pwd memastikan kita tahu posisi direktori saat ini, sedangkan ls -l memberikan informasi detail tentang file dan direktori, termasuk hak akses. Perintah ls -a menampilkan file tersembunyi, yang sering digunakan untuk konfigurasi sistem.

2.	Eksperimen 2
Dengan menjalankan perintah cat /etc/passwd | head -n 5, kami bisa melihat struktur file /etc/passwd yang menyimpan informasi pengguna sistem. File ini mengandung data penting tentang setiap akun pengguna, seperti UID, GID, direktori home, dan shell. Eksperimen ini mengajarkan pentingnya memahami format file sistem yang berisi informasi konfigurasi.

3.	Eksperimen 3 
Perintah chmod 600 percobaan.txt membatasi hak akses file, hanya memberi izin baca dan tulis kepada pemiliknya, sementara perintah chown mengubah pemilik file menjadi root. Eksperimen ini menggarisbawahi bagaimana pengaturan hak akses dan kepemilikan file sangat penting untuk menjaga keamanan sistem dan data.

4.	Eksperimen 4 
Dokumentasi yang dilakukan dengan mengambil screenshot dan menambahkan analisis ke laporan .md penting untuk mencatat hasil percobaan dan memudahkan verifikasi. Ini menunjukkan betapa pentingnya dokumentasi yang rapi dalam setiap eksperimen.

---

## Kesimpulan

Dari praktikum ini, dapat disimpulkan bahwa pengelolaan file dan pengaturan permission di Linux sangat penting untuk keamanan dan integritas sistem. Eksperimen menunjukkan bagaimana perintah dasar seperti pwd, ls -l, dan chmod digunakan untuk menavigasi, mengatur akses, dan memodifikasi file. Selain itu, perintah chown memungkinkan perubahan kepemilikan file, yang memberi kontrol lebih kepada administrator. Praktikum ini menggarisbawahi pentingnya pengaturan hak akses yang tepat untuk mencegah akses yang tidak sah dan menjaga keamanan sistem secara keseluruhan.

---

## Quiz

1.	Fungsi perintah chmod
   
Perintah chmod digunakan untuk mengubah hak akses atau permission pada sebuah file atau direktori. Dengan perintah ini, saya bisa mengatur siapa saja yang dapat membaca, menulis, atau mengeksekusi file, sehingga keamanan dan kontrol terhadap file dapat terjaga.

2.	Arti kode permission rwxr-xr--
   
Kode permission rwxr-xr-- menunjukkan hak akses file untuk tiga kategori pengguna.
•	rwx untuk pemilik file, artinya pemilik dapat membaca, menulis, dan mengeksekusi file.
•	r-x untuk grup, artinya anggota grup dapat membaca dan mengeksekusi file, tapi tidak bisa menulis.
•	r-- untuk pengguna lain, artinya mereka hanya bisa membaca file tanpa izin menulis atau mengeksekusi.

3.	Perbedaan antara chown dan chmod
   
Perintah chown digunakan untuk mengubah kepemilikan file atau direktori, baik pemilik maupun grup. Sedangkan chmod digunakan untuk mengubah hak akses file, seperti siapa yang bisa membaca, menulis, atau mengeksekusi file. Jadi, chown mengatur siapa yang memiliki file, sementara chmod mengatur apa yang bisa dilakukan terhadap file tersebut.


---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
