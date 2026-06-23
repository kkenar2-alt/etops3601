[README.md](https://github.com/user-attachments/files/29246281/README.md)
# EtOps 360

EtOps 360, et ve gıda üretim zincirlerinde karkastan kasaya kadar operasyon, sipariş, fire, WMS, kalite, kasa/POS ve banka mutabakat süreçlerini tek web platformunda izlemek için başlatılan modüler proje iskeletidir.

## Teknoloji Kararı

- Backend: .NET 10 ASP.NET Core Web API
- Frontend: React + TypeScript + Vite
- UI: CSS tabanlı soft modern tasarım, lucide ikonları, Recharts grafikler
- Mimari: modüler monolit + event-driven entegrasyona hazır katmanlar
- Gelecek entegrasyonlar: Logo Tiger 3, kasa/POS, bankalar, yemek kartları, online sipariş, kantar/terazi, soğuk zincir sensörleri

## Klasörler

- `src/EtOps360.Api`: HTTP API ve endpoint kayıtları
- `src/EtOps360.Application`: iş uygulama sözleşmeleri
- `src/EtOps360.Contracts`: frontend/API veri sözleşmeleri
- `src/EtOps360.Domain`: domain enum ve ileride eklenecek iş varlıkları
- `src/EtOps360.Infrastructure`: veri okuma, adaptörler ve entegrasyon altyapısı
- `src/web`: React web uygulaması
- `docs`: mimari ve proje notları
- `samples`: örnek veri/dosya formatları için ayrıldı
- `tools`: geliştirici yardımcı scriptleri için ayrıldı

## Kurulum

Bu makinede gerekli ana runtime'lar zaten mevcut:

- .NET SDK 10.0.300
- Node.js v26.3.0
- npm 11.16.0

Yeni makinede kurulması gerekenler:

1. .NET SDK 10 veya projenin hedeflediği LTS sürüm
2. Node.js 26 veya uyumlu güncel LTS
3. Git
4. Üretim ortamı için SQL Server veya PostgreSQL

## Çalıştırma

Backend:

```powershell
cd C:\Users\mentis\Documents\Codex\EtOps360
dotnet run --project .\src\EtOps360.Api\EtOps360.Api.csproj --launch-profile http
```

API:

- `http://localhost:5096`
- OpenAPI: `http://localhost:5096/openapi/v1.json`

Frontend:

```powershell
cd C:\Users\mentis\Documents\Codex\EtOps360\src\web
npm install
npm run dev
```

Web:

- `http://localhost:5173`

## İlk Çalışan Özellikler

- Şube ve ürün ailesi combo filtreleri
- Kullanıcı profil seçimi, şube kapsamlı giriş ve çıkış
- Rol bazlı izinli şube listesi
- Karkastan kasaya KPI ve akış paneli
- Satış, fire ve randıman grafiği
- Filtrelenebilir, gruplandırılabilir ve kolon genişliği elle değiştirilebilir operasyon tablosu
- Banka, yemek kartı ve online ödeme mutabakat paneli
- Evrak listesi, evrak detay açma, satır/audit gösterimi
- Entegrasyon olmayan firmalar için tıklama ile manuel evrak taslağı oluşturma

## Demo Giriş Profilleri

Giriş ekranında kullanıcılar ve yetkili oldukları şube/noktalar combodan seçilir.

- `merkez.planlama`: tüm şubeler ve merkez üretim
- `bolge.marmara`: Bursa 12
- `sube.bursa12`: Bursa 12
- `finans.pos`: tüm satış şubeleri
- `kalite.merkez`: merkez, İzmir 08, Antalya 03

Üretim ortamında bu demo profil yapısı SSO/MFA, kullanıcı dizini ve kalıcı yetki tablolarıyla değiştirilecektir.

## Sonraki Büyük Adımlar

1. Gerçek kimlik sistemi: SSO/MFA, RBAC + şube/bölge bazlı veri yetkisi.
2. Kalıcı veri katmanı: SQL Server/PostgreSQL, migration ve audit log.
3. Logo Tiger 3 adaptörü: resmi/çözüm ortağı onaylı API veya Logo Objects yöntemi.
4. Kasa/POS import adaptörleri: API, SFTP, read-only view veya kontrollü RPA.
5. Banka/yemek kartı/online platform mutabakat adaptörleri.
6. Kantar, terazi, barkod ve soğuk zincir sensör entegrasyonları.
7. Ekran bazlı lazy-load ve test otomasyonu.
