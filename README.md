# ☕ VR Kahve Köşesi — NPC Müşteri Sistemi

A-Frame (WebXR) tabanlı, tarayıcıda ve VR başlıklarında çalışan bir kahve dükkânı simülasyonu. Oyuncu tezgâhta içecek hazırlayıp müşterilere servis eder.

## 🎮 Özellikler

- **Otomatik müşteri spawn**: Her **5 saniyede** bir yeni müşteri gelmeye çalışır (kuyruk doluysa beklenir).
- **Tekrarsız müşteri tipi**: Aynı müşteri tipi (Adam / Kadın / Maceracı / Punk / İş Adamı) arka arkaya gelmez.
- **Tekrarsız sipariş**: Aynı sipariş (boy + içecek + ekstralar) arka arkaya tekrar etmez.
- **Yürüyerek gelme**: Müşteriler kapıdan girip kuyruk pozisyonuna kadar **yürüyerek** ilerler, siparişi teslim alınca çıkışa doğru yürüyerek ayrılır.
- **Walk / Idle animasyonları**: Karakterler yürürken `*_Walk`, beklerken `*_Idle` animasyon kliplerini kullanır (`animation-mixer`).
- **Sipariş kuyruğu**: En fazla 4 müşteri aynı anda kuyrukta bekleyebilir.
- **Nakit / Kart ödeme**, **sesli efektler** (Web Audio API, örnek ses dosyası gerekmez).
- Tamamı **tek `index.html`** dosyasında — harici build aracı gerekmez.

## 🚀 Yerelde çalıştırma

Tarayıcı güvenlik kısıtları (CORS/file://) nedeniyle basit bir local server ile açman gerekir:

```bash
# Python 3
python3 -m http.server 8080

# veya Node.js
npx serve .
```

Sonra tarayıcıdan `http://localhost:8080` adresine git.

## 🌐 GitHub Pages ile yayınlama

1. Bu repoyu GitHub'a push et.
2. **Settings → Pages** bölümünden `main` branch, `/ (root)` klasörünü seç ve kaydet.
3. Birkaç dakika içinde `https://<kullanici-adin>.github.io/<repo-adi>/` adresinden erişilebilir olacak.
4. `.nojekyll` dosyası zaten repoda — Jekyll işlemesini devre dışı bırakıp asset klasörlerinin (`assets/`) olduğu gibi servis edilmesini sağlar.

## 📁 Proje yapısı

```
.
├── index.html              # Tüm oyun mantığı, sahne ve UI burada
├── assets/models/*.glb      # 3D modeller (mobilya, karakterler, eşyalar)
└── .nojekyll                # GitHub Pages için Jekyll'i devre dışı bırakır
```

## 🕹️ Kontroller

- **Masaüstü**: WASD ile hareket, fare ile bakış, tıklayarak butonlara basma.
- **VR başlık**: Sahneye girince sağ/sol controller laser-controls ile butonlara işaret edip tetiği çekerek seçim yapılır (`raycaster: objects: .clickable`).

## 🛠️ Kullanılan teknolojiler

- [A-Frame 1.6.0](https://aframe.io/)
- [aframe-extras](https://github.com/n5ro/aframe-extras) (animation-mixer için)
- Web Audio API (sentetik ses efektleri, dosya gerektirmez)

## 📄 Lisans

Bu proje kişisel/eğitim amaçlı paylaşılmıştır. 3D modellerin lisanslarını kendi kaynaklarınıza göre kontrol ediniz.
