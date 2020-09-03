---
title: Частные галереи | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 895fbef5459de75c7ccdc6a090fc30ec27a030f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444925"
---
# <a name="private-galleries"></a>Private Galleries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете совместно использовать элементы управления, шаблоны и средства, которые вы разрабатываете, отправляя их в *частную коллекцию* в интрасети организации следующим образом:  
  
- Создайте канал Atom (RSS) в соответствующим образом настроенном центральном расположении (репозитории) в интрасети. Дополнительные сведения см. [в разделе инструкции. Создание веб-канала Atom для частной коллекции](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
- Распространите pkgdef-файл, описывающий частную коллекцию. Рекомендуется использовать эту конфигурацию для администраторов, желающих одновременно подключать частную коллекцию к нескольким компьютерам.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Добавление частной коллекции в расширения и обновления в Visual Studio  
 Если доступна частная коллекция, ее можно добавить в **расширения и обновления** в Visual Studio.  
  
 ![Диалоговое окно "Добавить" диспетчера расширений](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Добавление частной коллекции к расширениям и обновлениям  
  
1. В строке меню выберите **Сервис**, **Параметры**.  
  
2. В узле **Среда** выберите **расширения и обновления**.  
  
3. Выберите кнопку **Добавить**.  
  
4. В поле **имя** введите имя для частной коллекции, например `My Gallery` .  
  
5. В поле **URL-адрес** введите URL-адрес веб-канала Atom или сайта SharePoint, на котором размещается частная коллекция.  
  
    1. Если узел является каналом Atom, который подключается к частной коллекции, URL-адрес будет выглядеть следующим образом: `http://www.mywebsite/mygallery/atom.xml` .  Этот URL-адрес может ссылаться на файл или сетевой путь.  
  
    2. Если узел является сайтом SharePoint, URL-адрес будет выглядеть следующим образом: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .  
  
### <a name="managing-private-galleries"></a>Управление частными галереями  
 Администратор может сделать закрытую галерею доступной для нескольких компьютеров одновременно, изменив системный реестр на каждом компьютере. Для этого создайте файл pkgdef, описывающий новые разделы реестра и их значения.  Этот файл имеет следующий формат.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Дополнительные сведения см. [в разделе руководство. Управление частной коллекцией с помощью параметров реестра](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Установка расширений из частной коллекции  
 Вы можете искать и устанавливать расширения Visual Studio из частной коллекции в оснастке " **расширения и обновления**". В следующих шагах используется частная коллекция с именем `My Gallery` .  
  
 ![Диспетчер расширений устанавливает закрытую галерею](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Поиск и Установка расширений из частной коллекции  
  
1. В строке меню выберите **Сервис**, **Расширения и обновления**.  
  
2. В левой области выберите расширения в **Интернете**, а затем щелкните **Моя коллекция**.  
  
3. В области справа выберите расширение, а затем нажмите кнопку **скачать** .  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Обновление расширений из частной коллекции  
 После публикации новых версий расширений Visual Studio в частной коллекции можно обновить установленные расширения. В следующих шагах используется частная коллекция с именем `My Repository` .  
  
 ![Обновление закрытой галереи диспетчера расширений](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Обновление установленного расширения из частной коллекции  
  
1. В строке меню выберите **Сервис**, **Расширения и обновления**.  
  
2. В левой области выберите **обновления**, а затем щелкните **Мой репозиторий**.  
  
3. В области справа выберите расширение, а затем нажмите кнопку **Обновить** .  
  
## <a name="see-also"></a>См. также:  
 [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
