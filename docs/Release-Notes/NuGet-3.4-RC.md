---
title: "NuGet 3.4 RC sürüm notları | Microsoft Docs"
author: karann-msft
ms.author: karann-msft
manager: ghogen
ms.date: 11/11/2016
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 239d3d95-5a72-4fac-8389-b6deac27884d
description: "NuGet 3.4 bilinen sorunları, hata düzeltmeleri, eklenen özellikleri ve dcr dahil olmak üzere RC sürüm notları."
keywords: "Özellikler, dcr bilinen sorunlar, NuGet 3.4 RC sürüm notları, hata düzeltmeleri eklendi"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 86c37d516eede2ac5e6e5e842f687a8f3b17c0a4
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2017
---
# <a name="nuget-34-rc-release-notes"></a>NuGet 3.4 RC sürüm notları

[NuGet 3.3 Sürüm Notları](../release-notes/nuget-3.3.md) | [NuGet 3.4 sürüm notları](../release-notes/nuget-3.4.md)

NuGet 3.4-RC, 3 Mart 2016 Visual Studio 2015 güncelleştirme 2 RC yanında yayımlanmıştır ve minds içinde birkaç tenets ile oluşturuldu:

*  Platformlar arası desteği
*  Performans iyileştirmeleri
*  İkincil UI geliştirmeleri

Aşağıdaki özellikler ile daha fazla 3.4 son sürüm için planlı bu RC'de kullanılabilir.

## <a name="new-features"></a>Yeni Özellikler

* Gzip içerik kodlamasına depoları gelen NuGet istemcileri artık destekler
* Xproj projelerindeki paketlerden PDB'leri için destek
* İOS ve Android derleme eylemleri contentFiles öğesindeki desteği
* Netstandard ve netstandardapp bilinen adları framework adları için destek

## <a name="new-user-interface-features"></a>Yeni kullanıcı arabirimi özellikleri

* Özellikle, yüklü, güncelleştirmeleri ve birleştirme sekmelerde önemli performans geliştirmeleri
* Yüklü ve güncelleştirmeleri sekmeler şimdi alfabetik olarak sıralanır.
* Yenilenecek bir arama özelliğine imkan tanıyan bir Yenile düğmesini eklendi

## <a name="updates-and-improvements"></a>Güncelleştirmeleri ve geliştirmeleri

* Başvurulan paketleri `project.json` sahip bir kayan sürüm üzerinde her yapı güncelleştirmez. Bunun yerine, bunlar yalnızca geri yükleme, temizleme, yeniden oluşturmak veya değiştirmek için zorlandığında güncelleştirecektir `project.json`.
* NuGet yapılandırma kullanıcı Arabirimi kullandığınızda nuget.org depo kaynakları artık bir proje yapılandırma zorlanır.
* Artık NuGet paketleri paylaşılan projelerinde yükler veya kilit dosyası yazar.
* Biz, ağ hatası geliştirildi ve işleme erişilemiyor veya yanıt ile yavaş sunucuları için yeniden deneyin.
* Klavye ve fare davranışları Visual Studio Paket Yöneticisi Arabiriminde geliştirildi.
* En son artık desteklenmektedir `project.json` DNX şemada.

## <a name="known-issues"></a>Bilinen Sorunlar

Bizim GitHub sorunları listedeki konumunda bulunan sorunları izlemek devam: [http://github.com/nuget/home/issues](http://github.com/nuget/home/issues)