# Modüler Frontend Tasarım: Component’lerin Temel İlkeleri ve Kullanımı

![Nazif Can Durgut son.png](./images/Nazif_Can_Durgut_son.png)

# Component Nedir?

Component dediğimiz şey tekrar kullanılabilen parçalardır. En küçük parçadan en büyük parçaya her şey component olabilir. HTML içerisinde kullandığımız elementlerde aslında birer componenttir. Fakat biz frontend geliştirirken HTML’in sunduğu hazır componentler bize yetmez ve biz kendi özel componentlerimizi yazarız.

**HTML SELECT:**

![Untitled](./images/Untitled.png)

**CUSTOM SELECT:**

![Untitled](./images/Untitled-1.png)

# Component Kullanmanın Avantajları

• Bir kere yazıldıktan sonra istenilen her yerde kullanabilme imkanı sunar.

• Component yapısı sayesinde kod tekrarlarından kaçınılır.

• Componentler geliştirilen projenin yapısına göre mantıksal parçalara bölünebilir.

• Veriler **Props** olarak gönderilir.

• Tarayıcılar arasında ki farkları da etkisiz kılar.

• Test etmesi daha kolaydır.

_Büyük parçalara göre ufak parçaların test edilmesi daha kolaydır._

# Component Kullanmanın Dezavantajları

• Componentler belli mantık çerçevesinde parçalanmazlarsa geliştirme aşamasında zorluk yaratır.

• Component isimlendirmeleri aynı şekilde belli bir mantık çevresinde olmazsa kafa karışıklığına neden olabilirler.

• Sınırlı sayıda konfigürasyon.

# Component’leri Doğru Ayırmak/Parçalamak

Componentleri parçalarken belli bir mantık çerçevesinde parçalamamız gerekir. Yeniden kullanılabilirliğine dikkat etmemiz gerekir. Birebir aynı ama çok ufak farklar olan componentleri ayrı ayrı yazmak yerine tek bir component olarak yazıp props değeri ile bu farklılığı yaratabiliriz.

# Workshop Örneği

Bu workshopta örneğimiz bir kanban olacak. Aşağıdaki gibi bir arayüzümüz var. Öncelikle bu arayüzü inceleyelim. Ne ve neresi component olacak buna karar verelim.

![0.jpg](./images/0.jpg)

1. İlk olarak arayüze baktığımızda bir tane **KanbanBoard** isimli bir componentimizin olması gerektiğini görüyoruz. Çünkü bu component çok fazla alt kırılımı olan bir component, ve biz bu componenti başka bir sayfada da kullanmak isteyebiliriz.

![1.jpg](./images/1.jpg)

**KanbanBoard** componentimiz butun bir yapıyı tek bir arada tutuyor ve tek bir props alıyor*(örneğimize göre)*.

### KanbanBoard Props:

![Untitled](./images/Untitled-2.png)

1. **KanbanBoard** componentimizi incelediğimizde içerisinde birbirine benzer yapılar olduğunu görüyoruz ve bunları da component hale getirebiliriz. Bu componentlerimiz ise **KanbanColumn** componentleri olacak.

![2.jpg](./images/2.jpg)

**KanbanColumn** componentimiz içerisinde başlığı ve görevleri bir arada tutuyor.

### KanbanColumn Props:

![Untitled](./images/Untitled-3.png)

1. **KanbanColumn** componentimiz içerisinde ise **bir adet** sütun başlığı var. bu sütün başlığını component yapmamıza gerek yok. Çünkü biz **KanbanColumn** componentini **for/map** ile döneceğiz ve her sütun içerisinde zaten bir adet var ve bu başka bir yerde kullanılmayacak. Ama içerinde bir adet o sütun içerinde kaç tane kart olduğunu gösteren bir **Badge** componenti var.

**Badge** componenti sadece kanbana ait değil **projenin her yerinde kullanılacak bir component olduğundan ismine de genel bir isim veriyoruz.**

![3.jpg](./images/3.jpg)

**Badge** componentimiz **KanbanColumn** içerisinde kaç adet görev varsa onun sayısını tutuyor.

### Badge Props:

![Untitled](./images/Untitled-4.png)

1. **KanbanColumn** componentini incelemeye devam ettiğimizde içerisinde yine tekrar eden alanlar bulunmakta bu alanları da **KanbanTask** isimli bir component olarak ayırabiliriz.

![4.jpg](./images/4.jpg)

**KanbanTask** componentimiz içerisinde görevin açıklamasını, etiketleri, yaratılış tarihini, görevin atandığı kullanıcıyı ve yorum sayısını gösteriyor.

### KanbanTask Props:

![Untitled](./images/Untitled-5.png)

### KanbanTask Props(alternative):

![Untitled](./images/Untitled-6.png)

1. **KanbanTask** componentimiz içerisinde ise iki adet componentimiz daha var. Bunlar **Tag** ve **Avatar** componentleri. Bu component isimlerinde de **Kanban**… diye başlamadık çünkü bu componentlerde projenin yer yerinde kullanılabilecek componentler.

![6.jpg](./images/6.jpg)

**Tag** componentimiz **KanbanTask** içerisindeki etiketlerin renkli gösterimlerini sağlıyor.

### Tag Props:

![Untitled](./images/Untitled-7.png)

**Avatar** componentimiz **KanbanTask** içerisindeki görevin atandığı kullanıcının görselini gösterir.

### Avatar Props:

![Untitled](./images/Untitled-8.png)

Arayüzümüzü teoride inceledik ve parçalayacağımız componentleri ve componentlerin propslarini belirledik. Şimdi pratiğe geçelim…
