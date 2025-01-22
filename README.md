# PMG DNSBL

Bu döküman üzerinde PMG üzerinde DNSBL sitelerinin nasıl ekleneceğini ve hangilerinin eklenmesi gerektiği bilgisi verilmektedir.


## DNSBL 

![image](https://github.com/user-attachments/assets/a900ffb4-0d77-49e4-8ddc-dddd62b3720f)

Sol taraftaki menü üzerinden Mail proxy >> options sayfasına erişiniz. 


![image](https://github.com/user-attachments/assets/5bc604b7-9afa-4f98-8eed-2250c6297850)

Çok fazla DNSBL eklemek sağlıklı değildir. En çok kullanılan 3 tanesini ekledim.

```
bl.spamcop.net,b.barracudacentral.org,zen.spamhaus.org
```


Örnek reddetme logu:

```
2025-01-20T14:33:15.838889-05:00 mail postfix/postscreen[879438]: NOQUEUE: reject: RCPT from [1.1.1.1]:51705: 550 5.7.1 Service unavailable; client [1.1.1.1] blocked using zen.spamhaus.org; from=<example@domain.com, to=<example01@domain.com>, proto=ESMTP, helo=<smtp.domain.com>
```

**Not:** DNSBL Threshold ayarı default olarak `1` sayısı ile gelmektedir. Bunun anlamı gönderen sunucunun IP adresi eklemiş olduğunuz DNSBL sitelerinden sadece bir tanesinde bulunuyor ise reddedecektir. Kullanımınıza göre arttırabilirsiniz.


## Yaşanabilecek Sorunlar

Seneryo da karşı taraf sizlere bir mail gönderiyor ve gönderinin sunucu IP adresi eklemiş olduğunuz RBL sitelerinde yer alıyor. Sadece belirli bir IP adresine veya domain için Whitelist oluşturabilirsiniz.


Mail Filter >> Who Objects >> sayfasına erişiyoruz.

![image](https://github.com/user-attachments/assets/0efc77ec-98ed-43a9-9848-a936a63a2a8e)


Whitelist sayfası üzerinden Add butonuna tıklıyoruz.


`Domain (Sender)` veya `IP Adress (Sender)` seçeneği ile engellenen domaini veya IP adresini ekleyebilirsiniz. Sadece bu ayar yetmemektedir. 


Tekrardan aynı sayfa üzerinde 

![image](https://github.com/user-attachments/assets/12b3725a-ec24-4062-bd25-3ebbd45f197a)

`No Matches` seçeneğini seçiyoruz. Bu seçeneği seçerek Whitelist üzerinde bulunan kurallar için herhangi bir işlem sağlanmayacaktır.

## Kaynakça

- [PMG Forum](https://forum.proxmox.com/threads/whitelist-not-working.54204/)



