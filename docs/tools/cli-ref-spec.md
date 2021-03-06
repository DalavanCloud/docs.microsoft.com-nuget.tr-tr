---
title: Özel NuGet CLI komutu
description: Nuget.exe özel komut başvurusu
author: karann-msft
ms.author: karann
ms.date: 01/18/2018
ms.topic: reference
ms.openlocfilehash: 68b165751ab6794d2a01d7e466619b1ce4d7ed72
ms.sourcegitcommit: 1d1406764c6af5fb7801d462e0c4afc9092fa569
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43546455"
---
# <a name="spec-command-nuget-cli"></a>özel komut (NuGet CLI)

**İçin geçerlidir:** paket oluşturma &bullet; **desteklenen sürümler:** tüm

Oluşturur bir `.nuspec` için yeni bir paket dosyası. Bir proje dosyası ile aynı klasörde çalıştırırsanız (`.csproj`, `.vbproj`, `.fsproj`), `spec` bir simgeleştirilmiş oluşturur `.nuspec` dosya. Ek bilgi için bkz: [paket oluşturma](../create-packages/creating-a-package.md).

## <a name="usage"></a>Kullanım

```cli
nuget spec [<packageID>] [options]
```

Burada `<packageID>` kaydetmek için bir isteğe bağlı paket tanımlayıcısı `.nuspec` dosya.

## <a name="options"></a>Seçenekler

| Seçenek | Açıklama |
| --- | --- |
| AssemblyPath | Meta verileri için kullanılacak derleme yolunu belirtir. |
| Zorla | Var olan tüm üzerine yazar `.nuspec` dosya. |
| ForceEnglishOutput | *(3.5 +)*  Nuget.exe sabit, İngilizce tabanlı bir kültürü kullanarak çalışmaya zorlar. |
| Yardım | Bilgi komut için yardımı görüntüler. |
| NonInteractive | Kullanıcı girişini veya onaylar ister bastırır. |
| Ayrıntı Düzeyi | Çıktıda gösterilen ayrıntı miktarını belirtir: *normal*, *sessiz*, *ayrıntılı*. |

Ayrıca bkz: [ortam değişkenleri](cli-ref-environment-variables.md)

## <a name="examples"></a>Örnekler

```cli
nuget spec

nuget spec MyPackage

nuget spec -AssemblyPath MyAssembly.dll
```
