<p align=“center”>
<img src="https://miro.medium.com/max/788/1*zHtCt3QtecntikyCz-IN_Q.png"/>
</p>

# Form Recognizer Nedir ?

Azure Form Recognizer Microsoft’un piyasaya sunmuş olduğu Cognitive Servislerden Vision kategorisi içerisinde yer alan bir doküman dijitalleştirme servisi. Cognitive Servisler, geliştiricilerin Yapay Zeka (AI) ve Makine Öğrenmesi (ML) algoritmaları konusunda uzman olmasına gerek kalmadan kullanabileceği servislerden oluşuyor. Vision kategorisindeki servisler adı üzerinde görsel dosyalardan, dokümanlardan data-information extract ettiğimiz servisler. Form Recognizer da bu servislerden yalnızca bir tanesi. Servisi oluşturması ve kullanımı kolay olduğu için piyasada sıklıkla tercih ediliyor. Servisin çıktısı JSON formatında oluyor ve JSON parse ile çıktıları projelerinize kolayca entegre edebiliyorsunuz. Form Recognizer Servisini kullanabilmek için bir Azure account’ unuzun olması ve dokümanların eğitimini gerçekleştirebilmek için de Form OCR Testing Tool adında bir arayüz tooluna ihtiyacınız var.

Servisin iki şekilde kullanımı mevcut. Servisi tamamen bulut ortamında veya tamamen on-premise ortamda kullanabiliyorsunuz.

*Form Recognizer ile PDF, TIFF, JPG, PNG, BMP dosyalasından veri çıkarımları yapabilirsiniz.

## Servisin Cloud Ortamda Kullanımı

Servisi kullanabilmek için öncelikle bir Azure accountu açmak gerekiyor. Azure accountunuz var ise Azure portal(https://portal.azure.com/#home ) üzerinden bir Form Recognizer servisi oluşturuyoruz.

Servisi oluştururken Subscription, Resource group, Region ve servis ismi gibi bilgileri doldurduktan sonra Create edebiliriz.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*tr_09o85cHBVv-QR"/>
</p>

Servisi oluşturduktan sonra servis ile arayüzün bağlantısını sağlayabilmek için endpoint url ve api key bilgilerine ihtiyacımız var. Bu bilgilere portal üzerindeki sol menüden “Keys and EndPoint” sekmesinden ulaşabilirsiniz.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*gJrWKNfQsAB91wbo"/>
</p>

Key ve endpoint bilgilerini de aldıktan sonra Form OCR Testing Tool (FOTT) üzerinden modeller oluşturmaya başlayabilirsiniz. Tool’u .exe dosyası olarak makinenize indirebilir ya da browser üzerinden de kullanabilirsiniz. Browser üzerinden kullanımın sadece cloud senaryoları desteklediğinide unutmamakta fayda var.

FOTT .exe dosyası için ⇒ https://github.com/microsoft/OCR-Form-Tools/releases

FOTT browserüzerinden kullanmak için ⇒ https://fott-2-1.azurewebsites.net/

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*JnE0aEJQHH1qTfq3"/>
</p>

FOTT’ un arayüzü şekildeki gibi . Tool ile prebuilt model oluşturabilir, dokümanlardaki layout bilgisini çıkarabilir ve custom olarak kendi modellerinizi oluşturup eğitebilirsiniz. İlk olarak prebuilt model oluşturma ile başlayalım.

## Prebuilt Model ile Doküman Analizi Gerçekleştirme

Prebuilt modelle Microsoft tarafından oluşturulmuş hazır modellerin analizini gerçekleştirebilirsiniz. Şimdilik prebuilt model global olan invoice, receipt, business card ve ID dosyaları için analizler yapabilmekte. FOTT üzerinden Prebuilt model seçtikten sonra ilk olarak analiz etmek istediğiniz belgenin yerini tool’a belirtiyorsunuz. Belgeniz local’ inizde bulunan bir dosya olabilir veya bir url de girebilirsiniz. Sonrasında Azure portal üzerinde oluşturmuş olduğumuz servisin endpoint url bilgisini ve API key bilgilerini girmeniz gerekiyor. Son olarak da form tipini seçmeniz gerekiyor. Ben (https://storage.googleapis.com/support-forums-api/attachment/thread-51411542-10595185938482944992.png )adresindeki Google invoice belgesinin url bilgisini source kısmına girdim ve daha sonrasında Run analysis butonuyla dokümanın analiz işlemini gerçekleştirdim.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*f-_d0ZOqp7Ctt3Bs"/>
</p>

Buradaki sarı alanla taranan kısımlar servisin doküman üzerinde okuyabildiği tüm alanlar. Sağ tarafta da prebuilt modele göre oluşturulmuş bir analiz var. Dokümanda hangi confidence oranında hangi bilgiler mevcut Prediction results alanından kontrol edebilirsiniz. Aynı zamanda JSON veya CSV dosyası şeklinde de bu bilgileri download edip inceleyebilirsiniz.

## Layout Analizi

FOTT ile layout analizi gerçekleştirmek de çok basit. Prebuilt modelde olduğu gibi sağ panelde servis için elimizde var olan endpoint url ve api key bilgilerini giriyoruz. Sonrasında elimizde bulunan belgeyi seçerek Run layout butonuyla belgenin layout analizini gerçekleştiriyoruz. Buradaki belgede sarı ile taralı olan her alan tool’un extract edebileceği alanlar. Sonrasında da dilerseniz bu layout bilgisini JSON veya CSV formatında indirebilirsiniz.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*hKCv6x6qnNvRsEKa"/>
</p>

## Custom Model Analysis

Servisin en çok kullanılan ve daha fazla efor gerektiren kısmına gelelim. Custom model analizi adı üzerinde Microsoft tarafından oluşturulup eğitilmiş modeller yerine kendi oluşturup eğittiğiniz modelleri kullandığınız yapı. Bulut ortamında custom model oluşturabilmek için belgelerinizin Azure blob storage’ da olması gerekiyor. Öncelikle Azure portal üzerinden bir storage accounts oluşturuyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*iTlwO6JsqwhT-k0p"/>
</p>

Storage accounts oluşturduktan sonra sol menüden Containers sekmesini açarak yeni bir Container oluşturmamız gerekiyor. Container’a bir isim vererek Create butonuyla yeni containerimizi oluşturmuş oluyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*GJlhK_dQG4RYTG_i"/> 
</p>

Elimizde bulunan dosyaları oluşturduğumuz container’a upload ediyoruz. buraya upload ettiğimiz dosyaları FOTT içerisinde görebilmek için Shared access tokens generate etmemiz gerekiyor.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*D_zoxw5DKN_74ArX"/>
</p>

Shared access token generate ederken öncelikle permissions belirliyoruz. Read, Add, Create, Write, Delete, List yetkilerinin hepsini işaretleyebilirsiniz. Sonrasında bir Expiry tarihi belirleyip Generate SAS token and URL oluşturabilirsiniz. FOTT için connection’ ı sağlamak adına Blob SAS URL bağıntısını kullanıyor olacağız.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*gxJsrD76rEwIQQOC"/>
</p>

Son olarak Azure portal üzerinden kaynak paylaşımı (CORS) ayarlarını yapmamız gerekiyor. Bunun için sol menüden Resource sharing(CORS) sekmesine gelerek Blob service altında aşağıdaki gibi alanları doldurup Save ediyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/468/1*smHi0lvP0kYE1LE2FAyeTg.png"/>
</p>

Bu işlem de tamamlandıktan sonra artık FOTT üzerinden yeni bir proje oluşturabiliriz. İlk olarak soldaki ikonlardan Connections’a gelerek (+) sembolüyle yeni bir connection oluşturuyoruz. Aşağıdaki ekran görüntüsündeki gibi bağlantıya bir isim vermeniz gerekiyor. Sonrasında provider olarak Azure blob container seçiyoruz ve yazının üst kısımlarında oluşturmuş olduğumuz Shared Access Signature(SAS URI) bağıntısını ekleyerek Save Connection butonuyla yeni bir bağlantı oluşturmuş oluyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*WKTpH4dMvOSQlZFr"/>
</p>

Connection kısmı tanımladıktan sonra ana sayfaya gelerek custom model oluşturma kısmından New Project seçiyoruz. Buradan sonra Project Settings sayfası açılıyor. Öncelikle projeye bir isim veriyoruz. Token olarak Generate New Security Token seçerek ilerleyebilirsiniz. Source connection kısmında biraz önce oluşturmuş olduğumuz new connection’ ı seçiyoruz. Folder path boş kalabilir. Daha sonrasında Azure portal üzerinde oluşturmuş olduğumuz servis endpoint url ve api key bilgilerini girerek Save Project butonuyla projeyi oluşturuyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*uTwSXixiINPqx2jN"/>
</p>

Projeyi kaydettiğinizde ana sayfa kısmına artık Azure blob container içerisine upload ettiğiniz dokümanlarınız gelecektir. FOTT üzerinde eğitim yapabilmek için en az 5 belgeye ihtiyaç duyuyor. Bu sebeple container içerisinde en az 5 belge olması gerekiyor. Belgeler ana sayfaya geldikten sonra ilk adım olarak belgelerde extract edeceğimiz alanlar servis tarafından OCR lanıyor. Bunun için Run Layout on unvisited documents diyebilirsiniz. Sonrasında belgelerden extract edeceğimiz alanları etiketlemeye(tag) başlıyoruz. Ben burada market fişi örnekleri üzerinden data çıkarımı yapmayı hedefliyorum. Öncelikle sağ tarafta bulunan Tags kısmından (+) ile tag ekliyorum. Eklediğim taglere fotoğraf üzerinden tıklayarak ya da klavye üzerindeki sayılardan(1'den 10'a kadar taglerin yanındaki sayılar) seçerek etiketleme işlemini tüm belgeler için tamamlıyorum.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*ijBitVVV4d-6enLS"/>
</p>

Etiketleme işlemi bittikten sonra artık model oluşturabiliriz. Burada yapmamız gereken tek şey modele bir isim verip Train butonuna tıklamak olacak. Buradan sonrasında servis eğitimi gerçekleştirerek Model ID, Average accuracy, Estimated accuracy değerlerini oluşturarak model eğitimini tamamlayacaktır. Form Recognizer servisi, alttaki ekran görüntüsünde görüldüğü gibi, dokümanları yüksek bir accuracy oranıyla eğitmiş oldu. Burada oluşan sonuçları JSON dosyası olarak indirme şansınız da bulunuyor.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*DXvnbHH81Zpdva-R"/>
</p>

Eğitim işlemi tamamlandıktan sonra eğer elinizde benzer modeller varsa compose işlemi gerçekleştirebilirsiniz. Compose işlemi yapmanız doğruluk oranını artıracaktır. Örenğin TC kimlik belgelerini eğittiğiniz bir senaryoda Türkiye’de hala kullanılan yeni ve eski kimlik belgeleri ve bunların ön arka yüzleri için ayrı ayrı modeller oluşturup sonrasında bu oluşan 4 model için compose yapmanız eğitimin kalitesini arttıracaktır.

Son olarak da test dokümanlarınız üzerinden analiz gerçekleştirebilirsiniz. Bunun için oluşturduğunuz modeli (varsa compose modeli) kullanabilirsiniz. Local dosya veya url olarak seçtiğiniz dokümanın analizini gerçekleştirebilirsiniz. Ben internette bulduğum bir market fişi üzerinden analiz gerçekleştirdim. Sonuçları aşağıdaki ekran görüntüsünde bulabilirsiniz.

<p align=“center”>
<img src="https://miro.medium.com/max/788/0*Hcw-r6tVYkvip-S_"/>
</p>

Görüldüğü üzere Azure Form Recognizer servisi yüksek confidence oranlarıyla dokümanları dijitalleştirmek için kullanılıyor. Confidence değeri %75 üzeri olan dokümanları başarılı olarak değerlendiriyoruz. Bu örnekte değerlerin %90 üzerinde çıkması da servisin ne kadar başarılı olduğunun bir göstergesi olarak düşünebiliriz.
