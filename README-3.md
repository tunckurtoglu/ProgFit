# ProgFit — Akıllı Antrenman Takip Uygulaması

> **🔒 Bu repo proje tanıtımı içindir. Kaynak koda erişim için lütfen iletişime geçin.**

ProgFit, ağırlık antrenmanı yapan kişiler için tasarlanmış, bilim temelli bir antrenman ve gelişim takip uygulamasıdır. Her hareket için kişiselleştirilmiş hedef ağırlıklar hesaplar, ilerlemeyi haftalar boyunca takip eder ve kullanıcının seviyesine göre gerçekçi öneriler sunar.

---

## 📱 Uygulama Hakkında

ProgFit, "kaç kilo kaldırmalıyım?" sorusuna bilimsel bir cevap veren ve haftalık gelişimi görselleştiren mobil bir uygulamadır. Kullanıcının **boy, kilo, yaş, cinsiyet ve vücut yağ oranına** göre her hareket için bireysel hedef ağırlık ve potansiyel kapasite hesaplar.

### Çözdüğü Problem

Çoğu antrenman uygulaması yalnızca yapılan setleri kaydeder. ProgFit ise:
- Kullanıcının her hareket için **olması gereken ağırlığı** hesaplar (Strength Level 2024 verilerine dayalı)
- Hareket bazlı **boy ve yaş düzeltmesi** uygular (örn. uzun boylu biri için deadlift hedefi farklıdır)
- **Salon-uyumlu ağırlık yuvarlama** yapar (Dumbbell/Barbell 2.5 kg, Cable/Machine 5 kg)
- Yardım alınarak yapılan hareketlerde (Assisted Pull-Up gibi) hedef "0 kg'a inmek" olarak hesaplanır
- Bodyweight hareketlerde (Pull-Up, Push-Ups, Plank vb.) tekrar/süre artışını takip eder

---

## ✨ Özellikler

### 🏋️ Antrenman Yönetimi
- **6 günlük haftalık program** oluşturma — her gün için ayrı egzersiz listesi
- **Sürükle-bırak** ile gün sıralaması değiştirme
- **90+ egzersiz** kütüphanesi — 9 ana kas grubunda (Göğüs, Sırt, Omuz, Biceps, Triceps, Bacak/Kalça, Karın, Bel, Kardiyo)
- Her hareket için **animasyonlu GIF** görseli, doğru form gösterimi
- Her hareket için **birincil ve ikincil kas grubu** bilgisi
- Her hareket için **3 madde halinde profesyonel ipuçları**

### ⏱️ Aktif Antrenman Modu
- **Set bazlı tamamlama** sistemi — checkbox ile teker teker işaretleme
- **Her set için ağırlık girişi** (kg veya lbs)
- **Otomatik dinlenme süresi sayacı** — set sonrası geri sayım
- **Antrenman süresi sayacı** — antrenman boyunca toplam süre takibi
- **Kardiyo egzersizleri** için süre + hız + mesafe + hacim hesabı
- **Tamamlanma efektleri** — konfeti animasyonu, bildirim sesi

### 📊 Gelişim Takibi (Progress)
- Her hareket için **haftalık ağırlık grafiği**
- **Kişiselleştirilmiş hedef ağırlık** hesabı:
  - Bilimsel coefficient'lar (Strength Level 2024 verisine dayalı)
  - Boy düzeltmesi (Press hareketleri için <170 cm: +%5, >185 cm: -%5; Squat için ters; Deadlift için farklı eğri)
  - Yaş düzeltmesi (40 yaş üstü: yıl başına -%0.5, max -%20)
- **Potansiyel kapasite** göstergesi (hedefin üzerinde +1 step)
- **Kas grubuna göre filtreleme**
- **Reverse hareketler** için özel hedef hesabı (yardım azaltma)

### 📏 Vücut Ölçüm Takibi (Body)
- **Vücut yağ oranı hesaplama** (US Navy formülü — boy, bel, boyun, kalça)
- **Yağ kütlesi, yağsız kütle, kas kütlesi** hesabı
- **Kategori değerlendirmesi** — Sporcu / Fit / Ortalama / Yüksek (cinsiyet bazlı)
- **Geçmiş ölçümler listesi** — yatay kart şeklinde tarih, yağ oranı, kas kütlesi, bir önceki ölçüme göre değişim
- **Metrik / US (lbs/inch) birim sistemi**

### 👨‍💼 Online Koçluk (PRO)
- Kullanıcının ölçüleri, hedefi ve deneyimine göre **kişiselleştirilmiş program talebi**
- **PDF rapor** olarak e-posta gönderimi (10 dakika içinde)
- Hedef seçimi (Yağ yakımı / Kas kazanımı)
- Antrenman geçmişi (0-3 ay → 2+ yıl)
- Haftalık antrenman günü tercihi (1-6)

### 🌍 3 Dil Desteği
- **Türkçe** (varsayılan)
- **İngilizce**
- **Rusça**
- Tüm egzersiz açıklamaları, kas isimleri ve kategori isimleri 3 dilde

### 🔐 PRO Üyelik Sistemi
- **In-app purchase** entegrasyonu (RevenueCat)
- Aylık ve yıllık abonelik
- Ücretsiz katmanda temel özellikler, PRO'da Body ve Coach ekranları

---

## 🛠️ Teknoloji Yığını

### Mobile Frontend
- **React Native** + **Expo SDK** — iOS ve Android tek kod tabanı
- **Expo Router** — file-based routing
- **TypeScript** — tip güvenliği
- **React Hooks** — useState, useRef, useEffect, useCallback, useFocusEffect

### State Management & Data
- **React State Stores** — özel pub-sub pattern (`completedDaysStore`, `exerciseCacheStore`, `settingsStore`)
- **Optimistic UI updates** — kullanıcı etkileşimi anında ekrana yansır

### Backend & Database
- **Supabase** (PostgreSQL + Realtime + Auth)
- **Row Level Security** — kullanıcı bazlı veri izolasyonu
- **Supabase Edge Functions** — server-side iş mantığı (e-posta gönderimi vb.)
- **Supabase Auth** — Google, Apple, e-posta ile giriş

### Üyelik & Ödeme
- **RevenueCat** — abonelik yönetimi
- **App Store / Google Play** in-app purchase entegrasyonu

### Diğer
- **Expo Linear Gradient** — UI gradients
- **Expo AV** — ses efektleri (set tamamlama, scroll, tap)
- **React Native Reanimated** — akıcı animasyonlar
- **Custom GIF asset pipeline** — 90+ hareket için optimize edilmiş animasyonlar

---

## 🏗️ Mimari Yaklaşım

### Veritabanı Şeması (özet)
- `workout_days` — kullanıcının antrenman günleri (Pazartesi/Salı/...)
- `exercises` — her güne bağlı hareketler (sıralı)
- `weekly_weights` — her egzersiz için haftalık kayıt edilen ağırlıklar
- `completed_days` — tamamlanan antrenman günleri
- `body_measurements` — vücut ölçüm geçmişi
- `user_profiles` — temel kullanıcı bilgileri (boy, kilo, yaş, cinsiyet)
- `coaching_requests` — koçluk talepleri
- `day_order`, `week_notes` — UI durumu

### Önemli Algoritmalar

**1. Hedef Ağırlık Formülü:**
```
hedef = etkin_kilo × katsayı × boy_düzeltmesi × yaş_düzeltmesi
```
- `etkin_kilo` = vücut ağırlığı × 0.80 (sadece kas kütlesinin %80'i hesaba katılır)
- `katsayı` = harekete + cinsiyete + seviyeye özgü (orta/ileri)
- `boy_düzeltmesi` = harekete göre +5% / -5% / -3% / +3%
- `yaş_düzeltmesi` = 40 yaş üstü için yıl başına -0.5%

**2. Salon-Uyumlu Yuvarlama:**
- Dumbbell/Barbell: 2.5 kg adımlarla
- Cable/Machine: 5 kg adımlarla
- LBS sistemi: 5 lbs adımlarla
- Minimum hedef: 2× adım büyüklüğü

**3. Reverse Hareketler (Assisted Pull-Up Machine, Assisted Dips):**
```
ilk_hedef = round((başlangıç_kg / 3) / 2.5) × 2.5
final_hedef = 0 kg
```
Yardım miktarını azaltarak ilerleme.

**4. Kardiyo Hacim Formülü (Treadmill):**
```
Hacim = (Süre[sn] × Hız[km/h] × Mesafe[m]) / 1000
```

---

## 📂 Proje Yapısı (özet)

```
WorkoutApp/
├── app/
│   ├── (tabs)/
│   │   ├── index.tsx       # Program ekranı (haftalık görünüm)
│   │   ├── progress.tsx    # Gelişim grafiği
│   │   ├── body.tsx        # Vücut ölçümleri
│   │   └── coach.tsx       # PRO: Online koçluk
│   ├── day.tsx             # Günlük egzersiz listesi
│   └── workout.tsx         # Aktif antrenman ekranı
├── lib/
│   ├── supabase.ts         # Supabase client + state stores
│   ├── i18n.ts             # 3 dilli çeviri sistemi
│   ├── purchases.ts        # RevenueCat entegrasyonu
│   └── sound.ts            # Ses efektleri
├── components/
│   └── PaywallModal.tsx    # PRO abonelik modalı
└── assets/
    └── exercises/          # 90+ egzersiz GIF'i
```

---

## 🎨 Tasarım Felsefesi

- **Koyu mod** ana renk (`#1a1f2e`, `#2a2f3a`) — antrenman ortamına uygun
- **Vurgu rengi**: yeşil (`#a3e635`) — pozitif aksiyonlar, ilerleme, başarı
- **Krem arka plan** (`#f5f2eb`) — modern ve yumuşak
- **Tabular nums** font variant — sayıların kayma yapmaması için
- **Kompakt kartlar** — bilgi yoğun ama göz yormayan tasarım
- **Tutarlı border radius** — 14-20px arası
- Erişilebilirlik için **44px minimum tıklama alanı**

---

## 📈 Geliştirme Süreci

Bu proje, sıfırdan tek bir geliştirici tarafından geliştirilmiştir. Aktif olarak iyileştirilen alanlar:

- ✅ 90+ egzersiz için 3 dilli ipuçları ve kas grubu bilgisi
- ✅ Kişiselleştirilmiş hedef ağırlık formülü (boy/yaş düzeltmeli)
- ✅ Salon-uyumlu ağırlık yuvarlama
- ✅ Aktif antrenman süresi takibi
- ✅ Vücut yağ oranı + ölçüm geçmişi
- ✅ Online koçluk talep akışı
- ✅ 3 dilli i18n altyapısı
- 🔄 Apple HealthKit entegrasyonu (planlama)
- 🔄 Sosyal özellikler — antrenman paylaşımı (gelecek)

---

## 📸 Ekran Görüntüleri

> Talep üzerine paylaşılır — lütfen iletişime geçin.

---

## 🤝 İletişim

Bu projenin kaynak koduna erişim, demo talebi veya iş birliği için lütfen iletişime geçin.

- **E-posta:** [iletişim için lütfen profil bilgilerine bakın]
- **LinkedIn:** [profil linki]
- **Web:** [varsa]

---

## 📜 Lisans

© 2025 ProgFit. Tüm hakları saklıdır.

Bu repo yalnızca proje tanıtımı amacıyla halka açıktır. Kaynak kod, varlıklar ve algoritmalar telif hakkı kapsamındadır. İzin alınmadan kopyalanamaz, dağıtılamaz veya türetilmiş çalışmalarda kullanılamaz.
