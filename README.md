# Database-Management-and-SQL-Performance-in-Java    
### Bu makalede, Java programlama dilinde veritabanı yönetimi konusunu ele alacak ve SQL performansını artırmak için izolasyon seviyelerinden index optimizasyonuna kadar çeşitli konuları inceleyeceğiz.      
  <br>
   <br>
    
## Spring Transaction Yönetimi - @Transactional Annotasyonu

Transaction, veritabanı üzerinde yapılan birden çok işlemin bir bütün olarak işlenmesini ve hata durumunda bunların geri alınmasını sağlar. Bu sayede veritabanındaki kayıtlarda tutarsızlık oluşması engellenir ve veri bütünlüğü sağlanır.

Spring Framework, transaction yönetimi için bir soyutlama sağlar, bu sayede farklı Transaction API'leri için özel geliştirmeler yapmamız gerekmez. Hem programmatic hem de declarative programlamayı destekler. Böylece transaction yönetimini istediğimiz methodların içinde manuel olarak yapabileceğimiz gibi @Transactional annotasyonunu kullanarak otomatik olarak da yapabiliriz. Bu durumda Spring Container işlemi üstlenir.


## Spring Transaction Isolation Seviyeleri

Isolation, uygulama katmanında birden fazla transaction varsa her bir transaction altında yer alan iş parçacıklarının kullanacağı veriyi yönetmek için kullanılır. Isolation teknolojisi sayesinde birden fazla eş zamanlı transactionları, paralelde birbirlerini etkilemeden çalıştırmamızı sağlar.


## Multithreading

Çoklu iş parçacığı ile programlama, bir programın aynı anda birden fazla iş yapabilme yeteneğidir.

-Java'da bu, **Runnable** arayüzünü uygulayan sınıfların run metodunu override etmesiyle sağlanır.

-**Start** metodu, ana iş akışından farklı bir iş parçacığını başlatır.

-**Sleep**, belirli bir süre boyunca uygulamanın duraklamasını sağlar.

-**Yield**, iş parçacığının durdurulmasını ve diğer iş parçacıklarına öncelik verilmesini sağlar.

-**Interrupt**, uyuyan veya duraklatılan bir iş parçacığını başlatır.

-**Join**, iş parçacıklarının birbirini beklemesini sağlar.

-**IsAlive**, bir iş parçacığının çalışıp çalışmadığını kontrol eder.

-**SetPriority**, bir iş parçacığının çalışma önceliğini belirler.

-**GetPriority**, bir iş parçacığının önceliğini belirler.



## Synchronization

Java'da synchronized anahtar kelimesi, bir kod bloğuna sadece bir iş parçacığının aynı anda erişebileceğini ve diğerlerinin onun bitmesini beklemesi gerektiğini belirtir.

-**Wait**, senkronize edilmemiş bir durumun serbest kalmasını beklemek için kullanılır.
-**Notify**, kilitli bir nesnenin serbest olduğunu bildirir.
-**NotifyAll**, kilitli nesnelerin tümünün serbest olduğunu bildirir.


## Race Condition

Race Condition, birden çok iş parçacığının aynı anda paylaşılan bir hafıza alanına erişip değiştirmesi sonucu ortaya çıkan sorunlardır. Bu durumlar genellikle programların doğru çalışmasını engellerler. Race Condition'ları önlemek için paylaşılan hafıza alanına erişim yapılan kodlar Critical Section içine alınmalıdır.


## Mutex

Mutex, farklı prosesler veya aynı proses içindeki thread'ler arasında senkronizasyonu sağlayan veri yapılarıdır. Mutex'ler, paylaşılan kaynaklara erişim sırasını düzenleyerek race condition'ların önüne geçerler. Mutex, bir iş parçacığının bir kaynağa erişmek istediğinde sahipliğini alarak erişimi kontrol eder.


## Concurrency

Concurrency, birden fazla işin aynı anda yapılabilmesi durumunu ifade eder. Java'da, Concurrency bir çekirdekte gerçekleşirken, Parallelism ise birden fazla çekirdekte gerçekleşir. Concurrency, iş parçacıklarının sırayla çalışmasını sağlarken, Parallelism aynı anda birden fazla iş parçacığının çalışmasını sağlar.


## SQL Primary Key nedir?

SQL’de “Primary Key” (Anahtar Sütun veya Birincil Anahtar), bir ilişkisel veritabanı tablosundaki verilerin benzersiz bir şekilde tanımlandığı bir sütundur. Primary Key, bir tablodaki her bir satırın benzersiz bir kimlikle ayırt edilebildiği ve herhangi bir satırın birincil anahtar değerine sahip olması gerektiği anlamına gelir. Bu, verilerin tutarlılığını sağlamak, veritabanı sorgularını hızlandırmak ve ilişkisel veritabanlarındaki tablolar arasındaki ilişkileri tanımlamak için kullanışlıdır.


## SQL Foreign Key nedir?

SQL’de “Foreign Key” (Yabancı Anahtar), ilişkisel veritabanlarında kullanılan bir kavramdır ve ilişkisel veritabanlarında tablolar arasında ilişkiler kurmayı sağlar. Bir tablodaki bir sütunun, başka bir tablonun anahtar sütunuyla ilişkilendirilmesini ifade eder. Bu ilişki, veritabanı yöneticilerine verilerin tutarlılığını sağlama ve veritabanı tasarımını daha etkili hale getirme konusunda yardımcı olur.


## SQL’de Index nedir?

SQL’de “Index” (İndeks), bir veritabanı tablosundaki verilerin hızlı bir şekilde erişilmesini ve sorgulanmasını sağlayan bir yapıdır. Index, tablonun bir veya daha fazla sütununu kullanarak bu sütunun değerlerini sıralar ve bu sıralamayı bir yapı içinde saklar. Bu sayede veritabanı yöneticileri ve sorgular, verilere daha hızlı ve etkili bir şekilde erişebilirler. Indexler, veritabanı performansını artırma ve büyük veritabanlarında sorgu sürelerini kısaltma açısından önemlidir.


## Clustered Index(Primary Key)

Clustered index’ler tablodaki veriyi fiziksel olarak sıralar. Bir tablo fiziksel olarak sıralandığında tablo üzerinde sadece bir tane clustered index tanımlanabilir. Clustered index için seçilecek kolon veya kolonlar sorgularda en fazla kullanılan kolonlar olmalıdır. 

## Non-Clustered Index

Veriyi mantıksal olarak sıralar. Bu index’lerin leaf node’larında verinin kendisi değil nerede olduğu bilgisi tutulur.Non-clustered Index’ler veriye doğrudan erişemez. Heap üzerinden ya da bir Clustered Index üzerinden erişebilir. Bu Index’in de Clustered Index gibi sık kullanılan kolonlardan oluşturulması gerekir. 

Tüm bu tanımlamaların neticesinde Clustered Index bir kitabın ‘içindekiler’ bölümüne, Non-clustered Index ise sayfa numaralarına benzetilebilir. İçindekiler kısmında olduğu gibi Clustered Index’te yeni veri sıralamadaki/bölümlerdeki uygun yere eklenir. Non-clustered Index’te ise kitapta sayfaların numaralandırma yapısı gibi doğrudan sayfa numarası verilerek yer belirtilir. Clustered Index’ler Non-clustered Index’lere göre daha hızlıdır. Clustered Index’ler depolamanın sıralamasını tutar ve ekstra bir depolama alanına ihtiyaç duymazlar. Non-clustered Indexler ise ayrı bir tablo yapısında tuttuğu için ekstra alana ihtiyaç duyarlar.


## Database Optimizasyonu Nedir?

Veri tabanı optimizasyonu, veri tabanı yapısını ve sorgu optimizasyon tekniklerini değiştirerek veri tabanının performansını iyileştirme sürecidir. Veritabanı tasarımını optimize ederek ve sorgu optimizasyon tekniklerini iyileştirerek sorguların hızını ve verimliliğini artırmak için kullanılır. Ayrıca, verilerin en verimli şekilde düzenlenmesini sağlayarak veri tabanının ölçeklenebilirliğini ve güvenilirliğini artırmaya yardımcı olur.

### -Uygun İndekslemeyi Sağlayın
İndeksleme, veri alma sürecini hızlandırır, ancak aşırı indeksleme ile hiç indeksleme yapmama arasında doğru dengeyi kurmak önemlidir.

### -Tüm Kolonları ( * ) Sorgulamaktan Kaçının
Gereksiz sütunların döndürülmesini önlemek için tümünü yakalama kullanmak yerine sorgular gerekli verileri belirtmelidir.

### -Mümkün Olduğunda Sorguları Birleştirin
Birden çok bağımsız SQL sorgusu oluşturan döngüleri asla kullanmayın. Bunun yerine, süreci hızlandırmak için bu sorguları tek bir istekte gruplandırın.

### -N+1 Sorgudan Kaçının
Bir üst sorgu birden çok alt sorguyu tetikleyecek şekilde iç içe geçmiş sorgulardan kaçının. Bunun yerine, ebeveynin çocukları aynı anda istemesini sağlayın.

### -Kullanılmayan Tabloları Kaldır
Kullanılmayan tablolar, yine de SQL sunucusu tarafından aranmaları gerektiğinden performansta düşüşe neden olur, bu nedenle bunların silinmesi performansı artırmanın iyi bir yoludur.

### -Filtreler için WHERE Kullanın
HAVING ifadeleri, bir sorguyu koşullara göre filtrelemenin bir yolu olabilir, ancak bunu yaparken WHERE çok daha etkilidir.


## SQL’de Stored Procedure (Saklı Yordam) Nedir ?

Veritabanında CRUD gibi işlemlerde, her seferinde kodu tekrar yazmamız ve derlememiz gerekmektedir. Durum böyle olunca hem zaman hem de derleme açısından perormans kaybı olmaktadır. Bu gibi durumlarda Saklı Yordam (Store Procedure), programlamada kullanılan ifadelere göre kod yazmamızı sağlar. Böylece her seferinde aynı işlemleri yapma gereksinimi duymadan zamandan tasarruf etmiş oluruz.

### -Saklı Yordam Oluşturma (CREATE Store Procedure)

Yeni bir Saklı Yordam oluşturmak istediğimizde, CREATE PROCEDURE komutu ve Yordam ismi yazılır, sonrasında @ işareti ile kullanılacak parametreler tanımlanır. Saklı Yordam ismi ve parametreler tanımlandıktan sonra, AS ifadesiyle devam edilip BEGIN ve END ifadeleri arasında saklı yordamda yapılmam istenen sorgu yazılır. Sorguyu çalıştırdığımızda, [OrdersByDate] isminda yeni bir saklı yordam oluşturulur. Oluşturulan bu yordam dakullanıcıdan şipariş başlangıç tarihi, sipariş bitiş tarihi ve siparişin gönderileceği şehir bilgileri girilmesi istenir. Böylece istenilen şehirde belli tarih aralığında şipariş sorgusunu yazmak yerine, oluşturulan saklı yordam çağrılarak gerçekleştirilir.

### -Saklı Yordam Çalıştırma (EXECUTE Store Procedure)

Oluşturduğumuz [OrdersByDate] saklı yordamını çalıştırmak istediğimizde EXEC komutunu kullanırız.

EXEC OrdersByDate
@OrderBeginDate = '2000-01-01',
@OrderAndDate = '2001-01-01',
@ShipCity = 'Ankara';

Şeklinde kullanılır.


## SQL Fonksiyonları Nedir ?

SQL fonksiyonları, veri tabanlarındaki verileri işlemek ve analiz etmek için güçlü bir araçtır. Tek satır fonksiyonları, her bir veri satırını işlemek için kullanılır ve özellikle veri dönüşümleri ve basit hesaplamalar için uygundur.

 Grup fonksiyonları ise, bir veri kümesinin toplu işlenmesi ve analizi için idealdir. Bu fonksiyonlar, toplam, ortalama, maksimum veya minimum gibi işlemleri gerçekleştirir ve gruplandırılmış verilerin özetini sunar.


