Title: Chrome'un -99999999px sorunu
Slug: chrome-un-99999999px-sorunu
Date: 2012-11-14 9:32
Category: CSS
Tags: css, chrome, problem, gizle-göster

Diğer tarayıcılar rastlamadığım için bir sorun olarak yazıyorum. sizlerde eğer böyle bir tanım yaptı iseniz veya kullandığınız kod bloklarında kullanılmış ise benzer sorunu sizde yaşıyor olabilirsiniz.

Bazı elemanları gizle göster yapmak için görünür alanın dışına çıkarırız. Bunun için genelde left tanımına görünür alanın içine girmeyecek büyüklükte bir değer girerek yaparız. Amaç daha hızlı olarak elemanları gizle-göster yapmak. Örneğin

	:::css
	left:-9999px
	
gibi. Bazen yüksek çözünürlükteki ekranlar düşünülerek bu değer uçuk bir rakam verilir. 

	:::css
	left:-99999999px
	
gibi. Bu durumda Chrome 7. karakterden sonraki tanımları görmüyor ve bu atama yapılmamış gibi davranıyor. 


<iframe scrolling="no" height="150" frameborder="0" style="width: 100%; overflow: hidden;" allowtransparency="true" data-height="150" src="http://codepen.io/fatihhayri/embed/mcICs?type=css&amp;height=150" id="cp_embed_hgplm"></iframe>
