<p align="center">
  <img src="https://miro.medium.com/max/560/1*-F2WdLOf2GN0BUcDh02t_g.png"/>
</p>


# Nedir Bu DevOps?
DevOps’u araştırıp anlamaya çalıştığım şu süreçte bildiklerimi ve öğrendiklerimi taze tutmak amacıyla, edindiğim bilgileri burada paylaşmak istiyorum. Kendi adıma her ne kadar DevOps’ u araştırmaya geç kaldığımı düşünsem de birilerinin erkenden keşfedip öğrenmesine vesile olmak dileklerimle. Bu kadar lafügüzaf yeter sadede gelelim artık.,

DevOps’u araştırırken öncelikle büyük şirketlerin tanımlarını inceleyerek işe koyuldum. Bu alanda başarılı olan 3 büyüklerin DevOps tanımını da buraya bırakmak istiyorum.

> - **Google:** Yazılım teslim hızını artırmayı, hizmet güvenilirliğini iyileştirmeyi ve yazılım paydaşları arasında ortak mülkiyet oluşturmayı amaçlayan organizasyonel ve kültürel hareket
> - **Microsoft:** Geliştirme (Dev) ve işlemlerin (Ops) bir bileşeni olan DevOps müşterilere sürekli olarak değer sunmak için bir araya gelen kişiler, süreçler ve teknolojiler bütünüdür.
> - **Amazon:** DevOps, kurumların ürünleri geleneksel yazılım geliştirme ve altyapı yönetim süreçlerini kullanan kurumlara göre daha hızlı geliştirmesini ve iyileştirmesini sağlayarak, uygulama ve hizmetleri yüksek hızda sunma becerisini artıran kültürel felsefelerin, yöntemlerin ve araçların birleşimidir.

Ben de bu tanımlardan yola çıkarak kendi perspektifimden DevOps’u **developer** ve **operations** takımlarının iş birliği sayesinde daha kaliteli uygulamaları daha hızlı şekilde müşteriye ulaştırmayı hedefledikleri bir felsefe olarak tanımlamak istiyorum.
### **DevOps Nasıl Ortaya Çıktı?**
Aslında “DevOps” anlamlı bir kelime değil. Developer(Dev) ve Operations(Ops) kelimelerinin kısaltması. Bu kültürün temelleri John Allspaw ve Paul Hammond’un Flickr’daki Geliştirme ve Operasyonlardan bahsettiği konferansta atılıyor. Bu iki Flickr çalışanı nasıl günde 10'dan fazla dağıtım yaptıklarını ve çalışma ortamını anlatıyor. DevOps olarak tanımlamıyorlar fakat aynı yıl Patrick Debois Belçika’da DevOps günü düzenliyor. #DevOps hashtag’ i burada kullanılıyor ve artık bu kültür DevOps olarak kullanılmaya başlanıyor. Günümüzde de DevOps’un babası olarak Patrick Debois biliniyor.
### **Peki DevOps Nasıl Oluşuyor?**
DevOps temelde Dev ve Ops takımlarının iş birliği içerisinde çalışmasıyla oluşuyor.

<p align="center">
  <img src="https://miro.medium.com/max/560/1*C-h4Vd4qZUiaJvBjqikNKw.png"/>
</p>

**Dev Takımı** büyük ölçüde uygulamanın planlanması, kodlanması, build ve test işlemlerinden sorumlu.

**Ops Takımı** büyük ölçüde uygulamanın kullanılacağı ortamın tasarlanması ve bu ortamın devamlılığının sağlanmasından sorumlu. aynı zamanda Ops takımı uygulamaları monitoring ederek sistemde oluşacak sorunları dev takımına iletir.

<p align="center">
  <img src="https://miro.medium.com/max/560/1*YPz5octfJ9jY4QF95tFAeA.png"/>
</p>

Bu sonsuzluk diyagramını kullanmadan DevOps anlatıldığı görülmemiş bir şey. Mutlaka araştıran ya da anlatan herkesin kullandığı bir görsel bu. Ben de geleneği bozmak istemem. Aslında bu görsel DevOps sürecini çok güzel özetliyor. Dev takımının plan=>code=>build=>test aşamasından sonra uygulamayı Ops takımına devretmesi gösteriliyor. Hata oranı en aza indirgenmiş bu projeyi Ops takımını deploy=>operate=>monitoring aşamalarıyla sürekli tesliminin sağlayıp oluşan ya da oluşabilecek aksaklıkları dev takımına bildiriyor. Dev takımı da bu sorunlara karşı yeni çözümler planlayıp işlem bu şekilde sonsuz bir döngüde devam ediyor.

DevOps kültüründe iş birliği ve ekiplerin uyum içinde çalışması en önemli şey. Ben DevOps’u bir takım oyununa benzetiyorum. Burada her oyuncu tabiri caizse elini taşın altına sokmalı. Dev takımı da Ops takımı da üzerine düşen sorumluluğu almalı. İki ekip de beraber çalıştıkça ve süreç otomatize edildikçe projenin sürdürülebilirliği artıyor. Her iki ekip de karşılıklı olarak birbirini beslediği için hızla gelişen teknolojiye ayak uydurabilmek için sürekli öğrenme ve gelişme DevOps kültüründe önemli hale geliyor.
### **DevOps’un Avantaj ve Dezavantajları**
#### *Avantajları:*

- İş birliği arttıkça pazarlama süresi doğal olarak azalır.
- Teknolojinin sürekli gelişmesiyle pazara ayak uydurmak gerekir ve DevOps buna ortam sunar.
- Süreç bir döngü halinde ilerlediği için devamlılık sağlanır.
- DevOps ile süreç otomatize edildiği için hızlı ürün ortaya çıkar ve insan hata riski ortadan kalktığı için güvenilirlik sağlanır.
- İki ekip beraber bu süreci yönettiği için de ortalama kurtarma süresi de hızlanır.

#### *Dezavantajları:*
- Ops ekipleri monitoring sürecinde sistemde oluşan sorunları dev ekibine bildiriyor. Bu işlem otomatik olduğu için dönüşler hızlı olur. Bu yüzden dev takımı oluşan sorunlara karşı daha hızlı çözüm üretmek zorunda kalır. Bu dev takımı için daha fazla efor saf etmesine sebep olduğundan geliştiriciler tarafından bir dezavantajken müşteri açısından avantaj olabilir.
- Süreç otomatikleştikçe güvenlik riskleri oluşabilir.
- Sürekli gelişen ve ilerleyen teknolojiye ekiplerin ayak uydurma süreci yıpratıcı olabilir.

( DevOps’un dezavantajlarını bulmam avantajlarına oranla biraz daha zor oldu. Bu kültürü benimseyenler çok dezavantajlı bulmuyor sanırım.)

### **DevOps Yöntemleri**
- **Sürüm Denetimi (Version Control):** Geliştiricilerin koddaki hataları güncellemeleri versiyonlar olarak yönetmesi.
- **Çevik Yazılım Geliştirme (Agile Software Development):** Çevik geliştirme ekip işbirliğiyle beraber müşteri memnuniyetini de sağlayan bir yazılım geliştirme yöntemidir. Bu yöntem ile sürekli iyileştirme sağlanır.
- **Kod olarak Altyapı (Infrastructure as Code):** Sistem ekiplerinin kaynakların yönetimi ve dağıtımını otomatikleştirmesine yardımcı olan bir yöntem.
- **Yapılandırma Yönetimi (Configuration Management):** Kaynakların ve durumun yönetilmesi.
- **Sürekli İzleme(Continuous Monitoring):** Dağıtım süreci başladığında sistemin izlenip ayakta kalması sağlanır.
- **Sürekli tümleştirme (Continuous Integration(CI)):** Sürekli entegrasyon ile güncellenen kod sürekli test ve analiz edilir. Bu da geliştiricilerin çok az riskle yüksek kaliteli çözüm üretmesine olanak sağlar.
- **Sürekli dağıtım ve sürekli teslim (Continuous Delivery & Continuous Deployment(CD)):** Sürekli entegrasyon aşamasının başarıya ulaşmasının ardından projenin otomatize bir şekilde dağıtımının yapılması sürecidir.
