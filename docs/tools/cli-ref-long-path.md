---
title: NuGet CLI uzun yol desteği
description: Nuget.exe uzun yol desteği için başvuru
author: zhili1208
ms.author: lzhi
ms.date: 07/12/2018
ms.topic: reference
ms.openlocfilehash: 42b5b7d863d22d7aad99a65700ca11bcc2861db1
ms.sourcegitcommit: 0c5a49ec6e0254a4e7a9d8bca7daeefb853c433a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52453500"
---
# <a name="long-path-support-nuget-cli"></a>Uzun yol desteği (NuGet CLI)

**İçin geçerlidir:** tüm &bullet; **desteklenen sürümler:** 4.8 +

NuGet.exe 4,8 ve sonrasında destek uzun yollar dosyaları ve dizinleri senaryoları için paketi, geri yükleme, yükleme ve dosya yolları gereken Çoğu senaryoda ister.

## <a name="required-operating-system"></a>Gerekli işletim sistemi

-   Windows 10 (sürüm 1607 veya üzeri)
-   Windows 10 (Temmuz 2015 sürüm veya sürüm 1511) .NET Framework 4.6.2 sürümüne yükseltirseniz veya üzeri.
-   Windows Server 2016 (tüm sürümler)

## <a name="enable-win32-long-paths-group-policy"></a>"Win32 uzun yollar" Grup İlkesi'ni etkinleştir

Bir Grup İlkesi bu sistemlerde uzun yol desteğini etkinleştirmeniz gerekir.

Adımlar:
1. Başlatma **Grup İlkesi Düzenleyicisi** - türü "Başlangıç Arama çubuğuna Grup İlkesi düzenleme" veya "gpedit.msc" Run komutu (Windows-R) çalıştırın.
2. İçinde **yerel Grup İlkesi Düzenleyicisi**, etkinleştir "Yerel Bilgisayar İlkesi/Bilgisayar Yapılandırması/Yönetim Şablonları/tüm ayarları/etkinleştirme Win32 uzun yollar".

![Uzun yol İlkesi](media/LongPathPolicy.png)


> [!Note]
> Uzun yollar desteklemek için diğer NuGet araçları etkinleştirme
>
> -   DotNet CLI sürümü ve işletim sistemi ne olursa olsun uzun yollar destekler.
> -   Visual Studio veya msbuild - t: restore uzun yollar henüz desteklemiyor.
> -   Geri yükleme ve diğer komutları yürütmek için NuGet kitaplıklarını kullanan yazılım destekleyeceği uzun yollar aynı sistemlerde NuGet.exe üzerinde çalışan, ayrıca ayarlarsanız longPathAware kendi Windows bildirim ve UseLegacyPathHandling false App.Config aracılığıylayapılandırma[ Daha fazla bilgi](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/)

