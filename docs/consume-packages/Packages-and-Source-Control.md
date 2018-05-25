---
title: NuGet paketleri ve kaynak denetimi
description: Sürüm denetimi ve kaynak denetim sistemleri içindeki NuGet paketleri kabul etme ve git ve TFVC'yi paketlerle atlayın durumları.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 03/16/2018
ms.topic: conceptual
ms.openlocfilehash: bc2c6d5e9933f2f6103363a2e69fbb9b47f80ecf
ms.sourcegitcommit: 8127dd73ff8481a1a01acd9b7004dd131a9d84e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
---
# <a name="omitting-nuget-packages-in-source-control-systems"></a><span data-ttu-id="efad7-103">Kaynak Denetim sistemleri NuGet paketlerini atlama</span><span class="sxs-lookup"><span data-stu-id="efad7-103">Omitting NuGet packages in source control systems</span></span>

<span data-ttu-id="efad7-104">Geliştiriciler genellikle kendi kaynak denetimi depoları NuGet paketleri atlayın ve bunun yerine Bel [paket geri yükleme](package-restore.md) bir yapı önce bir proje bağımlılıklarınızı yeniden yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="efad7-104">Developers typically omit NuGet packages from their source control repositories and rely instead on [package restore](package-restore.md) to reinstall a project's dependencies before a build.</span></span>

<span data-ttu-id="efad7-105">Paket geri yükleme bağlı nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="efad7-105">The reasons for relying on package restore include the following:</span></span>

1. <span data-ttu-id="efad7-106">Git gibi dağıtılmış sürüm denetim sistemleri her sürüm deposu içinde her dosyanın tam kopyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="efad7-106">Distributed version control systems, such as Git, include full copies of every version of every file within the repository.</span></span> <span data-ttu-id="efad7-107">Sık sık güncelleştirilen ikili dosyaları için önemli oluşan şişirmeyi sağlama ve depoyu kopyalayın süresini düşey çizgi ise uzar.</span><span class="sxs-lookup"><span data-stu-id="efad7-107">Binary files that are frequently updated lead to significant bloat and lengthens the time it takes to clone the repository.</span></span>
1. <span data-ttu-id="efad7-108">Paketleri depoya eklendiğinde, geliştiricilerin, doğrudan paket içeriğini başvuru paketler sabit kodlanmış yol adları projesinde açabilir NuGet aracılığıyla yerine disk eklemek zararlardan önerilir.</span><span class="sxs-lookup"><span data-stu-id="efad7-108">When packages are included in the repository, developers are liable to add references directly to package contents on disk rather than referencing packages through NuGet, which can lead to hard-coded path names in the project.</span></span>
1. <span data-ttu-id="efad7-109">Paket klasörleri hala kullanımda silmeyin emin olmak gereksinim duyduğunuz çözümünüzün herhangi kullanılmayan paket klasörlerinin temiz zor olur.</span><span class="sxs-lookup"><span data-stu-id="efad7-109">It becomes harder to clean your solution of any unused package folders, as you need to ensure you don't delete any package folders still in use.</span></span>
1. <span data-ttu-id="efad7-110">Paketleri kaldırarak sahipliği temiz sınırlarının kodunuzu, bağlı diğer paketleri arasındaki korur.</span><span class="sxs-lookup"><span data-stu-id="efad7-110">By omitting packages, you maintain clean boundaries of ownership between your code and the packages from others that you depend upon.</span></span> <span data-ttu-id="efad7-111">Birçok NuGet paketleri kendi kaynak denetimi depoları zaten saklanır.</span><span class="sxs-lookup"><span data-stu-id="efad7-111">Many NuGet packages are maintained in their own source control repositories already.</span></span>

<span data-ttu-id="efad7-112">Paket geri yüklemesi varsayılan davranışı NuGet ile el ile bazı iş paketleri atlamak gerekli olsa da&mdash;öğesine, `packages` projenizdeki klasöre&mdash;kaynak denetiminden bu makalede anlatıldığı gibi.</span><span class="sxs-lookup"><span data-stu-id="efad7-112">Although package restore is the default behavior with NuGet, some manual work is necessary to omit packages&mdash;namely, the `packages` folder in your project&mdash;from source control, as described in this article.</span></span>

## <a name="omitting-packages-with-git"></a><span data-ttu-id="efad7-113">Git paketlerle atlama</span><span class="sxs-lookup"><span data-stu-id="efad7-113">Omitting packages with Git</span></span>

<span data-ttu-id="efad7-114">Kullanım [.gitignore dosyası](https://git-scm.com/docs/gitignore) NuGet paketlerini yoksaymak için (`.nupkg`) `packages` klasörünü ve `project.assets.json`, başka şeylerin.</span><span class="sxs-lookup"><span data-stu-id="efad7-114">Use the [.gitignore file](https://git-scm.com/docs/gitignore) to ignore NuGet packages (`.nupkg`) the `packages` folder, and `project.assets.json`, among other things.</span></span> <span data-ttu-id="efad7-115">Başvuru için bkz: [örnek `.gitignore` Visual Studio projeleri için](https://github.com/github/gitignore/blob/master/VisualStudio.gitignore):</span><span class="sxs-lookup"><span data-stu-id="efad7-115">For reference, see the [sample `.gitignore` for Visual Studio projects](https://github.com/github/gitignore/blob/master/VisualStudio.gitignore):</span></span>

<span data-ttu-id="efad7-116">Önemli kısımlarını `.gitignore` dosyası:</span><span class="sxs-lookup"><span data-stu-id="efad7-116">The important parts of the `.gitignore` file are:</span></span>

```gitignore
# Ignore NuGet Packages
*.nupkg

# The packages folder can be ignored because of Package Restore
**/[Pp]ackages/*

# except build/, which is used as an MSBuild target.
!**/[Pp]ackages/build/

# Uncomment if necessary however generally it will be regenerated when needed
#!**/[Pp]ackages/repositories.config

# NuGet v3's project.json files produces more ignorable files
*.nuget.props
*.nuget.targets

# Ignore other intermediate files that NuGet might create. project.lock.json is used in conjunction
# with project.json (NuGet v3); project.assets.json is used in conjunction with the PackageReference
# format (NuGet v4 and .NET Core).
project.lock.json
project.assets.json
```

## <a name="omitting-packages-with-team-foundation-version-control"></a><span data-ttu-id="efad7-117">Team Foundation sürüm denetimi paketlerle atlama</span><span class="sxs-lookup"><span data-stu-id="efad7-117">Omitting packages with Team Foundation Version Control</span></span>

> [!Note]
> <span data-ttu-id="efad7-118">Bu yönergeleri mümkünse *önce* projenizi kaynak denetimine ekleme.</span><span class="sxs-lookup"><span data-stu-id="efad7-118">Follow these instructions if possible *before* adding your project to source control.</span></span> <span data-ttu-id="efad7-119">Aksi takdirde, el ile silmeniz `packages` klasöründen depo ve devam etmeden önce bu değişikliği denetleyin.</span><span class="sxs-lookup"><span data-stu-id="efad7-119">Otherwise, manually delete the `packages` folder from your repository and check in that change before continuing.</span></span>

<span data-ttu-id="efad7-120">Seçili dosyaları için TFVC'yi kaynak denetimi tümleştirmesi devre dışı bırakmak için:</span><span class="sxs-lookup"><span data-stu-id="efad7-120">To disable source control integration with TFVC for selected files:</span></span>

1. <span data-ttu-id="efad7-121">Adlı bir klasör oluşturun `.nuget` çözüm klasördeki (burada `.sln` dosyası).</span><span class="sxs-lookup"><span data-stu-id="efad7-121">Create a folder called `.nuget` in your solution folder (where the `.sln` file is).</span></span>
    - <span data-ttu-id="efad7-122">İpucu: Kullanın adı, Windows bu klasörü Windows Gezgini'nde oluşturmak için `.nuget.` *ile* sondaki noktayı.</span><span class="sxs-lookup"><span data-stu-id="efad7-122">Tip: on Windows, to create this folder in Windows Explorer, use the name `.nuget.` *with* the trailing dot.</span></span>

1. <span data-ttu-id="efad7-123">Bu klasörde adlı bir dosya oluşturun `NuGet.Config` ve düzenlemek için açın.</span><span class="sxs-lookup"><span data-stu-id="efad7-123">In that folder, create a file named `NuGet.Config` and open it for editing.</span></span>

1. <span data-ttu-id="efad7-124">Minimum olarak aşağıdaki metni ekleyin nerede [disableSourceControlIntegration](../reference/nuget-config-file.md#solution-section) ayarı bildirir her şeyi atlamak için Visual Studio `packages` klasörü:</span><span class="sxs-lookup"><span data-stu-id="efad7-124">Add the following text as a minimum, where the [disableSourceControlIntegration](../reference/nuget-config-file.md#solution-section) setting instructs Visual Studio to skip everything in the `packages` folder:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
       <solution>
           <add key="disableSourceControlIntegration" value="true" />
       </solution>
   </configuration>
   ```

1. <span data-ttu-id="efad7-125">TFS 2010 veya önceki bir sürümünü kullanıyorsanız, gizlemek `packages` çalışma eşlemelerinizin klasöründe.</span><span class="sxs-lookup"><span data-stu-id="efad7-125">If you are using TFS 2010 or earlier, cloak the `packages` folder in your workspace mappings.</span></span>

1. <span data-ttu-id="efad7-126">TFS 2012 veya sonraki sürümünü veya Visual Studio Team Services ile oluşturma bir `.tfignore` dosya açıklandığı gibi [AddFiles sunucuya](/vsts/tfvc/add-files-server.md?view=vsts#tfignore).</span><span class="sxs-lookup"><span data-stu-id="efad7-126">On TFS 2012 or later, or with Visual Studio Team Services, create a `.tfignore` file as described on [AddFiles to the Server](/vsts/tfvc/add-files-server.md?view=vsts#tfignore).</span></span> <span data-ttu-id="efad7-127">Bu dosyada yapılan değişiklikler açıkça yoksaymak için aşağıdaki içerik `\packages` depo düzeyi ve diğer birkaç Ara dosyaları klasörü.</span><span class="sxs-lookup"><span data-stu-id="efad7-127">In that file, include the content below to explicitly ignore modifications to the `\packages` folder on the repository level and a few other intermediate files.</span></span> <span data-ttu-id="efad7-128">(Dosya adını kullanarak Windows Gezgini'nde oluşturabileceğiniz bir `.tfignore.` sondaki noktayı, ancak ile devre dışı bırakmak için "Bilinen dosya uzantılarını gizle" ilk seçenek.):</span><span class="sxs-lookup"><span data-stu-id="efad7-128">(You can create the file in Windows Explorer using the name a `.tfignore.` with the trailing dot, but you might need to disable the "Hide known file extensions" option first.):</span></span>

   ```cli
   # Ignore NuGet Packages
   *.nupkg

   # Ignore the NuGet packages folder in the root of the repository. If needed, prefix 'packages'
   # with additional folder names if it's not in the same folder as .tfignore.   
   packages

   # Exclude package target files which may be required for MSBuild, again prefixing the folder name as needed.
   !packages/*.targets

   # Omit temporary files
   project.lock.json
   project.assets.json
   *.nuget.props
   ```

1. <span data-ttu-id="efad7-129">Ekleme `NuGet.Config` ve `.tfignore` kaynak denetimi ve yaptığınız değişiklikleri denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="efad7-129">Add `NuGet.Config` and `.tfignore` to source control and check in your changes.</span></span>