# Mobile JKN Queue Provider

**Mobile JKN Queue Provider** adalah aplikasi layanan berbasis HTTP yang menyediakan data antrian pendaftaran kunjungan
rawat jalan dan rencana operasi di Klinik Utama Mata Silampari Sriwijaya Eye Centre Lubuklinggau. Pengembangan aplikasi
ini bertujuan untuk melayani _request_ dari aplikasi Mobile JKN milik BPJS pada opsi pendaftaran secara online. Mobile
JKN merupakan aplikasi yang di-desain oleh BPJS Kesehatan untuk memberikan kemudahan akses dan kenyamanan bagi peserta
JKN-KIS. Aplikasi ini lengkap memuat informasi seputar Program JKN-KIS, salah satunya adalah sistem pendaftaran online.

## API Specs

Aplikasi ini menyediakan beberapa _endpoint_ sesuai
spesifikasi [sistem antrean Mobile JKN](https://docs.google.com/spreadsheets/d/1AL8bvvrPXRerKI8gT-o60UugcVwXCER-PjqKmQeLpKo).

### Base URL: `http://jkn.ssec.co.id`

### Mengambil Token Autentikasi

- URL: `/auth`

- Method: **POST**

- Request body:

```json
{
    "username": "string",
    "password": "string"
}
```

- Response body:

```json
{
    "response": {
        "token": "Bearer token"
    },
    "metadata": {
        "message": "string",
        "code": "number"
    }
}
```

### Mengambil Nomor Antrean

- URL: `/lines`

- Method: **POST**

- Request header:
    * x-token: [Token Autentikasi](#mengambil-token-autentikasi)

- Request body:

```json
{
    "nomorkartu": "string",
    "nik": "string",
    "notelp": "string",
    "tanggalperiksa": "date",
    "kodepoli": "string",
    "nomorreferensi": "string",
    "jenisreferensi": "number",
    "jenisrequest": "number",
    "polieksekutif": "number"
}
```

- Response body:

```json
{
    "response": {
        "nomorantrean" : "string",
        "kodebooking" : "string",
        "jenisantrean" : "numbner",
        "estimasidilayani" : "timestamp",
        "namapoli" : "string",
        "namadokter" : "string"
    },
    "metadata": {
        "message": "string",
        "code": "number"
    }
}
```

### Mengambil Rekam Antrean

- URL: `/recap`

- Method: **POST**

- Request header:
    * x-token: [Token Autentikasi](#mengambil-token-autentikasi)

- Request body:

```json
{
    "tanggalperiksa": "date",
    "kodepoli": "string",
    "polieksekutif": "number"
}
```

- Response body:

```json
{
    "response": {
        "namapoli" : "string",
        "totalantrean" : "number",
        "jumlahterlayani" : "number",
        "lastupdate" : "timestamp"
    },
    "metadata": {
        "message": "string",
        "code": "number"
    }
}
```

### Mengambil Daftar Kode Booking Operasi

- URL: `/surgery-booking`

- Method: **POST**

- Request header:
    * x-token: [Token Autentikasi](#mengambil-token-autentikasi)

- Request body:

```json
{
    "nopeserta": "string"
}
```

- Response body:

```json
{
    "response": {
        "list" : [{
             "kodebooking": "string",
             "tanggaloperasi": "date",
             "jenistindakan": "string",
             "kodepoli": "string",
             "namapoli": "string",
             "terlaksana": "number"
        }]
    },
    "metadata": {
        "message": "string",
        "code": "number"
    }
}
```

### Mengambil Daftar Jadwal Operasi

- URL: `/surgery-schedule`

- Method: **POST**

- Request header:
    * x-token: [Token Autentikasi](#mengambil-token-autentikasi)

- Request body:

```json
{
    "tanggalawal": "date",
    "tanggalakhir": "date"
}
```

- Response body:

```json
{
    "response": {
        "list" : [{
             "kodebooking": "string",
             "tanggaloperasi": "date",
             "jenistindakan": "string",
             "kodepoli": "string",
             "namapoli": "string",
             "terlaksana": "number",
             "nopeserta": "string",
             "lastupdate": "timestamp" 
        }]
    },
    "metadata": {
        "message": "string",
        "code": "number"
    }
}
```

### Referensi Kode Poliklinik

| Kode | Nama |
| --- | --- |
| 142 | Onkologi Mata |
| MAT | Mata |
