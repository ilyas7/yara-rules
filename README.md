# wscript_malware.yar

## Deskripsi

Mendeteksi malware VBScript yang di-obfuskasi (disamarkan) menggunakan fungsi **Tinkturernes** dan decoder ekstraksi string **Sejrsskjorterne**. 

Malware ini menggunakan `WScript.Shell` untuk:
- Akses sistem
- Operasi registry
- Eksekusi muatan (payload) PowerShell yang disisipkan

Aturan ini mengidentifikasi kombinasi unik dari fungsi-fungsi dan pola decoder yang digunakan dalam keluarga malware spesifik ini.

## Indikator Utama

| Indikator | Deskripsi |
|---|---|
| `Tinkturernes` | Fungsi utama malware |
| `Sejrsskjorterne` | Fungsi decoder string (ekstraksi setiap 5 karakter) |
| `WScript.Shell` | Objek untuk akses sistem dan registry |
| `Frustrerende` | Objek WScript.Shell yang digunakan |
| `execute` | Perintah untuk menjalankan fungsi |

## Cara Penggunaan

```bash
# Scan satu file
yara wscript_malware.yar file.vbs

# Scan seluruh direktori
yara -r wscript_malware.yar /path/to/directory/

# Tampilkan detail string yang cocok
yara -s wscript_malware.yar file.vbs
