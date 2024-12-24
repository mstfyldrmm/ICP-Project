# ICP-Project
# Telefon Defteri ve Mesaj Geçmişi Uygulaması

Bu proje, Motoko dilinde yazılmış bir telefon defteri ve mesaj geçmişi uygulamasıdır. Telefon defterine yeni kişiler ekleyebilir, mesaj gönderebilir ve geçmişteki verilere ulaşabilirsiniz.

---

## Özellikler

- Telefon defterine kişi ekleme.
- Telefon numarası ve açıklama ile kişi bilgilerini alma.
- Mesaj gönderme ve geçmişteki mesajları görüntüleme.

---

## Kullanılan Yapılar

- **Telefon Defteri:** `HashMap` ile kişiler tutulur.
- **Mesaj Geçmişi:** `HashMap` ile mesajlar saklanır.

---

## Fonksiyonlar

### 1. `insert(name: Name, entry: Entry)`
- Telefon defterine yeni bir kişi ekler.
- **Parametreler:**
  - `name`: Kişinin adı.
  - `entry`: Kişinin açıklaması ve telefon numarası.

### 2. `getPhone(name: Name): async ?Entry`
- Telefon defterinde bir kişinin bilgilerini arar.
- **Parametre:**
  - `name`: Kişinin adı.
- **Dönen Değer:** 
  - Kayıt bulunursa `Entry`, aksi halde `null`.

### 3. `sendMessage(senderPhone: Phone, message: Message)`
- Mesaj gönderir ve geçmişe kaydeder.
- **Parametreler:**
  - `senderPhone`: Göndericinin telefon numarası.
  - `message`: Mesaj içeriği.

### 4. `getMessage(senderPhone: Phone): async ?Message`
- Gönderilmiş mesajları arar.
- **Parametre:**
  - `senderPhone`: Gönderenin telefon numarası.
- **Dönen Değer:** 
  - Mesaj bulunursa `Message`, aksi halde `null`.

---

## Örnek Kullanım

```motoko
// Telefon defterine kişi ekleme
await insert("Ahmet", {desc = "Arkadaş"; phone = "123-456"});

// Telefon numarasını bulma
let entry = await getPhone("Ahmet");

// Mesaj gönderme
await sendMessage("123-456", {receiver = "Mehmet"; mess = "Merhaba!"});

// Mesajı görüntüleme
let message = await getMessage("123-456");
