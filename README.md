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
**Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement(), disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!**

**Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!**

**Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!**

**Bagaimana penerapan clean architecture pada aplikasi Flutter?**

**Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)**