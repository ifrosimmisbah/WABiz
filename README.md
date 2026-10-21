
# Desain Proyek (UML)

Perancangan sistem WABiz menggunakan Unified Modeling Language (UML) untuk menggambarkan kebutuhan, aktivitas, dan interaksi antara aktor dengan sistem.

Diagram UML yang digunakan dalam perancangan WABiz meliputi:

- Use Case Diagram
- Activity Diagram
- Sequence Diagram

---

## 1. Use Case Diagram

Use Case Diagram menggambarkan interaksi antara aktor dengan fungsi-fungsi yang tersedia pada sistem WABiz.

### Use Case Diagram WABiz

![Use Case Diagram WABiz](docs/images/use-case.png)

**Aktor yang terlibat:**

- **Admin** — mengelola sistem, WhatsApp, client, campaign, AI Assistant, informasi lembaga, CS, dan percakapan.
- **Customer Service (CS)** — melihat dan menangani percakapan yang menjadi tanggung jawabnya.
- **Client** — mengirim pesan dan berinteraksi dengan sistem melalui WhatsApp.
- **AI** — menganalisis pesan, memberikan respons otomatis, dan membantu melakukan routing percakapan.

### Alur Use Case Diagram

```mermaid
flowchart LR
    Admin[Admin]
    CS[Customer Service]
    Client[Client]
    AI[AI Assistant]

    subgraph WABiz["Sistem WABiz"]
        A1([Login])
        A2([Kelola WhatsApp])
        A3([Kelola Client])
        A4([Kelola Campaign])
        A5([Jadwalkan Campaign])
        A6([Kelola AI Assistant])
        A7([Kelola Informasi Lembaga])
        A8([Kelola Anggota/CS])
        A9([Melihat Riwayat Percakapan])
        A10([Reset Riwayat])
        A11([Meneruskan Percakapan])
        A12([Mengirim Pesan])
        A13([Analisis Pesan])
        A14([Menjawab Pesan])
        A15([Routing ke CS])
    end

    Admin --- A1
    Admin --- A2
    Admin --- A3
    Admin --- A4
    Admin --- A5
    Admin --- A6
    Admin --- A7
    Admin --- A8
    Admin --- A9
    Admin --- A10
    Admin --- A11

    CS --- A1
    CS --- A9
    CS --- A11

    Client --- A12
    AI --- A13
    AI --- A14
    AI --- A15

    A13 -.->|include| A14
    A15 -.->|extend| A14
```

---

## 2. Activity Diagram

Activity Diagram menggambarkan alur proses penanganan pesan pada sistem WABiz.

### Activity Diagram WABiz

![Activity Diagram WABiz](docs/images/activity.png)

Alur utama dimulai ketika sistem menerima pesan dari client. Pesan kemudian disimpan dan dianalisis oleh AI Assistant. Sistem akan menentukan apakah pesan berkaitan dengan pendaftaran atau pertanyaan umum.

Jika pesan berkaitan dengan pendaftaran, sistem mengambil informasi dan link pendaftaran kemudian dapat meneruskan percakapan kepada CS Pendaftaran.

Jika pesan bukan mengenai pendaftaran, AI mengambil informasi dari knowledge lembaga dan menghasilkan respons untuk client.

### Alur Activity Diagram

```mermaid
flowchart TD
    A((Start)) --> B[Terima pesan]
    B --> C[Simpan pesan]
    C --> D[Analisis pesan oleh AI]
    D --> E{Apakah pertanyaan pendaftaran?}

    E -- Ya --> F[Ambil link pendaftaran]
    F --> G[Kirim link]
    G --> H[Forward ke CS]

    E -- Tidak --> I[Ambil knowledge lembaga]
    I --> J[Generate response]
    J --> K[Kirim response]

    H --> L[Simpan riwayat]
    K --> L
    L --> M((End))
```

---

## 3. Sequence Diagram

Sequence Diagram menggambarkan urutan interaksi antara Client, WhatsApp, WhatsApp Service, WABiz Backend, AI Assistant, Database, dan CS Pendaftaran pada proses pendaftaran.

### Sequence Diagram — Alur Pendaftaran

![Sequence Diagram WABiz](docs/images/sequence.png)

Pada alur ini, client mengirimkan pesan melalui WhatsApp. Pesan diteruskan oleh WhatsApp Service ke backend WABiz untuk diproses.

Backend mengambil pengaturan AI dan data informasi lembaga, kemudian mengirimkan pesan beserta data tersebut kepada AI Assistant untuk melakukan analisis intent.

Jika pesan teridentifikasi sebagai kebutuhan pendaftaran, sistem menyimpan informasi terkait, memberikan notifikasi kepada CS Pendaftaran, dan mengirimkan respons kembali kepada client.

### Alur Sequence Diagram

```mermaid
sequenceDiagram
    actor C as Client
    participant W as WhatsApp
    participant S as WhatsApp Service
    participant B as WABiz Backend
    participant AI as AI Assistant
    participant DB as Database
    actor CS as CS Pendaftaran

    C->>W: Saya ingin daftar
    W->>S: Kirim pesan
    S->>B: Request ke backend

    B->>DB: Ambil AI Settings
    DB-->>B: Data pengaturan AI

    B->>DB: Ambil data lembaga
    DB-->>B: Data lembaga

    B->>AI: Kirim pesan dan data
    AI->>AI: Detect Intent
    AI-->>B: Hasil analisis pendaftaran

    B->>DB: Simpan data pendaftaran
    DB-->>B: Konfirmasi penyimpanan

    B->>CS: Notifikasi pendaftaran

    B->>S: Kirim respons
    S->>W: Kirim pesan balasan
    W-->>C: Tampilkan pesan ke client
```

---

## Kesimpulan

Perancangan UML sistem WABiz terdiri dari Use Case Diagram, Activity Diagram, dan Sequence Diagram. Ketiga diagram tersebut digunakan untuk menjelaskan aktor yang terlibat, alur penanganan pesan, serta urutan interaksi antar komponen sistem dalam proses pelayanan dan pendaftaran melalui WhatsApp.
