# 🛡️ Kişisel Güvenlik ve Refah Uygulaması

Bu uygulama, kullanıcıların günlük yaşamlarında kendilerini güvende hissetmelerini sağlamak amacıyla geliştirilmiş, konum tabanlı ve acil durum müdahale odaklı bir mobil güvenlik çözümüdür.

## 🚀 Temel Özellikler

### 🚨 Acil Durum Yönetimi
* **Panik Düğmesi:** Tek dokunuşla konum paylaşımı ve otomatik sesli kanıt kaydı.
* **Sessiz Alarm:** Şüphe çekmeden gizli tetikleyici ile konum takibi ve ses kaydı.
* **Acil Durum Kişileri:** Kişiselleştirilebilir acil durum kişi yönetimi.

### 🛡️ Güvenlik ve İzleme
* **Güvenli Yürüyüş Arkadaşı:** Hedef süre dolduğunda otomatik konum uyarı sistemi.
* **Bölge İzleme (Geofencing):** Güvenli ve riskli bölgelere giriş/çıkışta otomatik bildirim ve SMS.
* **Batarya Alarmı:** Kritik batarya seviyelerinde son konumun otomatik gönderilmesi.

### 📞 Yardımcı Araçlar
* **Sahte Arama Tetikleyicisi:** Rahatsız edici durumlardan kurtulmak için sahte gelen çağrı simülasyonu.
* **Olay Geçmişi:** Tetiklenen tüm güvenlik olaylarının Firebase üzerinden kronolojik takibi.

---

## 🛠️ Teknik Yığın (Tech Stack)

| Kategori | Teknolojiler |
| :--- | :--- |
| **Platform** | React Native, Expo |
| **Veri Yönetimi** | Firebase Firestore, AsyncStorage |
| **Medya & Depolama** | expo-av, Firebase Storage |
| **Konum & Arka Plan** | expo-location, expo-task-manager |
| **Haberleşme** | expo-sms |

---
## Görseller
<img width="395" height="704" alt="image" src="https://github.com/user-attachments/assets/507dcac1-155d-409e-9982-b03079bfc2c8" />
<img width="396" height="704" alt="image" src="https://github.com/user-attachments/assets/8f5dc6b7-7932-4750-8f25-c87e2e3badac" />
<img width="396" height="706" alt="image" src="https://github.com/user-attachments/assets/8f082318-1132-4058-8a0f-c3ae61fd247f" />
<img width="395" height="704" alt="image" src="https://github.com/user-attachments/assets/6f136343-2449-4f11-8cf5-0e77810f0498" />
<img width="395" height="704" alt="image" src="https://github.com/user-attachments/assets/e26ba5a3-099c-4479-a325-107ec07fbd55" />
<img width="392" height="701" alt="image" src="https://github.com/user-attachments/assets/9c400b98-5c2e-45d5-82ca-d58a7dcbc5f6" />
<img width="394" height="703" alt="image" src="https://github.com/user-attachments/assets/641ef131-441b-4474-943a-c1cc297b4e02" />
<img width="393" height="702" alt="image" src="https://github.com/user-attachments/assets/fcf694a4-42a7-4c19-b9c9-857cfe7f647f" />
<img width="397" height="704" alt="image" src="https://github.com/user-attachments/assets/03bb7350-a7ae-4ac8-889c-4ad3df09e851" />
<img width="393" height="700" alt="image" src="https://github.com/user-attachments/assets/7e3e4599-ab1c-4d7c-b856-6e36f501c228" />
<img width="394" height="703" alt="image" src="https://github.com/user-attachments/assets/e04a99b4-d505-4f63-b624-e7c9e7226abe" />
<img width="397" height="702" alt="image" src="https://github.com/user-attachments/assets/067da153-e5e5-40c3-ad58-509f0d1cc61f" />
<img width="398" height="705" alt="image" src="https://github.com/user-attachments/assets/4ff409cf-6736-434f-912e-ad0c17817442" />
<img width="393" height="706" alt="image" src="https://github.com/user-attachments/assets/7b07c859-9b34-46d6-9ced-7031680a8878" />
<img width="392" height="700" alt="image" src="https://github.com/user-attachments/assets/f619ce8c-9eb6-461a-8a06-9d39ff25a07d" />
<img width="396" height="701" alt="image" src="https://github.com/user-attachments/assets/46ab9a15-f1c2-4aef-ab71-7cec14e877b4" />


## ⚙️ Güvenlik, Sistem ve Veri Akışı

### 🛡️ Güvenlik Kuralları (Firebase Security Rules)
Proje genelinde veritabanı güvenliği için **Firebase Security Rules** uygulanması zorunludur. Firestore ve Storage üzerinde sadece kimliği doğrulanmış (authenticated) kullanıcıların kendi verilerine okuma/yazma yapabilmesi için kurallar tanımlanmalı; halka açık erişim varsayılan olarak kapatılmalıdır.

### 🔋 Sistem Kararlılığı ve Arka Plan Süreçleri
Uygulama, `expo-task-manager` kullanarak arka planda konum takibi yapar. Modern işletim sistemleri pil tasarrufu için arka plan servislerini kısıtlayabilir. Kararlılık için:
* **Foreground Service:** Kritik arka plan işlemleri, sistem tarafından öldürülme riskini düşürmek için ön plan servisi ile birleştirilmelidir.
* **Pil Optimizasyonu:** Kullanıcıya, uygulama ayarlarından **"Pil Optimizasyonunu Kapat" (Ignore Battery Optimization)** izni vermesi önemle önerilir.

### 🧪 Test Stratejisi
* **Manuel Test:** Tüm acil durum tetikleyicileri (panik butonu, sahte arama vb.) gerçek fiziksel cihazlarda test edilmiştir.
* **Entegrasyon:** Firebase veritabanı ile Firebase Storage arasındaki veri bağlantıları doğrulanmıştır.
* **Canlı Test:** Uygulama geliştirme süresince `Expo Go` üzerinden anlık canlı testler yapılmıştır.

### 📈 Veri Akış Şeması
Aşağıdaki şema, sistemin bir tetikleyici algıladığında izlediği yolu özetler:

```mermaid
graph LR
    A[Tetikleme] --> B[Konum/Ses İşleme]
    B --> C((Güvenli Bağlantı))
    C --> D[Firebase Storage/Firestore]
    D --> E[SMS Bildirimi]


