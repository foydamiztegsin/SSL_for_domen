✅ Ubuntu 18.04 yoki undan avvali versiyalar uchun:
```rb
sudo apt-get update
sudo apt-get install certbot
```


✅ Ubuntu 20.04 yoki undan keyingi versiyalar uchun:
```rb
sudo apt update
sudo apt install certbot
```

❗️ pastdagi komandani berishdan oldin nginx ni stop qiling ✅ (sudo systemctl stop nginx) 80-portga ozod ulanishi uchun keyin esa
⬇️⬇️⬇️⬇️⬇️⬇️⬇️⬇️
```rb
sudo certbot certonly --standalone --preferred-challenges http -d example.com   # example.com sizning domeningiz(domen.uz)
```

```
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Enter email address (used for urgent renewal and security notices)
 (Enter 'c' to cancel): 
```

"""
✅ "Bu xabarda sizga Let's Encrypt sertifikatlarini yangilash va xavfsizlik xabarlari uchun elektron pochta manzilingizni so'ralmoqda. Sizdan pochta manzilingizni kiriting yoki 'c' tugmasini bosing va tasdiqlash xabarni bekor qiling.

Agar siz pochta manzilingizni kiritasiz, birinchi qadamda tasdiqlash va yangilash xabarlari olish uchun pochta manzilingizga xabarlar yuboriladi. Bu, Let's Encrypt serverlarining sertifikatlar va xavfsizlik yangilanishlariga doimiy ravishda e'tibor berish va ularga duch kelish uchun kerak bo'ladi.


Sizning e-mail manzilingizni kiritishingiz, Let's Encrypt xizmatlari bilan aloqada bo'lish va yangilanishlar haqidagi muhim ma'lumotlarni olishingizga yordam beradi."""

✅ ......gmail yoki email kiriting




```
Please read the Terms of Service at
https://letsencrypt.org/documents/LE-SA-v1.3-September-21-2022.pdf. You must
agree in order to register with the ACME server. Do you agree?
```

"""
Endi sizga Let's Encrypt xizmatlariga ro'yxatdan o'tish uchun shartnoma bilan tanishish va unga rozilik bildirishni so'raydi."""

✅ ........ Y ni kiriting



```
Would you be willing, once your first certificate is successfully issued, to
share your email address with the Electronic Frontier Foundation, a founding
partner of the Let's Encrypt project and the non-profit organization that
develops Certbot? We'd like to send you email about our work encrypting the web,
EFF news, campaigns, and ways to support digital freedom.
```

"""
Bu xabarda sizga Let's Encrypt loyihasining asosiy sheriki va Certbot dasturini ishlab chiqadigan elektron pochta manzilingizni Eff.org bilan ulashishga rozilik bildirishingiz so'ralmoqda. Eff.org sizga vebni shifrlash, EFF yangiliklari, kampaniyalari va raqamli erkinlikni qo'llab-quvvatlash yo'llarini haqida elektron pochta yuborishni istaydi."""

✅ ........ Y ni kiriting


```rb
Successfully received certificate.
Certificate is saved at: /etc/letsencrypt/live/sizning_domeningiz_boladi/fullchain.pem
Key is saved at:         /etc/letsencrypt/live/sizning_domeningiz_boladi/privkey.pem
This certificate expires on 2023-10-09.
These files will be updated when the certificate renews.
Certbot has set up a scheduled task to automatically renew this certificate in the background.

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
If you like Certbot, please consider supporting our work by:
 * Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
 * Donating to EFF:                    https://eff.org/donate-le
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```
"""
✅ Tabriklayman! Sertifikatingiz muvaffaqiyatli olinganligi haqida xabarni oldingiz!"""

❗️ Eslatma: Sertifikatning amal qilish muddati 2023-10-09 kuni tugaydi. Sertifikatni kelajakda yangilab olish yoki o'zgartirish uchun oddiy tartibda certbot dasturini qayta ishga tushurishingiz mumkin. Barcha sertifikatlaringizni avtomatik ravishda yangilash uchun "certbot renew" buyrug'ini ishga tushurishingiz mumkin.


✅ nginx ning faylida sozlamalarga ssl keylarini joylashtiring
```rb
sudo nano /etc/nginx/sites-available/sizning_nginx_faylingiz_nomi
```

```
server {
    listen 80;
    listen 443 ssl;
    server_name sizning_domeningiz_boladi(example.com);
    
    ssl_certificate /etc/letsencrypt/live/sizning_domeningiz_boladi/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/sizning_domeningiz_boladi/privkey.pem;
    
    location /static/ {
        alias static joylashuv yoli;
    }
    
    location /media/ {
        alias media joylashuv yoli;
    }
    
    # Qolgan server konfiguratsiyasini qo'shing
}
```

✅ klaviaturalar orqali:
	ctrl+s 
	ctrl+x 
	Y
	enter ketma-ketlikni bajaring 


❗️ agar siz ushbu buyruqni avval bergan bo'lsangiz
```rb
sudo ln -s /etc/nginx/sites-available/sizning_nginx_faylingiz_nomi /etc/nginx/sites-enabled
```

➡️ avval 
```rb
sudo rm -r /etc/nginx/sites-enabled/sizning_nginx_faylingiz_nom
```
yordamida sites-enabled papka ichidagi faylni ochiring.
va qaytadan yangilangan nginx faylingizni qoshing:
```rb
	sudo ln -s /etc/nginx/sites-available/sizning_nginx_faylingiz_nomi /etc/nginx/sites-enabled
```

✅ nginxni tekshiring
```rb
sudo nginx -t
```


✅ nginxni qayta ishga tushiring
```rb
sudo service nginx restart
```

 <hr>
 Mehnatimiz sizga foyda berayotgan bolsa GITHUB profilimizga obuna bo'ling va telegram kanalimizda reaksiyalarni qoldiring 👍
 
# *E'tiboringiz uchun rahmat* Savollaringiz bo'lsa [Telegram](https://t.me/foydamizteg_sin)













