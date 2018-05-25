---
title: NuGet Get-Package PowerShell başvurusu
description: Visual Studio'da NuGet Paket Yöneticisi konsolunda Get-Package PowerShell komut başvurusu.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 12/07/2017
ms.topic: reference
ms.openlocfilehash: c70e60b7391f19026e2dcd502d667fbe1da7e6e2
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="get-package-package-manager-console-in-visual-studio"></a><span data-ttu-id="00c25-103">Get-Package (Visual Studio'da Paket Yöneticisi Konsolu)</span><span class="sxs-lookup"><span data-stu-id="00c25-103">Get-Package (Package Manager Console in Visual Studio)</span></span>

<span data-ttu-id="00c25-104">*Bu konu içindeki komut açıklar [NuGet Paket Yöneticisi Konsolu](package-manager-console.md) Windows Visual Studio'da. Genel PowerShell Get-Package komutu için bkz: [PowerShell PackageManagement başvuru](/powershell/module/packagemanagement/?view=powershell-6).*</span><span class="sxs-lookup"><span data-stu-id="00c25-104">*This topic describes the command within the [NuGet Package Manager Console](package-manager-console.md) in Visual Studio on Windows. For the generic PowerShell Get-Package command, see the [PowerShell PackageManagement reference](/powershell/module/packagemanagement/?view=powershell-6).*</span></span>

<span data-ttu-id="00c25-105">Yerel depoda yüklü olan paketlerin listesini alır, - listavailable birlikte anahtarıyla birlikte kullanıldığında bir paket kaynağındaki paketleri listeler veya güncelleştirme anahtarıyla birlikte kullanıldığında kullanılabilir güncelleştirmeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="00c25-105">Retrieves the list of packages installed in the local repository, lists packages available from a package source when used with the -ListAvailable switch, or lists available updates when used with the -Update switch.</span></span>

## <a name="syntax"></a><span data-ttu-id="00c25-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00c25-106">Syntax</span></span>

```ps
Get-Package -Source <string> [-ListAvailable] [-Updates] [-ProjectName <string>]
    [-Filter <string>] [-First <int>] [-Skip <int>] [-AllVersions] [-IncludePrerelease]
    [-PageSize] [<CommonParameters>]
```

<span data-ttu-id="00c25-107">Hiçbir parametre `Get-Package` varsayılan projede yüklü olan paketlerin listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="00c25-107">With no parameters, `Get-Package` displays the list of packages installed in the default project.</span></span>

## <a name="parameters"></a><span data-ttu-id="00c25-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00c25-108">Parameters</span></span>

| <span data-ttu-id="00c25-109">Parametre</span><span class="sxs-lookup"><span data-stu-id="00c25-109">Parameter</span></span> | <span data-ttu-id="00c25-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00c25-110">Description</span></span> |
| --- | --- |
| <span data-ttu-id="00c25-111">Kaynak</span><span class="sxs-lookup"><span data-stu-id="00c25-111">Source</span></span> | <span data-ttu-id="00c25-112">Paket URL'si veya klasör yolu.</span><span class="sxs-lookup"><span data-stu-id="00c25-112">The URL or folder path for the package .</span></span> <span data-ttu-id="00c25-113">Yerel klasör yolları mutlak veya göreli geçerli klasörde olabilir.</span><span class="sxs-lookup"><span data-stu-id="00c25-113">Local folder paths can be absolute, or relative to the current folder.</span></span> <span data-ttu-id="00c25-114">Atlanırsa, `Get-Package` şu anda seçili paket kaynağını arar.</span><span class="sxs-lookup"><span data-stu-id="00c25-114">If omitted, `Get-Package` searches the currently selected package source.</span></span> <span data-ttu-id="00c25-115">-Listavailable ile birlikte, nuget.org varsayılanlara kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="00c25-115">When used with -ListAvailable, defaults to nuget.org.</span></span> |
| <span data-ttu-id="00c25-116">Listavailable birlikte</span><span class="sxs-lookup"><span data-stu-id="00c25-116">ListAvailable</span></span> | <span data-ttu-id="00c25-117">Nuget.org için varsayılan değer olarak, bir paket kaynağındaki paketleri listeler. -PageSize ve/veya - ilk belirtilmediği sürece varsayılan 50 paketlerin gösterir.</span><span class="sxs-lookup"><span data-stu-id="00c25-117">Lists packages available from a package source, defaulting to nuget.org. Shows a default of 50 packages unless -PageSize and/or -First are specified.</span></span> |
| <span data-ttu-id="00c25-118">Güncelleştirmeler</span><span class="sxs-lookup"><span data-stu-id="00c25-118">Updates</span></span> | <span data-ttu-id="00c25-119">Paket kaynağındaki güncelleştirmeye sahip paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="00c25-119">Lists packages that have an update available from the package source.</span></span> |
| <span data-ttu-id="00c25-120">ProjectName</span><span class="sxs-lookup"><span data-stu-id="00c25-120">ProjectName</span></span> | <span data-ttu-id="00c25-121">Yüklü paketler alınacağı projesi.</span><span class="sxs-lookup"><span data-stu-id="00c25-121">The project from which to get installed packages.</span></span> <span data-ttu-id="00c25-122">Atlanırsa, çözümün tamamı için projeleri döndürür yüklü.</span><span class="sxs-lookup"><span data-stu-id="00c25-122">If omitted, returns installed projects for the entire solution.</span></span> |
| <span data-ttu-id="00c25-123">Filtrele</span><span class="sxs-lookup"><span data-stu-id="00c25-123">Filter</span></span> | <span data-ttu-id="00c25-124">Paket kimliği, açıklamada ve etiketlerde uygulayarak paket listesini daraltmak için kullanılan bir filtre dizesi.</span><span class="sxs-lookup"><span data-stu-id="00c25-124">A filter string used to narrow down the list of packages by applying it to the package ID, description, and tags.</span></span> |
| <span data-ttu-id="00c25-125">ilk</span><span class="sxs-lookup"><span data-stu-id="00c25-125">First</span></span> | <span data-ttu-id="00c25-126">Listenin başlangıcından döndürülecek paket sayısı.</span><span class="sxs-lookup"><span data-stu-id="00c25-126">The number of packages to return from the beginning of the list.</span></span> <span data-ttu-id="00c25-127">Belirtilmezse, 50'ye varsayılan olur.</span><span class="sxs-lookup"><span data-stu-id="00c25-127">If not specified, defaults to 50.</span></span> |
| <span data-ttu-id="00c25-128">Atla</span><span class="sxs-lookup"><span data-stu-id="00c25-128">Skip</span></span> | <span data-ttu-id="00c25-129">İlk atlar &lt;int&gt; görüntülenen listeden paketler.</span><span class="sxs-lookup"><span data-stu-id="00c25-129">Omits the first &lt;int&gt; packages from the displayed list.</span></span>  |
| <span data-ttu-id="00c25-130">AllVersions</span><span class="sxs-lookup"><span data-stu-id="00c25-130">AllVersions</span></span> | <span data-ttu-id="00c25-131">Yalnızca en son sürümü yerine her paketin tüm kullanılabilir sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="00c25-131">Displays all available versions of each package instead of only the latest version.</span></span> |
| <span data-ttu-id="00c25-132">IncludePrerelease</span><span class="sxs-lookup"><span data-stu-id="00c25-132">IncludePrerelease</span></span> | <span data-ttu-id="00c25-133">Sonuçlarda Önsürüm paketlerinin içerir.</span><span class="sxs-lookup"><span data-stu-id="00c25-133">Includes prerelease packages in the results.</span></span> |
| <span data-ttu-id="00c25-134">PageSize</span><span class="sxs-lookup"><span data-stu-id="00c25-134">PageSize</span></span> | <span data-ttu-id="00c25-135">*(3.0 +)*  -(Gerekli) listavailable ile birlikte, devam etmek için bir istem vermeden önce listelemek için paket sayısı kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="00c25-135">*(3.0+)* When used with -ListAvailable (required), the number of packages to list before giving a prompt to continue.</span></span> |

<span data-ttu-id="00c25-136">Hiçbiri bu parametre ardışık düzen giriş veya joker karakter kabul edin.</span><span class="sxs-lookup"><span data-stu-id="00c25-136">None of these parameters accept pipeline input or wildcard characters.</span></span>

## <a name="common-parameters"></a><span data-ttu-id="00c25-137">Ortak parametreleri</span><span class="sxs-lookup"><span data-stu-id="00c25-137">Common Parameters</span></span>

<span data-ttu-id="00c25-138">`Get-Package` Aşağıdaki destekleyen [ortak PowerShell parametrelerini](http://go.microsoft.com/fwlink/?LinkID=113216): hata ayıklama, hata eylemi, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, ayrıntı, WarningAction ve WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="00c25-138">`Get-Package` supports the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216): Debug, Error Action, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction, and WarningVariable.</span></span>

## <a name="examples"></a><span data-ttu-id="00c25-139">Örnekler</span><span class="sxs-lookup"><span data-stu-id="00c25-139">Examples</span></span>

```ps
# Lists the packages installed in the current solution
Get-Package

# Lists the packages installed in a project
Get-Package -ProjectName MyProject

# Lists packages available in the current package source
Get-Package -ListAvailable

# Lists 30 packages at a time from the current source, and prompts to continue if more are available
Get-Package -ListAvailable -PageSize 30

# Lists packages with the Ninject keyword in the current source, up to 50
Get-Package -ListAvailable -Filter Ninject

# List all versions of packages matching the filter "jquery"
Get-Package -ListAvailable -Filter jquery -AllVersions

# Lists packages installed in the solution that have available updates
Get-Package -Updates

# Lists packages installed in a specific project that have available updates
Get-Package -Updates -ProjectName MyProject
```