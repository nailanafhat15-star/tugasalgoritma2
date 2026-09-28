# Tugas Algoritma Pertemuan 2
**Nama:** Ainun Naila Nafhat  
**Nim:** 1251170013  
**Kelas:** 3B  
**Mata Kuliah:** Algoritma dan  Struktur Data  
**Materi:** Struktur Kontrol & Representasi Pseudocode    
**Studi Kasus:** Sistem Transaksi & Validasi Toko Buku Modern  

--
# Analisis Komponen 
**Variabel & Tipe Data**
*  'is_member: Boolean (untuk menyimpan status keanggotaan pelanggan)
*  'jumlah_buku: Integer (untuk menyimpan jumlah fisik buku yang dibeli)
*  'total_awal: Real (untuk menyimpan total nominal belanja sebelum diskon)
*  'persentase_diskon: Real (untuk menyimpan persentase diskon yang berlaku)
*  'nominal_diskon: Real (untuk menyimpan hasil hitungan potongan harga)
*  'total_bayar: Real (untuk menyimpan total akhir yang dibayar)

**Identifikasi Struktur Kontrol**
*  **Sequence:** Digunakan untuk bagian - bagian yang dijalankan secara berurutan dari atas ke bawah tanpa syarat, pada input status keanggotaan, perhitungan diskon dan tottal biaya serta hasil akhir.
*  **Percabanga:** Digunakan dalam bentuk IF ELSE, penentuan besaran diskon bergantunga pada dua tahap pengecekan. Tahap pertama membedakan pelanggan berdasarkan status keanggotaan, yaitu member atau non-member, tahap kedua mengecek syarat tambahan diskon.
*  **Perulangan:** Digunakan pada tahap validasi input di awal dalam bentuk reppeat dan until. Perulangan akan terus berjalan selama total belanja bernilai negatif atau jumlah buku kurang dari satu, dan baru berhenti setelah kedua syarat tersebut terpenuhi secara bersamaan.

## B Penyusunan Pseudocode
Program Transaksi_TokoBuku

* **Deklarasi**   
  is_member: Boolean  
  jumlah_buku: Integer  
  total_awal: Real  
  persentase_diskon: Real  
  nominal_diskon: Real  
  total_bayar: Real  
  
* **Algoritma**  
    Input data awal    
INPUT (is_member)    
INPUT (jumlah_buku)  
INPUT (total_awal)  
    Validasi data yang di input
  IF (total_awal < 0) OR (jumlah_buku < 1) THEN      
OUTPUT("Input tidak valid, silakan masukkan ulang")      
    Ulangi jika tidak valid, lanjut jika valid      
UNTIL (total_awal >= 0) AND (jumlah_buku >= 1)     
    Input status keanggotaan  
INPUT(is_member)  
    Validasi pelanggan member       
  IF (is_member = True) THEN   
    Validasi syarat tambahan diskon untuk member      
  IF (total_awal >= 200000) AND (jumlah_buku >= 3) THEN   
     diskon 15%, persen_diskon &larr; 0.15 jika syarat terpenuhi     
ELSE  
     diskon 10%, persen_diskon &larr; 0.10 jika syarat tidak terpenuhi     
ENDIF     
ELSE  
     Validasi syarat tambahan diskon untuk non-member    
  IF (total_awal >=300000) THEN    
     diskon 5%, persen_diskon  0.05 jika syarat terpenuhi    
ELSE    
    tanpa diskon, persen_diskon &larr; 0.00 jika syarat tidak terpebuhi    
ENDIF  
    Hitung nominal diskon     
nominal_diskon &larr; total_awal * persen_diskon     
    Hitung total bayar akhir     
total_bayar &larr; total_awal - nominal_diskon    
    Tampilkan hasil     
OUTPUT(nominal_diskon)      
OUTPUT(total_bayar)  


## C Trace Table 
### Kasus A: Member, total_awal = 250.000, jumlah_buku = 4

| Baris | Aksi | total_awal | jumlah_buku | persen_diskon | nominal_diskon | total_bayar |
|---|---|---|---|---|---|---|
| 1 | input diterima:member, belanja 250.000, beli 4 buku | 250.000 | 4 | - | - | - |  
| 2 | Validasi: data valid (bukan minus, bukan <1 buku) &rarr; lanjut | 250.000 | 4 | - | - | - |
| 3 | Validasi diskon: member & syarat tambahan (≥200rb & ≥3 buku) terpenuhi &rarr; diskon | 250.000 | 4 | 0.15 | - | - |
| 4 | Hitung nominal diskon = 250.000 * 0.15 | 250.000 | 4 | 0.15 | 37.500 | - |
| 5 | Hitung hasil akhir | 250.000 | 4 | 0.15 | 37.500 | 212.500 |  

### Kasus B: non - member, total_awal = 350.000

| Baris | Aksi | total_awal | jumlah_buku | persen_diskon | nominal_diskon | total_bayar |
|---|---|---|---|---|---|---|
| 1 | Input diterima: non-member, belanja 350.000, beli 2 buku | 350.000 | 2 | - | - | - |
| 2 | Validasi: data valid  &rarr; lanjut | 350.000 | 2 | - | - | - |
| 3 | Validasi diskon: non-member & belanja ≥300.000 &rarr; diskon 5% | 350.000 | 2 | 0.05 | - | - |
| 4 | Hitung nominal diskon = 350.000 * 0.05 | 350.000 | 2 | 0.05 | 17.500 | - |
| 5 | Hitung hasil akhir | 350.000 | 2 | 0.05 | 17.500 | 332.500 |

### Kasus C: non-member, jumlah_buku = 1, total_awal = -50.000, dikoreksi -> 100.000  

| Baris | Aksi | total_awal | jumlah_buku | persen_diskon | nominal_diskon | total_bayar |
|---|---|---|---|---|---|---|
| 1 | Input awal (percobaan 1): belanja -50.000 | -50.000 | 1 | - | - | - |
| 2 | Validasi gagal (belanja < 0) &rarr; tampil error, minta input ulang | 100.000 | 1 | - | - | - |
| 3 | Validasi ulang berhasil &rarr; lanjut ke pengecekan diskon | 100.000 | 1 | - | - | - |
| 4 | Validasi diskon: non-member & belanja <300.000 &rarr; diskon 0% | 100.000 | 1 | 0.0 | 0 | - |
| 5 | Hitung hasil akhir | 100.000 | 1 | 0.0 | 0 | 100.000 |


 Ringkasan Hasil

| Kasus | Persen Diskon | Nominal Diskon | Total Bayar |
|---|---|---|---|
| A (member) | 15% | Rp 37.500 | Rp 212.500 |
| B (non-member) | 5% | Rp 17.500 | Rp 332.500 |
| C (non-member, input dikoreksi) | 0% | Rp 0 | Rp 100.000 |



