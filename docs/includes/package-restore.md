- **Paket Yöneticisi kullanıcı Arabirimi** (Visual Studio): Çözüm Gezgini'ndeki çözüme sağ tıklayın ve **NuGet paketleri geri**. Bir veya daha fazla tek tek paket olması durumunda düzgün yüklenmemiş hala (yani Çözüm Gezgini bir hata simgesi gösterir) ve sonra etkilenen paketleri kaldırmak ve bunları yeniden yüklemek için Paket Yöneticisi kullanıcı arabirimini kullanın. Bkz: [Reinstalling ve paketleri güncelleştiriliyor](../Consume-Packages/Reinstalling-and-Updating-Packages.md)

- **Komut satırı**: kullanmak [nuget restore](../tools/cli-ref-restore.md) komutu. Yalnızca çalışan `nuget restore` proje bağımlılıkları geri yüklemek klasör projede çalışır.