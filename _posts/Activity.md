---
title: Activity Selection Problem
date: 2025-05-02 
categories: [DESAIN ANALISIS ALGORITMA, PROGRAMMING]
tags: [activity-selection-problem, greedy-algorithm, algoritma]     # TAG names should always be lowercase
---
# Activity Selection Problem 🚀

Hai teman-teman! Pernah gak sih kalian pusing gara-gara jadwal yang bentrok? Mau ikut acara A tapi waktunya barengan sama acara B? Atau mungkin, sebagai seorang *programmer*, kalian lagi mikirin gimana caranya bikin jadwal *resource* biar efisien banget? Nah, kalau iya, berarti kalian sudah akrab (walaupun mungkin belum kenal namanya) dengan masalah seru yang namanya **Activity Selection Problem (ASP)**!

Yuk, kita bedah tuntas bareng-bareng!

## Apa Sih Sebenarnya Activity Selection Problem Itu? 🤔

Gampangnya gini: ASP itu adalah tantangan klasik di dunia ilmu komputer di mana tugas kita adalah memilih serangkaian kegiatan yang bisa dilakukan dalam satu waktu, tapi dengan satu aturan emas: **gak boleh ada kegiatan yang tumpang tindih!** Bayangin deh, kalau kalian punya banyak tawaran kegiatan, tapi cuma bisa fokus ke satu hal dalam satu waktu, gimana caranya biar bisa ikutan kegiatan paling banyak? Nah, itu dia ASP!

### Kenapa Masalah Ini Penting Banget di Dunia Nyata? 🌍

Percaya deh, masalah ini ada di mana-mana! Contohnya:

- **Jadwal Ruangan:** Kampus atau kantor punya banyak ruangan, dan banyak acara yang mau pakai. Gimana caranya biar semua ruangan terpakai optimal tanpa ada jadwal yang tabrakan?
- **Wawancara Kerja:** HRD harus menjadwalkan banyak kandidat. Kalau jadwalnya berantakan, bisa kacau semua!
- **Pengelolaan Sumber Daya:** Contohnya, mengatur penggunaan mesin di pabrik, atau slot waktu *server* biar semuanya jalan lancar.

Intinya, ASP ini membantu kita memanfaatkan waktu dan sumber daya sebaik mungkin. Keren, kan?

## Aturan Mainnya (Constraints) 😎

Agar permainan ASP ini adil, ada dua aturan utama yang wajib kita patuhi:

1. **Anti-Tabrakan Klub!** Aktivitas yang kita pilih harus punya waktu mulai yang *sama atau setelah* waktu selesai aktivitas sebelumnya. Jadi, kalau aktivitas pertama selesai jam 4 sore, aktivitas berikutnya harus mulai jam 4 sore atau lebih.
2. **Satu Cinta, Satu Waktu!** Kita cuma bisa melakukan satu aktivitas dalam satu waktu. Gak bisa dong nge-gym sambil ikut kelas masak! 😂

## Kenalan dengan Si Jagoan: Algoritma Greedy! ✨

Nah, buat menyelesaikan masalah ini, kita punya senjata ampuh bernama **Algoritma Greedy**.

### Apa Itu Algoritma Greedy?

Bayangin kalian lagi belanja, terus kalian selalu milih barang yang paling murah saat itu juga, dengan harapan total belanja kalian jadi yang paling murah. Itulah esensi Greedy Algorithm! Ini adalah pendekatan yang selalu membuat keputusan terbaik *saat ini* (secara lokal), dengan harapan keputusan-keputusan kecil ini akan menghasilkan solusi terbaik secara keseluruhan (secara global).

### Kenapa Greedy Cocok Banget buat ASP?

Algoritma Greedy pas banget buat ASP karena dua alasan utama:

- **Ada Optimalitas Lokal:** Kalau kita pilih aktivitas yang selesainya paling cepat, itu akan memberikan *ruang* paling banyak untuk aktivitas lain setelahnya. Logis, kan?
- **Solusi Global dari Keputusan Lokal:** Keputusan-keputusan "terbaik" di setiap langkah (yaitu memilih yang selesai paling cepat) akan secara ajaib membentuk solusi paling optimal secara keseluruhan.

## Strategi Jitu ala Algoritma Greedy untuk ASP 🎯

Penasaran gimana cara kerjanya? Ini dia langkah-langkahnya:

1. **Urutkan Dulu, Sesuai Waktu Selesai!** Ini kunci utama. Kita harus mengurutkan semua aktivitas berdasarkan waktu selesainya, dari yang paling cepat.
2. **Pilih yang Pertama Selesai!** Ambil aktivitas yang ada di urutan paling atas (yang selesainya paling cepat). Ini adalah pilihan awal kita.
3. **Lompat ke yang Gak Bentrok!** Setelah memilih satu aktivitas, cari aktivitas berikutnya di daftar yang waktu mulainya *setelah atau sama dengan* waktu selesai aktivitas yang baru saja kita pilih. Kalau ketemu, pilih dia!
4. **Ulangi Terus Sampai Habis!** Terus lakukan langkah ketiga sampai semua aktivitas di daftar kita cek.

Gampang, kan?

## Mari Berhitung! Contoh Soal Seru! 📊

Misalkan saya punya daftar kegiatan nih, lengkap dengan waktu mulai dan selesainya:

| Aktivitas | Waktu Mulai | Waktu Selesai |
|-----------|-------------|---------------|
| A         | 3           | 6             |
| B         | 1           | 4             |
| C         | 5           | 9             |
| D         | 8           | 10            |
| E         | 2           | 7             |

Tugas saya: Tentukan jumlah aktivitas maksimal yang bisa saya pilih tanpa ada yang tumpang tindih!

### Langkah-langkah Saya Menyelesaikan:

1. **Langkah 1: Urutkan berdasarkan waktu selesai**

   Setelah diurutkan, daftarnya jadi begini:

   | Aktivitas | Waktu Mulai | Waktu Selesai |
   |-----------|-------------|---------------|
   | B         | 1           | 4             |
   | A         | 3           | 6             |
   | E         | 2           | 7             |
   | C         | 5           | 9             |
   | D         | 8           | 10            |

2. **Langkah 2: Pilih Aktivitas Pertama**

   Saya ambil yang paling cepat selesai, yaitu **B** (mulai: 1, selesai: 4).

3. **Langkah 3: Pilih Aktivitas yang Tidak Tumpang Tindih**

   - Setelah B (selesai jam 4):
     - A (mulai jam 3): Ups, jam 3 itu sebelum jam 4. Bentrok! Lewati A.
     - E (mulai jam 2): Lagi-lagi, jam 2 sebelum jam 4. Bentrok! Lewati E.
     - C (mulai jam 5): Nah, jam 5 itu setelah jam 4! Aman! Saya pilih **C**. (C selesai jam 9).
     - D (mulai jam 8): Hmm, jam 8 itu sebelum jam 9 (selesai C). Bentrok! Lewati D.

4. **Langkah 4: Ulangi Proses**

   Sudah tidak ada lagi aktivitas yang bisa dipilih.

### Solusi yang Saya Temukan:

Aktivitas yang terpilih adalah **B** dan **C**.
Jadi, jumlah maksimal aktivitas yang bisa saya pilih adalah **2**.

## Latihan Seru! Yuk Coba Sendiri! 💪

Sekarang giliran kalian! Saya punya daftar kegiatan baru:

| Aktivitas | Waktu Mulai | Waktu Selesai |
|-----------|-------------|---------------|
| A         | 2           | 13            |
| B         | 0           | 6             |
| C         | 5           | 9             |
| D         | 8           | 11            |
| E         | 3           | 5             |
| F         | 12          | 14            |

Coba tentukan aktivitas maksimal yang dapat kalian pilih sehingga tidak ada aktivitas yang saling tumpang tindih!

<details>
<summary>Klik untuk melihat solusi!</summary>

### Solusi Latihan:

1. **Urutkan berdasarkan waktu selesai:**
   - E (mulai: 3, selesai: 5)
   - B (mulai: 0, selesai: 6)
   - C (mulai: 5, selesai: 9)
   - D (mulai: 8, selesai: 11)
   - A (mulai: 2, selesai: 13)
   - F (mulai: 12, selesai: 14)

2. **Pilih aktivitas pertama:** E (mulai: 3, selesai: 5).

3. **Pilih aktivitas berikutnya yang tidak tumpang tindih (setelah E selesai pada 5):**
   - B (mulai: 0) - tumpang tindih
   - C (mulai: 5) - tidak tumpang tindih dengan E (5 ≥ 5). Pilih C. (C selesai pada 9).
   - D (mulai: 8) - tumpang tindih dengan C (8 < 9). Lewati D.
   - A (mulai: 2) - tumpang tindih
   - F (mulai: 12) - tidak tumpang tindih dengan C (12 ≥ 9). Pilih F. (F selesai pada 14).

### Aktivitas yang terpilih adalah E, C, F.

Jumlah maksimal aktivitas yang bisa dipilih adalah **3**.

</details>

## Implementasi dengan C++ (Biar Makin Jago!) 💻

Saya juga sudah siapkan contoh kode C++ untuk menyelesaikan ASP ini. Jadi, kalian bisa langsung coba sendiri!

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

// Struktur untuk menyimpan aktivitas
struct Activity {
    int start;
    int finish;
};

// Fungsi perbandingan untuk mengurutkan aktivitas berdasarkan waktu selesai
bool compareActivities(Activity a, Activity b) {
    return (a.finish < b.finish);
}

// Fungsi untuk memilih aktivitas maksimal
void activitySelection(std::vector<Activity> activities, int n) {
    // Urutkan aktivitas berdasarkan waktu selesai
    std::sort(activities.begin(), activities.end(), compareActivities);

    std::cout << "Aktivitas yang dipilih:" << std::endl;

    // Pilih aktivitas pertama yang selesai lebih cepat
    int i = 0;
    std::cout << "Aktivitas: (Start: " << activities[i].start 
              << ", Finish: " << activities[i].finish << ")" << std::endl;

    // Gunakan loop untuk memilih aktivitas yang tidak tumpang tindih
    for (int j = 1; j < n; j++) {
        // Jika waktu mulai aktivitas saat ini lebih besar atau sama dengan
        // waktu selesai aktivitas yang terakhir dipilih
        if (activities[j].start >= activities[i].finish) {
            std::cout << "Aktivitas: (Start: " << activities[j].start 
                      << ", Finish: " << activities[j].finish << ")" << std::endl;
            i = j; // Perbarui aktivitas terakhir yang dipilih
        }
    }
}

int main() {
    // Definisikan aktivitas
    std::vector<Activity> activities = {
        {1, 8}, {3, 4}, {0, 6}, {5, 9}, {5, 7}, {8, 9}
    };
    int n = activities.size();

    // Memanggil fungsi activitySelection untuk menyelesaikan ASP
    activitySelection(activities, n);

    return 0;
}
```

### Penjelasan Kodenya (Biar Gak Bingung!) 🤓

- **`struct Activity`**: Ini semacam "cetak biru" untuk setiap aktivitas. Di dalamnya ada `start` (waktu mulai) dan `finish` (waktu selesai).
- **`compareActivities`**: Fungsi kecil ini gunanya buat ngurutin aktivitas. Dia memastikan `std::sort()` mengurutkan berdasarkan waktu selesai yang paling cepat.
- **`activitySelection`**: Ini dia *otak* programnya!
  - Pertama, semua aktivitas diurutkan pakai `std::sort()` dan `compareActivities`.
  - Lalu, aktivitas pertama yang selesai paling cepat langsung dipilih.
  - Setelah itu, ada perulangan (`for loop`) yang mencari aktivitas berikutnya. Syaratnya: waktu mulai aktivitas baru harus *sama atau setelah* waktu selesai aktivitas yang terakhir dipilih.
  - Setiap aktivitas yang terpilih akan dicetak.
- **`main()`**: Bagian ini cuma buat *nyobain* fungsinya. Saya definisikan beberapa aktivitas, lalu panggil `activitySelection` untuk melihat hasilnya.

### Hasil Akhir Kode (Output Program) 🥳

Kalau kalian jalankan kode C++ di atas, dengan contoh aktivitas yang ada, outputnya akan jadi seperti ini:

```
Aktivitas yang dipilih:
Aktivitas: (Start: 3, Finish: 4)
Aktivitas: (Start: 5, Finish: 7)
Aktivitas: (Start: 8, Finish: 9)
```

Aktivitas yang dipilih adalah (3,4), (5,7), dan (8,9). Program memilih aktivitas sebanyak mungkin yang tidak saling bertumpang tindih, persis seperti prinsip *greedy* yang sudah kita bahas!

## Kompleksitas Algoritma 📈

Mari kita bahas seberapa efisien algoritma ini:

- **Time Complexity**: O(n log n) - karena proses sorting yang mendominasi
- **Space Complexity**: O(1) - karena kita hanya butuh beberapa variabel tambahan

Sangat efisien untuk masalah penjadwalan praktis!

## Variasi Masalah ASP 🔄

Ada beberapa variasi menarik dari ASP:

1. **Weighted Activity Selection**: Setiap aktivitas punya bobot/nilai, dan kita mau maksimalkan total nilai
2. **Activity Selection with Penalties**: Ada penalti untuk tidak memilih aktivitas tertentu
3. **Multi-Resource Activity Selection**: Satu aktivitas bisa butuh beberapa resource sekaligus

## Tips dan Trik 💡

- Selalu pastikan data sudah terurut berdasarkan waktu selesai
- Gunakan struktur data yang tepat untuk mempercepat pencarian
- Pertimbangkan edge cases seperti aktivitas dengan durasi 0
- Untuk dataset besar, pertimbangkan optimasi algoritma sorting

## Kesimpulan Manisnya 🍬

Activity Selection Problem (ASP) itu masalah optimasi yang super penting di dunia nyata. Dengan memakai pendekatan *greedy*, kita bisa menyelesaikannya dengan efisien dan gampang dimengerti.

Intinya, kita memilih aktivitas yang selesai paling awal dan memastikan tidak ada aktivitas yang bertabrakan. Pendekatan ini cocok diterapkan dalam berbagai aplikasi penjadwalan seperti pengelolaan kelas, penggunaan ruang, atau pengaturan wawancara.

Keunggulan dari solusi ini adalah kesederhanaan logika dan efisiensi waktu komputasi. Semoga panduan ini membantu kalian memahami dan mengimplementasikan ASP dengan lebih baik!

---

*Happy coding! 🚀*