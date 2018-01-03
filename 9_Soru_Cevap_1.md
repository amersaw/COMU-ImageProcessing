
## 14/12/2017 Lab'te verilen sorulari

### Aşağıdaki linkteki örnek üzerinde birkaç soru verilmiştir:

https://machinelearningmastery.com/naive-bayes-classifier-scratch-python/

Örnekteki veri seti "Ulusal Diyabet ve Sindirim ve Böbrek Hastalıkları Enstitüsü" tarafından toplanan bir veri seti 768 kişi üzerinde yapılan araştırma sonucudur.

Her bir kişi için 9 veri toplanmıştır:
1. Hamile kalma sayısı
2. Oral glukoz tolerans testinde 2 saatlik plazma glikoz konsantrasyonu
3. Diastolik tansiyon (mm Hg)
4. Triceps deri kat kalınlığı (mm)
5. 2 saatlik serum insülini (mu U / ml)
6. Vücut kitle indeksi (ağırlık kg / (m yükseklik) ^ 2)
7. Diyabet soyağacı Fonksiyonu
8. Yaş (yıl)
9. Sonuç/class: diabetes mellitus hastalığı var mı yok mu ? (0 veya 1 şeklinde)

Örnekteki amacımız ilk 8 veriyi kullanarak kişide o hastalığı var mı yok mu karar verilmeli

Veri setten birkaç örneği:

![img](./Final/dataset.png?raw=true)

Veri hakkinda bilgi : https://archive.ics.uci.edu/ml/machine-learning-databases/pima-indians-diabetes/pima-indians-diabetes.names

## 1- Native Bayes nedir, ne amacla kullanılır ?

The Naive Bayes algorithm is an intuitive method that uses the probabilities of each attribute belonging to each class to make a prediction. It is the supervised learning approach you would come up with if you wanted to model a predictive modeling problem probabilistically.

Native Bayes algoritması, sezgisel bir methoddur, her özelliğin olasılığı kullanarak bir tahmin üretme


## 2- Classifier vs clusterer arasindaki farklari nedir ?
**classifier** : label verilrise bir taneden classify edecek
**clusterer** ise n tane cluster'e bolecek, baslangicta labeller yok

bir sekilde veriyi analyse ederek algoritma fonk

## 3- linkteki python kodundaki butun fonksiyonlarin input/output seklinde blok semasi olarak gosterip kısaca amacını yazınız ?

![img](./Final/ip2.png?raw=true)

## 4- datasetteki bir listin formunu kisaca aciklayiniz


```python
algo kullandigi veri seti bunu gosteriyor:
    form of a list
    img1.reshape(1,img1.shape[0]*img1.shape[1])
    img1[-1]='label'  ya da img1.append('label')
```


      File "<ipython-input-1-44a1eb34f505>", line 2
        algo kullandigi veri seti bunu gosteriyor:
                      ^
    SyntaxError: invalid syntax



## 5- kac tane mean degeri vardir

Her bir sütün bir mean değeri olacak, buna göre örnekteki veri setinde 9 sütün var olduğuna göre 9 tane olacaktır. ama son sütünde bir sonuç değeri olduğu için o değer önemli değildir. yani 8 tane mean değeri olacak

## 6- TrainSet, TestSet nedir dataset üzerinden açıklayınız

**Trainset** Bir model eğitmek için kullanılan veri seti.

**TestSet** elde edilen sonuçları ne kadar doğur olduğunu kontrol etmek için kullanılan veri seti.

Normalde Dataset (yani tüm veriler) başlamadan önce rastgele olarak 2ye ayrılır,30% testSet ve 70% trainset.

Testset'te bulunan trainset'te herhangi bir tane olmamalı.

## 7-prediction (tahmin etme) nedir, hatasi nasil olculur?

Bir trainset üzerinde eğitilmiş bir model için yeni bir veri ona verip elde edilen sonucu predection (tahmin edilir) denir.

Hata ölçmek için birden fazla kayıt (testset olarak adlandırılır) toplayıp bu seti için doğru cevaplar saklayıp tahminleri ölçeriz. ölçtükten sonra elde ettiğimiz değerler kaç tane doğru olduğunu tespit edip (doğru olmak, elde edilen tahmin gerçek değer ile aynı olmak demek) onların oranı tahmin hatası olarak kabul edilir.

## 8- kendinizin olusturdugu bir test veirisi ile bu algo calistiriniz.


ordaki algo: en sondaki predeiction kullanacagiz,
prediction = (97. satirda)
(Kullanaılacak fonksiyon: predictions = getPredictions(summaries, testSet))


Bunu yapabilmek için ellimizde bir veri set olmalı bu veriset için her bir satır için farklı farklı parametreler içermeli, aynı zamanda her satır için bir sonuç olmalı (parametreler sonucu etkileyen parametreler olmalı), daha sonra main fonksiyonunda yapıldığı gibi :

1. Dosyadan **loadCSV** fonksiyonu kullanarak değerleri okur (veya farklı bir yerden)
2. elde edilen sonuçları *trainingSet* ve *testSet* ikiye ayrılır **splitDataset** fonksiyonu ile.
3. özetleri (*summaries*) hesaplanır, **summarizeByClass** fonksiyonu ile.
4. tahminleri (*predictions*) ölçer, getPredictions fonksiyonu ile.
5. Elde edilen sonuçların doğrululuğu (Accuracy) hesaplar, **getAccuracy** fonksiyonu ile.
6. Accuracy'yı ekrana yazdırır

## 9- (1 2 3) şeklinde bir resim alan, kac tane sayi rakam oldugunu bulan bir fonk yaziniz

to BW, siniri 0 olan original sayacagiz... sonunda kac tane ada var bulan fonksiyon

## 10- 9de elde ettigimiz sayin kadar resim return eden fonk yaziniz

flood-fill ?

## 11- 10de elde ettigniz her bir resmin, linkteki kod ile calistirip sonucu yazdiriniz

## 12- bir resmi teta kadar rotation ceviren bir fonksiyon yaziniz
