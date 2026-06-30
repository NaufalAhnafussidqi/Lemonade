# 🍋 Lemonade

**Tugas Pemrograman Perangkat Bergerak**

Aplikasi Android interaktif untuk membuat lemonade, dibangun menggunakan **Kotlin** dan **Jetpack Compose**.

---

## ✨ Fitur

- 🌳 **Petik Lemon** — Ketuk pohon lemon untuk memetik buah
- 🤏 **Peras Lemon** — Ketuk lemon berulang kali (2–4 kali secara acak) untuk memerasnya
- 🥤 **Minum Lemonade** — Ketuk gelas lemonade untuk meminumnya
- 🔄 **Ulangi** — Ketuk gelas kosong untuk memulai dari awal
- 🎨 **UI Modern** — Menggunakan Jetpack Compose dengan Material Design 3

---

## 🛠️ Teknologi

| Komponen | Versi |
|----------|-------|
| Android Gradle Plugin | 9.1.1 |
| Kotlin | 2.2.10 |
| Compile SDK | 36 |
| Min SDK | 24 (Android 7.0) |
| Target SDK | 36 |
| Jetpack Compose BOM | 2026.02.01 |
| Material Design | 3 (Material3) |

---

## 📂 Struktur Proyek

```
Lemonade/
├── app/
│   ├── build.gradle.kts          # Konfigurasi build aplikasi
│   └── src/
│       └── main/
│           ├── AndroidManifest.xml
│           ├── java/com/example/lemonade/
│           │   └── MainActivity.kt   # Logika utama aplikasi
│           └── res/
│               ├── drawable/         # Gambar (lemon_tree, lemon_squeeze, lemon_drink, lemon_restart)
│               └── values/
│                   └── strings.xml   # String resource
├── build.gradle.kts              # Konfigurasi build root
├── settings.gradle.kts           # Pengaturan project
├── gradle/
│   └── libs.versions.toml        # Version catalog dependencies
├── gradlew / gradlew.bat         # Gradle wrapper
└── README.md                     # Dokumentasi proyek
```

---

## 🚀 Cara Menjalankan

### Prasyarat
- Android Studio (versi terbaru direkomendasikan)
- JDK 11 atau lebih tinggi
- Android SDK dengan API Level 36

### Langkah-langkah

1. **Clone repository**
   ```bash
   git clone https://github.com/NaufalAhnafussidqi/Lemonade.git
   cd Lemonade
   ```

2. **Buka di Android Studio**
   - Pilih **File → Open** dan arahkan ke folder proyek
   - Tunggu Gradle sync selesai

3. **Jalankan aplikasi**
   - Hubungkan perangkat Android atau buka emulator
   - Klik tombol **Run** (▶️) atau tekan `Shift + F10`

---

## 📝 Penjelasan Kode

### `MainActivity.kt`

File utama aplikasi yang mengatur alur interaksi pengguna melalui 4 tahap:

| Tahap | Gambar | Instruksi | Aksi |
|-------|--------|-----------|------|
| 1 | `lemon_tree` | *Tap the lemon tree to pick a lemon* | Ketuk pohon → pindah ke tahap 2 |
| 2 | `lemon_squeeze` | *Keep tapping the lemon to squeeze it* | Ketuk lemon berulang kali (acak 2–4 kali) |
| 3 | `lemon_drink` | *Tap the lemonade to drink it* | Ketuk gelas → pindah ke tahap 4 |
| 4 | `lemon_restart` | *Tap the empty glass to start again* | Ketuk gelas kosong → kembali ke tahap 1 |

### Logika Utama

```kotlin
var step by remember { mutableStateOf(1) }
var squeezeCount by remember { mutableStateOf(0) }

Image(
    painter = painterResource(id = imageRes),
    contentDescription = "Lemon Image",
    modifier = Modifier
        .size(250.dp)
        .clickable {
            when (step) {
                1 -> {
                    step = 2
                    squeezeCount = Random.nextInt(2, 5)  // Acak 2–4 kali peras
                }
                2 -> {
                    squeezeCount--
                    if (squeezeCount == 0) step = 3
                }
                3 -> step = 4
                4 -> step = 1
            }
        }
)
```

---

## 👤 Author

**Naufal Ahnafussidqi Perdana**

---

## 📄 Lisensi

Proyek ini dibuat untuk keperluan tugas pemrograman perangkat bergerak.
