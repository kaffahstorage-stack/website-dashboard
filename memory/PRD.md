# Momentum AI — PRD

## Original Problem Statement
Single-file HTML dashboard "Momentum AI" untuk menerima & menampilkan data momentum dari TradingView (nanti via Firebase Firestore). Semua kode HTML + CSS + JS dalam satu file. Tema terang, minimalis, responsive, tanpa framework.

## Architecture
- File tunggal: `/app/index.html`
- HTML + CSS + JavaScript murni (tanpa framework)
- Lucide Icons via CDN untuk ikon
- Firebase config = placeholder (siap diisi user nanti)
- Data source: dummy (12 entri) untuk demo; siap diganti Firestore realtime listener

## Core Requirements (Static)
- Header: brand "Momentum AI" + status scanner Online
- 5 kartu info: Momentum Terakhir, Range, Pair, Timeframe, Waktu
- Statistik harian: Total Signal, Bullish, Bearish
- Toolbar: Search + tombol Refresh
- Tabel History: No, Waktu, Pair, Direction, Range, Status (min 10 data)
- Struktur data: id, pair, timeframe, direction, range, open, high, low, close, time, status
- Firebase template functions: `connectFirebase()`, `listenMomentum()`, `addMomentum()`

## Implemented (2026-01)
- [x] Header + logo + status scanner online (animasi pulse hijau)
- [x] 5 kartu informasi terhubung ke data terbaru
- [x] Statistik Total/Bullish/Bearish otomatis dihitung dari data hari ini
- [x] Toolbar dengan search realtime & tombol refresh
- [x] Tabel history 12 entri dummy, terurut terbaru di atas
- [x] Search filter multi-field (pair, direction, status, timeframe, time)
- [x] Refresh: regenerate data dummy
- [x] Firebase config placeholder + template functions siap dipakai
- [x] Responsive (desktop, tablet, mobile)
- [x] Jam pada kartu "Waktu" ter-update per detik

## Backlog (P1/P2)
- P1: Integrasi Firebase Firestore asli (ganti config + aktifkan `listenMomentum`)
- P1: Webhook receiver dari TradingView (butuh backend/Cloud Function)
- P2: Push Notification (Web Push / FCM)
- P2: Telegram / Discord notifier
- P2: Grafik OHLC / distribusi Bullish vs Bearish
- P2: Statistik lanjutan (win-rate per pair, per timeframe)
- P2: Login Admin (Firebase Auth)
- P2: Filter lanjutan (per pair, per timeframe, per range tanggal)

## Files
- `/app/index.html` — seluruh aplikasi
