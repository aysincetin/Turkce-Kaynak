# AZURE DEVOPS İLE ÖRNEK CI/CD SÜRECİ TASARLAMA

<p align=“center”>
<img src="https://miro.medium.com/max/788/1*tZaywMZGDu_nlnaSi6-6qw.png"/>
</p>

Continuous Integration ve Continuous Delivery&Deployment kavramlarını öğrendiğimize göre Azure DevOps ürünüyle CI/CD sürecinin adım adım nasıl uygulandığına birlikte bakalım.

Öncelikle Azure DevOps ürününü kullanabilmek için bir Microsoft Azure DevOps hesabına ihtiyacımız var. Azure DevOps hesabını açtıktan sonra yeni bir proje oluşturarak işe başlayabiliriz.

**Adım 1:** İlk olarak Azure DevOps platformunda Pipelines bileşeninden Create Pipeline diyerek yeni bir pipeline oluşturuyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/538/1*kzy0-bagGzBtY3ZlYL3rzA.png"/>
</p>

**Adım 2:** Yeni Pipeline oluşturulurken yazmış olduğunuz kodun yerini belirtmenizi isteniyor. Bu aşamada kodlarınız GitHub ’da değilse classic editörü seçebiliriz.

<p align=“center”>
<img src="https://miro.medium.com/max/498/1*CUHOzeXM3ipjtTietozaMQ.png"/>
</p>

**Adım 3:** Ben ARM template ile bir proje oluşturdum ve bunu Azure Repos ‘a pushladım. Siz projeniz hangi source da yer alıyorsa onu seçebilirsiniz. Continue ile devam ediyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/457/1*hW14UjOdfs9cd51WhHMRNg.png"/>
</p>

**Adım 4:** Kodlarımın bulunduğu yeri belirttikten sonra projemin template’ ini seçiyorum. Ben burada empty job seçerek ilerliyorum. Bu adımda ARM template deployment taskini ekliyorum.

<p align=“center”>
<img src="https://miro.medium.com/max/744/1*mF4pwQHw16VxxCuDOXD1lg.png"/>
</p>

**Adım 5:** ARM template deployment için gerekli olan Azure Resource Management connection, subscription, resource group, location bilgilerini ve azuredeploy.json ve azuredeploy.parameters.json dosyalarını seçerek devam ediyorum. Siz bu kısmı kendi projenize göre ayarlayabilirsiniz. İstenen bilgileri doldurduktan sonra “Save&queue” kısmına tıklayarak kaydedip devam ediyorum.

<p align=“center”>
<img src="https://miro.medium.com/max/663/1*ONvCg0I-OWTiZY7qjcqIgA.png"/>
</p>

**Adım 6:** Bu adımda artık pipeline’ı run ediyorum ve oluşturduğum job Success olarak hazır hale geliyor.

<p align=“center”>
<img src="https://miro.medium.com/max/731/1*5Cj-ozWCEUFHu04haxetgQ.png"/>
</p>

**Adım 7:** Bir önceki adım başarılı şekilde gerçekleştikten sonra edit diyerek Triggers kısmından projemizde Continuous Integration ’ı enable ediyoruz. Sonrasında save ediyoruz. Böylece sürekli entegrasyon sağlanmış oldu.

<p align=“center”>
<img src="https://miro.medium.com/max/734/1*FUBgso4gymWyR-NgV74KxQ.png"/>
</p>

İçeriğin bu bölümüne kadar uygulamaların build ve test işlemlerinin otomatize edilme sürecine dair adımlar gösterildi. Buradan sonraki adımlar ise deployment ve delivery süreçlerinin otomatize edilmesine dair olacaktır.

**Adım 8:** Sürekli dağıtım için copy files ve publish build Artifacts tasklerini eklememiz gerekiyor. Bunun için de Pipelines kısmına giderek Agent Job eklemeliyiz. İlk olarak Copy Files’ ı ekliyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/728/1*hnhtILfav8AMGuoIikT1MQ.png"/>
</p>

Sonrasında da çıkan paneldeki boşlukları aşağıdaki gibi doldurabiliriz.

<p align=“center”>
<img src="https://miro.medium.com/max/574/1*gmI2dmpXqZvXdUSdJmS_wA.png"/>
</p>

**Adım 9:** Copy Files taskını ekledikten sonra Publish Build Artifacts ekle diyerek çıkan paneldeki boşlukları tamamlıyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/604/1*oZpCdjU7AlBA40epyvWeEQ.png"/>
</p>

**Adım 10:** Publish Artifacts panelindeki boşlukları da şekildeki gibi doldurduktan sonra Save edip devam ediyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/720/1*91SkzigBWFqVPqTkPL2iLw.png"/>
</p>

**Adım 11:** Uygulamamızın sürekli yayınını sağlamak için yeni release pipeline’ı oluşturup Empty Job template’ ini seçiyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/788/1*GUtge4MzA3JMKW0N3Fq0mw.png"/>
</p>

**Adım 12:** Burada hazır gelen Stage1’ i Test olarak adlandırarak devam ediyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/788/1*mFqJNqfHa_eW8h58un-NvA.png"/>
</p>

**Adım 13:** Sonrasında Artifacts kısmından Add diyerek build kısmındaki boşlukları şekildeki gibi değiştiriyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/530/1*k9jVdhrKupdnwAIAJ3JD3Q.png"/>
</p>

**Adım 14:** Bu adımdan sonra isterseniz Schedule set seçeneğinden süreci Schedule edebilirsiniz. Enable seçeneğini aktif ederek gün ve saat bilgilerini girebilirsiniz. Sonrasında flaş butonuna tıklayarak Sürekli Dağıtımı tetikliyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/189/1*u9Jtuk0JX0d6Qe4pt2nmkw.png"/>
</p>

**Adım 15:** Test Stage’ i seçiliyken Task sekmesinden Deploy’u seçerek ARM Template deployment ekleyerek devam ediyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/629/1*XIRvOwgvHMvhbYIgchqO9Q.png"/>
</p>

**Adım 16:** Stage1’in klonunu alarak Prod olarak isimlendirip save ediyoruz. Prod için Pre-deployment conditions kısmından After Stage olarak Stage1’i yani Testi seçip create ediyoruz.

<p align=“center”>
<img src="https://miro.medium.com/max/692/1*LPiMfefU7OuGAX_jcKDLKA.png"/>
</p>

**Adım 17:** Bu adımları tamamladıktan sonra da otomatik deploy işlemi tamamlanmış oldu.

<p align=“center”>
<img src="https://miro.medium.com/max/695/1*WsfLz7R9_dKjQMPVYYI0Ag.png"/>
</p>

Bu yazıda CI/CD süreçlerinden bahsederek ufak bir örnekle Azure DevOps platformu üzerinde nasıl otomatik entegrasyon ve deploy yaptığımızı öğrenmiş olduk.

> Referanslar;

(Bu yazıda kullanılan örnek için aşağıdaki linkleri inceleyebilirsiniz)

https://purple.telstra.com.au/blog/step-by-step-using-azure-devops-services-to-deploy-arm-templates-with-ci-cd-part-1

https://purple.telstra.com/blog/step-by-step-using-azure-devops-services-to-deploy-arm-templates-with-ci-cd-part-2
