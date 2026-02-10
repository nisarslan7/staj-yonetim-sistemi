# Staj Yönetim Sistemi

Bu proje, kurum bünyesinde staj yapan öğrencilerin başvurusu, günlük faaliyet takibi, mentor onayı ve performans değerlendirme süreçlerini yönetmek amacıyla geliştirilmiştir.

## Teknolojiler

- **Backend:** ASP.NET Core MVC (.NET 8.0)
- **Veritabanı:** SQL Server
- **Mimari:** Klasik MVC (Controller-Business-Entity-Data)

## Proje Yapısı

```
src/StajYonetimSistemi/
├── Controllers/      # HTTP isteklerini yöneten controller'lar
├── Business/         # İş mantığı (Service sınıfları)
├── Entities/         # Veritabanı tabloları (Entity sınıfları)
├── Data/             # DbContext ve veritabanı yapılandırması
├── Dtos/             # Veri taşıma nesneleri
├── Enums/            # Enum tanımları
├── Helpers/          # Yardımcı sınıflar
├── Views/            # Razor view dosyaları
└── wwwroot/          # Statik dosyalar (CSS, JS, uploads)
```

## Özellikler

### Stajyer
- ✅ Günlük faaliyet girişi (onay gerektirmez)
- ✅ Otomatik staj defteri oluşturma
- ✅ Devam durumu takibi (girilen gün sayısına göre)
- ✅ Belge yükleme

### Mentor
- ✅ Belgeleri inceleme
- ✅ Performans değerlendirmesi girişi

### Admin
- ✅ Kullanıcı atamaları (Mentor-Stajyer)
- ✅ Genel raporlar ve dashboard

## Kurulum

### Gereksinimler
- .NET 8.0 SDK
- SQL Server (LocalDB veya SQL Server Express)
- Visual Studio 2022 veya Visual Studio Code

### Adımlar

1. **Projeyi klonlayın veya indirin**

2. **Veritabanı bağlantı string'ini güncelleyin**
   
   `appsettings.json` dosyasındaki `ConnectionStrings` bölümünü kendi SQL Server bilgilerinize göre düzenleyin:
   ```json
   "ConnectionStrings": {
     "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=StajYonetimDB;Trusted_Connection=True;MultipleActiveResultSets=true"
   }
   ```

3. **NuGet paketlerini yükleyin**
   ```bash
   dotnet restore
   ```

4. **Veritabanı migration'larını oluşturun ve uygulayın**
   ```bash
   dotnet ef migrations add InitialCreate
   dotnet ef database update
   ```

5. **Projeyi çalıştırın**
   ```bash
   dotnet run
   ```

   Veya Visual Studio'da F5 tuşuna basın.

## Veritabanı Yapısı

- **Users:** Kullanıcılar (Stajyer, Mentor, Admin)
- **DailyActivities:** Günlük faaliyet kayıtları
- **Documents:** Yüklenen belgeler
- **PerformanceEvaluations:** Performans değerlendirmeleri
- **InternshipJournals:** Otomatik oluşturulan staj defterleri

## Önemli Notlar

- Günlük faaliyetler **onaylanmaz**, direkt kaydedilir
- Devam durumu = girilen gün sayısına göre hesaplanır
- Staj defteri = faaliyetlerin otomatik birleşimi
- Performans değerlendirmesi ayrı bir tablodur

## Rol Yapısı

- **Stajyer (1):** Günlük faaliyet girer, belge yükler
- **Mentor (2):** Belgeleri inceler, değerlendirme yapar
- **Admin (3):** Kullanıcı atamaları yapar, raporları görür

## Geliştirme

Proje basit MVC yapısı kullanmaktadır:
- Clean Architecture veya DDD kullanılmamıştır
- Generic Repository pattern kullanılmamıştır
- Sadece klasik Controller-Business-Entity-Data yapısı

## Lisans

Bu proje eğitim amaçlı geliştirilmiştir.
