# Posttest PBO 2
## Sistem Pengelolaan Pemesanan Album dan Merchandise K-pop

### 1. Penjelasan Program

Program ini merupakan sistem sederhana untuk mengelola produk K-pop berupa album dan merchandise serta pemesanan produk.

Program menerapkan konsep Object Oriented Programming (OOP), yaitu class dan object, atribut dan method, encapsulation, inheritance, serta relasi antarclass.

Class yang digunakan dalam program:
- ProdukKpop
- Album
- Merchandise
- Katalog
- DetailPesanan
- Pesanan

### 2. Inheritance

Inheritance digunakan pada class `Album` dan `Merchandise` yang mewarisi class `ProdukKpop`.

`ProdukKpop` berperan sebagai superclass, sedangkan `Album` dan `Merchandise` sebagai subclass.

```text
ProdukKpop
├── Album
└── Merchandise
```

Kedua subclass menggunakan constructor dari superclass dengan:

```python
super().__init__(idProduk, namaProduk, harga, stok)
```

Class `Album` memiliki atribut khusus:
- `artis`
- `versiAlbum`
- `jumlahLagu`

Class `Merchandise` memiliki atribut khusus:
- `jenisMerch`
- `ukuran`
- `bahan`

Method `tampilkan_produk()` dioverride pada kedua subclass.

### 3. Encapsulation

Program menggunakan atribut protected dan private.

Atribut protected yang digunakan adalah:

```python
self._harga
```

Atribut `_harga` berada pada superclass `ProdukKpop` dan digunakan langsung oleh subclass `Album` dan `Merchandise`.

Atribut private yang digunakan adalah:

```python
self.__stok
```

Atribut `__stok` berada pada class `ProdukKpop` dan diakses melalui property `stok`.

Program juga menggunakan `@property` dan setter untuk mengatur nilai `stok` dan `harga`. Setter melakukan validasi agar nilai yang diberikan tidak boleh 0 atau kurang.

### 4. Relasi Antarclass

#### a. Asosiasi

Asosiasi terdapat antara class `Pesanan` dengan `ProdukKpop`.

Pada class `Pesanan` terdapat:

```python
self.produk = produk
```

Hal ini menunjukkan bahwa sebuah pesanan memiliki hubungan dengan produk yang dipesan.

Contoh penggunaannya:

```python
pesanan1 = Pesanan(
    "O001",
    album1,
    2
)
```

Objek `album1` digunakan sebagai produk pada objek `pesanan1`.

#### b. Agregasi

Agregasi terdapat antara class `Katalog` dengan produk.

Class `Katalog` memiliki daftar produk:

```python
self.daftar_produk = []
```

Produk dibuat terlebih dahulu sebagai object yang berdiri sendiri, kemudian dimasukkan ke dalam katalog menggunakan method `tambah_produk()`.

Contohnya:

```python
katalog1.tambah_produk(album1)
katalog1.tambah_produk(album2)
```

Hal ini menunjukkan bahwa `Katalog` hanya menampung object produk yang sudah dibuat sebelumnya.

#### c. Komposisi

Komposisi terdapat antara class `Pesanan` dengan `DetailPesanan`.

Pada saat object `Pesanan` dibuat, object `DetailPesanan` juga dibuat di dalam constructor `Pesanan`:

```python
self.detail_pesanan = DetailPesanan(produk, jumlah)
```

`DetailPesanan` digunakan untuk menghitung subtotal dari produk yang dipesan.

Method yang digunakan adalah:

```python
def hitung_subtotal(self):
    return self.produk.harga * self.jumlah
```

### 5. Method pada Program

Program menggunakan beberapa jenis method.

#### Instance Method

Instance method digunakan untuk menjalankan fungsi dari object, contohnya:

- `tampilkan_produk()`
- `ubah_harga()`
- `tampilkan_katalog()`
- `hitung_total()`

#### Class Method

Class method digunakan untuk mengubah data yang dimiliki oleh class.

Contohnya:

```python
@classmethod
def ubah_nama_toko(cls, nama_baru):
    cls.nama_toko = nama_baru
```

dan:

```python
@classmethod
def ubah_status_default(cls, status_baru):
    cls.status_default = status_baru
```

#### Static Method

Static method digunakan untuk melakukan validasi tanpa bergantung pada object tertentu.

Contohnya:

```python
@staticmethod
def validasi_harga(harga):
    return harga > 0
```

dan:

```python
@staticmethod
def validasi_jumlah(jumlah):
    return jumlah > 0
```

### 6. Pengujian Program

Program melakukan beberapa pengujian, yaitu:

- Menampilkan data album.
- Menampilkan data merchandise.
- Menampilkan isi katalog.
- Menampilkan data pesanan.
- Mengubah nama toko menggunakan class method.
- Mengubah status default pesanan menggunakan class method.
- Melakukan validasi harga menggunakan static method.
- Melakukan validasi jumlah pesanan menggunakan static method.
- Mengubah stok album menggunakan setter.
- Menguji validasi stok dengan memasukkan nilai 0.
- Mengubah harga album menggunakan setter.
- Menampilkan seluruh produk.
- Menghapus produk dari daftar produk.
- Menampilkan total produk.
- Menampilkan total pesanan.

### 7. Kesimpulan

Program ini menerapkan konsep Object Oriented Programming dengan menggunakan class dan object, encapsulation, inheritance, serta relasi antarclass.

Inheritance diterapkan melalui superclass `ProdukKpop` dan subclass `Album` serta `Merchandise`.

Relasi asosiasi diterapkan pada `Pesanan` dengan `ProdukKpop`, agregasi diterapkan pada `Katalog` dengan produk, dan komposisi diterapkan pada `Pesanan` dengan `DetailPesanan`.

Program juga menggunakan atribut protected `_harga`, atribut private `__stok`, instance method, class method, static method, property, dan setter.