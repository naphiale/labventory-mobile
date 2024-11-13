# labventory

A new Flutter project.

## Getting Started

---
# Tugas 7

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

# Tugas 8

## 1. Kegunaan dan Keuntungan Menggunakan const di Flutter
#### *Kegunaan const:*
- const digunakan untuk mendefinisikan *immutable widgets* atau nilai tetap yang tidak berubah selama runtime.
- Memberitahu Flutter untuk *mengoptimalkan widget* karena nilainya tidak akan berubah.

#### *Keuntungan Menggunakan const:*
1. *Efisiensi Memori:* Widget yang menggunakan const disimpan sebagai satu instance dalam memori, sehingga mengurangi alokasi memori.
2. *Performa Lebih Baik:* Flutter dapat menghindari render ulang pada widget const karena dianggap tidak berubah.
3. *Meningkatkan Readability:* Memberikan sinyal kepada developer lain bahwa widget atau nilai bersifat tetap.

#### *Kapan Menggunakan const:*
- Gunakan const untuk widget yang tidak akan berubah nilainya selama runtime, seperti teks statis, padding tetap, atau icon.

#### *Kapan Tidak Menggunakan const:*
- Hindari const untuk widget yang bergantung pada input atau variabel dinamis yang nilainya berubah selama runtime.

## 2. Perbandingan Column dan Row
#### *Column:*
- Menyusun widget *secara vertikal* (dari atas ke bawah).
- Cocok untuk layout berbasis konten seperti form atau daftar.

#### *Row:*
- Menyusun widget *secara horizontal* (dari kiri ke kanan).
- Digunakan untuk menampilkan elemen yang berjejer, seperti ikon dengan teks.

#### *Contoh Implementasi:*
1. *Column:*
   dart
   Column(
     mainAxisAlignment: MainAxisAlignment.center,
     children: [
       Text('Judul'),
       Text('Subjudul'),
       ElevatedButton(onPressed: () {}, child: Text('Klik'))
     ],
   )
   

2. *Row:*
   dart
   Row(
     mainAxisAlignment: MainAxisAlignment.spaceBetween,
     children: [
       Icon(Icons.menu),
       Text('Judul Halaman'),
       Icon(Icons.settings)
     ],
   )
   


## *3. Elemen Input yang Digunakan dan Elemen Lainnya*
#### *Elemen Input yang Digunakan:*
- *TextFormField:* Untuk menerima teks (misalnya, mood dan deskripsi perasaan).
- *Slider:* Untuk menerima intensitas mood dalam skala tertentu.
- *ElevatedButton:* Untuk tombol simpan data.

#### *Elemen Input Lain yang Tidak Digunakan:*
- *Checkbox:* Untuk memilih nilai boolean (ya/tidak).
- *Switch:* Untuk mengaktifkan/mematikan fitur tertentu.
- *Radio:* Untuk memilih salah satu dari beberapa opsi.
- *DropdownButton:* Untuk memilih opsi dari daftar dropdown.
- *DatePicker:* Untuk memilih tanggal.

Elemen ini tidak digunakan karena tidak relevan dengan form mood entry.

## 4. Mengatur Tema dalam Aplikasi Flutter
#### *Mengatur Tema:*
- Tema dapat diatur menggunakan properti ThemeData di MaterialApp.
- Contohnya:
  dart
  MaterialApp(
    theme: ThemeData(
      primaryColor: Colors.blue,
      textTheme: TextTheme(
        bodyText1: TextStyle(fontSize: 16, color: Colors.black),
      ),
    ),
  );
  

#### *Konsistensi Tema:*
- Menggunakan tema global memastikan semua widget menggunakan gaya yang seragam.
- Tema ini mencakup warna utama, font, dan gaya teks.

#### *Implementasi Tema di Proyek Ini:*
- Jika tema belum diterapkan, sebaiknya tambahkan untuk konsistensi desain.

## 5. Menangani Navigasi dengan Banyak Halaman
#### *Cara Menangani Navigasi:*
1. *Menggunakan Navigator:*
   - Metode push dan pushReplacement digunakan untuk berpindah halaman.
   dart
   Navigator.push(context, MaterialPageRoute(builder: (context) => HalamanBaru()));
   

2. *Menentukan Route di MaterialApp:*
   - Menentukan daftar route di MaterialApp untuk navigasi yang lebih terstruktur.
   dart
   MaterialApp(
     initialRoute: '/',
     routes: {
       '/': (context) => HomePage(),
       '/form': (context) => FormPage(),
     },
   );
   

3. *Library Navigasi Lainnya:*
   - Gunakan *go_router* atau *auto_route* untuk navigasi yang lebih kompleks.

---
