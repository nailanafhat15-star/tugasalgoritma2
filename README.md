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

---
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
1. Input data awal  
   INPUT (is_member)  
   INPUT (jumlah_buku)  
   INPUT (total_awal)  
2. Validasi data yang di input    
   IF (total_awal < 0) OR (jumlah_buku < 1) THEN   
   OUTPUT("Input tidak valid, silakan masukkan ulang")   
3. Ulangi jika tidak valid, lanjut jika valid   
   UNTIL (total_awal >= 0) AND (jumlah_buku >= 1)   
4. Input status keanggotaan
   INPUT(is_member)
5. Validasi pelanggan member    
   IF (is_member = True) THEN  
6. Validasi syarat tambahan diskon untuk member   
   IF (total_awal >= 200000) AND (jumlah_buku >= 3) THEN  
   diskon 15%, persen_diskon &larr; 0.15 jika syarat terpenuhi    
ELSE  
  diskon 10%, persen_diskon &larr; 0.10 jika syarat tidak terpenuhi   
ENDIF   
  ELSE
7. Validasi syarat tambahan diskon untuk non-member  
   IF (total_awal >=300000) THEN  
   diskon 5%, persen_diskon  0.05 jika syarat terpenuhi  
ELSE  
   tanpa diskon, persen_diskon &larr; 0.00 jika syarat tidak terpebuhi  
ENDIF
8. Hitung nominal diskon   
   nominal_diskon &larr; total_awal * persen_diskon   
9. Hitung total bayar akhir    
   total_bayar &larr; total_awal - nominal_diskon  
10. Tampilkan hasil   
    OUTPUT(nominal_diskon)    
    OUTPUT(total_bayar)   

| 
