<p align=“center”>
<img src="https://miro.medium.com/max/875/1*djlFztuk2HlnG7rtM-qc3w.png"/>
</p>

AZURE DEVOPS İLE CI/CD SÜREÇLERİ
DevOps’u incelemeye başlayan herkes Continuous Integration (CI) ve Continuous Delivery (CD) kavramlarına denk gelecektir. Bu makalede Azure DevOps ile CI/CD kavramlarına açıklık getirmeye çalışacağım ama öncelikle biraz Azure DevOps platformundan bahsetmek istiyorum. Azure DevOps, DevOps süreçlerini uygulamamıza ortam sağlayan Microsoft’un sunmuş olduğu bir platform. Azure DevOps ile ekipler arası iş planları, sürüm denetimleri, versiyon yönetimi yapabilir, proje testleri gerçekleştirebilirsiniz. Azure DevOps için kısaca uçtan uca yazılım süreçlerinizi kolayca yönetmenizi sağlayan bir ortam diyebilirim. Azure DevOps platformunda tüm bu süreçleri kolayca yönetmek için bazı bileşenler bulunur. Bu bileşenler;

Azure Boards: Planlamaları yapmak, projeleri takip etmek, code defectlerini kayıt altına almak için,

Azure Repos: Proje kodlarını Git, TFVC (Team Foundation Version Control) yöntemleriyle yönetebilmek için,

Azure Pipelines: Uçtan uca CI/CD süreçlerini yönetmek için,

Azure Test Plans: Uygulamaları sürekli test edebilmek için,

Azure Artifacts: CI/CD süreçleri için gerekli olan maven, npm, nuget gibi paketleri entegre edebilmek için,

kullanılabilir. CI/CD süreçlerini yönetirken Azure DevOps ’un bu servislerini kullanmak hem güvenlik açısından hem de zaman yönetimi açısından kullanım kolaylığı ve avantajı sağlıyor.

CONTINUOUS INTEGRATION (CI)
Günümüz gelişen teknolojisinde ortaya konulan yazılım projeleri birçok alt yazılımın tümleştirilmesinden oluşur. Bu alt yazılım parçalarının her birinde farklı birimler ya da farklı yazılım geliştiriciler rol alabilir. Ortaya koyulan proje birden fazla kişi tarafından geliştirildiği için karmaşıklık artar. Geliştiricilerden birinin yaptığı hata tüm projeyi etkileyebilir ve bu hatanın tespiti uzun süreler alabilir. Bu gibi durumlarda kurtarıcı olan şey ise Continuous Integration sürecini projeye dahil etmektir.

Continuous Integration (CI) dilimize “Sürekli Tümleştirme” olarak çevirdiğimiz, ekipçe veya ekiplerce ortaya koyulan bir projede, kod üzerinde yapılan her değişikliğin otomatikleşmesi ve yapılan her değişiklikten, proje üzerinde çalışan herkesin haberdar olmasının sağlanmasıdır. Bir projeye başlanıldığında ekipler kendi geliştirdikleri kısımlarda sürekli olarak iyileştirmelerle uygulamayı daha efektif hale getirmeye çalışır. Gün sonunda iyileştirilen kısımların birbiriyle uyum içerisinde olması önemlidir. Bunu sağlamak da geleneksel yöntemlerle hem maliyetli hem de zaman olarak büyük bir kaynak tüketimine neden olur. Günümüz gelişen teknolojisinde Continuous Integration ile bunu sağlamak daha kolay ve pratik.

Continuous Integration ile proje bazında bütünlüğü sağlamak daha kolay hale gelir. Geleneksel yazılım geliştirme süreçlerini uygulayan ekipler, gün içerisinde tek bir entegrasyon yapabilirken CI süreciyle aynı gün içerisinde birden fazla entegrasyon yapıp otomatik olarak testlerini gerçekleştirebilirler.

<p align=“center”>
<img src="https://miro.medium.com/max/393/1*Uxw5YfnZih9Qno3pqCQTLg.png"/>
</p>

Yukarıdaki görsel Continuous Integration sürecini çok güzel şematize eden ve bu konuyu ele alan kişiler tarafından da sıkça kullanılan bir görsel. Continuous Integration ile süreç, yazılım geliştiriciler tarafından kodların geliştirilmesiyle başlar. Projede bulunan geliştiricilerin erişim sağlayabildiği ortak bir repository ’e kodların sürekli olarak commit edilmesi sağlanır. Sonrasında kodlar otomatik olarak build edilir ve otomatik testler gerçekleştirilir. Buradan dönen hatalara göre iyileştirmeler, güncellemeler yapılır. Testlerden dönen hatalar sıfıra veya önemsenmeyecek boyuta gelene kadar bu döngü devam eder ve nihayetinde tüm süreç denetlenebilir halde geliştirilmiş olur.

Continuous Integration süreciyle sistem sürekli olarak çalışır ve kontrol edilebilir durumda olur. Projede geliştirilen tüm kaynak kodlar merkezi bir kaynak kodu yönetim aracında tutulduğu için projede yer alan kişiler kodların diledikleri versiyonuna her zaman erişebilir durumda olurlar. Geliştiricilerin yaptığı her değişiklikten tüm takımın haberdar olması, süreci hızlandırır. Sürecin otomatikleşmesi daha hızlı hata tespitine olanak sağlar. Geleneksel yazılım yaşam döngüsüne oranla daha kolay bir yazılım yaşam döngüsü sağlanmış olur. Manuel olan testlerdeki hata payını düşünürsek testlerin otomatize olması daha güvenilir sonuçlar ortaya koyar ve bu da kod kalitesinin artmasını sağlar. Continuous Integration kaynak yönetimini kolaylaştırır ve aynı zamanda ortaya koyulan yazılımın kalitesinin artmasını sağlar. Projenin geliştirme süresini kısaltır ve aynı zamanda da proje üzerindeki işçilik maliyetini azaltır. Yazılımın sürekli hazır halde ve test edilmiş entegre bir sürümü hazırda bulunur.

Azure DevOps ürünü Continuous Integration süreci için birçok özellik sağlar. Continuous Integration süreci tasarlandıktan sonra Azure DevOps ortamında kolay bir şekilde yönetilebilir. Azure DevOps platformunda CI sürecini gerçekleştirmek için kodlarınızın Azure Repos üzerinde bulunmasına gerek yoktur. Kodlarınızın git destekleyen herhangi bir yerde olması yeterlidir. CI sürecini Azure DevOps platformunda gerçekleştirebilmek için öncelikle build pipeline oluşturmak gerekli. Pipeline’ı oluşturmak için kodlarınızın nerede olduğunu (Azure Repos, GitHub, Bitbucket vb.) belirtmeniz yeterli. Azure DevOps burada pipeline’ınız için birçok build şablonu sunuyor. Projeniz için php, Xamarin, python, ASP.NET , maven gibi birçok build şablonu Azure DevOps içerisinde bulabilirsiniz. Hazır şablonlardan size uygun olanını ya da boş olan bir şablonu kullanabilirsiniz. Sonrasında projeniz için gerekli job ve taskleri ekleyerek Continuous Integration seçeneğini aktif ederseniz oluşturduğunuz pipeline otomatik olarak çalışacaktır.

CONTINUOUS DELIVERY & CONTINUOUS DEPLOYMENT (CD)
Continuous Delivery & Deployment süreci başarılı bir şekilde gerçekleşmiş olan Continuous Integration aşamasından sonra başlar. Continuous Delivery (CD) dilimize “Sürekli Teslim” olarak çevirdiğimiz, entegrasyonun başarılı olması durumunda, projenin build’inin alınıp deploya hazır olduğu kısımdır. Continuous Delivery verimli ve hızlı yazılım yayınlamayı sağlar. Teslim işlemleri tamamlanmadan hataları tespit ederek yönetmeye imkan tanır. Üretilen yazılımların daha sık yeni versiyonlarını yayınlamayı sağlar. Continuous Deployment ise dilimize “Sürekli Dağıtım” olarak çevirdiğimiz, testlerden geçmiş ve onaylanmış projenin canlı ortama alınması kısmıdır. Kodu makineler arası dağıtım yapmak geleneksel yöntemlerle hataya çok müsait olmasına rağmen Continuous Deployment ile hata payını en aza indirmek mümkündür.

<p align= “center”>
<img src="https://miro.medium.com/max/875/1*UbiClNijVPbObFCHLCyUuA.png"/>
</p>

Deployment ve Delivery kavramlarının sektörde sık sık birbiri yerine kullanıldığına denk geliyoruz. İki kavram için de CD kısaltması kullanıldığı için karıştırılmaya müsait hale geliyor. Continuous Delivery, Continuous Deployment aşamasından önce gelir. İki kavram arasındaki temel fark; Continuous Delivery’ nin insan doğrulamasına ihtiyaç duyup manuel şekilde yürütülürken, Continuous Deployment’ ın ise otomatize edilmiş bir süreç olmasıdır.

Continuous Delivery ve Continuous Deployment sürecini anlamak için bu kavramları gündelik yaşamdan bir örnekle açıklamak istiyorum. İnternet üzerinden bir paket çikolata sipariş ettiğinizi düşünelim. Çikolatayı internet üzerinden sipariş verdikten sonra kargo firması paketinizi size getiriyor. İşte bu kısma yazılım geliştirme sürecinde Continuous Delivery diyoruz. Gelen paketi alıp, ürünü kontrol ediyorsunuz ve siparişiniz doğru gelmiş mi yoksa ürün hatalı mı diye kontrol ediyorsunuz. Eğer yanlış ürün gönderildiyse iade edebilirsiniz. Doğru ürün elinize ulaştıysa kargoyu kabul ediyorsunuz. Buna da yazılım geliştirmede Continuous Deployment diyoruz. Yazılım geliştiriciler de aynı bu örnekteki gibi gelen paket dağıtıma uygun hale gelene kadar otomatik testlerden geçirerek deploy edilmeye hazır hale getirir. Continuous Deployment son kullanıcının isteklerine hızlı ve güvenilir dönüşler sağladığı için hem yazılım geliştiricilere hem de müşterilere avantaj sağlar.


> https://docs.microsoft.com/en-us/devops/deliver/what-is-continuous-delivery

> https://docs.microsoft.com/sk-sk/devops/develop/what-is-continuous-integration

> https://docs.microsoft.com/en-us/sharepoint/dev/spfx/toolchain/implement-ci-cd-with-azure-devops
