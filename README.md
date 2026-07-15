# 📊 Analisis Data E-Commerce Indonesia (Excel, SQL, & Machine Learning)

Halo! Saya sedang dalam perjalanan belajar menjadi seorang **Data Analyst**. Ini adalah proyek pertama saya di mana saya memproses dataset penjualan e-commerce nyata di Indonesia menggunakan 3 *tools* sekaligus: **Excel**, **SQL**, dan **Python (Machine Learning)**.

Melalui proyek ini, saya belajar bagaimana mencari masalah bisnis, membersihkan data yang kotor, hingga mengelompokkan pasar menggunakan kecerdasan buatan.

---

## 🛠️ Tools & Skill yang Saya Gunakan:
*   **Excel:** Eksplorasi Data awal, Pivot Table, & Pivot Chart.
*   **SQL (DuckDB di Google Colab):** Pembersihan data (*Data Cleaning*) dan agregasi.
*   **Python (Google Colab):** Standardisasi data (`StandardScaler`), Pemodelan AI (`K-Means Clustering`), dan Visualisasi (`Matplotlib` & `Seaborn`).

---

## 📈 Tahap 1: Analisis Pembatalan Transaksi (Excel)
Menggunakan **Pivot Table**, saya menyaring transaksi yang gagal/dibatalkan untuk mencari tahu apa penyebab utamanya:
*   **Temuan:** Mayoritas pembatalan terjadi karena pembeli **berubah pikiran** atau ingin **mengubah pesanan/alamat mereka**. 
*   **Insight:** Pembeli sering terburu-buru melakukan *checkout*. Fitur konfirmasi ulang sebelum bayar sangat dibutuhkan oleh aplikasi ini.

---

## 🧹 Tahap 2: Merapikan Data Metode Pembayaran (SQL)
Saat menganalisis metode pembayaran, saya menemukan banyak data kotor (misalnya penulisan `COD`, `COD (Bayar di Tempat)`, dan `Cash On Delivery` terpisah-pisah, padahal artinya sama).

Saya menulis query SQL menggunakan perintah **`CASE WHEN`** untuk merapikannya secara otomatis:
```sql
SELECT 
    CASE 
        WHEN "Metode Pembayaran" IN ('COD (Bayar di Tempat)', 'COD', 'Cash On Delivery') THEN 'COD'
        WHEN "Metode Pembayaran" IN ('Saldo ShopeePay', 'saldo shopeepay', 'ShopeePay') THEN 'ShopeePay'
        -- dst...
    END AS Metode_Pembayaran_Bersih,
    COUNT(order_id) AS Jumlah_Transaksi
FROM 'indonesia_ecommerce_sales_challenging.csv'
GROUP BY Metode_Pembayaran_Bersih;

---

---

## 🤖 Tahap 3: Segmentasi Pasar Daerah (Python - Machine Learning)
Terakhir, saya menggunakan model AI sederhana bernama **K-Means Clustering** untuk mengelompokkan kota-kota di Indonesia berdasarkan keaktifan belanjanya. 

AI berhasil membagi kota-kota tersebut menjadi 3 kelompok (*Cluster*):
1.  **Cluster Merah (Pasar Pemula):** Transaksi masih sedikit dan perputaran uang kecil.
2.  **Cluster Biru (Pasar Potensial):** Transaksi sedang dan stabil.
3.  **Cluster Hijau (Pasar Raksasa):** Wilayah penyumbang uang terbesar (di atas 600 transaksi). 5 kota teratas di cluster ini adalah: **Kab. Tangerang, Kab. Bogor, Kota Tangerang, Kota Jakarta Barat,** dan **Kota Tangerang Selatan**.

---

## 💡 Apa yang Saya Pelajari dari Proyek Ini?
Sebagai pemula, proyek ini membuka mata saya bahwa data di dunia nyata itu kotor dan berantakan. Tugas seorang Data Analyst bukan cuma membuat grafik yang bagus, tapi memastikan datanya bersih, mengolahnya dengan *logic* yang tepat, lalu menerjemahkannya menjadi rekomendasi yang berguna bagi bisnis.
