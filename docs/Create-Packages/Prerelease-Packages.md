---
title: "NuGet paketlerini sürümlerde sürüm öncesi | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 8/14/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: df6a366a-22c1-47bb-8017-18231311ce88
description: "Yayın öncesi paketleri oluşturmak için yönergeler"
keywords: "sürüm oluşturma, NuGet paketini sürüm oluşturma, NuGet yayın öncesi sürümler, NuGet ön sürüm paketlerini, Önizleme paketi sürümleri, RC paketi sürümleri, Beta paketi sürümleri, NuGet anlamsal sürüm oluşturma"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 07cb9b9bdeeea6f283e95a11a06d7f2043c9b17c
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2017
---
# <a name="building-pre-release-packages"></a>Yayın öncesi paketleri oluşturma

Güncelleştirilmiş bir paketin yeni bir sürüm numarası olan yayın olduğunda, bir ", örneğin Paket Yöneticisi kullanıcı arabiriminde Visual Studio içinde gösterildiği gibi en son kararlı sürümü" olarak NuGet göz önünde bulundurur:

![Paket Yöneticisi en son kararlı sürümü gösteren UI](media/Prerelease_01-LatestStable.png)

Durağan sürümü üretimde kullanılacak güvenilir olarak görülmeyen biridir. En son kararlı sürümü de bir paket güncelleştirmesi veya paket geri yükleme sırasında yüklenecek sunucudur (açıklandığı gibi kısıtlamaları tabi [Reinstalling ve paketleri güncelleştiriliyor](../consume-packages/reinstalling-and-updating-packages.md)).

Yazılım sürüm yaşam döngüsü desteklemek için NuGet 1.6 ve üzeri yayın öncesi paket, dağıtım için burada sürüm numarası gibi bir anlamsal sürüm oluşturma soneki içerir verir `-alpha`, `-beta`, veya `-rc`. Daha fazla bilgi için bkz: [paket sürüm](../reference/package-versioning.md#pre-release-versions).

Bu tür sürümlerini iki yolla belirtebilirsiniz:

- `.nuspec`Dosya: semantik Sürüm soneki dahil `version` öğe:

    ```xml
    <version>1.0.1-alpha</version>
    ```

- Derleme özniteliklerinin: Visual Studio projesi paketinden oluştururken (`.csproj` veya `.vbproj`), kullanın `AssemblyInformationalVersionAttribute` sürüm belirtmek için:

    ```cs
    [assembly: AssemblyInformationalVersion("1.0.1-beta")]
    ```

    Bu değer yerine belirtilen bir NuGet alır `AssemblyVersion` anlamsal sürüm oluşturma desteklemiyor özniteliği.

Kararlı bir sürümünü hazır olduğunuzda, yalnızca soneki kaldırın ve paketin tüm yayın öncesi sürümlerini göre önceliklidir. Yeniden bkz [paket sürüm](../reference/package-versioning.md#pre-release-versions).


## <a name="installing-and-updating-pre-release-packages"></a>Yükleme ve ön sürüm paketlerini güncelleştirme

Varsayılan olarak, NuGet paketleri ile çalışırken, yayın öncesi sürümleri içermiyor, ancak bu davranışı aşağıdaki gibi değiştirebilirsiniz:

- **Visual Studio'da Paket Yöneticisi kullanıcı Arabirimi**: içinde **NuGet paketlerini Yönet** UI, onay **dahil et** kutusunda:

    ![Visual Studio INCLUDE Ön onay kutusu](media/Prerelease_02-CheckPrerelease.png)

    Ayarlama ya da bu kutusunu temizleyerek Paket Yöneticisi kullanıcı Arabirimi ve yükleyebileceğiniz kullanılabilir sürümlerin listesini yeniler.

- **Paket Yöneticisi Konsolu**: kullanım `-IncludePrerelease` anahtarı ile `Find-Package`, `Get-Package`, `Install-Package`, `Sync-Package`, ve `Update-Package` komutları. Başvurmak [PowerShell başvurusu](../tools/powershell-reference.md).

- **NuGet CLI**: kullanım `-prerelease` anahtarı ile `install`, `update`, `delete`, ve `mirror` komutları. Başvurmak [NuGet CLI başvurusu](../tools/nuget-exe-cli-reference.md)


## <a name="semantic-versioning"></a>Anlamsal sürüm oluşturma

[Anlamsal sürüm oluşturma veya SemVer kuralı](http://semver.org/spec/v1.0.0.html) iletmek için sürüm numaraları dizelerde kullanmaya açıklar arka plandaki kod anlamına gelir.

Bu kural, her üç bölümden sürümde `Major.Minor.Patch`, aşağıdaki anlamı ile:

- `Major`: Yeni değişiklikler
- `Minor`: Geriye dönük olarak uyumlu ancak yeni özellikler
- `Patch`: Geriye dönük uyumlu hata yalnızca düzeltmeleri

Yayın öncesi sürümleri kısa çizgi ve bir dize sonra düzeltme numarası ekleyerek belirtilir. Teknik olarak konuşarak kullanabilirsiniz * herhangi * tire ve NuGet paketi yayın öncesi kabul eder sonra dize. NuGet sonra kendileri için anlamı yorumlamaya tüketicileri bırakarak geçerli UI tam sürüm numarasını görüntüler.

Bu durum dikkate alınarak, aşağıdaki gibi tanınan adlandırma kurallarına uygun genellikle iyi olur:

- `-alpha`: Genelde iş ilerleme ve deneme için kullanılan alfa sürüm
- `-beta`: Beta sürümü, genellikle bir özellik için sonraki tam planlanmış serbest bırakma, ancak bilinen hataları içerebilir.
- `-rc`: Sürüm Adayı, genellikle büyük olasılıkla son bir yayın (stable) önemli hatalar ortaya çıkan sürece.

> [!Note]
> NuGet desteklemiyor [SemVer uyumlu (v2.0.0)](http://semver.org/spec/v2.0.0.html) yayın öncesi olarak noktalı gösterim ile numaraları `1.0.1-build.23`. Bir form gibi kullanabilirsiniz `1.0.1-build23` ancak bu her zaman bir yayım öncesi sürümü olarak kabul edilir.

Ancak, kullanan ne olursa olsun sonekleri NuGet bunları öncelik ters alfabetik sırada verecektir:

```
1.0.1
1.0.1-zzz
1.0.1-rc
1.0.1-open
1.0.1-beta12
1.0.1-beta05
1.0.1-beta
1.0.1-alpha2
1.0.1-alpha
```

Gösterildiği gibi herhangi bir sonek olmadan sürüm yayın öncesi sürümleri üzerinde her zaman öncelikli olur. Ayrıca ift kullanabilecek yayın öncesi etiketleriyle sayısal sonekleri kullanırsanız, sayılar (veya daha fazla), 2f3b beta01 ve beta05 olduğu gibi bunlar doğru sayıları büyük ulaştıklarında sıralaması emin olmak için unutmayın.