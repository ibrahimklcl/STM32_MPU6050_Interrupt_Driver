# STM32 MPU6050 Interrupt-Based Driver 

Bu repository, MPU6050 Gyro sensörü için geliştirilmiş **Non-Blocking (Bloklamasız)** I2C sürücü dosyalarını içerir. TUSAŞ staj deneyimi ile geliştirilen bu yapı, klasik polling yöntemi yerine **Interrupt (Kesme)** ve **Event-Flag** mimarisini kullanır.

## Dosya İçeriği
* **`mpu6050.c` / `mpu6050.h`:** Sürücü kütüphanesi. Projenize dahil edip kullanabilirsiniz.
* **`main.c`:** Örnek kullanım (Example Usage). Kesme yönetiminin (`HAL_I2C_MemRxCpltCallback`) nasıl yapılacağını gösterir.

## Nasıl Çalışır?
1.  Veri okuma işlemi `HAL_I2C_Mem_Read_IT` ile başlatılır.
2.  İşlemci veri beklerken meşgul edilmez (Non-Blocking).
3.  Veri hazır olduğunda bir Kesme (Interrupt) oluşur ve `dataReadyFlag` bayrağı kaldırılır.
4.  Ana döngü (Main Loop) bayrağı kontrol eder ve UART gönderimini güvenli bir şekilde yapar.

## Entegrasyon
Bu dosyaları kendi STM32 CubeIDE projenizin `Core/Src` ve `Core/Inc` klasörlerine kopyalayarak kullanabilirsiniz.
