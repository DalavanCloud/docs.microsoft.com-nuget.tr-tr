---
title: Oluşturma ve yayımlama dotnet CLI kullanarak bir NuGet paketi
description: Oluşturma ve yayımlama dotnet .NET Core CLI kullanarak bir NuGet paketi bir gözden geçirme Öğreticisi.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 01/24/2018
ms.topic: quickstart
ms.openlocfilehash: e47eb5f9b3cd7e915db82f043ebb6190b656fb28
ms.sourcegitcommit: a6ca160b1e7e5c58b135af4eba0e9463127a59e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="quickstart-create-and-publish-a-package-dotnet-cli"></a><span data-ttu-id="367a1-103">Hızlı Başlangıç: Oluşturma ve bir paket (dotnet CLI) yayımlama</span><span class="sxs-lookup"><span data-stu-id="367a1-103">Quickstart: Create and publish a package (dotnet CLI)</span></span>

<span data-ttu-id="367a1-104">Bir .NET sınıf kitaplığı'ndan bir NuGet paketi oluşturmak ve nuget.org kullanarak yayımlamak için basit bir işlemdir `dotnet` komut satırı arabirimi (CLI).</span><span class="sxs-lookup"><span data-stu-id="367a1-104">It's a simple process to create a NuGet package from a .NET Class Library and publish it to nuget.org using the `dotnet` command-line interface (CLI).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="367a1-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="367a1-105">Prerequisites</span></span>

1. <span data-ttu-id="367a1-106">Yükleme [.NET Core SDK](https://www.microsoft.com/net/download/), içeren `dotnet` CLI.</span><span class="sxs-lookup"><span data-stu-id="367a1-106">Install the [.NET Core SDK](https://www.microsoft.com/net/download/), which includes the `dotnet` CLI.</span></span>

1. <span data-ttu-id="367a1-107">[Kayıt nuget.org ücretsiz bir hesap için](https://www.nuget.org/users/account/LogOn?returnUrl=%2F) zaten yoksa.</span><span class="sxs-lookup"><span data-stu-id="367a1-107">[Register for a free account on nuget.org](https://www.nuget.org/users/account/LogOn?returnUrl=%2F) if you don't have one already.</span></span> <span data-ttu-id="367a1-108">Yeni bir hesap oluşturmadan bir onay e-posta gönderir.</span><span class="sxs-lookup"><span data-stu-id="367a1-108">Creating a new account sends a confirmation email.</span></span> <span data-ttu-id="367a1-109">Bir paket karşıya yüklemeden önce hesap onaylamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="367a1-109">You must confirm the account before you can upload a package.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="367a1-110">Sınıf kitaplığı proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="367a1-110">Create a class library project</span></span>

<span data-ttu-id="367a1-111">Varolan bir .NET sınıf kitaplığı proje paketini veya basit bir şekilde oluşturmak için istediğiniz kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="367a1-111">You can use an existing .NET Class Library project for the code you want to package, or create a simple one as follows:</span></span>

1. <span data-ttu-id="367a1-112">Adlı bir klasör oluşturun `AppLogger` ve içine değiştirin.</span><span class="sxs-lookup"><span data-stu-id="367a1-112">Create a folder called `AppLogger` and change into it.</span></span>

1. <span data-ttu-id="367a1-113">Kullanarak projeyi oluşturmak `dotnet new classlib`, proje için geçerli klasörün adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="367a1-113">Create the project using `dotnet new classlib`, which uses the name of the current folder for the project.</span></span>

## <a name="add-package-metadata-to-the-project-file"></a><span data-ttu-id="367a1-114">Proje dosyasına paket meta verileri ekleme</span><span class="sxs-lookup"><span data-stu-id="367a1-114">Add package metadata to the project file</span></span>

<span data-ttu-id="367a1-115">Her NuGet paketi paketin içeriği ve bağımlılıkları tanımlayan bir bildirim gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="367a1-115">Every NuGet package needs a manifest that describes the package's contents and dependencies.</span></span> <span data-ttu-id="367a1-116">Son bir pakette bildirimidir bir `.nuspec` proje dosyasında dahil NuGet meta verileri özelliklerinden oluşturulan dosya.</span><span class="sxs-lookup"><span data-stu-id="367a1-116">In a final package, the manifest is a `.nuspec` file that is generated from the NuGet metadata properties that you include in the project file.</span></span>

1. <span data-ttu-id="367a1-117">Proje dosyasını açın (`.csproj`) ve çıkma içinde en az aşağıdaki özellikleri ekleyin `<PropertyGroup>` değerleri uygun şekilde değiştirerek etiketi:</span><span class="sxs-lookup"><span data-stu-id="367a1-117">Open your project file (`.csproj`) and add the following minimal properties inside the exiting `<PropertyGroup>` tag, changing the values as appropriate:</span></span>

    ```xml
    <PackageId>AppLogger</PackageId>
    <Version>1.0.0</Version>
    <Authors>your_name</Authors>
    <Company>your_company</Company>
    ```

    > [!Important]
    > <span data-ttu-id="367a1-118">Nuget.org veya ne olursa olsun, ana bilgisayar genelinde benzersiz bir tanımlayıcı kullanmakta olduğunuz paket verin.</span><span class="sxs-lookup"><span data-stu-id="367a1-118">Give the package an identifier that's unique across nuget.org or whatever host you're using.</span></span> <span data-ttu-id="367a1-119">Bu kılavuz için (Bu herkes gerçekte kullanacağı olsa da) sonraki yayımlama adım paketi herkese görünür hale "Sample" veya "Test" adı dahil olmak üzere öneririz.</span><span class="sxs-lookup"><span data-stu-id="367a1-119">For this walkthrough we recommend including "Sample" or "Test" in the name as the later publishing step does make the package publicly visible (though it's unlikely anyone will actually use it).</span></span>

1. <span data-ttu-id="367a1-120">Açıklandığı isteğe bağlı özelliklerin eklemek [NuGet meta veri özelliklerini](/dotnet/core/tools/csproj#nuget-metadata-properties).</span><span class="sxs-lookup"><span data-stu-id="367a1-120">Add any optional properties described on [NuGet metadata properties](/dotnet/core/tools/csproj#nuget-metadata-properties).</span></span>

    > [!Note]
    > <span data-ttu-id="367a1-121">Ortak tüketim için oluşturulan paketler için özel dikkat **PackageTags** özelliği gibi etiketler başkalarının paketinizi bulun ve neler yaptığını anlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="367a1-121">For packages built for public consumption, pay special attention to the **PackageTags** property, as tags help others find your package and understand what it does.</span></span>

## <a name="run-the-pack-command"></a><span data-ttu-id="367a1-122">Paketi komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="367a1-122">Run the pack command</span></span>

<span data-ttu-id="367a1-123">Bir NuGet paketi oluşturmak için (bir `.nupkg` dosyası) projeden çalıştırma `dotnet pack` ayrıca projenin otomatik olarak oluşturur komutu:</span><span class="sxs-lookup"><span data-stu-id="367a1-123">To build a NuGet package (a `.nupkg` file) from the project, run the `dotnet pack` command, which also builds the project automatically:</span></span>

```cli
# Uses the project file in the current folder by default
dotnet pack
```

<span data-ttu-id="367a1-124">Çıkış yolu gösterir `.nupkg` dosyası:</span><span class="sxs-lookup"><span data-stu-id="367a1-124">The output shows the path to the `.nupkg` file:</span></span>

```output
Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 29.91 ms for D:\proj\AppLoggerNet\AppLogger\AppLogger.csproj.
  AppLogger -> D:\proj\AppLoggerNet\AppLogger\bin\Debug\netstandard2.0\AppLogger.dll
  Successfully created package 'D:\proj\AppLoggerNet\AppLogger\bin\Debug\AppLogger.1.0.0.nupkg'.
```

### <a name="automatically-generate-package-on-build"></a><span data-ttu-id="367a1-125">Yapı paketini otomatik olarak oluştur</span><span class="sxs-lookup"><span data-stu-id="367a1-125">Automatically generate package on build</span></span>

<span data-ttu-id="367a1-126">Otomatik olarak çalışacak şekilde `dotnet pack` çalıştırdığınızda `dotnet build`, proje dosyasında aşağıdaki satırı ekleyin `<PropertyGroup>`:</span><span class="sxs-lookup"><span data-stu-id="367a1-126">To automatically run `dotnet pack` when you run `dotnet build`, add the following line to your project file within `<PropertyGroup>`:</span></span>

```xml
<GeneratePackageOnBuild>true</GeneratePackageOnBuild>
```

## <a name="publish-the-package"></a><span data-ttu-id="367a1-127">Paket yayımlama</span><span class="sxs-lookup"><span data-stu-id="367a1-127">Publish the package</span></span>

<span data-ttu-id="367a1-128">Bulduktan sonra bir `.nupkg` dosyası, yayımlama, nuget.org kullanmaya `dotnet nuget push` nuget.org alınan bir API anahtarı ile birlikte komutu.</span><span class="sxs-lookup"><span data-stu-id="367a1-128">Once you have a `.nupkg` file, you publish it to nuget.org using the `dotnet nuget push` command along with an API key acquired from nuget.org.</span></span>

[!INCLUDE [publish-notes](includes/publish-notes.md)]

### <a name="acquire-your-api-key"></a><span data-ttu-id="367a1-129">API anahtarınızı edinin</span><span class="sxs-lookup"><span data-stu-id="367a1-129">Acquire your API key</span></span>

[!INCLUDE [publish-api-key](includes/publish-api-key.md)]

### <a name="publish-with-dotnet-nuget-push"></a><span data-ttu-id="367a1-130">DotNet nuget itme ile yayımlama</span><span class="sxs-lookup"><span data-stu-id="367a1-130">Publish with dotnet nuget push</span></span>

[!INCLUDE [publish-dotnet](includes/publish-dotnet.md)]

### <a name="publish-errors"></a><span data-ttu-id="367a1-131">Hataları yayımlama</span><span class="sxs-lookup"><span data-stu-id="367a1-131">Publish errors</span></span>

[!INCLUDE [publish-errors](includes/publish-errors.md)]

### <a name="manage-the-published-package"></a><span data-ttu-id="367a1-132">Yayımlanan paket yönetme</span><span class="sxs-lookup"><span data-stu-id="367a1-132">Manage the published package</span></span>

[!INCLUDE [publish-manage](includes/publish-manage.md)]

## <a name="related-topics"></a><span data-ttu-id="367a1-133">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="367a1-133">Related topics</span></span>

- [<span data-ttu-id="367a1-134">Bir paket oluşturun</span><span class="sxs-lookup"><span data-stu-id="367a1-134">Create a Package</span></span>](../create-packages/creating-a-package.md)
- [<span data-ttu-id="367a1-135">Paket Yayımlama</span><span class="sxs-lookup"><span data-stu-id="367a1-135">Publish a Package</span></span>](../create-packages/publish-a-package.md)
- [<span data-ttu-id="367a1-136">Ön yayın paketleri</span><span class="sxs-lookup"><span data-stu-id="367a1-136">Pre-release Packages</span></span>](../create-packages/Prerelease-Packages.md)
- [<span data-ttu-id="367a1-137">Birden çok hedef çerçeveyi desteği</span><span class="sxs-lookup"><span data-stu-id="367a1-137">Support multiple target frameworks</span></span>](../create-packages/supporting-multiple-target-frameworks.md)
- [<span data-ttu-id="367a1-138">Paket sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="367a1-138">Package versioning</span></span>](../reference/package-versioning.md)
- [<span data-ttu-id="367a1-139">Yerelleştirilmiş paketler oluşturma</span><span class="sxs-lookup"><span data-stu-id="367a1-139">Creating localized packages</span></span>](../create-packages/creating-localized-packages.md)
- [<span data-ttu-id="367a1-140">İmzalama paketleri</span><span class="sxs-lookup"><span data-stu-id="367a1-140">Signing packages</span></span>](../create-packages/Sign-a-package.md)