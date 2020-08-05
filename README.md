# alarmhisse
15 Dakika gecikmeli borsa alarmları
Öncelikle alarm dosyasını indiriyoruz.
Sonrasında ben /usr/local/bin içerisine attım sizde saklamak istediğiniz.Dizine alarm scriptimizi atın.
sonrasında
chmod komutu ile kullanıcımıza alarm scriptini çalıştırma execute etme yetkisi verelim.

sudo chmod +x alarm 

vim , vi yada nano gibi bir editör aracı ile alarm scriptimizi açalım 

sudo vim alarm

Karşımıza aşağıdaki değerlere sahip bir bash script dökümanı gelicektir.Aşağıda belirtilen #Portföy yazılı kısımda hisse senedi kısaltmaları örn;AKBNK,GARAN,TUKAS yazılı kısımlara takip etmek istediğiniz hisselerin kısaltmalarını yazınız.
#Hedef fiyat bölümünde alarm almak istediğiniz hedef fiyatların 100 ile çarpılmış halleri hedef fiyat olarak yazılır.Sonrasında şuanki fiyat hedef fiyattan büyük olduğunda ekrana mesaj döndürülmek isteniyorsa if içerisindeki kısımlar -gt eğer küçük olduğunda mesaj alınmak isteniyorsa if içerisindeki kısımlar -lt yazılarak güncellenmeli ve alarm scripti o şekilde kaydedilip kapatılmalıdır.


#!/bin/bash

#Portföy

h1=AKBNK

h2=GARAN

h3=TUKAS

h4=TUPRS

h5=TAVHL

h6=IHGZT

h7=SMART

h8=PAPIL

h9=ASELS

#Hedef Fiyat

z1=610

z2=840

z3=940

z4=8940

z5=1920

z6=400

z7=800

z8=1650

z9=2000


a1=$(curl -kis https://uzmanpara.milliyet.com.tr/canli-borsa/?Endex=XUTUM | grep h_td_fiyat_id_$h1 | cut -d ">" -f2 | cut -d "<" -f1 | sed 's/,/./')

a2=$(curl -kis https://uzmanpara.milliyet.com.tr/canli-borsa/?Endex=XUTUM | grep h_td_fiyat_id_$h2 | cut -d ">" -f2 | cut -d "<" -f1 | sed 's/,/./')

a3=$(curl -kis https://uzmanpara.milliyet.com.tr/canli-borsa/?Endex=XUTUM | grep h_td_fiyat_id_$h3 | cut -d ">" -f2 | cut -d "<" -f1 | sed 's/,/./')

a4=$(curl -kis https://uzmanpara.milliyet.com.tr/canli-borsa/?Endex=XUTUM | grep h_td_fiyat_id_$h4 | cut -d ">" -f2 | cut -d "<" -f1 | sed 's/,/./')

a5=$(curl -kis https://uzmanpara.milliyet.com.tr/canli-borsa/?Endex=XUTUM | grep h_td_fiyat_id_$h5 | cut -d ">" -f2 | cut -d "<" -f1 | sed 's/,/./')

a6=$(curl -kis https://uzmanpara.milliyet.com.tr/canli-borsa/?Endex=XUTUM | grep h_td_fiyat_id_$h6 | cut -d ">" -f2 | cut -d "<" -f1 | sed 's/,/./')

a7=$(curl -kis https://uzmanpara.milliyet.com.tr/canli-borsa/?Endex=XUTUM | grep h_td_fiyat_id_$h7 | cut -d ">" -f2 | cut -d "<" -f1 | sed 's/,/./')

a8=$(curl -kis https://uzmanpara.milliyet.com.tr/canli-borsa/?Endex=XUTUM | grep h_td_fiyat_id_$h8 | cut -d ">" -f2 | cut -d "<" -f1 | sed 's/,/./')

a9=$(curl -kis https://uzmanpara.milliyet.com.tr/canli-borsa/?Endex=XUTUM | grep h_td_fiyat_id_$h9 | cut -d ">" -f2 | cut -d "<" -f1 | sed 's/,/./')

#printf "$h1 $a1 \n$h2 $a2\n$h3 $a3\n$h4 $a4\n$h5 $a5\n$h6 $a6\n$h7 $a7\n$h8 $a8\n$h9 $a9\n"

b1=$(echo "$a1 * 100" | bc | cut -d '.' -f1)

b2=$(echo "$a2 * 100" | bc | cut -d '.' -f1)

b3=$(echo "$a3 * 100" | bc | cut -d '.' -f1)

b4=$(echo "$a4 * 100" | bc | cut -d '.' -f1)

b5=$(echo "$a5 * 100" | bc | cut -d '.' -f1)

b6=$(echo "$a6 * 100" | bc | cut -d '.' -f1)

b7=$(echo "$a7 * 100" | bc | cut -d '.' -f1)

b8=$(echo "$a8 * 100" | bc | cut -d '.' -f1)

b9=$(echo "$a9 * 100" | bc | cut -d '.' -f1)

if [ $b1 -gt $z1 ];then

	xmessage -display :0.0 $h1 ' 15 Dakika Once '  $a1 ' Fiyatina geldi'
fi
if [ $b2 -gt $z2 ];then

	xmessage -display :0.0 $h2 ' 15 Dakika Once '  $a2 ' Fiyatina geldi'
fi
if [ $b3 -gt $z3 ];then

	xmessage -display :0.0 $h3 ' 15 Dakika Once '  $a3 ' Fiyatina geldi'
fi
if [ $b4 -gt $z4 ];then

	xmessage -display :0.0 $h4 ' 15 Dakika Once '  $a4 ' Fiyatina geldi'
fi
if [ $b5 -gt $z5 ];then

	xmessage -display :0.0 $h5 ' 15 Dakika Once '  $a5 ' Fiyatina geldi'
fi
if [ $b6 -gt $z6 ];then

	xmessage -display :0.0 $h6 ' 15 Dakika Once '  $a6 ' Fiyatina geldi'
fi
if [ $b7 -gt $z7 ];then

	xmessage -display :0.0 $h7 ' 15 Dakika Once '  $a7 ' Fiyatina geldi'
fi
if [ $b8 -gt $z8 ];then

	xmessage -display :0.0 $h8 ' 15 Dakika Once '  $a8 ' Fiyatina geldi'
fi
if [ $b9 -gt $z9 ];then

	xmessage -display :0.0 $h9 ' 15 Dakika Once '  $a9 ' Fiyatina geldi'
fi

#xmessage -display :0.0 -display :0.0 'CALISTIM!'



Scriptteki düzenlemeler tamamlandıktan sonra scriptin her dakika çalışması için crontab işlemleri yapılmalıdır.

sudo crontab -e  
yazılarak aşağıdaki gibi crontab içeriği düzenlenebilir.ilk açılışta crontab bize dosyayı hangi editör ile açmak istediğimizi sorar ben vim editörünü seçtiğim için benim düzenlemem için vim editörü ile açıldı sonrasında en son satıra gelinerek her dakika çalışmasını istediğim için * * * * * yıldızları konulur ve düzenlediğiniz alarm scripti nerede ise * * * * * /usr/local/bin/alarm olacak şekilde crontaba eklenir ve kaydedilip çıkılır.

# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command

* * * * * /usr/local/bin/alarm 

Sonrasında her dakika  arka planda çalışacak ve istenilen değerler sağlandığında ekranın sol üst köşesinde hangi hissenin hangi hedef fiyata ulaştığına dair bir bilgilendirme mesajı yazılacaktır.Terminal ekranının açık olmasına gerek kalmadan bizi bu konuda bilgilendirecektir.
