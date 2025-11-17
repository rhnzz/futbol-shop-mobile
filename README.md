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

====================================================================================================================

===== TUGAS 9 =====

- Jelaskan mengapa kita perlu membuat model Dart saat mengambil/mengirim data JSON? Apa konsekuensinya jika langsung memetakan Map<String, dynamic> tanpa model (terkait validasi tipe, null-safety, maintainability)?
Memerlukan membuat model dart karena untuk memastikan data JSON yang diambil memiliki tipe yang sesuai dan tidak null (type safety dan null safety). Konsekuensinya jika langsung memetakan adalah kode jadi lebih mungkin terjadi runtime error, karena diperlukannya validasi tipe dan null. maintainability menjadi lebih susah.

- Apa fungsi package http dan CookieRequest dalam tugas ini? Jelaskan perbedaan peran http vs CookieRequest.
http berfungsi untuk mengirim dan menerima response HTTP, GET POST. CookieRequest berfungsi untuk menyimpan session cookie (sessionid dan CSRF token). perbedaan keduanya, kalau http menangani transfer data, sedangkan cookieRequest menangani autentikasi.

- Jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.
diperlukan karena cookieRequest menyimpan state autentikasi, jadi semua request HTTP akan menggunakan cookie yang sama untuk memastikan user masih terautentikasi  

- Jelaskan konfigurasi konektivitas yang diperlukan agar Flutter dapat berkomunikasi dengan Django. Mengapa kita perlu menambahkan 10.0.2.2 pada ALLOWED_HOSTS, mengaktifkan CORS dan pengaturan SameSite/cookie, dan menambahkan izin akses internet di Android? Apa yang akan terjadi jika konfigurasi tersebut tidak dilakukan dengan benar?
10.0.2.2 perlu ditambahkan karena itu adalah IP yang digunakan untuk merujuk ke tempat django berjalan. jika tidak ditambahkan, django akan HTTP 400 bad request. mengaktifkan CORS dibutuhkan agar django mengizinkan request dari flutter, jika tidak permintaan bisa diproses. menambahkan izin akses internet di android karena agar aplikasi tidak diblokir dari akses internet.

- Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.
user input data (flutter) -> data diubah menjadi model dart -> model diubah manjadi JSON -> mengirim HTTP POST ke django (JSON dan cookie) -> django memproses JSON dan memvalidasi cookie dan menyimpan data ke database -> django meresponse 200 ok -> flutter menerima response -> JSON diubah kembali menjadi model dart  

- Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.
register: flutter mengirim username, password (POST) dalam bentuk JSON ke register django. django membuat user dan menyimpan ke database dan memberi respon 200
login: flutter mengirim useername dan password (POST) dalam JSON ke endpoint register django. django memverifikasi dan jika berhasil akan memanggil django.contrib.auth.login() dan membuat session di database dan mengatur session id cookie
logout: POSt ke endpoint logout django. django memanggil django.contrib.auth.logout() untuk menghapus seesion dari database  

- Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).
(django) menambahkan app authenticaton lalu menginstall django-cors-headers lalu menyesuaikan settings.py (menambahkan authentication di installed apps, menambahkan 10.0.2.2 di allowed host, menambahkan corsheaders ke installed apps, dan yang lainnya)
(flutter) menambahkan depedensi dan menambahkan izin akses internt di android manifest
(django) membuat fungsi login logout register di authentication/views.py dan menambahkan pathn di untuk login logout register di authentication/urls.py
(flutter) menambahkan Provider<CookieRequest> untuk membagikan CookieRequest ke semua komponen agar dapat diakses ke seluruh aplikasi. lalu membuat halaman  untuk login dan register (login.dart dan register.dart)
(quick type) mengambil response JSON untuk di copy paste ke  quick type dan mengahasilkan model dart
(django) menambahkan endpoint proxy image dan create product flutter di main/views.py. lalu menambahkan path keduanya ke main/urls.py
(flutter) membuat halaman yang memuat dan menampilkan seluruh produk dan produk yang berintegrasi dengan user yang sedang login saja (produk yang dijual user yang sedang login) 
(django) menambahkan endpoint my product json dan menambahkan path nya (di main/vies.py dan main/urls.py)
(flutter) membuat product detail dart untuk menampilkan detail product. dan update widget-widget di main menu dan drawer
