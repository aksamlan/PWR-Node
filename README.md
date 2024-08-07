
### **PWR Zincir Doğrulayıcı Düğüm ve RPC Düğüm Kılavuzu**

### Explore : [Burdan](https://explorer.pwrlabs.io/)
### Twitter : [Burdan](https://x.com/pwrlabs)

### **Doğrulayıcı Düğüm Kılavuzu**

**Önemli Not**: Bu, ilk testnet lansmanıdır. Mükemmellik için çabalarken öngörülemeyen sorunlar olabilir. [Discord sunucumuzda](https://discord.gg/DJkcuy9SAg) bildirilen tüm geri bildirimleri, hata raporlarını veya diğer sorunları takdir ediyoruz.

#### **Gereksinimler**:
- **CPU**: 1 vCPU
- **Memory**: 1 GB RAM
- **Disk**: 25 GB HDD or higher
- **Open TCP Ports**: 8231, 8085
- **Open UDP Port**: 7621

#### **Setup on Ubuntu Server**:

1. **Update OS**: 
   ```bash
   sudo apt update
   ```

2. **Install Java**: 
   ```bash
   apt install openjdk-19-jre-headless
   ```

3. **Doğrulayıcı düğüm yazılımını ve yapılandırma dosyasını yükleyin**:
   ```bash
   wget https://github.com/pwrlabs/PWR-Validator-Node/raw/main/validator.jar
   wget https://github.com/pwrlabs/PWR-Validator-Node/raw/main/config.json
   ```

4. **Şifrenizi Ayarlayın**:
   ```bash
   sudo nano password
   ```
   - İstediğiniz şifreyi giriniz.
   - Kapatmak için `Ctrl + x` tuşlarına basın.
   - Şifreyi kaydetmeyi onaylamak için `Y` tuşuna basın.
  
5. **Doğrulayıcınızı İçe Aktarın**:

   Eğer içe aktarmak istediğiniz özel bir anahtarınız varsa bu komutu kullanın, aksi takdirde bir sonraki adıma geçin.
   ```bash
   sudo java -jar validator.jar --import-key <private key here> password
   ```

6. **Düğümü Çalıştıralım**:

   `<YOUR_SERVER_IP>` kısmını sunucunuzun gerçek IP'si ile değiştirin.
   ```bash
   screen -S pwr
   ```
   ```bash
   sudo java -jar validator.jar password <YOUR_SERVER_IP> --compression-level 0
   ```
   PWR Zinciri blok sıkıştırmayı destekleyen ilk zincirdir.
   --compression-level, düğümünüzün kullanmasını istediğiniz sıkıştırma düzeyini ayarlar.
   Sıkıştırma seviyesi 0 - 9 arasında değişir. 0 sıkıştırmayı devre dışı bırakır. 9 sıkıştırmayı maksimuma ayarlar.

7. **Adresinizi Alın**:
     ```
     curl localhost:8085/address/
     ```

9. **Doğrulayıcı Düğüm Olun**:

   - Başlangıçta, düğümünüz blok zinciriyle senkronize olacak ancak stake edilmiş PWR Coin'lere sahip olana kadar doğrulayıcı sorumluluklarını üstlenmeyecektir.
   
   - Staking için yeterli PWR Coin elde etmek için, [Discord sunucumuzda testnet doğrulayıcısı olmak için başvuruda bulunun](https://discord.gg/DJkcuy9SAg). Onaylandıktan sonra, staking için 100k PWR talep etmek üzere Discord botumuzu kullanabilirsiniz.
   
   - Coinlerinizi talep ettikten sonra, node'unuz doğrulayıcı olarak kaydolmak için bir işlem başlatacaktır.


10. **Özel Anahtarınızı Alma**:
    ```bash
    sudo java -jar validator.jar get-private-key password
    ```
    Bir hex dize özel anahtarı döndürülecektir. Bu anahtar [PWR Tarayıcı Cüzdanı](https://chromewebstore.google.com/u/3/detail/pwr-wallet/kennjipeijpeengjlogfdjkiiadhbmjl) içinde kullanılabilir

Tebrikler, artık bir PWR Zincir doğrulayıcı düğümü kurdunuz ve çalıştırdınız!

