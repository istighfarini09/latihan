# tugas-algoritma 2
**Nama:** istighfarini  
**NIM:** 1251170012  
**kelas:** 3B
 
### 1. Variabel dan tipe data  

| No | variabel | tipedata | keterangan |  
| --- | --- | --- | --- |
| 1 | is_member | Boolean | Status keanggotaan pelanggan(True/False) | 
| 2 | jumlah_buku | integer | jumlah buku yang di beli | 
| 3 | total_awal | real | total belanja sebelum diskon | 
| 4 | persen_diskon | real| persentase diskon yang berlaku | 
| 5 | nominal_diskon | real | nilai potongan dalam rupiah | 
| 6 | total_bayar | real | total yang harus di bayar setelah diskon | 

### 2. Struktur kontrol yang digunakan  
sekuensial: langkah-langkah yang dikerjakan secara berurutan dari atas ke bawah, yaitu memasukkan data status member, jumlah buku, total belanja, menghitung nominal diskon dan total bayar, lalu menampilkan hasilnya melalui output.  
percabangan: menentukan diskon sesuai aturan toko dalam bentuk IF-ELSE bertingkat, karena penentuan diskon bergantung pada dua tahap yaitu tahap pertama membedakan pelanggan yang member dan non member. tahap kedua mengecek syarat tambahan pada masing-masing jalur, yaitu kalau member, dapat diskon 10%. lalu dicek lagi, jika total belanja >= 200000 dan jumlah buku >= 3, diskonnya jadi 15%. jika bukan member, dicek apakah total belanjanya >= 300000. kalau iya diskonnya 5%, kalau kurang dari 300000 diskonnya 0% atau tidak ada diskon.  
perulangan: digunakan untuk validasi input. jika total belanjanya kurang dari 0 atau jumlah bukunya kurang dari 1, tampilkan pesan kesalahan dan meminta data dimasukkan ulang. diulang terus sampai datanya benar.perulangan terus berjalan selama total belanja bernilai negatif atau jumlah bukunya kurang dari satu, dan baru berhenti setelah kedua syarat terpenuhi secara bersamaan.  

 

--- 
## Pseudocode  
Program   
Hitung_total_bayar_toko_buku  

Deklarasi:  
is_member: Boolean  
jumlah_buku: integer  
total_awal: real  
persen_diskon: real  
nominal_diskon: real  
total_bayar: real  

Algoritma:  
INPUT(is_member)  
INPUT(total_awal, jumlah_buku)  

{Validation loop}  
WHILE (total_awal < 0) OR 
(jumlah_buku < 1) DO  
&emsp; OUTPUT (" input tidak valid,  
silakan masukkan ulang data")  
&emsp; INPUT (total_awal, jumlah_buku)  
ENDWHILE  

{Nested selection untuk menentukan persen diskon}  
IF (is_member = true) THEN  
&emsp; persen diskon &larr; 0.10  
&emsp; IF (total_awal >= 200000) AND  
(jumlah_buku >= 3) THEN  
&emsp; &emsp; persen_diskon &larr; 0.15  
&emsp; ENDIF  
ELSE  
&emsp; IF (total_awal >= 300000) THEN  
&emsp; &emsp; persen_diskon &larr; 0.05  
&emsp; ELSE  
&emsp; &emsp; persen_diskon &larr; 0.00  
&emsp; ENDIF  
ENDIF  

nominal_diskon &larr; total_awal * persen_diskon  
total_bayar &larr; total_awal - nominal_diskon  

OUTPUT(nominal_diskon)  
OUTPUT(total_bayar)  

--- 

## Uji logika/Trace table  

### kasus A: is_member = true, total_awal = 250000, jumlah_buku = 4  

| Langkah | aksi | total_awal | jumlah_buku | persen_diskon | nominal_diskon | total_bayar | 
| --- | --- | --- | --- | --- | --- | --- |
| 1 | input is_member | - | - | - | - | - | - | 
| 2 | input total_awal, jumlah_buku | true | 250000 | 4 | - | - | - | - | 
| 3 | cek WHILE: (250000<0) OR (4<1) | true | 250000 | 4 | false &rarr; loop tidak dijalankan | - | - | - | 
| 4 | cek IF is_number = true | true | 250000 | 4 | - | 0.10 | - | - | 
| 5 | cek IF (250000&ge;200000) AND (4&ge;3) | true | 250000 | 4 | - | 0.15 (true AND true | - | - | 
| 6 | nominal_diskon &larr; 250000*0.15 | true | 250000 | 4 | - | 0.15 | 37500 | - | 
| 7 | total_bayar &larr; 250000-37500 | true | 250000 | 4 | - | 0.15 | 37500 | 212500 | 
| 8 | output | - | - | - | - | - | **37500** | **212500** | 

### kasus B: is_member = false, total awal = 350000, jumlah buku = 2 

