# car-brands-deeplearning
<h1>Giriş</h1>
<p>Bu derin öğrenme setinde Car-Brand-Classification adlı veri setini seçtim. Amacımız çeşitli markaların araba görsellerini tanıması ve öğrenmesi için matematiksel modeli (benim projem için CNN) optimize etmek .Bu veri setinde train-val-test kısımları klasörler içinde ayrıldığı için projeyi geliştirme açısından kolaylık sağladı yani ayrıca veri setlerini ayırıp belirli değişken isimlerine atamaktansa direkt olarak dataset klasörleri içerisinden eriştim. Fakat bu iyiliğin kötü yanı olarak farklı veri setlerinde aynı fotoların olup olmadığını kontrol etme imkanını ortadan kaldırdığı için bir yandan birbirini dengeledi diiyebilirim. Veri seti ayrıştırmadan sonra train-val-test görsel sayılarını çıktı olarak gösterdim ve train setimizdeki sınıf dağılımını grafikle göstererek hemen ardından görsellerini ekledim. Train setimizde yaptıklarıma ek olarak bu setteki görsel boyut dağılımını grafikte göstererek IMG_SIZE ı belirlememde yardımcı olacak bilgilere eriştim. 'Data Augmentation' ksımına gelecek olursak modelin ezberlemesini zorlaştırmak amacıyla train setini yatay-dikey kaydırma,  zoom, kesme, çevirme, parlaklık, yansıtma işlemleri uygulayarak bu seti çeşitlendirdim.   Daha sonra 'Data Augmentation' olup olmadığını kontrol etmek amacıyla train den bir 'batch' çekip görselleri çıktı olarak aldım. CNN modelinde görüntüden birçok kademeli özellikler çıkarıp, son katmanımızda bu özellikleri sınıf olasılıklarına dönüştürdük. Daha sonra CNN modelimizi 'compile' ederken öğrenme kurallarını belirleyerek bu işlemi başlattık. Ardından model doğruluk ve kayıp eğrisini görselleştirerek overfitting yapıp yapmadığına baktık (bu konuda pek başarılı olduğum söylenemez). Sonraki adım olarak her car class için test setimizdeki tahmin ve doğru çıkma sayılarını ısı haritasında gösterdik ayrıca test sınıfımızdaki doğru ve yanlış tahmin edilen örnekleri görsellerle beraber destekledik. Transfer learning kısmına gelecek olursak VGG16 modelini kullanıp eğrilerle görselleştirerek kendi CNN modelimle hali hazırda ön-eğitimli modelin doğruluklarını karşılaştırmak istedim. Son olarak 3 farklı optimizatör ile CNN imi yeniden derleyip doğruluklarını grafikle karşılaştırdım.</p>

<h2>Metrikler</h2>
<p>Sonuçlar:
  
  Temel CNN: 
  Temel CNN modelinde train için 0.0319 dan 0.3569 a ve val için 0.0485 dan 0.2978 e kadar çıkan acc değeri elde ettim ve gözlemledim. Bunun yüksek olmadığını veriler de doğrularken benim düşüncem datasetini alırken halihazırda bu set klasörlerde train val test olarak ayrıldığı için bu setteki başka sınıflarda tekrarlanan ögeleri ayrıştırıp imha edememem ve datasetindeki resimlerin hafif boyut farklarından dolayı resize ederken ister istemez kaliteyi düşürüyor. Bu konuda birçok varyasyonu denememe rağmen (epochs maksimuma alma, learning rate değiştirme, earlystopping, en iyi modeli kaydetme, dropout geçişlerini azaltma) ancak bu kadar yükseltebildiğim için sebebinin bu olduğunu düşünmekteyim.
  Ayrıca model doğruluk ve kayıp eğrisine bakarsak sonlara doğru hafif overfit yaptığını görmekteyiz. Bunun sebebinin öğrenme oranını yükseltmek amacıyla kullandığım epochs=75 olduğunu düşünmekteyim. Epochs u maksimuma aldığım için sonlara doğru matematiksel modelin ezberlediğini ve overfit e sebep olduğunu tahmin ediyorum.

  Transfer Learning:
    Transfer Learning de VGG16 modelini kullandım. Burada işlerin Temel CNN modeline kıyasla iyi gittiği söylenebilir. Göreceli olarak düşük bir epochs ile (30) train için 0.0333 den 0.5496 ya ve val için 0.0671 den 0.5192 ye çıktığını gözlemledim. Açıkçası epochs sayısını arttırarak oranı hatrı sayılır biçimde arttırabilirdim fakat cnn modelinde gözlemlediğim matematiksel modelin ezber yapmasını istemedim.

  Optimizasyon:
    Optimizasyon kısmında aynı mimariyi 3 farklı optimizatörle (adam, RMSprop, SGD+momentum) kısaca eğitip test doğruluklarına baktığımız zaman en yüksek oranı RMSprop ile verdiğini gözlemledim.
</p>

<h2>Sonuç ve Gelecek Çalışmalar</h2>
<p>Çalışmamı gelecekte VGG16 ve optimizatör RMSprop ile geliştireceğim. Ayrıca datasetimi klasörden otomatik almak yerine tüm klasörleri birleştirip farklı klasörlerdeki tekrarlanan resimleri çıkartarak acc oranımı arttırmayı hedefliyorum. Genel olarak 'derin öğrenme' konusunda ilk projemi yapmak keyifli ve öğretici bir deneyimdi.    </p>
<h2> Linkler</h2>
<p>
  https://www.kaggle.com/code/furkanaslantrk/car-brand-deeplearning (kaggleda geliştirdiğim projeyi privateda yapıp notebook umu çıkardım, publice aldığımda tekrar tüm notebooku compile etmek zorunda kaldığım için acc ve loss sayısal değerleri ufak değişiklikler göstermiş olabilir)
  https://www.kaggle.com/datasets/ahmedelsany/car-brand-classification-dataset
</p>
