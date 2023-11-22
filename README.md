# serpentshaven
<br>

### Tugas 7
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

### Tugas 8
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

<br>

### Tugas 9
---

**1. Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?**
Pengambilan data JSON tidak selalu memerlukan pembuatan model terlebih dahulu. JSON (JavaScript Object Notation) adalah format data yang sering digunakan untuk pertukaran data antar aplikasi. Jika hanya perlu mengambil atau membaca data JSON yang telah ada,  tidak perlu membuat model khusus untuk itu.

Pengambilan data JSON dapat dilakukan dengan menggunakan bahasa pemrograman yang mendukung manipulasi JSON, seperti Python, JavaScript, atau bahasa pemrograman lainnya. Misalnya, dalam Python, dapat digunakan library seperti `json` untuk membaca data JSON:

```python
import json

# Contoh string JSON
json_data = '{"nama": "John", "umur": 30, "kota": "Jakarta"}'

# Membaca data JSON menjadi objek Python
data = json.loads(json_data)

# Mengakses nilai dalam objek Python
print("Nama:", data['nama'])
print("Umur:", data['umur'])
print("Kota:", data['kota'])
```

Maka, jika tujuannya hanya untuk mengambil data dari format JSON yang sudah ada, tidak perlu membuat model lagi. Namun, jika ada kebutuhan khusus, seperti memproses atau menganalisis data secara kompleks, atau jika bekerja dengan data yang besar dan kompleks, maka pembuatan model atau penggunaan alat pengolahan data seperti Pandas dalam Python mungkin dapat membantu.

Pembuatan model seringkali diperlukan ketika berurusan dengan tugas tertentu, seperti pengenalan entitas dalam teks, analisis sentimen, atau prediksi berdasarkan data yang kompleks. Jadi, kebutuhan untuk membuat model bergantung pada tujuan analisis atau manipulasi data yang dilakukan.

<br>

**2. Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.**
`CookieRequest` digunakan untuk menyimpan atau mengelola informasi cookie yang berkaitan dengan permintaan HTTP. Cookie biasanya digunakan untuk menyimpan data di sisi klien dan sering digunakan dalam konteks otentikasi dan keamanan web.

Fungsi umum dari `CookieRequest` melibatkan hal-hal seperti:

1. **Menyimpan dan Mengelola Cookie:** Cookie dapat digunakan untuk menyimpan informasi otentikasi atau sesi, dan `CookieRequest` mungkin memiliki metode atau properti untuk menetapkan dan mendapatkan nilai cookie.

2. **Menanggapi Perubahan Otentikasi:** Jika aplikasi melibatkan otentikasi pengguna, `CookieRequest` dapat berperan dalam menanggapi perubahan status otentikasi. Ini dapat melibatkan menyimpan dan mengirim cookie yang sesuai dengan permintaan HTTP.

3. **Berinteraksi dengan API atau Server:** Cookie mungkin diperlukan untuk berinteraksi dengan API atau server tertentu yang mengharuskan adanya cookie tertentu dalam setiap permintaan.

4. **Pemeliharaan Keamanan:** Penggunaan cookie dapat berkaitan dengan pemeliharaan keamanan aplikasi, terutama dalam konteks otentikasi dan otorisasi.

Mengapa instance `CookieRequest` perlu dibagikan ke semua komponen di aplikasi Flutter?

1. **Keperluan Otentikasi yang Konsisten:** Jika ada beberapa komponen atau layar yang memerlukan otentikasi, memiliki satu instance `CookieRequest` yang dibagikan memastikan bahwa informasi otentikasi tetap konsisten di seluruh aplikasi. Sebagai contoh, jika token otentikasi disimpan dalam cookie, komponen yang berbeda dapat mengakses dan menggunakan informasi tersebut.

2. **Menghindari Duplikasi Kode:** Menggunakan satu instance `CookieRequest` dapat menghindari duplikasi kode untuk mengelola cookie di beberapa bagian aplikasi. Ini dapat menyederhanakan pengembangan dan pemeliharaan.

3. **Sinkronisasi State:** Jika ada perubahan pada state `CookieRequest`, seperti perubahan status otentikasi, memiliki satu instance memastikan bahwa perubahan tersebut tercermin di seluruh aplikasi tanpa perlu menyinkronkannya secara manual.

4. **Menghindari Duplikasi Data:** Jika ada data yang perlu dibagikan di antara komponen-komponen yang berbeda, menggunakan satu instance `CookieRequest` dapat membantu menghindari redundansi data dan memastikan konsistensi.

<br>

**3. Jelaskan mekanisme pengambilan data dari JSON hingga dapat ditampilkan pada Flutter.**
1. **Mengambil Data dari Server:**
   - Fungsi `fetchItem` menggunakan package `http` untuk mengambil data dari server dengan URL yang ditentukan.
   - Menggunakan `jsonDecode` untuk mendekode response dari server.

```dart
var url = Uri.parse('http://localhost:8000/json/');
var response = await http.get(url, headers: {"Content-Type": "application/json"});
var data = jsonDecode(utf8.decode(response.bodyBytes));
```

2. **Konversi JSON ke Objek Dart:**
   - Model `Item` dan `Fields` digunakan untuk mengonversi data JSON menjadi objek Dart.

```dart
List<Item> list_item = [];
for (var d in data) {
    if (d != null) {
        list_item.add(Item.fromJson(d));
    }
}
return list_item;
```

3. **Pengelolaan State:**
   - Menggunakan `FutureBuilder` untuk menangani kasus ketika data masih diambil (menampilkan `CircularProgressIndicator`) atau ketika terjadi kesalahan.
   - Menerapkan `Consumer` untuk mendengarkan perubahan pada objek `DataProvider` (atau `CookieRequest`).

```dart
FutureBuilder(
    future: fetchItem(),
    builder: (context, AsyncSnapshot snapshot) {
        if (snapshot.data == null) {
            return const Center(child: CircularProgressIndicator());
        } else {
            // ...
        }
    },
)
```

4. **Menampilkan Data di Flutter:**
   - Menggunakan `ListView.builder` untuk menampilkan daftar item.
   - Memanfaatkan model `Item` untuk mengakses properti seperti `name`, `price`, dan `description`.

```dart
ListView.builder(
    itemCount: snapshot.data!.length,
    itemBuilder: (_, index) => Container(
        // ...
    ),
)
```

5. **Dependency Injection:**
   - Menggunakan `Provider` untuk menyediakan instance dari `CookieRequest` ke seluruh aplikasi.

```dart
return Provider(
    create: (_) {
        CookieRequest request = CookieRequest();
        return request;
    },
    child: MaterialApp(
        // ...
    ),
);
```

<br>

**4. Jelaskan mekanisme autentikasi dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.**
Mekanisme autentikasi yang dijelaskan melibatkan interaksi antara aplikasi Flutter dan backend Django. Berikut adalah rangkuman dari langkah-langkahnya:

### Django (Backend):

1. **Settings Django (`snakeInventory/settings.py`):**
   - Mengatur middleware dan konfigurasi keamanan seperti `CORS_ALLOW_ALL_ORIGINS` untuk memungkinkan permintaan dari berbagai origin dan pengaturan keamanan cookie.

2. **Views Django (`authentication/views.py`):**
   - Terdapat fungsi `login` untuk mengautentikasi pengguna berdasarkan username dan password yang diterima dari permintaan POST. Jika berhasil, memberikan respons JSON yang berisi informasi pengguna dan status login.
   - Fungsi `logout` untuk melakukan logout pengguna dan memberikan respons JSON.

3. **URLs Django (`authentication/urls.py`):**
   - Mengatur URL untuk endpoint login dan logout.

### Flutter (Frontend):

1. **Libraries Flutter:**
   - Menggunakan library eksternal seperti `pbp_django_auth` untuk memfasilitasi autentikasi dengan Django.

2. **Screens Flutter (`lib/screens/login.dart`):**
   - Terdapat dua widget utama: `LoginApp` dan `LoginPage`.
   - `LoginPage` memiliki dua `TextField` untuk input username dan password, dan sebuah `ElevatedButton` untuk melakukan login.
   - Pada penekanan tombol login, aplikasi mengirim permintaan HTTP ke endpoint login Django menggunakan instance `CookieRequest` yang disediakan oleh `Provider`.
   - Jika login berhasil, aplikasi menavigasi ke halaman lain (`MyHomePage` dalam tugas ini).

3. **Main Dart (`main.dart`):**
   - Menggunakan `Provider` untuk menyediakan instance `CookieRequest` ke seluruh aplikasi.
   - Menjalankan `MyApp` sebagai root widget aplikasi, yang menampilkan halaman login.

<br>

**5. Sebutkan seluruh widget yang kamu pakai pada tugas ini dan jelaskan fungsinya masing-masing.**  

`lib/screens/list_item.dart`:
1. **Scaffold:** Menyediakan struktur dasar untuk tata letak dan navigasi.
2. **AppBar:** Menampilkan judul halaman "Item" di bagian atas.
3. **LeftDrawer:** Widget kustom yang menyediakan drawer (menu geser dari kiri) dengan navigasi ke berbagai bagian aplikasi.
4. **FutureBuilder:** Menerima data masa depan (future) dan membangun widget berdasarkan status future (loading, error, atau completed).
5. **CircularProgressIndicator:** Menampilkan indikator putar saat data masih diambil.
6. **Column:** Menyusun widget-child secara vertikal.
7. **Text:** Menampilkan pesan jika tidak ada data item.
8. **ListView.builder:** Membangun daftar item menggunakan data yang diterima dari future.
9. **Container:** Mengelilingi setiap item dalam daftar.
10. **Text:** Menampilkan informasi item seperti nama, harga, dan deskripsi.
<br>
<br>

`lib/screens/login.dart`:
1. **MaterialApp:** Widget utama aplikasi Flutter.
2. **Scaffold:** Menyediakan struktur dasar untuk tata letak dan navigasi.
3. **AppBar:** Menampilkan judul halaman "Login" di bagian atas.
4. **Container:** Mengelilingi kolom input dan tombol.
5. **Column:** Menyusun widget-child secara vertikal.
6. **TextField:** Input untuk username dan password.
7. **ElevatedButton:** Tombol untuk mengirimkan permintaan login.
8. **SnackBar:** Muncul saat login berhasil atau gagal.
9. **AlertDialog:** Muncul saat login gagal untuk memberi tahu pengguna.
<br>
<br>

`lib/screens/menu.dart`:
1. **Scaffold:** Menyediakan struktur dasar untuk tata letak dan navigasi.
2. **AppBar:** Menampilkan judul halaman "Snake Inventory" di bagian atas.
3. **LeftDrawer:** Widget kustom yang menyediakan drawer (menu geser dari kiri) dengan navigasi ke berbagai bagian aplikasi.
4. **SingleChildScrollView:** Membungkus seluruh tata letak dengan scroll view agar dapat digulir jika kontennya melebihi ukuran layar.
5. **Column:** Menyusun widget-child secara vertikal.
6. **Padding:** Memberikan jarak di sekitar elemen-elemen.
7. **Text:** Menampilkan judul "Serpent's Haven".
8. **GridView.count:** Menampilkan kotak-kotak (cards) yang berisi item-item seperti "Lihat Item", "Tambah Item", dan "Logout".
9. **ShopCard:** Widget kustom yang mewakili setiap item pada grid.
<br>
<br>

`lib/screens/shoplist_form.dart`:
1. **Scaffold:** Menyediakan struktur dasar untuk tata letak dan navigasi.
2. **AppBar:** Menampilkan judul halaman "Form Tambah Produk" di bagian atas.
3. **LeftDrawer:** Widget kustom yang menyediakan drawer (menu geser dari kiri) dengan navigasi ke berbagai bagian aplikasi.
4. **Form:** Membungkus seluruh form untuk validasi dan pengelolaan input.
5. **TextFormField:** Input untuk nama produk, harga, dan deskripsi.
6. **ElevatedButton:** Tombol untuk menyimpan produk baru.
7. **SnackBar:** Muncul saat simpan produk berhasil atau gagal.
8. **AlertDialog:** Muncul saat simpan produk gagal untuk memberi tahu pengguna.
<br>

**6. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).**
1. Membuat halaman login pada proyek tugas Flutter.  

2. Mengintegrasikan sistem autentikasi Django dengan proyek tugas Flutter.  

3. Membuat model kustom sesuai dengan proyek aplikasi Django.  

4. Membuat halaman yang berisi daftar semua item yang terdapat pada endpoint JSON di Django yang telah kamu deploy.  

5. Tampilkan name, amount, dan description dari masing-masing item pada halaman ini.  

6. Membuat halaman detail untuk setiap item yang terdapat pada halaman daftar Item.  

7. Halaman ini dapat diakses dengan menekan salah satu item pada halaman daftar Item.  

8. Tampilkan seluruh atribut pada model item kamu pada halaman ini.  

9. Tambahkan tombol untuk kembali ke halaman daftar item.  
