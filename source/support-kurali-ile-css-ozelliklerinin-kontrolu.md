Title: @support kuralı ile CSS özelliklerinin kontrolü
Date: 2013-08-12 18:00
Category: CSS
Tags: :@support-kuralı, kontrol, css

Bir özelliğin tarayıcılar tarafından desteklenip desteklenemediğini genelde javascript kontrol ediyoruz. @support kuralı sayesinde artık CSS ile bu kontrolü yapabiliyoruz. 

@media kuralına benzer basit bir kullanımı var. Farklı tarayıcılar için kod yazmaya ihtiyaç duyan bizler için çok süper bir özellik. [Modernizr](http://modernizr.com/)’ın javascript ile yaptığını css ile yapacağız artık.

## Basit Yapısı

	:::css
	@supports(ozellik:deger) {
		/* stilleri buraya yaz */
	}

Bir örnek yapacak olursak;

	:::css
	@supports (display:flex) {
		section { display: flex }
	}

Tarayıcı eğer display:flex’i destekliyorsa bu blok css’e eklenecektir.

**@media** kuralı gibi **and, or** ve **not** operatörleri kullanılabilmektedir.

## ve(and) operatörü

Birden fazla koşula bağlı sorgular oluşturabiliyoruz.

	:::css
	@supports (display: table-cell) and (display: list-item){
		...
	}

## veya(or) operatörü

Veya operatörü yardımı ile iki koşul öne sürüp birisinin gerçekleşmesi durumu için css tanımları yapılabiliyor. Örneğin farklı tarayıcı önekleri için;

	:::css
	@supports (display: -webkit-flex) or
	           (display: -moz-flex) or
	           (display: flex) {
	     /* stiller buraya */
	}

## Olumsuzluk(not) operatörü

Desteklemiyorsa sorgusu için not operatörünü kullanabiliyoruz.

	:::css
	@supports not (display: flex) {
		div { float: left; } /* alternatif stil */
	}

## Tarayıcı Desteği 

Yeni nesil tarayıcılar desteğini sunarken İnternet Explorer’ın ve mobil tarafının eksik kalması işin kötü kısmı. Asıl İnternet Explorer için gerekli bir özellik aslında :D

**Tarayıcı Destekleme Listesi **   
Firefox 22+   
Chrome 28 +   
Safari Desteklemiyor   
Opera 12.1 +   
İnternet Explorer Desteklemiyor    
**Mobil Tarayıcılar **   
iOS Safari Desteklemiyor   
Opera Mobile Desteklemiyor   
Android Browser Desteklemiyor
{: .tarayiciuyum}

## Kaynaklar

* [http://www.w3.org/TR/css3-conditional/#at-supports](http://www.w3.org/TR/css3-conditional/#at-supports)
* [https://developer.mozilla.org/en-US/docs/Web/CSS/@supports](https://developer.mozilla.org/en-US/docs/Web/CSS/@supports)
* [http://dev.opera.com/articles/view/native-css-feature-detection-via-the-supports-rule/](http://dev.opera.com/articles/view/native-css-feature-detection-via-the-supports-rule/)
* [http://caniuse.com/#search=@support](http://caniuse.com/#search=@support)
* [http://davidwalsh.name/css-supports](http://davidwalsh.name/css-supports)
* [http://www.sitepoint.com/supports-native-css-feature-detection/](http://www.sitepoint.com/supports-native-css-feature-detection/) 
* [http://amdhas.com/blog/learning-css3-supports](http://amdhas.com/blog/learning-css3-supports) 
* [http://www.inserthtml.com/2012/09/css3-conditional-statements/](http://www.inserthtml.com/2012/09/css3-conditional-statements/) 
* [http://docs.webplatform.org/wiki/css/atrules/@supports](http://docs.webplatform.org/wiki/css/atrules/@supports) 
