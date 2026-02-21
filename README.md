# 🌙 Jadwal Imsakiyah API

A simple API wrapper to get prayer and imsakiyah schedules based on cities in Indonesia. Built with Hono.js + Bun + TypeScript

## 🛠️ Tech Stack

- [Bun](https://bun.sh/) - JavaScript runtime & package manager
- [Hono.js](https://hono.dev/) - Lightweight web framework
- TypeScript
- [MyQuran API v3](https://api.myquran.com) - Prayer schedule data source

## 🚀 Installation & Running

### Prerequisites
- Latest version of Bun

### Installation
```bash
# Clone repository
git clone https://github.com/IMPHNEN/Ramadhan-Code-Fest-2026.git
cd Ramadhan-Code-Fest-2026/jadwal-imsakiyah

# Install dependencies
bun install

# Run development server
bun run dev
```

Server will run at `http://localhost:3000`

## 📡 Endpoints

### 1. Welcome
```
GET /
```
**Response:**
```json
{
  "success": true,
  "message": "Selamat datang di API Jadwal Imsakiyah",
  "endpoints": {
    "list_kota": "GET /kota",
    "list_kota_by_keyword": "GET /kota?keyword={keyword}",
    "jadwal_hari_ini": "GET /jadwal/:kotaId",
    "jadwal_by_tanggal": "GET /jadwal/{kotaId}/{tahun}/{bulan}/{hari}"
  }
}
```

---

### 2. List All Cities
```
GET /kota
```
**Response:**
```json
{
  "success": true,
  "message": "Berhasil mengambil list kota",
  "data": [
    {
      "id": "c4ca4238a0b923820dcc509a6f75849b",
      "lokasi": "KAB. ACEH BARAT"
    }
  ]
}
```

---

### 3. Search City by Keyword
```
GET /kota?keyword=bandung
```
**Response:**
```json
{
  "success": true,
  "message": "Berhasil mengambil list kota",
  "data": [
    {
      "id": "fa7cdfad1a5aaf8370ebeda47a1ff1c3",
      "lokasi": "KAB. BANDUNG BARAT"
    }
  ]
}
```

---

### 4. Today's Prayer Schedule
```
GET /jadwal/:kotaId
```
**Example:**
```
GET /jadwal/fa7cdfad1a5aaf8370ebeda47a1ff1c3
```
**Response:**
```json
{
  "success": true,
  "message": "Berhasil mengambil jadwal hari ini",
  "data": {
    "tanggal": "Sabtu, 21/02/2026",
    "kota": "KAB. BANDUNG BARAT",
    "jadwal": {
      "imsak": "04:28",
      "subuh": "04:38",
      "terbit": "05:48",
      "dhuha": "06:19",
      "dzuhur": "12:07",
      "ashar": "15:15",
      "maghrib": "18:19",
      "isya": "19:25"
    }
  }
}
```

---

### 5. Prayer Schedule by Date
```
GET /jadwal/:kotaId/:tahun/:bulan/:hari
```
**Example:**
```
GET /jadwal/fa7cdfad1a5aaf8370ebeda47a1ff1c3/2026/03/01
```
**Response:**
```json
{
  "success": true,
  "message": "Berhasil mengambil jadwal",
  "data": {
    "tanggal": "Ahad, 01/03/2026",
    "kota": "KAB. BANDUNG BARAT",
    "jadwal": {
      "imsak": "04:27",
      "subuh": "04:37",
      "terbit": "05:47",
      "dhuha": "06:18",
      "dzuhur": "12:06",
      "ashar": "15:14",
      "maghrib": "18:18",
      "isya": "19:24"
    }
  }
}
```

## 📁 Project Structure
```
jadwal-imsakiyah/
├── src/
│   ├── index.ts
│   ├── routes/
│   │   └── imsakiyah.ts
│   ├── services/
│   │   └── imsakiyah.ts
│   └── types/
│       └── imsakiyah.ts
├── README.md
├── package.json
└── tsconfig.json
```
