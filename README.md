# Survey Parkiran — index.html (+CSS jadi satu), app.js, code.gs

CSS sekarang sudah digabung langsung ke dalam `index.html` (di dalam tag `<style>`),
jadi kamu **tidak perlu bikin file `style` terpisah lagi**. Ini bikin pemasangan
lebih sederhana dan lebih kecil kemungkinan error karena file kurang lengkap.

Sisa 1 file yang masih perlu trik "include" adalah `app.js`, karena Apps Script
tidak punya tipe file `.js` asli — jadi isinya tetap ditempel ke file HTML
bernama `app`, dan dipanggil dari `index.html` lewat `<?!= include('app'); ?>`.

## Langkah Instalasi

### 1. Buat Google Sheet baru
Buka [sheets.new](https://sheets.new), beri nama misalnya **"Survey Parkiran"**.

### 2. Buka Apps Script
Menu **Extensions → Apps Script**.

### 3. Buat & isi file-nya (total 3 file di editor)

| File di paket ini | Buat di Apps Script sebagai | Isi yang ditempel |
|---|---|---|
| `code.gs` | File **Script** bernama `Code` (bawaan) | tempel apa adanya |
| `index.html` | File **HTML** bernama `index` | tempel apa adanya (CSS sudah ikut di dalamnya) |
| `app.js` | File **HTML** bernama `app` | tempel **di dalam** `<script>` ... `</script>` |

Cara bikin file `app`:
1. Klik **+** di sebelah "Files" → **HTML** → beri nama `app`.
2. Isinya jadi begini:
   ```html
   <script>
   /* ... tempel seluruh isi app.js di sini ... */
   </script>
   ```

Simpan semua (Ctrl+S / Cmd+S).

### 4. Siapkan Sheet-nya
Pilih fungsi **`initializeSheet`** di dropdown atas editor → klik **Run (▶)**.
Izinkan akses (Review permissions → akun kamu → Advanced → Go to project (unsafe) → Allow).
Cek Sheet-mu, harus muncul sheet **"Responses"** dengan header.

### 5. Deploy sebagai Web App
**Deploy → New deployment** → ikon gerigi ⚙️ → **Web app**.
- Execute as: **Me**
- Who has access: **Anyone**

Klik **Deploy**, copy **Web app URL**-nya.

### 6. Pakai
Satu URL, satu halaman, 2 tab:
- **"📝 Isi Survey"** → bagikan ke peserta
- **"📊 Dashboard"** → kamu pantau hasilnya di sini

### 7. Setiap kali edit kode
**Deploy → Manage deployments → ✏️ → Version: New version → Deploy** (URL tetap sama).

## Troubleshooting singkat
- **Halaman blank / error "include is not defined"** → pastikan file HTML bernama persis `app` (bukan `App` atau `app.js`), dan `code.gs` masih punya fungsi `include()`.
- **"Sheet belum siap"** saat submit → jalankan `initializeSheet()` lagi.
- **Dashboard kosong** → wajar kalau belum ada data masuk sama sekali.
