# Dataset Praktik Manufaktur ERPNext - ERP_Rega

Paket dataset dan panduan praktikum ini disiapkan untuk simulasi implementasi modul **Manufacturing (Manufaktur)** pada ERPNext dengan studi kasus **PT Rega Manufaktur Kreasi** (Industri Furnitur Kayu Minimalis).

---

## 📁 Daftar Berkas dalam Folder `ERP_Rega`

| No | Nama File | Tipe File | DocType ERPNext Terkait | Deskripsi Singkat |
|---|---|---|---|---|
| 01 | `01_item_group.csv` | CSV | Item Group | Master kelompok barang (Bahan Baku, Sub-Assembly, Barang Jadi) |
| 02 | `02_uom.csv` | CSV | UOM | Master satuan ukuran (Pcs, Set, Lembar, Box, Liter, Jam) |
| 03 | `03_warehouse.csv` | CSV | Warehouse | Struktur gudang (Gudang RM, Gudang WIP, Gudang FG, Gudang Scrap) |
| 04 | `04_workstation.csv` | CSV | Workstation | Master 4 stasiun kerja beserta tarif beban operasional per jam |
| 05 | `05_operation.csv` | CSV | Operation | Master aktivitas operasi: Potong, Rakit, Finishing, QC & Packing |
| 06 | `06_item.csv` | CSV | Item | Master data 8 bahan baku/pembantu dan 2 produk jadi |
| 07 | `07_bom.csv` | CSV | BOM | Header formula produksi untuk Meja Kerja dan Kursi Kerja |
| 08 | `08_bom_item.csv` | CSV | BOM Item | Rincian kebutuhan komponen/bahan baku per 1 unit barang jadi |
| 09 | `09_bom_operation.csv` | CSV | BOM Operation | Urutan workstation dan alokasi durasi kerja per operasi |
| 10 | `10_supplier.csv` | CSV | Supplier | Master vendor pemasok kayu pinus, besi hollow, cat, & kardus |
| 11 | `11_customer.csv` | CSV | Customer | Master data pelanggan korporat dan toko ritel furnitur |
| 12 | `12_opening_stock.csv` | CSV | Stock Entry | Data saldo awal fisik bahan baku di Gudang Bahan Baku |
| 13 | `13_sales_order_sample.csv` | CSV | Sales Order | Sampel data pesanan penjualan untuk memicu alur produksi |
| 14 | `Panduan_Praktik_Manufaktur_ERPNext.docx` | DOCX | Buku Panduan | Dokumen lengkap pedoman impor, siklus manufaktur, & latihan |

---

## 🚀 Alur Praktik Singkat

1. **Buka Dokumen Panduan**: Buka file `Panduan_Praktik_Manufaktur_ERPNext.docx` untuk membaca panduan lengkap.
2. **Impor Master Data**: Gunakan fitur **Data Import** di ERPNext sesuai urutan:
   - `01_item_group.csv` $\to$ `02_uom.csv` $\to$ `03_warehouse.csv`
   - `04_workstation.csv` $\to$ `05_operation.csv` $\to$ `10_supplier.csv` $\to$ `11_customer.csv`
   - `06_item.csv` $\to$ Buat `BOM` (mengacu `07_bom.csv`, `08_bom_item.csv`, `09_bom_operation.csv`)
3. **Input Saldo Awal**: Input saldo fisik dari `12_opening_stock.csv` melalui **Stock Entry (Material Receipt)**.
4. **Jalankan Siklus Manufaktur**:
   - Buat **Sales Order** (mengacu `13_sales_order_sample.csv`).
   - Buat **Production Plan** $\to$ Submit $\to$ Generate **Work Order**.
   - Klik **Start** pada Work Order $\to$ Submit **Material Transfer for Manufacture** (Gudang RM $\to$ Gudang WIP).
   - Eksekusi 4 **Job Card** pada masing-masing Workstation.
   - Klik **Finish** pada Work Order $\to$ Submit **Manufacture Stock Entry** (Gudang WIP $\to$ Gudang FG).
   - Buat **Delivery Note** & **Sales Invoice** untuk menyelesaikan pesanan pelanggan.
