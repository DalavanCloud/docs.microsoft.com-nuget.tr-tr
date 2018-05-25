---
title: Nuget.org silme NuGet paketleri
description: Nuget.org unlisting paketlerinden ilkelerini; diğer ilkeler paketleri ihlal silme işlemi geri alınamaz dışında desteklenmez.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 01/18/2018
ms.topic: conceptual
ms.openlocfilehash: bea4f1589f184d38da27e5d82c3ce17a183fbdd1
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="deleting-packages"></a><span data-ttu-id="11c58-103">Paketlerin silinmesi</span><span class="sxs-lookup"><span data-stu-id="11c58-103">Deleting packages</span></span>

<span data-ttu-id="11c58-104">nuget.org paketleri kalıcı silinmesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="11c58-104">nuget.org does not support permanent deletion of packages.</span></span> <span data-ttu-id="11c58-105">Bunun yapılması her proje paket geri yükleme ile ilgili özellikle yapı iş akışlarıyla paketinin kullanılabilirliği bağlı olarak çalışmamasına neden.</span><span class="sxs-lookup"><span data-stu-id="11c58-105">Doing so would break every project depending on the availability of the package, especially with build workflows that involve package restore.</span></span>

<span data-ttu-id="11c58-106">nuget.org destekliyor mu *unlisting* web sitesinde paket Yönetimi sayfasındaki yapılabilir bir paket.</span><span class="sxs-lookup"><span data-stu-id="11c58-106">nuget.org does supports *unlisting* a package, which can be done in the package management page on the web site.</span></span> <span data-ttu-id="11c58-107">Listede bulunmayan paketleri nuget.org veya Visual Studio kullanıcı arabiriminde görünmez ve arama sonuçlarında görünmez.</span><span class="sxs-lookup"><span data-stu-id="11c58-107">Unlisted packages don't appear on nuget.org or in the Visual Studio UI, and do not appear in search results.</span></span> <span data-ttu-id="11c58-108">Listede bulunmayan paketleri, ancak hala indirilebilen ve paket geri yüklemesi destekleyen bir tam sürüm numarası kullanarak yüklü.</span><span class="sxs-lookup"><span data-stu-id="11c58-108">Unlisted packages, however, can still be downloaded and installed by using an exact version number, which supports package restore.</span></span> <span data-ttu-id="11c58-109">Ayrıca, listede bulunmayan paketleri hala aşağıdaki belirli senaryolarda bulunan:</span><span class="sxs-lookup"><span data-stu-id="11c58-109">In addition, unlisted packages may still be discovered in the following specific scenarios:</span></span>

- <span data-ttu-id="11c58-110">Paket geri yükleme kayan sürümlerini kullanan (örneğin, `1.0.0-*`), sürüm veya bağımlılık kısıtlamaları eşleşen en son kullanılabilir paket listelenmemiş paketidir.</span><span class="sxs-lookup"><span data-stu-id="11c58-110">Package restore using floating versions (for example, `1.0.0-*`), if the latest available package matching the version or dependency constraints is an unlisted package.</span></span>
- <span data-ttu-id="11c58-111">Çoğaltma Kataloğu yoluyla paketlerin (katalog de listelenmemiş paketlerini içeren gibi).</span><span class="sxs-lookup"><span data-stu-id="11c58-111">Replication of packages through the catalog (as the catalog also contains unlisted packages).</span></span>

## <a name="exceptions"></a><span data-ttu-id="11c58-112">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="11c58-112">Exceptions</span></span>

<span data-ttu-id="11c58-113">Telif hakkı ihlali ve zararlı içeriği gibi olağanüstü durumlarda, paketleri el ile NuGet ekibi tarafından silinebilir.</span><span class="sxs-lookup"><span data-stu-id="11c58-113">In exceptional situations such as copyright infringement and potentially harmful content, packages can be deleted manually by the NuGet team.</span></span> <span data-ttu-id="11c58-114">Bir destek isteği üzerinden göndermek [NuGet galerisinde](http://www.nuget.org) işlemini başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="11c58-114">Submit a support request through [NuGet Gallery](http://www.nuget.org) to start the process.</span></span>

## <a name="prohibited-use"></a><span data-ttu-id="11c58-115">Yasaklanan kullanın</span><span class="sxs-lookup"><span data-stu-id="11c58-115">Prohibited use</span></span>

<span data-ttu-id="11c58-116">Herhangi bir aşağıdaki ölçütleri karşılayan paketleri ortak NuGet galerisinde izin verilmiyor ve tartışma hemen kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="11c58-116">Packages that meet any of the following criteria are not allowed on the public NuGet gallery and will be immediately removed without discussion.</span></span> <span data-ttu-id="11c58-117">Sahipleri olacaktır, ancak paket, kaldırılmasını bildirilmesi.</span><span class="sxs-lookup"><span data-stu-id="11c58-117">Package owners will, however, be notified of the removal.</span></span>

- <span data-ttu-id="11c58-118">Kötü amaçlı yazılım, reklam veya casus yazılım her türlü içerir.</span><span class="sxs-lookup"><span data-stu-id="11c58-118">Contains malware, adware, or any kind of spyware.</span></span>
- <span data-ttu-id="11c58-119">Bir geliştiricinin iş istasyonu veya kuruluşu zarar vermek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="11c58-119">Are designed to harm a developer's workstation or their organization.</span></span>
- <span data-ttu-id="11c58-120">Telif Hakkı ihlal eden veya lisansları ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="11c58-120">Infringes copyrights or violates licenses.</span></span>
- <span data-ttu-id="11c58-121">Geçersiz içerik var.</span><span class="sxs-lookup"><span data-stu-id="11c58-121">Contains illegal content.</span></span>
- <span data-ttu-id="11c58-122">Kullanılmakta olan sıfır üretken içeriğe sahip paketleri de dahil olmak üzere paket tanımlayıcıları üzerinde squat için.</span><span class="sxs-lookup"><span data-stu-id="11c58-122">Are being used to squat on package identifiers, including packages that have zero productive content.</span></span> <span data-ttu-id="11c58-123">Paketleri kodu içermelidir veya sahipleri tanımlayıcı aktarmak üzere bir ürün olan başka birine bırakma gerekir.</span><span class="sxs-lookup"><span data-stu-id="11c58-123">Packages must contain code or the owners must concede the identifier to someone who actually has a product to ship.</span></span>
- <span data-ttu-id="11c58-124">Açıkça yapmak için tasarlanmış bir şeyler galeri yapmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="11c58-124">Attempt to make the gallery do something that it's not explicitly designed to do.</span></span>

<span data-ttu-id="11c58-125">İhlal bu öğelerden herhangi birini bir paket bulursanız tıklatın **rapor kötüye** bağlantı paketi ayrıntıları sayfasında ve bir rapor gönderin.</span><span class="sxs-lookup"><span data-stu-id="11c58-125">If you find a package that is in violation of any of these items, click the **Report Abuse** link on the package details page and submit a report.</span></span>

<span data-ttu-id="11c58-126">NuGet takım .NET Foundation ayırdığını herhangi bir zamanda Bu ölçütleri değiştirmek için sağ unutmayın.</span><span class="sxs-lookup"><span data-stu-id="11c58-126">Note that the NuGet team and the .NET Foundation reserves the right to change these criteria at any time.</span></span>