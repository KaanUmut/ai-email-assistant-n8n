# 📧 AI E-Mail Asistanı — n8n Automation

Gmail'e gelen e-postaları otomatik olarak analiz edip, gün sonunda özet bir rapor hazırlayan ve yine e-posta olarak gönderen bir AI ajanı.

## Nasıl Çalışıyor?

1. **Schedule Trigger** — Workflow her gün saat 09:00'da otomatik olarak tetiklenir.
2. **AI Agent (Google Gemini)** — Gmail'den son gelen e-postaları çeker, her birini gönderen, konu ve içerik açısından inceler.
3. **Sınıflandırma** — Ajan her e-postayı şu kategorilere ayırır:
   - 🔴 Önemli / Aksiyon Gerektiren
   - 🟡 Cevap Gerektiren
   - 🟢 Bilgilendirme
   - ⚪ Gereksiz / Reklam
   
   Sınıflandırma yaparken sadece anahtar kelimelere değil, e-postanın içerdiği tarih/saat, deadline, toplantı gibi bağlamsal sinyallere bakar.
4. **Rapor Gönderimi** — Ajan, hazırladığı yapılandırılmış raporu doğrudan e-posta olarak kullanıcıya gönderir.

## Kullanılan Node'lar

| Node | Görev |
|---|---|
| Schedule Trigger | Günlük otomatik tetikleme |
| AI Agent | Analiz ve raporlama mantığı |
| Gmail (Get many messages) | E-postaları okuma (AI Agent'a tool olarak bağlı) |
| Google Gemini Chat Model | Dil modeli (analiz motoru) |
| Gmail (Send a message) | Raporu e-posta olarak gönderme |

## Teknolojiler

`n8n` · `Google Gemini API` · `Gmail API` · `LangChain (n8n entegrasyonu)`

## Neden Yaptım?

Her gün gelen e-postaları tek tek okuyup önemli olanları ayırt etmek zaman alıyor. Bu ajan, hangi e-postaların gerçekten aksiyon/cevap gerektirdiğini otomatik tespit ederek manuel kontrol ihtiyacını ortadan kaldırıyor ve günün başında hızlı bir öncelik listesi sunuyor.

## Kurulum

1. n8n'e bu JSON dosyasını import edin (Workflows → Import from File).
2. Gmail OAuth2 ve Google Gemini API credential'larınızı bağlayın.
3. Schedule Trigger'daki saati isteğinize göre ayarlayın.
