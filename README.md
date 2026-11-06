# HSD Lingo Yarışması

Huawei Student Developers (HSD) etkinlikleri için hazırlanmış, eleme usulü bir **Lingo kelime yarışması** uygulaması. Gruplar ikişer ikişer karşılaşır ve harf ipuçlarıyla kelimeyi önce bulan grup turu geçer. Sunucu her şeyi tek ekrandan yönetir, ekran da projeksiyona yansıtılır.

Uygulama tek bir HTML sayfasıdır. Kurulum ya da sunucu gerektirmez, yaklaşık 217 bin kelimelik Türkçe sözlük de sayfanın içinde gelir.

Canlı sayfa: https://claude.ai/artifact/DJ6NY9aysKnr2uUqfpe79r

## Özellikler

**Turnuva**
- Eleme usulü, otomatik kura. Her turda gruplar ikişer eşleşir. Grup sayısı tekse bir grup maç yapmadan üst tura çıkar (bay); bir grup turnuvada en fazla bir kez bay geçer.
- Tur sayısı grup sayısından hesaplanır. 50 grup: 50 → 25 → 13 → 7 → 4 → 2 (6 tur). 80 grup: 80 → 40 → 20 → 10 → 5 → 3 → 2 (7 tur). Son üç tur çeyrek final, yarı final ve finaldir.
- Bütün turları gösteren turnuva tablosu, kurayı yeniden çekme, süren turnuvada eşleşmeleri düzenleme ve maç skorunu elle düzeltme.
- Maçı ilk 2 kelimeyi bilen grup kazanır (ayarlanabilir), yani maç en çok 3 kelime sürer. Kimsenin bilemediği kelime skora sayılmaz.

**Oyun**
- Klasik Lingo kuralları: kelimenin ilk harfi açık gelir, her tahminden sonra harfler renklenir.
  - Kırmızı: harf doğru, yeri de doğru.
  - Sarı: harf kelimede var ama başka yerde.
  - Gri: harf kelimede yok.
- İki tahmin düzeni: **Gruplar sırayla** (yanlış tahminde sıra rakibe geçer) ve **İlk basan cevaplar** (buzzer).
- Sunucu düğmeleri: Harf aç, Hak ekle, Kelimeyi göster, Kelimeyi değiştir, Sırayı geç, Maç skoru, Geri al.
- Deneme hakkı ve cevap süresi her tur için ayrı ayarlanır.
- Ses efektleri, ekran klavyesi, tam ekran ve ayarlanabilir harf açılma hızı.

**Kelimeler**
- Her turda maç maç kelime alanları (maç başına 3 kelime), turun yedek kelimeleri ve bütün turlar için ortak bir kelime bankası.
- Her kelimenin alanı *teknoloji* ya da *genel kültür*dür. Otomatik seçim her turu yaklaşık %60 teknoloji, %40 genel kültür tutar.
- **Kelimeyi değiştir**: aynı alandan yeni kelimeyi önce turun yedeklerinden, onlar bitince kelime bankasından getirir.
- **Eksikleri tamamla**: boş ya da hatalı kelime alanlarını ve eksik yedekleri tek tıkla doldurur.
- JSON dosyası yükleme ya da yapıştırma, toplu düzenleme ve ekran yansıtılırken kelimeleri gizleme.

**Sözlük kontrolü**
- Anlamsız tahminleri sayfanın içindeki Türkçe sözlükle yakalar. EVLERDE, SOKAKTA, GELDİ gibi çekimli haller kökünden tanınabilir.
- Sözlükte olmayan bir tahminde üç seçenek var: sunucuya sor (düzelt, anlamsız say ya da geçerli say), otomatik anlamsız say ya da hiç kontrol etme.

**Yönetim**
- PIN ile kilitlenen yönetim paneli. Varsayılan PIN `1234`; yarışmadan önce değiştirin.
- 2–128 grup, grup başına iki yarışmacı ve grup rengi. Turnuvaya katılacak gruplar işaretlenir; yeni eklenen bir grup siz seçene kadar turnuvaya girmez.
- Yarışma adı, alt başlık ve logo.
- Bütün ayarlar, gruplar ve kelimeler tek bir JSON yedeği olarak indirilip geri yüklenebilir.

## Yarışma günü: hızlı başlangıç

1. Sayfayı açın ve **Yönetim paneli**ne PIN ile girin.
2. **Gruplar** sekmesinde grup sayısını girin, adları ve yarışmacıları yazın, katılacak grupları işaretleyin. *Toplu düzenle* ile her satıra bir grup yazabilirsiniz: `Grup adı, 1. yarışmacı, 2. yarışmacı`.
3. **Turlar ve kelimeler** sekmesinde *JSON dosyası yükle* ile grup sayınıza uygun kelime setini seçin (aşağıdaki tabloya bakın). Yükleme penceresi her turun kaç kelime alacağını gösterir. Bir tur eksik kalırsa başındaki *Eksikleri tamamla* düğmesini kullanın.
4. Aynı sekmede her turun **deneme hakkını** ve **cevap süresini** ayarlayın.
5. **Oyun ayarları** sekmesinde tahmin düzenini ve sözlük kontrolünü seçin, PIN kodunu değiştirin.
6. **Turnuvayı başlat** ile kura çekilir. `Enter` ile sıradaki maça geçilir.

## Hazır kelime setleri

| Set | Dosya | Harf sayıları | Teknoloji / genel kültür |
|---|---|---|---|
| 50 grup, 5 harfle başlayan | `kelimeler/`: 6 tur dosyası ve `kelime-bankasi.json` | 1–3. tur 5, çeyrek final 6, yarı final 7, final 8 | %60 / %40 |
| 80 grup, 5 harfle başlayan | `kelimeler-80/`: 7 tur dosyası ve `80grup-kelime-bankasi.json` | 1–4. tur 5, çeyrek final 6, yarı final 7, final 8 | %60 / %40 |
| 50 grup, 4 harfle başlayan | `kelimeler-4harf/lingo-4harf-50grup.json` | 1–3. tur 4, çeyrek final 5, yarı final 6, final 7 | %60 / %40 |
| 80 grup, 4 harfle başlayan | `kelimeler-4harf/lingo-4harf-80grup.json` | 1–4. tur 4, çeyrek final 5, yarı final 6, final 7 | 4 harfli turlarda %39 / %61, son üç turda %60 / %40 |

- Bir setin bütün dosyalarını birlikte seçip yükleyin. 4 harfle başlayan setlerde turlar ve kelime bankası tek dosyadadır.
- 4 harfle başlayan bir seti yüklerken ayarı elle değiştirmeniz gerekmez: yükleme penceresi *İlk turların harf sayısı*nı dosyaya göre 4 yapar. 5 harfli bir set yüklenince yine 5'e döner.
- 80 gruplu setler 50 grupla da eksiksiz çalışır. 50 grupta olmayan "4. Tur" dosyası atlanır, çeyrek final ve yarı final dosyalarındaki ek kelimeler fazladan maçlara gider.
- Dosyalar tur adına (Çeyrek final, Yarı final, Final) göre yerleştiği için başka grup sayılarına da uyar. İlk turlarda maç sayısı artarsa *Eksikleri tamamla* eksik kelimeleri kelime bankasından getirir.
- 80 gruplu 4 harfli sette teknoloji oranı düşüktür, çünkü sözlükteki iyi 4 harfli teknoloji kelimelerinin hepsi kullanıldığı halde 270 kelimelik ihtiyaca yetmiyor. Yine de her maçta en az bir teknoloji kelimesi vardır.
- 50 gruplu 5 harfli set deneme hakkını da ayarlar (5, finalde 6). Diğer setler paneldeki deneme hakkına ve cevap süresine dokunmaz.
- Bütün kelimeler sözlükte kontrol edilmiştir. Her maçta iki alandan da kelime vardır ve bir kelime aynı sette iki kez geçmez.

> **Uyarı:** Kelime dosyalarını herkese açık bir yerde paylaşmayın, yarışmacılar kelimeleri önceden görebilir. Bu projeyi açık bir depoya koyacaksanız `kelimeler*/` klasörlerini `.gitignore`'a ekleyin.

## Kelime dosyası biçimi

Kelime dosyaları JSON'dur. Tek bir tur:

```json
{
  "format": "hsd-lingo-kelimeleri",
  "surum": 2,
  "tur": 1,
  "ad": "1. Tur",
  "harf": 5,
  "kelimeler": [
    { "kelime": "ÖRNEK", "alan": "genel kültür" },
    { "kelime": "KALEM", "alan": "genel kültür" },
    "KİTAP"
  ],
  "yedek": [
    { "kelime": "DEFNE", "alan": "genel kültür" }
  ]
}
```

| Alan | Açıklama |
|---|---|
| `tur` | Tur numarası (1–12). |
| `ad` | İsteğe bağlı. Turnuvada aynı adlı bir tur varsa (Çeyrek final, Yarı final, Final…) dosya o tura yüklenir, yoksa `tur` numarasına. |
| `harf` | İsteğe bağlı, bilgi amaçlı. Asıl ölçü kelimelerin uzunluğudur. |
| `kelimeler` | Sırayla maçlara dağıtılır: ilk 3 kelime 1. maçın, sonraki 3 kelime 2. maçın ve böyle devam eder. Maçlardan artanlar yedeğe geçer. |
| `yedek` | İsteğe bağlı. Turun yedek kelimeleri. |
| `deneme` | İsteğe bağlı. Turun deneme hakkı (1–12). |
| `sure` | İsteğe bağlı. Cevap süresi, saniye (0 süre sınırı yok demektir). |

Bir kelime düz metin (`"KİTAP"`) ya da alanıyla birlikte yazılabilir. `alan` "teknoloji" ya da "genel kültür" olur. Küçük harf ya da Türkçe karakter sorun olmaz.

Bütün turlar ve kelime bankası tek dosyada da verilebilir:

```json
{
  "format": "hsd-lingo-kelimeleri",
  "surum": 2,
  "turlar": [
    { "tur": 1, "ad": "1. Tur", "kelimeler": ["…"], "yedek": ["…"] },
    { "tur": 2, "ad": "2. Tur", "kelimeler": ["…"] }
  ],
  "banka": {
    "teknoloji":    { "4": ["…"], "5": ["…"] },
    "genel kültür": { "4": ["…"], "5": ["…"] }
  }
}
```

Kelime bankası ayrı bir dosya da olabilir:

```json
{
  "format": "hsd-lingo-kelime-bankasi",
  "surum": 1,
  "teknoloji":    { "5": ["…"], "6": ["…"] },
  "genel kültür": { "5": ["…"], "6": ["…"] }
}
```

Yüklerken:

- Pencere her turun kaç kelime alacağını, kaçının maçlara, kaçının yedeğe gideceğini ve alan dağılımını gösterir. Onaylamadan hiçbir şey değişmez.
- Yüklenen tur, o turun mevcut listesinin yerini alır. Kelime bankası da eskisinin yerini alır.
- Turun harf sayısına uymayan kelimeler ve tekrarlar atlanır.
- Dosyanın tamamı başka bir harf sayısı için hazırlanmışsa (ör. ilk turlar 4 harfli), pencere *İlk turların harf sayısı* ayarının nasıl değişeceğini gösterir ve onaylayınca uygular. Maçlar başlamış bir turnuvada bu ayar değiştirilmez.

## Harf sayıları ve kelime ihtiyacı

Çeyrek finale kadar bütün turlar *İlk turların harf sayısı* kadar harfle oynanır. *Artış* 1 ise çeyrek final 1, yarı final 2, final 3 harf uzun olur. Örneğin ilk turlar 5 harfliyse çeyrek final 6, yarı final 7, final 8 harfli olur.

Bir turun ihtiyacı: maç sayısı × 3 maç kelimesi, artı yedek olarak maç sayısının yaklaşık %60'ı (en az 2). Örneğin 50 grupta 1. turda 25 maç var: 75 maç kelimesi ve 15 yedek.

## Ayarlar

| Ayar | Varsayılan | Açıklama |
|---|---|---|
| Maçı kazanmak için bilinmesi gereken kelime | 2 | 2 ise maç en çok 3 kelime sürer. |
| İlk turların harf sayısı | 5 | Çeyrek finale kadar bütün turlar bu uzunlukta oynanır. |
| Çeyrek final, yarı final ve finalde artış | 1 | Son üç turda her tur kaç harf uzar. |
| Tahmin düzeni | İlk basan cevaplar | Diğer seçenek: Gruplar sırayla. |
| Yanlış tahmin eden grup bir sonraki tahminde basamasın | Açık | Yalnızca "İlk basan cevaplar" düzeninde geçerli. |
| Sözlükte olmayan tahminler | Sunucuya sor | Diğer seçenekler: Otomatik anlamsız say, Kontrol etme. |
| Çekimli halleri geçerli say | Açık | |
| Kelimenin ilk harfi açık gelsin | Açık | Klasik Lingo kuralı. |
| Bulunan harfler sonraki satırda gösterilsin | Açık | |
| Ses efektleri, ekran klavyesi | Açık | |
| Harflerin açılma hızı | Normal | Yavaş, Normal ya da Hızlı. |
| PIN kodu | 1234 | Boş bırakılırsa panel kilitlenmez. |

Deneme hakkı (varsayılan 5, 8 ve daha uzun kelimelerde 6) ve cevap süresi (varsayılan 20 saniye) her tur için *Turlar ve kelimeler* sekmesinden ayarlanır.

## Sunucu kısayolları

| Tuş | İşlev |
|---|---|
| Harf tuşları | Tahmini yazar (Türkçe harfler ekran klavyesinde de var). |
| `Enter` | Tahmini gönderir; maç ve tur ekranlarında sonraki adıma geçer. |
| `⌫` | Son harfi siler. |
| `1` / `2` | Grubun buzzer'ı ("İlk basan cevaplar" düzeninde). |
| `Esc` | Yanlışlıkla basılan buzzer'ı iptal eder. |
| `Ctrl` + `Z` | Son işlemi geri alır. |
| `K` / `R` | Sözlükte olmayan kelimeyi geçerli ya da anlamsız sayar. |
| Saate tıklama | Süreyi durdurur ya da devam ettirir. |

## Veriler ve yedekleme

- Sayfa claude.ai'de açıldığında ayarlar, kelimeler ve turnuva durumu sayfanın kendi veritabanında tutulur ve sayfa başka bir bilgisayarda açıldığında da yüklenir. Bu verileri yalnızca sayfanın sahibi okuyup yazabilir.
- Her şey ayrıca tarayıcıda saklanır. `index.html` doğrudan tarayıcıda açıldığında tek kayıt yeri tarayıcıdır.
- **Yedekleme** sekmesi bütün ayarları, grupları ve kelimeleri tek bir JSON dosyası olarak indirir ya da panoya kopyalar; aynı sekmeden geri yüklenir. *Turnuvayı sıfırla* eşleşmeleri ve sonuçları siler, grupları ve kelimeleri korur. *Varsayılan ayarlara dön* her şeyi baştan kurar.
