# WABiz — WhatsApp Business Management & AI Assistant

## Informasi Proyek

**Mata Kuliah:** Analisis & Pengujian Sistem  
**Nama Proyek:** WABiz  
**Platform:** Mobile Application  

---

## Deskripsi Proyek

WABiz merupakan aplikasi mobile yang dirancang untuk membantu lembaga pendidikan atau organisasi dalam mengelola komunikasi dengan client melalui WhatsApp secara terpusat dan terstruktur.

Sistem ini menyediakan fitur pengelolaan nomor WhatsApp, data client, campaign pesan, percakapan, customer service (CS), serta AI Assistant.

AI Assistant menggunakan informasi resmi yang diberikan oleh admin sebagai sumber informasi dalam membantu menjawab pertanyaan client. AI juga dapat membantu mengidentifikasi kebutuhan client dan mengarahkan percakapan kepada CS atau divisi yang sesuai.

---

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

---

# Desain Proyek (UML)

Perancangan sistem WABiz menggunakan Unified Modeling Language (UML) untuk menggambarkan kebutuhan, aktivitas, dan interaksi dalam sistem.

Diagram yang digunakan meliputi:

- Use Case Diagram
- Activity Diagram
- Sequence Diagram

---

## 1. Use Case Diagram

Use Case Diagram menggambarkan hubungan antara aktor dengan fungsi-fungsi yang tersedia pada sistem WABiz.

### Use Case Diagram WABiz

![Use Case Diagram](docs/images/use-case.png)

**Aktor utama:**

- Admin
- Customer Service (CS)
- Client
- WhatsApp Service
- AI Service

---

## 2. Activity Diagram

Activity Diagram menggambarkan alur aktivitas yang terjadi dalam sistem WABiz, mulai dari client mengirim pesan hingga pesan diproses oleh sistem dan diteruskan kepada AI atau CS sesuai kebutuhan.

### Activity Diagram WABiz

![Activity Diagram](docs/images/activity.png)

---

## 3. Sequence Diagram

Sequence Diagram menggambarkan urutan interaksi antara Client, WhatsApp Service, sistem WABiz, AI Service, dan Customer Service dalam menangani percakapan.

### Sequence Diagram WABiz

![Sequence Diagram](docs/images/sequence.png)

---

# Arsitektur Proyek

Arsitektur WABiz menggunakan pendekatan mobile application yang terintegrasi dengan backend, database, AI Service, dan WhatsApp Service.

Secara umum arsitektur sistem:

```text
+-----------------------------+
|     React Native + Expo     |
|          Mobile App         |
+-------------+---------------+
              |
              v
+-----------------------------+
|          Supabase           |
|                             |
|  - Authentication           |
|  - PostgreSQL Database      |
|  - Storage                  |
|  - Realtime                 |
|  - Edge Functions           |
+-------------+---------------+
              |
        +-----+-----+
        |           |
        v           v
+-------------+ +------------------+
| AI Service  | | WhatsApp Service |
+-------------+ +------------------+
