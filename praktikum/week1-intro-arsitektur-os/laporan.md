
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [Rizki Fernanda Rahardi]  
- **NIM**   : [250320573]  
- **Kelas** : [1DSRA]

---

## Tujuan  
> Mengidentifikasi komponen utama OS (kernel, system call, device driver, file system).

---

## Dasar Teori
1.komponen arsitektur operasi system
2.perbedaan antara linux dan windows
3.peran operasi siste dalam arsitektur komputer
4.mempelajari hubungan antara user-system call-kernel-hardware
5.perbedaan antara monolithic kernel, microkernel, dan layered architecture.

---

## Langkah Praktikum
1.Membuat akun github.
2.Mencari repositori dari akun orang lain yang akan di fork.
3.fork repositori sampai mumcul di akun github kita sendiri.
4.edit nama repositori sesuaikan dengan NIM.
5.edit file repositori di github.

---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```bash
uname -a
lsmod | head
dmesg | head
```

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![(example.png)


---

## Analisis
- Jelaskan makna hasil percobaan.
- makna hasil percobaan

uname -a :
menampilkan informasi sistem operasi kernel yang sedang dijlankan yaitu kernel linux versi 6.6.10s+.
Arsitektur prosesor : x86_64(64-bit)
menggunakan fitur SMP (Symmetric Multi Processing) dan PREEMPT_DYNAMIC (mendukung premmption dinamis, artinya kernel bisa beralih konteks cepat untuk performa interaktif)

lsmod | head : Menampilkan modul kernel yang sedang dimuat, seperti: • iptable_nat, xt_nat, xt_mark → modul terkait jaringan dan NAT (Network Address Translation) • veth → modul virtual ethernet, menandakan sistem berjalan dalam lingkungan virtual (container / VM)

dmesg | head : Menandakan tidak memiliki izin root, jadi akses langsung ke kernel buffer ditolak. Ini umum di Cloud Shell untuk alasan keamanan.  
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).
- (fungsi kernel, system call, arsitektur OS).
Kernel : Kernel adalah inti dari sistem operasi yang mengatur: • Manajemen perangkat keras • Manajemen proses • Manajemen memori • Manajemen sistem file terlihat kernel Linux 6.6.10, yang bekerja mengatur semua operasi sistem Cloud Shell. Kernel ini juga memuat modul (hasil lsmod) agar dapat menangani fungsi tambahan seperti jaringan virtual.
system call system call adalah antarmuka antara program dan kernel. Contohnya: ketika mengetik perintah uname, shell memanggil system call uname() untuk meminta info kernel. Begitu juga lsmod dan dmesg menggunakan system call untuk: • Mengakses daftar modul kernel • Membaca buffer pesan kernel Namun, karena bukan user root, system call untuk dmesg ditolak dengan pesan “Operation not permitted” — ini menunjukkan mekanisme proteksi kernel terhadap akses pengguna biasa.
arsitektur OS : Linux menggunakan arsitektur monolithic kernel, artinya: • Semua layanan inti OS (file system, device driver, jaringan, dll.) berjalan di mode kernel (ring 0). • Namun modul seperti iptable_nat atau veth bisa dimuat atau dilepas secara dinamis, membuatnya lebih fleksibel.  
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows
- Linux
kernel : mengggunakan monolithic kernel
shell/command line : menggunakan Bash,zsh, atau sh. perintah lsmoed,uname, dmesg digunakan untuk interaksi langsung dengan kernel
perintah uname : menampilkan detail kernel Linux (versi arsitektur, tanggal buld)
perintah lsmod : menampilkanm modul kernel yang dimuat (driver, jaringan, dll)
perintah dmesg : menampilkan log pesan kernel (boot, device, error)
akses ke kernel bisa langsung lewat system call
hak akses pengguna : dibedakan jelas root vs user biasa
Windows
menggunakan hybrid kernel (gabungan monolithic+microkernel)
menggunakan Command Prompt (CMD) atau PowerShell
uname tidak tersedia. sebagai gantinya di PoweShell : systeminfo
lsmod tidak ada di Windows, driver bisa dilihat di Device Manager
tidak ada dmesg. Windows menggunakan Event viewer
Akses kernel lebih dibatasi interaksi dilakukan melalui API windows
hak akses pengguna : ada kensep administrator

---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.
1.System call menjadi perantara antara pengguna (user space) dengan kernel (kernel space). Perintah seperti uname, lsmod, dan dmesg menggunakan system call untuk meminta informasi dari kernel. Namun, akses ke beberapa fungsi kernel dibatasi bagi pengguna non-root,
2.Arsitektur OS memengaruhi cara sistem beroperasi. Linux dengan arsitektur monolithic memberikan fleksibilitas dan keterbukaan akses, sementara Windows dengan hybrid kernel lebih membatasi akses langsung ke kernel demi stabilitas dan keamanan sistem.
3.kernel berperan sebagai inti sistem operasi yang mengatur seluruh sumber daya perangkat keras dan perangkat lunak.

---

## Quiz
1.3 fungsi system kernel
   Manajemen sumber daya (Resource Management)
   Manajemen file dan sisem I/O
   Manajemen proses dan keamanan sistem
2. USER MODE
 adalah mode tempat semua program aplikasi berjalan — seperti Microsoft Word, browser, atau pemutar musik. Ciri-cirinya: •      Akses ke perangkat keras (CPU, memori, disk, dll.) terbatas. • Jika aplikasi error atau crash, tidak akan memengaruhi sistem operasi. • Tidak boleh menjalankan instruksi khusus CPU (privileged instructions). • Untuk melakukan tugas penting (misalnya membaca file atau mencetak dokumen), aplikasi harus meminta bantuan kernel melalui system call.
KERNEL MODE Kernel Mode adalah mode di mana kernel (inti sistem operasi) berjalan. Di sini sistem punya hak penuh terhadap perangkat keras dan seluruh memori komputer. Ciri-cirinya: • Bisa menjalankan semua instruksi CPU, termasuk privileged instructions. • Digunakan untuk mengelola proses, memori, file system, dan perangkat keras. • Jika terjadi kesalahan di mode ini, bisa menyebabkan crash seluruh sistem (kernel panic).
PERBEDAAN USER MODE
Tingkat akses : akses terbatas, tidak bisa langsung akses hardware
fungsi utama : mejalankan aplikasi pengguna seperti browser,word,dsb
keamanan : lebih aman, error aplikasi tidak memengaruhi sistem
lokaksi kerja : berjalan di user space
Intruksi CPU : tidak bisa menjalankan intruksi istimewa -contoh aktivitas : menjalankan program aplikasi biasa
KERNEL MODE

Tingkat akses : akses penuh ke seluruh sumber daya sistem
fungsi utama : menjalankan fungsi inti sistem operasi
keamanan : risiko tinggi jika error karena bisa merusak sistem
lokasi kekrja : Berjalan di kernel space
intruksi CPU : bisa menjalankan intruksi istemewa (privilage intruction)
contoh aktivitas : system call, manajemen memory, driver perangkat
3.contoh OS arsitektur monolithic :
LINUX,(UBUNTU,Fedora, Debian, Android)
MS-DOS
Unix(versi lama sperti system v) contoh OS arsitektur Microkernel:
Minix
QNX
Mach(digunakan di MacOS dan IOS)
Integrity OS 

---

## Refleksi Diri
Tuliskan secara singkat:
- 1.Apa bagian yang paling menantang minggu ini?
-  yang paling menantang adalah karena ini merupakan hal baru bagi saya yang notabene memiliki basic di tkr dan langsung swape di bidang informatika
- 2.Bagaimana cara Anda mengatasinya?  
untuk mengatasinya saya memiliki waktu tersendiri dirumah untuk membuka kembali materi yang telah diajarkan dikelas
---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
