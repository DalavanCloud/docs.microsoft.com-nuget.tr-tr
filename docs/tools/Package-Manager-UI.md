---
title: NuGet Paket Yöneticisi kullanıcı Arabirimi başvurusu
description: NuGet paketleri ile çalışmak için Visual Studio'da NuGet Paket Yöneticisi kullanıcı Arabirimi kullanma için yönergeler.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 12/08/2017
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.nuget_package_manager
- vs.toolsoptionspages.nuget_package_manager.general
- vs.toolsoptionspages.nuget_package_manager.package_sources
- vs.nuget.packagemanager.ui
ms.openlocfilehash: 1d8cb8186b9cedb29918d48539bdf45b130030c0
ms.sourcegitcommit: 00c4c809c69c16fcf4d81012eb53ea22f0691d0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="nuget-package-manager-ui"></a><span data-ttu-id="43063-103">NuGet Package Manager UI</span><span class="sxs-lookup"><span data-stu-id="43063-103">NuGet Package Manager UI</span></span>

<span data-ttu-id="43063-104">Windows Visual Studio'da NuGet Paket Yöneticisi kullanıcı Arabirimi, kolayca yüklemek, kaldırmak ve projeler ve çözümler, NuGet paketlerini güncelleştirmeyi olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="43063-104">The NuGet Package Manager UI in Visual Studio on Windows allows you to easily install, uninstall, and update NuGet packages in projects and solutions.</span></span> <span data-ttu-id="43063-105">Visual Studio'da Mac için deneyimi için bkz: [dahil olmak üzere bir NuGet paketini projenize](/visualstudio/mac/nuget-walkthrough).</span><span class="sxs-lookup"><span data-stu-id="43063-105">For the experience in Visual Studio for Mac, see [Including a NuGet package in your project](/visualstudio/mac/nuget-walkthrough).</span></span> <span data-ttu-id="43063-106">Paket Yöneticisi kullanıcı Arabirimi ile Visual Studio Code dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="43063-106">The Package Manager UI is not included with Visual Studio Code.</span></span>

<span data-ttu-id="43063-107">Bu konuda:</span><span class="sxs-lookup"><span data-stu-id="43063-107">In this topic:</span></span>

- [<span data-ttu-id="43063-108">Bulma ve bir paket (Gözat sekmesi) yükleme</span><span class="sxs-lookup"><span data-stu-id="43063-108">Finding and installing a package (Browse tab)</span></span>](#finding-and-installing-a-package)
- [<span data-ttu-id="43063-109">Bir paket (yüklü sekmesi) kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="43063-109">Uninstalling a package (Installed tab)</span></span>](#uninstalling-a-package)
- <span data-ttu-id="43063-110">[Bir paket (yüklü ve güncelleştirmeleri sekmeleri) güncelleştirme](#updating-a-package) (içeren ["Bir SDK'sı tarafından başvurulan dolaylı olarak" veya "AutoReferenced" iletisi](#implicit_reference))</span><span class="sxs-lookup"><span data-stu-id="43063-110">[Updating a package (Installed and Updates tabs)](#updating-a-package) (includes the ["Implicitly referenced by an SDK" or "AutoReferenced" message](#implicit_reference))</span></span>
- <span data-ttu-id="43063-111">[Çözüm paketlerini yönetme](#managing-packages-for-the-solution) (aynı anda birden çok proje ile çalışma).</span><span class="sxs-lookup"><span data-stu-id="43063-111">[Managing packages for the solution](#managing-packages-for-the-solution) (working with multiple projects at the same time).</span></span>
- [<span data-ttu-id="43063-112">Paket kaynaklarını</span><span class="sxs-lookup"><span data-stu-id="43063-112">Package sources</span></span>](#package-sources)
- [<span data-ttu-id="43063-113">Paket Yöneticisi seçeneklerini denetleme</span><span class="sxs-lookup"><span data-stu-id="43063-113">Package manager Options control</span></span>](#package-manager-options-control)

> [!Note]
> <span data-ttu-id="43063-114">Visual Studio 2015'te NuGet Paket Yöneticisi kayıpsa denetleyin **Araçlar > Uzantılar ve güncelleştirmeler...**  arayın ve *NuGet Paket Yöneticisi* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="43063-114">If you're missing the NuGet Package Manager in Visual Studio 2015, check **Tools > Extensions and Updates...** and search for the *NuGet Package Manager* extension.</span></span> <span data-ttu-id="43063-115">Visual Studio Uzantıları yükleyici yapamıyorsanız doğrudan uzantısını [ https://dist.nuget.org/index.html ](https://dist.nuget.org/index.html).</span><span class="sxs-lookup"><span data-stu-id="43063-115">If you're unable to use the extensions installer in Visual Studio, download the extension directly from [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html).</span></span>
>
> <span data-ttu-id="43063-116">Visual Studio 2017 içinde NuGet ve NuGet Paket Yöneticisi otomatik olarak tüm yüklenir. NET ilgili iş yükleri.</span><span class="sxs-lookup"><span data-stu-id="43063-116">In Visual Studio 2017, NuGet and the NuGet Package Manager are automatically installed with any .NET-related workloads.</span></span> <span data-ttu-id="43063-117">Tek tek seçerek yüklemek **bileşenleri tek tek > kod Araçlar > NuGet Paket Yöneticisi** Visual Studio 2017 yükleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="43063-117">Install it individually by selecting the **Individual components > Code tools > NuGet package manager** option in the Visual Studio 2017 installer.</span></span>

## <a name="finding-and-installing-a-package"></a><span data-ttu-id="43063-118">Bulma ve bir paket yükleme</span><span class="sxs-lookup"><span data-stu-id="43063-118">Finding and installing a package</span></span>

1. <span data-ttu-id="43063-119">İçinde **Çözüm Gezgini**, sağ **başvuruları** veya bir proje ve **NuGet paketlerini Yönet...** .</span><span class="sxs-lookup"><span data-stu-id="43063-119">In **Solution Explorer**, right-click either **References**  or a project and select **Manage NuGet Packages...**.</span></span>

    ![NuGet paketlerini menü seçeneği yönetme](media/ManagePackagesUICommand.png)

1. <span data-ttu-id="43063-121">**Gözat** sekmesi seçili kaynağından popülerliği tarafından paketleri görüntüler (bkz [paketini kaynakları](#package-sources)).</span><span class="sxs-lookup"><span data-stu-id="43063-121">The **Browse** tab displays packages by popularity from the currently selected source (see [package sources](#package-sources)).</span></span> <span data-ttu-id="43063-122">Sol üst arama kutusunu kullanarak belirli bir paket için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="43063-122">Search for a specific package using the search box on the upper left.</span></span> <span data-ttu-id="43063-123">Ayrıca sağlar, bilgilerini görüntülemek için listeden bir paket seçin **yükleme** bir sürüm seçimi açılan birlikte düğmesi.</span><span class="sxs-lookup"><span data-stu-id="43063-123">Select a package from the list to display its information, which also enables the **Install** button along with a version-selection drop-down.</span></span>

    ![NuGet paket iletişim Gözat sekmesini yönetme](media/Search.png)

1. <span data-ttu-id="43063-125">Açılan listeden istediğiniz sürümü seçin ve Seç **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="43063-125">Select the desired version from the drop-down and select **Install**.</span></span> <span data-ttu-id="43063-126">Visual Studio Paketi ve bağımlılıklarını projeye yükler.</span><span class="sxs-lookup"><span data-stu-id="43063-126">Visual Studio installs the package and its dependencies into the project.</span></span> <span data-ttu-id="43063-127">Lisans koşullarını kabul etmeniz istenebilir.</span><span class="sxs-lookup"><span data-stu-id="43063-127">You may be asked to accept license terms.</span></span> <span data-ttu-id="43063-128">Yükleme tamamlandığında, eklenen paketler görünür **yüklü** sekmesi. Paketleri de listelenir **başvuruları** projedeki başvurmak olduğunu gösteren Çözüm Gezgini düğümünün `using` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="43063-128">When installation is complete, the added packages appear on the **Installed** tab. Packages are also listed in the **References** node of Solution Explorer, indicating that you can refer to them in the project with `using` statements.</span></span>

    ![Çözüm Gezgini'nde başvuruların](media/References.png)

> [!Tip]
> <span data-ttu-id="43063-130">Yayın öncesi sürümler dahil ve yayın öncesi sürümler açılan sürümünde kullanılabilir hale getirmek seçin **dahil et** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="43063-130">To include prerelease versions in the search, and to make prerelease versions available in the version drop-down, select the **Include prerelease** option.</span></span>

## <a name="uninstalling-a-package"></a><span data-ttu-id="43063-131">Bir paketi kaldırma</span><span class="sxs-lookup"><span data-stu-id="43063-131">Uninstalling a package</span></span>

1. <span data-ttu-id="43063-132">İçinde **Çözüm Gezgini**, sağ **başvuruları** veya istenen proje ' nı seçip **NuGet paketlerini Yönet...** .</span><span class="sxs-lookup"><span data-stu-id="43063-132">In **Solution Explorer**, right-click either **References** or the desired project, and select **Manage NuGet Packages...**.</span></span>
1. <span data-ttu-id="43063-133">Seçin **yüklü** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="43063-133">Select the **Installed** tab.</span></span>
1. <span data-ttu-id="43063-134">(Gerekirse listesini filtrelemek için arama'yı kullanarak) kaldırmak için paketini seçin ve Seç **kaldırma**.</span><span class="sxs-lookup"><span data-stu-id="43063-134">Select the package to uninstall (using search to filter the list if necessary) and select **Uninstall**.</span></span>

    ![Bir paketi kaldırma](media/UninstallPackage.png)

1. <span data-ttu-id="43063-136">Unutmayın **INCLUDE yayın öncesi** ve **paket kaynağı** denetimleri etkisiz paketleri kaldırırken.</span><span class="sxs-lookup"><span data-stu-id="43063-136">Note that the **Include prerelease** and **Package source** controls have no effect when uninstalling packages.</span></span>

## <a name="updating-a-package"></a><span data-ttu-id="43063-137">Paket güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="43063-137">Updating a package</span></span>

1. <span data-ttu-id="43063-138">İçinde **Çözüm Gezgini**, sağ **başvuruları** veya istenen proje ' nı seçip **NuGet paketlerini Yönet...** . (Web sitesi projelerinde sağ **Bin** klasörü.)</span><span class="sxs-lookup"><span data-stu-id="43063-138">In **Solution Explorer**, right-click either **References** or the desired project, and select **Manage NuGet Packages...**. (In web site projects, right-click the **Bin** folder.)</span></span>
1. <span data-ttu-id="43063-139">Seçin **güncelleştirmeleri** sekmesi seçili paketi kaynaklardan kullanılabilir güncelleştirmeleri sahip paketleri görmek için.</span><span class="sxs-lookup"><span data-stu-id="43063-139">Select the **Updates** tab to see packages that have available updates from the selected package sources.</span></span> <span data-ttu-id="43063-140">Seçin **dahil et** ön sürüm paketlerini güncelleştirme listeye dahil edilecek.</span><span class="sxs-lookup"><span data-stu-id="43063-140">Select **Include prerelease** to include prerelease packages in the update list.</span></span>
1. <span data-ttu-id="43063-141">Güncelleştirme, sağda açılan istediğiniz sürümü seçin ve seçmek için paketi seçin **güncelleştirme**.</span><span class="sxs-lookup"><span data-stu-id="43063-141">Select the package to update, select the desired version from the drop-down on the right, and select **Update**.</span></span>

    ![Paket güncelleştirme](media/UpdatePackages.png)

1. <a name="implicit_reference"></a><span data-ttu-id="43063-143">Bazı paketler için **güncelleştirme** düğmesi devre dışıdır ve bunu "örtük olarak bir SDK'sı tarafından başvurulduğundan" bildiren bir ileti görüntülenir (veya "AutoReferenced").</span><span class="sxs-lookup"><span data-stu-id="43063-143">For some packages, the **Update** button is disabled and a message appears saying that it's "Implicitly referenced by an SDK" (or "AutoReferenced").</span></span> <span data-ttu-id="43063-144">İleti Microsoft.NETCore.App veya Microsoft.NETStandard.Library, gibi paket daha büyük bir çerçeve veya SDK parçasıdır ve bağımsız olarak güncellenmemelidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="43063-144">The message indicates that the package, such as Microsoft.NETCore.App or Microsoft.NETStandard.Library, is part of a larger framework or SDK and should not be updated independently.</span></span> <span data-ttu-id="43063-145">(Gibi paketlerin dahili olarak işaretlenir `<IsImplicitlyDefined>True</IsImplicitlyDefined>`.) Güncelleştirme Paketi için paket adını içeren SDK'dan çıkarımını yapma ait olduğu, SDK güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="43063-145">(Such packages are internally marked with `<IsImplicitlyDefined>True</IsImplicitlyDefined>`.) To update the package, update the SDK to which it belongs, inferring the containing SDK from the package name.</span></span> <span data-ttu-id="43063-146">Örneğin, .NET Core SDK parçası paketidir Microsoft.NETCore.App gibi bu nedenle, .NET Core SDK yükleme güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="43063-146">For example, a package like Microsoft.NETCore.App is part of the .NET Core SDK, therefore you need to update your  .NET Core SDK installation.</span></span>

    ![Örnek paket başvuruları veya AutoReferenced dolaylı olarak işaretli](media/PackageManagerUIAutoReferenced.png)

1. <span data-ttu-id="43063-148">Birden çok paket yeni sürümlerine güncelleştirmek için bunları seçin ve liste içinde seçin **güncelleştirme** düğmesi listesinin üstünde.</span><span class="sxs-lookup"><span data-stu-id="43063-148">To update multiple packages to their newest versions, select  them in the list and select the **Update** button above the list.</span></span>
1. <span data-ttu-id="43063-149">Ayrıca tek bir paketi güncelleştirebilirsiniz **yüklü** sekmesi. Bu durumda, bir sürüm Seçici Paket ayrıntılarını içerir (tabi **INCLUDE yayın öncesi** seçeneği) ve bir **güncelleştirme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="43063-149">You can also update an individual package from the **Installed** tab. In this case, the details for the package include a version selector (subject to the **Include prerelease** option) and an **Update** button.</span></span>

## <a name="managing-packages-for-the-solution"></a><span data-ttu-id="43063-150">Çözüm paketlerini yönetme</span><span class="sxs-lookup"><span data-stu-id="43063-150">Managing packages for the solution</span></span>

<span data-ttu-id="43063-151">Çözüm paketlerini yönetme, aynı anda birden çok projelerle çalışmak için kullanışlı bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="43063-151">Managing packages for a solution is a convenient means to work with multiple projects simultaneously.</span></span>

1. <span data-ttu-id="43063-152">Seçin **Araçlar > NuGet Paket Yöneticisi > çözüm için NuGet paketlerini Yönet...**  menü komutunu veya çözüme sağ tıklayın ve seçin **NuGet paketlerini Yönet...** :</span><span class="sxs-lookup"><span data-stu-id="43063-152">Select the **Tools > NuGet Package Manager > Manage NuGet Packages for Solution...** menu command, or right-click the solution and select **Manage NuGet Packages...**:</span></span>

    ![Çözüm için NuGet paketlerini Yönet](media/ManagePackagesSolutionUICommand.png)

1. <span data-ttu-id="43063-154">Çözüm için paketlerini yönetirken, işlemleri tarafından etkilenen projeleri seçin kullanıcı Arabirimi sağlar:</span><span class="sxs-lookup"><span data-stu-id="43063-154">When managing packages for the solution, the UI lets you select the projects that are affected by the operations:</span></span>

    ![Çözüm için paketlerini yönetirken proje Seçici](media/SolutionPackagesUI.png)

### <a name="consolidate-tab"></a><span data-ttu-id="43063-156">Sekme birleştirin</span><span class="sxs-lookup"><span data-stu-id="43063-156">Consolidate tab</span></span>

<span data-ttu-id="43063-157">Geliştiriciler genellikle aynı çözümde farklı projeler arasında aynı NuGet paketi farklı sürümlerini kullanan hatalı bir uygulama düşünün.</span><span class="sxs-lookup"><span data-stu-id="43063-157">Developers typically consider it bad practice to use different versions of the same NuGet package across different projects in the same solution.</span></span> <span data-ttu-id="43063-158">Çözüm paketlerini yönetmek seçtiğinizde, Paket Yöneticisi kullanıcı Arabirimi sağlayan bir **Birleştir** üzerinde kolayca görebileceğiniz farklı sürüm numaralarını paketlerle çözümdeki farklı projeler tarafından kullanıldığı sekmesi:</span><span class="sxs-lookup"><span data-stu-id="43063-158">When you choose to manage packages for a solution, the Package Manager UI provides a **Consolidate** tab on which you can easily see where packages with distinct version numbers are used by different projects in the solution:</span></span>

![Paket Yöneticisi kullanıcı Arabirimi birleştirmek sekmesi](media/ConsolidateTab.png)

<span data-ttu-id="43063-160">Bu örnekte, ConsoleApp1 EntityFramework 6.1.0 kullanıyor ancak ClassLibrary1 projesindeki EntityFramework 6.2.0, kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="43063-160">In this example, the ClassLibrary1 project is using EntityFramework 6.2.0, whereas ConsoleApp1 is using EntityFramework 6.1.0.</span></span> <span data-ttu-id="43063-161">Paket sürümlerinin birleştirmek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="43063-161">To consolidate package versions, do the following:</span></span>

- <span data-ttu-id="43063-162">Proje listesinde güncelleştirmek için projeleri seçin.</span><span class="sxs-lookup"><span data-stu-id="43063-162">Select the projects to update in the project list.</span></span>
- <span data-ttu-id="43063-163">Bu tüm projelerde kullanmak için sürüm seçin **sürüm** EntityFramework 6.2.0 gibi denetim.</span><span class="sxs-lookup"><span data-stu-id="43063-163">Select the version to use in all those projects in the **Version** control, such as EntityFramework 6.2.0.</span></span>
- <span data-ttu-id="43063-164">Seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="43063-164">Select the **Install** button.</span></span>

<span data-ttu-id="43063-165">Paket Yöneticisi daha sonra paket artık görünür üzerinde tüm seçili projelerine seçili Paket sürümü yükler **Birleştir** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="43063-165">The Package Manager installs the selected package version into all selected projects, after which the package no longer appears on the **Consolidate** tab.</span></span>

## <a name="package-sources"></a><span data-ttu-id="43063-166">Paket kaynaklarını</span><span class="sxs-lookup"><span data-stu-id="43063-166">Package sources</span></span>

<span data-ttu-id="43063-167">Visual Studio paketleri aldığı kaynağını değiştirmek için bir kaynak seçici seçin:</span><span class="sxs-lookup"><span data-stu-id="43063-167">To change the source from which Visual Studio obtains packages, select one from the source selector:</span></span>

![Paket kaynak seçicide Paket Yöneticisi kullanıcı Arabirimi](media/PackageSourceDropDown.png)

<span data-ttu-id="43063-169">Paket kaynaklarını yönetmek için:</span><span class="sxs-lookup"><span data-stu-id="43063-169">To manage package sources:</span></span>

1. <span data-ttu-id="43063-170">Seçin **ayarları** Paket Yöneticisi kullanıcı Arabirimi simgesine aşağıda açıklanan veya kullanmak **Araçlar > Seçenekler** komut ve kaydırma **NuGet Paket Yöneticisi**:</span><span class="sxs-lookup"><span data-stu-id="43063-170">Select the **Settings** icon in the Package Manager UI outlined below or use the **Tools > Options** command and scroll to **NuGet Package Manager**:</span></span>

    ![Paket Yöneticisi kullanıcı Arabirimi ayarları simgesi](media/PackageSourceSettings.png)

1. <span data-ttu-id="43063-172">Seçin **paket kaynaklarını** düğümü:</span><span class="sxs-lookup"><span data-stu-id="43063-172">Select the **Package Sources** node:</span></span>

    ![Paket kaynağı seçenekleri](media/options.png)

1. <span data-ttu-id="43063-174">Bir kaynak eklemek için seçin **+**, ad düzenleme, URL veya yol girin **kaynak** denetlemek ve seçin **güncelleştirme**.</span><span class="sxs-lookup"><span data-stu-id="43063-174">To add a source, select **+**, edit the name, enter the URL or path in the **Source** control, and select  **Update**.</span></span> <span data-ttu-id="43063-175">Kaynak Seçici açılan artık görünür.</span><span class="sxs-lookup"><span data-stu-id="43063-175">The source now appears in the selector drop-down.</span></span>
1. <span data-ttu-id="43063-176">Paket kaynağı değiştirmek için seçmek, içinde düzenlemeler **adı** ve **kaynak** kutuları ' nı seçip **güncelleştirme**.</span><span class="sxs-lookup"><span data-stu-id="43063-176">To change a package source, select it, make edits in the **Name** and **Source** boxes, and select **Update**.</span></span>
1. <span data-ttu-id="43063-177">Paket kaynağı devre dışı bırakmak için listeden adı solundaki kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="43063-177">To disable a package source, clear the box to the left of the name in the list.</span></span>
1. <span data-ttu-id="43063-178">Paket kaynağı kaldırmak için onu seçin ve ardından **X** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="43063-178">To remove a package source, select it and then select the **X** button.</span></span>
1. <span data-ttu-id="43063-179">Yukarı ve aşağı ok düğmelerini paket kaynaklarını öncelik sırasını değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="43063-179">Use the up and down arrow buttons to change the priority order of the package sources.</span></span> <span data-ttu-id="43063-180">Visual Studio projesi için paketleri geri yüklenirken bu kaynakları öncelik sırasına göre arar.</span><span class="sxs-lookup"><span data-stu-id="43063-180">Visual Studio searches these sources in the priority order when restoring packages for a project.</span></span> <span data-ttu-id="43063-181">Daha fazla bilgi için bkz: [paket geri yüklemesi](../consume-packages/package-restore.md).</span><span class="sxs-lookup"><span data-stu-id="43063-181">For more information, see [Package restore](../consume-packages/package-restore.md).</span></span>

> [!Tip]
> <span data-ttu-id="43063-182">Paket kaynağı sildikten sonra görünürse, bir bilgisayar düzeyinde veya kullanıcı düzeyi listelenmeyebilir `NuGet.Config` dosyaları.</span><span class="sxs-lookup"><span data-stu-id="43063-182">If a package source reappears after deleting it, it may be listed in a computer-level or user-level `NuGet.Config` files.</span></span> <span data-ttu-id="43063-183">Bkz: [NuGet yapılandırma davranışı](../consume-packages/configuring-nuget-behavior.md) bu dosyaları için konum ardından dosyaları el ile düzenleme veya kullanarak kaynak kaldırın [nuget kaynakları komutu](../tools/nuget-exe-CLI-reference.md).</span><span class="sxs-lookup"><span data-stu-id="43063-183">See [Configuring NuGet behavior](../consume-packages/configuring-nuget-behavior.md) for the location of these files, then remove the source by editing the files manually or using the [nuget sources command](../tools/nuget-exe-CLI-reference.md).</span></span>

## <a name="package-manager-options-control"></a><span data-ttu-id="43063-184">Paket Yöneticisi seçeneklerini denetleme</span><span class="sxs-lookup"><span data-stu-id="43063-184">Package manager Options control</span></span>

<span data-ttu-id="43063-185">Bir paket seçildiğinde, küçük bir paket Yöneticisi kullanıcı Arabirimi görüntüler Genişletilebilir **seçenekleri** (her ikisi de daraltılmış ve genişletilmiş aşağıda gösterilen) sürüm Seçici altına denetimi.</span><span class="sxs-lookup"><span data-stu-id="43063-185">When a package is selected, the Package Manager UI displays a small, expandable **Options** control below the version selector (shown here both collapsed and expanded).</span></span> <span data-ttu-id="43063-186">Bazı proje türleri, yalnızca unutmayın **Göster önizleme penceresi** seçeneği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="43063-186">Note that for some project types, only the **Show preview window** option is provided.</span></span>

![Paket Yöneticisi seçenekleri](media/PackageManagerUIOptions.png)

<span data-ttu-id="43063-188">Aşağıdaki bölümlerde bu seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43063-188">The following sections explain these options.</span></span>

### <a name="show-preview-window"></a><span data-ttu-id="43063-189">Önizleme penceresi Göster</span><span class="sxs-lookup"><span data-stu-id="43063-189">Show preview window</span></span>

<span data-ttu-id="43063-190">Paket yüklenmeden önce kalıcı pencere seçildiğinde, seçilen Paket bağımlılıklarını görüntüler:</span><span class="sxs-lookup"><span data-stu-id="43063-190">When selected, a modal window displays which the dependencies of a chosen package before the package is installed:</span></span>

![Örnek Önizleme iletişim kutusu](media/InstallPreviewDialog.png)

<!-- This is here because the link in the UI needs this anchor. See https://github.com/NuGet/NuGet.Client/blob/dev/src/NuGet.Clients/PackageManagement.UI/Xamls/OptionsControl.xaml -->
<a name="install-options"></a>

### <a name="install-and-update-options"></a><span data-ttu-id="43063-192">Yükleme ve güncelleme seçenekleri</span><span class="sxs-lookup"><span data-stu-id="43063-192">Install and Update Options</span></span>

<span data-ttu-id="43063-193">(Mevcut değil tüm türleri proje için.)</span><span class="sxs-lookup"><span data-stu-id="43063-193">(Not available for all project types.)</span></span>

<span data-ttu-id="43063-194">**Bağımlılık davranışı** NuGet yüklemek için bağımlı paketler hangi sürümlerinin nasıl karar yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="43063-194">**Dependency behavior** configures how NuGet decides which versions of dependent packages to install:</span></span>

- <span data-ttu-id="43063-195">*Bağımlılıklar Yoksay* tüm bağımlılıkları genellikle yüklenen paket kıran yükleme atlar.</span><span class="sxs-lookup"><span data-stu-id="43063-195">*Ignore dependencies* skips installing any dependencies, which typically breaks the package being installed.</span></span>
- <span data-ttu-id="43063-196">*En düşük* [Varsayılan] birincil seçilen paketi gereksinimlerini karşılayan en az sürüm numarasına sahip bağımlılık yükler.</span><span class="sxs-lookup"><span data-stu-id="43063-196">*Lowest* [Default] installs the dependency with the minimal version number that meets the requirements of the primary chosen package.</span></span>
- <span data-ttu-id="43063-197">*En yüksek düzeltme eki* aynı birincil ve ikincil sürüm numaralarını, ancak en yüksek düzeltme numarası ile yeni sürümü yükler.</span><span class="sxs-lookup"><span data-stu-id="43063-197">*Highest Patch* installs the version with the same major and minor version numbers, but the highest patch number.</span></span> <span data-ttu-id="43063-198">Sürüm 1.2.2 belirtilmişse, örneğin, ardından 1.2 ile başlayan yüksek sürümü yüklenir</span><span class="sxs-lookup"><span data-stu-id="43063-198">For example, if version 1.2.2 is specified then the highest version that starts with 1.2 will be installed</span></span>
- <span data-ttu-id="43063-199">*En yüksek ikincil* aynı büyük sürüm numarasına ancak en yüksek ikincil numarası ve düzeltme numarası ile yeni sürümü yükler.</span><span class="sxs-lookup"><span data-stu-id="43063-199">*Highest Minor* installs the version with the same major version number but the highest minor number and patch number.</span></span> <span data-ttu-id="43063-200">Sürüm 1.2.2 belirtilirse, 1 ile başlayan en yüksek sürüm yüklenir</span><span class="sxs-lookup"><span data-stu-id="43063-200">If version 1.2.2 is specified, then the highest version that starts with 1 will be installed</span></span>
- <span data-ttu-id="43063-201">*En yüksek* paketi en yüksek kullanılabilir sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="43063-201">*Highest* installs the highest available version of the package.</span></span>

<span data-ttu-id="43063-202">**Dosya çakışma eylem** NuGet proje veya yerel makine zaten paketleri nasıl yöneteceğini belirtir:</span><span class="sxs-lookup"><span data-stu-id="43063-202">**File conflict action** specifies how NuGet should handle packages that already exist in the project or local machine:</span></span>

- <span data-ttu-id="43063-203">*Komut İstemi* tutun veya var olan paketler üzerine sormak için NuGet bildirir.</span><span class="sxs-lookup"><span data-stu-id="43063-203">*Prompt* instructs NuGet to ask whether to keep or overwrite existing packages.</span></span>
- <span data-ttu-id="43063-204">*Tüm Yoksay* herhangi bir varolan paket üzerine atlamak için NuGet bildirir.</span><span class="sxs-lookup"><span data-stu-id="43063-204">*Ignore All* instructs NuGet to skip overwriting any existing packages.</span></span>
- <span data-ttu-id="43063-205">*Tüm üzerine* herhangi bir varolan paket üzerine yazmak için NuGet bildirir.</span><span class="sxs-lookup"><span data-stu-id="43063-205">*Overwrite All* instructs NuGet to overwrite any existing packages.</span></span>

<!-- This is here because the link in the UI needs this anchor. See https://github.com/NuGet/NuGet.Client/blob/dev/src/NuGet.Clients/PackageManagement.UI/Xamls/OptionsControl.xaml -->
<a name="uninstall-options"></a>

### <a name="uninstall-options"></a><span data-ttu-id="43063-206">Kaldırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="43063-206">Uninstall Options</span></span>

<span data-ttu-id="43063-207">(Mevcut değil tüm türleri proje için.)</span><span class="sxs-lookup"><span data-stu-id="43063-207">(Not available for all project types.)</span></span>

<span data-ttu-id="43063-208">**Bağımlılıkları kaldırın**: Bunlar başka bir projede başvurulmayan seçili olduğunda, tüm bağımlı paketler kaldırır.</span><span class="sxs-lookup"><span data-stu-id="43063-208">**Remove dependencies**: when selected, removes any dependent packages if they're not referenced elsewhere in the project.</span></span>

<span data-ttu-id="43063-209">**Zorla kaldırın olsa bile bağımlılıklar üzerinde**: projede başvuruluyor olsa bile, seçili olduğunda, bir paketi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="43063-209">**Force uninstall even if there are dependencies on it**: when selected, uninstalls a package even if it's still being referenced in the project.</span></span> <span data-ttu-id="43063-210">Bu genellikle ile birlikte kullanılır **kaldırmak bağımlılıkları** ve her bir paketi kaldırmak için yüklü bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="43063-210">This is typically used in combination with **Remove dependencies** to remove a package and whatever dependencies it installed.</span></span> <span data-ttu-id="43063-211">Bu seçeneği kullanarak ancak projedeki bozuk başvurularda açabilir.</span><span class="sxs-lookup"><span data-stu-id="43063-211">Using this option may, however, lead to broken references in the project.</span></span> <span data-ttu-id="43063-212">Böyle durumlarda, gerekebilir [bu diğer paketleri yeniden](../consume-packages/reinstalling-and-updating-packages.md).</span><span class="sxs-lookup"><span data-stu-id="43063-212">In such cases, you may need to [reinstall those other packages](../consume-packages/reinstalling-and-updating-packages.md).</span></span>