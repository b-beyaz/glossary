---
title: Servis Ağı
status: Completed
category: technology
tags: ["networking", "", ""]
---

[Mikroservis](/microservices-architecture/) dünyasında, uygulamalar bir ağ üzerinden iletişim kuran daha küçük [servisler](/service/) halinde parçalara ayrılır.
Wifi ağınızda olduğu gibi, bilgisayar ağları da doğası gereği güvenilmez, saldırıya açık ve çoğu zaman yavaştır.
Servis ağları, servisler arasındaki trafiği (yani iletişimi) yöneterek ve tüm servislere tekdüze biçimde [güvenilirlik](/reliability/), [gözlemlenebilirlik](/observability/) ve güvenlik özellikleri ekleyerek bu yeni zorluklar bütününü ele alır.

## Hangi Sorunları Çözer

Mikroservis mimarisine geçilmesiyle birlikte mühendisler, hepsinin birbiriyle iletişim kurması gereken yüzlerce, hatta binlerce servisle baş başa kalmaktadır.
Bu durum, ağ üzerinde çok büyük miktarda trafiğin ileri geri akması anlamına gelir.
Bunun yanı sıra, bireysel uygulamaların mevzuat gerekliliklerini karşılamak için iletişimi şifrelemesi, operasyon ekiplerine ortak metrikler sağlaması ya da sorunların teşhisine yardımcı olmak için trafik hakkında ayrıntılı sezgiler sunması gerekebilir.
Bu özelliklerin her biri ayrı ayrı uygulamalara dahil edildiğinde, ekipler arasında sürtüşmeye yol açar ve yeni özelliklerin geliştirilmesini yavaşlatır.

## Nasıl Yardımcı Olur

Servis ağları, kod değişikliği gerektirmeksizin bir kümedeki tüm servislere tekdüze biçimde güvenilirlik, gözlemlenebilirlik ve güvenlik özellikleri ekler.
Servis ağları ortaya çıkmadan önce bu işlevlerin her bir servise ayrı ayrı kodlanması gerekiyordu; bu durum potansiyel bir hata ve teknik borç kaynağına dönüşüyordu.

[Sidecar Konteyner](/sidecar-container/) modeli, her [pod](/pod/) ile bir proxy'yi eşleştirir.
Pod başına düşen bu proxy, ağ trafiğini yakalar ve yönetir, güvenlik politikalarını uygular, iş yüklerini dengeler ve her servis için performans verisi toplar.
Bu yaklaşım mükemmel bir kontrol ve servise özgü trafik yönetimi sunsa da daha fazla bilişim kaynağı tüketir ve sistem büyüdükçe yönetimi daha karmaşık bir hale gelir.

Öte yandan **Sidecar'sız** tasarım, söz konusu ağ işlevselliğini [eBPF](/ebpf/) gibi kernel özelliklerini kullanarak işletim sistemi düzeyine taşır.
Pod başına proxy'lerden vazgeçilerek bu yöntemle kaynak kullanımı önemli ölçüde azaltılır ve gereksiz ağ atlamaları ortadan kaldırılır; bu da gecikmeyi düşürür ve performansı artırır.
Genel yük, pod sayısından bağımsız olarak sabit kaldığından ve dağıtılacak daha az ajan bulunduğundan, ekipler iş yükü arttıkça basitleştirilmiş operasyonlar ve doğrusal ölçeklenebilirlikten yararlanır.