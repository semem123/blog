Title: CSS3 Esnek Kutu Yerleşimi(Flexible Box Layout)
Date: 2011-09-16 22:47
Category: CSS, Haberler
Tags: box-align, box-direction, box-flex, box-flex-group, box-lines, box-ordinal-group, box-orient, box-pack, css3

CSS asıl çıkışını kazanmasında sayfa yerleşimini CSS ile ayarlamaya
başladığımızda yaptı. CSS3 ile birlikte bize daha avantajlı sayfa
yerleşimi özellikleri sunmayı gaye edinen W3C bizlere işimiz
kolaylaştıracak Esnek Kutu Yerleşimi Modülünü sunmaktadır.

Sayfa yerleşimini yaparken genelde float/clear veya position
özelliklerini kullanarak yapıyorduz. Tabloya göre büyük avantajlar
sağlayan bu yöntemlerden sonra web sayfası kodlamak daha kolay ve zevkli
bir hal aldı. Detay için[Tablo mu? Div mi? Karmaşasına Son Noktayı HTML5 koydu][] yazısını inceleyin.

Tabi CSS ile sayfa yerleşimi kodlamanın birçok avantajı var. Bunun
yanında bazı karışık sayfa yerleşimlerinde ise bizi zorladığı bir
gerçek. Özellikle esnek yapılı sayfa düzenleri ve dikey eksendeki
yerleşimlerdeki sorunlarını gören W3C bize bu konuda yardımcı olacak
yöntemleri üretmeye başladı. Bunlardan bir tanesi Esnek Kutu Yerleşimi
Modülüdür(EKYM).

Esnek Kutu Yerleşimi Modülü kapsayıcı bir eleman içindeki alt
elemanların yerleşimini sağlamaktadır. Daha önce dikeyde yaşadığımız
birçok sorunu(dikeyde ortalama ve aksak kolon sorunları gibi)
gidermemizi sağlıyor. Esnek Kutu Yerleşimi Modülünü bu makalemizde
inceleyeceğiz.

Kapsayıcı elemana tanımlanan display:box özelliği yardımı ile alt
elemanlara tanımlanan box(box-orient, box-direction, box-pack,
box-align, box-lines, box-ordinal-group, box-flex ve box-flex-group)
özellikleri ile sayfa yerleşimimizi çok kolay şekilde yapmamıza olanak
sağlamaktadır.

CSS3 EKYM olarak kısaltacağımız bu özellik bize olanaklarını display:box
tanımı içerisinde gelen yeni tanımlar ile getirmektedir. Bu yeni 8 tanım
aşağıdaki gibidir;

-   box-orient
-   box-direction
-   box-pack
-   box-align
-   box-lines
-   box-ordinal-group
-   box-flex
-   box-flex-group

EKYM ilk olarak 2009 yılında standardı oluşturuldu, ancak daha sonra
yeniden ele alındı ve şu an sonlandırılmak üzeredir. Biz 2009 yılındaki
standartlaşan özellikleri tanımlayacağız, çünkü tarayıcılar 2009
yılındaki standartları desteklemektedir ve yeni standartlaşan
özelliğinde mantık olarak çok büyük farklılığı yok.

## display:box

İlk olarak kapsayıcı esnek kutuları çevreleyen eleman **display:box**
tanımı yaparak başlıyoruz. Farklı tarayıcılar önek ile birlikte
desteklemektedir;

	:::css
	#esnekKutu{
		display: -webkit-box;
		display: -moz-box;
		display: -ms-box;
		display: box;
	} 

Tanımı ile kapsayıcı elemanı tanımlıyoruz. Bu tanım ile kapsayıcı eleman
içersindeki alt elemanların artık esnek yapılı olacağını ve EKYM
özellikleri alabileceğini belirliyoruz.

Çok basit bir şekilde kutularımızı yanyana dizebiliriz mesela

	:::css
	#esnekKutuKapsul{
	 display: box;
	 display:-webkit-box;
	 display:-moz-box;
	 display:-ms-box;
	 width:600px;
	 border:1px solid #03C;
	}
	
<iframe style="width: 100%; height: 300px" src="http://jsfiddle.net/fatihhayri/4KSzt/embedded/result,css,html"></iframe>

Kapsayıcı tanımlanan **display:box** tanımı ile içindeki elemanlar birer
**inline-block** eleman gibi davranır ve yanyana sıralanır.

## box-orient

**Yapısı:** box-orient: <deger\>  
**Aldığı Değerler:** horizontal | vertical | inline-axis | block-axis  
**Başlangıç değeri:** inline-axis  
**Uygulanabilen elementler:** display:box ve display:inline-box değeri
alan elemanlara  
**Kalıtsallık:** Yok
{: .cssozelliktanimi}

box-orient özelliği ile esnek kapsayıcı eleman içindeki kutuların hangi
eksende sıralanacağını belirleriz. Yukarıdaki örnekte gördüğümüz gibi
eğer bir tanım yapılmadı ise ve kapsayıcı eleman genişliği müsait ise
kutular yatayda yanyana sıralanır.

Biz bu durumu değiştirmek için **box-orient** özelliğini kullanırız. 3
adet değer alır.

-   **horizontal:** Kutular yatay eksende soldan sağa doğru sıralanır.
-   **vertical:** Kutular dikey eksende yukarıdan aşağıya doğru
    sıralanır.
-   **inherit:** Üst elemanın değerini alır.

Bunlardan başka iki değer daha mevcuttur. **inline-axis** yatayda ve
**block-axis** dikeyde sıralamayı sağlar. Bu tanımlar **horizontal** ve
**vertical** gibi davranırlar.

	:::css
	#esnekKutuKapsul{
		display: box;
		display:-webkit-box;
		display:-moz-box;
		box-orient:vertical;
		-moz-box-orient:vertical;
		-webkit-box-orient:vertical;
		width:200px;
		height:600px;
		border:1px solid #03C;
	} 

<iframe style="width: 100%; height: 300px" src="http://jsfiddle.net/fatihhayri/AsVDn/embedded/result,css,html"></iframe>

**box-orient:vertical** ile esnek kutularımızı dikeyde sıraladık.

## box-direction

**Yapısı:** box-direction: <deger\>  
**Aldığı Değerler:** normal | reverse  
**Başlangıç değeri:** inline-axis  
**Uygulanabilen elementler:** display:box ve display:inline-box değeri
alan elemanlara  
**Kalıtsallık:** Yok
{: .cssozelliktanimi}

**box-direction** özelliği kapsayıcı eleman içindeki esnek kutuların
sıralama yönünü belirler. İki değer alır; normal ve **reverse**.
**reverse** tanımlandığında sıralama yönü normalin tam tersine döner.

	:::css
	#esnekKutuKapsul{
		display: box;
		display:-webkit-box;
		display:-moz-box;
		box-orient:vertical;
		-moz-box-orient:vertical;
		-webkit-box-orient:vertical;
		box-direction: reverse;
		-moz-box-direction: reverse;
		-webkit-box-direction: reverse;
		width:200px;
		height:600px;
		border:1px solid #03C;
	}
	
<iframe style="width: 100%; height: 300px" src="http://jsfiddle.net/fatihhayri/S4c44/embedded/result,css,html"></iframe>

Yukarıdaki örnekte sıralama yukarıdan aşağı **Esnek Kutu1, Esnek Kutu2**
ve **Esnek Kutu3** iken **box-direction: reverse;** tanımı ile sıralama
**Esnek Kutu3, Esnek Kutu2** ve **Esnek Kutu1** şeklini almıştır.

**Not:** **box-orient** ve **box-direction** yerine ikisini kapsayan
**flex-direction** üzerinde çalışılmaktadır.

**flex-direction lr, rl, tb, bt, inline, inline-reverse, block** ve
**block-reverse** değerlerini alabilecek. sol(left - l), sağ(right - r),
üst(top - t) ve alt(bottom - b) kısaltmaları kullanılmıştır. CSS3’ün
birçok özelliği üzerinde halen çalışılan canlı bir yapıdır.
Değişikliklerin olabileceği dikkate alınmalıdır.

## box-pack

**Yapısı :** box-pack: <deger\>  
**Aldığı Değerler :** start | end | center | justify  
**Başlangıç değeri:** start  
**Uygulanabilen elementler:** display:box ve display:inline-box değeri
alan elemanlara  
**Kalıtsallık:** Yok
{: .cssozelliktanimi}

**box-pack** özelliği kapsayıcı kutunun içindeki esnek kutuların
kapsayıcıya göre konumunu belirlemek için kullanılır. Dört adet değer
alır başlangıç(start), son(end), ortalı(center) ve iki yana
yasla(justify)

Alt elemanların genişliğinin kapsayıcı elemandan küçük olduğu durumlarda
kalan boşluk alanına göre değerlendirme yapılır.

Bu özellik tanımı 2009’da tanımlandı şu an yenileniyor **flex-pack**
olarak değişecek. Tarayıcılar destekleyen kadar bu şekilde devam edecek.

	:::css
	#esnekKutuKapsul{
	     display: box;
	     display:-webkit-box;
	     display:-moz-box;
	     width:600px;
	     border:1px solid #03C;
	     box-pack:center;
	     -webkit-box-pack:center;
	     -moz-box-pack:center;
	}

<iframe style="width: 100%; height: 300px" src="http://jsfiddle.net/fatihhayri/MwWcm/embedded/result,css,html"></iframe>

## box-align

**Yapısı :** box-align: <deger\>  
**Aldığı Değerler :** stretch | start | end | center | baseline  
**Başlangıç değeri:** stretch  
**Uygulanabilen elementler:** display:box ve display:inline-box değeri
alan elemanlara  
**Kalıtsallık:** Yok
{: .cssozelliktanimi}

Kapsayıcı elemana atanan box-orient değerine göre kalan boşluğa göre
hizalama yapmak için kullanılır.

Beş adet değer alır. **stretch | start | end | center | baseline**
Başlangıç değeri **stretch**’dir; bunun anlamı **box-orient** değeri
**horizontal** ise **stretch** uygulanan elemanın alt elemanlarının
yükseklikleri yayılacaktır, eğer **box-orient** değeri **veritcal** ise
genişlikleri yayılacaktır. **start** ve **end** değerleri eğer
horizantal tanımlı ise sol ve sağa yaslayacaktır, **vertical** tanımlı
ise üste ve alta yaslayacaktır. **center** değeri ise ortalayacaktır.

	:::css
	#esnekKutuKapsul{
	    display: box;
	    display:-webkit-box;
	    display:-moz-box;
	    width:600px;
	    border:1px solid #03C;
	    box-orient:horizantal;
	    -moz-box-orient:horizantal;
	    -webkit-box-orient:horizantal;  
	    box-align: center;
	    -webkit-box-align: center;
	    -moz-box-align: center;
    }
    .esnekKutu{
         background-color:#999999;
         width:150px;
         height:150px;
         margin-right:15px;
    }
 
<iframe style="width: 100%; height: 300px" src="http://jsfiddle.net/fatihhayri/ZYz2M/1/embedded/result,css,html"></iframe>

## box-lines

**Yapısı :** box-lines: <deger>  
**Aldığı Değerler :** single | multiple  
**Başlangıç değeri:** single  
**Uygulanabilen elementler:** display:box ve display:inline-box değeri
alan elemanlara  
**Kalıtsallık:** Yok
{: .cssozelliktanimi}

Esnek Kutu Yerleşimi ile yerleştirilen kutular genelde bir eksen
üzerinde blok halinde hareket eder, **blox-line** özellik bu elemanların
alt satıra geçip geçmemesini ayarlar. İki değer alır.

-   **single:** Başlangıç değerdir. Bu değeri alan kutular kapsayıcı
    eleman üzerine taşma yapacaktır. Taşma durumunu kontrol etmek için
    overflow özelliği kullanılabilir.
-   **multiple:** Bu değer alan kutular tek satırda kendini
    sınırlamayacaklardır ve ikinci satıra inecektir.

Şu anki tarayıcılar bu özelliği henüz desteklemiyor. İE10 desteklediğine
dair duyumlar var.

Yenilenen EKYM standartlarında box-line özelliği görünmüyor. Onun yerine
benzer etki yapacak **flex-flow** tanımı gelecek gibi.

## box-ordinal-group

**Yapısı :** box-ordinal-group: <deger>  
**Aldığı Değerler :** <sayı>  
**Başlangıç değeri:** 1  
**Uygulanabilen elementler:** display:box ve display:inline-box değeri
alan elemanların normal akıştaki alt elemanları  
**Kalıtsallık:** Yok
{: .cssozelliktanimi}

**box-ordinal-group** özelliği kapsayıcı kutunun içindeki esnek
kutuların sıralamasını belirlememizi sağlar.

	:::css
	#esnekKutu1 {
	    box-ordinal-group: 2;
	    -webkit-box-ordinal-group: 2;
	    -moz-box-ordinal-group: 2;
	    background-color:#0CF;
	}
	
	#esnekKutu3 {
	    box-ordinal-group: 2;
	    -webkit-box-ordinal-group: 2;
	    -moz-box-ordinal-group: 2;
	    background-color:#9C3;
	}
	
	#esnekKutu4 {
	    box-ordinal-group: 1;
	    -webkit-box-ordinal-group: 1;
	    -moz-box-ordinal-group: 1;
	    background-color:#FC9;
	}
	
<iframe style="width: 100%; height: 300px" src="http://jsfiddle.net/fatihhayri/TaFBM/embedded/result,css,html"></iframe>

Dört adet kutumuz var. Bunların üç tanesine **box-ordinal-group** değeri
tanımladık.

**EsnekKutu1** ve **EsnekKutu3** için 2 değeri tanımladık bunlar ikinci
sırada gelecek. **EsnekKutu4**’e 1 değer tanımladık, buda ilk sırada
gelecek. **EsnekKutu2** için bir tanım yapmadık buda başlangıç değeri
olan 1 değerini almasına neden olacaktır. Buna göre sıralama 2,4,1,3
şeklinde olacaktır.

Bu özellik bize sıralama konusunda tam bir kontrol sağlamaktadır.

Yeni EKYM standardında **box-ordinal-group** yerine **flex-order**
özellik ismi kullanılması düşünülmektedir.

## box-flex

**Yapısı :** box-ordinal-group: <deger\>  
**Aldığı Değerler :** <sayı\>  
**Başlangıç değeri:** 0  
**Uygulanabilen elementler:** display:box ve display:inline-box değeri
alan elemanların normal akıştaki alt elemanları  
**Kalıtsallık:** Yok
{: .cssozelliktanimi}

**blox-flex** özelliği tanımlanması durumunda alt elemanların esnek
davranmasını sağlar. Tanım yapılmadığında ise alt elemanlar esnek olmaz.

Hesaplamanın mantığı şöyledir;

Gruptaki tüm esnek kutuların **box-flex** değeri toplanır ve her kutu
için toplam boşluk genişliği(Kapasayıcı eleman ile kutuların genişliği
toplamı arasındaki fark) bu sayıya bölünerek elde edilen değer kutu
genişliğini belirler.

	:::css
	#esnekKutuKapsul {
	     background: gray;
	    border: blue;
	    display: box;
	   display: -webkit-box;
	   display: -moz-box;
	   display: -ms-box;
	   width:100%;
	}
	
	.esnekKutu {
	   background-color:#999999;
	   height:150px;
	}
	
	#esnekKutu1 {
	    background-color:#0CF;  
	    border: orange solid 1px;
	    box-flex: 2;
	    -webkit-box-flex: 2;
	    -moz-box-flex: 2;
	    -ms-box-flex: 2;
	}
	
	#esnekKutu2 {
	    background: lightgray;
	    border: red solid 1px;
	    box-flex: 1;
	    -webkit-box-flex: 1;
	    -moz-box-flex: 1;
	    -ms-box-flex: 1;
	}
	
	#esnekKutu3 {
	    background-color:#9C3;    
	    border: red solid 1px;
	    box-flex: 0;
	    -webkit-box-flex: 0;
	    -moz-box-flex: 0;
	    -ms-box-flex: 0;
	}
	
	#esnekKutu4 {
	    background-color:#FC9;
	    border: red solid 1px;
	}
	
<iframe style="width: 100%; height: 300px" src="http://jsfiddle.net/fatihhayri/h7KAa/embedded/result,css,html"></iframe>

Daha sabit bir örnek verelim; genişliği 600px olan kapsayıcı eleman ve
 üç adet 100px’lik kutumuz olsun(Bu durumdan boşluk değeri 300px
olacaktır), bunların **box-flex** değerleri 1 olsun, her bir kutunun
genişliği 200px(100 + 300/3 * 1 = 200) olacaktır. Eğer bu kutulardan
bir tanesinin **box-flex** değeri 2 olarak değiştirilirse, değiştirilen
kutunun genişliği 250px(100 + 300/4 * 2 = 250) olurken diğer iki
kutunun genişliği 175px(100 + 300/4 * 1 = 175) olacaktır.

	:::css
	#esnekKutuKapsul {
	   background: gray;
	   border: blue;
	   display: box;
	   display: -webkit-box;
	   display: -moz-box;
	   display: -ms-box;
	   width:600px;
	}
	
	.esnekKutu {
	   background-color:#999999;
	   height:150px;
	   width:100px;
	}
	
	#esnekKutu1 {
	   background-color:#0CF;  
	   box-flex: 2;
	   -webkit-box-flex: 2;
	   -moz-box-flex: 2;
	   -ms-box-flex: 2;
	}
	
	#esnekKutu2 {
	   background: lightgray;
	   box-flex: 1;
	   -webkit-box-flex: 1;
	   -moz-box-flex: 1;
	   -ms-box-flex: 1;
	}
	
	#esnekKutu3 {
	   background-color:#9C3;    
	   box-flex: 1;
	   -webkit-box-flex: 1;
	   -moz-box-flex: 1;
	   -ms-box-flex: 1;
	}
	
<iframe style="width: 100%; height: 300px" src="http://jsfiddle.net/fatihhayri/Dyjq2/embedded/result,css,html"></iframe>

Eğer kutu genişlikleri toplamı kapsayıcı kutunun genişliğinden büyük ise
genişlik hesaplamasında benzer birim hesabına göre küçülme olacaktır. 0
değeri kutunun esnek olmayacağı anlamına gelir.

[Raphael Goetter][]’ın yaptığı örnek bu işin geleceği hakkında bize
güzel bir ipucu veriyor. Fantastik örnekler.(Chrome da daha iyi
gözüküyor)

**box-flex** özelliği 2009 yılındaki standartlardaki hali idi, yenilenen
standartlarda **box-flex** vede **box-flex-group** özelliklerini
kapsayan **flex()** fonksiyonu ile yenilenmektedir.

**Tarayıcı Destekleme Listesi**  
Firefox 3+ (-moz- öneki ile)  
Chrome 5+ (-webkit- öneki ile)  
Safari 3.2+ (-webkit- öneki ile)  
Opera desteklemiyor  
İnternet Explorer 10+ (-ms- öneki ile)  
**Mobil Tarayıcılar**  
iOS Safari 3.2+ (-webkit- öneki ile)  
Opera Mini desteklemiyor  
Opera Mobile destelemiyor  
Android Browser 2.2+ (-webkit- öneki ile)
{: .tarayiciuyum}

## Sonuç

Gerek CSS3 ve gerekse EKYM yeni özellikler ve hala gelişmektede olan
mecralar. Benim burada anlatmak istediğim CSS3’ün en büyük
yeniliklerinden biri olan sayfa planlamaya yönelim yeniliklerine bir göz
atmak, mantığını kavramak, geleceğe dair fikir edinmeyi sağlamaktır. Ben
burada sadece EKYM anlattım, ancak CSS3 ile sayfa planlamaya yönelik
başka modüllerde geliştirilmekte; [Çoklu Kolonlar(Multiple Column)][],
[Izgara Yerleşim Modeli(Grid Layout)][], [Şablon Yerleşim Modeli(Template Layout Model)][], [CSS Exclusions Module][], [CSS regions Module][]

CSS3 ile sayfa yerleşimi daha kolay olacağı kesin, bu konuda bir çok
modül üzerinde çalışma bitmek üzere veya bitmiş bulunmakta. Gelecekte
daha güzel şeyler olacağı kesin.

Yukarıda özelliklerin nasıl kullanıldığını göstermek için daha basit
örneklerler verdik, daha karmaşık örneklerde yapılabilir
[http://oli.jp/2011/css3-flexbox/][] sitesindeki örnekler incelenebilir.
 

Kalın sağlıcakla

## Kaynaklar

-   [http://www.html5rocks.com/en/tutorials/flexbox/quick/][] (güzel)
-   [http://www.css3.info/introducing-the-flexible-box-layout-module/][]
-   [http://www.w3.org/TR/css3-flexbox/][]
-   [http://dev.w3.org/csswg/css3-flexbox/][]
-   [http://robertnyman.com/2010/12/02/css3-flexible-box-layout-module-aka-flex-box-introduction-and-demostest-cases/][]
-   [http://www.456bereastreet.com/archive/201103/the_css3_flexible_box_layout_flexbox/][]
-   [http://hacks.mozilla.org/2010/04/the-css-3-flexible-box-model/][]
-   [http://www.the-haystack.com/2010/01/23/css3-flexbox-part-1/][]
-   [http://ie.microsoft.com/testdrive/html5/flexin/default.html][]
-   [http://htmlrockstars.com/blog/the-flexible-box-layout-module-css3/][]
-   [http://blog.w3conversions.com/2011/02/css3-flexible-box-model-layout-coolness-also-oddities-confusion/][]
-   [http://www.netmagazine.com/tutorials/css3-flexible-box-model-explained][]
-   [http://adactio.com/journal/4778/][]
-   [http://www.vanseodesign.com/css/flexbox/][] (güzel)
-   [http://oli.jp/2011/css3-flexbox/][] (karmaşık yerleşim uygulamalı)
-   [http://blog.isotoma.com/2010/08/css3-flexbox/][]
-   [http://www.w3schools.com/css3/css3_reference.asp#box][]
-   [http://portfo.li/madebyted/477862-css3-flexible-box-layout-module-aka-flex-box-introduction-and-demos-test-cases][]
-   [http://ontwik.com/css/css-3-the-flexible-box-model/][] (video)
-   [http://msdn.microsoft.com/en-us/ie/hh272902.aspx#_CSSFlexBox][] (güzel)
-   [http://caniuse.com/flexbox][] (tarayıcı desteği)
-   [http://coding.smashingmagazine.com/2011/09/19/css3-flexible-box-layout-explained/][]


  [Tablo mu? Div mi? Karmaşasına Son Noktayı HTML5 koydu]: http://www.fatihhayrioglu.com/tablo-mu-div-mi-karmasasina-son-noktayi-html5-koydu/
  [Raphael Goetter]: http://www.ie7nomore.com/fun/flexiblenav/
  [Çoklu Kolonlar(Multiple Column)]: http://www.fatihhayrioglu.com/css3-coklu-kolonlar/
  [Izgara Yerleşim Modeli(Grid Layout)]: http://dev.w3.org/csswg/css3-grid-align/
  [Şablon Yerleşim Modeli(Template Layout Model)]: http://www.w3.org/TR/css3-layout/
  [CSS Exclusions Module]: http://dev.w3.org/csswg/css3-exclusions/
  [CSS regions Module]: http://dev.w3.org/csswg/css3-regions/
  [http://oli.jp/2011/css3-flexbox/]: http://oli.jp/2011/css3-flexbox/
  [http://www.html5rocks.com/en/tutorials/flexbox/quick/]: http://www.html5rocks.com/en/tutorials/flexbox/quick/
  [http://www.css3.info/introducing-the-flexible-box-layout-module/]: http://www.css3.info/introducing-the-flexible-box-layout-module/
  [http://www.w3.org/TR/css3-flexbox/]: http://www.w3.org/TR/css3-flexbox/
  [http://dev.w3.org/csswg/css3-flexbox/]: http://dev.w3.org/csswg/css3-flexbox/
  [http://robertnyman.com/2010/12/02/css3-flexible-box-layout-module-aka-flex-box-introduction-and-demostest-cases/]: http://robertnyman.com/2010/12/02/css3-flexible-box-layout-module-aka-flex-box-introduction-and-demostest-cases/
  [http://www.456bereastreet.com/archive/201103/the_css3_flexible_box_layout_flexbox/]: http://www.456bereastreet.com/archive/201103/the_css3_flexible_box_layout_flexbox/
  [http://hacks.mozilla.org/2010/04/the-css-3-flexible-box-model/]: http://hacks.mozilla.org/2010/04/the-css-3-flexible-box-model/
  [http://www.the-haystack.com/2010/01/23/css3-flexbox-part-1/]: http://www.the-haystack.com/2010/01/23/css3-flexbox-part-1/
  [http://ie.microsoft.com/testdrive/html5/flexin/default.html]: http://ie.microsoft.com/testdrive/html5/flexin/default.html
  [http://htmlrockstars.com/blog/the-flexible-box-layout-module-css3/]: http://htmlrockstars.com/blog/the-flexible-box-layout-module-css3/
  [http://blog.w3conversions.com/2011/02/css3-flexible-box-model-layout-coolness-also-oddities-confusion/]: http://blog.w3conversions.com/2011/02/css3-flexible-box-model-layout-coolness-also-oddities-confusion/
  [http://www.netmagazine.com/tutorials/css3-flexible-box-model-explained]: http://www.netmagazine.com/tutorials/css3-flexible-box-model-explained
  [http://adactio.com/journal/4778/]: http://adactio.com/journal/4778/
  [http://www.vanseodesign.com/css/flexbox/]: http://www.vanseodesign.com/css/flexbox/
  [http://blog.isotoma.com/2010/08/css3-flexbox/]: http://blog.isotoma.com/2010/08/css3-flexbox/
  [http://www.w3schools.com/css3/css3_reference.asp#box]: http://www.w3schools.com/css3/css3_reference.asp#box
  [http://portfo.li/madebyted/477862-css3-flexible-box-layout-module-aka-flex-box-introduction-and-demos-test-cases]: http://portfo.li/madebyted/477862-css3-flexible-box-layout-module-aka-flex-box-introduction-and-demos-test-cases
  [http://ontwik.com/css/css-3-the-flexible-box-model/]: http://ontwik.com/css/css-3-the-flexible-box-model/
  [http://msdn.microsoft.com/en-us/ie/hh272902.aspx#_CSSFlexBox]: http://msdn.microsoft.com/en-us/ie/hh272902.aspx#_CSSFlexBox
  [http://caniuse.com/flexbox]: http://caniuse.com/flexbox
  [http://coding.smashingmagazine.com/2011/09/19/css3-flexible-box-layout-explained/]: http://coding.smashingmagazine.com/2011/09/19/css3-flexible-box-layout-explained/
