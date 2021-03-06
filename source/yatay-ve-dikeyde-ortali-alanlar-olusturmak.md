Title: Yatay ve Dikeyde Ortalı Alanlar Oluşturmak
Date: 2010-09-29 22:20
Category: CSS, XHTML
Tags: ortalama, sayfaya ortalama, yatay ve dikşeyde ortalama

![][]

Birçok kişi bu soruyu sordu ve bende belirli aralıklar bu tip
bir ihtiyacım oldu, sonunda buraya yazmaya karar verdim. Bu işi sadece
CSS kullanarak nasıl yapıldığını yazacağım burada.

Bir kaç yöntem var bu konuda. Burada sabit genişlik ve yükseklikte
alanları sayfanın dikeyde ve yatayda ortalı olması durumu yazımı
yazacağım. position:absolute metodu denen yöntem ile yazacağız kodu.

HTML kodumuz

	:::html
	<div id="ortalaAlan">
		Fatih Hayrioğlu'nun not defteri
	</div> 

CSS kodumuz yazmaya başlayalım

	:::css
	html, body {
		height: 100%;
	}
	
	body{
		margin:0; 
		padding:0;
	}

İnternet explorer için ilk satırı ve body boşluklarını sıfırlamak içinde
ikinci satırı yazdık.

	:::css
	#ortalaAlan {
	   width: 300px;
	   height: 80px;
	   background-color:#fff;
	   border:5px solid #E9E9E9;    
	}

Sabit genişlik ve yükseklik veriyoruz ve genel tanımlarımızı yapıyoruz.
Şimdi bu alanı ortalamak için kodumuzu yazalım.

	:::css
	#ortalaAlan {
	   width: 300px;
	   height: 80px;
	   background-color:#fff;
	   border:5px solid #E9E9E9;    
	   position: absolute;
	   left: 50%;
	   top: 50%;
	   margin-left: -150px;
	   margin-top: -40px;
	}
	


Yukarıdaki kodu incelersek, postion:absolute ve left:50% ve top:50%
değerleri ile elemanımızı ortalıyoruz. Bu ortalama elemanımızın sıfır
noktası içindir, ancak bizim elemanımızın belirli bir genişliği ve
yüksekliği olduğu için bu tam bir ortalama sağlamayacaktır.

Tam bir ortalama için ise elemanın genişliğinin yarısı kadar sola
çekmeli ve elemanın yüksekliğinin yarısı kadarda yukarı çekmeliyiz.
Bunun için eksi değerli margin-left ve margin-top kullanıyoruz. Bu
kodlar elemanımızı dikeyde ve yatayda ortalayacaktır.

Kodumuzu ve içeriğimiz biraz daha süslersek

	:::html
	<div id="ortalaAlan">
		<p>Fatih Hayrioğlu'nun not defteri</p>
	</div> 

CSS kodumuzu

	:::css
	html, body {
		height: 100%;
	}
	
	body{
		margin:0; 
		padding:0; 
		background-color:#D2D2D2
	}
	
	#ortalaAlan {
	   width: 300px;
	   height: 80px;
	   background-color:#fff;
	   border:5px solid #E9E9E9;    
	   position: absolute;
	   left: 50%;
	   top: 50%;
	   margin-left: -155px;
	   margin-top: -45px;
	}
	
	#ortalaAlan p{
	    background:url(gudi.gif) 0 0 no-repeat;
	    color:##333333;
	    font:24px "Trebuchet MS", Arial, Helvetica, sans-serif;
	    padding-left:35px;
	    margin:10px
	}

Border olarak eklediğimiz değerleride çıkardığımız için değerlerimiz
-5px daha azalmıştır.

Örneği görmek için [tıklayınız.][]

![][1]

Bu kodu tüm tarayıcılar destekliyor.

## Kaynaklar

-   [http://www.joe2torials.com/view_tutorial.php?view=37][]
-   [http://perishablepress.com/press/2006/09/18/absolutely-centered-layout/][]
-   [http://hicksdesign.co.uk/journal/vertical--horizontal-centering-2][]
-   [http://www.456bereastreet.com/lab/centered/both/][]

  []: /images/dikey_yatayda_ortalama_ornek.gif
  [tıklayınız.]: /dokumanlar/dikey_yatay_ortalama.html
  [1]: /images/dikey_yatayda_ortalama-300x223.gif
  [http://www.joe2torials.com/view_tutorial.php?view=37]: http://www.joe2torials.com/view_tutorial.php?view=37
  [http://perishablepress.com/press/2006/09/18/absolutely-centered-layout/]: http://perishablepress.com/press/2006/09/18/absolutely-centered-layout/
  [http://hicksdesign.co.uk/journal/vertical--horizontal-centering-2]: http://hicksdesign.co.uk/journal/vertical--horizontal-centering-2
  [http://www.456bereastreet.com/lab/centered/both/]: http://www.456bereastreet.com/lab/centered/both/
