# JMeter-Basic-Level-Performance-Test
Bu projede JMeter ile Performans Testi yapılmıştır. JMeter kullanarak medium.com web servisine sanal kullanıcı ile request gönderilir.

JMeter ile fonksiyonel test, yük testi, performans testi ve stres testleri yapılabilir. Uygulamayı sanal kullanıcı gibi kullanarak test işlemini gerçekleştirir. Sanal kullanıcı gibi görünmek için ise HTTP protokolünü kullanır. Yapılan testler sonucu raporlar ile web uygulamasının performansı ölçülür.

<br>



https://github.com/ceren-aydin/JMeter-Basic-Level-Performance-Test/assets/74559017/23792e75-8357-478c-82a4-1b0157aeea63



# Proje Adımları
JMeter'da test planı altında thread group oluşturulur. Bu thread group'ta Number of Threads (users) için 100 değeri verilir. Her thread test edilen uygulamayı kullanan bir kullanıcıyı temsil eder. Ramp-up period (seconds) için 10 değeri verilir. Böylece 100 kullanıcı için 10 saniyede giriş yapması sağlanır. Loop Count için 4 değeri verilir. 100 kullanıcının 10 saniyede giriş yapması ve bunun 4 defa tekrarlanması sağlanır. Sonuç olarak server'a 400 kullanıcı request atmış olacaktır.

Kullanıcıların server'a request göndermesi Sampler elementi ile gerçekleştirilir. Thread group altında HTTP Request adında Sampler elementi oluşturulur. Bu element ile web sunucusuna request gönderilir. Thread group altında HTTP Request Default adında Config elementi oluşturulur. Oluşturulan 100 requestin tamamı aynı server'a gönderildiği için bu element sayesinde Server Name or IP parametresi request'lerin tamamı için eklenmiş olur.

Yapılan isteklerin sonuçlarının görüntülenmesi için View Result Tree ve View Result in Table adında Listener elemenleri oluşturulur. View Result Tree tablosu için; Yeşil renkteki HTTP Request'ler isteklerin başarılı oluduğunu gösterir. Kırmızı renkte olması ise başarısız olduğunu gösterir. Sampler result ile web server tarafından döndürülen veriler görülmekte. Örneğin response code:200'dür, isteğin başarıyla tamamlandığı anlamına gelir. Request ile web server'a gönderilen tüm veriler görülmekte. Response data ile server'dan alınan response verileri görülmektedir. View Result in Table tablosu için; sample, simüle edilen request numarasıdır. Sample time, her request'in ms türünden response time değeridir. Bu değerin yüksek çıkmaması gerekir, bu test için normal değerdedir. Bytes server'dan gelen cevabın boyutudur. Değişkenlik göstermesinin sebebi ise dinamik sayfalarda birçok değişken olmasıdır.
