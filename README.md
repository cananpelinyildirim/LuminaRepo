# Lumina - Kapalı Döngü Uzay Tarımı Yaşam Destek Sistemi

Lumina, uzun süreli uzay görevleri ve gelecekteki uzay kolonileri için tasarlanmış **kapalı döngü, otonom aeroponik tarım sistemidir**. Bu sistem, AI ve IoT destekli sensörlerle bitki sağlığını takip eder ve sürdürülebilir gıda üretimi sağlar.

## 📌 Proje Amacı

- Uzayda sürdürülebilir gıda üretimi sağlamak.
- Kapalı döngü su ve besin sistemi ile %95 su tasarrufu.
- Yapay zeka destekli otomasyon ile minimum insan müdahalesi.
- Eğitim ve simülasyon amaçlı interaktif bitki izleme paneli.

## 🖥️ Sistem Özellikleri

### 1. Ana Panel (`index.html`)
- Tüm bitkileri tek bir panelden izleme.
- Bitki kartları:
  - Görsel
  - Nem, sıcaklık, ışık değerleri
  - Tıklama ile detay sayfasına geçiş
- Responsive tasarım ve yatay kaydırma.

### 2. Bitki Kontrol Paneli (`domates.html` örneği)
- Aeroponik bitki yönetimi simülasyonu.
- Sensör verileri:
  - Nem (%)
  - Sıcaklık (°C)
  - Işık seviyesi (lx)
  - Su seviyesi (%)
- Kontrol slider’ları ile manuel ayarlama.
- Tohum ekme ve ürün takibi simülasyonu.
- Yaprak sağlığı ve risk durumu simülasyonu.

### 3. Simülasyon Mantığı (JavaScript)
- Sensör verileri random olarak güncellenir.
- Slider ile sıcaklık, ışık ve su seviyesi manuel kontrol edilir.
- Tohum ekme ve ürün artırma mekanizması.
- Tehlike taraması:
  - Nem, sıcaklık, ışık ve su seviyelerini kontrol eder.
  - Yaprak sağlığı (sağlıklı, solma, sararma, hastalık) risklerini simüle eder.
- AlertBox ile kullanıcıya uyarılar gösterilir.

### 4. Önerilen İyileştirmeler
- Sensör verilerinin gerçek IoT cihazları ile entegrasyonu.
- Yapay zeka ile otomatik risk ve üretim optimizasyonu.
- LeafHealth ve updateSensors fonksiyonlarının bug fix’leri:
```js
// LeafHealth örnek düzeltme
if (rand < 20) leafHealth = "hastalık";
else if (rand < 40) leafHealth = "solma";
else if (rand < 60) leafHealth = "sararma";
else leafHealth = "sağlıklı";

// Sensör güncelleme fonksiyonu ekleme
function updateSensors() {
  humidity = Math.floor(Math.random()*100);
  temperature = Math.floor(Math.random()*35);
  light = Math.floor(Math.random()*1000);
  waterLevel = Math.floor(Math.random()*100);
  document.getElementById('humidity').textContent = humidity;
  document.getElementById('temperature').textContent = temperature;
  document.getElementById('light').textContent = light;
  document.getElementById('water').textContent = waterLevel;
}
setInterval(updateSensors, 5000);
