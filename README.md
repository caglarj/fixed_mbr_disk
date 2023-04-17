# Windows 10 ve 11'de  "The selected disk is not a fixed MBR disk" hatası, nedeni ve çözümü.


Elde ettiğiniz hata, Windows 11 veya Windows 10'un Disk Yönetimi veya DISKPART yardımcı programı kullanarak disk bölümlerini yönetmeye çalışırken karşılaştığınız bir sorundur. 

Hata mesajı,



```
The selected disk is not a fixed MBR disk. The ACTIVE command can only be used on fixed MBR disks.
```
Seçtiğiniz disk sabit bir MBR disk değil. ACTIVE komutu sadece sabit MBR disklerinde kullanılabilir şeklindedir.

Bu hata genellikle, bir UEFI sisteminin disk bölümünü etkinleştirmeye çalıştığınızda ortaya çıkar. Ancak, ACTIVE komutu yalnızca BIOS/MBR tabanlı bir sisteminiz olduğunda çalışır. Bu nedenle, UEFI sistemlerde disk türü MBR yerine GPT'dir.

Hata mesajı çözmek için birkaç adım var.  UEFI'yi devre dışı bırakmanız veya diski sabit bir MBR diski haline getirmeniz gerekebilir. Ancak bu işlemler öncesinde verilerinizi harici bir sürücüye yedeklemeniz önemlidir.

UEFI'yi devre dışı bırakmak için, bilgisayarı Gelişmiş Başlangıç Seçenekleri'ne başlatarak ve UEFI Bellenim Ayarları altında Güvenli Önyükleme seçeneğini kapatmanız gerekir. İşiniz bittiğinde, Eski Desteği etkinleştirdiğinizden emin olun, değişiklikleri kaydedin ve bilgisayarınızı yeniden başlatın.

Önyükleme yöneticisini düzeltmek için, Komut İstemi'ni açın ve BCD'yi yeniden oluşturmak için gerekli komutları kullanın.

>BCD, Binary-Coded Decimal (İkili Kodlu Onluk Sayı Sistemi) kısaltmasıdır. Bu sistemde onluk sayılar 4 bitlik ikili sayılarla ifade edilir. BCD, hesaplama ve gösterim kolaylığı sağladığı için özellikle elektronik cihazlarda sıklıkla kullanılır.



Eğer bu yöntemle sorunu çözemiyorsanız, önyüklenebilir bir Windows 10 USB sürücüsü yapmanız ve ardından bilgisayarınızı kullanarak başlatmanız gerekebilir.

Son olarak, diski MBR'ye dönüştürmek için, dosya sisteminizi GPT'den MBR'ye değiştirmeniz gerekmektedir. Ancak bu işlem sırasında mevcut verilerinizi kaybedeceğiniz için önceden yedeklemeniz önemlidir.



---
Sorunu ve çözümü tanımladığımıza göre şimdi sırasıyla işlemlere geçebiliriz.


**Hata şunu belirtir:**

```
The selected disk is not a fixed MBR disk. The ACTIVE command can only be used on fixed MBR disks.
```

![screenshot](https://github.com/caglarj/fixed_mbr_disk/blob/a9d869f574c39dba30e8860f1d3109e7b5739a79/4CFFBCE9-DF18-4630-9944-3E163145B776.jpeg)


Seçili disk sabit bir MBR diski değil. ACTIVE komutu sadece sabit MBR disklerinde kullanılabilir.



Hata yalnızca UEFI Sistem Bölümünde bir disk bölümünü etkinleştirmeye çalıştığınızda ortaya çıkar. Ancak komut sadece BIOS/MBR tabanlı bir sisteminiz olduğunda çalışır. UEFI yönteminin etkin bölüm kavramı yoktur. Bir UEFI sisteminiz olduğu için disk türü MBR yerine GPT'dir. Özetlemek gerekirse, BIOS'un MBR disk türüne, UEFI'nin ise GPT tipi diske ihtiyacı vardır.

Seçilen disk sabit bir MBR diski değil

"ACTIVE komutu yalnızca sabit MBR disklerinde kullanılabilir" sorununu çözmenize yardımcı olabilecek birkaç düzeltme var. 

UEFI'yi devre dışı bırakmanız veya bir diski sabit bir MBR disk haline getirmeniz gerekebilir. BIOS/MBR sisteminde “INACTIVE” komutunu kullanırsanız aynı hata oluşabilir.

1. UEFI'yi Devre Dışı Bırak
2. Boot yöneticisini düzelt
3. Diski MBR’ye dönüştürün.

>ÖNEMLİ: Başlamadan önce verilerinizi harici bir sürücüye yedeklemeyi unutmayın.

1. UEFI'yi devre dışı bırak

BIOS ayarlarında Güvenli Önyüklemeyi devre dışı bırakmanız gerekebilir.  Bilgisayarı Gelişmiş Başlangıç ​​Seçeneklerinde önyükleyerek ve UEFI Ürün Yazılımı Ayarları altındaki Güvenli Önyükleme seçeneğini kapatarak yapılır.  Bittiğinde, Eski Desteği etkinleştirdiğinizden emin olun.  Değişiklikleri kaydedin ve bilgisayarınızı yeniden başlatın.

Her OEM'in seçenekleri uygulama şekli vardır. Güvenli Önyükleme genellikle Güvenlik > Önyükleme > Kimlik Doğrulama Sekmesi (Security > Boot > Authentication Tab) altında kullanılabilir. Devre Dışı olarak ayarlayın.

Güvenli Önyüklemeyi devre dışı bırakmak bilgisayarınızı “daha az güvenli” hale getireceğinden bunu geçici bir önlem olarak kullanın. 

2. Önyükleme Yöneticisini Düzeltin

Gelişmiş Başlangıç Seçeneklerine erişebiliyorsanız, Komut İstemi'ni açın ve BCD'yi yeniden oluşturmak için kullanın.

Bunu yapamıyorsanız, önyüklenebilir bir Windows 10 USB sürücüsü yapmanız ve ardından bilgisayarınızı kullanarak başlatmanız gerekecektir. Ardından, İleri'ye tıklamak için Hoş Geldiniz Ekranını aldığınızda ve ardından pencerenin sol alt kısmındaki Bilgisayarınızı Onar'a tıklayın.

Ardından Sorun Giderme > Gelişmiş Seçenekler > Komut İstemi'ne (Troubleshoot > Advanced Options > Command Prompt) tıklayın.

Şimdi, Komut İstemi penceresini açtıktan sonra, sırayla aşağıdaki komutları tek tek çalıştırın –




```
bootrec /FixMbr

bootrec /FixBoot

bootrec /RebuildBcd

```

Son olarak, Komut İstemi penceresini kapatın, bilgisayarınızı yeniden başlatın ve yardımcı olup olmadığına bakın.

3.  Diski MBR'ye dönüştürün

Sürücünün Dosya Sistemini GPT'den MBR'ye değiştirebilirsiniz. Ancak bunu yapmadan önce, mevcut verilerinizi kaybedeceğiniz için verilerinizi önce harici bir sürücüye yedekleyin.

Bunu yaptıktan sonra, Önyüklenebilir bir Windows 10 Ortamı oluşturun. Ondan önyükledikten sonra, tıklayın

On Bilgisayarınızı ilk Windows 10 kurulum kurulum penceresinde onarın. Aldığınız seçeneklerden işletim sistemi bölümünü seçin ve İleri'ye tıklayın.

Sistem Kurtarma Seçenekleri kutusunda Komut İstemi'ni seçin ve komutu yazın



```
diskpart
```



Bu, Komut İstemi içinde Diskpart yardımcı programını başlatacaktır. Sonra ikisinden birini yazın-
```
list disk

```


Veya
```
list volume
```
Bu komutlar, tüm Disk bağlantılarını veya oluşturulan bu disklerdeki tüm bölümleri listelemenize yardımcı olacaktır.

Buradan girdiğiniz liste komutuna bağlı olarak bir komut seçmeniz gerekecek.

Komutları Yazın-

```
select disk #
```
Veya
```
select volume #
```
Enter'a basın. Bu, seçmek istediğiniz Diski veya Bölümü seçecektir.

Son olarak, yazın-
```
clean
```
Enter'a basın. Bu, tüm verilerinizi kaldıracak ve sürücünüzü temizleyecektir.

Son olarak, seçim birimini MBR olarak dönüştürmek için aşağıdakileri yazın,
```
Convert MBR
```
Bilgisayarınızı yeniden başlatın ve bunun sorunlarınızı çözüp çözmediğini kontrol edin.


sorun özet :

Seçili disk sabit bir MBR diski değil. ACTIVE komutu sadece sabit MBR disklerinde kullanılabilir.

Seçilen disk Windows 10'da sabit bir MBR disk hatası
