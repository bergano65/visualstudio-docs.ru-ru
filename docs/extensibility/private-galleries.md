---
title: "Закрытые галереи | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 8ce054bf6149f0224785f4c3cd9274e86dc09d04
ms.openlocfilehash: e4c49a19a9befad5d90b9526842786f49af0851b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/17/2017

---
# <a name="private-galleries"></a>Private Galleries
Можно совместно использовать элементы управления, шаблонов и средства, разрабатываемых путем внесения их в *частной коллекции* в интрасети для организации, как показано ниже:  
  
-   Создайте канал Atom (RSS) соответственно настроенного центральное расположение (репозитория) в интрасети. Дополнительные сведения см. в разделе [как: создать канал Atom для закрытой коллекции](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Распространите pkgdef-файл, который описывает частной коллекции. Эта конфигурация для администраторов, которым требуется подключиться частной коллекции на нескольких компьютерах, в то же время рекомендуется.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Добавление расширения и обновления в Visual Studio закрытой коллекции  
 Если доступен частной коллекции, его можно добавить к **расширения и обновления** в Visual Studio.  
  
 ![Диалоговое окно добавления диспетчера расширений](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Чтобы добавить частной коллекции расширения и обновления  
  
1.  В строке меню выберите **Сервис**, **Параметры**.  
  
2.  В **среды** выберите **расширения и обновления**.  
  
3.  Нажмите кнопку **Добавить** .  
  
4.  В **имя** введите имя частной коллекции, например, `My Gallery`.  
  
5.  В **URL-адрес** введите URL-адрес веб-канала Atom или сайта SharePoint, на котором размещается частной коллекции.  
  
    1.  Если узел является веб-канал Atom, при подключении к частной коллекции, URL-адрес будет выглядеть следующим образом, данный: http://www.mywebsite/mygallery/atom.xml.  Этот URL-адрес может ссылаться на файл или сетевой путь.  
  
    2.  Если узел является узлом SharePoint, этого класса, будет выглядеть URL-адрес: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>Управление закрытые галереи  
 Администратор может сделать частной коллекции доступны на несколько компьютеров одновременно путем изменения реестра системы на каждом компьютере. Для этого создайте pkgdef-файл, описывающий новые ключи реестра и их значения.  Этот файл имеет следующий формат.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Дополнительные сведения см. в разделе [как: управление частной коллекции, с помощью реестра параметров](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Установка расширений из закрытой коллекции  
 Можно найти и установить расширения Visual Studio из частной коллекции в **расширения и обновления**. В следующих действиях используется частной коллекции с именем `My Gallery`.  
  
 ![Диспетчер расширений Установка закрытой коллекции](../extensibility/media/em_.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Чтобы найти и установить расширения из частной коллекции  
  
1.  В строке меню выберите **Сервис**, **Расширения и обновления**.  
  
2.  В левой области выберите **расширений в Интернете**, а затем выберите **Мои коллекции**.  
  
3.  В области справа выберите расширение, а затем выберите **загрузки** кнопки.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Обновление расширений из закрытой коллекции  
 Поскольку новые версии расширений Visual Studio учитываются в частной коллекции, можно обновить расширения, которые вы установили. В следующих действиях используется частной коллекции с именем `My Repository`.  
  
 ![Расширение обновление закрытой галереи диспетчера](../extensibility/media/em_update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Чтобы обновить установленное расширение из частной коллекции  
  
1.  В строке меню выберите **Сервис**, **Расширения и обновления**.  
  
2.  В левой области выберите **обновления**и выберите **Мои репозитория**.  
  
3.  В области справа выберите расширение, а затем выберите **обновление** кнопки.  
  
## <a name="see-also"></a>См. также  
 [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
