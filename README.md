# one-digit-calculator-DESIGN-USING-PROTEUS8.3-MASM5

# LABIN KONUSU

2 adet 8255, 1 adey keypad, 1 adet 16 segment ANODE display, 1 adet 7 segment KATHODE display ile desteklenmiş 8086 mikro işlemcisi ile gerçeklenen 1 basamaklı hesap makinesi tasarımı.

# SEMANIN TAMAMI
<img src="https://github.com/sercaksoy/one-digit-calculator-DESIGN-USING-PROTEUS8.3-MASM5/blob/main/supportive_images/full_schema.png">

# YAPILMASI GEREKENLER
<b>1</b>.Keypad den girilen 1. sayı değeri 7 segmentte gösterilmeli, (16 Segment henüz hiçbir şey göstermiyor)(Girdi alınan sayıya ilişkin negatiflik, çok basamaklılık, arda arda 2 sayı girme gibi kontrolleri yapmanıza gerek yok; ilk girilen değeri pozitif olarak alsın, yeterli.)
</br><b>2</b>.Sonra herhangi dört işlem tuşuna basıldığında (+  -  x  :), 7 segmentte “0” değeri gösterilmeli. (16 Segment henüz hiçbir şey göstermiyor)
</br><b>3.</b>2.sayıya bastığımızda ise 2. sayıyı göstermeden, <u>direkt işlemin sonucunu 7 segmentte göstermeli</u>. Bu noktada hatalı ve hatasız işlemlere göre 16 segmentin davranışı kontrol edilmeli.

<b>Hatasız işlem:</b> 3 + 5,   7 – 2,   6 : 2,   2 x 1 gibi sonucu pozitif olan, birbirine bölünebilen, 1 basamaklı  çıkış veren işlemleri dikkate alın ve sonucunu 7 segmente yazdırın; 16 segmente ise sırasıyla ‘O’ , ‘N’ , ‘A’ , ‘Y’ harflerini aralarda kısa süreli delay vererek yazdırın (DELAY PROSEDÜRÜ). 
</br><b>Hatalı işlem:</b> 5 + 6,   2 – 7,   6 : 4,  2 x 8 … vb gibi sonucu negatif olan, tam bölünemeyen, 1 basamaktan fazla sonuç veren işlemleri ekranda, 7 segmenti tamamen söndürüp; 16 segmente sırasıyla ‘H’ , ‘A’ , ‘T’ , ‘A’ harflerini aralarda kısa süreli delay vererek yazdırın (DELAY PROSEDÜRÜ).

İki ayrı 8255 ile I/O kontrolü sağlayacaksınız. Birinci 8255’e keypad ve 7 segment bağlı olacak ve handshake ile veri alma-gönderme yapılacak <i>(Mod1)</i>. İkinci 8255’e 16 segment bağlanacak ve PortA & PortB birarada output olarak bu göstergeyi kontrol edecek <i>(Mod0)</i>. Birinci 8255 için PortA 200H adresinden başlayarak ardışık olarak çift adreste, ikinci 8255 için PortA 60H adresinden başlayarak ardışık olarak çift adreste işlem yapılacak.

Keypad için MM74C922 , 7 segment display için ise 4511 yardımcı devreleri kullanılabilir bunun dışında herhangi bir başka yardımcı eleman <u>KULLANILMAYACAKTIR.</u>

<h2>16 segment DISPLAY için ledlerin numaraları :</h2>
<img src="https://github.com/sercaksoy/one-digit-calculator-DESIGN-USING-PROTEUS8.3-MASM5/blob/main/supportive_images/16-segment-display.png">
<h2>Sadece belirtilen adreslemelerde 8255 lerin cevap vermesi için gerekli bağlantıların düzenlenmesi:</h2>
<img src="https://github.com/sercaksoy/one-digit-calculator-DESIGN-USING-PROTEUS8.3-MASM5/blob/main/supportive_images/data_gate.png">
<h2>Adresleme ve secilen 'CHIP SELECT'ler</h2>
<img src="https://github.com/sercaksoy/one-digit-calculator-DESIGN-USING-PROTEUS8.3-MASM5/blob/main/supportive_images/address_info.png">
<h2>16 segmentte gerekli mesajın yazılması için ayarlanmış diziler:</h2>
<img src="https://github.com/sercaksoy/one-digit-calculator-DESIGN-USING-PROTEUS8.3-MASM5/blob/main/supportive_images/used_arrays.png">
<h2>Soruda bahsedilen DELAY prosedürü:</h2>
<img src="https://github.com/sercaksoy/one-digit-calculator-DESIGN-USING-PROTEUS8.3-MASM5/blob/main/supportive_images/delay_procedure.png">

