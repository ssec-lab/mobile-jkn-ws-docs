# Mobile JKN Web Service

**Mobile JKN Web Service** adalah aplikasi layanan berbasis HTTP yang menyediakan data antrian pendaftaran kunjungan
rawat jalan dan rencana operasi di Klinik Utama Mata Silampari Sriwijaya Eye Centre Lubuklinggau. Pengembangan aplikasi
ini bertujuan untuk melayani _request_ dari aplikasi Mobile JKN milik BPJS pada opsi pendaftaran secara online. Mobile
JKN merupakan aplikasi yang di-desain oleh BPJS Kesehatan untuk memberikan kemudahan akses dan kenyamanan bagi peserta
JKN-KIS. Aplikasi ini lengkap memuat informasi seputar Program JKN-KIS, salah satunya adalah sistem pendaftaran online.

## API Specs

Aplikasi ini menyediakan beberapa _endpoint_ sesuai
spesifikasi [sistem antrean Mobile JKN](https://dvlp.bpjs-kesehatan.go.id:8888/trust-mark/portal.html).

### Base URL: `http://mjkn.ssec.co.id`

- `/auth/token` - Mendapakan token
- `/antre/buat` - Ambil antrean
- `/antre/status` - Cek status antrean
- `/antre/sisa` - Cek sisa antrean peserta
- `/antre/batal` - Batal antrean
- `/antre/checkin` - Check in
- `/antre/pasien` - Kirim data pasien baru
- `/operasi/faskes` - Jadwal operasi faskes
- `/operasi/pasien` - Jadwal operasi pasien
