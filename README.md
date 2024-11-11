# Tugas 1: Aplikasi Cek Nomor Genap/Ganjil

### Pembuat
- **Nama**: Ferdhyan Dwi Rangga Saputra
- **NPM**: 2210010171

---

## 1. Deskripsi Program
Aplikasi ini memungkinkan pengguna untuk:
- Memasukkan sebuah angka pada TextField.
- Menekan tombol **Cek** untuk memverifikasi apakah angka tersebut genap atau ganjil.
- Hasil pengecekan ditampilkan pada JLabel di aplikasi.

## 2. Komponen GUI
- **JFrame**: Window utama aplikasi.
- **JPanel**: Panel untuk menampung komponen.
- **JLabel**: Menampilkan hasil apakah angka genap atau ganjil.
- **JTextField**: Input untuk memasukkan angka yang akan diperiksa.
- **JButton**: Tombol untuk melakukan pemeriksaan angka.

## 3. Logika Program
- Menggunakan struktur kondisional (if-else) untuk memeriksa apakah angka genap atau ganjil.
- Validasi input untuk memastikan pengguna hanya memasukkan angka.

## 4. Events
Menggunakan **ActionListener** dan **KeyAdapter** untuk mempermudah interaksi pengguna:

### A. Tombol Cek
Menampilkan hasil pemeriksaan angka (genap atau ganjil) setelah memvalidasi input.

```java
private void btnCekActionPerformed(java.awt.event.ActionEvent evt) {                                       
        String input = txtGanjilGenap.getText();
        if (input.isEmpty()) {
            JOptionPane.showMessageDialog(this, "Input tidak boleh kosong!", "Error", JOptionPane.ERROR_MESSAGE);
            return;
        }

        try {
            int angka = Integer.parseInt(input);
            String hasil = "";

            if (angka % 2 == 0) {
                hasil += "Angka " + angka + " adalah Genap.\n";
            } else {
                hasil += "Angka " + angka + " adalah Ganjil.\n";
            }

            if (isPrime(angka)) {
                hasil += "Angka " + angka + " adalah bilangan prima.";
            } else {
                hasil += "Angka " + angka + " bukan bilangan prima.";
            }

            JOptionPane.showMessageDialog(this, hasil, "Hasil", JOptionPane.INFORMATION_MESSAGE);
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Input harus berupa angka!", "Error", JOptionPane.ERROR_MESSAGE);
        }
    } 
```
### B. Key Adapter untuk membatasi input hanya angka
```java
txtGanjilGenap.addKeyListener(new KeyAdapter() {
        @Override
        public void keyTyped(KeyEvent e) {
            char c = e.getKeyChar();
            if (!Character.isDigit(c) && c != KeyEvent.VK_BACK_SPACE) {
                e.consume(); // Membatasi input hanya angka
            }
        }
    });   
```

## 5. Variasi
Aplikasi ini memiliki variasi tambahan berikut:
### A. Pemeriksaan Bilangan Prima
```java
if (isPrime(angka)) {
                hasil += "Angka " + angka + " adalah bilangan prima.";
            } else {
                hasil += "Angka " + angka + " bukan bilangan prima.";
            }

private boolean isPrime(int n) {
        if (n <= 1) return false;
        if (n <= 3) return true;
        if (n % 2 == 0 || n % 3 == 0) return false;
        for (int i = 5; i * i <= n; i += 6) {
            if (n % i == 0 || n % (i + 2) == 0) return false;
        }
        return true;
    }
```
### B. JOptionPane
Menampilkan pesan hasil dan pesan error menggunakan JOptionPane.
```java
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Input harus berupa angka!", "Error", JOptionPane.ERROR_MESSAGE);
        }
```
### C. FocusListener
Menghapus isi JTextField saat mendapatkan fokus.
```java
txtGanjilGenap.addFocusListener(new FocusAdapter() {
        @Override
        public void focusGained(FocusEvent e) {
            txtGanjilGenap.setText(""); // Membersihkan input saat mendapatkan fokus
        }
    });
```
## 6. Tampilan Saat di Run :

  ![Screenshot 2024-11-08 001302](https://github.com/user-attachments/assets/cc38a883-e64f-4a1f-aaee-1a0c607d1abd)

## Indikator Penilaian:

| No  | Komponen         |  Persentase  |
| :-: | --------------   |   :-----:    |
|  1  | Komponen GUI     |    20    |
|  2  | Logika Program   |    20    |
|  3  | Events           |    15    |
|  4  | Kesesuaian UI    |    15    |
|  5  | Memenuhi Variasi |    30    |
|     | TOTAL        | 100 |
