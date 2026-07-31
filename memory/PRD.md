# Momentum AI — PRD

## Original Problem Statement
Single-file HTML dashboard "Momentum AI" untuk menampilkan data momentum TradingView via Firebase Firestore realtime. Semua kode HTML + CSS + JS dalam satu file, tema terang minimalis, tanpa framework.

## Architecture
- File tunggal: `/app/index.html`
- HTML + CSS + JS murni + Firebase JS SDK v10 (ESM CDN)
- Firestore realtime via `onSnapshot`
- Koleksi: `momentum_signals`, urut `time desc`, limit 100
- Tidak ada backend / build tool

## Core Requirements
- Header + status scanner (Online/Belum Terhubung)
- 5 kartu info: Momentum Terakhir, Range, Pair, Timeframe, Waktu
- Statistik harian: Total, Bullish, Bearish (auto dihitung dari data hari ini)
- Toolbar: search realtime + tombol Refresh
- Tabel history (No, Waktu, Pair, Direction, Range, Status)
- Firebase: `connectFirebase()`, `listenMomentum()`, `addMomentum()`

## Implemented
- [x] (v1) UI dashboard lengkap, tema terang, responsif
- [x] (v1) Kartu info + statistik + tabel + search + refresh
- [x] (v2, 2026-01) Integrasi Firebase Firestore REALTIME via `onSnapshot`
  - Query `orderBy("time","desc")` + `limit(100)` ke koleksi `momentum_signals`
  - Dummy data dihilangkan sepenuhnya
  - Auto-update kartu momentum terakhir, statistik, dan tabel ketika data baru masuk
  - Animasi highlight baris baru sekali muncul
  - Deteksi placeholder config → banner peringatan + status "Belum Terhubung"
  - `addMomentum(item)` helper dengan idempotent `setDoc` bila `id` diisi

## How to Activate Firebase
1. Buka `/app/index.html`
2. Isi variabel `firebaseConfig` (bagian B) dengan konfigurasi dari Firebase Console
3. Muat ulang halaman → dashboard otomatis menerima data realtime dari `momentum_signals`

## Backlog (Ditunda per instruksi user)
- Webhook TradingView (server-side)
- Push Notification / FCM
- Telegram / Discord notifier
- Grafik statistik
- Login Admin (Firebase Auth)

## Files
- `/app/index.html` — seluruh aplikasi
