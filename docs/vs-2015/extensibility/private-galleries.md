---
title: Частные коллекции | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 820b0e992b79af28ca1b7f65f6a2f6221396da9e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192616"
---
# <a name="private-galleries"></a>Private Galleries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно совместно использовать элементы управления, шаблонов и средств, разработанных, публикуя их *частной коллекции* в интрасети для вашей организации, как показано ниже:  
  
-   Создание Atom RSS-канал в подходящим образом настроенный центральное расположение (репозитория), в интрасети. Дополнительные сведения см. в разделе [как: Создание веб-канал Atom для частной коллекции](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Распространение pkgdef-файл, описывающий частной коллекции. Рекомендуется, чтобы эта конфигурация для администраторов, которым требуется подключиться частной коллекции на нескольких компьютерах, в то же время.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Добавление закрытой коллекции расширений и обновлений в Visual Studio  
 Когда частной коллекции станет доступным, его можно добавить к **расширения и обновления** в Visual Studio.  
  
 ![Диалоговое окно добавления диспетчера расширений](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Чтобы добавить частной коллекции для расширения и обновления  
  
1.  В строке меню выберите **Сервис**, **Параметры**.  
  
2.  В **среды** выберите **расширения и обновления**.  
  
3.  Нажмите кнопку **Добавить** .  
  
4.  В **имя** введите имя частной коллекции, например, `My Gallery`.  
  
5.  В **URL-адрес** введите URL-адрес веб-канала Atom или сайта SharePoint, на котором размещается частной коллекции.  
  
    1.  Если узел работает веб-канала Atom, подключается к частной коллекции, URL-адрес будет выглядеть примерно так Вот: http://www.mywebsite/mygallery/atom.xml.  Этот URL-адрес может ссылаться на файл или сетевой путь.  
  
    2.  Если узел находится на сайте SharePoint, URL-адрес будет выглядеть примерно так Вот: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>Управление закрытые коллекции  
 Администратор может сделать частной коллекции доступны для нескольких компьютеров в то же время, изменив системного реестра на каждом компьютере. Для этого создайте pkgdef-файл, описывающий новые ключи реестра и их значения.  Формат этого файла выглядит следующим образом.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Дополнительные сведения см. в разделе [как: управление частной коллекции, с помощью параметров реестра](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Установка расширений из закрытой коллекции  
 Можно найти и установить расширения Visual Studio в частной коллекции в **расширения и обновления**. В следующих действиях используется частной коллекции с именем `My Gallery`.  
  
 ![Диспетчер расширений, установка закрытой коллекции](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Чтобы найти и установить расширения из частной коллекции  
  
1.  В строке меню выберите **Сервис**, **Расширения и обновления**.  
  
2.  В левой области выберите **сетевых расширений**, а затем выберите **Мои коллекции**.  
  
3.  В области справа выберите расширение, а затем выберите **загрузить** кнопки.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Обновление расширений из закрытой коллекции  
 Поскольку новые версии расширений Visual Studio будут опубликованы в частной коллекции, можно обновить расширения, которые вы установили. В следующих действиях используется частной коллекции с именем `My Repository`.  
  
 ![Расширение обновление закрытой галереи диспетчера](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Чтобы обновить установленное расширение из частной коллекции  
  
1.  В строке меню выберите **Сервис**, **Расширения и обновления**.  
  
2.  В левой области выберите **обновления**, а затем выберите **Мои репозитория**.  
  
3.  В области справа выберите расширение, а затем выберите **обновления** кнопки.  
  
## <a name="see-also"></a>См. также  
 [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)

