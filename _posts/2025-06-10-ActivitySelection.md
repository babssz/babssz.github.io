---
title: Activity Selection Problem
date: 2025-05-06 
categories: [TOP_CATEGORIE, SUB_CATEGORIE]
tags: [activity-selection-problem, greedy-algorithm, algoritma]     # TAG names should always be lowercase
---
# Memilih Kegiatan Terbaik: Rahasia di Balik Activity Selection Problem! 🚀

Hai teman-teman!  
Pernah gak sih kalian pusing gara-gara jadwal yang bentrok? Mau ikut acara A tapi waktunya barengan sama acara B? Atau mungkin, sebagai seorang programmer, kalian lagi mikirin gimana caranya bikin jadwal resource biar efisien banget?

Nah, kalau iya, berarti kalian sudah akrab (walaupun mungkin belum kenal namanya) dengan masalah seru yang namanya **Activity Selection Problem (ASP)**!

Yuk, kita bedah tuntas bareng-bareng!

---

## Apa Sih Sebenarnya Activity Selection Problem Itu? 🤔

Gampangnya gini: ASP itu adalah tantangan klasik di dunia ilmu komputer di mana tugas kita adalah memilih serangkaian kegiatan yang bisa dilakukan dalam satu waktu, tapi dengan satu aturan emas: **gak boleh ada kegiatan yang tumpang tindih!**

---

## Kenapa Masalah Ini Penting Banget di Dunia Nyata? 🌍

Contoh penerapannya:
- **Jadwal Ruangan**
- **Wawancara Kerja**
- **Pengelolaan Mesin atau Server**

ASP membantu kita **memanfaatkan waktu dan sumber daya sebaik mungkin.**

---

## Aturan Mainnya (Constraints) 😎

1. **Anti-Tabrakan Klub!**  
   Aktivitas selanjutnya harus dimulai **setelah atau tepat saat** aktivitas sebelumnya selesai.

2. **Satu Cinta, Satu Waktu!**  
   Kita cuma bisa melakukan satu aktivitas dalam satu waktu. Gak bisa dong ngerjain dua hal sekaligus 😅

---

## Kenalan dengan Si Jagoan: Algoritma Greedy! ✨

### Apa Itu Algoritma Greedy?
Greedy = ambil keputusan **terbaik saat ini**, berharap semua keputusan lokal menghasilkan **solusi terbaik global**.

### Kenapa Cocok Buat ASP?
- **Pilih aktivitas dengan waktu selesai tercepat** → bisa sisip lebih banyak aktivitas berikutnya.
- Sederhana, cepat, dan optimal!

---

## Strategi Jitu ala Algoritma Greedy untuk ASP 🎯

Langkah-langkahnya:

1. Urutkan aktivitas berdasarkan waktu selesai.
2. Ambil aktivitas pertama.
3. Pilih aktivitas selanjutnya yang dimulai **setelah atau saat** aktivitas terakhir selesai.
4. Ulangi sampai semua diperiksa.

---

## Mari Berhitung! Contoh Soal Seru! 📊

### Daftar Aktivitas:

| Aktivitas | Waktu Mulai | Waktu Selesai |
|----------|--------------|----------------|
| A        | 3            | 6              |
| B        | 1            | 4              |
| C        | 5            | 9              |
| D        | 8            | 10             |
| E        | 2            | 7              |

### Langkah-Langkah:
1. Urutkan berdasarkan waktu selesai:
   B (1-4), A (3-6), E (2-7), C (5-9), D (8-10)
2. Pilih B → selesai jam 4
3. Lanjut ke C (mulai jam 5) → aman
4. D (mulai jam 8) → bentrok dengan C (masih berlangsung)

✅ **Hasil: B dan C → 2 aktivitas maksimal**

---

## Latihan Seru! Yuk Coba Sendiri! 💪

| Aktivitas | Waktu Mulai | Waktu Selesai |
|----------|--------------|----------------|
| A        | 2            | 13             |
| B        | 0            | 6              |
| C        | 5            | 9              |
| D        | 8            | 11             |
| E        | 3            | 5              |
| F        | 12           | 14             |

<details>
<summary>Klik untuk lihat solusi! 👇</summary>

### Urutan berdasarkan waktu selesai:
- E (3-5)
- B (0-6)
- C (5-9)
- D (8-11)
- A (2-13)
- F (12-14)

### Pilihan:
- E → selesai jam 5
- C → mulai jam 5
- D → mulai jam 8 → bentrok dengan C (masih jalan)
- F → mulai jam 12 → bisa!

✅ **Hasil: E, C, F → 3 aktivitas (atau E, C, D, F jika urutannya beda & cek ketat)**

</details>

---

## Implementasi dengan C++ 💻

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

struct Activity {
    int start;
    int finish;
};

bool compareActivities(Activity a, Activity b) {
    return (a.finish < b.finish);
}

void activitySelection(std::vector<Activity> activities, int n) {
    std::sort(activities.begin(), activities.end(), compareActivities);

    std::cout << "Aktivitas yang saya pilih:\n";

    int i = 0;
    std::cout << "(Start: " << activities[i].start << ", Finish: " << activities[i].finish << ")\n";

    for (int j = 1; j < n; j++) {
        if (activities[j].start >= activities[i].finish) {
            std::cout << "(Start: " << activities[j].start << ", Finish: " << activities[j].finish << ")\n";
            i = j;
        }
    }
}

int main() {
    std::vector<Activity> activities = {
        {1, 8}, {3, 4}, {0, 6}, {5, 9}, {5, 7}, {8, 9}
    };
    int n = activities.size();

    activitySelection(activities, n);

    return 0;
}



 


