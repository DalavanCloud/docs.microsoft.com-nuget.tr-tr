---
title: "NuGet paketi yüklemesi yolları | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 02/12/2018
ms.topic: get-started-article
ms.prod: nuget
ms.technology: 
description: "Bir projeye diskte ve geçerli proje dosyalarına olanlar da dahil olmak üzere NuGet paketlerini yükleme işlemi açıklanmaktadır."
keywords: "NuGet paketleri, NuGet paket referanslarını yükleniyor NuGet, NuGet paketi tüketim yükleyin"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 3bae03e148a366388c10d08e83c89dac6ff56d06
ms.sourcegitcommit: 33436d122873249dbb20616556cd8c6783f38909
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2018
---
# <a name="different-ways-to-install-a-nuget-package"></a><span data-ttu-id="be5bb-104">Bir NuGet paketi yüklemek için farklı yollar</span><span class="sxs-lookup"><span data-stu-id="be5bb-104">Different ways to install a NuGet Package</span></span>

<span data-ttu-id="be5bb-105">NuGet paketlerini karşıdan yüklenir ve aşağıdaki yöntemlerden birini kullanarak yüklü (bkz [Nuget'i yükle istemci araçları](../install-nuget-client-tools.md) Bunlar zaten yüklü yoksa):</span><span class="sxs-lookup"><span data-stu-id="be5bb-105">NuGet packages are downloaded and installed using any of the following methods (see [Install NuGet client tools](../install-nuget-client-tools.md) if you don't have these installed already):</span></span>

| <span data-ttu-id="be5bb-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="be5bb-106">Method</span></span> | <span data-ttu-id="be5bb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be5bb-107">Description</span></span> |
| --- | --- |
| <span data-ttu-id="be5bb-108">dotnet.exe CLI</span><span class="sxs-lookup"><span data-stu-id="be5bb-108">dotnet.exe CLI</span></span><br/>`dotnet install <package_name>` | <span data-ttu-id="be5bb-109">(Tüm platformlar) Tarafından tanımlanan paketi indirir \<paket_adı\>, bir klasöre geçerli dizinin içeriğini genişletir ve proje dosyasına bir başvuru ekler.</span><span class="sxs-lookup"><span data-stu-id="be5bb-109">(All platforms) Downloads the package identified by \<package_name\>, expands its contents into a folder in the current directory, and adds a reference to the project file.</span></span> <span data-ttu-id="be5bb-110">Ayrıca indirir ve bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="be5bb-110">Also downloads and installs dependencies.</span></span><ul><li>[<span data-ttu-id="be5bb-111">Paket (dotnet CLI) yükleme ve kullanma</span><span class="sxs-lookup"><span data-stu-id="be5bb-111">Install and use a package (dotnet CLI)</span></span>](../quickstart/install-and-use-a-package-using-the-dotnet-cli.md)</li><li>[<span data-ttu-id="be5bb-112">dotnet komutları</span><span class="sxs-lookup"><span data-stu-id="be5bb-112">dotnet commands</span></span>](../tools/dotnet-commands.md)</li></ul> |
| <span data-ttu-id="be5bb-113">Paket Yöneticisi kullanıcı Arabirimi (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="be5bb-113">Package Manager UI (Visual Studio)</span></span> | <span data-ttu-id="be5bb-114">(Windows ve Mac) Üzerinden, Gözat, seçebilir ve paketleri ve bunların bağımlılıklarını bir projeye yükle bir kullanıcı Arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="be5bb-114">(Windows and Mac) Provides a UI through which you can browse, select, and install packages and their dependencies into a project.</span></span> <span data-ttu-id="be5bb-115">Yüklü paketler başvuruları proje dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="be5bb-115">Adds references to installed packages to the project file.</span></span><ul><li>[<span data-ttu-id="be5bb-116">Paket (dotnet CLI) yükleme ve kullanma</span><span class="sxs-lookup"><span data-stu-id="be5bb-116">Install and use a package (Visual Studio)</span></span>](../quickstart/install-and-use-a-package-in-visual-studio.md)</li><li>[<span data-ttu-id="be5bb-117">Paket Yöneticisi kullanıcı Arabirimi başvurusu (Windows)</span><span class="sxs-lookup"><span data-stu-id="be5bb-117">Package Manager UI reference (Windows)</span></span>](../tools/package-manager-ui.md)</li><li>[<span data-ttu-id="be5bb-118">NuGet paketini projenize (Mac) dahil olmak üzere</span><span class="sxs-lookup"><span data-stu-id="be5bb-118">Including a NuGet package in your project (Mac)</span></span>](/visualstudio/mac/nuget-walkthrough)</li></ul> |
| <span data-ttu-id="be5bb-119">Paket Yöneticisi Konsolu (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="be5bb-119">Package Manager Console (Visual Studio)</span></span><br/>`Install-Package <package_name>` | <span data-ttu-id="be5bb-120">(Yalnızca Windows) İndirir ve tarafından tanımlanan paketi yükler \<paket_adı\> çözümdeki belirtilen projeye sonra proje dosyasına bir başvuru ekler.</span><span class="sxs-lookup"><span data-stu-id="be5bb-120">(Windows only) Downloads and installs the package identified by \<package_name\> into a specified project in the solution, then adds a reference to the project file.</span></span> <span data-ttu-id="be5bb-121">Ayrıca indirir ve bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="be5bb-121">Also downloads and installs dependencies.</span></span><ul><li>[<span data-ttu-id="be5bb-122">Paket (dotnet CLI) yükleme ve kullanma</span><span class="sxs-lookup"><span data-stu-id="be5bb-122">Install and use a package (Visual Studio)</span></span>](../quickstart/install-and-use-a-package-in-visual-studio.md)</li><li>[<span data-ttu-id="be5bb-123">Paket Yöneticisi konsolu Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="be5bb-123">Package Manager Console guide</span></span>](../tools/package-manager-console.md)</li></ul> |
| <span data-ttu-id="be5bb-124">nuget.exe CLI</span><span class="sxs-lookup"><span data-stu-id="be5bb-124">nuget.exe CLI</span></span><br/>`nuget install <package_name>` | <span data-ttu-id="be5bb-125">(Tüm platformlar) Tarafından tanımlanan paketi indirir \<paket_adı\> ve geçerli dizinde bir klasöre içeriğinin genişletir; listelenen tüm paketler de indirebilirsiniz bir `packages.config` dosyası.</span><span class="sxs-lookup"><span data-stu-id="be5bb-125">(All platforms) Downloads the package identified by \<package_name\> and expands its contents into a folder in the current directory; can also download all packages listed in a `packages.config` file.</span></span> <span data-ttu-id="be5bb-126">Ayrıca indirir ve bağımlılıkları yükler, ancak proje dosyalarına hiçbir değişiklik yapmaz.</span><span class="sxs-lookup"><span data-stu-id="be5bb-126">Also downloads and installs dependencies, but makes no changes to project files.</span></span><ul><li>[<span data-ttu-id="be5bb-127">Yükleme komutu</span><span class="sxs-lookup"><span data-stu-id="be5bb-127">install command</span></span>](../tools/cli-ref-install.md)</li></ul> |

## <a name="general-install-process"></a><span data-ttu-id="be5bb-128">Genel yükleme işlemi</span><span class="sxs-lookup"><span data-stu-id="be5bb-128">General install process</span></span>

<span data-ttu-id="be5bb-129">Genel olarak, NuGet paket yükleme istenir şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="be5bb-129">In general, NuGet does the following then asked to install a package:</span></span>

1. <span data-ttu-id="be5bb-130">Paket edinin:</span><span class="sxs-lookup"><span data-stu-id="be5bb-130">Acquire the package:</span></span>
    - <span data-ttu-id="be5bb-131">İstenen paketin bir önbellekte olup olmadığını denetle (bkz [NuGet önbelleği yönetme](managing-the-nuget-cache.md)).</span><span class="sxs-lookup"><span data-stu-id="be5bb-131">Check if the requested package already exists in a cache (see [Managing the NuGet cache](managing-the-nuget-cache.md)).</span></span>
    - <span data-ttu-id="be5bb-132">Paket önbellekte değilse, listelenen kaynaklardan gelen paket indirme girişiminde [yapılandırma dosyalarını](Configuring-NuGet-Behavior.md).</span><span class="sxs-lookup"><span data-stu-id="be5bb-132">If the package is not in the cache, attempt to download the package from the sources listed in the [configuration files](Configuring-NuGet-Behavior.md).</span></span>
      - <span data-ttu-id="be5bb-133">Kullanarak projeleri için `packages.config` başvuru biçimi, NuGet sırayı yapılandırmasında kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="be5bb-133">For projects using the `packages.config` reference format, NuGet uses the order of the sources in the configuration.</span></span>
      - <span data-ttu-id="be5bb-134">PackageReference biçimi kullanarak projeleri için NuGet önce yerel klasörleri olan kaynakları denetler ağ paylaşımları üzerindeki kaynakları denetler, sonra HTTP (Internet) kaynakları denetler.</span><span class="sxs-lookup"><span data-stu-id="be5bb-134">For projects using the PackageReference format, NuGet checks sources that are local folders first, then checks sources on network shares, then checks HTTP (Internet) sources.</span></span>
      - <span data-ttu-id="be5bb-135">Genel olarak, belirli bir tanımlayıcı ve sürüm numarası ile verilen herhangi bir paket tam olarak aynı bulduğunda ne olursa olsun kaynağında olduğundan NuGet kaynakları denetler sipariş özellikle anlamlı değil.</span><span class="sxs-lookup"><span data-stu-id="be5bb-135">In general, the order in which NuGet checks sources isn't particularly meaningful, because any given package with a specific identifier and version number is exactly the same on whatever source it's found.</span></span>
    - <span data-ttu-id="be5bb-136">NuGet paketi başarıyla kaynaklardan biri satın aldıysanız, önbelleğe ekler.</span><span class="sxs-lookup"><span data-stu-id="be5bb-136">If the package is successfully acquired from one of the sources, NuGet adds it to the cache.</span></span> <span data-ttu-id="be5bb-137">Aksi takdirde yükleme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="be5bb-137">Otherwise, installation fails.</span></span>

1. <span data-ttu-id="be5bb-138">Paketini projeye genişletin.</span><span class="sxs-lookup"><span data-stu-id="be5bb-138">Expand the package into the project.</span></span>
    - <span data-ttu-id="be5bb-139">Paketin içeriği uygun bir alt klasöre unzipping genişleyen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="be5bb-139">Expanding means unzipping the package's contents into an appropriate subfolder.</span></span> <span data-ttu-id="be5bb-140">Bir kopyasını `.nupkg` kendisi de alt klasöründe yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="be5bb-140">A copy of the `.nupkg` itself is also placed in the subfolder.</span></span>
    - <span data-ttu-id="be5bb-141">Paket bir Visual Studio veya .NET Core projeye yüklü ise yalnızca projenin hedef çerçevesi için ilgili dosyaların genişletilir.</span><span class="sxs-lookup"><span data-stu-id="be5bb-141">If the package is being installed into a Visual Studio or .NET Core project, only the files relevant to the project's target framework are expanded.</span></span> <span data-ttu-id="be5bb-142">Nuget.exe komut satırını kullanarak yüklediğinizde, tüm derlemelerde genişletilir.</span><span class="sxs-lookup"><span data-stu-id="be5bb-142">When installed using the nuget.exe command line, all assemblies are expanded.</span></span>

1. <span data-ttu-id="be5bb-143">Paket Visual Studio veya CLI dotnet içinde yüklediyseniz uygun proje dosyasına bir başvuru eklenir (veya `packages.config` bazı Visual Studio Proje türleri için).</span><span class="sxs-lookup"><span data-stu-id="be5bb-143">If the package is installed within Visual Studio or the dotnet CLI, a reference is added to the appropriate project file (or `packages.config` for some project types in Visual Studio).</span></span>

## <a name="related-topics"></a><span data-ttu-id="be5bb-144">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="be5bb-144">Related topics</span></span>

- [<span data-ttu-id="be5bb-145">Genel bakış ve iş akışı paket tüketimi</span><span class="sxs-lookup"><span data-stu-id="be5bb-145">Overview and workflow of package consumption</span></span>](../consume-packages/overview-and-workflow.md)
- [<span data-ttu-id="be5bb-146">Paketleri bulma ve seçme</span><span class="sxs-lookup"><span data-stu-id="be5bb-146">Finding and choosing packages</span></span>](../consume-packages/finding-and-choosing-packages.md)
- [<span data-ttu-id="be5bb-147">NuGet davranışını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="be5bb-147">Configuring NuGet behavior</span></span>](../consume-packages/configuring-nuget-behavior.md)
- [<span data-ttu-id="be5bb-148">NuGet önbelleğini yönetme</span><span class="sxs-lookup"><span data-stu-id="be5bb-148">Managing the NuGet cache</span></span>](managing-the-nuget-cache.md)