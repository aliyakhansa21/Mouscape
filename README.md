<div align="center">

# 🐭 Mouscape

### Run through the forest. Collect the cheese. Make your escape!

**Game runner 3D kasual dengan karakter tikus kecil bernama Mousey.**

**Unreal Engine 5.8 · Blueprint · Single-player · Proyek Praktikum Pengembangan Game**

[**Gameplay**](#-tentang-game) · [**Kontrol**](#-kontrol-permainan) · [**Instalasi**](#-cara-menjalankan-project) · [**Struktur Project**](#-struktur-project) · [**Kredit Aset**](#-kredit-aset)

</div>

---

## 🎮 Tentang Game

**Mouscape** adalah game *3D runner* bertema hutan dengan gaya visual cerah dan sederhana. Pemain mengendalikan **Mousey**, seekor tikus yang berlari menyusuri lintasan untuk mengumpulkan keju sambil menghindari rintangan.

Berbeda dari *endless runner*, Mouscape menggunakan **lintasan dengan titik akhir (*fixed-length track*)**. Tantangan utamanya adalah mengumpulkan **10 keju** sebelum perjalanan berakhir, tanpa menabrak rintangan.

Game dirancang dengan kontrol yang sederhana, durasi permainan relatif singkat, dan fokus pada ketepatan waktu saat berpindah ke kiri, ke kanan, atau melompat.

| Informasi | Detail |
| --- | --- |
| **Judul** | Mouscape |
| **Genre** | Casual 3D Runner |
| **Mode** | Single-player |
| **Perspektif** | Third-person |
| **Engine** | Unreal Engine 5.8 |
| **Pengembangan & pengujian** | Windows, Unreal Engine 5.8.4 |
| **Bahasa pemrograman visual** | Unreal Engine Blueprints |
| **Status** | Dalam pengembangan (*prototype*) |

## 🧀 Konsep dan Aturan Permainan

Pemain mengarahkan Mousey melewati lintasan hutan. Karakter dirancang bergerak maju secara otomatis; pemain berfokus pada gerakan lateral dan lompatan untuk mengumpulkan keju sekaligus menghindari rintangan.

**Aturan dan tujuan desain:**

1. **Kumpulkan 10 keju.** Keju merupakan *collectible* utama yang menjadi target permainan.
2. **Hindari rintangan.** Tabrakan dengan rintangan berbahaya dirancang menyebabkan *Game Over* (sistem *one-hit KO*).
3. **Capai kondisi menang.** Target kemenangan adalah mengumpulkan 10 keju; tidak ada lintasan tanpa akhir.
4. **Ulangi permainan jika gagal.** Pemain dapat memulai kembali untuk mencoba rute dan waktu gerakan yang lebih baik.

> **Catatan pengembangan:** Aturan di atas menjelaskan gameplay yang dituju. Implementasi kondisi menang/kalah, layar akhir, dan penyempurnaan gameplay masih mengikuti progres pengembangan tim.

## ⌨️ Kontrol Permainan

| Aksi | Tombol keyboard |
| --- | --- |
| Bergerak ke kiri | `A` atau `←` |
| Bergerak ke kanan | `D` atau `→` |
| Melompat | `Space` |
| Bergerak maju | Otomatis sesuai logic runner |

**Catatan:** Pemetaan input menggunakan sistem **Enhanced Input** di Unreal Engine. Jika kontrol tidak merespons pada level tertentu, periksa *Input Mapping Context*, Pawn yang sedang dikendalikan, dan konfigurasi GameMode level tersebut.

## 🛠️ Teknologi

- **Unreal Engine 5.8** — engine utama untuk level, gameplay, lighting, dan animasi.
- **Blueprint Visual Scripting** — interaksi karakter, rintangan, collectible, serta alur permainan.
- **Animation Blueprint & State Machine** — mengatur perpindahan animasi Mousey, termasuk Run dan Jump.
- **Enhanced Input** — mengelola tombol movement dan jump.
- **Git & GitHub** — version control dan kolaborasi tim.
- **Git LFS** — pengelolaan aset biner Unreal Engine, khususnya `.uasset` dan `.umap`.
- **Blender** — pemeriksaan model dan Action animasi bila dibutuhkan saat proses impor aset.

## 🚀 Cara Menjalankan Project

### Prasyarat

Siapkan aplikasi berikut pada komputer Windows:

1. **Unreal Engine 5.8**. Versi yang digunakan untuk pengujian tim: **5.8.4**.
2. **Git**.
3. **Git LFS**.
4. **Epic Games Launcher**, untuk mengakses instalasi Unreal Engine.

> Disarankan menggunakan versi engine yang sama dengan tim. Jangan melakukan konversi versi project secara sembarangan, terutama ketika bekerja pada repository bersama.

### 1. Clone Repository

Buka **Command Prompt (CMD)** atau terminal pada lokasi penyimpanan yang diinginkan, lalu jalankan:

```bash
git lfs install
git clone https://github.com/aliyakhansa21/Mouscape.git
cd Mouscape
git lfs pull
```

`git lfs pull` memastikan aset Unreal yang disimpan melalui Git LFS diunduh sebagai file sebenarnya, bukan hanya *pointer*.

### 2. Buka Project di Unreal Engine

1. Cari file **`Mouscape.uproject`** di folder hasil clone.
2. Buka file tersebut menggunakan **Unreal Engine 5.8**.
3. Jika Windows menampilkan pesan perbedaan versi engine, periksa dulu versi editor yang terpasang. Pilih **Switch Unreal Engine version** pada file `.uproject` bila perlu, bukan langsung mengonversi project asli.
4. Tunggu proses pemuatan aset dan kompilasi shader awal selesai.

### 3. Buka Level Gameplay

Di **Content Browser**, buka:

```text
Content/Mouscape/World/LV_Run
```

Kemudian tekan **Play** untuk mencoba gameplay.

`LV_ThirdPerson` juga digunakan sebagai level pengujian karakter dan input selama pengembangan.

Jika karakter tidak muncul atau tombol tidak berfungsi, pastikan GameMode level mengarahkan **Default Pawn Class** ke `BP_Mousey` serta *Input Mapping Context* Mousey aktif.

## 📁 Struktur Project

Berikut bagian-bagian penting repository yang digunakan pada pengembangan Mouscape. Susunan folder lain dapat berkembang seiring penambahan aset dan fitur.

```text
Mouscape/
├── Config/
├── Content/
│   └── Mouscape/
│       ├── Blueprints/
│       │   └── Actors/
│       │       ├── BP_Cheese.uasset
│       │       └── BP_TrackTile.uasset
│       │
│       ├── Characters/
│       │   ├── BP_Mousey.uasset
│       │   └── Mousey/
│       │       ├── Mesh/
│       │       ├── Animations/
│       │       └── Materials/
│       │
│       ├── Collectibles/
│       │   └── Cheese/
│       │
│       └── World/
│           └── LV_Run.umap
│
├── .gitattributes
├── .gitignore
└── Mouscape.uproject
```

### Komponen Penting

| Aset / Sistem | Peran |
| --- | --- |
| `BP_Mousey` | Karakter pemain, komponen movement, dan integrasi input |
| `ABP_Mousey` | Animation Blueprint untuk memilih animasi karakter |
| `SK_Mousey` | Skeletal Mesh Mousey |
| `A_Mousey_Run` | Animasi berlari |
| `A_Mousey_Jump_*` | Kandidat animasi melompat |
| `PHYS_Mousey` | Physics Asset karakter |
| `BP_Cheese` | Actor collectible dan logic pengambilan cheese |
| `SM_Cheese` | Static Mesh untuk tampilan keju |
| `BP_TrackTile` | Blueprint elemen lintasan |
| `LV_Run` | Level utama pengembangan runner |

> Nama aset pada tabel mengacu pada penamaan yang digunakan selama pengembangan. Letak aset tertentu dapat berubah ketika struktur folder dirapikan.

## 🔄 Alur Gameplay dan Animasi

### Pergerakan Karakter

`BP_Mousey` menangani karakter dan pergerakannya. Sistem input keyboard berinteraksi dengan komponen **Character Movement**.

Animasi visual dipisahkan ke **`ABP_Mousey`** sehingga gerakan karakter dan pemutaran animasi dapat dikelola secara terpisah.

```text
Input Pemain / Logic Runner
           │
           ▼
        BP_Mousey
           │
           ├── Gerakan maju otomatis
           ├── Gerakan lateral kiri / kanan
           └── Jump / Character Movement
                       │
                       ▼
                   ABP_Mousey
                       │
                  Is In Air?
                    /     \
                   /       \
              False       True
                │           │
               Run         Jump
```

Animasi Run digunakan saat karakter berada di tanah. Ketika Mousey melompat, Animation Blueprint mendeteksi kondisi `IsInAir` dan memindahkan state ke Jump.

Setelah Mousey mendarat, state kembali ke Run.

### Sistem Collectible

Cheese yang ditempatkan di lintasan menggunakan actor collectible.

Model keju 3D diintegrasikan sebagai **Static Mesh** pada Blueprint collectible yang sudah memiliki logic interaksi.

Bentuk visual keju dapat diganti tanpa menghapus komponen collision dan sistem pengambilan yang telah dibuat.

Untuk pengujian, pastikan Mousey dapat menyentuh cheese, interaksi terdeteksi, dan perubahan counter berlangsung sesuai aturan permainan ketika sistem counter aktif.

## 🧪 Status Pengembangan

Mouscape masih berada dalam tahap pengembangan. Beberapa sistem utama sudah dibuat dan diuji, sementara fitur lain masih perlu dilengkapi.

| Area | Status Pengembangan |
| --- | --- |
| Karakter Mousey | Model, skeleton, dan Animation Blueprint telah diintegrasikan |
| Run & Jump | Animasi dan kontrol karakter telah diuji |
| Gerakan kiri/kanan | Input telah dihubungkan dan diuji |
| Level `LV_Run` | Lintasan runner sedang dikembangkan |
| Cheese Collectible | Blueprint interaksi dan visual 3D cheese telah dikerjakan |
| Kondisi menang 10 cheese | Target desain, perlu verifikasi implementasi final |
| Game Over & Restart | Bagian dari rancangan gameplay |
| UI/HUD | Dikembangkan secara bertahap |
| Audio & Sound Effects | Mengikuti progres pengembangan tim |

## 🧰 Troubleshooting

### 1. Karakter atau animasi tidak muncul setelah clone

Jalankan:

```bash
git lfs pull
```

Kemudian buka kembali Unreal Engine dan pastikan Skeletal Mesh serta Animation Blueprint tersedia.

### 2. Project memperingatkan perbedaan versi Unreal Engine

Pastikan instalasi **UE 5.8** yang digunakan sesuai.

Jika perlu, klik kanan `Mouscape.uproject` di Windows, kemudian pilih **Switch Unreal Engine version**.

Hindari melakukan konversi project bersama tanpa koordinasi.

### 3. Input berfungsi di satu level tetapi tidak di level lain

Periksa:

- GameMode dan Default Pawn Class.
- Karakter yang sedang dikontrol PlayerController.
- Input Mapping Context.
- Kondisi gameplay yang membatasi movement.
- Fokus keyboard pada jendela game.

Untuk memeriksa Enhanced Input, gunakan console:

```text
showdebug enhancedinput
```

### 4. Animasi Jump tidak kembali ke Run

Periksa variabel `IsInAir` dan transisi pada State Machine di `ABP_Mousey`.

```text
Run  → Jump : IsInAir = True
Jump → Run  : IsInAir = False
```

### 5. Import glTF gagal karena file BIN tidak ditemukan

Pastikan file `.gltf`, `.bin`, dan tekstur pendamping berada pada struktur folder sumber yang sesuai.

Jika tersedia, format `.glb` bisa digunakan sebagai alternatif karena umumnya menyimpan model dan data binernya dalam satu file.

### 6. Git mengalami konflik pada Blueprint

File `.uasset` dan `.umap` merupakan file biner yang tidak dapat digabung secara otomatis seperti file kode biasa.

Jika dua anggota tim mengubah Blueprint yang sama:

1. Simpan backup kedua versi.
2. Jangan melakukan `git push --force`.
3. Bandingkan perubahan Blueprint menggunakan Unreal Engine.
4. Integrasikan node dan pengaturan yang diperlukan secara manual.
5. Lakukan pengujian sebelum menyelesaikan merge commit.

## 🤝 Kolaborasi dan Git LFS

Repository Mouscape menggunakan **Git Large File Storage (Git LFS)** untuk mengelola aset Unreal Engine.

Contoh konfigurasi `.gitattributes`:

```gitattributes
*.uasset filter=lfs diff=lfs merge=lfs -text
*.umap filter=lfs diff=lfs merge=lfs -text
```

### Alur Kerja Tim

1. Pastikan perubahan sebelumnya sudah disimpan.
2. Ambil perubahan terbaru dari GitHub sebelum mulai bekerja.
3. Gunakan branch fitur jika mengerjakan perubahan besar.
4. Hindari mengedit Blueprint atau level yang sama secara bersamaan tanpa koordinasi.
5. Periksa `git status` sebelum commit.
6. Gunakan Git LFS untuk file aset Unreal Engine.
7. Uji perubahan sebelum digabungkan ke branch utama.

Contoh pemeriksaan Git:

```bash
git status
git lfs ls-files
git branch --show-current
```

Untuk aset Unreal Engine, pastikan file `.uasset` dan `.umap` tersimpan melalui Git LFS.

Folder hasil build dan cache seperti:

```text
Binaries/
Intermediate/
Saved/
DerivedDataCache/
```

tidak perlu dimasukkan ke Git karena dapat dibuat kembali oleh Unreal Engine.

## 🎨 Kredit Aset

Terima kasih kepada kreator aset yang membantu proses pengembangan dan prototipe Mouscape.

| Aset | Kreator | Sumber |
| --- | --- | --- |
| Mouse Character | Charlie Catling | [Mouse — Fab](https://www.fab.com/listings/b1ae92f9-7ac8-449a-8fdb-1893ac9f3a77) |
| Food Kit / Cheese | Kenney | [Kenney Food Kit](https://kenney.nl/assets/food-kit) |
| Nature Kit (referensi/kandidat) | Kenney | [Kenney Nature Kit](https://kenney.nl/assets/nature-kit) |

Model karakter Mousey mengikuti ketentuan lisensi yang berlaku pada listing Fab.

Kenney Food Kit dan Nature Kit tersedia dengan lisensi **CC0 1.0**.

Aset yang digunakan dalam pengembangan harus dicatat sumber, kreator, format, dan ketentuan lisensinya.

> Aset referensi atau kandidat hanya boleh dicantumkan sebagai aset yang benar-benar digunakan setelah diterapkan dalam project.

## 📌 Tentang Proyek

Mouscape dikembangkan sebagai proyek kelompok dalam mata kuliah **Praktikum Pengembangan Game**.

**Program Studi D-IV Teknologi Rekayasa Perangkat Lunak**  
**Universitas Gadjah Mada**  
**Tahun Akademik 2026/2027**

Repository ini digunakan untuk dokumentasi proses pengembangan, kolaborasi tim, serta pengujian prototipe game.

Seluruh aset pihak ketiga tetap menjadi hak pemiliknya masing-masing dan penggunaannya mengikuti lisensi sumber terkait.

> **Lisensi repository:** Belum ada lisensi khusus untuk kode dan karya asli proyek yang dinyatakan pada repository. Akses publik tidak otomatis memberikan izin penggunaan ulang seluruh isi repository.

---

<div align="center">

### 🐭 Mouscape

**One little mouse, ten pieces of cheese, and a forest full of challenges. 🧀**

*Run. Jump. Collect. Escape.*

</div>
