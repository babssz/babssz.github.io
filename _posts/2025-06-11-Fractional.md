---
title: Fractional Knapsack
date: 2025-05-06 
categories: [DESAIN ANALISIS ALGORITMA, PROGRAMING]
tags: [knapsack-problem, fractional-knapsack, greedy-algorithm, algoritma]     # TAG names should always be lowercase
---
# Fractional Knapsack! 🎒💰

Hai teman-teman! Pernah gak sih kalian bayangin lagi liburan terus punya ransel yang kapasitasnya terbatas, tapi kalian pengen bawa barang sebanyak mungkin dengan nilai paling tinggi? Atau, mungkin kalian lagi main game RPG dan harus milih *item* mana yang paling berharga untuk dibawa? Nah, kalau iya, berarti kalian lagi berhadapan sama masalah yang namanya **Fractional Knapsack**!

Yuk, kita selami lebih dalam dan pecahkan misteri ransel ini bareng-bareng!

## Fractional Knapsack Itu Apa Sih? 🤔

Jadi gini, **Fractional Knapsack** adalah salah satu varian dari masalah *knapsack* (ransel) di dunia algoritma. Bedanya dengan yang lain? Di sini, kita **boleh banget mengambil sebagian dari suatu *item***! Ibaratnya, kalau ada emas 5 kg dan ransel kita cuma muat 3 kg, kita bisa potong emasnya dan cuma bawa 3 kg itu. Tujuannya cuma satu: **memaksimalkan nilai total barang** yang bisa kita bawa dengan kapasitas ransel yang terbatas.

Kata "fractional" sendiri berarti pecahan atau bagian, jadi memang kita bisa mengambil "pecahan" dari barang. Sedangkan "knapsack" itu artinya ransel atau tas, yang jadi metafora buat kapasitas penyimpanan kita yang terbatas.

## Masalah Dasar Knapsack (The Big Picture) 🤯

Pada dasarnya, masalah Knapsack ini muncul kalau kita punya tas dengan kapasitas terbatas, dan kita mau pilih barang-barang yang bisa masuk ke tas itu buat **memaksimalkan nilai total** barang yang kita bawa. Intinya, gimana caranya "isi tas dengan barang yang memberi nilai tertinggi, tanpa melebihi kapasitas."

### Ada Berapa Jenis Knapsack Problem Sih?

Secara umum, ada dua jenis Knapsack Problem yang sering kita temui:

1. **0/1 Knapsack Problem:** Ini yang "keras kepala". Kita cuma bisa milih barang **utuh**, gak bisa ambil sebagian (pecahan). Ibaratnya, kalau emasnya kegedean, ya gak bisa dibawa sama sekali.
2. **Fractional Knapsack Problem:** Nah, ini yang "fleksibel"! Di sini, kita **bisa mengambil sebagian** dari barang, gak harus utuh. Ini yang sedang kita bahas!

## Konsep Kunci Fractional Knapsack (FKO) 🔑

Bayangkan kalian punya tas dengan kapasitas terbatas, dan di depan kalian ada beberapa barang dengan berat dan nilai yang berbeda-beda. Tujuan kita, seperti yang sudah saya sebutkan, adalah memaksimalkan nilai barang yang kita bawa, tapi ingat, kapasitas tas itu terbatas!

Karena ini *fractional*, kita boleh potong-potong barangnya! Jadi, kalau kalian cuma bisa bawa 3 kg dari emas seberat 5 kg, gak masalah! Yang penting nilainya tetap ikut proporsional sesuai porsi yang diambil.

## Latihan Seru! Yuk, Isi Ransel Kita! 🎒

Sekarang, mari kita coba latihan biar makin paham!

Sebuah tas punya kapasitas maksimum **50 kg**. Tersedia 3 barang berikut ini:

| Barang | Berat (kg) | Nilai (Rp) |
| :----- | :--------- | :--------- |
| A      | 10         | 60         |
| B      | 20         | 100        |
| C      | 30         | 120        |

Kita boleh banget mengambil barang sebagian atau seluruhnya.

Tentukan nilai maksimum yang dapat dibawa oleh tas dengan strategi Fractional Knapsack!

### Langkah-langkah Penyelesaian (Jurus Rahasia Kita!) 👇

Ini dia strateginya, pakai algoritma *greedy* tentunya!

1. **Langkah 1: Hitung Nilai Per Berat (Value/Weight) Setiap Barang!**
   Ini penting banget buat tahu barang mana yang paling "berharga" per kilogramnya.
   * **A:** 60 / 10 = **6.0**
   * **B:** 100 / 20 = **5.0**
   * **C:** 120 / 30 = **4.0**

2. **Langkah 2: Urutkan Barang Berdasarkan Rasio (Nilai Per Berat) Tertinggi ke Terendah!**
   * A (rasio 6.0)
   * B (rasio 5.0)
   * C (rasio 4.0)

3. **Langkah 3: Mulai Isi Ransel dari yang Paling Berharga!**
   Kapasitas awal tas kita: **50 kg**.

   * **Ambil Barang A (10 kg, nilai 60)**
     * Masih muat? Tentu! Kita ambil seluruhnya.
     * Sisa kapasitas = 50 - 10 = **40 kg**
     * Total nilai = **60**

   * **Ambil Barang B (20 kg, nilai 100)**
     * Masih muat? Ya! Kapasitas kita masih 40 kg. Kita ambil seluruhnya.
     * Sisa kapasitas = 40 - 20 = **20 kg**
     * Total nilai = 60 + 100 = **160**

   * **Ambil Barang C (30 kg, nilai 120)**
     * Tidak muat seluruhnya! Kapasitas kita tinggal 20 kg, tapi barang C beratnya 30 kg.
     * Kita ambil sebagian, yaitu sebanyak **20 kg dari 30 kg** yang tersedia.
     * Proporsi yang diambil = 20 / 30 = **2/3**
     * Nilai yang diambil dari C = (2/3) × 120 = **80**
     * Sisa kapasitas = **0 kg** (tas sudah penuh!)
     * Total nilai = 160 + 80 = **240**

### Hasilnya:

Nilai maksimum yang dapat kita bawa adalah **Rp 240!**

## Implementasi dengan C++ (Biar Kalian Makin Jago!) 💻

Sebagai seorang *programmer*, tentu kurang lengkap kalau gak ada kodenya, kan? Nah, saya sudah siapkan contoh implementasi Fractional Knapsack pakai C++:

```cpp
#include <iostream> // Untuk input/output dasar
#include <vector>   // Untuk menggunakan dynamic array (vector)
#include <algorithm> // Untuk fungsi sort()

using namespace std; // Mempermudah penulisan kode

// Struktur data untuk merepresentasikan sebuah barang
struct Barang {
    int berat; // berat barang
    int nilai; // nilai barang

    // Fungsi untuk menghitung rasio nilai terhadap berat
    double nilaiPerBerat() const {
        return (double)nilai / berat; // Menghasilkan nilai desimal
    }
};

// Fungsi pembanding untuk mengurutkan barang berdasarkan rasio nilai per berat (dari yang tertinggi)
bool bandingkan(Barang a, Barang b) {
    return a.nilaiPerBerat() > b.nilaiPerBerat(); // Mengurutkan menurun
}

// Fungsi utama untuk menyelesaikan masalah Knapsack Fraksional
double knapsackFraksional(int kapasitas, vector<Barang>& daftarBarang) {
    // Urutkan daftar barang berdasarkan rasio nilai per berat secara menurun
    sort(daftarBarang.begin(), daftarBarang.end(), bandingkan);

    double totalNilai = 0.0; // Menyimpan total nilai barang yang diambil, mulai dari nol

    // Iterasi setiap barang dalam daftar
    for (const auto& barang : daftarBarang) {
        if (kapasitas == 0) break; // Jika kapasitas tas sudah penuh, berhenti

        if (barang.berat <= kapasitas) {
            // Jika berat barang masih muat di tas, ambil seluruhnya
            kapasitas -= barang.berat; // Kurangi kapasitas tas
            totalNilai += barang.nilai; // Tambahkan nilai barang ke total
        } else {
            // Jika barang terlalu berat, ambil sebagian sesuai sisa kapasitas
            totalNilai += barang.nilaiPerBerat() * kapasitas; // Ambil nilai proporsional
            kapasitas = 0; // Kapasitas tas habis
        }
    }

    return totalNilai; // Kembalikan total nilai maksimum yang bisa dibawa
}

int main() {
    int kapasitasTas = 50; // Kapasitas maksimum tas

    // Daftar barang yang tersedia (berat, nilai)
    vector<Barang> daftarBarang = {
        {10, 60},  // Barang pertama: Berat 10, Nilai 60
        {20, 100}, // Barang kedua: Berat 20, Nilai 100
        {30, 120}  // Barang ketiga: Berat 30, Nilai 120
    };

    // Hitung nilai maksimum yang bisa dibawa dengan tas
    double nilaiMaksimum = knapsackFraksional(kapasitasTas, daftarBarang);

    // Tampilkan hasil
    cout << "Nilai maksimum yang bisa dibawa: " << nilaiMaksimum << endl;

    return 0;
}
```

### Penjelasan Kodenya (Biar Gak Bingung!) 🤓

* **`struct Barang`**: Ini adalah "cetak biru" untuk setiap barang. Dia menyimpan `berat` dan `nilai` barangnya. Yang paling penting, ada fungsi `nilaiPerBerat()` yang langsung menghitung rasio nilai terhadap berat, jadi kita gak perlu pusing lagi di fungsi utama.
* **`bandingkan`**: Fungsi ini khusus buat `std::sort()`. Dia akan membandingkan dua barang berdasarkan `nilaiPerBerat()` mereka dan mengurutkannya dari yang rasionya paling tinggi.
* **`knapsackFraksional`**: Ini dia jantungnya algoritma *greedy* kita!
  * Pertama, semua `daftarBarang` akan diurutkan pakai `bandingkan`.
  * Lalu, ada `totalNilai` yang disiapkan dengan nilai awal 0.0.
  * Program akan mengiterasi setiap barang yang sudah diurutkan.
  * Jika ransel sudah penuh (`kapasitas == 0`), proses berhenti.
  * Kalau berat barang **muat semua** di ransel, barang itu diambil utuh, kapasitas dikurangi, dan nilai ditambahkan.
  * Kalau berat barang **tidak muat semua**, kita cuma ambil sebagian yang bisa masuk, hitung nilai proporsionalnya, dan kapasitas ransel jadi 0.
* **`main()`**: Bagian ini cuma buat *nyobain* fungsi `knapsackFraksional`. Saya set kapasitas tas jadi 50 kg dan mendefinisikan 3 barang contoh. Setelah itu, hasilnya akan dicetak ke konsol.

### Hasil Akhir Kode (Output Program) 🥳

Kalau kalian jalankan kode C++ di atas, dengan contoh barang yang saya berikan, outputnya akan jadi:

```
Nilai maksimum yang bisa dibawa: 240
```

Cocok banget sama perhitungan manual kita, kan? Ini menunjukkan bahwa algoritma *greedy* kita berhasil memaksimalkan nilai barang yang dibawa!

## Kesimpulan Manisnya 🍬

Dari petualangan kita mengisi ransel ini, ada beberapa poin penting yang bisa kita simpulkan:

* Dalam Fractional Knapsack, kita punya kebebasan untuk **memilih sebagian barang** kalau gak muat semuanya. Fleksibel!
* Solusi terbaiknya adalah pakai **algoritma *greedy***. Caranya? Selalu pilih barang yang **rasio nilai per beratnya paling tinggi** duluan.
* Langkah-langkahnya simpel: **hitung rasio, urutkan barang, lalu masukkan ke tas** sesuai kapasitas.
* Efisiensinya juga lumayan bagus, punya kompleksitas waktu O(n log n)! Ini karena proses pengurutan yang paling memakan waktu.

Masalah Fractional Knapsack ini sering banget muncul di kehidupan nyata, lho! Semoga penjelasan ini bikin kalian makin paham dan semangat belajar algoritma, ya! 💪