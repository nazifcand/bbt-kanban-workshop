# Modüler Frontend Tasarım: Component’lerin Temel İlkeleri ve Kullanımı

![Nazif Can Durgut.png](https://user-images.githubusercontent.com/36958113/242708166-f5919962-22c6-4d80-b948-d3fb13244489.png)

# Component Nedir?

Component dediğimiz şey tekrar kullanılabilen parçalardır. En küçük parçadan en büyük parçaya her şey component olabilir. HTML içerisinde kullandığımız elementlerde aslında birer componenttir. Fakat biz frontend geliştirirken HTML’in sunduğu hazır componentler bize yetmez ve biz kendi özel componentlerimizi yazarız.

**HTML SELECT:**

![Untitled](https://user-images.githubusercontent.com/36958113/242708203-86c1e82c-ef4b-4065-ad1c-b2217950ff0c.png)

**CUSTOM SELECT:**

![Untitled](https://user-images.githubusercontent.com/36958113/242708173-3f0cf223-dcbd-4dd0-bd6f-304ba6581f65.png)

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

![0.jpg](https://user-images.githubusercontent.com/36958113/242708144-70a0440e-e519-4241-9def-f7b0f4610001.jpg)

1. İlk olarak arayüze baktığımızda bir tane **KanbanBoard** isimli bir componentimizin olması gerektiğini görüyoruz. Çünkü bu component çok fazla alt kırılımı olan bir component, ve biz bu componenti başka bir sayfada da kullanmak isteyebiliriz.

![1.jpg](https://user-images.githubusercontent.com/36958113/242708149-92e7871f-2ff9-4f41-b4e9-05156e549ce2.jpg)

**KanbanBoard** componentimiz butun bir yapıyı tek bir arada tutuyor ve tek bir props alıyor*(örneğimize göre)*.

### KanbanBoard Props:

![Untitled](https://user-images.githubusercontent.com/36958113/242708175-601b51bc-6416-47e7-8a5e-42a3c845fd64.png)

1. **KanbanBoard** componentimizi incelediğimizde içerisinde birbirine benzer yapılar olduğunu görüyoruz ve bunları da component hale getirebiliriz. Bu componentlerimiz ise **KanbanColumn** componentleri olacak.

![2.jpg](https://user-images.githubusercontent.com/36958113/242708151-b4262a9f-8a67-4568-a8e6-9be307cfc837.jpg)

**KanbanColumn** componentimiz içerisinde başlığı ve görevleri bir arada tutuyor.

### KanbanColumn Props:

![Untitled](https://user-images.githubusercontent.com/36958113/242708156-9bbb4630-e118-483d-b585-ed458f5fca34.jpg)

1. **KanbanColumn** componentimiz içerisinde ise **bir adet** sütun başlığı var. bu sütün başlığını component yapmamıza gerek yok. Çünkü biz **KanbanColumn** componentini **for/map** ile döneceğiz ve her sütun içerisinde zaten bir adet var ve bu başka bir yerde kullanılmayacak. Ama içerinde bir adet o sütun içerinde kaç tane kart olduğunu gösteren bir **Badge** componenti var.

**Badge** componenti sadece kanbana ait değil **projenin her yerinde kullanılacak bir component olduğundan ismine de genel bir isim veriyoruz.**

![3.jpg](https://user-images.githubusercontent.com/36958113/242708158-e52e9627-c8fe-4a68-9d3c-c204d5f91bc7.jpg)

**Badge** componentimiz **KanbanColumn** içerisinde kaç adet görev varsa onun sayısını tutuyor.

### Badge Props:

![Untitled](https://user-images.githubusercontent.com/36958113/242708183-d78d5ce9-746e-4376-99ca-7d4308bbbfc1.png)

1. **KanbanColumn** componentini incelemeye devam ettiğimizde içerisinde yine tekrar eden alanlar bulunmakta bu alanları da **KanbanTask** isimli bir component olarak ayırabiliriz.

![4.jpg](https://user-images.githubusercontent.com/36958113/242708158-e52e9627-c8fe-4a68-9d3c-c204d5f91bc7.jpg)

**KanbanTask** componentimiz içerisinde görevin açıklamasını, etiketleri, yaratılış tarihini, görevin atandığı kullanıcıyı ve yorum sayısını gösteriyor.

### KanbanTask Props:

![Untitled](https://user-images.githubusercontent.com/36958113/242708191-991f108e-f578-45e1-888a-b7c0d673e1e9.png)

### KanbanTask Props(alternative):

![Untitled](https://user-images.githubusercontent.com/36958113/242708194-559833ff-bb93-425f-ba72-ad44625edc05.png)

1. **KanbanTask** componentimiz içerisinde ise iki adet componentimiz daha var. Bunlar **Tag** ve **Avatar** componentleri. Bu component isimlerinde de **Kanban**… diye başlamadık çünkü bu componentlerde projenin yer yerinde kullanılabilecek componentler.

![6.jpg](https://user-images.githubusercontent.com/36958113/242708162-5f6fd630-4a49-41d3-b6e3-83f03999a1f3.jpg)

**Tag** componentimiz **KanbanTask** içerisindeki etiketlerin renkli gösterimlerini sağlıyor.

### Tag Props:

![Untitled](https://user-images.githubusercontent.com/36958113/242708198-362f4bf0-3765-40d2-8361-3b39d144ac9b.png)

**Avatar** componentimiz **KanbanTask** içerisindeki görevin atandığı kullanıcının görselini gösterir.

### Avatar Props:

![Untitled](https://user-images.githubusercontent.com/36958113/242708200-84cce7ee-ff6a-42c9-b323-16d49729134a.png)

Arayüzümüzü teoride inceledik ve parçalayacağımız componentleri ve componentlerin propslarini belirledik. Şimdi pratiğe geçelim…
