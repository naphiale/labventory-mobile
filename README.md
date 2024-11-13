# labventory

A new Flutter project.

## Getting Started

---

## 1. Perbedaan *Stateless Widget* dan *Stateful Widget*

- **Stateless Widget**: Widget yang **tidak memiliki kondisi** atau **state** yang bisa berubah. Stateless widget digunakan ketika tampilan dan perilaku widget tidak dipengaruhi oleh interaksi pengguna atau perubahan data. Sekali widget ini dirender, isinya tetap sama dan tidak bisa diubah. Contoh: `Text`, `Icon`, dan `Container`.

- **Stateful Widget**: Widget yang memiliki **state** yang bisa berubah selama siklus hidup widget. Stateful widget digunakan ketika tampilan perlu diperbarui berdasarkan interaksi pengguna atau perubahan data. Stateful widget memiliki objek `State` yang menyimpan data yang bisa berubah. Contoh: `Checkbox`, `Slider`, dan widget interaktif lainnya.

- **Perbedaan Utama**:
  - *Stateless*: Tidak memiliki objek `State`. Tidak bisa berubah setelah dirender.
  - *Stateful*: Memiliki objek `State`. Bisa berubah seiring waktu dan merender ulang berdasarkan perubahan state.

## 2. Widget yang Digunakan dalam Proyek dan Fungsinya

Berikut adalah daftar widget yang digunakan dalam proyek ini dan penjelasan fungsinya:

- **`Scaffold`**: Struktur utama dari aplikasi yang menyediakan tata letak dasar seperti `appBar`, `body`, dan `floatingActionButton`. `Scaffold` membantu menciptakan struktur halaman aplikasi.

- **`AppBar`**: Komponen header yang berfungsi sebagai bagian atas dari aplikasi, menampilkan judul atau kontrol lain seperti tombol.

- **`Padding`**: Memberi jarak di sekitar widget yang dibungkusnya, digunakan untuk mengatur spasi dalam tata letak.

- **`Column`**: Mengatur widget dalam susunan vertikal (atas ke bawah), cocok untuk tata letak yang membutuhkan tumpukan komponen.

- **`Row`**: Menyusun widget secara horizontal (samping ke samping), digunakan untuk menempatkan elemen dalam satu baris.

- **`InfoCard`** (Custom Stateless Widget): Digunakan untuk menampilkan informasi pengguna (NPM, Nama, Kelas) dalam bentuk kartu.

- **`GridView.count`**: Menyusun widget dalam grid dengan jumlah kolom tetap. Digunakan untuk menampilkan item tombol dalam tata letak grid yang rapi.

- **`Material`**: Digunakan untuk memberi efek material (seperti bayangan atau efek klik) pada widget. Dalam proyek ini, `Material` digunakan untuk menampilkan latar belakang berwarna pada `ItemCard`.

- **`InkWell`**: Widget interaktif yang memberikan efek visual ketika ditekan. `InkWell` digunakan pada tombol untuk mendeteksi interaksi pengguna dan menampilkan `SnackBar`.

- **`SnackBar`**: Widget untuk menampilkan pesan singkat di bagian bawah layar. Digunakan untuk memberi feedback ketika pengguna menekan tombol.

- **`Icon`** dan **`Text`**: Menampilkan ikon dan teks pada tombol, sesuai dengan fungsi dan label yang ditentukan dalam `ItemHomepage`.

## 3. Fungsi `setState()`

`setState()` adalah fungsi khusus dalam *Stateful Widget* yang digunakan untuk **memperbarui state** dan **merender ulang tampilan**. Ketika `setState()` dipanggil, widget akan memanggil ulang metode `build()` dan memperbarui tampilan dengan nilai terbaru. Contoh variabel yang bisa terdampak oleh `setState()` antara lain:

- Variabel yang menyimpan **data dinamis** atau **nilai sementara** yang perlu diperbarui berdasarkan interaksi pengguna (misalnya, `counter` untuk menghitung, atau status login).
- Data yang terkait dengan widget interaktif yang memungkinkan perubahan tampilan ketika pengguna berinteraksi, seperti `Checkbox` atau `Slider`.

Di proyek ini, karena menggunakan *Stateless Widget*, tidak ada `setState()` karena tidak ada data atau variabel yang perlu diperbarui.

## 4. Perbedaan `const` dan `final`

- **`const`**:
  - Digunakan untuk **nilai yang bersifat konstan** pada waktu kompilasi. Dengan kata lain, nilai `const` harus diketahui dan tidak boleh berubah setelah kode dikompilasi.
  - `const` membuat **nilai tetap untuk semua instansi**. Jika suatu objek didefinisikan dengan `const`, maka objek tersebut akan **diinisialisasi satu kali saja** dan digunakan kembali di seluruh kode yang sama.
  - Cocok untuk nilai tetap yang tidak akan berubah selama runtime.

- **`final`**:
  - Digunakan untuk **nilai yang hanya bisa diinisialisasi sekali** pada waktu runtime. Setelah nilai final ditetapkan, nilainya tidak bisa diubah.
  - `final` lebih fleksibel dibanding `const` karena bisa menerima nilai yang ditentukan di runtime, bukan hanya saat kompilasi.
  - Cocok untuk variabel yang nilainya ditentukan nanti tapi tidak boleh diubah setelah itu.

**Contoh Penggunaan**:
  - `const`: `const double pi = 3.14;` (nilai ini tetap, sehingga bisa digunakan `const`).
  - `final`: `final String userName = getUserName();` (nilai `userName` didapatkan saat runtime, sehingga menggunakan `final`).

## 5. Step by Step

### 1. Membuat Program Flutter Baru

1. **Buka Terminal atau Command Prompt**:
   - Buat dan masuk ke direktori tempat proyek akan disimpan.

2. **Generate proyek baru** dengan nama `Labventory` menggunakan perintah:
   ```bash
   flutter create e_commerce_app
   ```
   
3. **Masuk ke direktori proyek**:
   ```bash
   cd e_commerce_app
   ```

4. **Jalankan proyek** untuk memastikan semuanya berfungsi:
   ```bash
   flutter run
   ```

### 2. Membuat Tiga Tombol dengan Ikon dan Teks

1. Buka file `lib/main.dart` di proyek.

2. Di dalam file `main.dart`, tambahkan kode untuk membuat tombol-tombol ini.

3. **Deklarasikan List tombol-tombol** pada `MyHomePage` di dalam class `MyHomePage` untuk tombol “Lihat Daftar Produk,” “Tambah Produk,” dan “Logout”:

   ```dart
   class MyHomePage extends StatelessWidget {
     final List<ItemHomepage> items = [
       ItemHomepage("Lihat Daftar Produk", Icons.list, Colors.blue),
       ItemHomepage("Tambah Produk", Icons.add, Colors.green),
       ItemHomepage("Logout", Icons.logout, Colors.red),
     ];
     ...
   }
   ```

4. Di luar `MyHomePage`, buat class `ItemHomepage` untuk mendefinisikan atribut tombol (name, icon, color):
   ```dart
   class ItemHomepage {
     final String name;
     final IconData icon;
     final Color color;

     ItemHomepage(this.name, this.icon, this.color);
   }
   ```

### 3. Membuat Tombol dengan Ikon dan Warna Berbeda untuk Setiap Tombol

1. Tambahkan kode dalam class `MyHomePage` untuk menampilkan tombol-tombol dengan warna, teks, dan ikon yang berbeda.

2. Buat class `ItemCard` di file `main.dart` untuk menampilkan setiap tombol dalam bentuk card, termasuk fungsi `onTap` untuk menampilkan Snackbar:

   ```dart
   class ItemCard extends StatelessWidget {
     final ItemHomepage item;

     const ItemCard(this.item, {super.key});

     @override
     Widget build(BuildContext context) {
       return Material(
         color: item.color,
         borderRadius: BorderRadius.circular(12),
         child: InkWell(
           onTap: () {
             ScaffoldMessenger.of(context)
               ..hideCurrentSnackBar()
               ..showSnackBar(SnackBar(content: Text("Kamu telah menekan tombol ${item.name}")));
           },
           child: Container(
             padding: const EdgeInsets.all(8),
             child: Center(
               child: Column(
                 mainAxisAlignment: MainAxisAlignment.center,
                 children: [
                   Icon(item.icon, color: Colors.white, size: 30.0),
                   const SizedBox(height: 5),
                   Text(item.name, textAlign: TextAlign.center, style: const TextStyle(color: Colors.white)),
                 ],
               ),
             ),
           ),
         ),
       );
     }
   }
   ```

### 4. Mengintegrasikan Tombol di Halaman Utama (`MyHomePage`)

1. Di dalam `Widget build` di `MyHomePage`, tambahkan `GridView.count` untuk menampilkan tombol dalam grid dengan jarak yang rapi.

2. Kode akhir pada `build` method di `MyHomePage` akan terlihat seperti ini:

   ```dart
   @override
   Widget build(BuildContext context) {
     return Scaffold(
       appBar: AppBar(
         title: const Text('Labventory'),
         backgroundColor: Colors.deepPurple,
       ),
       body: Padding(
         padding: const EdgeInsets.all(16.0),
         child: Center(
           child: GridView.count(
             primary: false,
             padding: const EdgeInsets.all(20),
             crossAxisSpacing: 10,
             mainAxisSpacing: 10,
             crossAxisCount: 3,
             shrinkWrap: true,
             children: items.map((ItemHomepage item) => ItemCard(item)).toList(),
           ),
         ),
       ),
     );
   }
   ```

### 5. Menjalankan dan Menguji Program

1. Jalankan aplikasi:
   ```bash
   flutter run
   ```

2. Uji setiap tombol untuk memastikan Snackbar muncul dengan pesan yang sesuai saat tombol ditekan.

---

## *1. Mengapa Perlu Membuat Model untuk Pengambilan/Pengiriman Data JSON?*
Model berfungsi sebagai representasi struktur data yang akan diolah, baik untuk menerima data dari API (parsing) maupun untuk mengirim data ke API (serialization). Model ini penting karena:

- *Mempermudah Pengelolaan Data*: Dengan model, kita dapat memanipulasi data secara terstruktur tanpa harus mengakses elemen JSON secara manual.
- *Meningkatkan Keamanan*: Model memungkinkan validasi data sebelum data diterima atau dikirim.
- *Meningkatkan Readability dan Maintainability*: Model membantu memisahkan logika data dari logika UI, sehingga kode lebih mudah dibaca dan dipelihara.

Jika tidak membuat model terlebih dahulu:
- Tidak akan terjadi error jika kita hanya menampilkan data sederhana.
- Namun, untuk aplikasi besar dengan banyak data kompleks, pengolahan data secara manual rentan terhadap *human error*, kesalahan parsing, atau ketidaksesuaian format data.

---

## *2. Fungsi dari Library http*
Library http di Flutter digunakan untuk melakukan permintaan HTTP, seperti GET, POST, PUT, dan DELETE, ke server. Beberapa fungsi utama dari library ini adalah:

- *Melakukan Permintaan HTTP*: Mengirimkan request dan menerima response dari API.
- *Mengolah Data JSON*: Memungkinkan aplikasi Flutter untuk menerima dan memproses data JSON yang diterima dari server.
- *Komunikasi dengan Backend*: Menjembatani aplikasi Flutter dengan backend berbasis REST API, seperti Django.

Implementasi pada tugas ini:
- http.get: Digunakan untuk mengambil data dari API.
- http.post: Digunakan untuk mengirim data ke API, seperti data login atau registrasi.

---

## *3. Fungsi dari CookieRequest*
CookieRequest adalah komponen dari package pbp_django_auth yang digunakan untuk menangani sesi autentikasi berbasis cookie di Flutter. Fungsi utamanya:

- *Menyimpan Cookie*: Membantu menyimpan dan mengirimkan cookie yang diterima dari server Django untuk autentikasi.
- *Mengelola Sesi*: Memastikan pengguna tetap masuk (logged in) hingga mereka logout.
- *Mempermudah Request*: Menyediakan metode seperti login, logout, dan get untuk mempermudah komunikasi dengan server.

*Mengapa CookieRequest Perlu Dibagikan ke Semua Komponen?*
- Instance CookieRequest harus bersifat *global* karena cookie yang tersimpan di dalamnya digunakan untuk setiap request ke server.
- Dengan membagikannya, kita dapat menjaga sesi autentikasi dan memastikan bahwa semua komponen dalam aplikasi dapat mengakses data pengguna yang relevan.

---

## *4. Mekanisme Pengiriman Data dari Input hingga Ditampilkan pada Flutter*
1. *Input Data*:
   - Pengguna memasukkan data di aplikasi Flutter melalui widget seperti TextField atau Form.

2. *Pengiriman Data*:
   - Data yang diinput oleh pengguna dikumpulkan dan dikirim ke server menggunakan request HTTP (misalnya, http.post) atau melalui instance CookieRequest.

3. *Pengolahan Data di Backend*:
   - Backend Django menerima data, memprosesnya (misalnya, menyimpan ke database atau melakukan perhitungan), dan mengembalikan response dalam format JSON.

4. *Parsing Data*:
   - Data JSON dari response backend diterima oleh Flutter.
   - JSON di-decode menggunakan fungsi json.decode atau dimasukkan ke dalam model menggunakan fromJson.

5. *Menampilkan Data*:
   - Data yang telah diproses atau diubah menjadi model ditampilkan di UI Flutter menggunakan widget seperti ListView, Text, atau widget lainnya.

---

## *5. Mekanisme Autentikasi (Login, Register, Logout)*

#### *Mekanisme Login*:
1. Pengguna memasukkan username dan password di Flutter.
2. Flutter mengirimkan request POST ke endpoint Django (misalnya /auth/login/) dengan data username dan password.
3. Django:
   - Memvalidasi data pengguna di database.
   - Jika valid, mengembalikan response berisi cookie sesi yang akan digunakan untuk autentikasi selanjutnya.
4. Flutter:
   - CookieRequest menyimpan cookie sesi.
   - Menu utama atau halaman selanjutnya ditampilkan sesuai status login.

#### *Mekanisme Register*:
1. Pengguna mengisi form registrasi di Flutter.
2. Flutter mengirimkan request POST ke endpoint Django (misalnya /auth/register/) dengan data pengguna.
3. Django:
   - Memvalidasi dan menyimpan data pengguna di database.
   - Mengembalikan response sukses atau error.
4. Flutter:
   - Menampilkan notifikasi kepada pengguna berdasarkan response (misalnya, sukses registrasi).

#### *Mekanisme Logout*:
1. Pengguna menekan tombol logout di Flutter.
2. Flutter mengirimkan request ke endpoint Django (misalnya /auth/logout/).
3. Django:
   - Menghapus sesi pengguna di server.
4. Flutter:
   - Menghapus cookie dari CookieRequest.
   - Mengalihkan pengguna ke halaman login.

---

## Step by Step

### *1. Membuat Drawer Menu*
1. *Buat File Baru:*
   - Buat file left_drawer.dart di folder widgets untuk menampung komponen Drawer.

2. *Tambahkan Struktur Drawer:*
   - Gunakan widget Drawer yang berisi DrawerHeader untuk menampilkan judul aplikasi atau pesan motivasi.
   - Tambahkan beberapa ListTile untuk navigasi ke halaman lain seperti Halaman Utama dan Tambah Mood.

3. *Integrasikan Drawer ke Halaman Utama:*
   - Di file menu.dart atau halaman utama lainnya, tambahkan drawer ke dalam widget Scaffold dan impor LeftDrawer.

---

### *2. Membuat Halaman Form Tambah Mood*
1. *Buat File Baru:*
   - Buat file moodentry_form.dart untuk menampung halaman form.

2. *Tambahkan Scaffold dengan Drawer:*
   - Gunakan widget Scaffold untuk menambahkan AppBar dan Drawer ke halaman ini.

3. *Buat Form Input:*
   - Gunakan Form dengan beberapa TextFormField untuk menerima input dari pengguna:
     - *Mood*: Teks untuk mood yang dirasakan.
     - *Feelings*: Teks untuk deskripsi perasaan.
     - *Mood Intensity*: Angka untuk intensitas mood (misalnya skala 1-10).

4. *Tambahkan Tombol Simpan:*
   - Gunakan widget ElevatedButton untuk menyimpan input pengguna.
   - Validasi input menggunakan Form dan tampilkan dialog konfirmasi setelah data berhasil disimpan.

---

### *3. Menghubungkan Drawer Menu dengan Halaman Form*
1. *Tambahkan Navigasi:*
   - Di file left_drawer.dart, tambahkan fungsi navigasi ke halaman Form Tambah Mood menggunakan Navigator.pushReplacement.

2. *Uji Aplikasi:*
   - Jalankan aplikasi dan pastikan Drawer dapat digunakan untuk berpindah ke halaman Form Tambah Mood.

---
