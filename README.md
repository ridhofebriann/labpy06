# labpy06
Nama        : M.Ridho Febrian <p>

Kelas       : TI.24.A.5 <p>

Nim         : 312410500 <p>

Mata kuliah : Bahasa Pemrograman <p>

# Praktikum 6

# Program daftar nilai Mahasiswa

Pada praktikum 6, kita akan membuat program sederhana untuk membuat daftar nilai mahasiswa menggunakan Dictionary dengan python.

#### Codingan Praktikum 6

```python

daftar_mahasiswa = {}

def tambah_siswa():
    """Fungsi untuk menambahkan siswa baru ke dalam daftar_mahasiswa."""
    nama_siswa = input("Masukkan nama siswa: ")
    jumlah_mata_pelajaran = int(input("Masukkan jumlah mata pelajaran: "))

    nilai_siswa = {}  # Sebuah dictionary kosong untuk menyimpan pasangan mata pelajaran-nilai untuk siswa

    # Loop untuk input mata pelajaran dan nilai
    for i in range(jumlah_mata_pelajaran):
        mata_pelajaran = input(f"Masukkan nama mata pelajaran {i + 1}: ")
        nilai = float(input(f"Masukkan nilai {mata_pelajaran}: "))
        nilai_siswa[mata_pelajaran] = nilai  # Simpan pasangan mata pelajaran-nilai dalam dictionary nilai_siswa

    daftar_mahasiswa[nama_siswa] = nilai_siswa  # Simpan nilai siswa dalam dictionary daftar_mahasiswa
    print(f"{nama_siswa} telah ditambahkan dengan nilai: {nilai_siswa}")

def hitung_rata_rata(nama_siswa):
    """Fungsi untuk menghitung rata-rata nilai siswa."""
    nilai_siswa = daftar_mahasiswa.get(nama_siswa)  # Mengambil dictionary mata pelajaran-nilai untuk nama siswa yang diberikan

    if nilai_siswa:
        total = sum(nilai_siswa.values())  # Hitung total nilai
        jumlah_mata_pelajaran = len(nilai_siswa)  # Hitung jumlah mata pelajaran
        rata_rata = total / jumlah_mata_pelajaran  # Hitung rata-rata

        return rata_rata
    else:
        return None

def tampilkan_info_siswa():
    """Fungsi untuk menampilkan informasi nilai siswa dan rata-ratanya."""
    nama_siswa = input("Masukkan nama siswa untuk menampilkan info: ")
    nilai_siswa = daftar_mahasiswa.get(nama_siswa)  # Ambil data siswa

    if nilai_siswa:
        print(f"Nilai untuk {nama_siswa}:")
        for mata_pelajaran, nilai in nilai_siswa.items():
            print(f"{mata_pelajaran}: {nilai}")

        rata_rata = hitung_rata_rata(nama_siswa)  # Hitung rata-rata nilai siswa
        print(f"Nilai rata-rata: {rata_rata}")

    else:
        print(f"{nama_siswa} tidak ditemukan!!")

def hapus(nama):
    """Fungsi untuk menghapus data siswa berdasarkan nama."""
    if nama in daftar_mahasiswa:
        del daftar_mahasiswa[nama]  # Hapus data siswa
        print(f"Data untuk {nama} telah dihapus.")
    else:
        print(f"{nama} tidak ditemukan dalam data siswa.")

def ubah(nama):
    """Fungsi untuk mengubah nilai mata pelajaran siswa yang sudah ada."""
    if nama in daftar_mahasiswa:
        print(f"Data saat ini untuk {nama}: {daftar_mahasiswa[nama]}")
        jumlah_mata_pelajaran = int(input("Masukkan jumlah mata pelajaran yang ingin diubah: "))
        
        # Loop untuk mengubah nilai
        for i in range(jumlah_mata_pelajaran):
            mata_pelajaran = input(f"Masukkan nama mata pelajaran yang ingin diubah (atau tekan 'skip' untuk melewati): ")
            if mata_pelajaran.lower() == 'skip':
                continue
            nilai = float(input(f"Masukkan nilai baru untuk {mata_pelajaran}: "))
            daftar_mahasiswa[nama][mata_pelajaran] = nilai  # Ubah nilai mata pelajaran
        print(f"Data untuk {nama} telah diperbarui menjadi: {daftar_mahasiswa[nama]}")
    else:
        print(f"{nama} tidak ditemukan dalam data siswa.")

# Loop utama program
while True:
    print("\nMenu:")
    print("Tekan 1 untuk menambah siswa")
    print("Tekan 2 untuk menampilkan info siswa")
    print("Tekan 3 untuk menghapus siswa")
    print("Tekan 4 untuk mengubah data siswa")
    print("Tekan 5 untuk keluar")
    
    pilihan = int(input("Masukkan pilihan Anda: "))
    
    if pilihan == 1:
        tambah_siswa()  # Tambah siswa baru
    elif pilihan == 2:
        tampilkan_info_siswa()  # Tampilkan informasi siswa
    elif pilihan == 3:
        nama = input("Masukkan nama siswa yang ingin dihapus: ")
        hapus(nama) 
    elif pilihan == 4:
        nama = input("Masukkan nama siswa yang ingin diubah: ")
        ubah(nama)  # Ubah data siswa
    elif pilihan == 5:
        print("Terima kasih! Program selesai.")
        break  # Keluar dari loop dan program
    else:
        print("Pilihan tidak valid! Silakan coba lagi.")
```

#### Penjelasan :

1.  kita membuat sebuah dictionary kosong yang nantinya akan diinputkan data ketika program dijalankan.
```python
data_mahasiswa = {}
```
Dictionary daftar_mahasiswa: Di sini, kita membuat sebuah dictionary kosong yang akan digunakan untuk menyimpan data siswa. Di dalam dictionary ini, nama siswa akan menjadi kunci (key), dan nilai-nilai mereka (mata pelajaran dan nilai) akan disimpan dalam dictionary lain sebagai nilai (value).


2. Fungsi untuk Menambahkan Siswa
```python
def tambah_siswa():
    """Fungsi untuk menambahkan siswa baru ke dalam daftar_mahasiswa."""
    nama_siswa = input("Masukkan nama siswa: ")
    jumlah_mata_pelajaran = int(input("Masukkan jumlah mata pelajaran: "))

    nilai_siswa = {}  # Sebuah dictionary kosong untuk menyimpan pasangan mata pelajaran-nilai untuk siswa
```
Fungsi `tambah_siswa`: Fungsi ini bertanggung jawab untuk menambahkan siswa baru ke dalam `daftar_mahasiswa`.

Input Nama Siswa: Menggunakan `input()`, pengguna diminta untuk memasukkan nama siswa.

Input Jumlah Mata Pelajaran: Pengguna juga diminta untuk memasukkan jumlah mata pelajaran yang ingin dicatat. Nilai ini diubah menjadi integer.

  Input Mata Pelajaran dan Nilai
```python
    # Loop untuk input mata pelajaran dan nilai
    for i in range(jumlah_mata_pelajaran):
        mata_pelajaran = input(f"Masukkan nama mata pelajaran {i + 1}: ")
        nilai = float(input(f"Masukkan nilai {mata_pelajaran}: "))
        nilai_siswa[mata_pelajaran] = nilai  # Simpan pasangan mata pelajaran-nilai dalam dictionary nilai_siswa
```
Loop untuk Input: Menggunakan for untuk mengulang sebanyak jumlah mata pelajaran yang dimasukkan.

Input Mata Pelajaran: Dalam setiap iterasi, pengguna diminta untuk memasukkan nama mata pelajaran.

Input Nilai: Setelah itu, pengguna diminta untuk memasukkan nilai untuk mata pelajaran tersebut. Nilai ini diubah menjadi float untuk mengakomodasi nilai desimal.

Simpan Nilai: Setiap pasangan mata pelajaran dan nilai disimpan dalam dictionary nilai_siswa.

Menyimpan Data Siswa
```python
    daftar_mahasiswa[nama_siswa] = nilai_siswa  # Simpan nilai siswa dalam dictionary daftar_mahasiswa
    print(f"{nama_siswa} telah ditambahkan dengan nilai: {nilai_siswa}")
```
Simpan Data: Setelah semua mata pelajaran dan nilai dimasukkan, dictionary nilai_siswa disimpan dalam daftar_mahasiswa dengan nama_siswa sebagai kunci.

Pesan Konfirmasi: Mencetak pesan yang mengonfirmasi bahwa siswa telah ditambahkan beserta nilai-nilai mereka.


3. Fungsi untuk Menghitung Rata-rata Nilai
```python
def hitung_rata_rata(nama_siswa):
    """Fungsi untuk menghitung rata-rata nilai siswa."""
    nilai_siswa = daftar_mahasiswa.get(nama_siswa)  # Mengambil dictionary mata pelajaran-nilai untuk nama siswa yang diberikan

    if nilai_siswa:
        total = sum(nilai_siswa.values())  # Hitung total nilai
        jumlah_mata_pelajaran = len(nilai_siswa)  # Hitung jumlah mata pelajaran
        rata_rata = total / jumlah_mata_pelajaran  # Hitung rata-rata

        return rata_rata
    else:
        return None
```
Fungsi hitung_rata_rata: Fungsi ini digunakan untuk menghitung rata-rata nilai siswa berdasarkan nama yang diberikan.

Ambil Data Siswa: Menggunakan get() untuk mengambil nilai siswa dari daftar_mahasiswa. Jika nama tidak ditemukan, nilai_siswa akan menjadi None.

Hitung Total dan Rata-rata:
Jika nilai_siswa tidak None, program menghitung total nilai dengan sum() yang menjumlahkan semua nilai dalam dictionary.
Menghitung jumlah mata pelajaran dengan len().
Menghitung rata-rata dengan membagi total nilai dengan jumlah mata pelajaran.
Return: Mengembalikan nilai rata-rata. Jika siswa tidak ditemukan, mengembalikan None.


4. Fungsi untuk Menampilkan Informasi Siswa
```python
def tampilkan_info_siswa():
    """F ungsi untuk menampilkan informasi nilai siswa dan rata-ratanya."""
    nama_siswa = input("Masukkan nama siswa untuk menampilkan info: ")
    nilai_siswa = daftar_mahasiswa.get(nama_siswa)  # Ambil data siswa

    if nilai_siswa:
        print(f"Nilai untuk {nama_siswa}:")
        for mata_pelajaran, nilai in nilai_siswa.items():
            print(f"{mata_pelajaran}: {nilai}")

        rata_rata = hitung_rata_rata(nama_siswa)  # Hitung rata-rata nilai siswa
        print(f"Nilai rata-rata: {rata_rata}")

    else:
        print(f"{nama_siswa} tidak ditemukan!!")
```
Fungsi tampilkan_info_siswa: Fungsi ini digunakan untuk menampilkan informasi nilai siswa dan rata-ratanya.

Input Nama Siswa: Pengguna diminta untuk memasukkan nama siswa yang informasinya ingin ditampilkan.

Ambil Data Siswa: Menggunakan get() untuk mengambil nilai siswa dari daftar_mahasiswa.

Tampilkan Nilai: Jika siswa ditemukan, program mencetak semua mata pelajaran dan nilai yang terkait.

Hitung Rata-rata: Memanggil fungsi hitung_rata_rata untuk menghitung dan menampilkan rata-rata nilai siswa.

Pesan Tidak Ditemukan: Jika siswa tidak ditemukan, program mencetak pesan yang sesuai.


5. Fungsi untuk Menghapus Data Siswa
```python
    """Fungsi untuk menghapus data siswa berdasarkan nama."""
    if nama in daftar_mahasiswa:
        del daftar_mahasiswa[nama]  # Hapus data siswa
        print(f"Data untuk {nama} telah dihapus.")
    else:
        print(f"{nama} tidak ditemukan dalam data siswa.")
```
Fungsi hapus: Fungsi ini digunakan untuk menghapus data siswa berdasarkan nama.

Cek Keberadaan Siswa: Memeriksa apakah nama siswa ada dalam daftar_mahasiswa.

Hapus Data: Jika ada, data siswa dihapus menggunakan del.

Pesan Konfirmasi: Mencetak pesan yang mengonfirmasi penghapusan atau memberi tahu jika siswa tidak ditemukan.

6. Fungsi untuk Mengubah Data Siswa
```python
def ubah(nama):
    """Fungsi untuk mengubah nilai mata pelajaran siswa yang sudah ada."""
    if nama in daftar_mahasiswa:
        print(f"Data saat ini untuk {nama}: {daftar_mahasiswa[nama]}")
        jumlah_mata_pelajaran = int(input("Masukkan jumlah mata pelajaran yang ingin diubah: "))
        
        # Loop untuk mengubah nilai
        for i in range(jumlah_mata_pelajaran):
            mata_pelajaran = input(f"Masukkan nama mata pelajaran yang ingin diubah (atau tekan 'skip' untuk melewati): ")
            if mata_pelajaran.lower() == 'skip':
                continue
            nilai = float(input(f"Masukkan nilai baru untuk {mata_pelajaran}: "))
            daftar_mahasiswa[nama][mata_pelajaran] = nilai  # Ubah nilai mata pelajaran
        print(f"Data untuk {nama} telah diperbarui menjadi: {daftar_mahasiswa[nama]}")
    else:
        print(f"{nama} tidak ditemukan dalam data siswa.")
```
Fungsi ubah: Fungsi ini digunakan untuk mengubah nilai mata pelajaran siswa yang sudah ada.

Cek Keberadaan Siswa: Memeriksa apakah nama siswa ada dalam daftar_mahasiswa.

Tampilkan Data Saat Ini: Jika ada, program menampilkan data saat ini untuk siswa tersebut.

Input Jumlah Perubahan: Meminta pengguna untuk memasukkan jumlah mata pelajaran yang ingin diubah.

Loop untuk Mengubah Nilai: Menggunakan loop untuk meminta nama mata pelajaran yang ingin diubah dan nilai baru. Jika pengguna mengetik 'skip', program akan melewati iterasi tersebut.

Update Data: Nilai baru disimpan dalam dictionary daftar_mahasiswa.

Pesan Konfirmasi: Mencetak pesan yang mengonfirmasi bahwa data telah diperbarui.

7. Loop Utama Program
```python
# Loop utama program
while True:
    print("\nMenu:")
    print("Tekan 1 untuk menambah siswa")
    print("Tekan 2 untuk menampilkan info siswa")
    print("Tekan 3 untuk menghapus siswa")
    print("Tekan 4 untuk mengubah data siswa")
    print("Tekan 5 untuk keluar")
    
    pilihan = int(input("Mas ukkan pilihan Anda: "))
    
    if pilihan == 1:
        tambah_siswa()  # Tambah siswa baru
    elif pilihan == 2:
        tampilkan_info_siswa()  # Tampilkan informasi siswa
    elif pilihan == 3:
        nama = input("Masukkan nama siswa yang ingin dihapus: ")
        hapus(nama) 
    elif pilihan == 4:
        nama = input("Masukkan nama siswa yang ingin diubah: ")
        ubah(nama)  # Ubah data siswa
    elif pilihan == 5:
        print("Terima kasih! Program selesai.")
        break  # Keluar dari loop dan program
    else:
        print("Pilihan tidak valid! Silakan coba lagi.")
```
Loop Utama: Program berjalan dalam loop tak terbatas (while True), yang memungkinkan pengguna untuk terus melakukan interaksi hingga mereka memilih untuk keluar.

Menu Utama: Program menampilkan menu dengan pilihan untuk menambah, menampilkan, menghapus, mengubah data siswa, atau keluar dari program.

Input Pilihan: Pengguna diminta untuk memasukkan pilihan mereka.

Eksekusi Berdasarkan Pilihan: Menggunakan if-elif untuk memanggil fungsi yang sesuai berdasarkan pilihan pengguna.

Keluar dari Program: Jika pengguna memilih untuk keluar (pilihan 5), program mencetak pesan terima kasih dan menghentikan loop dengan break.

Pesan Pilihan Tidak Valid: Jika pengguna memasukkan pilihan yang tidak valid, program mencetak pesan yang sesuai dan meminta pengguna untuk mencoba lagi.

### Tampilan Program Saat Dijalankan

##### menu
![menu](https://github.com/user-attachments/assets/72b59e19-bc21-407c-98b9-74747c71707e)


##### pilihan 1 Tambah Data +  pilihan 2 menampilkan info siswa
![tambah data1](https://github.com/user-attachments/assets/062d97cb-8397-4c48-8f5f-9f0a6eb30ceb)
![menampilkan pilihan 2](https://github.com/user-attachments/assets/9fc03539-4338-4938-a78d-109b01b7c469)


##### pilihan 4 Ubah Data + pilihan 2 menampilkan info siswa
![ubah data4](https://github.com/user-attachments/assets/9976f85a-eb45-4966-9600-e5c7b4c28334)
![menampilkan pilihan 2](https://github.com/user-attachments/assets/ef0b0194-d25d-415e-9540-106e6f07e0d9)



##### pilihan 3 Hapus Data 
![hapus data](https://github.com/user-attachments/assets/7df31a47-532d-4f56-86ce-0867bd5637b1)



##### pilihan 5 Keluar
![keluar](https://github.com/user-attachments/assets/da1009b1-853a-4d09-83cb-ff08182e8625)





