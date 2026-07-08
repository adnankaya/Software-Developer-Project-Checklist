# Yazılımcılar için Proje Kontrol Listesi (2026)

Her yeni projede, ya da mevcut bir projeyi sağlamlaştırma turunda bu listeyi kullan.

## 1. Geliştirme akışı (development workflow)
- [ ] Ajan tabanlı kodlama aracı kullanımda (agentic coding tool) (opencode, Claude Code vb.)
- [ ] Büyük özelliklerden önce spesifikasyon odaklı geliştirme (spec-driven development) (openspec veya benzeri)
- [ ] Tekrar kullanılabilir ajan becerileri / promptlar (agent skills) yaygın mühendislik görevleri için
- [ ] Birleştirmeden (merge) önce geçmesi zorunlu otomatik testler (unit + integration test)
- [ ] Her pull request'te CI pipeline (GitHub Actions veya benzeri)

## 2. Güvenlik (security) — Yapay zekanın ürettiği kod varsayılan olarak güvenilmez
- [ ] SAST taraması CI'da **zorunlu** bir kontrol olarak (isteğe bağlı değil)
- [ ] CI'da bağımlılık / tedarik zinciri taraması (dependency / SCA scanning)
- [ ] Commit'lerde ve geçmişte gizli anahtar taraması (secret scanning) (sızan anahtarları hemen iptal et)
- [ ] Bağımlılıklar sabitlenmiş (pinned); yeni/tanıdık olmayan paketler kurulmadan önce doğrulanıyor (halüsinasyon paketlere / "slopsquatting" saldırılarına dikkat)
- [ ] Şunlarda insan incelemesi zorunlu: kimlik doğrulama akışları (auth flows), ödeme kodu, gizli bilgilere veya müşteri verisine dokunan her şey
- [ ] Gizli bilgi yöneticisi (secrets manager) kullanımda (dağınık `.env` dosyaları değil) — özellikle ajanların dosya sistemine erişimi olduğu için

## 3. Gözlemlenebilirlik ve güvenilirlik (observability & reliability)
- [ ] Uyarılı çalışma süresi izleme (uptime monitoring) (telefon/e-posta bildirimi)
- [ ] Hata takibi (error tracking) (Sentry benzeri) — sadece "çalışıyor mu" değil, "neden bozuldu ve kimin için" bilgisi
- [ ] Prod'da LLM/ajan iş akışları çalışıyorsa: ajana özel izleme (agent-specific tracing) (çok adımlı hatalar normal HTTP hatası gibi görünmez)
- [ ] Bir şeyler bozulduğunda gerçekten sorgulayabileceğin temel loglama

## 4. Dağıtım güvenliği (deployment safety)
- [ ] Her pull request için önizleme/staging ortamı
- [ ] Bilinen, hızlı bir geri alma (rollback) yolu (test edilmiş, sadece teoride değil)
- [ ] Geri alınabilir veritabanı migration'ları
- [ ] Yedekler (backups) — ve gerçekten test edilmiş bir geri yükleme (restore), sadece "yedekler var" değil

## 5. Bağımlılık hijyeni (dependency hygiene)
- [ ] Otomatik bağımlılık güncellemeleri (Renovate/Dependabot) düzenli çalışıyor
- [ ] Terk edilmiş/yüksek riskli bağımlılıklar için periyodik manuel kontrol

## 6. İş tarafı temelleri (business basics)
- [ ] Kullanım Koşulları (Terms of Service) + Gizlilik Politikası (Privacy Policy) hazır
- [ ] AB/Kaliforniya kullanıcıları varsa temel uyumluluk kontrolü (GDPR/CCPA temelleri)
- [ ] Ürün analitiği (product analytics) (PostHog veya benzeri) entegre
- [ ] Kısa kişisel olay müdahale rehberi (incident runbook) ("X bozulursa önce Y'ye bak") — tek nöbetçi sensin

## 7. Bir projeyi "production ready" ilan etmeden önce
- [ ] Bölüm 2'nin (güvenlik) tamamı kontrol edildi
- [ ] Bölüm 3'ün (gözlemlenebilirlik) tamamı kontrol edildi
- [ ] Rollback en az bir kez test edildi
- [ ] Yedekler en az bir kez restore testinden geçti
