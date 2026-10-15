# ⚡ Mini Step-Up Circuit Diagram

Oleh: **Dicky Yased Arya Muyla**

Proyek ini adalah desain rangkaian **Mini Step-Up Regulator (Boost Converter)** menggunakan IC **B628** (sering tertulis sebagai DB628 / MT3608). Rangkaian ini mampu menaikkan tegangan input rendah menjadi tegangan output yang lebih tinggi secara stabil dengan memanfaatkan *resistor divider* atau modulasi PWM.

---

## 📌 Fitur & Spesifikasi Utama

* **IC Utama:** B628 / DB628 (High-Efficiency Step-Up DC-DC Converter)
* **Rentang Input:** 1V – 22V DC
* **Tegangan Output:** *Fixed* (Ditetapkan menggunakan *resistor divider*, contoh konfigurasi: **12.14V**)
* **Tegangan Referensi (Vref):** 0.6V (Dapat disesuaikan dengan kebutuhan variabel Anda)

---

## 🖼️ Tampilan Proyek

Berikut adalah visualisasi fisik atau tata letak komponen dari proyek *Mini Step-Up* ini:

![Screenshot Project](a1.png)

---

## 🧮 Rumus & Cara Perhitungan Output

Tegangan output pada rangkaian ini dapat diatur melalui dua metode: menggunakan kombinasi resistor statis (*resistor divider*) atau dikendalikan secara dinamis menggunakan sinyal PWM.

### 1. Menggunakan Resistor Divider (Statis)
Tegangan output standar ditentukan oleh dua buah resistor umpan balik ($R_1$ dan $R_2$) yang terhubung ke pin **FB (Feedback)** berdasarkan rumus berikut:

$$V_{out} = V_{ref} \times \left(1 + \frac{R_1}{R_2}\right)$$

*Jika $V_{ref} = 0.6V$, Anda tinggal menyesuaikan nilai $R_1$ dan $R_2$ untuk mendapatkan output yang diinginkan (misal: 12.14V).*

### 2. Menggunakan Sinyal PWM (Dinamis)
Untuk mengontrol atau mengubah tegangan output melalui mikrokontroler (seperti Arduino/ESP32), Anda bisa menyuntikkan sinyal **PWM (Pulse Width Modulation)** ke jalur *feedback* melalui sebuah resistor tambahan ($R_{pwm}$) dan filter RC.

* **Prinsip Kerja:** Mengubah *Duty Cycle* PWM akan mengubah tegangan rata-back pada pin FB. Semakin tinggi *Duty Cycle* (tegangan PWM naik), maka IC akan mendeteksi bahwa output sudah "cukup tinggi" sehingga IC akan **menurunkan** tegangan output utama, dan sebaliknya.

---

## 🔌 Skema Diagram Rangkaian

Gunakan skema di bawah ini sebagai panduan utama untuk proses perakitan komponen (*soldering*) atau pembuatan Jalur PCB:

![Skema Diagram](design1.png)

---

## 🛠️ Komponen yang Dibutuhkan
* 1x IC Step-Up (B628 / DB628)
* 1x Induktor (Ukurannya disesuaikan dengan target arus)
* 1x Dioda Schottky (Untuk *switching* cepat)
* Kapasitor Input & Output (Filter tegangan)
* Resistor Divider ($R_1$, $R_2$, dan $R_{pwm}$ jika memakai PWM)
