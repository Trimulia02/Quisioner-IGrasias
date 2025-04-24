# Quisioner-IGrasias
# Bookmarklet Survei Dosen - Pilih "Puas" Otomatis

Skrip ini adalah **bookmarklet JavaScript** yang secara otomatis:
- Memilih jawaban **"Puas"** di setiap pertanyaan survei berdasarkan elemen `<div class="answerlist1">Puas</div>`
- Mengisi semua kolom komentar (textarea) dengan teks **"sudah bagus"**

## 📌 Cara Penggunaan

1. **Salin seluruh kode JavaScript di bawah ini:**

    ```javascript
    javascript:(function(){
        document.querySelectorAll(".answerlist1").forEach(div => {
            if (div.textContent.trim() === "Puas") {
                // Coba cari input radio sebagai sibling atau di parent-nya
                let radio = div.previousElementSibling?.type === "radio" ? div.previousElementSibling :
                            div.nextElementSibling?.type === "radio" ? div.nextElementSibling :
                            div.parentElement.querySelector('input[type="radio"]');
                if (radio) radio.checked = true;
            }
        });

        // Isi semua kolom komentar (textarea) dengan "sudah bagus"
        document.querySelectorAll('textarea').forEach(text => {
            text.value = "sudah bagus";
        });
    })();
    ```

2. **Buat Bookmark Baru** di browser kamu.
   - Klik kanan di bookmark bar > *Add Page* (atau *Bookmark this page*).
   - Isi nama bebas, misalnya: `Auto Survey`
   - Di kolom URL, paste kode JavaScript di atas.

3. **Buka halaman survei dosen** di browser.

4. Klik bookmark `Auto Survey` yang kamu buat tadi.

5. Semua opsi "Puas" akan otomatis terpilih dan komentar akan terisi `"sudah bagus"`.

## ⚠️ Catatan

- Pastikan form survei menggunakan struktur HTML seperti:
    ```html
    <input type="radio" name="...">
    <div class="answerlist1">Puas</div>
    ```
- Jika tidak bekerja, kemungkinan struktur HTML berbeda. Silakan periksa dengan fitur Inspect Element pada browser.

## 🛠️ Lisensi

Skrip ini disediakan bebas untuk digunakan dan dimodifikasi sesuai kebutuhan pribadi.
