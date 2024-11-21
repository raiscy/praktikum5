# praktikum5

# Tugas Praktikum 05

Buat program sederhana yang akan menampilkan daftar nilai mahasiswa, dengan ketentuan : 
1. Program dibuat dengan menggunakan Dictionary
2. Tampilkan menu pilihan: (Tambah Data, Ubah Data, Hapus Data, Tampilkan Data, Cari Data)
3. Nilai Akhir diambil dari perhitungan 3 komponen nilai (tugas: 30%, uts: 35%, uas: 35%)
4. Buat flowchart dan penjelasan programnya

        # Program Pengelolaan Data Nilai Mahasiswa
        data_mahasiswa = []

        def lihat_data():
            print("\nDaftar Nilai")
            print("="*50)
            print("| NO |   NIM   |    NAMA    | TUGAS | UTS | UAS | AKHIR |")
            print("="*50)
            if len(data_mahasiswa) == 0:
                print("|                     TIDAK ADA DATA                     |")
            else:
                for i, data in enumerate(data_mahasiswa):
                    akhir = (data['Tugas'] * 0.3) + (data['UTS'] * 0.35) + (data['UAS'] * 0.35)
                    print(f"| {i+1:2} | {data['NIM']:7} | {data['Nama']:10} | {data['Tugas']:5} | {data['UTS']:3} | {data['UAS']:3} | {akhir:.2f} |")
          print("="*50)

        def tambah_data():
            print("\nTambah Data")
            nim = input("NIM: ")
            nama = input("Nama: ")
            tugas = int(input("Nilai Tugas: "))
            uts = int(input("Nilai UTS: "))
            uas = int(input("Nilai UAS: "))
            data_mahasiswa.append({
                  'NIM': nim,
                  'Nama': nama,
                  'Tugas': tugas,
                  'UTS': uts,
                  'UAS': uas
            })
            print("Data berhasil ditambahkan!")

        def ubah_data():
            lihat_data()
            index = int(input("Masukkan nomor data yang ingin diubah: ")) - 1
            if 0 <= index < len(data_mahasiswa):
                  print("\nData baru:")
                  nim = input("NIM: ")
                  nama = input("Nama: ")
                  tugas = int(input("Nilai Tugas: "))
                  uts = int(input("Nilai UTS: "))
                  uas = int(input("Nilai UAS: "))
                  data_mahasiswa[index] = {
                      'NIM': nim,
                      'Nama': nama,
                      'Tugas': tugas,
                      'UTS': uts,
                      'UAS': uas
                  }
                  print("Data berhasil diubah!")
          else:
              print("Data tidak ditemukan!")

        def hapus_data():
            lihat_data()
            index = int(input("Masukkan nomor data yang ingin dihapus: ")) - 1
            if 0 <= index < len(data_mahasiswa):
                data_mahasiswa.pop(index)
                print("Data berhasil dihapus!")
            else:
                print("Data tidak ditemukan!")

        def cari_data():
            nim = input("Masukkan NIM yang dicari: ")
            print("\nHasil Pencarian")
            print("="*50)
            print("| NO |   NIM   |    NAMA    | TUGAS | UTS | UAS | AKHIR |")
            print("="*50)
            found = False
            for i, data in enumerate(data_mahasiswa):
                if data['NIM'] == nim:
                    akhir = (data['Tugas'] * 0.3) + (data['UTS'] * 0.35) + (data['UAS'] * 0.35)
                    print(f"| {i+1:2} | {data['NIM']:7} | {data['Nama']:10} | {data['Tugas']:5} | {data['UTS']:3} | {data['UAS']:3} | {akhir:.2f} |")
                    found = True
            if not found:
                print("|                     DATA TIDAK DITEMUKAN              |")
            print("="*50)

        while True:
            print("\n[(L)ihat, (T)ambah, (U)bah, (H)apus, (C)ari, (K)eluar]")
            pilihan = input("Pilih menu: ").lower()

            if pilihan == 'l':
                lihat_data()
            elif pilihan == 't':
                tambah_data()
            elif pilihan == 'u':
                ubah_data()
            elif pilihan == 'h':
                hapus_data()
           elif pilihan == 'c':
                cari_data()
            elif pilihan == 'k':
                print("Keluar dari program.")
                break
            else:
                print("Pilihan tidak valid!")

PROSES INPUT DATA 
![Screenshot 2024-11-21 105418](https://github.com/user-attachments/assets/c3ae89b5-30d7-412e-b0c4-53d86449576b)
![Screenshot 2024-11-21 105537](https://github.com/user-attachments/assets/0e0744e3-a454-41fd-80b3-4bb3658b4aea)
![Screenshot 2024-11-21 105612](https://github.com/user-attachments/assets/ed59021a-c55a-4d86-8aa9-5a712ebb8bef)
![Screenshot 2024-11-21 105827](https://github.com/user-attachments/assets/1cc00937-57e8-41f6-a055-acd4819498a1)

HASIL OUTPUT 
![hasil tugas praktikum](https://github.com/user-attachments/assets/1a4553d0-767c-412f-9421-0e898ea9e726)

PENJELASAN : 

1. Fungsi lihat_data():
        Menampilkan daftar nilai mahasiswa dalam format tabel.
        Jika tidak ada data, menampilkan pesan bahwa tidak ada data.
        Menghitung nilai akhir berdasarkan bobot: 30% untuk tugas, 35% untuk UTS, dan 35% untuk UAS.
        Menggunakan enumerate untuk menampilkan nomor urut mahasiswa.

2. Fungsi tambah_data():
        Meminta input dari pengguna untuk menambahkan data mahasiswa baru.
        Data yang dimasukkan (NIM, nama, nilai tugas, UTS, dan UAS) disimpan dalam dictionary dan ditambahkan ke list data_mahasiswa.
        Menampilkan pesan konfirmasi bahwa data berhasil ditambahkan.

3. Fungsi ubah_data():
        Menampilkan data yang ada dengan memanggil lihat_data().
        Meminta pengguna untuk memasukkan nomor data yang ingin diubah.
        Jika nomor valid, pengguna diminta untuk memasukkan data baru, yang kemudian menggantikan data lama di list.
        Menampilkan pesan konfirmasi bahwa data berhasil diubah.

4. Fungsi hapus_data():
        Menampilkan data yang ada dengan memanggil lihat_data().
        Meminta pengguna untuk memasukkan nomor data yang ingin dihapus.
        Jika nomor valid, data dihapus dari list menggunakan pop().
        Menampilkan pesan konfirmasi bahwa data berhasil dihapus.

5. Fungsi cari_data():
        Meminta pengguna untuk memasukkan NIM yang ingin dicari.
        Mencari data mahasiswa berdasarkan NIM dan menampilkan hasilnya dalam format tabel.
        Jika tidak ditemukan, menampilkan pesan bahwa data tidak ditemukan.

FLOWCHART 



# LATIHAN 
1. Buat Dictionary daftar kontak ( Nama sebagai key, dan nomor sebagai value )
2. Tampilkan kontaknya Ari
3. Tambah kontak baru dengan nama Riko, nomor 087654544
4. Ubah kontak Dina dengan nomor baru 088999776
5. Tampilkan semua Nama
6. Tampilkan semua Nomor
7. Tampilkan daftar Nama dan nomornya
8. Hapus kontak Dina.

        # 1. Buat Dictionary daftar kontak
          daftar_kontak = {
              "Raifa": "08123456789",
              "Dokyeom": "08234567890",
              "Mingyu": "08345678901"
        }

        # 2. Tampilkan kontaknya Ari
          print("Kontak Raifa:", daftar_kontak.get("Raifa"))

        # 3. Tambah kontak baru dengan nama Riko, nomor 087654544
          daftar_kontak["Dokyeom"] = "087654544"
          print("Kontak Dokyeom telah ditambahkan.")

        # 4. Ubah kontak Dina dengan nomor baru 088999776
        daftar_kontak["Mingyu"] = "088999776"
        print("Kontak Mingyu telah diubah.")

        # 5. Tampilkan semua Nama
        print("Semua Nama:", list(daftar_kontak.keys()))

        # 6. Tampilkan semua Nomor
        print("Semua Nomor:", list(daftar_kontak.values()))

        # 7. Tampilkan daftar Nama dan nomornya
        print("Daftar Nama dan Nomornya:")
        for nama, nomor in daftar_kontak.items():
        print(f"{nama}: {nomor}")

        # 8. Hapus kontak Dina
        if "Mingyu" in daftar_kontak:
        del daftar_kontak["Mingyu"]
        print("Kontak Mingyu telah dihapus.")
            else:
            print("Kontak Mingyu tidak ditemukan.")

PROSES INPUT DATA 
![Screenshot 2024-11-21 112657](https://github.com/user-attachments/assets/4a9ee501-2c00-4b60-86fc-d5b2aae90bc6)
![Screenshot 2024-11-21 113152](https://github.com/user-attachments/assets/5d4adfd8-d469-4713-a699-e3b045a3e4ec)

HASIL OUTPUT 
![hasil latihan 1](https://github.com/user-attachments/assets/3931d0a8-8ea7-4c09-865a-5abcbb2c3f34)

PENJELASAN : 
1. Membuat Dictionary Daftar Kontak ( Di sini, sebuah dictionary bernama daftar_kontak dibuat. Kunci (key) dari dictionary ini adalah nama-nama kontak (Raifa, Dokyeom, Mingyu), dan nilainya (value) adalah nomor telepon yang sesuai. )
2. Menampilkan Kontak Raifa ( Menggunakan metode get(), kode ini menampilkan nomor telepon yang terdaftar untuk kontak "Raifa". Jika "Raifa" tidak ada dalam dictionary, get() akan mengembalikan None tanpa menghasilkan error. )
3. Menambahkan Kontak Baru ( Di sini, kontak baru dengan nama "Dokyeom" dan nomor "087654544" ditambahkan ke dalam dictionary. Jika nama tersebut sudah ada, nilainya akan diperbarui. )
4. Mengubah Kontak Mingyu ( Kontak "Mingyu" diubah dengan nomor baru "088999776". Jika "Mingyu" tidak ada, maka kontak baru akan ditambahkan. )
5. Menampilkan Semua Nama (digunakan untuk mendapatkan semua kunci (nama) dari dictionary, yang kemudian diubah menjadi list untuk ditampilkan)
6. Menampilkan Semua Nomor (digunakan untuk mendapatkan semua nilai (nomor telepon) dari dictionary, yang juga diubah menjadi list untuk ditampilkan.)
7. Menampilkan Daftar Nama dan Nomornya (digunakan untuk mendapatkan pasangan kunci-nilai dari dictionary. Dalam loop, setiap nama dan nomor ditampilkan dalam format yang rapi.)
8. Menghapus Kontak Mingyu







