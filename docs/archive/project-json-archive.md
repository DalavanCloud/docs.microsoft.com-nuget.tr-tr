---
title: "NuGet project.json arşiv içerik | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 01/17/2018
ms.topic: article
ms.prod: nuget
ms.technology: 
description: "Çeşitli BITS project.json içeriğin diğer NuGet belgelerine alanlarından kaldırıldı."
keywords: "NuGet project.json dosyası"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 1cca7304ee3dbecaed3fbb337ad2d31f383f4c43
ms.sourcegitcommit: 262d026beeffd4f3b6fc47d780a2f701451663a8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2018
---
# <a name="projectjson-archive"></a>project.json archive

`project.json` Başvuru biçimi NuGet ile sunulmuştur 3.x ve belirli proje türleri kullanılır. Bağımlılıklar doğrudan proje dosyasında listelenen PackageReference biçimi girişiyle kullanımdan kaldırılmıştır.

Ayrıca bkz.:

- [project.json schema](project-json.md)
- [Paketi yazarları Project.JSON etkisini](project-json-impact.md)
- [project.json ve UWP](project-json-and-uwp.md)

## <a name="projectjson-reference-format"></a>project.json reference format

*İlk olarak, [paket geri yüklemesi](../what-is-nuget.md).*

Başvuru biçimleri listesinde:

- [`project.json`](project-json.md): *(kullanım dışı)* proje bağımlılıkları ile ilişkili bir dosyası bir genel paket grafiğinde bir listesini tutar bir JSON dosyası `project.lock.json`. Bu biçim lehinde PackageReference kullanım dışıdır.

## <a name="nuget-restore-on-mono"></a>Mono nuget geri yükleme

*İlk olarak, [Nuget'i yükle istemci araçları](../install-nuget-client-tools.md).*

İle birlikte çalışır `project.json`.

## <a name="constraining-package-versions-with-restore"></a>Geri yükleme ile kısıtlayan paketi sürümleri

*İlk olarak, [paket geri yüklemesi](../consume-packages/package-restore.md#constraining-package-versions-with-restore).*

- `project.json`: Doğrudan bağımlılık ait sürüm numarasına sahip bir sürüm aralığı belirtin. Örneğin:

    ```json
    "Newtonsoft.json": "[6, 7)"
    ```

## <a name="nuget-cli-commands"></a>NuGet CLI komutları

- `nuget install`ile çalışmaz `project.json`.
- `nuget restore`: kullanarak projeleri ile `project.json`, oluşturan bir `project.lock.json` dosyası ve bir `<project>.nuget.props` gerekirse, dosya. (Her iki dosyası kaynak denetiminden atlanabilir.) `<projectPath>` Bağımsız değişkeni noktası bir `project.json` işaret olarak aynı davranışı sahiptir ve dosya bir `packages.config` veya proje dosyası. Paket klasörler için öncelik sırasına `%userprofile%\.nuget\packages` kullanırken ilk aranır `project.json`.
- `nuget update`: Mono üzerinde bu komutu kullanarak projeleri ile çalışmıyor `project.json`.

## <a name="dependency-resolution-with-packagereference"></a>PackageReference bir bağımlılık çözümleme

*İlk olarak, [bağımlılık çözümlemesi](../Consume-Packages/dependency-resolution.md#dependency-resolution-with-packagereference).*

PackageReference davranışını için de geçerlidir `project.json`. NuGet restore bağımlılık grafiğinin adlı bir dosyaya yazar `project.lock.json` yanında `project.json`.

## <a name="managing-dependency-assets"></a>Bağımlılık varlıklarını yönetme

*İlk olarak, [bağımlılık çözümlemesi](../Consume-Packages/dependency-resolution.md#managing-dependency-assets).*

Kullanırken `project.json` biçimi, en üst düzey proje bağımlılıkları akışına hangi varlıklarından kontrol edebilirsiniz. Ayrıntılar için bkz [project.json](project-json.md).

## <a name="excluding-references"></a>Başvuruları hariç

*İlk olarak, [bağımlılık çözümlemesi](../Consume-Packages/dependency-resolution.md#excluding-references).*

- `project.json`: eklemek `"exclude" : "all"` PackageC bağımlılığı içinde:

    ```json
    {
        "dependencies": {
            "PackageC": {
            "version": "1.0.0",
            "exclude": "all"
            }
        }
    }
    ```

## <a name="resolving-incompatible-package-errors"></a>Uyumsuz paket hatalarını çözme

*İlk olarak, [bağımlılık çözümlemesi](../Consume-Packages/dependency-resolution.md#resolving-incompatible-package-errors).*

Hataları çözümleme eklenen anlamına gelir:

- **Önerilmez**: geçici bir çözüm olarak için paket yazarına ile çalışırken projeleri hedefleyen `netcore`, `netstandard`, ve `netcoreapp` uyumlu, böylece bu hedefleme paketleri izin verme olarak diğer çerçeveler belirtmek kullanılacak diğer çerçeveler. Bkz: [project.json alır](project-json.md#imports) ve [MSBuild geri yükleme hedefi PackageTargetFallback](../schema/msbuild-targets.md#packagetargetfallback). Bu beklenmeyen davranışları neden şekilde yeniden üzerinde bir güncelleştirme için paket yazarına ile çalışarak paket uyumsuzlukları gidermek en iyisidir.

## <a name="target-frameworks"></a>Hedef Çerçeve

*İlk olarak, [hedef çerçeveler](../schema/target-frameworks.md).*

- [Project.JSON](project-json.md): `frameworks` düğümü karşı proje derlenmiş framework sürümlerini belirtir.

## <a name="creating-a-package"></a>Paket oluşturma

*İlk olarak, [paket oluşturma](../Create-Packages/creating-a-package.md)*

### <a name="setting-a-package-type"></a>Ayar paket türü

Pakette 1.x, paket yüklü DotnetCliTool, Visual Studio .NET Core ile yerleştirir `project.json` `tools` yerine düğümü `dependencies` düğümü.

Paket türleri ayarlanır `project.json`.

- `project.json`: İçinde paket türünü gösteren bir `packOptions.packageType` özelliği json:

    ```json
    {
        // ...
        "packOptions": {
        "packageType": "DotnetCliTool"
        }
    }
    ```

### <a name="adding-targets-and-props-for-msbuild"></a>MSBuild hedefleri ve özellik ekleme

*İlk olarak, [Visual Studio 2015 ile birlikte .NET standart NuGet paketlerini oluşturmak](../guides/create-net-standard-packages-vs2015.md).*

Kullanırken `project.json`, hedefleri projeye eklenmez ancak kullanılabilir hale getirilir `project.lock.json`.

### <a name="package-versioning"></a>Paket sürümü oluşturma

*İlk olarak, [paket sürüm](../reference/package-versioning.md).*

Kullanırken `project.json` biçimi, NuGet ayrıca bir joker karakter gösterimini kullanarak destekler \*, birincil, ikincil, düzeltme eki ve sayının yayın öncesi soneki bölümleri için.

### <a name="nugetconfig-reference"></a>NuGet.Config başvurusu

*İlk olarak, [NuGet.Config başvuru](../schema/nuget-config-file.md).*

`globalPackagesFolder`yalnızca geçerli `project.json`.

### <a name="nuspec-file-reference"></a>nuspec dosyası başvurusu

*İlk olarak, [nuspec başvuru](../schema/nuspec.md).*

`<contentFiles>` Öğe yerine kullanılır `<files>` ile `project.json`.

### <a name="package-manager-options-control"></a>Paket Yöneticisi seçenekleri denetimi

*İlk olarak, [Paket Yöneticisi kullanıcı Arabirimi başvurusu](../tools/Package-Manager-UI.md).*

Kullanarak projeleri `project.json` başvuru biçimi Göster yalnızca **Göster önizleme penceresi** seçeneği.

### <a name="visual-studio-templates"></a>Visual Studio şablonları

*İlk olarak, [Visual Studio şablonları NuGet paketlerine](../Visual-Studio-Extensibility/visual-studio-templates.md).*

En iyi uygulamalar: şablonları içermeyen bir `project.json` dosya ve içermeyen veya tüm başvuruları veya NuGet paketleri yüklendiğinde ekleneceği içerik.