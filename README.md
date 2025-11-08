# futbolshop

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

====================================================================================================================

===== TUGAS 7 =====
- Jelaskan apa itu widget tree pada Flutter dan bagaimana hubungan parent-child (induk-anak) bekerja antar widget.
widget tree adalah struktur hirarki yang menggambarkan UI pada proyek flutter. setiap widget adalah anak dari parentnya. dalam hubungannya parent bertugas untuk mewariskan batasan ke anaknya untuk mengontrol anaknya dan anaknya bertugas untuk menerima warisan batasan dari parentnya dan mengatur ukurannya sendiri berdasarkan warisan batasannya.

- Sebutkan semua widget yang kamu gunakan dalam proyek ini dan jelaskan fungsinya.
MyApp : widget root yang merender MaterialApp
MyHomePage: widget yang mendefinisikan seluruh tata letak home page
InfoCard: widget yg menampilkan kartu berisi judul dan NPM, nama, kelas
ItemCard: widget yang menampilkan item menu di GridView
MaterialApp: widget root yang membungkus seluruh aplikasi dan menyediakan tema dan navigasi
Scaffold: menyediakan kerangka visual dasar untuk layar
AppBar: menyediakan judul di bagian atas
Theme: mengatur skema warna aplikasi

- Apa fungsi dari widget MaterialApp? Jelaskan mengapa widget ini sering digunakan sebagai widget root.
fungsi dari widget MaterialApp adalah menyediakan skema warna dan style font yang bisa diakses oleh widget childnya, mengelola navigasi yg memungkinkan berpindah halaman. widget ini sering digunakan sebagai widget root karena dia menyediakan fitur2 penting ke seluruh widget di app

- Jelaskan perbedaan antara StatelessWidget dan StatefulWidget. Kapan kamu memilih salah satunya?
stateless widget adalah widget yang tidak akan berubah dalam situasi apapun. kalau statefull widget adalah widget yang bisa berubah dalam situasi tertentu. stateless digunakan saat ingin membuat widget yg tidak perlu berubah dalam semua situasi, statefull digunakan saat tampilan widget perlu berubah untuk interaksi ke user

- Apa itu BuildContext dan mengapa penting di Flutter? Bagaimana penggunaannya di metode build?
BuildContext adalah yang memberi tahu lokasi sebuah widget di dalam Widget Tree. sangat penting karena widget tidak bisa melihat parent nya tanpa BuildContext. metode build(BuildContext context) menerima context kemudian menggunakannya untuk mencari warisan parent terdekat. contohnya Theme.of(context) mencari ke parent2 dan menemukan ThemeData terdekat

- Jelaskan konsep "hot reload" di Flutter dan bagaimana bedanya dengan "hot restart".
hot reload itu langsung menyisipkan kode2 baru diubah ke virtual machine yang sedang run, hot reload sangat cepat dan biasanya dipakai untuk melihat hasil dari perubahan UI, hot reload juga menyimpan state dari aplikasi. kalau hot restart itu mematikan vm yang sedang run dan mulai ulang seluruh aplikasi dari awal, hot restart lebih lambat dari hot reload, biasanya digunakan jika ada perubahan data atau logika dalam kodenya, hot restart tidak menyimpan state aplikasinya 


====================================================================================================================

===== TUGAS 8 =====

- Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement() pada Flutter. Dalam kasus apa sebaiknya masing-masing digunakan pada aplikasi Football Shop kamu?
kalau Navigator.push() menambahkan halaman baru ke stack halaman dan halaman2 sebelumnya masih ada dibawahnya, user bisa return ke halaman sebelumnya. kalau Navigator.pushReplacement() halaman sekarang diganti ke halaman baru dan halaman yang sekarang langsung dibuang dari memori, user tidak bisa return ke halaman sebelumnya. 
dalam kasus ingin membuka detail produk sebaiknya menggunakan Navigator.push() dan dalam kasus pindah halaman setelah login berhasil sebaiknya pakai Navigator.pushReplacement() agar user tidak bisa return ke halaman login

- Bagaimana kamu memanfaatkan hierarchy widget seperti Scaffold, AppBar, dan Drawer untuk membangun struktur halaman yang konsisten di seluruh aplikasi?
Scaffold: sebagai kerangka dasar untuk setiap halaman, menyediakan slot untuk appBar, body, dan Drawer
AppBar: berada di slot appBar pada Scaffold, memastikan setiap halaman memiliki judul yang sama di bagian atas
Drawer: berada di slot Drawer pada Scaffold, Scaffold yg menangani logika membuka dan menutup drawer

- Dalam konteks desain antarmuka, apa kelebihan menggunakan layout widget seperti Padding, SingleChildScrollView, dan ListView saat menampilkan elemen-elemen form? Berikan contoh penggunaannya dari aplikasi kamu.
Padding:
    Kelebihan: Memberi ruang di sekitar TextFormField. Tanpa Padding, field menempel satu sama lain

    Contoh: "Padding(padding: EdgeInsets.all(10))," >>> memberi jarak 10 piksel di sekeliling setiap field.

SingleChildScrollView:
    Kelebihan: membungkus Column yang lebih panjang dari layar dan memungkinkan seluruh form di-scroll secara vertikal 

    Contoh: "child: SingleChildScrollView( child: Column(..." >>> membungkus seluruh Column yang berisi Padding dan TextFormField

ListView:
    Kelebihan: untuk daftar yang sangat panjang atau dinamis, ia hanya render item yang terlihat di layar

    Contoh: "child: ListView(
        children: ["

- Bagaimana kamu menyesuaikan warna tema agar aplikasi Football Shop memiliki identitas visual yang konsisten dengan brand toko?
Cara terbaik untuk memastikan konsistensi brand adalah mendefinisikan tema di dalam MaterialApp (di main.dart) >>> "return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSwatch(primarySwatch: Colors.blue)
        .copyWith(secondary: Colors.blueAccent[400]),
      ),
      home: MyHomePage(),
    );"