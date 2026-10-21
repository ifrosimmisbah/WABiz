# WABiz — WhatsApp Business Management & AI Assistant

## Informasi Proyek

**Mata Kuliah:** Analisis & Pengujian Sistem  
**Nama Proyek:** WABiz  
**Platform:** Mobile Application  

## Deskripsi Proyek

WABiz merupakan aplikasi mobile yang dirancang untuk membantu lembaga pendidikan atau organisasi dalam mengelola komunikasi dengan client melalui WhatsApp secara terpusat dan terstruktur.

Sistem ini menyediakan fitur pengelolaan nomor WhatsApp, data client, campaign pesan, percakapan, customer service (CS), serta AI Assistant.

AI Assistant menggunakan informasi resmi yang diberikan oleh admin sebagai sumber informasi dalam membantu menjawab pertanyaan client. AI juga dapat membantu mengidentifikasi kebutuhan client dan mengarahkan percakapan kepada CS atau divisi yang sesuai.

## Fitur Utama

- Login Admin dan Customer Service
- Sinkronisasi nomor WhatsApp menggunakan QR
- Pengelolaan data client
- Pembuatan campaign pesan
- Pengiriman campaign secara langsung
- Penjadwalan campaign
- AI Assistant untuk menjawab pertanyaan client
- Pengelolaan informasi resmi lembaga
- Informasi pendaftaran dan link pendaftaran
- Penyimpanan riwayat percakapan
- Routing percakapan kepada CS atau divisi
- Pengelolaan CS berdasarkan divisi
- Dashboard aktivitas sistem

## Desain Proyek (UML)

Perancangan sistem menggunakan Unified Modeling Language (UML), yang meliputi:

- Use Case Diagram
- Activity Diagram
- Sequence Diagram
- Class Diagram
- Entity Relationship Diagram (ERD)

## Arsitektur Proyek

Arsitektur WABiz menggunakan pendekatan mobile application yang terintegrasi dengan backend, database, AI Service, dan WhatsApp Service.

Secara umum:

```text
React Native + Expo
        |
        v
     Supabase
        |
   +----+----+
   |         |
   v         v
AI Service   WhatsApp Service
