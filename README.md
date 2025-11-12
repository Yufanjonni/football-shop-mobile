<details>
<summary>Tugas 7</summary>
# Jelaskan apa itu widget tree pada Flutter dan bagaimana hubungan parent-child (induk-anak) bekerja antar widget.

Flutter membangun seluruh antarmuka pengguna (UI) dengan struktur pohon widget (widget tree).
Artinya, setiap elemen di layar — seperti teks, tombol, kolom, atau gambar — adalah sebuah widget, dan widget bisa memiliki anak (child) atau beberapa anak (children). Hubungan ini membentuk hierarki UI yang disebut widget tree, dan saat Flutter melakukan rendering, perubahan di satu node akan mempengaruhi tampilan turunannya.

## Sebutkan semua widget yang kamu gunakan dalam proyek ini dan jelaskan fungsinya.
- **Scaffold**: Menjadi kerangka dasar halaman dengan AppBar dan body.	
- **AppBar**: Menampilkan judul halaman di bagian atas.	
- **Padding**: Memberikan jarak di sekeliling konten halaman.	
- **Column**: Menyusun widget secara vertikal.	
- **SizedBox**: Memberi jarak vertikal antar widget.	
- **Center**: Menempatkan widget di tengah layar.	
- **Text**: Menampilkan teks statis.	
- **GridView.count**: Menampilkan widget dalam format grid.
- **Material**: Membungkus kartu agar mendukung efek Material (shadow, ripple).	
- **InkWell**: Menangani interaksi klik/tap pada kartu.	
- **SnackBar**: Menampilkan notifikasi sementara saat kartu ditekan.	
- **Container**: Mengatur padding dan layout isi kartu.	
- **Icon**: Menampilkan ikon.	
- **ItemCard**: Menampilkan 1 item (ikon + teks + warna).	
- **ItemHomepage**: Model data untuk tiap item (nama, ikon, warna).

## Apa fungsi dari widget MaterialApp? Jelaskan mengapa widget ini sering digunakan sebagai widget root.

MaterialApp adalah widget root dalam aplikasi Flutter berbasis Material Design.
Widget ini menyediakan:

1. Tema global (ThemeData)

2. Routing dan navigasi (Navigator)

3. Title aplikasi

4. Localizations (bahasa, format tanggal)

5. Debug banner control (menonaktifkan banner debug)

## Jelaskan perbedaan antara StatelessWidget dan StatefulWidget. Kapan kamu memilih salah satunya?
StatelessWidget
    1. Keadaan (State) Tidak berubah
    2. Digunakan untuk	Tampilan statis (misal teks, ikon, gambar tetap)
    3. Contoh penggunaan Text, Icon, Container
    4. Lifecycle Hanya dibangun sekali

StatefulWidget
    1. Keadaan (State) Dapat berubah (mutable)
    2. Digunakan untuk Tampilan dinamis (misal input pengguna, data dari API)
    3. Contoh penggunaan TextField, Checkbox, ListView dengan data dinamis
    4. Memiliki lifecycle: initState(), setState(), dispose()

## Apa itu BuildContext dan mengapa penting di Flutter? Bagaimana penggunaannya di metode build?

**BuildContext** adalah objek yang merepresentasikan lokasi sebuah widget dalam widget tree.
BuildContext penting Karena Flutter membangun UI sebagai tree of widgets, setiap widget perlu tahu hubungan dengan widget di atasnya agar bisa:
    1. Mengambil data dari widget induk (parent)
    2. Menampilkan elemen seperti SnackBar atau Dialog
    3. Navigasi antar halaman

Metode build(BuildContext context) untuk mengakses context saat membangun UI.

## Jelaskan konsep "hot reload" di Flutter dan bagaimana bedanya dengan "hot restart".
- **Hot Reload** Memuat ulang kode sumber dan memperbarui UI tanpa menghapus state
- **Hot Restart** Memulai ulang seluruh aplikasi dari awal

</details>

<details>
<summary>Tugas 8<summary>
## Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement() pada Flutter. Dalam kasus apa sebaiknya masing-masing digunakan pada aplikasi Football Shop kamu?

**Navigator.push()** menambahkan (push) halaman baru di atas halaman saat ini di stack navigasi.
- Halaman lama tetap tersimpan di memori (tidak hilang).
- User bisa kembali ke halaman sebelumnya dengan tombol Back.

**Navigator.pushReplacement()** mengganti (replace) halaman saat ini dengan halaman baru.
- Halaman lama dihapus dari stack (tidak bisa kembali ke sana).
- Tombol “Back” tidak akan mengembalikan ke halaman sebelumnya, karena sudah diganti.

## Bagaimana kamu memanfaatkan hierarchy widget seperti Scaffold, AppBar, dan Drawer untuk membangun struktur halaman yang konsisten di seluruh aplikasi?

1. **Scaffold**: kerangka dasar halaman di Flutter menyediakan struktur visual utama: AppBar, Drawer, Body, FloatingActionButton, dll.
2. **AppBar**: bagian header halaman (biasanya berisi judul, logo, atau tombol aksi).
3. **Drawer**: digunakan untuk navigasi antar halaman utama aplikasi.

Dengan menggunakan kombinasi:
-Scaffold untuk struktur halaman utama,
-AppBar untuk judul dan aksi global,
-Drawer untuk navigasi antar halaman utama,

##  Dalam konteks desain antarmuka, apa kelebihan menggunakan layout widget seperti Padding, SingleChildScrollView, dan ListView saat menampilkan elemen-elemen form? Berikan contoh penggunaannya dari aplikasi kamu.

1. **Padding**
- Meningkatkan keterbacaan dan kenyamanan visual.
- Mencegah elemen bertabrakan dengan tepi layar.
- Membantu menciptakan spacing yang konsisten di seluruh halaman.

<pre>Padding(
  padding: const EdgeInsets.all(8.0),
  child: TextFormField(
    decoration: InputDecoration(
      hintText: "Nama Product",
      labelText: "Nama Product",
      border: OutlineInputBorder(
        borderRadius: BorderRadius.circular(5.0),
      ),
    ),
  ),
),</pre>

2. **SingleChildScrollView**
- Mencegah error "Bottom Overflowed by pixels" saat keyboard muncul.
- Cocok untuk form panjang yang tidak muat di satu layar.
- Memastikan pengguna bisa mengakses semua input tanpa terpotong.

<pre>
body: Form(
  key: _formKey,
  child: SingleChildScrollView(
    child: Column(
      children: [
        // ... banyak TextFormField
      ],
    ),
  ),
),</pre>

3. **ListView**
-
-
-

<pre>
 child: ListView(
        children: [
          const DrawerHeader(
            decoration: BoxDecoration(color: Colors.blue),
            child: Column(
              children: [
                Text(
                  'Football Shop',
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 30,
                    fontWeight: FontWeight.bold,
                    color: Colors.white,
                  ),
                ),
              ],
            ),
          )
        ],
        ),
</pre>

## Bagaimana kamu menyesuaikan warna tema agar aplikasi Football Shop memiliki identitas visual yang konsisten dengan brand toko?

warna tema disesuaikan melalui properti seperti AppBar.backgroundColor dan ElevatedButton.styleFrom().
<details>