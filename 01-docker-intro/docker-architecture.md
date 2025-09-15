# Docker Mimarisi

Docker, uygulamaların taşınabilir ve izole bir şekilde çalışmasını sağlayan bir platformdur. Bu mimari, **Client (CLI)** ve **Server (Daemon)** olmak üzere iki ana bileşenden oluşur. Bu ikisi arasındaki iletişim **REST API** üzerinden sağlanır.

---

## 1. Docker Mimarisinin Genel Görünümü


- **Client (Docker CLI):** Kullanıcının `docker run`, `docker build`, `docker ps` gibi komutlar yazdığı kısımdır.  
- **REST API:** CLI ile Daemon arasındaki haberleşmeyi sağlar.  
- **Server (Docker Daemon):** Asıl işi yapan, konteynerleri ve diğer bileşenleri yöneten kısımdır.

📌 Görsel olarak:  

<img width="550" height="430" alt="docker-architecture" src="https://github.com/user-attachments/assets/44d8c0b1-752b-4a13-8a08-542f8084e048" />



---

## 2. Docker’ın Yönettiği Kaynaklar

Docker Daemon, aşağıdaki dört ana kaynağı yönetir:

### 🔹 Container (Konteynerler)
- Çalışan uygulamaları temsil eder.  
- Bir imajın çalışır (runtime) halidir.  
- İzole bir ortamda çalışır.

### 🔹 Image (İmajlar)
- Konteynerlerin şablonudur.  
- Bir uygulamanın çalışması için gerekli tüm bağımlılıkları içerir.  
- `docker build` komutu ile oluşturulur, `docker run` ile çalıştırılır.

### 🔹 Network (Ağ)
- Konteynerlerin birbirleriyle veya dış dünya ile iletişim kurmasını sağlar.  
- Örneğin, aynı network üzerindeki konteynerler doğrudan haberleşebilir.

### 🔹 Data Volumes (Veri Hacimleri)
- Konteyner silinse bile verilerin kaybolmamasını sağlar.  
- Kalıcı depolama alanıdır.  
- Özellikle veritabanı gibi uygulamalarda kullanılır.

---

## 3. Örnek Akış

Örnek: `docker run nginx` komutunu çalıştırdığında:

1. **CLI** komutu alır ve **REST API** aracılığıyla **Daemon**’a gönderir.  
2. **Daemon**, gerekli imajı kontrol eder.  
   - Eğer yerelde yoksa, Docker Hub’dan indirir.  
3. İmajdan bir **Container** oluşturur.  
4. Konteyneri uygun **Network** ve **Volume** ayarlarıyla başlatır.  

---

## 4. Özet

- **Client (CLI):** Kullanıcı arayüzü, komutların yazıldığı yer.  
- **REST API:** İletişim köprüsü.  
- **Daemon:** Konteyner, imaj, network ve volume yönetim motoru.  

👉 Yani, Docker mimarisinde işleyiş şu şekildedir:  
**Client → REST API → Daemon → (Container, Image, Network, Volume)**

---
