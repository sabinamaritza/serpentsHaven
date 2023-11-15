# serpentshaven
<br>

### Tugas 1
---

**1. Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?**  
**Stateless widget** merupakan widget yang tidak bisa diganti (immutable) sehingga data yang di display tidak akan berganti seperti teks judul, sedangkan **stateful widget** merupakan widget yang dapat diganti (mutable) sehingga widget bisa memegang data yang dapat berganti seperti sebuah counter.

**2. Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing.**  

#### **1. MaterialApp**
- **Function**: Root dari widget di dalam aplikasi, menyediakan *setting* seperti theme, title, dan home screen.

#### 2. **Scaffold**
- **Function**: Mengatur struktur layout home page secara visual.
- **Sub-widgets**:
    - **AppBar**: Memunculkan toolbar dengan judul.
    - **Body (SingleChildScrollView)**: Container *scrollable* sehingga bisa di-*scroll* jika kontennya melebihi batas ukuran layar.

#### 3. **Column**
- **Function**: Mengatur children nya secara vertikal.
- **Sub-widget**: 
    - **Padding**: Menambahkan padding di sekitar widget.
    - **Text**: Memunculkan teks.

#### 4. **GridView**
- **Function**: Menampilkan widget dalam array 2D yang bisa di *scroll*.
- **Sub-widget**:
    - **ShopCard (mapped items)**: Membuat list *cards* berdasarkan list **items**.

#### 5. **ShopCard (Custom Widget)**
- **Function**: Merepresentasikan setiap item dalam bentuk card.
- **Sub-widgets**:
    - **Material (InkWell)**: Menambahkan efek **tap** untuk card.
    - **Container**: Membuat container persegi untuk mengelompokkan konten dari card.
    - **Icon**: Menampilkan **icon** dari item
    - **Text**: Menampilkan **nama** dari item.
    - **SnackBar (ScaffoldMessenger)**: Menampilkan snackbar yang berisi teks yang menandakan bahwa card telah di-*click*.

**3. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial)**  
#### 1. **Membuat tiga tombol sederhana Lihat Item, Tambah Item, dan Logout dengan ikon dan teks**
Pertama, membuat class MyHomePage yang bersifat stateless karena isi dari home page nya tidak berganti-ganti. Lalu membuat class ShopItem untuk mendefinisikan data yang dibutuhkan untuk card tombol nya, setelah itu baru menambahkan list item dalam MyHomePage yang terdiri dari nama card beserta icon nya: "Lihat Item" dengan icon checklist, "Tambah Item" dengan icon cart, dan "Logout" dengan icon logout. Class MyHomePage juga mengatur grid penampilan dari cards yang ada. Kemudian akan ditambahkan class ShopCard yang menampilkan items dalam bentuk card.

#### 2. **Memunculkan Snackbar ketika tombol di-*click***
Pada class ShopCard, telah ditambahkan juga function onTap yang bertujuan untuk menampilkan snackbar ketika tombol nya di-*click*.

<br>

### Tugas 2
---
**1. Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement(), disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!**

1. **Navigator.push():**
   * Metode ini menambahkan halaman baru ke tumpukan navigasi.
   * Ketika menggunakan **Navigator.push()**, halaman saat ini tetap ada di tumpukan navigasi, dan halaman baru ditambahkan di atasnya.

   ```dart
   onTap: () {
      Navigator.push(
          context,
          MaterialPageRoute(
            builder: (context) => MyHomePage(),
          ));
   },
   ```
   Pada contoh di atas, ketika item di drawer diklik, halaman **MyHomePage** ditambahkan ke tumpukan navigasi.  
<br>

2. **Navigator.pushReplacement():**
   * Metode ini menggantikan halaman saat ini dengan halaman baru.
   * Setelah menggunakan **Navigator.pushReplacement()**, halaman saat ini dihapus dari tumpukan navigasi, dan halaman baru ditambahkan sebagai gantinya.

    Penggunaan dalam **left_drawer.dart** untuk ke halaman **MyHomePage**
   ```dart
    onTap: () {
      Navigator.pushReplacement(
        context,
        MaterialPageRoute(
          builder: (context) => MyHomePage(),
        ));
    },
   ```

Pemilihan antara keduanya tergantung pada kebutuhan aplikasi. Jika riwayat navigasi ingin disimpan, lebih baik menggunakan **Navigator.push()**. Namun, jika ingin mengganti halaman saat ini dan tidak ingin disimpan di tumpukan navigasi, **Navigator.pushReplacement()** lebih sesuai. Misalnya, ketika ingin mengganti halaman saat pengguna melakukan tindakan tertentu, seperti login berhasil, dan tidak ingin pengguna dapat kembali ke halaman login dengan menekan tombol *back*.

<br>

**2. Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!**  
Flutter menyediakan berbagai layout widgets yang dapat digunakan untuk mengatur tata letak (layout) dari elemen-elemen UI dalam aplikasi. Berikut adalah beberapa layout widget yang umum digunakan beserta konteks penggunaannya:

1. **Container:**
   - **Deskripsi:** `Container` adalah widget yang dapat digunakan untuk mengatur tata letak dan dekorasi dari anak-anaknya.
   - **Konteks Penggunaan:** Digunakan ketika ingin mengelompokkan beberapa widget ke dalam satu kotak dengan layout dan dekorasi tertentu.

   ```dart
   Container(
     width: 200.0,
     height: 100.0,
     color: Colors.blue,
     child: Text('Hello, World!'),
   )
   ```

2. **Row dan Column:**
   - **Deskripsi:** `Row` dan `Column` adalah widget yang digunakan untuk menempatkan children nya secara horizontal (`Row`) atau vertikal (`Column`).
   - **Konteks Penggunaan:** Digunakan untuk menyusun elemen-elemen UI secara berurutan.

   ```dart
   Row(
     children: [
       Icon(Icons.star),
       Text('5 stars'),
     ],
   )

   Column(
     children: [
       Text('First item'),
       Text('Second item'),
     ],
   )
   ```

3. **ListView:**
   - **Deskripsi:** `ListView` adalah widget yang dapat digunakan untuk menampilkan daftar scrollable dari widget children nya.
   - **Konteks Penggunaan:** Berguna untuk menampilkan daftar item, seperti dalam aplikasi daftar belanja atau berita.

   ```dart
   ListView(
     children: [
       ListTile(
         title: Text('Item 1'),
       ),
       ListTile(
         title: Text('Item 2'),
       ),
     ],
   )
   ```

4. **Stack:**
   - **Deskripsi:** `Stack` adalah widget yang memposisikan anak-anaknya satu di atas yang lain.
   - **Konteks Penggunaan:** Berguna ketika ingin menumpuk widget atau mengatur elemen secara relatif.

   ```dart
   Stack(
     children: [
       Container(
         width: 100.0,
         height: 100.0,
         color: Colors.red,
       ),
       Container(
         width: 50.0,
         height: 50.0,
         color: Colors.green,
       ),
     ],
   )
   ```

5. **Expanded dan Flexible:**
   - **Deskripsi:** `Expanded` dan `Flexible` adalah widget yang digunakan untuk memberikan fleksibilitas dalam layout, terutama di dalam `Row` dan `Column`.
   - **Konteks Penggunaan:** Digunakan untuk mengatur bagaimana ruang yang tersedia dibagi antara child `Row` atau `Column`.

   ```dart
   Row(
     children: [
       Expanded(
         child: Container(
           color: Colors.blue,
         ),
       ),
       Container(
         color: Colors.green,
       ),
     ],
   )
   ```

<br>

**3. Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!**  
Pada form dalam `ShopFormPage`, terdapat tiga elemen input utama:

1. **TextFormField untuk Nama Produk:**
   - **Deskripsi:** Digunakan untuk mengambil input nama produk dari pengguna.
   - **Alasan Penggunaan:** Nama produk merupakan informasi penting dalam formulir tambah produk. Pengguna diminta untuk memberikan input sesuai dengan nama produk yang ingin mereka tambahkan.

2. **TextFormField untuk Harga:**
   - **Deskripsi:** Menggunakan `TextFormField` untuk menerima input harga produk.
   - **Alasan Penggunaan:** Harga produk biasanya berupa angka. Dengan menggunakan `TextFormField` dan memberikan validasi, Anda dapat memastikan bahwa input yang dimasukkan adalah angka dan bukan teks. Selain itu, ini membantu dalam menghindari kesalahan input.

3. **TextFormField untuk Deskripsi:**
   - **Deskripsi:** Menyediakan `TextFormField` untuk menerima deskripsi produk.
   - **Alasan Penggunaan:** Deskripsi memberikan informasi tambahan tentang produk. Dengan menggunakan `TextFormField`, pengguna dapat memberikan deskripsi produk dengan nyaman dan memastikan bahwa deskripsi yang dimasukkan tidak kosong.

Penggunaan `TextFormField` pada ketiga elemen input ini memungkinkan pengguna untuk memberikan input dengan mudah sambil memberikan validasi untuk memastikan bahwa input sesuai dengan kebutuhan aplikasi. Selain itu, setiap `TextFormField` juga memberikan error message kepada pengguna melalui dekorasi dan message validasi yang ditampilkan.
<br>

**4. Bagaimana penerapan clean architecture pada aplikasi Flutter?**  
Clean Architecture adalah konsep arsitektur software yang bertujuan untuk memisahkan berbagai lapisan dalam aplikasi dengan tujuan utama agar kode menjadi bersih, terpisah, dan mudah diuji. Penerapan Clean Architecture dalam aplikasi Flutter melibatkan pembagian kode menjadi beberapa bagian. Pada proyek ini, dimana `widgets` berisi komponen UI yang dapat digunakan kembali (`ShopCard` dan `LeftDrawer`), sedangkan `screens` berisi layar utama aplikasi (`MyHomePage` dan `ShopFormPage`).

1. **Modularitas dan Dapat Digunakan Kembali:**
   - Menempatkan berkas yang terkait bersama-sama dalam sebuah direktori mempromosikan modularitas. Sebagai contoh, direktori `widgets` berisi komponen UI yang dapat digunakan kembali (`ShopCard` dan `LeftDrawer`) yang dapat dengan mudah digunakan kembali di berbagai layar.
   - Memisahkan layar ke dalam direktori mereka sendiri (`screens`) membuat jelas di mana halaman utama aplikasi berada, meningkatkan kejelasan dan organisasi.

2. **Organisasi dan Keterbacaan:**
   - Mengelompokkan berkas berdasarkan tipe atau fungsionalitas (misalnya, `widgets`, `screens`, dll.) membuatnya lebih mudah bagi pengembang untuk menemukan dan menjelajahi kode.
   - Ini meningkatkan keterbacaan struktur proyek secara keseluruhan, terutama dalam kode yang lebih besar.

3. **Pemisahan Kepentingan:**
   - Prinsip-prinsip Clean Architecture menekankan pemisahan kepentingan, membagi kode menjadi lapisan (misalnya, `domain`, `data`, `presentation`). Pemisahan ini membantu menjaga perbedaan yang jelas antara berbagai aspek aplikasi, seperti logika bisnis, penanganan data, dan UI.

4. **Kemudahan Pemeliharaan:**
   - Struktur direktori yang terorganisir dengan baik menyederhanakan proses pemeliharaan dan pembaruan kode. Pengembang dapat dengan cepat menemukan berkas yang terkait dengan fitur atau komponen tertentu.

<br>

**5. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)**
#### 1. **Membuat minimal satu halaman baru pada aplikasi, yaitu halaman formulir tambah item baru dengan ketentuan sebagai berikut:**
* Memakai minimal tiga elemen input, yaitu name, amount, description. Tambahkan elemen input sesuai dengan model pada aplikasi tugas Django yang telah kamu buat.  
Pertama, dibuat class baru untuk menampilkan page penambahan item baru. Dalam class tersebut, ditambahkan 3 variabel untuk menyimpan input pengguna: name, amount, dan description. Lalu, dibuat Form dengan child TextFormField untuk setiap variabel yang posisi nya diatur dengan Column.

* Memiliki sebuah tombol Save.  
Lalu, ditambahkan button Save yang di-align center. Button ini dibuat sehingga jika pengguna menekan tombol nya, Form akan di-validasi, dan menampilkan message jika ada error, dan jika semua elemen input tidak memiliki masalah, akan muncul sebuah dialog box yang berisi nama, harga, dan deskripsi dari item yang ditambah. Setelah itu, form input akan di-*reset*.

* Setiap elemen input di formulir juga harus divalidasi dengan ketentuan sebagai berikut:
    * Setiap elemen input tidak boleh kosong.  
    Hal-hal berikut akan di-*check* dengan membuat validator. Jika String nama, harga, atau deskripsi kosong, akan di-*return* "*nama field* tidak boleh kosong".
    * Setiap elemen input harus berisi data dengan tipe data atribut modelnya.  
    Untuk field harga, dipastikan dia berupa integer dengan cara melakukan parse kepada value yang di-*input* pengguna.

#### 2. **Mengarahkan pengguna ke halaman form tambah item baru ketika menekan tombol Tambah Item pada halaman utama.**  
Hal ini dilakukan dengan cara menambahkan barisan berikut ke dalam `shop_card.dart` untuk di-cek apakah button yang di-*click* memiliki nama "Tambah Item"
```dart
if (item.name == "Tambah Item") {
  Navigator.push(context,
    MaterialPageRoute(builder: (context) => const ShopFormPage()));
}
```

#### 3. **Memunculkan data sesuai isi dari formulir yang diisi dalam sebuah pop-up setelah menekan tombol Save pada halaman formulir tambah item baru.**  
Pada file `shoplist_form.dart`, ditambahkan AlertDialog dengan child Column yang mengatur children Text berisi nama, harga, dan deskripsi.

#### 4. **Membuat sebuah drawer pada aplikasi dengan ketentuan sebagai berikut:**
Membuat file `left_drawer.dart` yang berfungsi untuk menampilkan drawer dan menavigasi pengguna ke halaman `menu.dart` dan `shoplist_form.dart`

* Drawer minimal memiliki dua buah opsi, yaitu Halaman Utama dan Tambah Item.  
Menambahkan ListTile pada Drawer dengan nama Halaman Utama dan Tambah Item beserta icon yang sesuai.
* Ketika memiih opsi Halaman Utama, maka aplikasi akan mengarahkan pengguna ke halaman utama.  
Menggunakan Navigator.pushReplacement untuk me-redirect ke halaman menu.dart
* Ketika memiih opsi (Tambah Item), maka aplikasi akan mengarahkan pengguna ke halaman form tambah item baru.  
Menggunakan Navigator.push untuk me-redirect ke halaman shoplist_form.dart