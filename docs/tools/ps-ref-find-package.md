---
title: NuGet Bul-Package PowerShell başvurusu
description: Visual Studio'da NuGet Paket Yöneticisi konsolu Bul-Package PowerShell komutunda referansı.
author: karann-msft
ms.author: karann
ms.date: 6/1/2017
ms.topic: reference
ms.openlocfilehash: c6797e3778c7095a9abfc6cd87e2337313988c20
ms.sourcegitcommit: 1d1406764c6af5fb7801d462e0c4afc9092fa569
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43550984"
---
# <a name="find-package-package-manager-console-in-visual-studio"></a>Find-Package (Visual Studio'da Paket Yöneticisi Konsolu)

*Sürüm 3.0 +; Bu konu içindeki komut açıklar [NuGet Paket Yöneticisi Konsolu](package-manager-console.md) Windows üzerinde Visual Studio'da. Genel PowerShell Bul-Package komutu için bkz: [PowerShell PackageManagement başvuru](/powershell/module/packagemanagement/?view=powershell-6).*

Belirtilen kimliği veya anahtar sözcükleri ile uzak paketleri paket kaynağından alır.

## <a name="syntax"></a>Sözdizimi

```ps
Find-Package [-Id] <keywords> -Source <string> [-AllVersions] [-First [<int>]]
    [-Skip <int>] [-IncludePrerelease] [-ExactMatch] [-StartWith] [<CommonParameters>]
```

## <a name="parameters"></a>Parametreler

| Parametre | Açıklama |
| --- | --- |
| Kimliği &lt;anahtar sözcükleri&gt; | (Gerekli) Paket kaynağı ararken kullanmak için anahtar sözcükler. Paket kimliği anahtar sözcüklerle eşleşen paketleri döndürülecek - ExactMatch kullanın. Anahtar sözcük verilirse `Find-Package` ilk belirtilen-ilk 20 paketleri indirme veya sayı listesi döndürür. Kimliği isteğe bağlıdır ve İşlemsiz - unutmayın. |
| Kaynak | Aranacak paket kaynağı için URL veya klasör yolu. Yerel klasör yol mutlak veya göreli geçerli klasörde olabilir. Atlanırsa, `Find-Package` seçili paket kaynağı arar. |
| AllVersions | Tüm kullanılabilir sürümlerin her paketin yerine yalnızca en son sürümünü görüntüler. |
| ilk | Listeye başlangıcından itibaren döndürülecek paket sayısı; Varsayılan değer 20'dir. |
| Atla | İlk atlar &lt;int&gt; görüntülenen listeden paketleri.  |
| IncludePrerelease | Yayın öncesi paketleri sonuçları içerir. |
| ExactMatch | Belirtilen kullanılacak &lt;anahtar sözcükleri&gt; olarak büyük küçük harfe duyarlı paket kimliği |
| StartWith | Paketler, paket kimliği ile başlayan döndürür &lt;anahtar sözcükleri&gt;. |

Hiçbiri bu parametre ardışık düzen giriş veya joker karakterler kabul edin.

## <a name="common-parameters"></a>Ortak parametreleri

`Find-Package` şunları desteklemektedir [ortak PowerShell parametrelerini](http://go.microsoft.com/fwlink/?LinkID=113216): hata ayıklama, hata eylemi, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, ayrıntılı, WarningAction ve WarningVariable.

## <a name="examples"></a>Örnekler

```ps
# Find packages containing keywords
Find-Package elmah
Find-Package logging

# List packages whose ID begins with Elmah
Find-Package Elmah -StartWith

# By default, Get-Package returns a list of 20 packages; use -First to show more
Find-Package logging -First 100

# List all versions of the package with the ID of "jquery"
Find-Package jquery -AllVersions -ExactMatch
```
