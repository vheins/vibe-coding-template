# TEMPLATE DOKUMENTASI MODUL
 
 > Gunakan template ini sebagai standar dokumentasi untuk setiap modul sistem (Inti / Pendukung / Opsional).
 
 ---
 
 ## Header & Navigasi
 
 - [Kembali ke Ikhtisar Modul](#)
 - [Link ke Semua Modul](#)
 - [Link ke Skenario Pengujian](../../testing/<module-name>/overview.md)
 
 ---
 
 ## 1. Ikhtisar Modul (Module Overview)
 
 - **Deskripsi singkat modul:**
 - **Posisi modul dalam sistem:**
 - **Hubungan dengan domain bisnis utama:**
 
 ---
 
 ## 2. Tujuan & Nilai Bisnis (Purpose & Business Value)
 
 ### 2.1 Tanggung Jawab Utama
 - Fungsi inti modul
 - Peran modul dalam proses bisnis
 
 ### 2.2 Nilai Bisnis
 - **Kepatuhan (Compliance):**
 - **Pengurangan Risiko (Risk reduction):**
 - **Efisiensi Operasional (Operational efficiency):**
 - **Akurasi Data (Data accuracy):**
 - **Pemberdayaan Strategis (Strategic enablement):**
 
 ---
 
 ## 3. Lingkup (Scope)
 
 ### 3.1 Dalam Lingkup (In-Scope)
 - Fitur dan tanggung jawab yang ditangani modul
 
 ### 3.2 Di Luar Lingkup (Out-of-Scope)
 - Fitur yang tidak ditangani
 - Alasan
 - Modul pemilik sesungguhnya
 
 ---
 
 ## 4. Cerita Pengguna (User Stories)
 
 Daftar kebutuhan berbasis peran (role).
 
 | ID   | Peran (Role) | Tujuan (Goal) | Manfaat (Benefit) |
 | :--- | :----------- | :------------ | :---------------- |
 |      |              |               |                   |
 
 ---
 
 ## 5. Alur & Aturan Bisnis (Business Flow & Rules)
 
 ### 5.1 Alur Bisnis (Business Flow)
 - **Wajib:** Sertakan diagram alur menggunakan Mermaid (Sequence/Flowchart).
 - Siklus hidup proses
 
 ### 5.2 Aturan Bisnis & Kebutuhan Fungsional
 
 #### 5.2.1 Aturan Domain (Domain Rules)
 - Ketentuan bisnis
 - Validasi penting
 
 #### 5.2.2 Aturan Finansial / Operasional
 - Perhitungan
 - Tanggal efektif
 - Mata uang / unit
 
 ---
 
 ## 6. Model Data (Data Model)
 
 ### 6.1 Entity Relationship Diagram (ERD)
 - Diagram relasi entitas utama
 
 ### 6.2 Definisi Entitas (Opsional)
 - Field penting
 - Batasan (constraint) kritikal
 
 ---
 
 ## 7. Spesifikasi API (API Specification)
 
 > Detail spesifikasi API dipisahkan ke dalam dokumen tersendiri di folder `.agent/api/<module-name>/`.
 > Silakan rujuk ke file Spesifikasi API terkait.
 
 - [Link ke Spesifikasi API](../../api/<module-name>/api-<feature>.md)
 
 ---
 
 ## 8. Ketergantungan (Dependencies)
 
 ### 8.1 Modul yang Dibutuhkan (Required Modules)
 - **Ketergantungan Keras (Hard dependency):**
 - **Alasan:**
 
 ### 8.2 Modul Opsional
 - **Manfaat integrasi:**
 
 ### 8.3 Ketergantungan Data
 - **Masukan Data (Data inbound):**
 - **Entitas yang direferensikan:**
 
 ---
 
 ## 9. Titik Integrasi (Integration Points)
 
 ### 9.1 Integrasi Masuk (Inbound Integration)
 - **Modul Sumber:**
 - **Data:**
 - **Pola Integrasi:**
 
 ### 9.2 Integrasi Keluar (Outbound Integration)
 - **Modul Target:**
 - **Data yang diekspos:**
 
 ### 9.3 Event yang Diterbitkan (Published Events)
 - **Nama Event:**
 - **Pemicu (Trigger):**
 - **Payload:**
 - **Subscriber:**
 
 ---
 
 ## 10. Kepatuhan & Audit (Compliance & Audit)
 
 ### 10.1 Kepatuhan Regulasi
 - Regulasi relevan
 - Implementasi sistem
 
 ### 10.2 Retensi & Pengarsipan Data
 - Periode retensi
 - Aturan pengarsipan
 - Penghapusan / anonimisasi
 
 ### 10.3 Kebutuhan Jejak Audit (Audit Trail)
 - Field yang diaudit
 - Aktor
 - Waktu (Timestamp)
 - Rantai persetujuan (Approval chain)
 
 ---
 
 ## 11. Kepemilikan & Siklus Hidup Data
 
 ### 11.1 Kepemilikan Entitas
 - **Pemilik (Owner):**
 - **Izin Baca / Tulis:**
 
 ### 11.2 Status Siklus Hidup
 - **Daftar status:**
 - **Diagram transisi:**
 
 ### 11.3 Aturan Transisi Status
 - **Pemicu:**
 - **Validasi:**
 - **Efek samping:**
 
 ### 11.4 Izin Pembaruan Data
 - **Matriks Peran vs Field:**
 
 ---
 
 ## 12. Catatan Ekstensibilitas
 
 ### 12.1 Konfigurasi & Kustomisasi
 - Perluasan berbasis konfigurasi
 
 ### 12.2 Peningkatkan Masa Depan
 - Perbaikan yang direncanakan
 
 ### 12.3 Ekstensibilitas Integrasi
 - Webhooks
 - API Kustom
 
 ### 12.4 Lokalisasi & Dukungan Multi-Wilayah
 - Aturan spesifik negara
 - Bahasa
 
 ---
 
 ## 13. Invarian Wajib
 - Aturan yang tidak boleh dilanggar sama sekali
 
 ---
 
 ## 14. Kebutuhan UI/UX
 
 ### 14.1 Web / Admin
 - Komponen inti
 - Aturan UX
 
 ### 14.2 Mobile (jika berlaku)
 - Persetujuan (Approval)
 - Notifikasi
 
 ---
 
 ## 15. Tugas Implementasi (Implementation Tasks)
 
 **Aturan Ketat:** Setiap tugas backend yang melibatkan antarmuka pengguna harus memiliki tugas frontend yang sesuai.
 
 | ID Tugas | Platform | Status | Deskripsi |
 | :------- | :------- | :----- | :-------- |
 |          | Backend  |        |           |
 |          | Frontend |        |           |
 
 ---
 
 ## Lampiran (Opsional)
 
 - Daftar Istilah (Glossary)
 - Pertanyaan terbuka
 - Batasan yang diketahui
 - Referensi
