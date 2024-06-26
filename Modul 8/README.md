# <h1 align="center">Laporan Praktikum Modul Queue</h1>

<p align="center">Jeremy Marcello Waani / 2311110003 / S1SD04-A</p>

## Dasar Teori

### 1. Pengertian Queue

Queue atau antrian adalah struktur data linier yang mengikuti aturan First In First Out (FIFO) [1]. Artinya, elemen yang pertama kali masuk ke dalam queue akan menjadi elemen pertama yang dikeluarkan [1]. Queue sering dianalogikan dengan antrian di kehidupan nyata, di mana orang yang datang pertama kali akan dilayani terlebih dahulu [1].

Implementasi Queue:

Queue dapat diimplementasikan dengan berbagai cara, salah satu yang umum adalah menggunakan array atau linked list. Berikut adalah beberapa fungsi dasar yang terdapat dalam queue:
* **enqueue(element):** Fungsi ini menambahkan elemen baru ke bagian belakang queue [1].
* **dequeue():** Fungsi ini menghapus elemen terdepan dari queue dan mengembalikan nilainya [1].
* **front():** Fungsi ini mengembalikan nilai elemen terdepan dari queue tanpa menghapusnya [1].
* **empty():** Fungsi ini memeriksa apakah queue kosong atau tidak [1].
* **size():** Fungsi ini mengembalikan jumlah elemen yang terdapat dalam queue [1].



## Guided
```C++
#include <iostream>
#include <string>
using namespace std;

const int maksimalQueue = 5; // Maksimal Antrian
int front = 0; // Penanda Depan Antrian
int back = 0; // Penanda Belakang Antrian
string queueTeller[5]; // Deklarasi Antrian Teller

bool isFull() { // Pengecekan Antrian Sudah Penuh Atau Tidak
    if (back == maksimalQueue) {
        return true; // = 1
    } else {
        return false;
    }
}


bool isEmpty() { // Pengecekan Antrian Sudah Kosong Atau Tidak
    if (back == 0) {
        return true;
    } else {
        return false;
    }
}

void enqueueAntrian(string data) { // Fungsi Menambahkan Antrian
    if (isFull()) {
        cout << "Antrian Sudah Penuh" << endl;
    } else {
        if (isEmpty()) {
            queueTeller[0] = data;
            front++;
            back++;
        } else {
            queueTeller[back] = data;
            back++;
        }
    }
}

void dequeueAntrian() { // Fungsi Mengurangi Antrian
    if (isEmpty()) {
        cout << "Antrian Kosong" << endl;
    } else {
        for (int i = 0; i < back; i++) {
            queueTeller[i] = queueTeller[i + 1];
        }
        back--;
    }
}

int countQueue() { // Fungsi Menghitung Banyak Antrian
    return back;
}

void clearQueue() { // Fungsi Menghapus Antrian
    if (isEmpty()) {
        cout << "Antrian Kosong" << endl;
    } else {
        for (int i = 0; i < back; i++) {
            queueTeller[i] = "";
        }
        front = 0;
        back = 0;
    }
}

void viewQueue() { // Fungsi Melihat Antrian
    cout << "Data Antrian Teller :" << endl;
    for (int i = 0; i < maksimalQueue; i++) {
        if (queueTeller[i] != "") {
            cout << i + 1 << ". " << queueTeller[i] << endl;
        } else {
            cout << i + 1 << ". (Kosong)" << endl;
        }
    }
}

int main() {
    enqueueAntrian("Andi");
    enqueueAntrian("Maya");
    
    viewQueue();
    cout << "Jumlah Antrian = " << countQueue() << endl;
    
    dequeueAntrian();
    viewQueue();
    cout << "Jumlah Antrian = " << countQueue() << endl;
    
    clearQueue();
    viewQueue();
    cout << "Jumlah Antrian = " << countQueue() << endl;
    
    return 0;
}
```

**Output:**
![8G1](https://github.com/JeremyMarcello/Assignment-Praktikum-Algoritma-dan-Struktur-Data/assets/156126843/855264f2-5105-4913-8685-b5f546bdfa04)

**Kode yang diberikan mengimplementasikan sistem antrian untuk mengatur antrian teller di bank. Berikut interpretasi detailnya:**

**Struktur Data:**

* queueTeller: Array string dengan ukuran maksimalQueue (5) untuk menyimpan data nasabah yang sedang mengantri di teller bank.
* front: Variabel integer untuk menunjuk ke indeks elemen terdepan dalam antrian (awalnya 0).
* back: Variabel integer untuk menunjuk ke indeks elemen belakang dalam antrian (awalnya 0).

**Fungsi:**

* isFull(): Memeriksa apakah antrian penuh dengan mengembalikan true jika back sama dengan maksimalQueue dan false sebaliknya.
* isEmpty(): Memeriksa apakah antrian kosong dengan mengembalikan true jika back sama dengan 0 dan false sebaliknya.
* enqueueAntrian(data): Menambahkan data nasabah baru ke antrian.
    * Memeriksa apakah antrian penuh.
        * Jika penuh, tampilkan pesan "Antrian Penuh".
        * Jika tidak penuh:
            * Jika antrian kosong (back == 0), tambahkan data ke indeks 0 pada array queueTeller dan update front dan back ke 1.
            * Jika tidak kosong, tambahkan data ke indeks back pada array queueTeller dan update back ditambahan 1.
* dequeueAntrian(): Menghapus data nasabah terdepan dari antrian.
    * Memeriksa apakah antrian kosong.
        * Jika kosong, tampilkan pesan "Antrian kosong".
        * Jika tidak kosong, lakukan loop untuk memindahkan elemen antrian ke indeks sebelumnya (geser ke depan) hingga indeks terakhir.
        * Kurangi nilai back untuk menunjukkan elemen terakhir yang baru.
* countQueue(): Menghitung jumlah data nasabah yang sedang mengantri.
    * Mengembalikan nilai back, yang menunjukkan indeks elemen terakhir dalam antrian ditambah 1 (jumlah elemen).
* clearQueue(): Menghapus semua data nasabah dari antrian.
    * Memeriksa apakah antrian kosong.
        * Jika kosong, tampilkan pesan "Antrian kosong".
        * Jika tidak kosong, loop untuk mengisi semua elemen dalam array queueTeller dengan string kosong.
        * Update back dan front ke 0 untuk mereset antrian.
* viewQueue(): Menampilkan data nasabah yang sedang mengantri.
    * Cetak judul "Data antrian teller".
    * Loop melalui seluruh elemen queueTeller.
        * Jika elemen tidak kosong, cetak data nasabah dengan format "[nomor urut]. [nama nasabah]".
        * Jika elemen kosong, cetak "[nomor urut]. (kosong)" untuk menandakan posisi kosong dalam antrian.

**Fungsi Utama (main):**

* Memasukkan data nasabah "Andi" dan "Maya" ke dalam antrian * menggunakan enqueueAntrian.
* Menampilkan data antrian menggunakan viewQueue.
* Menampilkan jumlah antrian menggunakan countQueue.
* Menghapus data nasabah terdepan dari antrian menggunakan dequeueAntrian.
* Menampilkan data antrian dan jumlah antrian setelah penghapusan.
* Menghapus semua data nasabah dari antrian menggunakan clearQueue.
* Menampilkan data antrian dan jumlah antrian setelah penghapusan semua data (antrian kosong).

Kesimpulan:

Kode ini mensimulasikan antrian teller bank menggunakan konsep antrian (queue). Fungsi-fungsi yang disediakan dapat mempermudah untuk menambahkan, mengurangi, melihat jumlah antrian.

## Unguided

### 1. Ubahlah penerapan konsep queue pada bagian guided dari array menjadi linked list

```C++
#include <iostream>
#include <string>
using namespace std;

struct Node {
    string data;
    Node* next;
};

Node* front = NULL;
Node* back = NULL;

bool isFull() { // Pengecekan Antrian Sudah Penuh Atau Tidak
    // Tidak ada batas maksimal
    return false;
}

bool isEmpty() { // Pengecekan Antrian Sudah Kosong Atau Tidak
    if (back == 0) {
        return true;
    } else {
        return false;
    }
}

void enqueueAntrian(string data) { // Fungsi Menambahkan Antrian
    Node* newNode = new Node;
    newNode->data = data;
    newNode->next = NULL;
    if (isEmpty()) {
            front = back = newNode;
    } else {
            back->next = newNode;
            back = newNode;
    }
}

void dequeueAntrian() { // Fungsi Mengurangi Antrian
    if (isEmpty()) {
        cout << "Antrian Kosong" << endl;
    } else {
        Node* temp = front;
        front = front->next;
        delete temp;
        if (front == NULL) {
            back = NULL;
        }
    }
}

int countQueue() { // Fungsi Menghitung Banyak Antrian
    int count = 0;
    Node* cur = front;
    while (cur != NULL) {
        count++;
        cur = cur->next;
    }
    return count;
}

void clearQueue() { // Fungsi Menghapus Antrian
    if (isEmpty()) {
        cout << "Antrian Kosong" << endl;
    } else {
        while (front != NULL) {
            dequeueAntrian();
        }
    }
}

void viewQueue() {
  if (isEmpty()) {
    cout << "Antrian Kosong" << endl;
    return;
  }

  cout << "Data Antrian Teller :" << endl;
  Node* cur = front;
  int n = 1;
  while (cur != NULL) {
    cout << n << ". " << cur->data << endl;
    cur = cur->next;
    n++;
  }
  cout << endl;
}


int main() {
    enqueueAntrian("Andi");
    enqueueAntrian("Maya");
    
    viewQueue();
    cout << "Jumlah Antrian = " << countQueue() << endl;
    
    dequeueAntrian();
    viewQueue();
    cout << "Jumlah Antrian = " << countQueue() << endl;
    
    clearQueue();
    viewQueue();
    cout << "Jumlah Antrian = " << countQueue() << endl;
    
    return 0;
}
```

#### Output:

![8U1](https://github.com/JeremyMarcello/Assignment-Praktikum-Algoritma-dan-Struktur-Data/assets/156126843/ceb33183-0b3e-4a46-a013-05d77a97f5a6)

**Kode ini juga mengimplementasikan antrian (queue) untuk mengatur antrian teller di bank, namun menggunakan struktur data linked list. Berikut interpretasi detailnya:**

**Struktur Data:**

* Node: Struktur untuk menyimpan data nasabah (data) dan pointer ke node selanjutnya (next).
* front: Pointer yang menunjuk ke node terdepan dalam antrian (awalnya NULL).
* back: Pointer yang menunjuk ke node belakang dalam antrian (awalnya NULL).

**Fungsi:**

* isFull(): Tidak digunakan pada linked list karena tidak ada batasan maksimum elemen. Selalu mengembalikan false.
* isEmpty(): Memeriksa apakah antrian kosong dengan mengembalikan true jika back bernilai NULL dan false sebaliknya.
* enqueueAntrian(data): Menambahkan data nasabah baru ke antrian.
    * Alokasikan memori untuk node baru (newNode).
    * Isi data nasabah (data) dan set pointer next ke NULL (node terakhir).
    * Jika antrian kosong (isEmpty() bernilai true), set front dan back sama dengan newNode.
    * Jika tidak kosong, set back->next (pointer next dari node belakang) menjadi newNode dan update back menjadi newNode.
* dequeueAntrian(): Menghapus data nasabah terdepan dari antrian.
    * Memeriksa apakah antrian kosong.
        * Jika kosong, tampilkan pesan "Antrian Kosong".
    * Jika tidak kosong, simpan node terdepan sementara di temp.
    * Update front untuk menunjuk ke node selanjutnya.
    * Hapus memori temp.
    * Jika front menjadi NULL setelah penghapusan (artinya antrian kosong), update back menjadi NULL juga.
* countQueue(): Menghitung jumlah data nasabah yang sedang mengantri.
    * Inisialisasi count menjadi 0.
    * Loop dengan pointer cur mulai dari front.
    * Hitung setiap node yang dilewati (count++).
    * Gerakan cur ke node selanjutnya menggunakan cur->next.
    * Kembalikan nilai count.
* clearQueue(): Menghapus semua data nasabah dari antrian.
    * Memeriksa apakah antrian kosong.
        * Jika kosong, tampilkan pesan "Antrian Kosong".
    * Loop menggunakan dequeueAntrian() untuk menghapus elemen antrian sampai kosong.
* viewQueue(): Menampilkan data nasabah yang sedang mengantri.
    * Memeriksa apakah antrian kosong.
        * Jika kosong, tampilkan pesan "Antrian Kosong" dan hentikan fungsi.
    * Cetak judul "Data Antrian Teller".
    * Loop dengan pointer cur mulai dari front.
    * Tampilkan data nasabah dengan format "[nomor urut]. [nama nasabah]".
    * Gerakan cur ke node selanjutnya menggunakan cur->next.
    * Tampilkan baris baru setelah loop.

**Fungsi Utama (main):**

Sama dengan kode sebelumnya, program ini mensimulasikan penggunaan enqueue, dequeue, viewQueue, countQueue, dan clearQueue untuk antrian teller bank.

**Kesimpulan:**

Kode ini menggunakan linked list untuk membuat antrian teller bank yang dinamis (dapat menampung jumlah nasabah yang bervariasi). Fungsi-fungsi yang disediakan memungkinkan operasi dasar untuk mengelola antrian, seperti yang dijelaskan sebelumnya.


### 2. Dari nomor 1 buatlah konsep antri dengan atribut Nama mahasiswa dan NIM Mahasiswa

```C++
#include <iostream>
#include <string>
using namespace std;

struct mahasiswa {
  string nama;
  string nim;
};

struct Node {
    mahasiswa data;
    Node* next;
};

Node* front = NULL;
Node* back = NULL;

bool isFull() { // Pengecekan Antrian Sudah Penuh Atau Tidak
    // Tidak ada batas maksimal
    return false;
}

bool isEmpty() { // Pengecekan Antrian Sudah Kosong Atau Tidak
    if (back == 0) {
        return true;
    } else {
        return false;
    }
}

void enqueueAntrian(mahasiswa data) { // Fungsi Menambahkan Antrian
    Node* newNode = new Node;
    newNode->data = data;
    newNode->next = NULL;
    if (isEmpty()) {
            front = back = newNode;
    } else {
            back->next = newNode;
            back = newNode;
    }
}

void dequeueAntrian() { // Fungsi Mengurangi Antrian
    if (isEmpty()) {
        cout << "Antrian Kosong" << endl;
    } else {
        Node* temp = front;
        front = front->next;
        delete temp;
        if (front == NULL) {
            back = NULL;
        }
    }
}

int countQueue() { // Fungsi Menghitung Banyak Antrian
    int count = 0;
    Node* cur = front;
    while (cur != NULL) {
        count++;
        cur = cur->next;
    }
    return count;
}

void clearQueue() { // Fungsi Menghapus Antrian
    if (isEmpty()) {
        cout << "Antrian Kosong" << endl;
    } else {
        while (front != NULL) {
            dequeueAntrian();
        }
    }
}

void viewQueue() {
  if (isEmpty()) {
    cout << "Antrian Kosong" << endl;
    return;
  }

  cout << "Data Antrian Teller :" << endl;
  Node* cur = front;
  int n = 1;
  while (cur != NULL) {
    cout << n << ". " << "Nama : " << cur->data.nama << ", NIM : " << cur->data.nim << endl;
    cur = cur->next;
    n++;
  }
  cout << endl;
}


int main() {
    enqueueAntrian({"Andi", "2311110069"});
    enqueueAntrian({"Maya", "2311110099"});
    
    viewQueue();
    cout << "Jumlah Antrian = " << countQueue() << endl;
    
    dequeueAntrian();
    viewQueue();
    cout << "Jumlah Antrian = " << countQueue() << endl;
    
    clearQueue();
    viewQueue();
    cout << "Jumlah Antrian = " << countQueue() << endl;
    
    return 0;
}
```

#### Output:

![8U2](https://github.com/JeremyMarcello/Assignment-Praktikum-Algoritma-dan-Struktur-Data/assets/156126843/d8432142-6fe8-4aae-951b-5b86eee1d41c)

**Kode ini mengimplementasikan antrian (queue) untuk mengatur antrian mahasiswa menggunakan linked list. Berikut interpretasi detailnya:**

**Struktur Data:**

* mahasiswa: Struktur untuk menyimpan data mahasiswa (nama dan NIM).
* Node: Struktur untuk menyimpan data mahasiswa (data) dan pointer ke node selanjutnya (next).
* front: Pointer yang menunjuk ke node terdepan dalam antrian (awalnya NULL).
* back: Pointer yang menunjuk ke node belakang dalam antrian (awalnya NULL).

**Fungsi:**

Sama seperti kode antrian teller bank sebelumnya, fungsi-fungsi seperti isFull(), isEmpty(), enqueueAntrian(), dequeueAntrian(), countQueue(), clearQueue(), dan viewQueue() memiliki fungsi yang serupa dengan penyesuaian pada tipe data yang disimpan (menggunakan struktur mahasiswa).

* Perbedaan pada enqueueAntrian() dan viewQueue():
    *enqueueAntrian(): Menerima parameter mahasiswa yang berisi nama dan nim mahasiswa baru.
    *viewQueue(): Mencetak data mahasiswa dengan format "[nomor urut]. Nama : [nama mahasiswa], NIM : [NIM mahasiswa]".

**Fungsi Utama (main):**

Program ini mensimulasikan penggunaan enqueue, dequeue, viewQueue, dan countQueue untuk antrian mahasiswa.

**Kesimpulan:**

Kode ini memodifikasi kode antrian teller bank sebelumnya untuk  mengelola antrian mahasiswa.  Linked list digunakan untuk membuat antrian yang dinamis dan fungsi-fungsi yang disediakan memungkinkan operasi dasar untuk menambahkan, menghapus, melihat, dan menghitung elemen dalam antrian mahasiswa.


## Kesimpulan
Dalam C++, queue adalah struktur data fundamental yang mematuhi prinsip First In, First Out (FIFO). Elemen ditambahkan di bagian belakang (akhir) dan dihapus dari bagian depan (beginning). Karakteristik ini membuat baris yang ideal untuk skenario di mana item harus diproses dalam urutan mereka ditambahkan.

Implementasi queue di C++ dimfasilitasi oleh std::queue yang ditemukan dalam header <queue>. Ini menawarkan fungsi anggota seperti push(), pop(), front(), back(), empty(), dan size() untuk memungkinkan operasi FIFO yang efisien.

## Referensi

[1] Goodrich, M. T., Tamassia, R., & Goldwasser, M. H. (2021). Data Structures and Algorithms in C++. Upper Saddle River, NJ: Pearson.
